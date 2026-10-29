# On screen notes widget
# saved on desktop notes for everyday immediate note taking for important events and work.
# to work this file, extract all into another folder named- apple notes

# paste the following into powershell

# cd $env:USERPROFILE\Downloads

# Expand-Archive (Get-ChildItem .\Island-windows-widget*.zip | Sort-Object LastWriteTime -Descending | Select-Object -First 1).FullName C:\Island2 -Force

# cd C:\Island2\Island

# .\Island.ps1 -DebugMode

# when asked to enter path to file you can just type in C:\apple notes to just directly path it to the file
