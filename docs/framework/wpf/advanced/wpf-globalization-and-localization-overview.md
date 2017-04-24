---
title: "WPF 全球化和當地語系化概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "全球化, 關於全球化"
  - "當地語系化, 關於當地語系化"
ms.assetid: 56e5a5c8-6c96-4d19-b8e1-a5be1dc564af
caps.latest.revision: 39
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 34
---
# WPF 全球化和當地語系化概觀
當您將自己的產品限制為只能提供一種語言時，您也同時將潛在客戶群限制為全球 65 億人口中的一小部分。  如果您希望應用程式能夠達到全球化的目標，則針對產品進行符合成本效益的當地語系化作業，不僅是最好也最經濟的一種方式，而且能夠吸引更多的客戶。  
  
 本概觀簡介 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 的全球化和當地語系化功能。  全球化是指設計及開發可在多個地點執行的應用程式。  例如，全球化可支援當地語系化的使用者介面和不同文化特性 \(Culture\) 之使用者的地區資料。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供全球化設計功能，包括自動配置、附屬組件，以及當地語系化的屬性 \(Attribute\) 和註解。  
  
 當地語系化是指針對應用程式支援的特定文化特性，將應用程式資源轉譯成當地語系化的版本。  在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中進行當地語系化時，您可以使用 <xref:System.Windows.Markup.Localizer> 命名空間中的 API。這些 API 是 [LocBaml 工具範例](http://go.microsoft.com/fwlink/?LinkID=160016)命令列工具背後的動力。  如需如何建置 \(Build\) 及使用 LocBaml 的詳細資訊，請參閱 [將應用程式當地語系化](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)。  
  
   
  
## WPF 全球化和當地語系化的最佳做法  
 您可以遵照本節提供的 UI 設計與當地語系化相關秘訣，充分利用已內建在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的全球化和當地語系化功能。  
  
### WPF UI 設計的最佳做法  
 在設計 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 架構的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 時，請考慮採用下列最佳做法：  
  
-   以 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 撰寫 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]；避免在程式碼中建立 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 建立 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 時，您會透過內建的當地語系化 API 公開 \(Expose\) 它。  
  
-   避免使用絕對位置和固定大小來配置內容，請使用相對或自動調整的大小。  
  
    -   使用 <xref:System.Windows.Window.SizeToContent%2A>，並將寬度和高度設定保持為 `Auto`。  
  
    -   避免使用 <xref:System.Windows.Controls.Canvas> 來配置 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
    -   使用 <xref:System.Windows.Controls.Grid> 及其大小共用功能。  
  
-   在邊界部分提供額外的空間，因為當地語系化的文字通常需要較多空間。  額外的空間可以容納可能突出的字元。  
  
-   在 <xref:System.Windows.Controls.TextBlock> 上啟用 <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> 以防止裁剪發生。  
  
-   設定 **xml:lang** 屬性。  此屬性描述特定項目及其子項目的文化特性。  這個屬性的值可變更 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中幾項功能的行為。例如，它會變更斷字、拼字檢查、數字替換、複雜指令碼成形以及字型後援 \(Fallback\) 的行為。  如需設定 [XAML 中的 xml:lang 處理](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md)的詳細資訊，請參閱[WPF 的全球化](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)。  
  
-   建立自訂的複合字型，進一步控制用於不同語言的字型。  根據預設，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會使用 Windows\\Fonts 目錄中的 GlobalUserInterface.composite 字型。  
  
-   當您建立的巡覽應用程式可以當地語系化成某個文化特性，而在這個文化特性中，文字呈現的格式是由右至左時，請明確設定每個頁面的 <xref:System.Windows.FlowDirection>，以確保頁面不會從 <xref:System.Windows.Navigation.NavigationWindow> 繼承 <xref:System.Windows.FlowDirection>。  
  
