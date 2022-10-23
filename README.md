「本機群組原則編輯器 gpedit.msc」Windows 10 Home 家用版沒有這項功能。本篇就以最簡單的方式，執行BAT批次檔就能讓Windows 10 Home 家用版新增gpedit.msc功能

以正常來說，在Windows 10 Pro專業版中，按下「Windows鍵 + R」後，再輸入「gpedit.msc」就可以呼叫出本機群組原則編輯器，但Windows 10 Home 家用版沒有這項功能，因此無法使用此項功能。

但其實在作業系統內部，仍然是有此項功能，只是被隱藏掉。因此當按下「Windows鍵 + R」後，再輸入「gpedit.msc」後按確定會跳出找不到的視窗。但其實仍可以透過其他種方式將此功能打開，


也可以用以下的內容另存成bat副檔名的檔案，再透過「以系統管理員身分執行」來執行即可。

</script>
</div>

<p>如果老貓的連結失效，也可以用以下的內容另存成bat副檔名的檔案，再透過「<strong>以系統管理員身分執行</strong>」來執行即可。</p>
<p><code>@echo off<br>
pushd "%~dp0"<br>
dir /b %SystemRoot%\servicing\Packages\<a href="https://iqmore.tw/tag/microsoft" class="st_tag internal_tag " rel="tag" title="Posts tagged with Microsoft">Microsoft</a>-<a href="https://iqmore.tw/tag/windows" class="st_tag internal_tag " rel="tag" title="Posts tagged with Windows">Windows</a>-GroupPolicy-ClientExtensions-Package~3*.mum &gt;List.txt<br>
dir /b %SystemRoot%\servicing\Packages\<a href="https://iqmore.tw/tag/microsoft" class="st_tag internal_tag " rel="tag" title="Posts tagged with Microsoft">Microsoft</a>-<a href="https://iqmore.tw/tag/windows" class="st_tag internal_tag " rel="tag" title="Posts tagged with Windows">Windows</a>-GroupPolicy-ClientTools-Package~3*.mum &gt;&gt;List.txt<br>
for /f %%i in ('findstr /i . List.txt 2^&gt;nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i"<br>
pause</code></p><div class="03d217882a668356b98fb52c120f6bd4" data-index="4" style="float: none; margin:10px 0 10px 0; text-align:center;">
<script type="text/javascript" src="//js1.bloggerads.net/contentads.aspx?blogid=20221015000003" async></script>
</div>


使用時，針對這個檔案點選右鍵後選擇「以系統管理員身分執行」。

接下來要讓程式跑一段時間，通常不會太久，但要確定等他完整跑完後再關閉。
