---
title: WPF 中的印刷樣式
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: 16897413c31e39be5c1d45b43d6ef816d3f80aad
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482687"
---
# <a name="typography-in-wpf"></a>WPF 中的印刷樣式
本主題將介紹 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的主要印刷樣式功能。 這些功能包括提升文字轉譯的品質與效能、[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 印刷樣式支援、已增強的國際文字、已增強的字型支援，以及新的文字應用程式開發介面 (API)。  
  
<a name="Improved_Quality_and_Performance_of_Text"></a>   
## <a name="improved-quality-and-performance-of-text"></a>提升文字的品質與效能  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的文字是使用 [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] 來轉譯，可增強文字的清晰度與可讀性。 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 軟體技術是由 [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] 所開發，此技術改善了現有 LCD (液晶顯示器) 上的文字可讀性，例如膝上型電腦螢幕、Pocket PC 螢幕和平面監視器。 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 使用子像素轉譯，讓文字可利用像素的小數部分來對齊字元，使用更高畫質來顯示它的真正樣貌。 額外的解析度可提高文字顯示細節的解析度，即使經過長時間也很容易閱讀。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 的另一項改進是以 y 方向消除鋸齒，這會使文字字元中平滑曲線頂端和底部更平滑。 如需 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 功能的詳細資訊，請參閱 [ClearType 概觀](cleartype-overview.md)。  
  
 ![以 ClearType y 的文字&#45;反方向&#45;別名](./media/typographyinwpf02.gif "TypographyInWPF02")  
以 ClearType Y 方向消除鋸齒功能顯示的文字  
  
 整個文字轉譯管線可在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 上啟用硬體加速，但前提是您的機器符合所需硬體的最低層級。 無法使用硬體執行的轉譯會回復為軟體轉譯。 硬體加速會影響文字轉譯管線的所有階段；範圍從儲存個別字符、將字符組合至字符執行、套用效果，到將 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 混色演算法套用至最終顯示的輸出。 如需硬體加速的詳細資訊，請參閱[圖形轉譯層](graphics-rendering-tiers.md)。  
  
 ![文字轉譯管線的圖表](./media/typographyinwpf01.png "TypographyInWPF01")  
文字轉譯管線的圖表  
  
 此外，具動畫效果的文字 (無論是字元或字符) 都可充分利用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 所啟用的圖形硬體功能。 這樣可產生平滑的文字動畫。  
  
<a name="Rich_Typography"></a>   
## <a name="rich-typography"></a>豐富的印刷樣式  
 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] 字型格式是 [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] 字型格式的延伸。 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] 字型格式是由 [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] 和 Adobe 共同開發，並提供各式各樣豐富的進階印刷樣式功能。 <xref:System.Windows.Documents.Typography>物件會公開的許多進階功能[!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]字型，例如文體替代字和花飾字。 [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] 提供一組範例 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] 字型，這組字型的設計具有豐富的特色，例如 Pericles 和 Pescadero 字型。 如需詳細資訊，請參閱[範例 OpenType 字型套件](sample-opentype-font-pack.md)。  
  
 Pericles [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] 字型包含其他字符，可為標準的字符組提供文體替代字。 下列文字顯示文體替代字符。  
  
 ![使用 OpenType 文體替代字符的文字](./media/typography-in-wpf/opentype-stylistic-alternate-glyphs.gif "使用 OpenType 文體替代字符的文字")  
  
 花飾字是裝飾性字符，會使用精心設計且通常與書寫體相關聯的裝飾。 下列文字顯示 Pescadero 字型的標準和花飾字字符。  
  
 ![使用 OpenType 標準和花飾字字符的文字](./media/typography-in-wpf/opentype-standard-swash-glyphs.gif "使用 OpenType 標準和花飾字字符的文字")  
  
 如需 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] 功能的詳細資訊，請參閱 [OpenType 字型功能](opentype-font-features.md)。  
  
<a name="Enhanced_International_Text_Support"></a>   
## <a name="enhanced-international-text-support"></a>已增強的國際文字支援  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 藉由提供下列功能來提供已增強的國際文字支援：  
  
-   在所有書寫系統中，使用自動調整度量功能來自動調整行間距。  
  
-   對於國際文字的廣泛支援。 如需詳細資訊，請參閱 [WPF 的全球化](globalization-for-wpf.md)。  
  
-   語言導向的分行、斷字及對齊。  
  
<a name="Enhanced_Font_Support"></a>   
## <a name="enhanced-font-support"></a>已增強的字型支援  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 藉由提供下列功能來提供已增強的字型支援：  
  
-   適用於所有文字的 Unicode。 字型行為和選取不再需要字元集或字碼頁。  
  
-   字型行為與全域設定 (例如系統地區設定) 無關。  
  
