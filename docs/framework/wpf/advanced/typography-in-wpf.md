---
title: WPF 中的印刷樣式
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: b4ae0d03c0207413d826e62de1d157f938b4d775
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016121"
---
# <a name="typography-in-wpf"></a>WPF 中的印刷樣式
本主題將介紹 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的主要印刷樣式功能。 這些功能包括改善文字轉譯的品質和效能、OpenType 印刷樣式支援、增強的國際文字、增強的字型支援, 以及新的文字應用程式開發介面 (Api)。  
  
<a name="Improved_Quality_and_Performance_of_Text"></a>   
## <a name="improved-quality-and-performance-of-text"></a>提升文字的品質與效能  
 中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的文字會使用 Microsoft ClearType 來轉譯, 這可增強文字的清晰度和可讀性。 ClearType 是由 Microsoft 開發的軟體技術, 可改善現有 Lcd (液晶顯示器) 的文字可讀性, 例如膝上型電腦螢幕、Pocket PC 螢幕和平面監視器。 ClearType 使用子圖元轉譯, 藉由在圖元的小數部分對齊字元, 讓文字顯示為真形狀的精確度更高。 額外的解析度可提高文字顯示細節的解析度，即使經過長時間也很容易閱讀。 中的 ClearType 的另[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]一項改進是 y 方向消除鋸齒, 這會平滑文字字元中淺層曲線的頂端和底端。 如需 ClearType 功能的詳細資訊, 請參閱[Cleartype 總覽](cleartype-overview.md)。  
  
 ![套用 ClearType Y 方向消除鋸齒功能的文字](./media/typography-in-wpf/text-y-direction-antialiasing.gif)  
以 ClearType Y 方向消除鋸齒功能顯示的文字  
  
 整個文字轉譯管線可在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 上啟用硬體加速，但前提是您的機器符合所需硬體的最低層級。 無法使用硬體執行的轉譯會回復為軟體轉譯。 硬體加速會影響文字轉譯管線的所有階段—從儲存個別的字元、將圖像合成字元執行、套用效果, 到最終顯示的輸出都會套用 ClearType 混合演算法。 如需硬體加速的詳細資訊，請參閱[圖形轉譯層](graphics-rendering-tiers.md)。  
  
 ![文字轉譯管線的圖表](./media/typography-in-wpf/text-rendering-pipeline.png)  
  
 此外，具動畫效果的文字 (無論是字元或字符) 都可充分利用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 所啟用的圖形硬體功能。 這樣可產生平滑的文字動畫。  
  
<a name="Rich_Typography"></a>   
## <a name="rich-typography"></a>豐富的印刷樣式  
 OpenType 字型格式是[!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)]字型格式的延伸。 OpenType 字型格式是由 Microsoft 和 Adobe 共同開發, 並提供豐富的先進印刷樣式功能。 <xref:System.Windows.Documents.Typography>物件會公開 OpenType 字型的許多先進功能, 例如, 樣式替代和花飾字。 Windows SDK 提供一組範例 OpenType 字型, 這些字型是以豐富的功能 (例如 Pericles 和 Pescadero 字型) 所設計。 如需詳細資訊，請參閱[範例 OpenType 字型套件](sample-opentype-font-pack.md)。  
  
 Pericles OpenType 字型包含額外的圖像, 可為標準的圖像集提供樣式替代。 下列文字顯示文體替代字符。  
  
 ![使用 OpenType 樣式替代字元的文字](./media/typography-in-wpf/opentype-stylistic-alternate-glyphs.gif "使用 OpenType 樣式替代字元的文字")  
  
 花飾字是裝飾性字符，會使用精心設計且通常與書寫體相關聯的裝飾。 下列文字顯示 Pescadero 字型的標準和花飾字字符。  
  
 ![使用 OpenType 標準和花飾字字元的文字](./media/typography-in-wpf/opentype-standard-swash-glyphs.gif "使用 OpenType 標準和花飾字字元的文字")  
  
 如需 OpenType 功能的詳細資訊, 請參閱[Opentype 字型功能](opentype-font-features.md)。  
  
<a name="Enhanced_International_Text_Support"></a>   
## <a name="enhanced-international-text-support"></a>已增強的國際文字支援  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 藉由提供下列功能來提供已增強的國際文字支援：  
  
- 在所有書寫系統中，使用自動調整度量功能來自動調整行間距。  
  
- 對於國際文字的廣泛支援。 如需詳細資訊，請參閱 [WPF 的全球化](globalization-for-wpf.md)。  
  