-   當您建立裝載 \(Host\) 於瀏覽器外部的獨立巡覽應用程式時，請將初始應用程式的 <xref:System.Windows.Application.StartupUri%2A> 設定為 <xref:System.Windows.Navigation.NavigationWindow>，而非設定成頁面 \(例如 `<Application StartupUri="NavigationWindow.xaml">`\)。  這種設計可以讓您變更視窗及巡覽列的 <xref:System.Windows.FlowDirection>。  如需詳細資訊和範例，請參閱[全球化首頁範例](http://go.microsoft.com/fwlink/?LinkID=159990) \(英文\)。  
  
### WPF 當地語系化的最佳做法  
 在當地語系化 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 架構的應用程式時，請考慮採用下列最佳做法：  
  
-   使用當地語系化註解為當地語系化人員提供額外的內容。  
  
-   使用當地語系化屬性控制當地語系化，而不要選擇性地省略項目上的 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> 屬性。  如需詳細資訊，請參閱[當地語系化屬性和註解](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md)。  
  
-   使用 **msbuild \/t:updateuid** 和**\/t:checkuid** 在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中加入及檢查 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> 屬性。  使用 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> 屬性追蹤開發和當地語系化之間的變更。<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> 屬性可幫助您當地語系化新的開發變更。  如果您手動將 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> 屬性加入至 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，工作內容通常很瑣碎而且比較不精確。  
  
    -   請勿在開始進行當地語系化之後編輯或變更 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> 屬性。  
  
    -   請勿使用重複的 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> 屬性 \(使用複製及貼上的命令時，請牢記這個秘訣\)。  
  
    -   設定 AssemblyInfo.\* 中的 `UltimateResourceFallback` 位置，以指定後援的適當語言 \(例如 `[assembly: NeutralResourcesLanguage("en-US",   UltimateResourceFallbackLocation.Satellite)]`\)。  
  
         如果您決定在專案檔中省略 `<UICulture>` 標記，以便在主要組件中包含來源語言，請將 `UltimateResourceFallback` 位置設定為主要組件，而非附屬組件 \(例如 `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.MainAssembly)]`\)。  
  
<a name="workflow_to_localize"></a>   
## 當地語系化 WPF 應用程式  
 當地語系化 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式時，您有幾項選擇。  例如，您可以將應用程式中可當地語系化的資源繫結至 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 檔案、將可當地語系化的文字儲存在 resx 資料表，或是讓當地語系化人員使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 檔案。  本節說明會使用 BAML 式 XAML 的當地語系化工作流程，這種工作流程具有下列幾項優點：  
  
-   您可以在完成建置之後進行當地語系化。  
  
-   您可以從舊版 BAML 式 XAML 的翻譯更新為新版 BAML 式 XAML，使您可以在開發的過程中同時進行當地語系化。  
  
-   您可以在編譯時期驗證原始的來源項目和語意，因為 BAML 式 XAML 是編譯形式的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。  
  
### 當地語系化建置程序  
 開發 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式時，當地語系化的建置程序如下：  
  
-   程式開發人員負責建立並全球化 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。  程式開發人員會在專案檔中設定 `<UICulture>en-US</UICulture>`，如此在編譯應用程式時，將會產生非語言相關的主要組件。這個組件具有附屬 .resources.dll 檔案，檔案中包含所有的可當地語系化資源。另外，您還可以選擇將來源語言保留在主要組件中，因為我們的當地語系化 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 可支援從主要組件擷取的功能。  
  
-   將檔案編譯成組建後，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 會轉換成 BAML 式 XAML。  非文化特性相關的 `MyDialog.exe` 和文化特性相關 \(英文\) 的 `MyDialog.resources.dll` 檔案都會釋出給使用英文的客戶。  
  
### 當地語系化工作流程  
 當地語系化流程是在建置未當地語系化的 `MyDialog.resources.dll` 檔案之後開始。  原始 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 項目和屬性會透過 <xref:System.Windows.Markup.Localizer> 底下的 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]，從 BAML 式 XAML 擷取至索引鍵\/值組中。  當地語系化人員會使用索引鍵\/值組來當地語系化應用程式。  您可以在當地語系化完成之後，利用新的值產生新的 .resource.dll。  
  
 索引鍵\/值組的索引鍵是程式開發人員放入原始 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的 `x:Uid` 值。  這些 `x:Uid` 值可以讓 [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 追蹤並合併當地語系化過程中程式開發與當地語系化之間發生的變更。  例如，如果程式開發人員在當地語系化人員開始當地語系化工作之後變更 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，您可以將這項開發變更與已經完成的當地語系化工作合併，使流失的轉譯工作減到最少。  
  
 下圖顯示以 BAML 式 XAML 為基礎的一般當地語系化工作流程。  此圖表假設程式開發人員是以英文撰寫應用程式。  程式開發人員負責建立並全球化 WPF 應用程式。  在專案檔中，程式開發人員設定了 `<UICulture>en-US</UICulture>`，因此在建置時會產生非語言相關的主要組件，以及包含所有可當地語系化資源的附屬 .resources.dll。  或者，相關人員也可以將來源語言保留在主要組件中，因為 WPF 當地語系化 API 支援從主要組件擷取的功能。  在建置程序完成之後，XAML 就會編譯成 BAML。  非文化特性相關的 MyDialog.exe.resources.dll 也會傳送給使用英文的客戶。  
  
 ![當地語系化工作流程](../../../../docs/framework/wpf/advanced/media/localizationworkflow.png "LocalizationWorkflow")  
  
 ![未當地語系化工作流程](../../../../docs/framework/wpf/advanced/media/localizationworkflow2.png "LocalizationWorkflow2")  
  
<a name="examples_of_localization"></a>   
## WPF 當地語系化範例  
 本節包含當地語系化應用程式的範例，以幫助您了解如何建置及當地語系化 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。  
  
#### 執行對話方塊範例  
 下圖顯示 \[**執行**\] 對話方塊範例的輸出。  
  
 **：**  
  
 ![執行對話方塊](../../../../docs/framework/wpf/advanced/media/rundialogenglish.png "RunDialogEnglish")  
  
 **德文：**  
  
 ![德文的執行對話方塊](../../../../docs/framework/wpf/advanced/media/rundialoggerman.png "RunDialogGerman")  
  
 **設計全域對話方塊**  
  
 這個範例利用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 產生 \[**執行**\] 對話方塊。  此對話方塊相當於可從 [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] \[開始\] 功能表存取的 \[**執行**\] 對話方塊。  
  
 建立全域對話方塊的部分重點如下：  
  
 **Automatic Layout**  
  
 *在 Window1.xaml 中：*  
  
 `<Window SizeToContent="WidthAndHeight">`  
  
 前述 Window 屬性會根據內容的多寡自動調整視窗大小。  這個屬性可以避免視窗切斷當地語系化之後增加的內容，也可以在當地語系化之後移除因為內容減少而產生的多餘空間。  
  
 `<Grid x:Uid="Grid_1">`  
  
 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> 屬性是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 當地系統化 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 正常運作的必要項目。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 當地語系化 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 使用這些屬性追蹤[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 的開發和當地語系化之間的變更。  <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> 屬性可讓您合併新版 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 與舊版的當地語系化 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  您可以透過在命令提示字元中執行 **msbuild \/t:updateuid RunDialog.csproj** 來加入 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> 屬性。  建議您使用這種方法加入 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> 屬性，因為手動加入通常相當費時，而且比較不精確。  您可以透過執行 **msbuild \/t:checkuid RunDialog.csproj**，檢查 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> 屬性設定是否正確。  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的結構是利用 <xref:System.Windows.Controls.Grid> 控制項建立，這個好用的控制項可以讓您使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的自動配置。  請注意，對話方塊會分成三列五欄。  沒有任何一個列或欄定義具有固定大小，因此放入各個儲存格的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 項目都可在當地語系化過程中，配合增減其大小。  
  
 [!code-xml[GlobalizationRunDialog#GridColumnDef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef)]  
  
 前兩欄 \(也就是放置 \[**開啟：**\] 標籤和 <xref:System.Windows.Controls.ComboBox> 的位置\) 佔用 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 總寬度的 10%。  
  
 [!code-xml[GlobalizationRunDialog#GridColumnDef2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef2)]  
  
 請注意，此範例使用 <xref:System.Windows.Controls.Grid> 的共用大小功能。  後面三欄即透過將本身放置在相同的 <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> 來利用這項功能。  如同您對屬性名稱的預期一般，它可以讓這幾欄共用相同的大小。  因此，當 "Browse…" 當地語系化成較長的字串 "Durchsuchen…" 時，所有按鈕的寬度都會增加，而不會出現 \[OK\] 按鈕和 \[Durchsuchen…\] 按鈕兩者大小不成比例 \(前者小後者大\) 的情況。  
  
 **Xml:lang**  
  
 `Xml:lang="en-US"`  
  
 請注意放置在 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 之根項目 \(Root Element\) 的 [XAML 中的 xml:lang 處理](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md)。  這個屬性描述指定之項目及其子系的文化特性。  這個值可供 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的幾項功能使用，而且在當地語系化過程中應該經過適當的變更。  這個值會變更用於斷字及拼字檢查的語言字典。  它也會影響數字的顯示以及字型後援系統如何選擇使用的字型。  此外，這個屬性還會影響數字的顯示方式，以及以複雜指令碼撰寫之文字的外形。  預設值為 "en\-US"。  
  
 **Building a Satellite Resource Assembly**  
  
 *在 .csproj 中：*  
  
 `<UICulture>en-US</UICulture>`  
  
 請注意加入的 `UICulture` 值。  當這個屬性設定為有效的 <xref:System.Globalization.CultureInfo> 值 \(例如 en\-US 時\)，建置專案後將會產生內含所有可當地語系化資源的附屬組件。  
  
 `<Resource Include="RunIcon.JPG">`  
  
 `<Localizable>False</Localizable>`  
  
 `</Resource>`  
  
 `RunIcon.JPG` 不需要當地語系化，因為它在所有文化特性中顯示的外觀應該相同。  另外，`Localizable` 會設定為 `false`，以便保留在非語言相關的主要組件中，而不是附屬組件中。  所有非相容資源的預設值都會將 `Localizable` 設定為 `true`。  
  
 **當地語系化執行對話方塊**  
  
 **Parse**  
  
 在建置應用程式之後，當地語系化的第一個步驟是剖析附屬組件內的可當地語系化資源。  在本主題中，請使用可在 [LocBaml 工具範例](http://go.microsoft.com/fwlink/?LinkID=160016) \(英文\) 中找到的 LocBaml 範例工具。  請注意，LocBaml 只是一套範例工具，目的是要幫助您根據自己所採用的當地語系化程序，開始著手建置適合的當地語系化工具。  請利用 LocBaml 執行下列命令進行剖析：**LocBaml \/parse RunDialog.resources.dll \/out:**，藉以產生 "RunDialog.resources.dll.CSV" 檔案。  
  
 **Localize**  
  
 使用支援 Unicode 的慣用 CSV 編輯器來編輯這個檔案。  篩選掉當地語系化分類屬於「無」的所有項目。  您應該會看到下列項目：  
  
||||  
|-|-|-|  
|資源索引鍵|當地語系化分類|值|  
|Button\_1:System.Windows.Controls.Button.$Content|Button|OK|  
|Button\_2:System.Windows.Controls.Button.$Content|Button|Cancel|  
|Button\_3:System.Windows.Controls.Button.$Content|Button|Browse...|  
|ComboBox\_1:System.Windows.Controls.ComboBox.$Content|ComboBox||  
|TextBlock\_1:System.Windows.Controls.TextBlock.$Content|文字|Type the name of a program, folder, document, or Internet resource, and Windows will open it for you.|  
|TextBlock\_2:System.Windows.Controls.TextBlock.$Content|文字|Open:|  
|Window\_1:System.Windows.Window.Title|標題|回合|  
  
 將應用程式當地語系化為德文需要進行下列翻譯：  
  
||||  
|-|-|-|  
|資源索引鍵|當地語系化分類|值|  
|Button\_1:System.Windows.Controls.Button.$Content|Button|OK|  
|Button\_2:System.Windows.Controls.Button.$Content|Button|Abbrechen|  
|Button\_3:System.Windows.Controls.Button.$Content|Button|Durchsuchen…|  
|ComboBox\_1:System.Windows.Controls.ComboBox.$Content|ComboBox||  
|TextBlock\_1:System.Windows.Controls.TextBlock.$Content|文字|Geben Sie den Namen eines Programms, Ordners, Dokuments oder einer Internetresource an.|  
|TextBlock\_2:System.Windows.Controls.TextBlock.$Content|文字|Öffnen:|  
|Window\_1:System.Windows.Window.Title|標題|回合|  
  
 **Generate**  
  
 當地語系化的最後一個步驟包括建立新的當地語系化附屬組件。  您可以使用下列 LocBaml 命令完成這項工作：  
  
 **LocBaml.exe \/generate RunDialog.resources.dll \/trans:RunDialog.resources.dll.CSV \/out: .  \/cul:de\-DE**  
  
 在德文版 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 中，如果這個 resources.dll 放在主要組件旁邊的 de\-DE 資料夾中，系統會自動載入這項資源，而非 en\-US 資料夾中的資源。  如果您沒有德文版的 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 可以測試，請將文化特性設定為您所使用之 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 的任何文化特性 \(例如   en\-US\)，然後取代原始的 resources.dll。  
  
 **Satellite Resource Loading**  
  
|MyDialog.exe|en\-US\\MyDialog.resources.dll|de\-DE\\MyDialog.resources.dll|  
|------------------|------------------------------------|------------------------------------|  
|程式碼|原始英文 BAML|當地語系化 BAML|  
|非文化特性相關資源|其他英文資源|當地語系化為德文的其他資源|  
  
 .NET Framework 會根據應用程式的 `Thread.CurrentThread.CurrentUICulture`，自動選擇所要載入的附屬資源組件。  這個文化特性預設為 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 作業系統的文化特性。  因此，如果您使用德文版 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]，de\-DE\\MyDialog.resources.dll 就會載入，而如果使用的是英文版 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]，則會載入 en\-US\\MyDialog.resources.dll。  您可以在專案的 AssemblyInfo.\* 中指定 NeutralResourcesLanguage，以設定應用程式的後援資源。  例如，如果指定：  
  
 `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]`  
  
 則當 de\-DE\\MyDialog.resources.dll 或 de\\MyDialog.resources.dll 都無法使用時，便會在德文版 Windows 中使用 en\-US\\MyDialog.resources.dll。  
  
### Microsoft 沙烏地阿拉伯首頁  
 下列圖形顯示英文和阿拉伯文首頁。  如需產生這些圖形的完整範例，請參閱[全球化首頁範例](http://go.microsoft.com/fwlink/?LinkID=159990) \(英文\)。  
  
 **：**  
  
 ![英文頁面](../../../../docs/framework/wpf/advanced/media/englishhomepage.png "EnglishHomepage")  
  
 **阿拉伯文：**  
  
 ![阿拉伯語頁面](../../../../docs/framework/wpf/advanced/media/arabichomepage.png "ArabicHomepage")  
  
### 設計全球化 Microsoft 首頁  
 這個模擬的 Microsoft 沙烏地阿拉伯網站說明了針對 RightToLeft 語言所提供的全球化功能。  諸如希伯來文和阿拉伯文等語言的閱讀方向都是由右到左，因此 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的配置通常必須採用與英文等由左至右語言相當不同的方式來安排。  將由左至右語言當地語系化成由右至左語言 \(或相反\) 可能相當困難。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的設計大幅簡化了這種當地語系化作業。  
  
 **FlowDirection**  
  
 *Homepage.xaml:*  
  
 [!code-xml[GlobalizationHomepage#Homepage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#homepage)]  
  
 請留意 <xref:System.Windows.Controls.Page> 上的 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 屬性。  將這個屬性變更為 <xref:System.Windows.FlowDirection>，會變更 <xref:System.Windows.Controls.Page> 及其子項目的 <xref:System.Windows.FrameworkElement.FlowDirection%2A>，以翻轉此 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的配置，使其變成阿拉伯文使用者習慣的由右至左配置。  使用者可以透過在任何項目上指定明確 <xref:System.Windows.FrameworkElement.FlowDirection%2A>，以覆寫繼承 \(Inheritance\) 行為。  您可在任何 <xref:System.Windows.FrameworkElement> 或具有 <xref:System.Windows.FlowDirection> 隱含值的文件相關項目中找到 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 屬性。  
  
 請注意，當根 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 變更時，甚至連背景漸層筆刷也會正確翻轉。  
  
 **FlowDirection\="LeftToRight"**  
  
 ![方向由左至右](../../../../docs/framework/wpf/advanced/media/lefttoright.png "LeftToRight")  
  
 **FlowDirection\="RightToLeft"**  
  
 ![方向由右至左](../../../../docs/framework/wpf/advanced/media/righttoleft.png "RightToLeft")  
  
 **避免在面板和控制項中使用固定維度**  
  
 在完整瀏覽 Homepage.xaml 之後，您會發現除了最上層 <xref:System.Windows.Controls.DockPanel> 指定了整個 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的固定寬度和高度之外，並沒有其他固定的維度 \(Dimension\)。  請避免使用固定維度，以免裁剪長度超過來源文字的當地語系化文字。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 面板和控制項會根據其包含的內容自動調整大小。  大部分的控制項也都有最小和最大維度，您可以設定這兩個值，進一步控制維度 \(例如   MinWidth\= "20"\)。  您可以透過 <xref:System.Windows.Controls.Grid>，使用 '\*' \(例如 Width\= "0.25\*"\) 設定相對寬度和高度，  或是使用其儲存格大小共用功能。  
  
 **當地語系化註解**  
  
 佷多情況下，內容可能模稜兩可而難以翻譯。  程式開發人員或設計人員都能夠透過當地語系化註解提供額外的內容和註解。  例如，下列 Localization.Comments 釐清了 '&#124;' 字元的使用方式。  
  
 [!code-xml[GlobalizationHomepage#LocalizationComment](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcomment)]  
  
 這個註解會變成與 TextBlock\_1 的內容相關聯，而在 LocBaml 工具的案例 \(請參閱 [將應用程式當地語系化](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)\) 中，它會顯示在輸出之 .csv 檔案中 TextBlock\_1 列的第 6 欄：  
  
|||||||  
|-|-|-|-|-|-|  
|資源索引鍵|分類|可讀取|可修改|註解|值|  
|TextBlock\_1:System.Windows.Controls.TextBlock.$Content|文字|TRUE|TRUE|這個字元是做為裝飾規則使用。|&#124;|  
  
 註解可以放在任何項目的內容或屬性上，使用的語法如下：  
  
 [!code-xml[GlobalizationHomepage#LocalizationCommentsProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcommentsprop)]  
  
 **當地語系化屬性**  
  
 程式開發人員或當地語系化管理人員通常必須控制當地語系化人員可以讀取及修改的內容。  例如，您可能不希望當地語系化人員翻譯公司名稱或法律用語。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供多種屬性 \(Attribute\)，供您設定當地語系化工具可用來鎖定、隱藏或排序項目之項目內容或屬性 \(Property\) 可否讀取、可否修改以及其分類。  如需詳細資訊，請參閱 <xref:System.Windows.Localization.Attributes%2A>。  在這個範例中，LocBaml 工具只會輸出這些屬性 \(Attribute\) 的值。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項都有這些屬性的預設值，但是您可以覆寫這些預設值。  例如，下列範例會覆寫 `TextBlock_1` 的預設當地語系化屬性，並將內容設定為可供當地語系化人員讀取但不可修改。  
  
 [!code-xml[LocalizationComAtt#LocalizationAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributes)]  
  
 除了可否讀取和可否修改的屬性 \(Attribute\) 之外，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 還提供常見 UI 分類 \(<xref:System.Windows.LocalizationCategory>\) 的列舉型別，可用來提供更多內容給當地語系化人員。  您也可以在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中覆寫平台控制項的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 預設分類：  
  
 [!code-xml[LocalizationComAtt#LocalizationAttributesOverridden](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributesoverridden)]  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供的預設當地語系化屬性也可以透過程式碼覆寫，因此您可以正確設定自訂控制項的適當預設值。  例如：  
  
 `[Localizability(Readability = Readability.Readable, Modifiability=Modifiability.Unmodifiable, LocalizationCategory.None)]`  
  
 `public class CorporateLogo: TextBlock`  
  
 `{`  
  
 `…`  
  
 `..`  
  
 `.`  
  
 `}`  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中設定的個別執行個體屬性，其優先順序高於在自訂控制項上以程式碼設定的值。  如需屬性和註解的詳細資訊，請參閱[當地語系化屬性和註解](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md)。  
  
 **字型後援和複合字型**  
  
 如果指定的字型不支援特定字碼指標範圍，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 將會使用 Windows\\Fonts 目錄中的 Global User Interface.compositefont，自動回復成支援該字碼指標範圍的後援字型。  複合字型的運作方式和其他任何字型完全相同，而且您可以透過設定項目的 FontFamily \(例如   FontFamily\= "Global User Interface"\) 明確使用複合字型。  您可以建立自己的複合字型，並指定用於特定字碼指標範圍和語言的字型，藉以指定您自己的字型後援設定。  
  
 如需複合字型的詳細資訊，請參閱 <xref:System.Windows.Media.FontFamily>。  
  
 **當地語系化 Microsoft 首頁**  
  
 您可以遵照「執行對話方塊範例」的相同步驟來當地語系化這個應用程式。  您可以在[全球化首頁範例](http://go.microsoft.com/fwlink/?LinkID=159990) \(英文\) 中找到阿拉伯文適用的當地語系化 .csv 檔案。