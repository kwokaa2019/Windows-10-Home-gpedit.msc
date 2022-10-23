「本機群組原則編輯器 gpedit.msc」Windows 10 Home 家用版沒有這項功能。本篇就以最簡單的方式，執行BAT批次檔就能讓Windows 10 Home 家用版新增gpedit.msc功能

以正常來說，在Windows 10 Pro專業版中，按下「Windows鍵 + R」後，再輸入「gpedit.msc」就可以呼叫出本機群組原則編輯器，但Windows 10 Home 家用版沒有這項功能，因此無法使用此項功能。

但其實在作業系統內部，仍然是有此項功能，只是被隱藏掉。因此當按下「Windows鍵 + R」後，再輸入「gpedit.msc」後按確定會跳出找不到的視窗。但其實仍可以透過其他種方式將此功能打開，


也可以用以下的內容另存成bat副檔名的檔案，再透過「以系統管理員身分執行」來執行即可。

@echo off

pushd "%~dp0"

dir /b %SystemRoot%\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientExtensions-Package~3*.mum >List.txt

dir /b %SystemRoot%\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientTools-Package~3*.mum >>List.txt

for /f %%i in ('findstr /i . List.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i"

pause


使用時，針對這個檔案點選右鍵後選擇「以系統管理員身分執行」。

接下來要讓程式跑一段時間，通常不會太久，但要確定等他完整跑完後再關閉。

接下來重新在執行視窗中輸入「gpedit.msc」，就能跑出本機群組原則編輯器嚕！雖然不用重開機就能立即執行，但建議重新開機一下比較保險，確保程式能正確執行。
