```cmd
@echo off
setlocal

REM Check if the program name is provided
if "%~1"=="" (
    echo Usage: run_as_admin.bat [ProgramName]
    echo Example: run_as_admin.bat vscode
    echo Example: run_as_admin.bat intellij
    echo Example: run_as_admin.bat cmd
    exit /b 1
)

REM Define program paths
set "vscode=C:\Program Files\Microsoft VS Code\Code.exe"
set "intellij=C:\Program Files\JetBrains\IntelliJ IDEA\bin\idea64.exe"
set "cmd=C:\Windows\System32\cmd.exe"

REM Get the program path based on user input
set "programName=%~1"
call set "programPath=%%%programName%%%"

REM Check if the path was found
if "%programPath%"=="" (
    echo Error: No path found for the program '%programName%'
    exit /b 1
)

REM Check if the program exists at the specified path
if not exist "%programPath%" (
    echo Error: The program does not exist at %programPath%
    exit /b 1
)

REM Run the program as admin using saved credentials
echo Starting %programName% as administrator...
runas /user:Administrator /savecred "%programPath%"

endlocal

```
