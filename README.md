# Dummy.exe-Files
Test Dummy .exe Files 

Created with the following powershell script 

# Set the directory where the dummy.exe files will be created
$outputDir = "D:\DummyEXEs"  # Change this to your desired directory

# Create the output directory if it doesn't exist
if (!(Test-Path -Path $outputDir)) {
    New-Item -ItemType Directory -Path $outputDir | Out-Null
}

# Loop to create 10000 dummy.exe files
for ($i = 1; $i -le 10000; $i++) {
    # Create a simple batch file with a.bat extension
    $batchFile = Join-Path $outputDir "dummy_$i.bat"
    "@echo off`nexit" | Out-File -FilePath $batchFile -Encoding ASCII

    # Rename the.bat file to.exe
    $exeFile = Join-Path $outputDir "dummy_$i.exe"
    Rename-Item -Path $batchFile -NewName $exeFile
}

Write-Host "Created 10000 dummy.exe files in $outputDir"
