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
# <a name="optimizing-performance-text"></a><span data-ttu-id="60b14-102">優化效能:文字</span><span class="sxs-lookup"><span data-stu-id="60b14-102">Optimizing Performance: Text</span></span>

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="60b14-103">支援透過使用功能豐富的 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 控制項來呈現文字內容。</span><span class="sxs-lookup"><span data-stu-id="60b14-103">includes support for the presentation of text content through the use of feature-rich [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] controls.</span></span> <span data-ttu-id="60b14-104">一般而言，您可以將文字轉譯劃分為三個層級：</span><span class="sxs-lookup"><span data-stu-id="60b14-104">In general you can divide text rendering in three layers:</span></span>

1. <span data-ttu-id="60b14-105">直接使用<xref:System.Windows.Media.GlyphRun>和物件。 <xref:System.Windows.Documents.Glyphs></span><span class="sxs-lookup"><span data-stu-id="60b14-105">Using the <xref:System.Windows.Documents.Glyphs> and <xref:System.Windows.Media.GlyphRun> objects directly.</span></span>

2. <span data-ttu-id="60b14-106"><xref:System.Windows.Media.FormattedText>使用物件。</span><span class="sxs-lookup"><span data-stu-id="60b14-106">Using the <xref:System.Windows.Media.FormattedText> object.</span></span>

3. <span data-ttu-id="60b14-107">使用高層級的<xref:System.Windows.Controls.TextBlock>控制項, 例如和<xref:System.Windows.Documents.FlowDocument>物件。</span><span class="sxs-lookup"><span data-stu-id="60b14-107">Using high-level controls, such as the <xref:System.Windows.Controls.TextBlock> and <xref:System.Windows.Documents.FlowDocument> objects.</span></span>

<span data-ttu-id="60b14-108">本主題提供文字轉譯的效能建議。</span><span class="sxs-lookup"><span data-stu-id="60b14-108">This topic provides text rendering performance recommendations.</span></span>

<a name="Glyph_Level"></a>

## <a name="rendering-text-at-the-glyph-level"></a><span data-ttu-id="60b14-109">在圖像層級轉譯文字</span><span class="sxs-lookup"><span data-stu-id="60b14-109">Rendering Text at the Glyph Level</span></span>

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="60b14-110">提供先進的文字支援, 包括可<xref:System.Windows.Documents.Glyphs>直接存取的圖像層級標記, 適用于想要在格式化之後攔截並保存文字的客戶。</span><span class="sxs-lookup"><span data-stu-id="60b14-110">provides advanced text support including glyph-level markup with direct access to <xref:System.Windows.Documents.Glyphs> for customers who want to intercept and persist text after formatting.</span></span> <span data-ttu-id="60b14-111">這些功能可針對下列每個案例中的不同文字轉譯需求提供重要支援。</span><span class="sxs-lookup"><span data-stu-id="60b14-111">These features provide critical support for the different text rendering requirements in each of the following scenarios.</span></span>

- <span data-ttu-id="60b14-112">固定格式文件的螢幕顯示。</span><span class="sxs-lookup"><span data-stu-id="60b14-112">Screen display of fixed-format documents.</span></span>

