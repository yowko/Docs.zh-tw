### <a name="currentculture-and-currentuiculture-flow-across-tasks"></a>工作之間的 CurrentCulture 和 CurrentUICulture 流程

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.6 開始，<xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> 會儲存在執行緒的 <xref:System.Threading.ExecutionContext?displayProperty=name>，它會在非同步作業之間流動。這表示變更 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> 會反映在稍後以非同步方式執行的工作。 這與舊版 .NET Framework 的行為不同，而舊版本會重設所有非同步工作中的 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name>。|
|建議|受到此變更影響的應用程式，可以藉由明確地設定所需的 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> 作為非同步工作中的第一個作業來因應。 或者，可以藉由設定下列相容性參數，以選擇加入舊的行為 (不流動 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name>)：<pre><code class="language-C#">AppContext.SetSwitch(&quot;Switch.System.Globalization.NoAsyncCurrentCulture&quot;, true);&#13;&#10;</code></pre>.NET Framework 4.6.2 中的 WPF 已修正此問題。 .NET Frameworks 4.6、4.6.1 也已透過 [KB 3139549](https://support.microsoft.com/kb/3139549) 進行修正。 以 .NET 4.6 或更新版本為目標的應用程式將在 WPF 應用程式中自動取得正確的行為 - <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> 會跨發送器作業保留。|
|範圍|次要|
|版本|4.6|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType></li><li><xref:System.Threading.Thread.CurrentCulture?displayProperty=nameWithType></li><li><xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=nameWithType></li><li><xref:System.Threading.Thread.CurrentUICulture?displayProperty=nameWithType></li></ul>|

