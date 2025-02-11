@echo off
setlocal

REM Check if the program name is provided
if "%~1"=="" (
echo Usage: run_as_admin.bat [ProgramPath]
echo Example: run_as_admin.bat "C:\Program Files\JetBrains\IntelliJ IDEA\bin\idea64.exe"
echo Example: run_as_admin.bat "C:\Program Files\Microsoft VS Code\Code.exe"
exit /b 1
)

REM Get the program path from argument
set PROGRAM_PATH="%~1"

REM Check if the program exists
if not exist %PROGRAM_PATH% (
echo Error: The specified program does not exist at %PROGRAM_PATH%
exit /b 1
)

REM Run the program as admin using saved credentials
echo Starting %PROGRAM_PATH% as administrator...
runas /user:Administrator /savecred %PROGRAM_PATH%

endlocal
