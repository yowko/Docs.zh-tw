---
title: GlyphRun 物件和 Glyphs 項目簡介
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], Glyphs element
- Glyphs elements [WPF]
- GlyphRun object [WPF]
- text [WPF], glyphs
- glyphs [WPF]
- typography [WPF], GlyphRun object
ms.assetid: 746ca769-a331-4435-9b95-f72a883b67c1
ms.openlocfilehash: 32e8ab7104b8ea2f985395065868ed154ca1e378
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181956"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a><span data-ttu-id="8a1ce-102">GlyphRun 物件和 Glyphs 項目簡介</span><span class="sxs-lookup"><span data-stu-id="8a1ce-102">Introduction to the GlyphRun Object and Glyphs Element</span></span>
<span data-ttu-id="8a1ce-103">本主題介紹物件<xref:System.Windows.Media.GlyphRun>和<xref:System.Windows.Documents.Glyphs>元素。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-103">This topic describes the <xref:System.Windows.Media.GlyphRun> object and the <xref:System.Windows.Documents.Glyphs> element.</span></span>  

<a name="text_glyphrunovw_intro"></a>
## <a name="introduction-to-glyphrun"></a><span data-ttu-id="8a1ce-104">GlyphRun 簡介</span><span class="sxs-lookup"><span data-stu-id="8a1ce-104">Introduction to GlyphRun</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="8a1ce-105">提供高級文本支援，包括字形級標記，可直接存取<xref:System.Windows.Documents.Glyphs>希望在格式化後攔截和保留文本的客戶。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-105">provides advanced text support including glyph-level markup with direct access to <xref:System.Windows.Documents.Glyphs> for customers who want to intercept and persist text after formatting.</span></span> <span data-ttu-id="8a1ce-106">這些功能可針對下列每個案例中的不同文字轉譯需求提供重要支援。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-106">These features provide critical support for the different text rendering requirements in each of the following scenarios.</span></span>  
  
1. <span data-ttu-id="8a1ce-107">固定格式文件的螢幕顯示。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-107">Screen display of fixed-format documents.</span></span>  
  
2. <span data-ttu-id="8a1ce-108">列印案例。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-108">Print scenarios.</span></span>  
  
    - <span data-ttu-id="8a1ce-109">使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 作為裝置印表機語言。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-109">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] as a device printer language.</span></span>  
  
    - <span data-ttu-id="8a1ce-110">微軟XPS文檔編寫器。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-110">Microsoft XPS Document Writer.</span></span>  
  
    - <span data-ttu-id="8a1ce-111">以前的印表機驅動程式，從 Win32 應用程式輸出到固定格式。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-111">Previous printer drivers, output from Win32 applications to the fixed format.</span></span>  
  
    - <span data-ttu-id="8a1ce-112">列印多工緩衝處理格式。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-112">Print spool format.</span></span>  
  
