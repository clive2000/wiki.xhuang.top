# Archive subfolder

{% code-tabs %}
{% code-tabs-item title="to7z.ps1" %}
```text
# Loop thorugh folder

$7z = 'C:\Program Files\7-Zip\7z.exe'
Get-ChildItem $PWD -Directory | ForEach-Object {
    & $7z a -t7z (-join($_.Name,".7z")) $_.FullName
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

A powershell to archive each subfolder into seperate 7z file in windows. 7zip installation is required.