-   個別<xref:System.Windows.FontWeight>， <xref:System.Windows.FontStretch>，並<xref:System.Windows.FontStyle>定義的型別<xref:System.Windows.Media.FontFamily>。 這提供的彈性比使用 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 程式設計還要大，其中的斜體與粗體布林值組合是用來定義字型家族。  
  
-   書寫方向 (水平和垂直) 會與字型名稱分開處理。  
  
-   可攜式 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 檔案中的字型連結和字型遞補，使用的是複合字型技術。 複合字型，能夠建構全系列的多語系字型。 複合字型也提供一種機制來避免顯示遺漏的字符。 如需詳細資訊，請參閱中的備註<xref:System.Windows.Media.FontFamily>類別。  
  
-   從複合字型，使用單一語言字型群組建置的國際字型。 這可在開發多國語言的字型時節省資源成本。  
  
-   內嵌於文件中的複合字型，藉此提供文件的可攜性。 如需詳細資訊，請參閱中的備註<xref:System.Windows.Media.FontFamily>類別。  
  
<a name="New_Text_APIs"></a>   
## <a name="new-text-application-programming-interfaces-apis"></a>新的文字應用程式開發介面 (API)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供數個文字 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]，讓開發人員能夠在他們的應用程式中包含文字時使用。 這些 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 可分為三個類別：  
  