3. <span data-ttu-id="8a1ce-113">固定格式的文檔表示形式，包括早期版本的 Windows 和其他計算裝置的用戶端。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-113">Fixed-format document representation, including clients for previous versions of Windows and other computing devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a1ce-114"><xref:System.Windows.Documents.Glyphs><xref:System.Windows.Media.GlyphRun>並專為固定格式的文檔演示和列印方案而設計。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-114"><xref:System.Windows.Documents.Glyphs> and <xref:System.Windows.Media.GlyphRun> are designed for fixed-format document presentation and print scenarios.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="8a1ce-115">為常規佈局和[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]方案（如 和<xref:System.Windows.Controls.Label><xref:System.Windows.Controls.TextBlock>）提供了多個元素。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-115">provides several elements for general layout and [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenarios such as <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="8a1ce-116">有關佈局和[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]方案的詳細資訊，請參閱[WPF 中的排版](typography-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-116">For more information on layout and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenarios, see the [Typography in WPF](typography-in-wpf.md).</span></span>  
  
<a name="text_glyphrunovw_glyphrunobject"></a>
## <a name="the-glyphrun-object"></a><span data-ttu-id="8a1ce-117">GlyphRun 物件</span><span class="sxs-lookup"><span data-stu-id="8a1ce-117">The GlyphRun Object</span></span>  
 <span data-ttu-id="8a1ce-118">物件<xref:System.Windows.Media.GlyphRun>表示單個字體單個字體的單個面的字形序列，該字形具有單個呈現樣式。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-118">The <xref:System.Windows.Media.GlyphRun> object represents a sequence of glyphs from a single face of a single font at a single size, and with a single rendering style.</span></span>  
  
 <span data-ttu-id="8a1ce-119"><xref:System.Windows.Media.GlyphRun>包括字體詳細資訊，如字形<xref:System.Windows.Documents.Glyphs.Indices%2A>和單個字形位置。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-119"><xref:System.Windows.Media.GlyphRun> includes both font details such as glyph <xref:System.Windows.Documents.Glyphs.Indices%2A> and individual glyph positions.</span></span> <span data-ttu-id="8a1ce-120">它還包括運行生成的原始 Unicode 代碼點、字元到字形緩衝區偏移映射資訊以及每個字元和每個字形標誌。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-120">It also includes the original Unicode code points the run was generated from, character-to-glyph buffer offset mapping information, and per-character and per-glyph flags.</span></span>  
  
 <span data-ttu-id="8a1ce-121"><xref:System.Windows.Media.GlyphRun>具有相應的高級<xref:System.Windows.FrameworkElement>。 <xref:System.Windows.Documents.Glyphs></span><span class="sxs-lookup"><span data-stu-id="8a1ce-121"><xref:System.Windows.Media.GlyphRun> has a corresponding high-level <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="8a1ce-122"><xref:System.Windows.Documents.Glyphs>可用於元素樹和[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記表示<xref:System.Windows.Media.GlyphRun>輸出。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-122"><xref:System.Windows.Documents.Glyphs> can be used in the element tree and in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup to represent <xref:System.Windows.Media.GlyphRun> output.</span></span>  
  
<a name="text_glyphrunovw_glyphselement"></a>
## <a name="the-glyphs-element"></a><span data-ttu-id="8a1ce-123">Glyphs 項目</span><span class="sxs-lookup"><span data-stu-id="8a1ce-123">The Glyphs Element</span></span>  
 <span data-ttu-id="8a1ce-124">元素<xref:System.Windows.Documents.Glyphs>表示<xref:System.Windows.Media.GlyphRun>in[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的輸出。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-124">The <xref:System.Windows.Documents.Glyphs> element represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="8a1ce-125">以下標記語法用於描述元素<xref:System.Windows.Documents.Glyphs>。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-125">The following markup syntax is used to describe the <xref:System.Windows.Documents.Glyphs> element.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="8a1ce-126">下列屬性定義對應至範例標記中的前四個屬性。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-126">The following property definitions correspond to the first four attributes in the sample markup.</span></span>  
  
|<span data-ttu-id="8a1ce-127">屬性</span><span class="sxs-lookup"><span data-stu-id="8a1ce-127">Property</span></span>|<span data-ttu-id="8a1ce-128">描述</span><span class="sxs-lookup"><span data-stu-id="8a1ce-128">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|<span data-ttu-id="8a1ce-129">指定資源識別碼：檔案名、Web 統一資源識別項 （URI） 或應用程式 .exe 或容器中的資源引用。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-129">Specifies a resource identifier: file name, Web uniform resource identifier (URI), or resource reference in the application .exe or container.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|<span data-ttu-id="8a1ce-130">指定字型大小 (以繪圖介面單位為單位) (預設值為 .96 英吋)。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-130">Specifies the font size in drawing surface units (default is .96 inches).</span></span>|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|<span data-ttu-id="8a1ce-131">指定粗體和斜體樣式的旗標。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-131">Specifies flags for bold and Italic styles.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|<span data-ttu-id="8a1ce-132">指定雙向配置層級。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-132">Specifies the bidirectional layout level.</span></span> <span data-ttu-id="8a1ce-133">偶數值和零值表示由左至右的版面配置，奇數值則表示由右至左的版面配置。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-133">Even-numbered and zero values imply left-to-right layout; odd-numbered values imply right-to-left layout.</span></span>|  
  
<a name="text_glyphrunovw_indicesproperty"></a>
### <a name="indices-property"></a><span data-ttu-id="8a1ce-134">Indices 屬性</span><span class="sxs-lookup"><span data-stu-id="8a1ce-134">Indices property</span></span>  
 <span data-ttu-id="8a1ce-135">屬性<xref:System.Windows.Documents.Glyphs.Indices%2A>是一串字形規格。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-135">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property is a string of glyph specifications.</span></span> <span data-ttu-id="8a1ce-136">如果由一系列字符形成單一叢集，則會先指定叢集中的第一個字符，再指定合併多少字符和多少字碼指標來形成叢集。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-136">Where a sequence of glyphs forms a single cluster, the specification of the first glyph in the cluster is preceded by a specification of how many glyphs and how many code points combine to form the cluster.</span></span> <span data-ttu-id="8a1ce-137">屬性<xref:System.Windows.Documents.Glyphs.Indices%2A>在一個字串中收集以下屬性。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-137">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property collects in one string the following properties.</span></span>  
  
- <span data-ttu-id="8a1ce-138">字符索引</span><span class="sxs-lookup"><span data-stu-id="8a1ce-138">Glyph indices</span></span>  
  
- <span data-ttu-id="8a1ce-139">字符遞增寬度</span><span class="sxs-lookup"><span data-stu-id="8a1ce-139">Glyph advance widths</span></span>  
  
- <span data-ttu-id="8a1ce-140">合併字符附加向量</span><span class="sxs-lookup"><span data-stu-id="8a1ce-140">Combining glyph attachment vectors</span></span>  
  
- <span data-ttu-id="8a1ce-141">從字碼指標到字符的叢集對應</span><span class="sxs-lookup"><span data-stu-id="8a1ce-141">Cluster mapping from code points to glyphs</span></span>  
  
- <span data-ttu-id="8a1ce-142">字符旗標</span><span class="sxs-lookup"><span data-stu-id="8a1ce-142">Glyph flags</span></span>  
  
 <span data-ttu-id="8a1ce-143">每個字符規格的形式如下。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-143">Each glyph specification has the following form.</span></span>  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>
## <a name="glyph-metrics"></a><span data-ttu-id="8a1ce-144">字符度量</span><span class="sxs-lookup"><span data-stu-id="8a1ce-144">Glyph Metrics</span></span>  
 <span data-ttu-id="8a1ce-145">每個字形定義指標，指定它如何與其他<xref:System.Windows.Documents.Glyphs>對齊。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-145">Each glyph defines metrics that specify how it aligns with other <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="8a1ce-146">下圖定義兩個不同字符字元的各種印刷品質。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-146">The following graphic defines the various typographic qualities of two different glyph characters.</span></span>  
  
 <span data-ttu-id="8a1ce-147">![圖像量測的繪圖器](./media/glyph-example.png "glyph_example")</span><span class="sxs-lookup"><span data-stu-id="8a1ce-147">![Diagraph of glyph measurements](./media/glyph-example.png "glyph_example")</span></span>  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>
## <a name="glyphs-markup"></a><span data-ttu-id="8a1ce-148">字符標記</span><span class="sxs-lookup"><span data-stu-id="8a1ce-148">Glyphs Markup</span></span>  
 <span data-ttu-id="8a1ce-149">以下代碼示例演示如何在 中使用<xref:System.Windows.Documents.Glyphs>[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]元素的各種屬性。</span><span class="sxs-lookup"><span data-stu-id="8a1ce-149">The following code example shows how to use various properties of the <xref:System.Windows.Documents.Glyphs> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8a1ce-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a1ce-150">See also</span></span>

- [<span data-ttu-id="8a1ce-151">WPF 中的印刷樣式</span><span class="sxs-lookup"><span data-stu-id="8a1ce-151">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="8a1ce-152">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="8a1ce-152">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="8a1ce-153">文本</span><span class="sxs-lookup"><span data-stu-id="8a1ce-153">Text</span></span>](optimizing-performance-text.md)
