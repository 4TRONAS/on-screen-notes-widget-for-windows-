# On screen notes widget
# saved on desktop notes for everyday immediate note taking for important events and work.
# to work this file, extract all into another folder named- apple notes

# paste the following into powershell

 $folder = (Read-Host 'Paste the full path to your apple notes folder').Trim('"')
$file = Get-ChildItem -LiteralPath $folder -Filter LittleNotes.ps1 -Recurse -File | Select-Object -First 1
if (!$file) { throw 'LittleNotes.ps1 was not found in that folder.' }

Copy-Item -LiteralPath $file.FullName -Destination ($file.FullName + '.bak') -Force
$code = Get-Content -LiteralPath $file.FullName -Raw
$code = $code.Replace(
    '$script:TitleBox.ClearUndo(); $script:Editor.ClearUndo()',
    '$script:TitleBox.IsUndoEnabled = $false; $script:Editor.IsUndoEnabled = $false; $script:TitleBox.IsUndoEnabled = $true; $script:Editor.IsUndoEnabled = $true'
)
Set-Content -LiteralPath $file.FullName -Value $code -Encoding UTF8

& "$env:SystemRoot\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -STA -ExecutionPolicy Bypass -File $file.FullName

# when asked to enter path to file you can just type in C:\apple notes to just directly path it to the file
