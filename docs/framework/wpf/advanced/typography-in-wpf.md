---
title: 印刷樣式
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: 501a4221c99d405484a2fb908641d27d1f38f266
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187342"
---
# <a name="typography-in-wpf"></a>WPF 中的印刷樣式
本主題將介紹 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的主要印刷樣式功能。 這些功能包括提高文本呈現的品質和性能、OpenType 排版支援、增強的國際文本、增強的字體支援以及新的文本應用程式開發介面 （API）。  
  
<a name="Improved_Quality_and_Performance_of_Text"></a>
## <a name="improved-quality-and-performance-of-text"></a>提升文字的品質與效能  
 中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的文本使用 Microsoft ClearType 呈現，這增強了文本的清晰度和可讀性。 ClearType 是 Microsoft 開發的一種軟體技術，可提高現有 LCD（液晶顯示器）文本的可讀性，例如筆記本電腦螢幕、袖珍 PC 螢幕和平板顯示器。 ClearType 使用子圖元渲染，通過對齊圖元小部分上的字元，從而允許文本以更高的真實形狀的逼真度顯示。 額外的解析度可提高文字顯示細節的解析度，即使經過長時間也很容易閱讀。 ClearType 的另[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]一個改進是 y 方向反鋸齒，它平滑文本字元中淺曲線的頂部和底部。 有關清除類型功能的更多詳細資訊，請參閱[清除類型概述](cleartype-overview.md)。  
  
 ![套用 ClearType Y 方向消除鋸齒功能的文字](./media/typography-in-wpf/text-y-direction-antialiasing.gif)  
以 ClearType Y 方向消除鋸齒功能顯示的文字  
  
 整個文字轉譯管線可在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 上啟用硬體加速，但前提是您的機器符合所需硬體的最低層級。 無法使用硬體執行的轉譯會回復為軟體轉譯。 硬體加速影響文本呈現管道的所有階段 - 從存儲單個字形、將字形合成字形到字形運行、應用效果，到將 ClearType 混合演算法應用於最終顯示的輸出。 如需硬體加速的詳細資訊，請參閱[圖形轉譯層](graphics-rendering-tiers.md)。  
  
 ![文字轉譯管線的圖表](./media/typography-in-wpf/text-rendering-pipeline.png)  
  
 此外，具動畫效果的文字 (無論是字元或字符) 都可充分利用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 所啟用的圖形硬體功能。 這樣可產生平滑的文字動畫。  
  
<a name="Rich_Typography"></a>
## <a name="rich-typography"></a>豐富的印刷樣式  
 OpenType 字型格式是 TrueType ®字體格式的副檔名。 OpenType 字型格式由微軟和 Adobe 共同開發，提供了豐富的高級排版功能。 該<xref:System.Windows.Documents.Typography>物件公開了 OpenType 字型的許多高級功能，例如樣式替代和套線。 Windows SDK 提供了一組示例 OpenType 字型，這些字體設計具有豐富的功能，如 Pericles 和 Pescadero 字體。 有關詳細資訊，請參閱[示例打開字體包](sample-opentype-font-pack.md)。  
  
 Pericles OpenType 字型包含其他字形，這些字形為標準字形集提供樣式替代。 下列文字顯示文體替代字符。  
  
 ![使用 OpenType 文體替代圖像的文字](./media/typography-in-wpf/opentype-stylistic-alternate-glyphs.gif "使用 OpenType 文體替代圖像的文字")  
  
 花飾字是裝飾性字符，會使用精心設計且通常與書寫體相關聯的裝飾。 下列文字顯示 Pescadero 字型的標準和花飾字字符。  
  
 ![使用 OpenType 標準和花飾字字符的文字](./media/typography-in-wpf/opentype-standard-swash-glyphs.gif "使用 OpenType 標準和勾耳圖像的文字")  
  
 有關 OpenType 功能的更多詳細資訊，請參閱[OpenType 字型功能](opentype-font-features.md)。  
  
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
  
- 用於<xref:System.Windows.FontWeight>定義<xref:System.Windows.FontStretch>的<xref:System.Windows.FontStyle><xref:System.Windows.Media.FontFamily>單獨 和 類型。 這提供了比 Win32 程式設計更大的靈活性，其中斜體和粗體的布林組合用於定義字型家族。  
  
