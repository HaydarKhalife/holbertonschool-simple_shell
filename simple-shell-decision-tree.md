![decision-tree](https://github.com/manningstinson/holbertonschool-simple_shell/assets/104523090/407a7ec2-3e1f-4577-8b24-b29eb55e2d87)

# Simple Shell Process Flow & Error Handling
Here's a breakdown of the given shell execution process in a flowchart format. Included are flows for error handing, non built in commands, and subshell commands.  

**Shell Awaits User Input** <br>
The process initiates as the shell awaits user input.

**Tokenize and Parse User Input** <br>
User input undergoes tokenization and parsing for further processing.

## Is it a Built-in Command
The initial decision point involves determining if the user input corresponds to a built-in command.

**Execute Built-in Command** <br>
If the input matches a built-in command, execute it, advancing the process.

## Is it an Executable File?
The second decision point examines whether the user input is an executable file.

**Child Process Execution** <br>
The child process, created by forking, is responsible for executing the external command.

**Loading the Executable** <br>
The child process loads the executable code of the external command into its address space.

**Replacing Image** <br>
The child process replaces its current image with the image of the external command. This involves loading the code and data of the external command into the memory space of the child process.

**Command Execution** <br>
The external command is executed within the context of the child process. This involves performing the actions specified by the command, whether it's running a program, processing data, or performing some other operation.

**Child Process Termination** <br>
Once the external command completes its execution, the child process terminates. The termination might be normal, indicating that the command executed successfully, or it could be due to an error.

**Exit Status** <br>
The child process may exit with a status code, which indicates the outcome of the command execution. The exit status is typically checked by the parent process (the shell) to determine whether the command executed successfully or encountered an issue.

**Parent Process Handling** <br>
The parent process (the shell) may perform additional actions based on the exit status of the child process. For example, it might display an error message if the command failed, or it might continue with the next steps if the command succeeded.

**Waiting for Child Process** <br>
In many cases, the parent process waits for the child process to complete before proceeding. This ensures that the shell doesn't move on to the next command until the current one has finished executing.

**Fork and Execute the Command** <br>
For executable files, fork and execute the command to progress further.

## Is it a Directory?
The third decision point assesses if the user input represents a directory.

**Change to the Directory** <br>
If the input denotes a directory, change to it to continue the process.

## Is it a Subshell Command?
The fourth decision point involves identifying if the user input is a subshell command.

**Subshell Execution Process**<br>
The subshell command initiates a subprocess dedicated to executing a series of commands within a confined environment.

**Shell Forks Subshell Process** <br>
The shell invokes a new subprocess (subshell) through the fork system call.

**Subshell Command Execution**<br>
The newly created subprocess commences the execution of commands specified in the subshell.

**Command Execution in Subshell**<br>
The subshell rigorously executes the provided series of commands within its isolated environment.

**Subshell Command Completion**<br>
The subshell finalizes the execution of all commands within its designated environment.

**Subshell Process Termination**<br>
The subprocess (subshell) concludes its execution after successfully running all the specified commands.

**Subshell Exit Status**<br>
The subshell may exit with a status code, indicating the success or failure of the commands within.

**Parent Process Handling**<br>
The parent process (main shell) examines the exit status of the subshell to ascertain the success of its commands.

**Parent Process Continues**<br>
Following subshell completion, the parent process resumes execution, handling the exit status, performing error handling, or proceeding with subsequent steps.

**Shell Continues Execution Flow**<br>
The shell seamlessly resumes its regular execution flow, potentially processing additional user commands or instructions. The newly created subprocess commences the execution of commands specified in the subshell.

## If User Doesn't Interrupt

**Error Detection** <br>
The shell detects an error during the execution of a command. Errors can occur for various reasons, such as a command not being found, permission issues, syntax errors, etc.

**Error Handling** <br>
The shell performs error handling to manage the encountered issue. This may involve displaying an error message to the user, logging the error for further analysis, or taking corrective actions if possible.

**Error Message to User** <br>
The shell often displays an error message to inform the user about the nature of the problem. The message might include details about the error, such as the command that failed and a description of the issue.

**Error Exit Status** <br>
The command that encountered the error typically exits with a non-zero exit status to indicate that an issue occurred. The specific exit status code may provide additional information about the type of error.

**Parent Process (Shell) Handling** <br>
The parent process (the main shell) checks the exit status of the command to determine whether it completed successfully or encountered an error. If the exit status indicates an error, the shell may take appropriate actions.

**Continuation or Termination** <br>
Depending on the nature of the error and the shell's configuration, the shell may decide whether to continue or terminate further execution. Some shells have options to continue executing subsequent commands even if one command encounters an error (using constructs like && or ||), while others may terminate the script or interactive session on the first error.

**User Interaction** <br>
The shell may prompt the user for additional input or instructions, depending on the severity and type of the error. This could involve asking the user to provide corrected input or making decisions on how to proceed.

**Logging and Debugging** <br>
The shell may log information about the encountered error for debugging purposes. This information could be useful for diagnosing issues and improving the overall reliability of the shell.
