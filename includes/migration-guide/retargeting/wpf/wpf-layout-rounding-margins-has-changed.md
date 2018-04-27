### <a name="wpf-layout-rounding-of-margins-has-changed"></a>邊界的 WPF 版面配置進位已變更

|   |   |
|---|---|
|詳細資料|邊界的進位方式以及邊界內部的框線和背景皆有所變更。 此變更的結果：<ul><li>項目寬度或高度的增減最多不超過一個像素。</li><li>物件的位置的位最多不超過一個像素。</li><li>置中項目的垂直或水平位移最多不超過一個像素。</li></ul>預設只有以 .NET Framework 4.6 為目標的應用程式才會啟用此新版面配置。|
|建議|由於此修改會停用高 DPI 之 WPF 控制項右側或底端的裁剪功能；因此，應用程式若是以舊版 .NET Framework 為目標，但要在 .NET Framework 4.6 上執行，可在 app.config 檔案的 <code>&lt;runtime&gt;</code> 區段中新增下列程式行來選擇使用此新行為：<code>&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false&quot; /&gt;</code>應用程式若是以 .NET Framework 4.6 為目標，但想使用先前的配置演算法來呈現 WPF 控制項，可在 app.config 檔案的 <code>&lt;runtime&gt;</code> 區段中新增下列程式行，以執行此作業：<code>&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true&quot; /&gt;</code>。|
|範圍|次要|
|版本|4.6|
|類型|正在重定目標|

