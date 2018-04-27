### <a name="workflow-checksums-changed-from-md5-to-sha1"></a>工作流程總和檢查碼從 MD5 變更為 SHA1

|   |   |
|---|---|
|詳細資料|為了支援使用 Visual Studio 進行偵錯，工作流程執行階段會使用雜湊演算法為工作流程執行個體產生總和檢查碼。 在 .NET Framework 4.6.2 和更早版本中，工作流程總和檢查碼雜湊使用 MD5 演算法，它會在啟用 FIPS 的系統上造成問題。 從 .NET Framework 4.7 開始，演算法是 SHA1。 如果您的程式碼已保存這些總和檢查碼，就會不相容。|
|建議|如果您的程式碼因為總和檢查碼失敗而無法載入工作流程執行個體，請嘗試將 <code>AppContext</code> 參數 &quot;Switch.System.Activities.UseMD5ForWFDebugger&quot; 設為 true。在程式碼中：<pre><code class="language-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseMD5ForWFDebugger&quot;, true);&#13;&#10;</code></pre>或者，在組態中：<pre><code class="language-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseMD5ForWFDebugger=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|範圍|次要|
|版本|4.7|
|類型|正在重定目標|

