---
title: "WPF 中的印刷樣式 | Microsoft Docs"
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
  - "印刷樣式, 關於印刷樣式"
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
caps.latest.revision: 27
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 26
---
# WPF 中的印刷樣式
本主題介紹 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的主要印刷樣式功能。  這些功能包含改善的文字呈現品質和效能、[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 印刷樣式支援、增強型國際文字、增強型字型支援和全新的文字應用程式開發介面 \(API\)。  
  
   
  
<a name="Improved_Quality_and_Performance_of_Text"></a>   
## 改善的文字品質和效能  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的文字是使用 [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] 呈現的，會增強文字的清晰度和可讀性。  [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 是由 [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] 開發的軟體技術，能夠改善現有 LCD \(液晶顯示，例如膝上型電腦螢幕、Pocket PC 螢幕和平面監視器\) 文字的可讀性。  [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 使用子像素呈現，會藉由對齊像素小數部分的字元，以更大的真實圖案逼真度來顯示文字。  極高解析度會增加文字顯示中微小細節的清晰度，讓長時間閱讀方便得多。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 的另一項改善是 Y 方向消除鋸齒，就是讓文字字元淺曲線的上下端更加平滑。  如需 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 功能的詳細資訊，請參閱 [ClearType 概觀](../../../../docs/framework/wpf/advanced/cleartype-overview.md)。  
  
 ![套用 ClearType Y 方向消除鋸齒功能的文字](../../../../docs/framework/wpf/advanced/media/typographyinwpf02.png "TypographyInWPF02")  
使用 ClearType Y 方向消除鋸齒的文字  
  
 只要您的電腦符合所需硬體的最低層級需求，就可以透過硬體加快 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中用於呈現文字的整個流程。  無法使用硬體執行的呈現會切換回軟體呈現。  硬體加速會影響文字呈現流程的所有階段，包括儲存個別圖像、將圖像組合至圖像執行、套用效果，以及將 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 混合演算法套用至最終顯示輸出。  如需硬體加速的詳細資訊，請參閱[圖形轉譯層](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)。  
  
 ![文字轉譯管線的圖表](../../../../docs/framework/wpf/advanced/media/typographyinwpf01.png "TypographyInWPF01")  
文字呈現流程圖  
  
 此外，無論是字元或圖像的動畫文字，都會充分運用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 所賦予的圖形硬體功能。  得到的結果就會是平滑的文字動畫。  
  
<a name="Rich_Typography"></a>   
## 豐富的印刷樣式  
 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] 字型格式是 [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] 字型格式的延伸。  [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] 字型格式是由 [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] 和 Adobe 共同開發，可以提供豐富的進階印刷樣式功能。  <xref:System.Windows.Documents.Typography> 物件會公開 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] 字型的許多進階功能，例如文體替代字和花飾字。  [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] 提供了一組具備眾多功能的 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] 範例字型，例如 Pericles 和 Pescadero 字型。  如需詳細資訊，請參閱[範例 OpenType 字型套件](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)。  
  
 Pericles [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] 字型包含額外的圖像，這些圖像可以提供標準圖像集的文體替代字。  下列文字顯示文體替代字圖像。  
  
 ![使用 OpenType 文體替代圖像的文字](../../../../docs/framework/wpf/advanced/media/opentypefont02.png "opentypefont02")  
使用 OpenType 文體替代字圖像的文字  
  
 花飾字一般是與書法相關的精緻裝飾性圖像。  下列文字顯示 Pescadero 字型的標準和花飾字圖像。  
  
 ![使用 OpenType 標準和勾耳圖像的文字](../../../../docs/framework/wpf/advanced/media/opentypefont08.png "opentypefont08")  
使用 OpenType 標準和花飾字圖像的文字  
  
 如需 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] 功能的詳細資訊，請參閱 [OpenType 字型功能](../../../../docs/framework/wpf/advanced/opentype-font-features.md)。  
  
<a name="Enhanced_International_Text_Support"></a>   
## 增強型國際文字支援  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 具備下列功能，提供了增強型國際文字支援：  
  
-   使用適應性度量，自動調整所有書寫系統中的行距。  
  
-   廣泛的國際文字支援。  如需詳細資訊，請參閱 [WPF 的全球化](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)。  
  
-   語言指引的分行、斷字和對齊。  
  
<a name="Enhanced_Font_Support"></a>   
## 增強型字型支援  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 具備下列功能，提供了增強型字型支援：  
  
-   所有文字都使用 Unicode。  字型行為和選取不再需要字元集或字碼頁。  
  
-   字型行為與全域設定 \(例如系統地區設定\) 無關。  
  
-   不同的 <xref:System.Windows.FontWeight>、<xref:System.Windows.FontStretch> 和 <xref:System.Windows.FontStyle> 型別是用於定義 <xref:System.Windows.Media.FontFamily>。  相較於使用斜體和粗體布林組合來定義字型系列的 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 程式設計，這提供更大的彈性。  
  
-   書寫方向 \(水平和垂直\) 處理與字型名稱無關。  
  
