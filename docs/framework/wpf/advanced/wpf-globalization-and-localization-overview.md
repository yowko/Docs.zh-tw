---
title: "WPF 全球化和當地語系化概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- globalization [WPF], about globalization
- localization [WPF], about localization
ms.assetid: 56e5a5c8-6c96-4d19-b8e1-a5be1dc564af
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f2bc9021ca376b7b27f74efed6866a907b480ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="wpf-globalization-and-localization-overview"></a>WPF 全球化和當地語系化概觀
當您限制只有一種語言可以使用您的產品時，就是將潛在客戶群限制為全世界 65 億人口的一小部分。 如果您想要全球對象都可以使用應用程式，則具成本效益的產品當地語系化是更多客戶可以使用的一種最佳且最經濟的方法。  
  
 本概觀介紹全球化和當地語系化的[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]。 全球化是在多個位置執行之應用程式的設計和開發。 例如，全球化支援不同文化特性中使用者的當地語系化使用者介面和地區資料。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供全球化的設計功能，包括自動版面配置、 附屬組件，與當地語系化的屬性和註解。
  
 當地語系化會將應用程式資源翻譯為應用程式所支援之特定文化特性的當地語系化版本。 當您將當地語系化中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，使用中的 Api<xref:System.Windows.Markup.Localizer>命名空間。 這些應用程式開發介面電源[LocBaml 工具範例](http://go.microsoft.com/fwlink/?LinkID=160016)命令列工具。 如需如何建立及使用 LocBaml 資訊，請參閱[當地語系化應用程式](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)。    
  
## <a name="best-practices-for-globalization-and-localization-in-wpf"></a>WPF 中的全球化和當地語系化最佳做法  
 您可以進行大部分的內建的全球化和當地語系化功能[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]遵循 UI 設計和此章節提供當地語系化相關的提示。  
  
### <a name="best-practices-for-wpf-ui-design"></a>WPF UI 設計最佳做法  
 當您設計[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– 基礎[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，請考慮實作這些最佳作法：  
  
-   撰寫您[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; 避免建立[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]程式碼中。 當您建立您[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您將它公開透過內建當地語系化應用程式開發介面。  
  
-   請避免使用絕對位置和固定的大小來配置內容。請改用相對或自動調整大小。
  
    -   使用<xref:System.Windows.Window.SizeToContent%2A>; 並將寬度和高度設定為保留`Auto`。  
  
    -   請避免使用<xref:System.Windows.Controls.Canvas>配置[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]s。  
  
    -   使用<xref:System.Windows.Controls.Grid>及其大小共用功能。  
  
-   因為當地語系化文字通常需要更多空間，所以請在邊界提供額外空間。 額外空間可放置可能突出的字元。  
  
-   啟用<xref:System.Windows.Controls.TextBlock.TextWrapping%2A>上<xref:System.Windows.Controls.TextBlock>避免裁剪。
  
-   設定**xml: lang**屬性。 這個屬性所描述的文化特性特定的項目和其子項目。 這個屬性的值變更數個功能中的行為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。 例如，它會變更斷字、拼字檢查、數字替代、複雜指令碼形成和字型遞補的行為。 請參閱[WPF 的全球化](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)如需有關設定[xml: lang 處理在 XAML 中](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md)。  
  
-   建立自訂的複合字型，以取得不同語言所用字型的較佳的控制項。 根據預設，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用 GlobalUserInterface.composite 字型 Windows\Fonts 目錄中的。  
  
-   當您建立瀏覽應用程式可能會當地語系化的文化特性中的格式，呈現文字由右至左，明確地設定<xref:System.Windows.FlowDirection>每一頁，以確保頁面不會繼承<xref:System.Windows.FlowDirection>從<xref:System.Windows.Navigation.NavigationWindow>。  
  
-   當您建立外部瀏覽器所裝載的獨立瀏覽應用程式時，設定<xref:System.Windows.Application.StartupUri%2A>初始應用程式<xref:System.Windows.Navigation.NavigationWindow>而不是到網頁 (例如， `<Application StartupUri="NavigationWindow.xaml">`)。 此設計可讓您變更<xref:System.Windows.FlowDirection>的視窗，並導覽列。 如需詳細資訊和範例，請參閱[全球化首頁範例](http://go.microsoft.com/fwlink/?LinkID=159990)。  
  
### <a name="best-practices-for-wpf-localization"></a>WPF 當地語系化最佳做法  
 當您將當地語系化[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– 應用程式，請考慮實作這些最佳作法：  
  
-   用於當地語系化註解的當地語系化人員提供額外的內容。  
  
-   用於當地語系化屬性控制而不是選擇性地省略當地語系化<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>項目上的屬性。 請參閱[當地語系化屬性和註解](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md)如需詳細資訊。  
  
-   使用**msbuild /t:updateuid**和**/t:checkuid**新增並檢查<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>屬性中的您[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 使用<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>來追蹤開發和當地語系化之間變更的屬性。 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>屬性可協助您將新的開發變更的當地語系化。 如果您手動新增<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>屬性[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，此工作是通常繁瑣且較不精確。  
  
    -   無法編輯或變更<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>之後開始當地語系化的屬性。  
  
    -   請勿使用重複<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>屬性 （當您使用複製和貼上 命令時，請記住這個提示）。  
  
    -   設定`UltimateResourceFallback`中指定適當的語言進行遞補 AssemblyInfo.* 位置 (例如， `[assembly: NeutralResourcesLanguage("en-US",   UltimateResourceFallbackLocation.Satellite)]`)。  
  
         如果您決定要包含在主要組件中的原始碼語言，藉由略過`<UICulture>`專案檔中標記中，設定`UltimateResourceFallback`主組件，而不是附屬項目位置 (例如， `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.MainAssembly)]`)。  
  
<a name="workflow_to_localize"></a>   
## <a name="localize-a-wpf-application"></a>將 WPF 應用程式當地語系化  
 當您將當地語系化[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式中，有數個選項。 例如，您的應用程式中繫結可當地語系化的資源[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]檔案，可當地語系化的文字儲存在 resx 資料表中，或使用您當地語系化[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案。 本章節描述使用 BAML 形式的 XAML，有數個優點的當地語系化工作流程：  
  
-   建置之後，即可進行當地語系化。  
  
-   您可以使用當地語系化從 BAML 形式之 XAML 的舊版本更新為 BAML 形式之 XAML 的新版本，以在開發的同時進行當地語系化。  
  
-   您可以驗證原始來源項目及語意在編譯時期因為 BAML 形式的 XAML 的編譯的形式[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。  
  
### <a name="localization-build-process"></a>當地語系化建置程序  
 當您開發[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式，當地語系化的建置程序如下所示：  
  
-   開發人員建立和全球化[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。 在專案檔中的開發人員集`<UICulture>en-US</UICulture>`，讓應用程式編譯時，會產生非語言相關的主要組件。 此組件具有包含所有可當地語系化資源的附屬 .resources.dll 檔案。 （選擇性） 您可以保留原始碼語言中主要組件因為我們當地語系化[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]支援主要組件中的擷取。  
  
-   當檔案會編譯成組建，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]轉換成 BAML 形式的 XAML。 文化特性中性`MyDialog.exe`和文化特性上相依 （英文）`MyDialog.resources.dll`檔案會發行給英語的客戶。  
  
### <a name="localization-workflow"></a>當地語系化工作流程  
 當地語系化程序開始後未當地語系化`MyDialog.resources.dll`建置檔案。 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]元素和屬性，在您的原始[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]從中使用為索引鍵 / 值組 BAML 形式的 XAML[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]下<xref:System.Windows.Markup.Localizer>。 當地語系化人員會使用鍵值組來當地語系化應用程式。 當地語系化完成之後，即可從新值產生新的 .resource.dll。  
  
 索引鍵-值組的索引鍵為`x:Uid`值放在開發人員在原始的[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 這些`x:Uid`值可讓[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]來追蹤和合併期間當地語系化開發人員和當地語系化之間發生的變更。 例如，如果開發人員變更[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]當地語系化人員開始當地語系化之後，您可以合併開發具有的變更已經完成的當地語系化工作，因此最少的轉譯工作就會遺失。  
  
 下圖顯示根據 BAML 形式之 XAML 的一般當地語系化工作流程。 此圖表會假設在英文中，開發人員撰寫應用程式。 開發人員會建立和全球化 WPF 應用程式。 在專案檔中的開發人員集`<UICulture>en-US</UICulture>`，以便建置語言中性主要組件取得產生的附屬項目.resources.dll 包含所有可當地語系化的資源。 或者，有人保持主要組件中的來源語言，因為 WPF 當地語系化 API 支援從主要組件進行擷取。 建置程序之後，XAML 會編譯到 BAML。 與文化特性無關的 MyDialog.exe.resources.dll 會傳送給英語系的客戶。  
  
 ![當地語系化工作流程](../../../../docs/framework/wpf/advanced/media/localizationworkflow.png "LocalizationWorkflow")  
  
 ![未當地語系化工作流程](../../../../docs/framework/wpf/advanced/media/localizationworkflow2.png "LocalizationWorkflow2")  
  
<a name="examples_of_localization"></a>   
## <a name="examples-of-wpf-localization"></a>WPF 當地語系化範例  
 本章節包含的當地語系化應用程式，協助您了解如何建置和當地語系化範例[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。  
  
#### <a name="run-dialog-box-example"></a>執行對話方塊範例  
 下圖顯示的輸出**執行**對話方塊範例。  
  
 **英文：**  
  
 ![執行對話方塊](../../../../docs/framework/wpf/advanced/media/rundialogenglish.PNG "RunDialogEnglish")  
  
 **德文：**  
  
 ![德文的執行對話方塊](../../../../docs/framework/wpf/advanced/media/rundialoggerman.PNG "RunDialogGerman")  
  
 **設計全域執行對話方塊**  
  
 這個範例會產生**執行**對話方塊使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]和[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 這個對話方塊就相當於**執行**對話方塊可從[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]開始 功能表。  
  
 建立全域對話方塊的一些重點如下︰  
  
 **自動版面配置**  
  
 *在 Window1.xaml 中：*  
  
 `<Window SizeToContent="WidthAndHeight">`  
  
 前一個 Window 屬性會根據內容的大小來自動調整視窗大小。 此屬性會防止視窗中在當地語系化因大小增加而裁切內容；內容在當地語系化後大小減少時，它也會移除不必要的空間。  
  
 `<Grid x:Uid="Grid_1">`  
  
 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>為了讓需要屬性時[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]當地語系化[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]正常運作。  
  
 它們由[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]當地語系化[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]變更追蹤之間的開發和當地語系化的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]。 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>屬性可讓您合併較新版的[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]與較舊的當地語系化[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 您將加入<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>屬性執行**msbuild /t:updateuid RunDialog.csproj**命令殼層。 這是建議的方法加入的<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>屬性，所以手動加入它們通常相當耗時而且需要較不精確。 您可以檢查<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>屬性均已正確設定執行**msbuild /t:checkuid RunDialog.csproj**。  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]使用結構化<xref:System.Windows.Controls.Grid>控制項，這是利用自動配置的有用控制項中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。 請注意，對話方塊分成三個資料列和五個資料行。 不是其中一個資料列和資料行定義具有固定的大小。因此，[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]位於每個資料格中的項目可以調整增加和減少大小當地語系化過程。  
  
 [!code-xaml[GlobalizationRunDialog#GridColumnDef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef)]  
  
 前兩個資料行其中**開啟：**標籤和<xref:System.Windows.Controls.ComboBox>位於使用 10%的[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]總寬度。  
  
 [!code-xaml[GlobalizationRunDialog#GridColumnDef2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef2)]  
  
 請注意，此範例會使用的共用調整大小功能<xref:System.Windows.Controls.Grid>。 最後三個資料行本身放置在同一個充分利用這<xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A>。 因為其中一個預期來自屬性名稱，所以這可讓資料行共用相同的大小。 因此，如果 "Browse…" 當地語系化為較長的字串 "Durchsuchen…"，則所有按鈕的寬度都會增加，而不會有較小的 "OK" 按鈕，以及顯得特別大的 "Durchsuchen…" 按鈕。  
  
 **Xml:lang**  
  
 `Xml:lang="en-US"`  
  
 請注意[xml: lang 處理在 XAML 中](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md)放在根項目[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 此屬性描述所指定項目的文化特性和其子項目。 這個值由數個功能中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]且適當地當地語系化過程中變更。 此值可變更使用何種語言字典來進行斷字和拼字檢查。 它也會影響顯示的位數，以及字型遞補系統如何選取要使用的字型。 最後，此屬性會影響數字顯示方式，以及使用複雜指令碼所撰寫之文字的形成方式。 預設值是 "en-US"。  
  
 **建置附屬資源組件**  
  
 *在 .csproj 中：*  
  
 `<UICulture>en-US</UICulture>`  
  
 請注意新增`UICulture`值。 這設定為有效<xref:System.Globalization.CultureInfo>值，例如 EN-US，建置專案將會在它產生附屬組件與所有可當地語系化的資源。  
  
 `<Resource Include="RunIcon.JPG">`  
  
 `<Localizable>False</Localizable>`  
  
 `</Resource>`  
  
 `RunIcon.JPG`不需要當地語系化，因為它應該會出現相同的所有文化特性。 `Localizable`設定為`false`，使其仍然語言中性主要組件中而不是附屬組件。 所有 noncompilable 資源的預設值是`Localizable`設`true`。  
  
 **將執行對話方塊當地語系化**  
  
 **剖析**  
  
 建置應用程式之後，將它當地語系化的第一個步驟是剖析附屬組件的可當地語系化資源。 本主題的用途，使用範例 LocBaml 工具，可以在找到[LocBaml 工具範例](http://go.microsoft.com/fwlink/?LinkID=160016)。 請注意，LocBaml 只是一種範例工具，旨在協助您開始建置符合當地語系化程序的當地語系化工具。 使用 LocBaml，執行下列命令以剖析： **LocBaml/剖析 RunDialog.resources.dll /out:**來產生 「 RunDialog.resources.dll.CSV"檔案。  
  
 **當地語系化**  
  
 使用支援 Unicode 的慣用 CSV 編輯器，才能編輯這個檔案。 篩選出當地語系化分類為 "None" 的所有項目。 您應該會看到下列項目：  
  
|資源索引鍵|當地語系化分類|值|  
|-|-|-| 
|Button_1:System.Windows.Controls.Button.$Content|按鈕|確定|  
|Button_2:System.Windows.Controls.Button.$Content|按鈕|取消|  
|Button_3:System.Windows.Controls.Button.$Content|按鈕|瀏覽...|  
|ComboBox_1:System.Windows.Controls.ComboBox.$Content|ComboBox||  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Text|輸入程式、資料夾、文件或網際網路資源的名稱，Windows 會自動開啟。|  
|TextBlock_2:System.Windows.Controls.TextBlock.$Content|Text|開啟：|  
|Window_1:System.Windows.Window.Title|標題|執行|  
  
 將應用程式當地語系化為德文需要下列翻譯︰  
  
|資源索引鍵|當地語系化分類|值|  
|-|-|-| 
|Button_1:System.Windows.Controls.Button.$Content|按鈕|確定|  
|Button_2:System.Windows.Controls.Button.$Content|按鈕|Abbrechen|  
|Button_3:System.Windows.Controls.Button.$Content|按鈕|Durchsuchen…|  
|ComboBox_1:System.Windows.Controls.ComboBox.$Content|ComboBox||  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Text|Geben Sie den Namen eines Programms, Ordners, Dokuments oder einer Internetresource an.|  
|TextBlock_2:System.Windows.Controls.TextBlock.$Content|Text|Öffnen:|  
|Window_1:System.Windows.Window.Title|標題|執行|  
  
 **產生**  
  
 當地語系化的最後一個步驟包括建立新的當地語系化附屬組件。 使用下列 LocBaml 命令，即可完成這項作業：  
  
 **LocBaml.exe /generate RunDialog.resources.dll /trans:RunDialog.resources.dll.CSV /out: . /cul:de-DE**  
  
 在德文[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]，如果此.resources.dll 放在 DE-DE 資料夾旁邊的主要組件，這項資源會自動載入而非 EN-US 資料夾中。 如果您沒有德文版的[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]若要測試這種情況，設定文化特性的任何文化特性[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]您使用 (也就是 EN-US)，並取代原始.resources.dll。  
  
 **附屬資源載入**  
  
|MyDialog.exe|en-US\MyDialog.resources.dll|de-DE\MyDialog.resources.dll|  
|------------------|------------------------------------|------------------------------------|  
|程式碼|附屬資源 BAML|當地語系化 BAML|  
|文化特性中性資源|英文的其他資源|當地語系化為德文的其他資源|  
  
 .NET framework 會自動選擇要載入根據應用程式的哪些附屬資源組件`Thread.CurrentThread.CurrentUICulture`。 預設值的文化特性為您[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]OS。 因此，如果您使用德文[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]，de-DE\MyDialog.resources.dll 載入，如果您使用英文[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]，en-US\MyDialog.resources.dll 載入。 您可以在專案的 AssemblyInfo.* 中指定 NeutralResourcesLanguage，以設定應用程式的最終後援資源。 例如，如果您指定：  
  
 `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]`  
  
 則在無法使用 de-DE\MyDialog.resources.dll 或 de\MyDialog.resources.dll 時，會搭配使用 en-US\MyDialog.resources.dll 與德文 Windows。  
  
### <a name="microsoft-saudi-arabia-homepage"></a>Microsoft Saudi Arabia 首頁  
 下圖顯示英文和阿拉伯文首頁。 完整的範例會產生這些圖形，請參閱[全球化首頁範例](http://go.microsoft.com/fwlink/?LinkID=159990)。  
  
 **英文：**  
  
 ![英文頁面](../../../../docs/framework/wpf/advanced/media/englishhomepage.jpg "EnglishHomepage")  
  
 **阿拉伯文：**  
  
 ![阿拉伯文頁面](../../../../docs/framework/wpf/advanced/media/arabichomepage.jpg "ArabicHomepage")  
  
### <a name="designing-a-global-microsoft-homepage"></a>設計全域 Microsoft 首頁  
 這個模擬的 Microsoft Saudi Arabia 網站說明針對 RightToLeft 語言所提供的全球化功能。 希伯來文與阿拉伯文等語言因此具有由右至左讀取順序的版面配置[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]必須經常進行配置方式則相當不同比其在由左到右的語言，例如英文。 從由左至右語言當地語系化為由右至左語言 (反之亦然) 可能相當困難。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 設計成讓這類當地語系化更為簡單。  
  
 **FlowDirection**  
  
 *Homepage.xaml：*  
  
 [!code-xaml[GlobalizationHomepage#Homepage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#homepage)]  
  
 請注意<xref:System.Windows.FrameworkElement.FlowDirection%2A>屬性<xref:System.Windows.Controls.Page>。 變更此屬性為<xref:System.Windows.FlowDirection.RightToLeft>會變更<xref:System.Windows.FrameworkElement.FlowDirection%2A>的<xref:System.Windows.Controls.Page>及其子系項目，讓這個配置[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]翻轉變成由右至左，如阿拉伯文的使用者所預期。 其中一個可以藉由指定明確覆寫繼承行為<xref:System.Windows.FrameworkElement.FlowDirection%2A>的任何項目。 <xref:System.Windows.FrameworkElement.FlowDirection%2A>屬性位於任何<xref:System.Windows.FrameworkElement>或文件相關的項目，隱含的值為<xref:System.Windows.FlowDirection.LeftToRight>。  
  
 觀察，即使背景漸層筆刷翻轉了並排顯示正確當根<xref:System.Windows.FrameworkElement.FlowDirection%2A>變更：  
  
 **FlowDirection="LeftToRight"**  
  
 ![方向由左至右](../../../../docs/framework/wpf/advanced/media/lefttoright.PNG "LeftToRight")  
  
 **FlowDirection="RightToLeft"**  
  
 ![方向由右至左](../../../../docs/framework/wpf/advanced/media/righttoleft.PNG "RightToLeft")  
  
 **避免面板和控制項使用固定維度**  
  
 透過 Homepage.xaml 看，請注意，除了用的固定的寬度和高度指定的整個[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]在上方<xref:System.Windows.Controls.DockPanel>，有沒有固定的維度。 請避免使用固定維度，防止裁剪長度超過來源文字的當地語系化文字。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 面板和控制項將會根據所含的內容來自動調整大小。 大部分控制項也有您可針對更多控制項設定的最小和最大維度 (即 MinWidth= "20")。 與<xref:System.Windows.Controls.Grid>，您也可以設定相對寬度和高度，使用 ' *' (也就是寬度 ="0.25\*") 或使用共用功能的儲存格大小。  
  
 **當地語系化註解**  
  
 在許多情況下，內容可能會模稜兩可，而不容易翻譯。 開發人員或設計人員可以透過當地語系化註解來提供額外內容和註解。 例如，下面的 Localization.Comments 釐清字元 ‘&#124;’ 的使用。  
  
 [!code-xaml[GlobalizationHomepage#LocalizationComment](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcomment)]  
  
 這個註解會變成 TextBlock_1 的內容與在 LocBaml 工具的情況下 (請參閱[當地語系化應用程式](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md))，第 6 TextBlock_1 資料列，輸出.csv 檔案中的資料行中看到它：  
  
|資源索引鍵|分類|可讀取|可修改|註解|值|  
|-|-|-|-|-|-|  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|Text|true|true|此字元是當成裝飾規則使用。|&#124;|  
  
 使用下列語法，可以放入任何項目之內容或屬性的註解︰  
  
 [!code-xaml[GlobalizationHomepage#LocalizationCommentsProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcommentsprop)]  
  
 **當地語系化屬性**  
  
 開發人員或當地語系化管理員通常需要控制當地語系化人員可以讀取和修改的內容。 例如，您可能不想要當地語系化人員翻譯公司名稱或法律用語。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供屬性，可讓您設定項目內容或屬性的可讀性、可修改性和分類，而當地語系化工具可以使用此內容或屬性來鎖定、隱藏或排序項目。 如需詳細資訊，請參閱<xref:System.Windows.Localization.Attributes%2A>。 基於此範例的目的，LocBaml 工具只會輸出這些屬性的值。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項都會有這些屬性的預設值，但您可以覆寫它們。 例如，下列範例會覆寫的預設當地語系化屬性`TextBlock_1`和設定的內容是可讀取但無法修改當地語系化。  
  
 [!code-xaml[LocalizationComAtt#LocalizationAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributes)]  
  
 除了可讀性和可修改性屬性[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供數種常見的 UI 類別 (<xref:System.Windows.LocalizationCategory>)，可以用來將多個內容提供當地語系化。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]平台控制項的預設分類會覆寫中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]以及：  
  
 [!code-xaml[LocalizationComAtt#LocalizationAttributesOverridden](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributesoverridden)]  
  
 預設當地語系化屬性 (attribute)[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供也會覆寫透過程式碼，所以您可以正確地設定自訂控制項的正確的預設值。 例如:   
  
 `[Localizability(Readability = Readability.Readable, Modifiability=Modifiability.Unmodifiable, LocalizationCategory.None)]`  
  
 `public class CorporateLogo: TextBlock`  
  
 `{`  
  
 `…`  
  
 `..`  
  
 `.`  
  
 `}`  
  
 每個執行個體的屬性中設定[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]將優先於設定中的自訂控制項程式碼的值。 如需有關屬性和註解的詳細資訊，請參閱[當地語系化屬性和註解](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md)。  
  
 **字型遞補和複合字型**  
  
 如果您指定不支援指定的字碼指標範圍的字型[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]會自動後援會使用位於 Windows\Fonts 目錄全域使用者 Interface.compositefont 的其中一個。 複合字型的運作方式就像任何其他字型一樣，而且設定項目的 FontFamily 即可明確地使用 (即 FontFamily= "Global User Interface")。 建立您自己的複合字型並指定要用於特定字碼指標範圍和語言的字型，即可指定自己的字型遞補喜好設定。  
  
 如需有關複合字型，請參閱<xref:System.Windows.Media.FontFamily>。  
  
 **將 Microsoft 首頁當地語系化**  
  
 您可以遵循「執行對話方塊」範例中的相同步驟，將此應用程式當地語系化。 當地語系化的.csv 檔案，如阿拉伯文是否可供您在[全球化首頁範例](http://go.microsoft.com/fwlink/?LinkID=159990)。
