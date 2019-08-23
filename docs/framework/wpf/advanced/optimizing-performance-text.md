---
title: 優化效能:文字
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- rendering text [WPF]
- hyperlinks [WPF]
- formatted text [WPF]
- text [WPF], performance
- glyphs [WPF]
ms.assetid: 66b1b9a7-8618-48db-b616-c57ea4327b98
ms.openlocfilehash: 318972c20f6461489226e19b3e517ba0ac069b28
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933357"
---
# <a name="optimizing-performance-text"></a>優化效能:文字

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 支援透過使用功能豐富的 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 控制項來呈現文字內容。 一般而言，您可以將文字轉譯劃分為三個層級：

1. 直接使用<xref:System.Windows.Media.GlyphRun>和物件。 <xref:System.Windows.Documents.Glyphs>

2. <xref:System.Windows.Media.FormattedText>使用物件。

3. 使用高層級的<xref:System.Windows.Controls.TextBlock>控制項, 例如和<xref:System.Windows.Documents.FlowDocument>物件。

本主題提供文字轉譯的效能建議。

<a name="Glyph_Level"></a>

## <a name="rendering-text-at-the-glyph-level"></a>在圖像層級轉譯文字

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供先進的文字支援, 包括可<xref:System.Windows.Documents.Glyphs>直接存取的圖像層級標記, 適用于想要在格式化之後攔截並保存文字的客戶。 這些功能可針對下列每個案例中的不同文字轉譯需求提供重要支援。

- 固定格式文件的螢幕顯示。

- 列印案例。

  - 使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 作為裝置印表機語言。

  - Microsoft XPS 檔寫入器。

  - 先前的印表機驅動程式，從 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 應用程式輸出為固定格式。

  - 列印多工緩衝處理格式。

- 固定格式的檔標記法, 包括舊版 Windows 和其他計算裝置的用戶端。

> [!NOTE]
> <xref:System.Windows.Documents.Glyphs>和<xref:System.Windows.Media.GlyphRun>是針對固定格式的檔簡報和列印案例所設計。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]針對一般版面配置和[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]案例<xref:System.Windows.Controls.Label> (例如和<xref:System.Windows.Controls.TextBlock>) 提供數個元素。 如需配置和 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 案例的詳細資訊，請參閱 [WPF 中的印刷樣式](typography-in-wpf.md)。

下列範例示範如何在中<xref:System.Windows.Documents.Glyphs> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]定義物件的屬性。 物件代表<xref:System.Windows.Media.GlyphRun> 中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的輸出。 <xref:System.Windows.Documents.Glyphs> 此範例假設 Arial、Courier New 和 Times New Roman 字型會安裝在本機電腦的 **C:\WINDOWS\Fonts** 資料夾。

[!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]

### <a name="using-drawglyphrun"></a>使用 DrawGlyphRun

如果您有自訂控制項, 而且想要轉譯圖像, 請<xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A>使用方法。

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]也會透過使用<xref:System.Windows.Media.FormattedText>物件, 提供較低層級的自訂文字格式服務。 在中[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]轉譯文字最有效率的方式, 就是使用<xref:System.Windows.Documents.Glyphs>和<xref:System.Windows.Media.GlyphRun>在圖像層級產生文字內容。 不過, 這項效率的代價是, 不容易使用 rtf 格式, 這是控制項的[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]內建功能, <xref:System.Windows.Controls.TextBlock>例如和<xref:System.Windows.Documents.FlowDocument>。

<a name="FormattedText_Object"></a>

## <a name="formattedtext-object"></a>FormattedText 物件

<xref:System.Windows.Media.FormattedText>物件可讓您繪製多行文字, 其中文字中的每個字元都可以個別格式化。 如需詳細資訊，請參閱[繪製格式化的文字](drawing-formatted-text.md)。

若要建立格式化的文字, <xref:System.Windows.Media.FormattedText.%23ctor%2A>請呼叫此函<xref:System.Windows.Media.FormattedText>式來建立物件。 建立初始的格式化文字字串之後，您就可以套用一系列的格式化樣式。 如果您的<xref:System.Windows.Media.FormattedText>應用程式想要執行自己的版面配置, 則物件比使用控制項 ( <xref:System.Windows.Controls.TextBlock>例如) 更適合選擇。 如需物件的<xref:System.Windows.Media.FormattedText>詳細資訊, 請參閱[繪製格式化的文字](drawing-formatted-text.md)。

<xref:System.Windows.Media.FormattedText>物件提供低層級的文字格式化功能。 您可以將多個格式化樣式套用到一或多個字元。 例如, 您可以同時<xref:System.Windows.Media.FormattedText.SetFontSize%2A>呼叫和<xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A>方法, 以變更文字中前五個字元的格式。