- <span data-ttu-id="60b14-113">列印案例。</span><span class="sxs-lookup"><span data-stu-id="60b14-113">Print scenarios.</span></span>

  - <span data-ttu-id="60b14-114">使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 作為裝置印表機語言。</span><span class="sxs-lookup"><span data-stu-id="60b14-114">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] as a device printer language.</span></span>

  - <span data-ttu-id="60b14-115">Microsoft XPS 檔寫入器。</span><span class="sxs-lookup"><span data-stu-id="60b14-115">Microsoft XPS Document Writer.</span></span>

  - <span data-ttu-id="60b14-116">先前的印表機驅動程式，從 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 應用程式輸出為固定格式。</span><span class="sxs-lookup"><span data-stu-id="60b14-116">Previous printer drivers, output from [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications to the fixed format.</span></span>

  - <span data-ttu-id="60b14-117">列印多工緩衝處理格式。</span><span class="sxs-lookup"><span data-stu-id="60b14-117">Print spool format.</span></span>

- <span data-ttu-id="60b14-118">固定格式的檔標記法, 包括舊版 Windows 和其他計算裝置的用戶端。</span><span class="sxs-lookup"><span data-stu-id="60b14-118">Fixed-format document representation, including clients for previous versions of Windows and other computing devices.</span></span>

> [!NOTE]
> <span data-ttu-id="60b14-119"><xref:System.Windows.Documents.Glyphs>和<xref:System.Windows.Media.GlyphRun>是針對固定格式的檔簡報和列印案例所設計。</span><span class="sxs-lookup"><span data-stu-id="60b14-119"><xref:System.Windows.Documents.Glyphs> and <xref:System.Windows.Media.GlyphRun> are designed for fixed-format document presentation and print scenarios.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="60b14-120">針對一般版面配置和[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]案例<xref:System.Windows.Controls.Label> (例如和<xref:System.Windows.Controls.TextBlock>) 提供數個元素。</span><span class="sxs-lookup"><span data-stu-id="60b14-120">provides several elements for general layout and [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenarios such as <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="60b14-121">如需配置和 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 案例的詳細資訊，請參閱 [WPF 中的印刷樣式](typography-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="60b14-121">For more information on layout and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenarios, see the [Typography in WPF](typography-in-wpf.md).</span></span>

<span data-ttu-id="60b14-122">下列範例示範如何在中<xref:System.Windows.Documents.Glyphs> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]定義物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="60b14-122">The following examples show how to define properties for a <xref:System.Windows.Documents.Glyphs> object in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="60b14-123">物件代表<xref:System.Windows.Media.GlyphRun> 中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的輸出。 <xref:System.Windows.Documents.Glyphs></span><span class="sxs-lookup"><span data-stu-id="60b14-123">The <xref:System.Windows.Documents.Glyphs> object represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="60b14-124">此範例假設 Arial、Courier New 和 Times New Roman 字型會安裝在本機電腦的 **C:\WINDOWS\Fonts** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="60b14-124">The examples assume that the Arial, Courier New, and Times New Roman fonts are installed in the **C:\WINDOWS\Fonts** folder on the local computer.</span></span>

[!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]

### <a name="using-drawglyphrun"></a><span data-ttu-id="60b14-125">使用 DrawGlyphRun</span><span class="sxs-lookup"><span data-stu-id="60b14-125">Using DrawGlyphRun</span></span>

<span data-ttu-id="60b14-126">如果您有自訂控制項, 而且想要轉譯圖像, 請<xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A>使用方法。</span><span class="sxs-lookup"><span data-stu-id="60b14-126">If you have custom control and you want to render glyphs, use the <xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A> method.</span></span>

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="60b14-127">也會透過使用<xref:System.Windows.Media.FormattedText>物件, 提供較低層級的自訂文字格式服務。</span><span class="sxs-lookup"><span data-stu-id="60b14-127">also provides lower-level services for custom text formatting through the use of the <xref:System.Windows.Media.FormattedText> object.</span></span> <span data-ttu-id="60b14-128">在中[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]轉譯文字最有效率的方式, 就是使用<xref:System.Windows.Documents.Glyphs>和<xref:System.Windows.Media.GlyphRun>在圖像層級產生文字內容。</span><span class="sxs-lookup"><span data-stu-id="60b14-128">The most efficient way of rendering text in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is by generating text content at the glyph level using <xref:System.Windows.Documents.Glyphs> and <xref:System.Windows.Media.GlyphRun>.</span></span> <span data-ttu-id="60b14-129">不過, 這項效率的代價是, 不容易使用 rtf 格式, 這是控制項的[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]內建功能, <xref:System.Windows.Controls.TextBlock>例如和<xref:System.Windows.Documents.FlowDocument>。</span><span class="sxs-lookup"><span data-stu-id="60b14-129">However, the cost of this efficiency is the loss of easy to use rich text formatting, which are built-in features of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] controls, such as <xref:System.Windows.Controls.TextBlock> and <xref:System.Windows.Documents.FlowDocument>.</span></span>

<a name="FormattedText_Object"></a>

## <a name="formattedtext-object"></a><span data-ttu-id="60b14-130">FormattedText 物件</span><span class="sxs-lookup"><span data-stu-id="60b14-130">FormattedText Object</span></span>

<span data-ttu-id="60b14-131"><xref:System.Windows.Media.FormattedText>物件可讓您繪製多行文字, 其中文字中的每個字元都可以個別格式化。</span><span class="sxs-lookup"><span data-stu-id="60b14-131">The <xref:System.Windows.Media.FormattedText> object allows you to draw multi-line text, in which each character in the text can be individually formatted.</span></span> <span data-ttu-id="60b14-132">如需詳細資訊，請參閱[繪製格式化的文字](drawing-formatted-text.md)。</span><span class="sxs-lookup"><span data-stu-id="60b14-132">For more information, see [Drawing Formatted Text](drawing-formatted-text.md).</span></span>

<span data-ttu-id="60b14-133">若要建立格式化的文字, <xref:System.Windows.Media.FormattedText.%23ctor%2A>請呼叫此函<xref:System.Windows.Media.FormattedText>式來建立物件。</span><span class="sxs-lookup"><span data-stu-id="60b14-133">To create formatted text, call the <xref:System.Windows.Media.FormattedText.%23ctor%2A> constructor to create a <xref:System.Windows.Media.FormattedText> object.</span></span> <span data-ttu-id="60b14-134">建立初始的格式化文字字串之後，您就可以套用一系列的格式化樣式。</span><span class="sxs-lookup"><span data-stu-id="60b14-134">Once you have created the initial formatted text string, you can apply a range of formatting styles.</span></span> <span data-ttu-id="60b14-135">如果您的<xref:System.Windows.Media.FormattedText>應用程式想要執行自己的版面配置, 則物件比使用控制項 ( <xref:System.Windows.Controls.TextBlock>例如) 更適合選擇。</span><span class="sxs-lookup"><span data-stu-id="60b14-135">If your application wants to implement its own layout, then the <xref:System.Windows.Media.FormattedText> object is better choice than using a control, such as <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="60b14-136">如需物件的<xref:System.Windows.Media.FormattedText>詳細資訊, 請參閱[繪製格式化的文字](drawing-formatted-text.md)。</span><span class="sxs-lookup"><span data-stu-id="60b14-136">For more information on the <xref:System.Windows.Media.FormattedText> object, see [Drawing Formatted Text](drawing-formatted-text.md) .</span></span>

<span data-ttu-id="60b14-137"><xref:System.Windows.Media.FormattedText>物件提供低層級的文字格式化功能。</span><span class="sxs-lookup"><span data-stu-id="60b14-137">The <xref:System.Windows.Media.FormattedText> object provides low-level text formatting capability.</span></span> <span data-ttu-id="60b14-138">您可以將多個格式化樣式套用到一或多個字元。</span><span class="sxs-lookup"><span data-stu-id="60b14-138">You can apply multiple formatting styles to one or more characters.</span></span> <span data-ttu-id="60b14-139">例如, 您可以同時<xref:System.Windows.Media.FormattedText.SetFontSize%2A>呼叫和<xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A>方法, 以變更文字中前五個字元的格式。</span><span class="sxs-lookup"><span data-stu-id="60b14-139">For example, you could call both the <xref:System.Windows.Media.FormattedText.SetFontSize%2A> and <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> methods to change the formatting of the first five characters in the text.</span></span>

<span data-ttu-id="60b14-140">下列程式碼範例會建立<xref:System.Windows.Media.FormattedText>物件並加以呈現。</span><span class="sxs-lookup"><span data-stu-id="60b14-140">The following code example creates a <xref:System.Windows.Media.FormattedText> object and renders it.</span></span>

[!code-csharp[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
[!code-vb[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]

<a name="FlowDocument_TextBlock_Label"></a>

## <a name="flowdocument-textblock-and-label-controls"></a><span data-ttu-id="60b14-141">FlowDocument、TextBlock 和 Label 控制項</span><span class="sxs-lookup"><span data-stu-id="60b14-141">FlowDocument, TextBlock, and Label Controls</span></span>

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="60b14-142">包含多個將文字繪製到螢幕的控制項。</span><span class="sxs-lookup"><span data-stu-id="60b14-142">includes multiple controls for drawing text to the screen.</span></span> <span data-ttu-id="60b14-143">每個控制項都是針對不同案例，而且有自己的功能與限制清單。</span><span class="sxs-lookup"><span data-stu-id="60b14-143">Each control is targeted to a different scenario and has its own list of features and limitations.</span></span>

### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a><span data-ttu-id="60b14-144">FlowDocument 對效能的影響超過 TextBlock 或 Label</span><span class="sxs-lookup"><span data-stu-id="60b14-144">FlowDocument Impacts Performance More than TextBlock or Label</span></span>

<span data-ttu-id="60b14-145">一般而言, 需要有限<xref:System.Windows.Controls.TextBlock>的文字支援時 (例如[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]中的簡短句子), 應使用元素。</span><span class="sxs-lookup"><span data-stu-id="60b14-145">In general, the <xref:System.Windows.Controls.TextBlock> element should be used when limited text support is required, such as a brief sentence in a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span> <span data-ttu-id="60b14-146"><xref:System.Windows.Controls.Label>當需要最少的文字支援時, 可以使用。</span><span class="sxs-lookup"><span data-stu-id="60b14-146"><xref:System.Windows.Controls.Label> can be used when minimal text support is required.</span></span> <span data-ttu-id="60b14-147">元素是重新 flowable 檔的容器, 可支援豐富的內容呈現, 因此, 效能的影響會比<xref:System.Windows.Controls.TextBlock>使用或<xref:System.Windows.Controls.Label>控制項更大。 <xref:System.Windows.Documents.FlowDocument></span><span class="sxs-lookup"><span data-stu-id="60b14-147">The <xref:System.Windows.Documents.FlowDocument> element is a container for re-flowable documents that support rich presentation of content, and therefore, has a greater performance impact than using the <xref:System.Windows.Controls.TextBlock> or <xref:System.Windows.Controls.Label> controls.</span></span>

<span data-ttu-id="60b14-148">如需有關的<xref:System.Windows.Documents.FlowDocument>詳細資訊, 請參閱非固定格式[檔總覽](flow-document-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="60b14-148">For more information on <xref:System.Windows.Documents.FlowDocument>, see [Flow Document Overview](flow-document-overview.md).</span></span>

### <a name="avoid-using-textblock-in-flowdocument"></a><span data-ttu-id="60b14-149">避免在 FlowDocument 中使用 TextBlock</span><span class="sxs-lookup"><span data-stu-id="60b14-149">Avoid Using TextBlock in FlowDocument</span></span>

<span data-ttu-id="60b14-150">元素衍生自<xref:System.Windows.UIElement>。 <xref:System.Windows.Controls.TextBlock></span><span class="sxs-lookup"><span data-stu-id="60b14-150">The <xref:System.Windows.Controls.TextBlock> element is derived from <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="60b14-151">元素衍生自<xref:System.Windows.Documents.TextElement>, 其使用<xref:System.Windows.UIElement>的成本較低, 而不是衍生物件。 <xref:System.Windows.Documents.Run></span><span class="sxs-lookup"><span data-stu-id="60b14-151">The <xref:System.Windows.Documents.Run> element is derived from <xref:System.Windows.Documents.TextElement>, which is less costly to use than a <xref:System.Windows.UIElement>-derived object.</span></span> <span data-ttu-id="60b14-152">可能的話, 請<xref:System.Windows.Documents.Run>使用, <xref:System.Windows.Controls.TextBlock>而不要在中<xref:System.Windows.Documents.FlowDocument>顯示文字內容。</span><span class="sxs-lookup"><span data-stu-id="60b14-152">When possible, use <xref:System.Windows.Documents.Run> rather than <xref:System.Windows.Controls.TextBlock> for displaying text content in a <xref:System.Windows.Documents.FlowDocument>.</span></span>

<span data-ttu-id="60b14-153">下列標記範例說明在中<xref:System.Windows.Documents.FlowDocument>設定文字內容的兩種方式:</span><span class="sxs-lookup"><span data-stu-id="60b14-153">The following markup sample illustrates two ways of setting text content within a <xref:System.Windows.Documents.FlowDocument>:</span></span>

[!code-xaml[Performance#PerformanceSnippet13](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]

### <a name="avoid-using-run-to-set-text-properties"></a><span data-ttu-id="60b14-154">避免使用 Run 來設定文字屬性</span><span class="sxs-lookup"><span data-stu-id="60b14-154">Avoid Using Run to Set Text Properties</span></span>

<span data-ttu-id="60b14-155">一般而言, 在<xref:System.Windows.Documents.Run> <xref:System.Windows.Controls.TextBlock>中使用會比完全不使用明確<xref:System.Windows.Documents.Run>物件更具效能。</span><span class="sxs-lookup"><span data-stu-id="60b14-155">In general, using a <xref:System.Windows.Documents.Run> within a <xref:System.Windows.Controls.TextBlock> is more performance intensive than not using an explicit <xref:System.Windows.Documents.Run> object at all.</span></span> <span data-ttu-id="60b14-156">如果您使用<xref:System.Windows.Documents.Run>來設定文字屬性, 請<xref:System.Windows.Controls.TextBlock>改為直接在上設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="60b14-156">If you are using a <xref:System.Windows.Documents.Run> in order to set text properties, set those properties directly on the <xref:System.Windows.Controls.TextBlock> instead.</span></span>

<span data-ttu-id="60b14-157">下列標記範例說明這兩種設定 text 屬性的方式, 在此案例<xref:System.Windows.Controls.TextBlock.FontWeight%2A>中為屬性:</span><span class="sxs-lookup"><span data-stu-id="60b14-157">The following markup sample illustrates these two ways of setting a text property, in this case, the <xref:System.Windows.Controls.TextBlock.FontWeight%2A> property:</span></span>

[!code-xaml[Performance#PerformanceSnippet12](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]

<span data-ttu-id="60b14-158">下表顯示顯示包含和不具明確<xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Documents.Run>之1000物件的成本。</span><span class="sxs-lookup"><span data-stu-id="60b14-158">The following table shows the cost of displaying 1000 <xref:System.Windows.Controls.TextBlock> objects with and without an explicit <xref:System.Windows.Documents.Run>.</span></span>

|<span data-ttu-id="60b14-159">**TextBlock 類型**</span><span class="sxs-lookup"><span data-stu-id="60b14-159">**TextBlock type**</span></span>|<span data-ttu-id="60b14-160">**建立時間 (毫秒)**</span><span class="sxs-lookup"><span data-stu-id="60b14-160">**Creation time (ms)**</span></span>|<span data-ttu-id="60b14-161">**轉譯時間 (毫秒)**</span><span class="sxs-lookup"><span data-stu-id="60b14-161">**Render time (ms)**</span></span>|
|------------------------|------------------------------|----------------------------|
|<span data-ttu-id="60b14-162">Run 設定文字屬性</span><span class="sxs-lookup"><span data-stu-id="60b14-162">Run setting text properties</span></span>|<span data-ttu-id="60b14-163">146</span><span class="sxs-lookup"><span data-stu-id="60b14-163">146</span></span>|<span data-ttu-id="60b14-164">540</span><span class="sxs-lookup"><span data-stu-id="60b14-164">540</span></span>|
|<span data-ttu-id="60b14-165">TextBlock 設定文字屬性</span><span class="sxs-lookup"><span data-stu-id="60b14-165">TextBlock setting text properties</span></span>|<span data-ttu-id="60b14-166">43</span><span class="sxs-lookup"><span data-stu-id="60b14-166">43</span></span>|<span data-ttu-id="60b14-167">453</span><span class="sxs-lookup"><span data-stu-id="60b14-167">453</span></span>|

### <a name="avoid-databinding-to-the-labelcontent-property"></a><span data-ttu-id="60b14-168">避免資料繫結至 Label.Content 屬性</span><span class="sxs-lookup"><span data-stu-id="60b14-168">Avoid Databinding to the Label.Content Property</span></span>

<span data-ttu-id="60b14-169">假設您有<xref:System.Windows.Controls.Label>一個<xref:System.String>從來源經常更新之物件的案例。</span><span class="sxs-lookup"><span data-stu-id="60b14-169">Imagine a scenario where you have a <xref:System.Windows.Controls.Label> object that is updated frequently from a <xref:System.String> source.</span></span> <span data-ttu-id="60b14-170">當資料<xref:System.Windows.Controls.Label>將專案的<xref:System.Windows.Controls.ContentControl.Content%2A>屬性系結至<xref:System.String>來源物件時, 您可能會遇到效能不佳的情況。</span><span class="sxs-lookup"><span data-stu-id="60b14-170">When data binding the <xref:System.Windows.Controls.Label> element's <xref:System.Windows.Controls.ContentControl.Content%2A> property to the <xref:System.String> source object, you may experience poor performance.</span></span> <span data-ttu-id="60b14-171">每次更新來源<xref:System.String>時, 就會捨棄<xref:System.String>舊的物件, 並重新<xref:System.String>建立新的, 因為<xref:System.String>物件是不可變的, 無法修改。</span><span class="sxs-lookup"><span data-stu-id="60b14-171">Each time the source <xref:System.String> is updated, the old <xref:System.String> object is discarded and a new <xref:System.String> is recreated—because a <xref:System.String> object is immutable, it cannot be modified.</span></span> <span data-ttu-id="60b14-172">接著, 這會導致<xref:System.Windows.Controls.ContentPresenter> <xref:System.Windows.Controls.Label>物件的捨棄舊內容, 並重新產生新的內容以顯示新<xref:System.String>的。</span><span class="sxs-lookup"><span data-stu-id="60b14-172">This, in turn, causes the <xref:System.Windows.Controls.ContentPresenter> of the <xref:System.Windows.Controls.Label> object to discard its old content and regenerate the new content to display the new <xref:System.String>.</span></span>

<span data-ttu-id="60b14-173">這個問題的解決方法很簡單。</span><span class="sxs-lookup"><span data-stu-id="60b14-173">The solution to this problem is simple.</span></span> <span data-ttu-id="60b14-174"><xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.TextBlock.Text%2A>如果未設定為自訂<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>值, 請將取代為, 並將其屬性系結至來源字串。 <xref:System.Windows.Controls.Label></span><span class="sxs-lookup"><span data-stu-id="60b14-174">If the <xref:System.Windows.Controls.Label> is not set to a custom <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> value, replace the <xref:System.Windows.Controls.Label> with a <xref:System.Windows.Controls.TextBlock> and data bind its <xref:System.Windows.Controls.TextBlock.Text%2A> property to the source string.</span></span>

|<span data-ttu-id="60b14-175">**資料繫結屬性**</span><span class="sxs-lookup"><span data-stu-id="60b14-175">**Data bound property**</span></span>|<span data-ttu-id="60b14-176">**更新時間 (毫秒)**</span><span class="sxs-lookup"><span data-stu-id="60b14-176">**Update time (ms)**</span></span>|
|-----------------------------|----------------------------|
|<span data-ttu-id="60b14-177">Label.Content</span><span class="sxs-lookup"><span data-stu-id="60b14-177">Label.Content</span></span>|<span data-ttu-id="60b14-178">835</span><span class="sxs-lookup"><span data-stu-id="60b14-178">835</span></span>|
|<span data-ttu-id="60b14-179">TextBlock.Text</span><span class="sxs-lookup"><span data-stu-id="60b14-179">TextBlock.Text</span></span>|<span data-ttu-id="60b14-180">242</span><span class="sxs-lookup"><span data-stu-id="60b14-180">242</span></span>|

<a name="Hyperlink"></a>

## <a name="hyperlink"></a><span data-ttu-id="60b14-181">超連結</span><span class="sxs-lookup"><span data-stu-id="60b14-181">Hyperlink</span></span>

<span data-ttu-id="60b14-182"><xref:System.Windows.Documents.Hyperlink>物件是內嵌層級的非固定格式內容專案, 可讓您在流程內容中裝載超連結。</span><span class="sxs-lookup"><span data-stu-id="60b14-182">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span>

### <a name="combine-hyperlinks-in-one-textblock-object"></a><span data-ttu-id="60b14-183">在一個 TextBlock 物件中合併超連結</span><span class="sxs-lookup"><span data-stu-id="60b14-183">Combine Hyperlinks in One TextBlock Object</span></span>

<span data-ttu-id="60b14-184">您可以將多個<xref:System.Windows.Documents.Hyperlink>專案的使用方式, 藉由將它們群組在相同<xref:System.Windows.Controls.TextBlock>的一起進行優化。</span><span class="sxs-lookup"><span data-stu-id="60b14-184">You can optimize the use of multiple <xref:System.Windows.Documents.Hyperlink> elements by grouping them together within the same <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="60b14-185">這可讓您在應用程式中建立的物件數目降到最低。</span><span class="sxs-lookup"><span data-stu-id="60b14-185">This helps to minimize the number of objects you create in your application.</span></span> <span data-ttu-id="60b14-186">例如，您可能想要顯示多個超連結，如下所示：</span><span class="sxs-lookup"><span data-stu-id="60b14-186">For example, you may want to display multiple hyperlinks, such as the following:</span></span>

<span data-ttu-id="60b14-187">MSN 首頁 | 我的 MSN</span><span class="sxs-lookup"><span data-stu-id="60b14-187">MSN Home &#124; My MSN</span></span>

<span data-ttu-id="60b14-188">下列標記範例顯示用來<xref:System.Windows.Controls.TextBlock>顯示超連結的多個元素:</span><span class="sxs-lookup"><span data-stu-id="60b14-188">The following markup example shows multiple <xref:System.Windows.Controls.TextBlock> elements used to display the hyperlinks:</span></span>

[!code-xaml[Performance#PerformanceSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]

<span data-ttu-id="60b14-189">下列標記範例顯示更有效率的方式來顯示超連結, 這次是使用單一<xref:System.Windows.Controls.TextBlock>的:</span><span class="sxs-lookup"><span data-stu-id="60b14-189">The following markup example shows a more efficient way of displaying the hyperlinks, this time, using a single <xref:System.Windows.Controls.TextBlock>:</span></span>

[!code-xaml[Performance#PerformanceSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]

### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a><span data-ttu-id="60b14-190">只在 MouseEnter 事件的超連結上顯示底線</span><span class="sxs-lookup"><span data-stu-id="60b14-190">Showing Underlines on Hyperlinks Only on MouseEnter Events</span></span>

<span data-ttu-id="60b14-191"><xref:System.Windows.TextDecoration>物件是您可以加入至文字的視覺精心設計且; 不過, 具現化可能需要大量的效能。</span><span class="sxs-lookup"><span data-stu-id="60b14-191">A <xref:System.Windows.TextDecoration> object is a visual ornamentation that you can add to text; however, it can be performance intensive to instantiate.</span></span> <span data-ttu-id="60b14-192">如果您大量使用<xref:System.Windows.Documents.Hyperlink>元素, 請考慮只在觸發事件時顯示底線, 例如<xref:System.Windows.ContentElement.MouseEnter>事件。</span><span class="sxs-lookup"><span data-stu-id="60b14-192">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span> <span data-ttu-id="60b14-193">如需詳細資訊，請參閱[指定超連結是否要加上底線](how-to-specify-whether-a-hyperlink-is-underlined.md)。</span><span class="sxs-lookup"><span data-stu-id="60b14-193">For more information, see [Specify Whether a Hyperlink is Underlined](how-to-specify-whether-a-hyperlink-is-underlined.md).</span></span>

<span data-ttu-id="60b14-194">下圖顯示 MouseEnter 事件如何觸發加底線的超連結:</span><span class="sxs-lookup"><span data-stu-id="60b14-194">The following image shows how the MouseEnter event triggers the underlined hyperlink:</span></span>

![顯示 TextDecoration 的超連結](./media/how-to-specify-whether-a-hyperlink-is-underlined/text-decorations-hyperlinks.png)

<span data-ttu-id="60b14-196">下列標記範例顯示<xref:System.Windows.Documents.Hyperlink>定義了且不含底線的:</span><span class="sxs-lookup"><span data-stu-id="60b14-196">The following markup sample shows a <xref:System.Windows.Documents.Hyperlink> defined with and without an underline:</span></span>

[!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]

<span data-ttu-id="60b14-197">下表顯示顯示包含和不含底線之<xref:System.Windows.Documents.Hyperlink> 1000 元素的效能成本。</span><span class="sxs-lookup"><span data-stu-id="60b14-197">The following table shows the performance cost of displaying 1000 <xref:System.Windows.Documents.Hyperlink> elements with and without an underline.</span></span>

|<span data-ttu-id="60b14-198">**超連結**</span><span class="sxs-lookup"><span data-stu-id="60b14-198">**Hyperlink**</span></span>|<span data-ttu-id="60b14-199">**建立時間 (毫秒)**</span><span class="sxs-lookup"><span data-stu-id="60b14-199">**Creation time (ms)**</span></span>|<span data-ttu-id="60b14-200">**轉譯時間 (毫秒)**</span><span class="sxs-lookup"><span data-stu-id="60b14-200">**Render time (ms)**</span></span>|
|-------------------|------------------------------|----------------------------|
|<span data-ttu-id="60b14-201">包含底線</span><span class="sxs-lookup"><span data-stu-id="60b14-201">With underline</span></span>|<span data-ttu-id="60b14-202">289</span><span class="sxs-lookup"><span data-stu-id="60b14-202">289</span></span>|<span data-ttu-id="60b14-203">1130</span><span class="sxs-lookup"><span data-stu-id="60b14-203">1130</span></span>|
|<span data-ttu-id="60b14-204">不含底線</span><span class="sxs-lookup"><span data-stu-id="60b14-204">Without underline</span></span>|<span data-ttu-id="60b14-205">299</span><span class="sxs-lookup"><span data-stu-id="60b14-205">299</span></span>|<span data-ttu-id="60b14-206">776</span><span class="sxs-lookup"><span data-stu-id="60b14-206">776</span></span>|

<a name="Text_Formatting_Features"></a>

## <a name="text-formatting-features"></a><span data-ttu-id="60b14-207">文字格式設定功能</span><span class="sxs-lookup"><span data-stu-id="60b14-207">Text Formatting Features</span></span>

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="60b14-208">提供 RTF 文字格式設定服務，例如自動斷字。</span><span class="sxs-lookup"><span data-stu-id="60b14-208">provides rich text formatting services, such as automatic hyphenations.</span></span> <span data-ttu-id="60b14-209">這些服務可能會影響應用程式效能，只有在必要時才應使用。</span><span class="sxs-lookup"><span data-stu-id="60b14-209">These services may impact application performance and should only be used when needed.</span></span>

### <a name="avoid-unnecessary-use-of-hyphenation"></a><span data-ttu-id="60b14-210">避免使用不必要的斷字</span><span class="sxs-lookup"><span data-stu-id="60b14-210">Avoid Unnecessary Use of Hyphenation</span></span>

<span data-ttu-id="60b14-211">自動斷字會尋找文字行的連字號中斷點, 並允許和<xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Documents.FlowDocument>物件中的行有額外的中斷點位置。</span><span class="sxs-lookup"><span data-stu-id="60b14-211">Automatic hyphenation finds hyphen breakpoints for lines of text, and allows additional break positions for lines in <xref:System.Windows.Controls.TextBlock> and <xref:System.Windows.Documents.FlowDocument> objects.</span></span> <span data-ttu-id="60b14-212">這些物件預設已停用自動斷字功能。</span><span class="sxs-lookup"><span data-stu-id="60b14-212">By default, the automatic hyphenation feature is disabled in these objects.</span></span> <span data-ttu-id="60b14-213">您可以將物件的 IsHyphenationEnabled 屬性設定為 `true` 來啟用此功能。</span><span class="sxs-lookup"><span data-stu-id="60b14-213">You can enable this feature by setting the object's IsHyphenationEnabled property to `true`.</span></span> <span data-ttu-id="60b14-214">不過, 啟用此功能會[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]導致起始元件物件模型 (COM) 互通性, 這可能會影響應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="60b14-214">However, enabling this feature causes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to initiate Component Object Model (COM) interoperability, which can impact application performance.</span></span> <span data-ttu-id="60b14-215">若非必要，建議您不要使用自動斷字功能。</span><span class="sxs-lookup"><span data-stu-id="60b14-215">It is recommended that you do not use automatic hyphenation unless you need it.</span></span>

### <a name="use-figures-carefully"></a><span data-ttu-id="60b14-216">小心使用圖表</span><span class="sxs-lookup"><span data-stu-id="60b14-216">Use Figures Carefully</span></span>

<span data-ttu-id="60b14-217"><xref:System.Windows.Documents.Figure>元素代表可以在內容頁面中絕對位置的部分流動內容。</span><span class="sxs-lookup"><span data-stu-id="60b14-217">A <xref:System.Windows.Documents.Figure> element represents a portion of flow content that can be absolutely-positioned within a page of content.</span></span> <span data-ttu-id="60b14-218">在某些情況下, <xref:System.Windows.Documents.Figure>如果其位置與已經配置的內容衝突, 可能會導致整個頁面自動重新格式化。您可以將不必要的重新格式化的可能性降<xref:System.Windows.Documents.Figure>到最低, 方法是將專案彼此分組, 或在固定頁面大小案例中接近內容的頂端。</span><span class="sxs-lookup"><span data-stu-id="60b14-218">In some cases, a <xref:System.Windows.Documents.Figure> may cause an entire page to automatically reformat if its position collides with content that has already been laid-out. You can minimize the possibility of unnecessary reformatting by either grouping <xref:System.Windows.Documents.Figure> elements next to each other, or declaring them near the top of content in a fixed page size scenario.</span></span>

### <a name="optimal-paragraph"></a><span data-ttu-id="60b14-219">最佳段落</span><span class="sxs-lookup"><span data-stu-id="60b14-219">Optimal Paragraph</span></span>

<span data-ttu-id="60b14-220"><xref:System.Windows.Documents.FlowDocument>物件的最佳段落功能會配置段落, 讓泛空白字元盡可能平均地散發。</span><span class="sxs-lookup"><span data-stu-id="60b14-220">The optimal paragraph feature of the <xref:System.Windows.Documents.FlowDocument> object lays out paragraphs so that white space is distributed as evenly as possible.</span></span> <span data-ttu-id="60b14-221">依預設已停用最佳段落功能。</span><span class="sxs-lookup"><span data-stu-id="60b14-221">By default, the optimal paragraph feature is disabled.</span></span> <span data-ttu-id="60b14-222">您可以藉由將物件的<xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A>屬性設定為來`true`啟用此功能。</span><span class="sxs-lookup"><span data-stu-id="60b14-222">You can enable this feature by setting the object's <xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A> property to `true`.</span></span> <span data-ttu-id="60b14-223">不過，啟用此功能會影響應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="60b14-223">However, enabling this feature impacts application performance.</span></span> <span data-ttu-id="60b14-224">若非必要，建議您不要使用最佳段落功能。</span><span class="sxs-lookup"><span data-stu-id="60b14-224">It is recommended that you do not use the optimal paragraph feature unless you need it.</span></span>

## <a name="see-also"></a><span data-ttu-id="60b14-225">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60b14-225">See also</span></span>

- [<span data-ttu-id="60b14-226">最佳化 WPF 應用程式效能</span><span class="sxs-lookup"><span data-stu-id="60b14-226">Optimizing WPF Application Performance</span></span>](optimizing-wpf-application-performance.md)
- [<span data-ttu-id="60b14-227">應用程式效能規劃</span><span class="sxs-lookup"><span data-stu-id="60b14-227">Planning for Application Performance</span></span>](planning-for-application-performance.md)
- [<span data-ttu-id="60b14-228">運用硬體</span><span class="sxs-lookup"><span data-stu-id="60b14-228">Taking Advantage of Hardware</span></span>](optimizing-performance-taking-advantage-of-hardware.md)
- [<span data-ttu-id="60b14-229">版面配置與設計</span><span class="sxs-lookup"><span data-stu-id="60b14-229">Layout and Design</span></span>](optimizing-performance-layout-and-design.md)
- [<span data-ttu-id="60b14-230">2D 圖形和影像處理</span><span class="sxs-lookup"><span data-stu-id="60b14-230">2D Graphics and Imaging</span></span>](optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="60b14-231">物件行為</span><span class="sxs-lookup"><span data-stu-id="60b14-231">Object Behavior</span></span>](optimizing-performance-object-behavior.md)
- [<span data-ttu-id="60b14-232">應用程式資源</span><span class="sxs-lookup"><span data-stu-id="60b14-232">Application Resources</span></span>](optimizing-performance-application-resources.md)
- [<span data-ttu-id="60b14-233">資料繫結</span><span class="sxs-lookup"><span data-stu-id="60b14-233">Data Binding</span></span>](optimizing-performance-data-binding.md)
- [<span data-ttu-id="60b14-234">其他效能建議</span><span class="sxs-lookup"><span data-stu-id="60b14-234">Other Performance Recommendations</span></span>](optimizing-performance-other-recommendations.md)
