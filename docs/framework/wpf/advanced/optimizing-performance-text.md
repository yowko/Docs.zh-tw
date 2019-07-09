---
title: 最佳化效能：文字
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
ms.openlocfilehash: 67549e75244790973554d08de8f4dac99d28bd80
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67660766"
---
# <a name="optimizing-performance-text"></a>最佳化效能：文字

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 支援透過使用功能豐富的 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 控制項來呈現文字內容。 一般而言，您可以將文字轉譯劃分為三個層級：

1. 使用<xref:System.Windows.Documents.Glyphs>和<xref:System.Windows.Media.GlyphRun>直接物件。

2. 使用<xref:System.Windows.Media.FormattedText>物件。

3. 使用高階的控制項，例如<xref:System.Windows.Controls.TextBlock>和<xref:System.Windows.Documents.FlowDocument>物件。

本主題提供文字轉譯的效能建議。

<a name="Glyph_Level"></a>

## <a name="rendering-text-at-the-glyph-level"></a>在圖像層級轉譯文字

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供進階的文字支援包括圖像層級標記，直接存取<xref:System.Windows.Documents.Glyphs>客戶想要攔截和保存格式化之後的文字。 這些功能可針對下列每個案例中的不同文字轉譯需求提供重要支援。

- 固定格式文件的螢幕顯示。

- 列印案例。

  - 使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 作為裝置印表機語言。

  - [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)].

  - 先前的印表機驅動程式，從 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 應用程式輸出為固定格式。

  - 列印多工緩衝處理格式。

- 固定格式文件呈現，包括舊版 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 和其他電腦裝置的用戶端。

> [!NOTE]
> <xref:System.Windows.Documents.Glyphs> 和<xref:System.Windows.Media.GlyphRun>專為固定格式文件展示及列印案例。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供數個項目用於一般配置和[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]運用於如下案例<xref:System.Windows.Controls.Label>和<xref:System.Windows.Controls.TextBlock>。 如需配置和 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 案例的詳細資訊，請參閱 [WPF 中的印刷樣式](typography-in-wpf.md)。

