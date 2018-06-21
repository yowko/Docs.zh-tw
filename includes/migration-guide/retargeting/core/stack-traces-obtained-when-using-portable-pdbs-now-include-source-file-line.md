### <a name="stack-traces-obtained-when-using-portable-pdbs-now-include-source-file-and-line-information-if-requested"></a>使用可攜式 PDB 時取得的堆疊追蹤，現已包含來源檔案與程式碼資訊 (若要求)

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.7.2 開始，如果要求，使用可攜式 PDB 時取得的堆疊追蹤會包含來源檔案與程式碼資訊。 在 .NET Framework 4.7.2 之前的版本中，即使明確要求，使用可攜式 PDB 時也無法取得來源檔案和程式碼資訊。|
|建議|若為以 .NET Framework 4.7.2 為目標的應用程式，如果不需要，您可以透過將下列內容新增至 <code>app.config</code> 檔案的 <code>&lt;runtime&gt;</code> 區段，選擇使用可攜式 PDB 時不包含來源檔案和程式碼資訊︰<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>若為以舊版 .NET Framework 為目標但卻在 .NET Framework 4.7.2 或更新版本上執行的應用程式，則可將下列內容新增至 <code>app.config</code> 檔案的 <code>&lt;runtime&gt;</code> 區段，選擇使用可攜式 PDB 時包含來源檔案和程式碼資訊︰<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|範圍|Edge|
|版本|4.7.2|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Diagnostics.StackTrace.%23ctor(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Boolean)?displayProperty=nameWithType><li><xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Int32,System.Boolean)?displayProperty=nameWithType></li></ul>|