-   **版面配置和使用者介面**。 [!INCLUDE[TLA#tla_gui](../../../../includes/tlasharptla-gui-md.md)] 的一般文字控制項。  
  
-   **輕量型文字繪製**。 可讓您直接對物件繪製文字。  
  
-   **進階文字格式化**。 可讓您實作自訂的文字引擎。  
  
### <a name="layout-and-user-interface"></a>版面配置和使用者介面  
 在最高層級的功能中，文字[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]提供通用[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]這類控制<xref:System.Windows.Controls.Label>， <xref:System.Windows.Controls.TextBlock>，和<xref:System.Windows.Controls.TextBox>。 這些控制項提供應用程式內基本的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 元素，以及提供一種簡單方式來呈現文字並與之互動。 控制這類<xref:System.Windows.Controls.RichTextBox>和<xref:System.Windows.Controls.PasswordBox>啟用更進階或特製化的文字處理。 這類類別和<xref:System.Windows.Documents.TextRange>， <xref:System.Windows.Documents.TextSelection>，和<xref:System.Windows.Documents.TextPointer>可讓您更有用的文字操作。 這些[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]控制項提供屬性，例如<xref:System.Windows.Controls.Control.FontFamily%2A>， <xref:System.Windows.Controls.Control.FontSize%2A>，和<xref:System.Windows.Controls.Control.FontStyle%2A>，可讓您控制用來呈現文字的字型。  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>使用點陣圖效果、轉換和文字效果  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可讓您藉由使用點陣圖效果、轉換和文字效果等功能，對文字建立具視覺效果的趣味用法。 下列範例示範套用至文字之延伸陰影效果的典型類型。  
  
 ![文字陰影濃淡&#61;0.25](./media/shadowtext01.jpg "ShadowText01")  
具有延伸陰影的文字  
  
 下列範例示範套用至文字的延伸陰影效果與雜點。  
  
 ![具有雜點的文字陰影](./media/shadowtext04.jpg "ShadowText04")  
具有延伸陰影與雜點的文字  
  
 下列範例示範套用至文字的外光暈效果。  
  
 ![使用 OuterGlowBitmapEffect 的文字陰影](./media/shadowtext05.jpg "ShadowText05")  
具有外光暈效果的文字  
  
 下列範例示範套用至文字的模糊效果。  
  
 ![使用 BlurBitmapEffect 的文字陰影](./media/shadowtext06.jpg "ShadowText06")  
具有模糊效果的文字  
  
 下列範例示範沿著 X 軸縮放 150% 的第二行文字，以及沿著 Y 軸縮放 150% 的第三行文字。  
  
 ![使用 ScaleTransform 縮放的文字](./media/transformedtext02.jpg "TransformedText02")  
使用 ScaleTransform 的文字  
  
 下列範例示範沿著 X 軸傾斜的文字。  
  
 ![使用 skewtransform 傾斜的文字](./media/transformedtext03.jpg "TransformedText03")  
使用 SkewTransform 的文字  
  
 A<xref:System.Windows.Media.TextEffect>物件是協助程式物件，可讓您將文字視為文字字串中的字元的一個或多個群組。 下列範例示範旋轉個別字元。 每一個字元會以 1 秒的間隔獨立旋轉。  
  
 ![旋轉文字的文字效果螢幕擷取畫面](./media/texteffect01.jpg "TextEffect01")  
旋轉文字效果動畫的範例  
  
#### <a name="using-flow-documents"></a>使用非固定格式文件  
 除了一般[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]控制項[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供的文字呈現的版面配置控制項 —<xref:System.Windows.Documents.FlowDocument>項目。 <xref:System.Windows.Documents.FlowDocument>項目，搭配<xref:System.Windows.Controls.DocumentViewer>項目，提供大量具有不同的版面配置需求的文字的控制項。 版面配置控制項提供的存取權透過的進階印刷樣式<xref:System.Windows.Documents.Typography>物件和其他的字型相關屬性[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]控制項。  
  
 下列範例顯示的文字內容裝載於<xref:System.Windows.Controls.FlowDocumentReader>，以提供搜尋、 瀏覽、 分頁及內容縮放支援。  
  
 ![使用 OpenType 字型範例螢幕擷取畫面](./media/typographyinwpf-03.png "TypographyInWPF_03")  
裝載於 FlowDocumentReader 的文字  
  
 如需詳細資訊，請參閱 [WPF 中的文件](documents-in-wpf.md)。  
  
### <a name="lightweight-text-drawing"></a>輕量型文字繪製  
 您可以直接繪製文字[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用的物件<xref:System.Windows.Media.DrawingContext.DrawText%2A>方法<xref:System.Windows.Media.DrawingContext>物件。 若要使用此方法，您建立<xref:System.Windows.Media.FormattedText>物件。 這個物件可讓您繪製多行文字，且可個別格式化文字中的每個字元。 功能<xref:System.Windows.Media.FormattedText>物件包含許多 Win32 API 中 DrawText 旗標的功能。 颾魤 ㄛ<xref:System.Windows.Media.FormattedText>物件包含像是省略符號支援，當文字超過其範圍時，會顯示省略符號的功能。 下列範例示範的文字具有數種已套用的格式，包括第二個和第三個字的線性漸層。  
  
 ![使用 FormattedText 物件顯示的文字](./media/formattedtext01.jpg "FormattedText01")  
使用 FormattedText 物件顯示的文字  
  
 您可以將轉換成的格式化的文字<xref:System.Windows.Media.Geometry>物件，可讓您建立其他類型的趣味視覺文字。 例如，您可以在其中建立<xref:System.Windows.Media.Geometry>物件根據文字字串的外框。  
  
 ![以線性漸層筆刷繪製外框的文字](./media/outlinedtext02.jpg "OutlinedText02")  
以線性漸層筆刷繪製外框的文字  
  
 下列範例示範數種方式，可透過修改筆劃、填滿和反白顯示轉換的文字，來建立有趣的視覺效果。  
  
 ![以不同的色彩填滿和筆劃的文字](./media/outlinedtext03.jpg "OutlinedText03")  
設定筆劃並填滿不同色彩的範例  
  
 ![影像筆刷套用至筆觸的文字](./media/outlinedtext04.jpg "OutlinedText04")  
影像筆刷套用至筆劃的範例  
  
 ![影像筆刷套用至筆觸的文字](./media/outlinedtext05.jpg "OutlinedText05")  
影像筆刷套用至筆劃並反白顯示的範例  
  
 如需詳細資訊<xref:System.Windows.Media.FormattedText>物件，請參閱 <<c2> [ 繪製格式化的文字](drawing-formatted-text.md)。  
  
### <a name="advanced-text-formatting"></a>進階文字格式化  
 在最進階的文字[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]可讓您藉由建立自訂文字版面配置<xref:System.Windows.Media.TextFormatting.TextFormatter>物件中和其他類型<xref:System.Windows.Media.TextFormatting>命名空間。 <xref:System.Windows.Media.TextFormatting.TextFormatter>和相關聯的類別可讓您實作自訂文字版面配置，支援您自己定義的字元格式、 段落樣式行分行規則及其他版面配置功能，針對國際文字。 在非常少數的情況下，您會想要覆寫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 文字配置支援的預設實作。 不過，如果您要建立文字編輯控制項或應用程式，您可能需要不同於預設 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作的實作。  
  
 不同於傳統的文字[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]，則<xref:System.Windows.Media.TextFormatting.TextFormatter>互動文字配置用戶端透過一組回呼方法。 它需要用戶端提供這些方法的實作中<xref:System.Windows.Media.TextFormatting.TextSource>類別。 下圖說明用戶端應用程式之間的文字版面配置互動和<xref:System.Windows.Media.TextFormatting.TextFormatter>。  
  
 ![文字配置用戶端和 TextFormatter 的圖表](./media/textformatter01.png "TextFormatter01")  
應用程式和 TextFormatter 之間的互動  
  
 如需如何建立自訂文字版面配置的詳細資訊，請參閱[進階文字格式化](advanced-text-formatting.md)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Media.FormattedText>
- <xref:System.Windows.Media.TextFormatting.TextFormatter>
- [ClearType 概觀](cleartype-overview.md)
- [OpenType 字型功能](opentype-font-features.md)
- [繪製格式化的文字](drawing-formatted-text.md)
- [進階文字格式化](advanced-text-formatting.md)
- [Text](optimizing-performance-text.md)
- [Microsoft 印刷樣式](https://docs.microsoft.com/typography/)