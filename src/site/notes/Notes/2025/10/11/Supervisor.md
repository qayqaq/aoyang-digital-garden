---
{"dg-publish":true,"permalink":"/notes/2025/10/11/supervisor/"}
---

#process-management #devops #linux #system-administration

[[Supervisor.canvas\|Supervisor.canvas]]

# Supervisor: A Process Control System

## 1. Introduction to Supervisor

**Supervisor** is a client/server system designed to monitor and control a number of processes on UNIX-like operating systems. Its primary purpose is to ensure that critical application processes remain running by automatically restarting them if they crash or exit unexpectedly. While it shares some functional similarities with system initialization tools like `init` or `systemd`, Supervisor is not intended as a replacement. Instead, it is specifically engineered to manage **application-level processes**, providing a robust, centralized, and easy-to-use framework for process management.

The significance of Supervisor lies in its simplicity and reliability. It provides developers and system administrators with a consistent way to manage application lifecycles, handle logging, and ensure high availability without the complexity of writing custom `init` scripts or managing processes manually.

## 2. Core Architecture: A Client/Server Model

Supervisor operates on a classic client/server model, which decouples the process management daemon from the user interface used to control it. This architecture consists of two primary components.

### 2.1. `supervisord`: The Server Daemon

The core of the system is `supervisord`, a long-running daemon process. Its key responsibilities include:
-   **Starting Child Processes**: It launches and manages all processes defined in its configuration file.
-   **Monitoring Process States**: It continuously monitors the state of its child processes (e.g., running, stopped, exited).
-   **Automatic Restarting**: If a process terminates unexpectedly, `supervisord` can automatically restart it based on its configuration.
-   **Log Aggregation**: It captures the `stdout` and `stderr` streams from its child processes and redirects them to specified log files.
-   **Responding to Commands**: It listens for commands from clients (like `supervisorctl`) on a UNIX or TCP socket and acts upon them.

### 2.2. `supervisorctl`: The Command-Line Client

`supervisorctl` is the default command-line interface (CLI) for interacting with the `supervisord` daemon. It provides a simple shell-like environment for:
-   Checking the status of managed processes.
-   Starting, stopping, and restarting processes individually or in groups.
-   Forcing `supervisord` to re-read its configuration and apply changes.

In addition to the CLI, Supervisor also offers an optional **Web Interface** that provides similar control capabilities through a browser, and an **XML-RPC interface** for programmatic control.

## 3. The Configuration File

Supervisor is controlled by a central configuration file, typically named `supervisord.conf`. This file uses an INI-style format and is composed of different sections, or blocks, each controlling a specific aspect of the system.

### 3.1. Structure of `supervisord.conf`

The configuration is organized into sections denoted by `[section_name]`. The most critical sections are:

-   **`[supervisord]`**: Contains global settings for the `supervisord` daemon itself, such as the location of its log file and PID file.
-   **`[supervisorctl]`**: Configures the `supervisorctl` client, including the server URL it should connect to.
-   **`[program:x]`**: Defines a program to be managed by Supervisor. Each program gets its own `[program:...]` block, where `x` is the unique name of the program.

### 3.2. Example Program Configuration

This is the most important part of the configuration, as it defines what processes to run and how to run them.

```ini
[program:my_app]
; The command to execute to start the process
command=/usr/bin/python /path/to/my_app.py

; The directory to run the command from
directory=/path/to/

; The user to run the process as
user=www-data

; Start this program automatically when supervisord starts
autostart=true

; Automatically restart the process if it exits
; Options: false, true, unexpected (restarts only on unexpected exit codes)
autorestart=true

; Number of seconds the program needs to stay running to be considered "started"
startsecs=10

; Number of times to retry starting the program before giving up
startretries=3

; Where to redirect the process's stdout and stderr streams
stdout_logfile=/var/log/my_app.out.log
stderr_logfile=/var/log/my_app.err.log

; Number of processes to start. Useful for running multiple workers.
numprocs=4

; Naming for multiple processes (e.g., my_app_00, my_app_01)
process_name=%(program_name)s_%(process_num)02d
```

## 4. Process States and Lifecycle Management

Supervisor manages processes through a well-defined state machine. Understanding these states is key to diagnosing and managing applications effectively.

-   `STOPPED`: The process has been stopped intentionally or has never been started.
-   `STARTING`: The process is in the process of being started.
-   `RUNNING`: The process has been running for more than `startsecs` and is considered stable.
-   `BACKOFF`: The process has entered the `STARTING` state but exited too quickly to be considered `RUNNING`. Supervisor will wait for a backoff period before retrying.
-   `STOPPING`: The process is being stopped.
-   `EXITED`: The process has exited from the `RUNNING` state. If `autorestart` is configured, it will be restarted.
-   `FATAL`: The process could not be started successfully `startretries` times in a row. It will not be retried again.
-   `UNKNOWN`: The `supervisord` daemon has encountered an unexpected error.

The transition between these states is governed by directives like `autorestart`, `startsecs`, `startretries`, and `exitcodes` (which defines the "expected" exit codes). This system ensures that failing processes do not consume excessive system resources in a rapid restart loop.

## 5. Practical Management with `supervisorctl`

The `supervisorctl` client is the primary tool for day-to-day process management.

#### Common Commands:

-   **`status`**: View the current state of all managed processes.
    ```bash
    supervisorctl status
    my_app_00                        RUNNING   pid 123, uptime 0:15:42
    my_app_01                        RUNNING   pid 124, uptime 0:15:42
    ```
-   **`stop <name>`**: Stop a specific process or all processes in a group.
    ```bash
    supervisorctl stop my_app_01
    ```
-   **`start <name>`**: Start a process.
    ```bash
    supervisorctl start my_app_01
    ```
-   **`restart <name>`**: A convenient shortcut for `stop` followed by `start`.
    ```bash
    supervisorctl restart my_app:  # Restarts all processes in the 'my_app' group
    ```
-   **`reread`**: Checks for changes in the configuration files but does not apply them.
    ```bash
    supervisorctl reread
    ```
-   **`update`**: Applies the configuration changes identified by `reread`. This will start any new programs and stop/restart any modified or removed ones.
    ```bash
    supervisorctl update
    ```
-   **`reload`**: A combined command that performs a `reread` and `update`, and also restarts the `supervisord` daemon itself.

## 6. Conclusion

Supervisor provides a simple, robust, and highly effective solution for managing and monitoring application processes. Its client/server architecture, clear configuration syntax, and reliable automatic restart capabilities make it an invaluable tool for ensuring application uptime and simplifying operational management. While modern container orchestration platforms like Docker and Kubernetes offer more advanced, distributed process management, Supervisor remains a highly relevant and widely used tool for managing processes on a single host, particularly in traditional server environments and for development purposes.
