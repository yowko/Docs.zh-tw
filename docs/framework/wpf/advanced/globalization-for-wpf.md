---
title: "WPF 的全球化 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "全球化"
  - "國際化使用者介面, XAML"
  - "XAML, 全球化"
  - "XAML, 國際化使用者介面"
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
caps.latest.revision: 35
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 31
---
# WPF 的全球化
本主題介紹當您針對全球市場撰寫 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式時應該注意的問題。  全球化程式設計項目是定義於 [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] 的 `System.Globalization` 中。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="xaml_globalization"></a>   
## XAML 全球化  
 [!INCLUDE[TLA#tla_xaml#initcap](../../../../includes/tlasharptla-xamlsharpinitcap-md.md)] 是以 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 為基礎，因此可以利用 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 規格中定義的全球化支援。  下列章節說明一些您應該要知道的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 功能。  
  
<a name="char_reference"></a>   
### 字元參考  
 字元參考會以十進位或十六進位數字代表特定 [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] 字元。  下列範例顯示十進位字元參考。  
  
```  
Ϩ  
```  
  
 下列範例顯示十六進位字元參考。  請注意在十六進位數字前面有個 **x**。  
  
```  
Ϩ  
```  
  
<a name="encoding"></a>   
### 編碼方式  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 支援的編碼方式有 [!INCLUDE[TLA#tla_ascii](../../../../includes/tlasharptla-ascii-md.md)]、[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] UTF\-16 和 UTF\-8。  編碼方式陳述式 \(Statement\) 位於 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 文件的開頭。  如果編碼方式屬性 \(Attribute\) 不存在，而且沒有位元組順序，則剖析器 \(Parser\) 會預設為 UTF\-8。  UTF\-8 和 UTF\-16 是慣用編碼方式。  不支援 UTF\-7。  下列範例示範如何在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案中指定 UTF\-8 編碼方式。  
  
```  
?xml encoding="UTF-8"?  
```  
  
<a name="lang_attrib"></a>   
### 語言屬性  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 會使用 [xml:lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) 代表項目的語言屬性 \(Attribute\)。  若要利用 <xref:System.Globalization.CultureInfo> 類別，語言屬性 \(Attribute\) 值必須是 <xref:System.Globalization.CultureInfo> 預先定義的其中一個文化特性 \(Culture\) 名稱。  [xml:lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) 在項目樹狀目錄中是可繼承的項目 \(依照 XML 規則，但是不一定是因為相依性屬性 \(Property\) 繼承\)，如果沒有明確指派值，則預設值為空字串。  
  
 語言屬性在指定方言時十分有用。  例如，法國、魁北克、比利時和瑞典地區的法文無論是在拼字、詞彙和發音上都不同。  此外，中文、日文和韓文雖然在 [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] 中會共用字碼指標，但是它們的表意圖案十分不同，使用的字型也完全不同。  
  
 下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 範例會使用 `fr-CA` 語言屬性 \(Attribute\) 指定加拿大法文。  
  
```  
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>  
```  
  
<a name="unicode"></a>   
### Unicode  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 支援所有 [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] 功能，包括 Surrogate。  只要字元集 \(Character Set\) 可以對應至 [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]，就能受到支援。  例如，GB18030 中有些字元對應至 Chinese、Japanese 和 Korean \(CFK\) 擴充 A 和 B 以及 Surrogate 字組，因此完全受到支援。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式可以使用 <xref:System.Globalization.StringInfo> 來操作字串，而不需要知道字串中是否有 Surrogate 字組或組合字元。  
  
<a name="design_intl_ui_with_xaml"></a>   
## 使用 XAML 設計國際化使用者介面  
 本節說明當您在撰寫應用程式時，應該知道的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 功能。  
  
<a name="intl_text"></a>   
### 國際化文字  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 針對所有支援 [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] 的書寫系統內建了處理功能。  
  
 以下列出目前支援的文字系統：  
  
-   阿拉伯文  
  
-   孟加拉文  
  
-   梵文字母  
  
-   斯拉夫文  
  
-   希臘文  
  
-   古吉拉特文  
  
-   果魯穆奇文字  
  
-   希伯來文  
  
-   表意文字系統  
  
-   坎那達文  
  
-   寮文  
  
-   拉丁文  
  
-   馬來亞拉姆文  
  
-   蒙古文  
  
-   歐迪亞文  
  
-   敘利亞文  
  
-   坦米爾文  
  
-   特拉古文  
  
-   塔安那文  
  
-   泰文\*  
  
-   藏文  
  
 \*這個版本可支援顯示和編輯泰文文字，但是不支援斷字功能。  
  
 下列是目前不支援的文字系統：  
  
-   高棉文  
  
-   舊韓文  
  
-   緬甸文  
  
-   錫蘭文  
  
 所有的書寫系統引擎都支援 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型。  [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] 字型可以包含 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] 版面配置表格，供字型建立者設計更好、更優美的國際化印刷樣式字型。  [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] 字型版面配置表格含有圖像 \(Glyph\) 替換、圖像位置、對齊和基準位置等資訊，可讓文字處理應用程式改善文字配置。  
  
 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] 字型可讓您使用 [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] 編碼方式處理大型圖像集。  這類編碼方式可以提供廣泛的國際化支援，以及各種印刷樣式圖像相似字。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 文字呈現是由支援獨立解析的 [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] 子像素技術所提供。  這樣可大幅改善可讀性，並且支援對所有文字系統使用高品質的字型，來建立如同雜誌一般精美的文件。  
  