- 語言導向的分行、斷字及對齊。  
  
<a name="Enhanced_Font_Support"></a>   
## <a name="enhanced-font-support"></a>已增強的字型支援  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 藉由提供下列功能來提供已增強的字型支援：  
  
- 適用於所有文字的 Unicode。 字型行為和選取不再需要字元集或字碼頁。  
  
- 字型行為與全域設定 (例如系統地區設定) 無關。  
  
- 個別<xref:System.Windows.FontWeight>的<xref:System.Windows.FontStretch>、和<xref:System.Windows.FontStyle>類型, 用於定義。 <xref:System.Windows.Media.FontFamily> 這提供的彈性比使用 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 程式設計還要大，其中的斜體與粗體布林值組合是用來定義字型家族。  
  
- 書寫方向 (水平和垂直) 會與字型名稱分開處理。  
  
- 可攜式 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 檔案中的字型連結和字型遞補，使用的是複合字型技術。 複合字型，能夠建構全系列的多語系字型。 複合字型也提供一種機制來避免顯示遺漏的字符。 如需詳細資訊, 請參閱<xref:System.Windows.Media.FontFamily>類別中的備註。  
  
- 從複合字型，使用單一語言字型群組建置的國際字型。 這可在開發多國語言的字型時節省資源成本。  
  
- 內嵌於文件中的複合字型，藉此提供文件的可攜性。 如需詳細資訊, 請參閱<xref:System.Windows.Media.FontFamily>類別中的備註。  
  
<a name="New_Text_APIs"></a>   
## <a name="new-text-application-programming-interfaces-apis"></a>新的文字應用程式開發介面 (API)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供數個文字 Api, 供開發人員在其應用程式中包含文字時使用。 這些 Api 分為三個類別:  
  
- **版面配置和使用者介面**。 圖形化使用者介面 (GUI) 的一般文字控制項。  
  
- **輕量型文字繪製**。 可讓您直接對物件繪製文字。  
  
- **進階文字格式化**。 可讓您實作自訂的文字引擎。  
  
### <a name="layout-and-user-interface"></a>版面配置和使用者介面  
 在最高層級的功能中, 文字 api 會提供[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]常見的控制項<xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBlock>例如、 <xref:System.Windows.Controls.TextBox>和。 這些控制項提供應用程式內基本的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 元素，以及提供一種簡單方式來呈現文字並與之互動。 <xref:System.Windows.Controls.RichTextBox>和之類的控制項<xref:System.Windows.Controls.PasswordBox>可讓您進行更先進的文字處理。 和類別 (例如<xref:System.Windows.Documents.TextRange>、 <xref:System.Windows.Documents.TextSelection> <xref:System.Windows.Documents.TextPointer>和) 會啟用有用的文字操作。 這些[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]控制項提供<xref:System.Windows.Controls.Control.FontFamily%2A>、 <xref:System.Windows.Controls.Control.FontSize%2A>和等屬性,可讓您控制用來呈現文字的字型。<xref:System.Windows.Controls.Control.FontStyle%2A>  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>使用點陣圖效果、轉換和文字效果  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可讓您藉由使用點陣圖效果、轉換和文字效果等功能，對文字建立具視覺效果的趣味用法。 下列範例示範套用至文字之延伸陰影效果的典型類型。  
  
 ![具有柔和度&#61; 0.25 的文字陰影](./media/typography-in-wpf/drop-shadow-text-effect.jpg) 
  
 下列範例示範套用至文字的延伸陰影效果與雜點。  
  
 ![具有雜點的文字陰影](./media/typography-in-wpf/drop-shadow-noise-text.jpg) 
  
 下列範例示範套用至文字的外光暈效果。  
  
 ![使用 OuterGlowBitmapEffect 的文字陰影](./media/typography-in-wpf/text-shadow-glow-effect.jpg)
  
 下列範例示範套用至文字的模糊效果。  
  
 ![使用 BlurBitmapEffect 的文字陰影](./media/typography-in-wpf/text-shadow-blur-effect.jpg)  

 下列範例示範沿著 X 軸縮放 150% 的第二行文字，以及沿著 Y 軸縮放 150% 的第三行文字。  
  
 ![使用 ScaleTransform 縮放的文字](./media/typography-in-wpf/scaled-text-scaletransform.jpg) 
  
 下列範例示範沿著 X 軸傾斜的文字。  
  
 ![使用 SkewTransform 傾斜的文字](./media/typography-in-wpf/skewed-transformed-text.jpg)
  
 <xref:System.Windows.Media.TextEffect>物件是 helper 物件, 可讓您將文字視為文字字串中的一或多個字元群組。 下列範例示範旋轉個別字元。 每一個字元會以 1 秒的間隔獨立旋轉。  
  
 ![旋轉文字的文字效果螢幕擷取畫面](./media/typography-in-wpf/rotating-text-effect.jpg) 
  
#### <a name="using-flow-documents"></a>使用非固定格式文件  
 除了通用[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]控制項以外, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]還提供文字呈現的版面配置控制項, 也就<xref:System.Windows.Documents.FlowDocument>是元素。 專案 (結合<xref:System.Windows.Controls.DocumentViewer>元素) 可針對具有不同版面配置需求的大量文字提供控制項。 <xref:System.Windows.Documents.FlowDocument> 版面配置控制項可讓您透過其他<xref:System.Windows.Documents.Typography> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]控制項的物件和字型相關屬性, 存取先進的印刷樣式。  
  
 下列範例顯示在中<xref:System.Windows.Controls.FlowDocumentReader>裝載的文字內容, 其提供搜尋、導覽、分頁和內容縮放支援。  
  
 ![顯示 OpenType 字型的螢幕擷取畫面。](./media/typography-in-wpf/typography-text-flowdocumentreader.png)
  
 如需詳細資訊，請參閱 [WPF 中的文件](documents-in-wpf.md)。  
  