下列程式碼範例會建立<xref:System.Windows.Media.FormattedText>物件並加以呈現。

[!code-csharp[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
[!code-vb[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]

<a name="FlowDocument_TextBlock_Label"></a>

## <a name="flowdocument-textblock-and-label-controls"></a>FlowDocument、TextBlock 和 Label 控制項

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包含多個將文字繪製到螢幕的控制項。 每個控制項都是針對不同案例，而且有自己的功能與限制清單。

### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a>FlowDocument 對效能的影響超過 TextBlock 或 Label

一般而言, 需要有限<xref:System.Windows.Controls.TextBlock>的文字支援時 (例如[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]中的簡短句子), 應使用元素。 <xref:System.Windows.Controls.Label>當需要最少的文字支援時, 可以使用。 元素是重新 flowable 檔的容器, 可支援豐富的內容呈現, 因此, 效能的影響會比<xref:System.Windows.Controls.TextBlock>使用或<xref:System.Windows.Controls.Label>控制項更大。 <xref:System.Windows.Documents.FlowDocument>

如需有關的<xref:System.Windows.Documents.FlowDocument>詳細資訊, 請參閱非固定格式[檔總覽](flow-document-overview.md)。

### <a name="avoid-using-textblock-in-flowdocument"></a>避免在 FlowDocument 中使用 TextBlock

元素衍生自<xref:System.Windows.UIElement>。 <xref:System.Windows.Controls.TextBlock> 元素衍生自<xref:System.Windows.Documents.TextElement>, 其使用<xref:System.Windows.UIElement>的成本較低, 而不是衍生物件。 <xref:System.Windows.Documents.Run> 可能的話, 請<xref:System.Windows.Documents.Run>使用, <xref:System.Windows.Controls.TextBlock>而不要在中<xref:System.Windows.Documents.FlowDocument>顯示文字內容。

下列標記範例說明在中<xref:System.Windows.Documents.FlowDocument>設定文字內容的兩種方式:

[!code-xaml[Performance#PerformanceSnippet13](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]

### <a name="avoid-using-run-to-set-text-properties"></a>避免使用 Run 來設定文字屬性

一般而言, 在<xref:System.Windows.Documents.Run> <xref:System.Windows.Controls.TextBlock>中使用會比完全不使用明確<xref:System.Windows.Documents.Run>物件更具效能。 如果您使用<xref:System.Windows.Documents.Run>來設定文字屬性, 請<xref:System.Windows.Controls.TextBlock>改為直接在上設定這些屬性。

下列標記範例說明這兩種設定 text 屬性的方式, 在此案例<xref:System.Windows.Controls.TextBlock.FontWeight%2A>中為屬性:

[!code-xaml[Performance#PerformanceSnippet12](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]

下表顯示顯示包含和不具明確<xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Documents.Run>之1000物件的成本。

|**TextBlock 類型**|**建立時間 (毫秒)**|**轉譯時間 (毫秒)**|
|------------------------|------------------------------|----------------------------|
|Run 設定文字屬性|146|540|
|TextBlock 設定文字屬性|43|453|

### <a name="avoid-databinding-to-the-labelcontent-property"></a>避免資料繫結至 Label.Content 屬性

假設您有<xref:System.Windows.Controls.Label>一個<xref:System.String>從來源經常更新之物件的案例。 當資料<xref:System.Windows.Controls.Label>將專案的<xref:System.Windows.Controls.ContentControl.Content%2A>屬性系結至<xref:System.String>來源物件時, 您可能會遇到效能不佳的情況。 每次更新來源<xref:System.String>時, 就會捨棄<xref:System.String>舊的物件, 並重新<xref:System.String>建立新的, 因為<xref:System.String>物件是不可變的, 無法修改。 接著, 這會導致<xref:System.Windows.Controls.ContentPresenter> <xref:System.Windows.Controls.Label>物件的捨棄舊內容, 並重新產生新的內容以顯示新<xref:System.String>的。

這個問題的解決方法很簡單。 <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.TextBlock.Text%2A>如果未設定為自訂<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>值, 請將取代為, 並將其屬性系結至來源字串。 <xref:System.Windows.Controls.Label>

|**資料繫結屬性**|**更新時間 (毫秒)**|
|-----------------------------|----------------------------|
|Label.Content|835|
|TextBlock.Text|242|

<a name="Hyperlink"></a>

## <a name="hyperlink"></a>超連結

<xref:System.Windows.Documents.Hyperlink>物件是內嵌層級的非固定格式內容專案, 可讓您在流程內容中裝載超連結。

### <a name="combine-hyperlinks-in-one-textblock-object"></a>在一個 TextBlock 物件中合併超連結

您可以將多個<xref:System.Windows.Documents.Hyperlink>專案的使用方式, 藉由將它們群組在相同<xref:System.Windows.Controls.TextBlock>的一起進行優化。 這可讓您在應用程式中建立的物件數目降到最低。 例如，您可能想要顯示多個超連結，如下所示：

MSN 首頁 | 我的 MSN

下列標記範例顯示用來<xref:System.Windows.Controls.TextBlock>顯示超連結的多個元素:

[!code-xaml[Performance#PerformanceSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]

下列標記範例顯示更有效率的方式來顯示超連結, 這次是使用單一<xref:System.Windows.Controls.TextBlock>的:

[!code-xaml[Performance#PerformanceSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]

### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a>只在 MouseEnter 事件的超連結上顯示底線

<xref:System.Windows.TextDecoration>物件是您可以加入至文字的視覺精心設計且; 不過, 具現化可能需要大量的效能。 如果您大量使用<xref:System.Windows.Documents.Hyperlink>元素, 請考慮只在觸發事件時顯示底線, 例如<xref:System.Windows.ContentElement.MouseEnter>事件。 如需詳細資訊，請參閱[指定超連結是否要加上底線](how-to-specify-whether-a-hyperlink-is-underlined.md)。

下圖顯示 MouseEnter 事件如何觸發加底線的超連結:

![顯示 TextDecoration 的超連結](./media/how-to-specify-whether-a-hyperlink-is-underlined/text-decorations-hyperlinks.png)

下列標記範例顯示<xref:System.Windows.Documents.Hyperlink>定義了且不含底線的:

[!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]

下表顯示顯示包含和不含底線之<xref:System.Windows.Documents.Hyperlink> 1000 元素的效能成本。

|**超連結**|**建立時間 (毫秒)**|**轉譯時間 (毫秒)**|
|-------------------|------------------------------|----------------------------|
|包含底線|289|1130|
|不含底線|299|776|

<a name="Text_Formatting_Features"></a>

## <a name="text-formatting-features"></a>文字格式設定功能

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供 RTF 文字格式設定服務，例如自動斷字。 這些服務可能會影響應用程式效能，只有在必要時才應使用。

### <a name="avoid-unnecessary-use-of-hyphenation"></a>避免使用不必要的斷字

自動斷字會尋找文字行的連字號中斷點, 並允許和<xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Documents.FlowDocument>物件中的行有額外的中斷點位置。 這些物件預設已停用自動斷字功能。 您可以將物件的 IsHyphenationEnabled 屬性設定為 `true` 來啟用此功能。 不過, 啟用此功能會[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]導致起始元件物件模型 (COM) 互通性, 這可能會影響應用程式效能。 若非必要，建議您不要使用自動斷字功能。

### <a name="use-figures-carefully"></a>小心使用圖表

<xref:System.Windows.Documents.Figure>元素代表可以在內容頁面中絕對位置的部分流動內容。 在某些情況下, <xref:System.Windows.Documents.Figure>如果其位置與已經配置的內容衝突, 可能會導致整個頁面自動重新格式化。您可以將不必要的重新格式化的可能性降<xref:System.Windows.Documents.Figure>到最低, 方法是將專案彼此分組, 或在固定頁面大小案例中接近內容的頂端。

### <a name="optimal-paragraph"></a>最佳段落

<xref:System.Windows.Documents.FlowDocument>物件的最佳段落功能會配置段落, 讓泛空白字元盡可能平均地散發。 依預設已停用最佳段落功能。 您可以藉由將物件的<xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A>屬性設定為來`true`啟用此功能。 不過，啟用此功能會影響應用程式效能。 若非必要，建議您不要使用最佳段落功能。

## <a name="see-also"></a>另請參閱

- [最佳化 WPF 應用程式效能](optimizing-wpf-application-performance.md)
- [應用程式效能規劃](planning-for-application-performance.md)
- [運用硬體](optimizing-performance-taking-advantage-of-hardware.md)
- [版面配置與設計](optimizing-performance-layout-and-design.md)
- [2D 圖形和影像處理](optimizing-performance-2d-graphics-and-imaging.md)
- [物件行為](optimizing-performance-object-behavior.md)
- [應用程式資源](optimizing-performance-application-resources.md)
- [資料繫結](optimizing-performance-data-binding.md)
- [其他效能建議](optimizing-performance-other-recommendations.md)
