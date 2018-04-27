### <a name="throttle-concurrent-requests-per-session"></a>每一個工作階段的節流閥並行要求數目

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.6.2 和更早版本中，ASP.NET 會使用相同的 Sessionid 循序執行要求，且 ASP.NET 預設一律會透過 Cookie 發出 Sessionid。 如果頁面會花很長的時間來回應，光是在瀏覽器上按 F5 便會大幅降低伺服器效能。 在修正程式中，我們新增了一個計數器來追蹤佇列要求，並在超過指定限制時終止要求。 預設值為 50。 如果達到限制，會在事件記錄檔記錄警告並在 IIS 記錄檔中記錄 HTTP 500 回應。|
|建議|若要還原舊行為，您可以將下列設定加入您的 web.config 檔案以選擇退出新行為。<pre><code class="language-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;aspnet:RequestQueueLimitPerSession&quot; value=&quot;2147483647&quot;/&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|範圍|Edge|
|版本|4.7|
|類型|正在重定目標|