<a name="intl_layout"></a>   
### 國際化配置  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供一種非常便利的方式來支援水平、雙向和垂直的版面配置。  在 Presentation Framework 中，<xref:System.Windows.FrameworkElement.FlowDirection%2A> 屬性 \(Property\) 可以用來定義版面配置。  行文方向模式有：  
  
-   *LeftToRight* \- 適用於拉丁文、東亞文字等等的水平版面配置。  
  
-   *RightToLeft* \- 適用於阿拉伯文、希伯來文等的雙向版面配置。  
  
<a name="developing_localizable_apps"></a>   
## 開發可當地語系化的應用程式  
 當您針對全球消費市場撰寫應用程式時，請記住，應用程式必須是可當地語系化的。  下列主題會指出需要考量的事項。  
  
<a name="mui"></a>   
### 多語系使用者介面  
 多語系使用者介面 \(MUI\) 是一項能將 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] 從一個語言轉換至另一個語言的 [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] 支援。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式會使用組件模型來支援 MUI。  一個應用程式中會同時包含語言中性的組件以及語言相關的附屬資源組件。  進入點則是主要組件內的 Managed .EXE。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 資源載入器會利用 [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)] 的資源管理員來支援資源查閱和資源後援。  多語系附屬組件會使用同一個主要組件。  載入的資源組件取決於目前執行緒的 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A>。  
  
<a name="localizable_ui"></a>   
### 可當地語系化的使用者介面  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式會使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 定義 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 可讓開發人員利用一組屬性 \(Property\) 和邏輯來建立物件階層。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的主要用途是開發 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式，但也可以用來指定任何 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 物件的階層。  大多數的開發人員都會 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 指定其應用程式的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，並且使用 [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] 等程式設計語言來做出對使用者互動的回應。  
  
 從資源的觀點來看，設計來描述依語言而定之 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案是一種資源項目，因此其最終散發格式必須是可當地語系化的，以便支援國際化語言。  因為 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 無法處理事件，所以許多 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 應用程式都會包含可處理事件的程式碼區塊。  如需詳細資訊，請參閱 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)。  當 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案被語彙基元化成 BAML 式 XAML 時，程式碼會被拿掉並編譯成不同的二進位碼檔案。BAML 式 XAML 的檔案、影像和其他類型的 Managed 資源物件會內嵌在附屬資源組件中 \(如果需要進行當地語系化\)，或內嵌在主要組建中 \(如果不需要進行當地語系化\)。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式支援所有的 [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)] [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 資源，包括字串資料表 \(String Table\)、影像等等。  
  
<a name="building_localizable_apps"></a>   
### 建置可當地語系化的應用程式  
 當地語系化的意義是要讓 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 適應不同的文化特性。  若要讓 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式變成可供當地語系化，開發人員必須將所有可當地語系化的資源建置至一個資源組件中。  這個資源組件會被譯為不同的語言，而程式碼後置 \(Code\-Behind\) 會使用資源管理 [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] 進行載入。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式需要的其中一個檔案是專案檔 \(.proj\)。  所有您在應用程式中使用的資源都應該要包含在專案檔中。  下列 .csproj 檔案的範例顯示如何進行這項操作。  
  
```  
<Resource Include="data\picture1.jpg"/>  
<EmbeddedResource Include="data\stringtable.en-US.restext"/>  
```  
  
 若要在應用程式中使用資源，請具現化 \(Instantiate\) <xref:System.Resources.ResourceManager>，然後載入想要使用的資源。  下列範例示範如何進行這項操作。  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]  
  
<a name="using_clickonce"></a>   
## 對當地語系化的應用程式使用 ClickOnce  
 ClickOnce 是一項隨 [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] 提供的新式 Windows Form 部署技術。  它可用於應用程式安裝以及將 Web 應用程式升級。  當透過 ClickOnce 部署的應用程式已當地語系化時，就只能以當地語系化的文化特性檢視該應用程式。  例如，如果部署的應用程式已當地語系化成日文，則只能在日文版的 [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] 而不是英文版的 [!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)] 中檢視該應用程式。  這樣會有個問題，那就是日文版使用者經常會執行英文版的 [!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)]。  
  
 這個問題的解決方案就是設定中性的語言後援屬性 \(Attribute\)。  應用程式開發人員可以選擇性的移除主要組件中的資源，然後指定這些資源可以在特定文化特性的對應附屬組件中找到。  若要控制這個程序，請使用 <xref:System.Resources.NeutralResourcesLanguageAttribute>。  <xref:System.Resources.NeutralResourcesLanguageAttribute> 類別的建構函式具有兩個簽章 \(Signature\)，其中一個會使用 <xref:System.Resources.UltimateResourceFallbackLocation> 參數指定 <xref:System.Resources.ResourceManager> 應從中抽取後援資源的位置：主要組件或附屬組件。  下列範例顯示如何使用這個屬性 \(Attribute\)。  對於最終後援位置，這個程式碼會促使 <xref:System.Resources.ResourceManager> 在目前正在執行的組件之目錄的 "de" 子目錄中尋找資源。  
  
```  
[assembly: NeutralResourcesLanguageAttribute(  
    "de" , UltimateResourceFallbackLocation.Satellite)]  
  
```  
  
## 請參閱  
 [WPF 全球化和當地語系化概觀](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)