下列範例示範如何定義的屬性<xref:System.Windows.Documents.Glyphs>物件中[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。 <xref:System.Windows.Documents.Glyphs>物件所表示的輸出<xref:System.Windows.Media.GlyphRun>在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 此範例假設 Arial、Courier New 和 Times New Roman 字型會安裝在本機電腦的 **C:\WINDOWS\Fonts** 資料夾。

[!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]

### <a name="using-drawglyphrun"></a>使用 DrawGlyphRun

如果您有自訂控制項，而且您想要轉譯圖像 （glyph），請使用<xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A>方法。

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 也提供自訂文字格式設定使用的較低層級服務<xref:System.Windows.Media.FormattedText>物件。 中的轉譯文字的最有效率的方式[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]是藉由產生在圖像層級使用的文字內容<xref:System.Windows.Documents.Glyphs>和<xref:System.Windows.Media.GlyphRun>。 不過，這種效率的成本會遺失任何即可輕易使用 rtf 文字格式，也就是內建功能的[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]控制項，例如<xref:System.Windows.Controls.TextBlock>和<xref:System.Windows.Documents.FlowDocument>。

<a name="FormattedText_Object"></a>

## <a name="formattedtext-object"></a>FormattedText 物件

<xref:System.Windows.Media.FormattedText>物件可讓您繪製多行文字，可以個別格式化文字中的每個字元。 如需詳細資訊，請參閱[繪製格式化的文字](drawing-formatted-text.md)。

若要建立格式化的文字，請呼叫<xref:System.Windows.Media.FormattedText.%23ctor%2A>建構函式建立<xref:System.Windows.Media.FormattedText>物件。 建立初始的格式化文字字串之後，您就可以套用一系列的格式化樣式。 如果您的應用程式想要實作自己的配置，則<xref:System.Windows.Media.FormattedText>物件是比較好的選擇，比使用控制項，例如<xref:System.Windows.Controls.TextBlock>。 如需詳細資訊<xref:System.Windows.Media.FormattedText>物件，請參閱 <<c2> [ 繪製格式化的文字](drawing-formatted-text.md)。

<xref:System.Windows.Media.FormattedText>物件會提供低階的文字格式設定功能。 您可以將多個格式化樣式套用到一或多個字元。 例如，您可以呼叫這兩<xref:System.Windows.Media.FormattedText.SetFontSize%2A>和<xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A>方法來變更文字中的前五個字元的格式。

下列程式碼範例會建立<xref:System.Windows.Media.FormattedText>物件，並呈現它。

[!code-csharp[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
[!code-vb[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]

<a name="FlowDocument_TextBlock_Label"></a>

## <a name="flowdocument-textblock-and-label-controls"></a>FlowDocument、TextBlock 和 Label 控制項

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包含多個將文字繪製到螢幕的控制項。 每個控制項都是針對不同案例，而且有自己的功能與限制清單。

### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a>FlowDocument 對效能的影響超過 TextBlock 或 Label

一般情況下，<xref:System.Windows.Controls.TextBlock>必要項目，例如一個簡短的句子，在有限的文字支援時，就應該使用項目[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]。 <xref:System.Windows.Controls.Label> 需要最少的文字支援時，可以使用。 <xref:System.Windows.Documents.FlowDocument>元素是支援豐富呈現內容，自動重排文件的容器，因此，具有比使用更高的效能影響<xref:System.Windows.Controls.TextBlock>或<xref:System.Windows.Controls.Label>控制項。

如需詳細資訊<xref:System.Windows.Documents.FlowDocument>，請參閱 <<c2> [ 非固定格式文件概觀](flow-document-overview.md)。

### <a name="avoid-using-textblock-in-flowdocument"></a>避免在 FlowDocument 中使用 TextBlock

<xref:System.Windows.Controls.TextBlock>項目衍生自<xref:System.Windows.UIElement>。 <xref:System.Windows.Documents.Run>項目衍生自<xref:System.Windows.Documents.TextElement>，這是比使用成本更低<xref:System.Windows.UIElement>-衍生物件。 可能的話，請使用<xref:System.Windows.Documents.Run>而非<xref:System.Windows.Controls.TextBlock>來顯示文字內容中<xref:System.Windows.Documents.FlowDocument>。

下列標記範例說明兩種方式設定內的文字內容的<xref:System.Windows.Documents.FlowDocument>:

[!code-xaml[Performance#PerformanceSnippet13](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]

### <a name="avoid-using-run-to-set-text-properties"></a>避免使用 Run 來設定文字屬性

一般情況下，使用<xref:System.Windows.Documents.Run>內<xref:System.Windows.Controls.TextBlock>是更高的效能比不使用 明確大量<xref:System.Windows.Documents.Run>所有物件。 如果您使用<xref:System.Windows.Documents.Run>若要設定文字屬性，設定這些屬性直接在<xref:System.Windows.Controls.TextBlock>改。

下列標記範例說明如何設定文字屬性，在此情況下，這兩種方式<xref:System.Windows.Controls.TextBlock.FontWeight%2A>屬性：

[!code-xaml[Performance#PerformanceSnippet12](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]

下表顯示顯示 1000年個的成本<xref:System.Windows.Controls.TextBlock>物件，包含或不含明確<xref:System.Windows.Documents.Run>。

|**TextBlock 類型**|**建立時間 (毫秒)**|**轉譯時間 (毫秒)**|
|------------------------|------------------------------|----------------------------|
|Run 設定文字屬性|146|540|
|TextBlock 設定文字屬性|43|453|

### <a name="avoid-databinding-to-the-labelcontent-property"></a>避免資料繫結至 Label.Content 屬性

假設您有一種情況<xref:System.Windows.Controls.Label>物件，會經常更新從<xref:System.String>來源。 當資料繫結<xref:System.Windows.Controls.Label>項目的<xref:System.Windows.Controls.ContentControl.Content%2A>屬性設<xref:System.String>來源物件，您可能會遇到效能不佳。 每次來源<xref:System.String>更新時，舊<xref:System.String>物件是捨棄，並使用新<xref:System.String>會重新建立，因為<xref:System.String>物件是不可變、 無法修改。 這會導致<xref:System.Windows.Controls.ContentPresenter>的<xref:System.Windows.Controls.Label>捨棄其舊內容，並重新產生新的內容，以顯示新的物件<xref:System.String>。

這個問題的解決方法很簡單。 如果<xref:System.Windows.Controls.Label>未設為自訂<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>值，取代<xref:System.Windows.Controls.Label>具有<xref:System.Windows.Controls.TextBlock>和資料繫結其<xref:System.Windows.Controls.TextBlock.Text%2A>來源字串的屬性。

|**資料繫結屬性**|**更新時間 (毫秒)**|
|-----------------------------|----------------------------|
|Label.Content|835|
|TextBlock.Text|242|

<a name="Hyperlink"></a>

## <a name="hyperlink"></a>超連結

<xref:System.Windows.Documents.Hyperlink>物件是內嵌層級非固定格式內容項目，可讓您將非固定格式內容內超連結。

### <a name="combine-hyperlinks-in-one-textblock-object"></a>在一個 TextBlock 物件中合併超連結

您可以最佳化使用多個<xref:System.Windows.Documents.Hyperlink>藉由將它們群組在一起在相同的項目<xref:System.Windows.Controls.TextBlock>。 這可讓您在應用程式中建立的物件數目降到最低。 例如，您可能想要顯示多個超連結，如下所示：

MSN 首頁 | 我的 MSN

下列標記範例示範多個<xref:System.Windows.Controls.TextBlock>用來顯示超連結項目：

[!code-xaml[Performance#PerformanceSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]

下列標記範例示範更有效率的方式顯示的超連結，此期間，使用單一<xref:System.Windows.Controls.TextBlock>:

[!code-xaml[Performance#PerformanceSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]

### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a>只在 MouseEnter 事件的超連結上顯示底線

A<xref:System.Windows.TextDecoration>物件是您可以新增至文字的視覺裝飾; 然而，它可以是效能密集具現化。 若要大量使用<xref:System.Windows.Documents.Hyperlink>項目，請考慮這類觸發事件時，才顯示底線<xref:System.Windows.ContentElement.MouseEnter>事件。 如需詳細資訊，請參閱[指定超連結是否要加上底線](how-to-specify-whether-a-hyperlink-is-underlined.md)。

下圖顯示 MouseEnter 事件觸發的加底線的超連結的方式：

![顯示 TextDecoration 的超連結](./media/how-to-specify-whether-a-hyperlink-is-underlined/text-decorations-hyperlinks.png)

下列標記範例示範<xref:System.Windows.Documents.Hyperlink>定義不含底線與：

[!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]

下表顯示的效能成本，顯示 1000年個<xref:System.Windows.Documents.Hyperlink>與且不含底線的項目。

|**超連結**|**建立時間 (毫秒)**|**轉譯時間 (毫秒)**|
|-------------------|------------------------------|----------------------------|
|包含底線|289|1130|
|不含底線|299|776|

<a name="Text_Formatting_Features"></a>

## <a name="text-formatting-features"></a>文字格式設定功能

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供 RTF 文字格式設定服務，例如自動斷字。 這些服務可能會影響應用程式效能，只有在必要時才應使用。

### <a name="avoid-unnecessary-use-of-hyphenation"></a>避免使用不必要的斷字

自動斷字功能尋找的文字行，連字號中斷點，並允許其他中斷位置中的線條<xref:System.Windows.Controls.TextBlock>和<xref:System.Windows.Documents.FlowDocument>物件。 這些物件預設已停用自動斷字功能。 您可以將物件的 IsHyphenationEnabled 屬性設定為 `true` 來啟用此功能。 然而，啟用此功能會導致 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 起始 [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)] 的互通性，這可能會影響應用程式效能。 若非必要，建議您不要使用自動斷字功能。

### <a name="use-figures-carefully"></a>小心使用圖表

A<xref:System.Windows.Documents.Figure>項目代表可以一頁內容內絕對位置的非固定格式內容的一部分。 在某些情況下，<xref:System.Windows.Documents.Figure>可能會造成整個頁面自動重新設定格式，如果它的位置相衝突已配置的內容。您可以不需要重新格式化，任一個分組的可能性降至最低<xref:System.Windows.Documents.Figure>旁，或在固定的頁面大小的案例中的內容頂端附近宣告這些項目。

### <a name="optimal-paragraph"></a>最佳段落

最佳段落功能<xref:System.Windows.Documents.FlowDocument>物件配置段落，讓空白字元盡量平均分散。 依預設已停用最佳段落功能。 您可以啟用此功能藉由設定物件的<xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A>屬性設`true`。 不過，啟用此功能會影響應用程式效能。 若非必要，建議您不要使用最佳段落功能。

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
