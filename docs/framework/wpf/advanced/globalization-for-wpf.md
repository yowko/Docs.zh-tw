---
title: WPF 的全球化
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-wpf
ms.topic: article
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e6f39d40284e6212715d85fece545e653ff2e60a
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2018
---
# <a name="globalization-for-wpf"></a>WPF 的全球化
本主題將介紹問題，您應該瞭解的撰寫時[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]的全球市場的應用程式。 全球化的程式設計項目中所定義[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)]中`System.Globalization`。  
  

  
<a name="xaml_globalization"></a>   
## <a name="xaml-globalization"></a>XAML 全球化  
 [!INCLUDE[TLA#tla_xaml#initcap](../../../../includes/tlasharptla-xamlsharpinitcap-md.md)] 根據[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]，並利用中定義的全球化支援[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]規格。 下列章節描述一些[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]您應該注意的功能。  
  
<a name="char_reference"></a>   
### <a name="character-references"></a>字元參考  
字元參考可提供於特定的 UTF16 字碼單位[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]其字元表示，以十進位或十六進位。 下列範例會顯示十進位字元參考科普特文 CAPITAL LETTER 水，或 'Ϩ':

```
&#1000;
```

下列範例顯示十六進位字元參考。 請注意，它有**x**前面的十六進位數字。

```
&#x3E8;
```

<a name="encoding"></a>   
### <a name="encoding"></a>編碼  
 支援的編碼方式[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]是[!INCLUDE[TLA#tla_ascii](../../../../includes/tlasharptla-ascii-md.md)]， [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] utf-16 和 utf-8。 編碼的陳述式的開頭是[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]文件。 如果沒有任何編碼屬性，而且沒有位元組順序，則剖析器預設為 UTF-8。 UTF-8 和 UTF-16 是慣用的編碼。 不支援 UTF-7。 下列範例示範如何指定 utf-8 編碼中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案。  
  
```  
?xml encoding="UTF-8"?  
```  
  
<a name="lang_attrib"></a>   
### <a name="language-attribute"></a>語言屬性  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 使用[xml: lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md)來代表項目的 language 屬性。  若要善用<xref:System.Globalization.CultureInfo>類別，語言屬性值必須為其中一個預先定義的文化特性名稱<xref:System.Globalization.CultureInfo>。 [xml:lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) 在項目樹狀結構中為可繼承 (依 XML 規則，不一定是因為相依性屬性繼承)，如未明確指派，其預設值為空字串。  
  
 語言屬性在指定方言方面非常有用。 例如，法國、魁北克、比利時和瑞士的法文拼字、字彙和發音不同。 中文、 日文和韓文也共用程式碼中的點[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]，但在表意字元的形狀是不同，並使用完全不同的字型。  
  
 下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]範例會使用`fr-CA`指定加拿大法文語言屬性。  
  
```xml  
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>  
```  
  
<a name="unicode"></a>   
### <a name="unicode"></a>Unicode  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 支援所有[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]功能，包括 surrogate。 只要字元集可以對應至[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]，支援它。 例如，GB18030 推出可對應至中文、日文和韓文 (CFK) 延伸模組 A 和 B 及 surrogate 字組的某些字元，因此受到完整支援。 A[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式可以使用<xref:System.Globalization.StringInfo>來操作不需要了解它們是否有 surrogate 字組或組合字元的字串。  
  
<a name="design_intl_ui_with_xaml"></a>   
## <a name="designing-an-international-user-interface-with-xaml"></a>使用 XAML 設計國際化的使用者介面  
 本章節描述[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]撰寫的應用程式時，您應該考慮的功能。  
  
<a name="intl_text"></a>   
### <a name="international-text"></a>國際文字  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包含所有內建處理[!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)]支援書寫系統。  
  
 目前支援下列指令碼︰  
  
-   阿拉伯文  
  
-   孟加拉文  
  
-   梵文字母  
  
-   斯拉夫文  
  
-   希臘文  
  
-   古吉拉特文  
  
-   果魯穆奇文  
  
-   希伯來文  
  
-   表意指令碼  
  
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
  
-   泰文*  
  
-   西藏文  
  
 *本版支援泰文文字的顯示和編輯，不支援斷詞。  
  
 目前不支援下列指令碼︰  
  
-   高棉文  
  
-   古韓文  
  
-   緬甸文  
  
-   僧伽羅文  
  
 所有的書寫系統引擎支援[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字型。 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] 字型可以包括[!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]版面配置表格可讓設計更好國際和高階的印刷樣式字型的字型建立者。 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]字型版面配置表格包含圖像 （glyph） 的替代項目、 圖像定位、 理由，與基準定位，資訊啟用文字處理應用程式，以改善文字版面配置。  
  
 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] 字型則可以讓大型圖像 （glyph） 的處理設定使用[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]編碼方式。 這類編碼促進廣泛的國際支援以及各種印刷樣式字符。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 文字轉譯功能由[!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)]子像素的技術，支援解析獨立性。 這會大幅改善可讀性，並可讓您支援所有指令碼的高品質雜誌樣式文件。  
  
