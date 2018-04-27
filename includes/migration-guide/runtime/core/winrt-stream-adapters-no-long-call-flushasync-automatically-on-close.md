### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a>WinRT 資料流配接器不會再於關閉時自動呼叫 FlushAsync

|   |   |
|---|---|
|詳細資料|在 Windows 市集應用程式中，Windows 執行階段資料流配接器不會再從 Dispose 方法呼叫 FlushAsync 方法。|
|建議|這項變更應該是透明的。 開發人員可以撰寫下列程式碼來還原舊有行為：<pre><code class="language-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>|
|範圍|透明|
|版本|4.5.1|
|類型|執行階段|