- 書寫方向 (水平和垂直) 會與字型名稱分開處理。  
  
- 使用複合字體技術，在可擕式 XML 檔中進行字體連結和字體回退。 複合字型，能夠建構全系列的多語系字型。 複合字型也提供一種機制來避免顯示遺漏的字符。 有關詳細資訊，請參閱類中的<xref:System.Windows.Media.FontFamily>備註。  
  
- 從複合字型，使用單一語言字型群組建置的國際字型。 這可在開發多國語言的字型時節省資源成本。  
  
- 內嵌於文件中的複合字型，藉此提供文件的可攜性。 有關詳細資訊，請參閱類中的<xref:System.Windows.Media.FontFamily>備註。  
  
<a name="New_Text_APIs"></a>
## <a name="new-text-application-programming-interfaces-apis"></a>新的文字應用程式開發介面 (API)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供了幾個文本 API 供開發人員在其應用程式中包含文本時使用。 這些 API 分為三類：  
  
- **佈局和使用者介面**。 圖形化使用者介面 （GUI） 的通用文本控制項。  
  
- **羽量級文本繪圖**。 可讓您直接對物件繪製文字。  
  
- **進階文字格式化**。 可讓您實作自訂的文字引擎。  
  
### <a name="layout-and-user-interface"></a>版面配置和使用者介面  
 在最高級別的功能中，文本 API[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]提供常見的控制項，如<xref:System.Windows.Controls.Label>和<xref:System.Windows.Controls.TextBlock>。 <xref:System.Windows.Controls.TextBox> 這些控制項提供應用程式內基本的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 元素，以及提供一種簡單方式來呈現文字並與之互動。 控制項，如<xref:System.Windows.Controls.RichTextBox>和<xref:System.Windows.Controls.PasswordBox>啟用更高級或更專用的文本處理。 和類，如<xref:System.Windows.Documents.TextRange> <xref:System.Windows.Documents.TextSelection>，並<xref:System.Windows.Documents.TextPointer>啟用有用的文本操作。 這些[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]控制項提供屬性，如<xref:System.Windows.Controls.Control.FontFamily%2A> <xref:System.Windows.Controls.Control.FontSize%2A>，<xref:System.Windows.Controls.Control.FontStyle%2A>和 ， 使您能夠控制用於呈現文本的字體。  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>使用點陣圖效果、轉換和文字效果  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可讓您藉由使用點陣圖效果、轉換和文字效果等功能，對文字建立具視覺效果的趣味用法。 下列範例示範套用至文字之延伸陰影效果的典型類型。  
  
 ![具有柔和度&#61; 0.25 的文本陰影](./media/typography-in-wpf/drop-shadow-text-effect.jpg)
  
 下列範例示範套用至文字的延伸陰影效果與雜點。  
  
 ![具有雜點的文字陰影](./media/typography-in-wpf/drop-shadow-noise-text.jpg)
  
 下列範例示範套用至文字的外光暈效果。  
  
 ![使用 OuterGlowBitmapEffect 的文字陰影](./media/typography-in-wpf/text-shadow-glow-effect.jpg)
  
 下列範例示範套用至文字的模糊效果。  
  
 ![使用 BlurBitmapEffect 的文字陰影](./media/typography-in-wpf/text-shadow-blur-effect.jpg)  

 下列範例示範沿著 X 軸縮放 150% 的第二行文字，以及沿著 Y 軸縮放 150% 的第三行文字。  
  
 ![使用 ScaleTransform 縮放的文字](./media/typography-in-wpf/scaled-text-scaletransform.jpg)
  
 下列範例顯示沿著 X 軸扭曲的文字。  
  
 ![使用 SkewTransform 傾斜的文字](./media/typography-in-wpf/skewed-transformed-text.jpg)
  
 物件<xref:System.Windows.Media.TextEffect>是説明物件，允許您將文本視為文本字串中的一個或多個字元組。 下列範例示範旋轉個別字元。 每一個字元會以 1 秒的間隔獨立旋轉。  
  
 ![旋轉文字的文字效果螢幕擷取畫面](./media/typography-in-wpf/rotating-text-effect.jpg)
  
#### <a name="using-flow-documents"></a>使用非固定格式文件  
 除了公共[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]控制項之外，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]還提供文本表示的佈局控制項 -<xref:System.Windows.Documents.FlowDocument>元素。 該<xref:System.Windows.Documents.FlowDocument>元素與元素<xref:System.Windows.Controls.DocumentViewer>結合，為具有不同佈局要求的大量文本提供了控制項。 佈局控制項通過<xref:System.Windows.Documents.Typography>其他[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]控制項的物件和字體相關屬性提供對高級排版的訪問。  
  
 下面的示例顯示 託管在 中的文本<xref:System.Windows.Controls.FlowDocumentReader>內容，該內容提供搜索、導航、分頁和內容縮放支援。  
  
 ![顯示"打開字體"的螢幕截圖。](./media/typography-in-wpf/typography-text-flowdocumentreader.png)
  
 如需詳細資訊，請參閱 [WPF 中的文件](documents-in-wpf.md)。  
  