<a name="intl_layout"></a>   
### <a name="international-layout"></a>國際版面配置  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供非常方便的方式來支援水平、雙向和垂直版面配置。 在展示架構<xref:System.Windows.FrameworkElement.FlowDirection%2A>屬性可以用來定義配置。 流程方向模式有︰  
  
-   *LeftToRight* - 拉丁文、東亞等的水平配置。  
  
-   *RightToLeft* - 阿拉伯文、希伯來文等的雙向配置。  
  
<a name="developing_localizable_apps"></a>   
## <a name="developing-localizable-applications"></a>開發可當地語系化的應用程式  
 當您撰寫供全域使用的應用程式時，您應該記住應用程式必須是可當地語系化。 下列主題指出要考量的事項。  
  
<a name="mui"></a>   
### <a name="multilingual-user-interface"></a>多語系使用者介面  
 多語系使用者介面 (MUI) 是[!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]支援切換[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]從到另一種語言。 A[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式會使用組件模型支援 MUI。 一個應用程式包含語言中性的組件以及語言相關的附屬資源組件。 進入點是主要組件中的 Managed .EXE。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 資源載入器會利用[!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]的資源管理員，以支援資源查閱和後援。 多語言附屬組件使用相同的主要組件。 載入資源組件相依於<xref:System.Globalization.CultureInfo.CurrentUICulture%2A>目前執行緒。  
  
<a name="localizable_ui"></a>   
### <a name="localizable-user-interface"></a>可當地語系化的使用者介面  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]來定義其[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 可讓開發人員使用一組屬性和邏輯指定物件的階層。 主要用途[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]擬定[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式，但它可以用來指定的任何階層[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]物件。 大部分的開發人員使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]來指定其應用程式[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]和使用的程式語言，例如[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)]以回應使用者互動。  
  
 從資源觀點來看，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案以描述語言相依[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]資源項目，並因此其最終發佈格式必須是可當地語系化支援國際語言。 因為[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]無法處理事件許多[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]應用程式包含執行此動作的程式碼區塊。 如需詳細資訊，請參閱[XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)。 程式碼會去除並編譯成不同的二進位檔時[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案語彙基元化成 BAML 形式的 XAML。 BAML 格式的 XAML 檔案、映像和其他類型的 Managed 資源物件會內嵌到附屬資源組件中，以當地語系化為其他語言，或在不需要當地語系化時內嵌到主要組件中。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式支援所有[!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)][!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]資源包括字串資料表、 影像和其他等等。  
  
<a name="building_localizable_apps"></a>   
### <a name="building-localizable-applications"></a>組建可當地語系化的應用程式  
 當地語系化表示調整[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]至不同的文化特性。 若要讓[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式當地語系化，開發人員必須建置成資源組件的所有可當地語系化的資源。 資源組件已當地語系化成不同的語言和程式碼後置會使用資源管理[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]載入。 其中一個所需的檔案[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式是專案檔 (.proj)。 專案檔案應該包含您在應用程式中使用的所有資源。 以下的 .csproj 檔案範例示範如何執行這項工作。  
  
```xml  
<Resource Include="data\picture1.jpg"/>  
<EmbeddedResource Include="data\stringtable.en-US.restext"/>  
```  
  
 若要使用您的應用程式中的資源具現化<xref:System.Resources.ResourceManager>和載入您想要使用的資源。 下列範例示範如何進行這項操作。  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]  
  
<a name="using_clickonce"></a>   
## <a name="using-clickonce-with-localized-applications"></a>使用 ClickOnce 與當地語系化的應用程式  
 ClickOnce 是新的 Windows Form 部署技術，將獍旓[!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)]。 它能讓應用程式安裝及升級 Web 應用程式。 當地語系化使用 ClickOnce 部署的應用程式時，只能在已當地語系化的文化特性中檢視它。 例如，如果部署的應用程式當地語系化為日文它只能檢視在日文[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]不能在英文[!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)]。 這會產生一個問題，因為它是日文的使用者執行的英文版的常見案例[!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)]。  
  
 此問題的解決方案是設定中性的語言後援屬性。 應用程式開發人員可以選擇性地從主要組件中移除資源，指定可在附屬組件中找到的資源對應至特定的文化特性。 若要控制此程序使用<xref:System.Resources.NeutralResourcesLanguageAttribute>。 建構函式<xref:System.Resources.NeutralResourcesLanguageAttribute>類別有兩個簽章，一個會採用<xref:System.Resources.UltimateResourceFallbackLocation>參數來指定位置其中<xref:System.Resources.ResourceManager>應該擷取後援資源： 主要組件或附屬組件。 下列範例顯示如何使用這個屬性。 此程式碼所造成的最終後援位置<xref:System.Resources.ResourceManager>尋找"de"目錄的子目錄中的目前執行的組件的資源。  
  
```  
[assembly: NeutralResourcesLanguageAttribute(  
    "de" , UltimateResourceFallbackLocation.Satellite)]  
```  
  
## <a name="see-also"></a>另請參閱  
 [WPF 全球化和當地語系化概觀](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)