-   可攜式 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 檔案中的字型連結和字型後援 \(使用複合字型技術\)。  複合字型允許建構各項多語字型。  複合字型也提供了可以避免顯示遺失圖像的機制。  如需詳細資訊，請參閱 <xref:System.Windows.Media.FontFamily> 類別中的備註。  
  
-   使用一組單一語言字型，從複合字型建立國際字型。  在開發多個語言的字型時，這可以節省資源成本。  
  
-   複合字型會內嵌在文件中，因此可以提供文件可攜性。  如需詳細資訊，請參閱 <xref:System.Windows.Media.FontFamily> 類別中的備註。  
  
<a name="New_Text_APIs"></a>   
## 全新的文字應用程式開發介面 \(API\)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供了數個文字 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]，可供開發人員在應用程式中包含文字時使用。  這些 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 分為三類：  
  
-   **配置和使用者介面**：  [!INCLUDE[TLA#tla_gui](../../../../includes/tlasharptla-gui-md.md)] 的通用文字控制項。  
  
-   **輕量型文字繪製**：  讓您直接在物件上繪製文字。  
  
-   **進階文字格式**：  讓您實作自訂文字引擎。  
  
### 配置和使用者介面  
 以最高層級的功能角度來說，文字 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 會提供通用[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 控制項，例如 <xref:System.Windows.Controls.Label>、<xref:System.Windows.Controls.TextBlock> 和 <xref:System.Windows.Controls.TextBox>。  這些控制項會在應用程式中提供基本的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 項目，並提供簡單的方式來呈現文字以及與文字互動。  <xref:System.Windows.Controls.RichTextBox> 和 <xref:System.Windows.Controls.PasswordBox> 之類的控制項會啟用更進階或特定的文字處理。  而 <xref:System.Windows.Documents.TextRange>、<xref:System.Windows.Documents.TextSelection> 和 <xref:System.Windows.Documents.TextPointer> 之類的類別則會啟用有用的文字管理。  這些 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 控制項提供了屬性，例如 <xref:System.Windows.Controls.Control.FontFamily%2A>、<xref:System.Windows.Controls.Control.FontSize%2A> 和 <xref:System.Windows.Controls.Control.FontStyle%2A>，可讓您控制用於呈現文字的字型。  
  
#### 使用點陣圖效果、轉換和文字效果  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可讓您使用功能 \(例如點陣圖效果、轉換和文字效果\) 來建立具有有趣外觀的文字。  下列範例顯示套用至文字的一般下拉式陰影效果類型。  
  
 ![Softness &#61; 0.25 的文字陰影](../../../../docs/framework/wpf/advanced/media/shadowtext01.png "ShadowText01")  
具有下拉式陰影的文字  
  
 下列範例顯示套用至文字的下拉式陰影效果和雜訊。  
  
 ![具有雜點的文字陰影](../../../../docs/framework/wpf/advanced/media/shadowtext04.png "ShadowText04")  
具有下拉式陰影和雜訊的文字  
  
 下列範例顯示套用至文字的外部光暈效果。  
  
 ![使用 OuterGlowBitmapEffect 的文字陰影](../../../../docs/framework/wpf/advanced/media/shadowtext05.png "ShadowText05")  
具有外部光暈效果的文字  
  
 下列範例顯示套用至文字的模糊效果。  
  
 ![使用 BlurBitmapEffect 的文字陰影](../../../../docs/framework/wpf/advanced/media/shadowtext06.png "ShadowText06")  
具有模糊效果的文字  
  
 下列範例顯示第二行文字沿著 X 軸調整 150%，第三行文字沿著 Y 軸調整 150%。  
  
 ![使用 ScaleTransform 縮放的文字](../../../../docs/framework/wpf/advanced/media/transformedtext02.png "TransformedText02")  
使用 ScaleTransform 的文字  
  
 下列範例顯示文字沿著 X 軸傾斜。  
  
 ![使用 SkewTransform 傾斜的文字](../../../../docs/framework/wpf/advanced/media/transformedtext03.png "TransformedText03")  
使用 SkewTransform 的文字  
  
 <xref:System.Windows.Media.TextEffect> 物件是可以允許您將文字視為文字字串中之一或多組字元的 Helper 物件。  下列範例會顯示個別旋轉的字元。  每個字元是以 1 秒間隔獨立旋轉。  
  
 ![旋轉文字的文字效果螢幕擷取畫面](../../../../docs/framework/wpf/advanced/media/texteffect01.png "TextEffect01")  
旋轉文字效果動畫的範例  
  
#### 使用流程文件  
 除了通用 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 控制項之外，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 還提供用於進行文字展示的配置控制項，即 <xref:System.Windows.Documents.FlowDocument> 項目。  當 <xref:System.Windows.Documents.FlowDocument> 項目與 <xref:System.Windows.Controls.DocumentViewer> 項目搭配使用時，可以為具有各種配置需求的大量文字提供控制。  配置控制項會透過 <xref:System.Windows.Documents.Typography> 物件和其他 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 控制項的字型相關屬性，提供進階印刷樣式存取。  
  
 下列範例顯示 <xref:System.Windows.Controls.FlowDocumentReader> 中裝載的文字內容，會提供搜尋、巡覽、分頁和內容縮放比例支援。  
  
 ![使用 OpenType 字型範例螢幕擷取畫面](../../../../docs/framework/wpf/advanced/media/typographyinwpf-03.png "TypographyInWPF\_03")  
FlowDocumentReader 中裝載的文字  
  
 如需詳細資訊，請參閱 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)。  
  
### 輕量型文字繪製  
 您可以使用 <xref:System.Windows.Media.DrawingContext> 物件的 <xref:System.Windows.Media.DrawingContext.DrawText%2A> 方法，直接在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 物件上繪製文字。  若要使用這個方法，您必須建立 <xref:System.Windows.Media.FormattedText> 物件。  這個物件可讓您繪製多行文字，而文字中的每個字元都可以個別格式化。  <xref:System.Windows.Media.FormattedText> 物件的功能包含 Win32 API 中 DrawText 旗標的許多功能。  此外，<xref:System.Windows.Media.FormattedText> 物件還包含其他功能，例如省略符號支援，即文字超出範圍時顯示省略符號。  下列範例顯示套用多種格式的文字，包括第二和第三個字上的線形漸層。  
  
 ![使用 FormattedText 物件顯示的文字](../../../../docs/framework/wpf/advanced/media/formattedtext01.png "FormattedText01")  
使用 FormattedText 物件的顯示文字  
  
 您可以將格式化文字轉換為 <xref:System.Windows.Media.Geometry> 物件，以便建立具有有趣外觀的其他文字類型。  例如，您可以根據文字字串的外框來建立 <xref:System.Windows.Media.Geometry> 物件。  
  
 ![以線性漸層筆刷繪製外框的文字](../../../../docs/framework/wpf/advanced/media/outlinedtext02.png "OutlinedText02")  
使用線形漸層筆刷的文字外框  
  
 下列範例說明藉由修改轉換文字的筆劃、填滿和反白顯示，建立有趣視覺效果的多個方法。  
  
 ![使用不同填色和筆觸色彩的文字](../../../../docs/framework/wpf/advanced/media/outlinedtext03.png "OutlinedText03")  
將筆劃和填滿設定為不同色彩的範例  
  
 ![影像筆刷套用至筆觸的文字](../../../../docs/framework/wpf/advanced/media/outlinedtext04.png "OutlinedText04")  
在筆劃上套用影像筆刷的範例  
  
 ![影像筆刷套用至筆觸的文字](../../../../docs/framework/wpf/advanced/media/outlinedtext05.png "OutlinedText05")  
在筆劃和反白顯示上套用影像筆刷的範例  
  
 如需 <xref:System.Windows.Media.FormattedText> 物件的詳細資訊，請參閱[繪製格式化的文字](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)。  
  
### 進階文字格式化  
 以文字 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 的最進階層級角度來說，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會藉由使用 <xref:System.Windows.Media.TextFormatting.TextFormatter> 物件和 <xref:System.Windows.Media.TextFormatting> 命名空間中其他的型別來為您提供建立自訂文字配置的能力。  <xref:System.Windows.Media.TextFormatting.TextFormatter> 和相關類別可讓您實作自訂文字配置，以支援您自己的國際文字字元格式、段落樣式、分行規則和其他配置功能的定義。  您幾乎不需要覆寫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 文字配置支援的預設實作。  但是當您建立文字編輯控制項或應用程式時，您可能會需要預設 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作之外的不同實作。  
  
 與傳統文字 [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] 不同的是，<xref:System.Windows.Media.TextFormatting.TextFormatter> 會透過一組回呼方法，與文字配置用戶端互動。  它會要求要用戶端在 <xref:System.Windows.Media.TextFormatting.TextSource> 類別實作中提供這些方法。  下列圖表說明用戶端應用程式和 <xref:System.Windows.Media.TextFormatting.TextFormatter> 之間的文字配置互動。  
  
 ![文字配置用戶端和 TextFormatter 的圖表](../../../../docs/framework/wpf/advanced/media/textformatter01.png "TextFormatter01")  
應用程式和 TextFormatter 之間的互動  
  
 如需建立自訂文字配置的詳細資訊，請參閱[進階文字格式化](../../../../docs/framework/wpf/advanced/advanced-text-formatting.md)。  
  
## 請參閱  
 <xref:System.Windows.Media.FormattedText>   
 <xref:System.Windows.Media.TextFormatting.TextFormatter>   
 [ClearType 概觀](../../../../docs/framework/wpf/advanced/cleartype-overview.md)   
 [OpenType 字型功能](../../../../docs/framework/wpf/advanced/opentype-font-features.md)   
 [繪製格式化的文字](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)   
 [進階文字格式化](../../../../docs/framework/wpf/advanced/advanced-text-formatting.md)   
 [文字](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [Microsoft 印刷樣式](http://www.microsoft.com/typography/default.mspx)