### <a name="lightweight-text-drawing"></a>輕量型文字繪製  
 可以使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Media.DrawingContext>物件<xref:System.Windows.Media.DrawingContext.DrawText%2A>的方法將文本直接繪製到物件。 要使用此方法，請創建一個<xref:System.Windows.Media.FormattedText>物件。 這個物件可讓您繪製多行文字，且可個別格式化文字中的每個字元。 <xref:System.Windows.Media.FormattedText>物件的功能包含 Windows API 中 DrawText 標誌的大部分功能。 此外，該<xref:System.Windows.Media.FormattedText>物件包含橢圓支援等功能，在其中，當文本超出其邊界時，將顯示省略號。 下列範例示範的文字具有數種已套用的格式，包括第二個和第三個字的線性漸層。  
  
 ![使用 FormattedText 物件顯示的文字](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)
  
 您可以將格式化的文本轉換為<xref:System.Windows.Media.Geometry>物件，從而創建其他類型的視覺上有趣的文本。 例如，可以基於文本字串的<xref:System.Windows.Media.Geometry>輪廓創建物件。  
  
 ![以線性漸層筆刷繪製外框的文字](./media/typography-in-wpf/text-outline-linear-gradient.jpg)  
  
 下列範例示範數種方式，可透過修改筆劃、填滿和反白顯示轉換的文字，來建立有趣的視覺效果。  
  
 ![使用不同填色和筆觸色彩的文字](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![影像筆刷套用至筆觸的文字](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![應用影像筆刷進行描邊和高光的文本](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 有關物件的詳細資訊，<xref:System.Windows.Media.FormattedText>請參閱[繪製格式化文字](drawing-formatted-text.md)。  
  
### <a name="advanced-text-formatting"></a>進階文字格式化  
 在文本 API 的最高級級別，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使您能夠使用<xref:System.Windows.Media.TextFormatting.TextFormatter><xref:System.Windows.Media.TextFormatting>命名空間中的物件和其他類型創建自訂文本佈局。 <xref:System.Windows.Media.TextFormatting.TextFormatter>和相關類允許您實現自訂文本佈局，該佈局支援您自己的國際文本字元格式、段落樣式、換行規則和其他佈局功能的定義。 在非常少數的情況下，您會想要覆寫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 文字配置支援的預設實作。 不過，如果您要建立文字編輯控制項或應用程式，您可能需要不同於預設 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作的實作。  
  
 與傳統文本 API 不同，<xref:System.Windows.Media.TextFormatting.TextFormatter>通過一組回檔方法與文本佈局用戶端進行交互。 它要求用戶端在<xref:System.Windows.Media.TextFormatting.TextSource>類的實現中提供這些方法。 下圖說明瞭用戶端應用程式和<xref:System.Windows.Media.TextFormatting.TextFormatter>之間的文本佈局交互。  
  
 ![文字配置用戶端和 TextFormatter 的圖表](./media/typography-in-wpf/text-layout-text-formatter-interaction.png)  
  
 如需如何建立自訂文字版面配置的詳細資訊，請參閱[進階文字格式化](advanced-text-formatting.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.FormattedText>
- <xref:System.Windows.Media.TextFormatting.TextFormatter>
- [ClearType 概觀](cleartype-overview.md)
- [OpenType 字型功能](opentype-font-features.md)
- [繪製格式化的文字](drawing-formatted-text.md)
- [高級文本格式](advanced-text-formatting.md)
- [文本](optimizing-performance-text.md)
- [Microsoft 印刷樣式](https://docs.microsoft.com/typography/)
