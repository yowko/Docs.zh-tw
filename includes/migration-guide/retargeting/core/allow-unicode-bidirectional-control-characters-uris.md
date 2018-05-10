### <a name="allow-unicode-bidirectional-control-characters-in-uris"></a>允許在 URI 中使用 Unicode 雙向控制字元

|   |   |
|---|---|
|詳細資料|Unicode 會指定數個特殊控制字元，用來指定文字的方向。 在舊版的 .NET Framework 中，這些字元會從所有 URI 中不正確地移除，即使它們存在於自己的百分比編碼中。 為進一步遵循 [RFC 3987](http://tools.ietf.org/html/rfc3987)，我們現在允許在 URI 中使用這些字元。 在 URI 找到未編碼的內容時，它們是百分比編碼的。 找到百分比編碼的內容時，它們會保持現況。|
|建議|以 .NET Framework 4.7.2 版開始為目標的應用程式，預設啟用對 Unicode 雙向字元的支援。 如果不需要這項變更，您可以在應用程式組態檔的 <code>&lt;runtime&gt;</code> 區段中新增下列 [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 參數來停用此變更：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>對於以舊版 .NET Framework 為目標，但執行版本低於 .NET Framework 4.7.2 (含) 的應用程式，預設停用對 Unicode 雙向字元的支援。 您可以在應用程式組態檔的 <code>&lt;runtime&gt;</code> 區段中新增下列 [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 參數停用它：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|範圍|次要|
|版本|4.7.2|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

