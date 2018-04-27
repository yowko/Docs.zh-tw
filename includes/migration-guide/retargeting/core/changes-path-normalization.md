### <a name="changes-in-path-normalization"></a>路徑正規化的變更

|   |   |
|---|---|
|詳細資料|從以 .NET Framework 4.6.2 為目標的應用程式開始，執行階段正規化路徑的方式已變更。正規化路徑涉及修改識別路徑或檔案的字串，使它符合目標作業系統上的有效路徑。 正規化通常牽涉到︰<ul><li>規範化元件和目錄分隔符號。</li><li>將目前的目錄套用到相對路徑。</li><li>評估路徑中的相對目錄 (.) 或上層目錄 (..)。</li><li>修剪指定的字元。</li></ul>從以 .NET Framework 4.6.2 為目標的應用程式開始，預設會啟用路徑正規化的下列變更：<ul><li>執行階段會延後至作業系統的 [GetFullPathName](https://msdn.microsoft.com/library/windows/desktop/aa364963(v=vs.85).aspx) 函式再進行路徑正規化。</li><li>正規化不再涉及修剪目錄區段的結尾 (例如目錄名稱結尾的空格)。</li><li>完全信任的裝置路徑語法支援，包括 <code>\\.\</code> and, for file I/O APIs in mscorlib.dll, '\?'.</li><li>The runtime does not validate device syntax paths.</li><li>The use of device syntax to access alternate data streams is supported.</li></ul>These changes improve performance while allowing methods to access previously inaccessible paths. Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.|
|建議|以 .NET Framework 4.6.2 或更新版本為目標的應用程式可透過在應用程式設定檔的 <code>&lt;runtime&gt;</code> 區段中新增下列內容來選擇退出此變更，並使用舊版行為：<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>以 .NET Framework 4.6.1 或更早版本為目標，但在 .NET Framework 4.6.2 或更新版本上執行的應用程式，可以藉由在應用程式設定檔的 <code>&lt;runtime&gt;</code> 區段新增下行，就能啟用路徑正規化的變更：<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|範圍|次要|
|版本|4.6.2|
|類型|正在重定目標|

