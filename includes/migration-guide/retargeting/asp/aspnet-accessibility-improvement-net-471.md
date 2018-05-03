### <a name="aspnet-accessibility-improvement-in-net-471"></a>.NET 4.7.1 中的 ASP.NET 協助工具改善

|   |   |
|---|---|
|詳細資料|ASP.NET 正在改善 ASP.NET Web 控制項如何使用 Visual Studio 中的協助工具技術，更妥善支援 ASP.NET 客戶。  這些包括下列變更：<ul><li>在控制項 (例如 [詳細資料檢視精靈] 的 [新增欄位] 對話方塊) 中，實作遺漏 UI 協助工具模式的變更。</li><li>改善高對比模式顯示的變更，例如資料頁面巡覽區欄位編輯器。</li><li>改善控制項 (例如 [Configure Object Context Window (設定物件內容)] 視窗或 [Configure Data Source Window (設定資料來源)] 視窗) 之鍵盤瀏覽體驗的變更。</li></ul>|
|建議|**如何選擇加入或退出這些變更**：為了讓 Visual Studio 設計工具可受益於這些變更，它必須在 .NET Framework 4.7.1 或更新版本上執行。 Web 應用程式可以由下列任一種方式受益於這些變更：<ul><li>安裝 Visual Studio 2017 15.3 或更新版本中，依預設它會以下列 AppContext 參數支援新的協助工具功能。</li><li>藉由將 **Switch.UseLegacyAccessibility** AppContext 參數新增至 devenv.exe.config 檔案中的 `<runtime>` 區段，並將它設定為 `false`，選擇退出舊版協助工具行為，如下列範例所示。</li></ul><pre><code>&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;<br />&lt;configuration&gt;<br />&lt;runtime&gt;<br />...</code></pre>|
|範圍|次要|
|版本|4.7.1|
|類型|正在重定目標|
