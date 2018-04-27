### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a>WPF 視窗在擴充到單一顯示器之外時呈現而不裁剪

|   |   |
|---|---|
|詳細資料|在 Windows 8 和更新版本中執行的 .NET Framework 4.6 多重監視器案例中，如果視窗擴充到單一顯示畫面之外，可呈現完整視窗而不會將其裁剪。 這與舊版 .NET Framework 不同，後者會在 WPF 視窗擴充到單一顯示畫面之外時裁剪該視窗。|
|建議|您可以在應用程式組態檔的 <code>&lt;appSettings&gt;</code> 中使用 <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> 項目，或在應用程式啟動時藉由設定 <code>EnableMultiMonitorDisplayClipping</code> 屬性，來明確設定這項行為 (不論是否裁剪)。|
|範圍|次要|
|版本|4.6|
|類型|執行階段|