### <a name="lightweight-text-drawing"></a>輕量型文字繪製  
 您可以使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Media.DrawingContext>物件的<xref:System.Windows.Media.DrawingContext.DrawText%2A>方法, 將文字直接繪製到物件。 若要使用這個方法, 您可以<xref:System.Windows.Media.FormattedText>建立物件。 這個物件可讓您繪製多行文字，且可個別格式化文字中的每個字元。 <xref:System.Windows.Media.FormattedText>物件的功能包含 Windows API 中 DrawText 旗標的許多功能。 此外, <xref:System.Windows.Media.FormattedText>物件也包含省略號支援之類的功能, 其中文字超出其邊界時, 會顯示省略號。 下列範例示範的文字具有數種已套用的格式，包括第二個和第三個字的線性漸層。  
  
 ![使用 FormattedText 物件顯示的文字](./media/typography-in-wpf/text-formatted-linear-gradient.jpg) 
  
 您可以將格式化的文字<xref:System.Windows.Media.Geometry>轉換成物件, 讓您建立其他類型的視覺效果文字。 例如, 您可以根據文字字串<xref:System.Windows.Media.Geometry>的外框來建立物件。  
  
 ![以線性漸層筆刷繪製外框的文字](./media/typography-in-wpf/text-outline-linear-gradient.jpg)  
  
 下列範例示範數種方式，可透過修改筆劃、填滿和反白顯示轉換的文字，來建立有趣的視覺效果。  
  
 ![使用不同填色和筆觸色彩的文字](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![影像筆刷套用至筆觸的文字](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![影像筆刷套用至筆劃和反白顯示的文字](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 如需物件的<xref:System.Windows.Media.FormattedText>詳細資訊, 請參閱[繪製格式化的文字](drawing-formatted-text.md)。  
  
### <a name="advanced-text-formatting"></a>進階文字格式化  
 在最先進的文字 api 層級中, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]可讓您<xref:System.Windows.Media.TextFormatting.TextFormatter>使用物件<xref:System.Windows.Media.TextFormatting>和命名空間中的其他類型來建立自訂文字版面配置。 和<xref:System.Windows.Media.TextFormatting.TextFormatter>相關聯的類別可讓您執行自訂文字版面配置, 以支援您自己的字元格式定義、段落樣式、分行規則, 以及其他國際文字的版面配置功能。 在非常少數的情況下，您會想要覆寫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 文字配置支援的預設實作。 不過，如果您要建立文字編輯控制項或應用程式，您可能需要不同於預設 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作的實作。  
  
 不同于傳統文字 API, <xref:System.Windows.Media.TextFormatting.TextFormatter>會透過一組回呼方法與文字佈局用戶端互動。 它要求用戶端在<xref:System.Windows.Media.TextFormatting.TextSource>類別的執行中提供這些方法。 下圖說明用戶端應用程式與<xref:System.Windows.Media.TextFormatting.TextFormatter>之間的文字版面配置互動。  
  
 ![文字配置用戶端和 TextFormatter 的圖表](./media/typography-in-wpf/text-layout-text-formatter-interaction.png)  
  
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
