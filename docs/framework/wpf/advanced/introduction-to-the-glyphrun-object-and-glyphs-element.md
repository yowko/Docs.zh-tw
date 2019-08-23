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
ms.openlocfilehash: 9e40a9656bd1d89203b167860ef6951d5e30377c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918404"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a><span data-ttu-id="d150a-102">GlyphRun 物件和 Glyphs 項目簡介</span><span class="sxs-lookup"><span data-stu-id="d150a-102">Introduction to the GlyphRun Object and Glyphs Element</span></span>
<span data-ttu-id="d150a-103">本主題描述<xref:System.Windows.Media.GlyphRun>物件<xref:System.Windows.Documents.Glyphs>和元素。</span><span class="sxs-lookup"><span data-stu-id="d150a-103">This topic describes the <xref:System.Windows.Media.GlyphRun> object and the <xref:System.Windows.Documents.Glyphs> element.</span></span>  

<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a><span data-ttu-id="d150a-104">GlyphRun 簡介</span><span class="sxs-lookup"><span data-stu-id="d150a-104">Introduction to GlyphRun</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="d150a-105">提供先進的文字支援, 包括可<xref:System.Windows.Documents.Glyphs>直接存取的圖像層級標記, 適用于想要在格式化之後攔截並保存文字的客戶。</span><span class="sxs-lookup"><span data-stu-id="d150a-105">provides advanced text support including glyph-level markup with direct access to <xref:System.Windows.Documents.Glyphs> for customers who want to intercept and persist text after formatting.</span></span> <span data-ttu-id="d150a-106">這些功能可針對下列每個案例中的不同文字轉譯需求提供重要支援。</span><span class="sxs-lookup"><span data-stu-id="d150a-106">These features provide critical support for the different text rendering requirements in each of the following scenarios.</span></span>  
  
1. <span data-ttu-id="d150a-107">固定格式文件的螢幕顯示。</span><span class="sxs-lookup"><span data-stu-id="d150a-107">Screen display of fixed-format documents.</span></span>  
  
2. <span data-ttu-id="d150a-108">列印案例。</span><span class="sxs-lookup"><span data-stu-id="d150a-108">Print scenarios.</span></span>  
  
    - <span data-ttu-id="d150a-109">使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 作為裝置印表機語言。</span><span class="sxs-lookup"><span data-stu-id="d150a-109">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] as a device printer language.</span></span>  
  
    - <span data-ttu-id="d150a-110">Microsoft XPS 檔寫入器。</span><span class="sxs-lookup"><span data-stu-id="d150a-110">Microsoft XPS Document Writer.</span></span>  
  
    - <span data-ttu-id="d150a-111">先前的印表機驅動程式，從 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 應用程式輸出為固定格式。</span><span class="sxs-lookup"><span data-stu-id="d150a-111">Previous printer drivers, output from [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications to the fixed format.</span></span>  
  
    - <span data-ttu-id="d150a-112">列印多工緩衝處理格式。</span><span class="sxs-lookup"><span data-stu-id="d150a-112">Print spool format.</span></span>  
  
3. <span data-ttu-id="d150a-113">固定格式的檔標記法, 包括舊版 Windows 和其他計算裝置的用戶端。</span><span class="sxs-lookup"><span data-stu-id="d150a-113">Fixed-format document representation, including clients for previous versions of Windows and other computing devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d150a-114"><xref:System.Windows.Documents.Glyphs>和<xref:System.Windows.Media.GlyphRun>是針對固定格式的檔簡報和列印案例所設計。</span><span class="sxs-lookup"><span data-stu-id="d150a-114"><xref:System.Windows.Documents.Glyphs> and <xref:System.Windows.Media.GlyphRun> are designed for fixed-format document presentation and print scenarios.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="d150a-115">針對一般版面配置和[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]案例<xref:System.Windows.Controls.Label> (例如和<xref:System.Windows.Controls.TextBlock>) 提供數個元素。</span><span class="sxs-lookup"><span data-stu-id="d150a-115">provides several elements for general layout and [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenarios such as <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="d150a-116">如需配置和 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 案例的詳細資訊，請參閱 [WPF 中的印刷樣式](typography-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="d150a-116">For more information on layout and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenarios, see the [Typography in WPF](typography-in-wpf.md).</span></span>  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a><span data-ttu-id="d150a-117">GlyphRun 物件</span><span class="sxs-lookup"><span data-stu-id="d150a-117">The GlyphRun Object</span></span>  
 <span data-ttu-id="d150a-118"><xref:System.Windows.Media.GlyphRun>物件代表單一字型單一字型的一系列字元, 並以單一轉譯樣式呈現。</span><span class="sxs-lookup"><span data-stu-id="d150a-118">The <xref:System.Windows.Media.GlyphRun> object represents a sequence of glyphs from a single face of a single font at a single size, and with a single rendering style.</span></span>  
  
 <span data-ttu-id="d150a-119"><xref:System.Windows.Media.GlyphRun>包含字型詳細資料<xref:System.Windows.Documents.Glyphs.Indices%2A> , 例如圖像和個別圖像位置。</span><span class="sxs-lookup"><span data-stu-id="d150a-119"><xref:System.Windows.Media.GlyphRun> includes both font details such as glyph <xref:System.Windows.Documents.Glyphs.Indices%2A> and individual glyph positions.</span></span> <span data-ttu-id="d150a-120">它也包含從產生[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]執行的原始程式碼點、字元到圖像緩衝區位移對應資訊, 以及每個字元和每個字元的旗標。</span><span class="sxs-lookup"><span data-stu-id="d150a-120">It also includes the original [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] code points the run was generated from, character-to-glyph buffer offset mapping information, and per-character and per-glyph flags.</span></span>  
  
 <span data-ttu-id="d150a-121"><xref:System.Windows.Media.GlyphRun>具有對應的高層級<xref:System.Windows.FrameworkElement>。 <xref:System.Windows.Documents.Glyphs></span><span class="sxs-lookup"><span data-stu-id="d150a-121"><xref:System.Windows.Media.GlyphRun> has a corresponding high-level <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="d150a-122"><xref:System.Windows.Documents.Glyphs>可以在專案樹狀結構和標記中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]用來表示<xref:System.Windows.Media.GlyphRun>輸出。</span><span class="sxs-lookup"><span data-stu-id="d150a-122"><xref:System.Windows.Documents.Glyphs> can be used in the element tree and in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup to represent <xref:System.Windows.Media.GlyphRun> output.</span></span>  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a><span data-ttu-id="d150a-123">Glyphs 項目</span><span class="sxs-lookup"><span data-stu-id="d150a-123">The Glyphs Element</span></span>  
 <span data-ttu-id="d150a-124">元素代表<xref:System.Windows.Media.GlyphRun> 中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的輸出。 <xref:System.Windows.Documents.Glyphs></span><span class="sxs-lookup"><span data-stu-id="d150a-124">The <xref:System.Windows.Documents.Glyphs> element represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="d150a-125">下列標記語法是用來描述<xref:System.Windows.Documents.Glyphs>元素。</span><span class="sxs-lookup"><span data-stu-id="d150a-125">The following markup syntax is used to describe the <xref:System.Windows.Documents.Glyphs> element.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="d150a-126">下列屬性定義對應至範例標記中的前四個屬性。</span><span class="sxs-lookup"><span data-stu-id="d150a-126">The following property definitions correspond to the first four attributes in the sample markup.</span></span>  
  
|<span data-ttu-id="d150a-127">屬性</span><span class="sxs-lookup"><span data-stu-id="d150a-127">Property</span></span>|<span data-ttu-id="d150a-128">描述</span><span class="sxs-lookup"><span data-stu-id="d150a-128">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|<span data-ttu-id="d150a-129">指定資源識別碼: 檔案名、Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]或應用程式 .exe 或容器中的資源參考。</span><span class="sxs-lookup"><span data-stu-id="d150a-129">Specifies a resource identifier: file name, Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], or resource reference in the application .exe or container.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|<span data-ttu-id="d150a-130">指定字型大小 (以繪圖介面單位為單位) (預設值為 .96 英吋)。</span><span class="sxs-lookup"><span data-stu-id="d150a-130">Specifies the font size in drawing surface units (default is .96 inches).</span></span>|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|<span data-ttu-id="d150a-131">指定粗體和斜體樣式的旗標。</span><span class="sxs-lookup"><span data-stu-id="d150a-131">Specifies flags for bold and Italic styles.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|<span data-ttu-id="d150a-132">指定雙向配置層級。</span><span class="sxs-lookup"><span data-stu-id="d150a-132">Specifies the bidirectional layout level.</span></span> <span data-ttu-id="d150a-133">偶數值和零值表示由左至右的版面配置，奇數值則表示由右至左的版面配置。</span><span class="sxs-lookup"><span data-stu-id="d150a-133">Even-numbered and zero values imply left-to-right layout; odd-numbered values imply right-to-left layout.</span></span>|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a><span data-ttu-id="d150a-134">Indices 屬性</span><span class="sxs-lookup"><span data-stu-id="d150a-134">Indices property</span></span>  
 <span data-ttu-id="d150a-135"><xref:System.Windows.Documents.Glyphs.Indices%2A>屬性是圖像規格的字串。</span><span class="sxs-lookup"><span data-stu-id="d150a-135">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property is a string of glyph specifications.</span></span> <span data-ttu-id="d150a-136">如果由一系列字符形成單一叢集，則會先指定叢集中的第一個字符，再指定合併多少字符和多少字碼指標來形成叢集。</span><span class="sxs-lookup"><span data-stu-id="d150a-136">Where a sequence of glyphs forms a single cluster, the specification of the first glyph in the cluster is preceded by a specification of how many glyphs and how many code points combine to form the cluster.</span></span> <span data-ttu-id="d150a-137"><xref:System.Windows.Documents.Glyphs.Indices%2A>屬性會在一個字串中收集下列屬性。</span><span class="sxs-lookup"><span data-stu-id="d150a-137">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property collects in one string the following properties.</span></span>  
  
- <span data-ttu-id="d150a-138">字符索引</span><span class="sxs-lookup"><span data-stu-id="d150a-138">Glyph indices</span></span>  
  
- <span data-ttu-id="d150a-139">字符遞增寬度</span><span class="sxs-lookup"><span data-stu-id="d150a-139">Glyph advance widths</span></span>  
  
- <span data-ttu-id="d150a-140">合併字符附加向量</span><span class="sxs-lookup"><span data-stu-id="d150a-140">Combining glyph attachment vectors</span></span>  
  
- <span data-ttu-id="d150a-141">從字碼指標到字符的叢集對應</span><span class="sxs-lookup"><span data-stu-id="d150a-141">Cluster mapping from code points to glyphs</span></span>  
  
- <span data-ttu-id="d150a-142">字符旗標</span><span class="sxs-lookup"><span data-stu-id="d150a-142">Glyph flags</span></span>  
  
 <span data-ttu-id="d150a-143">每個字符規格的形式如下。</span><span class="sxs-lookup"><span data-stu-id="d150a-143">Each glyph specification has the following form.</span></span>  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a><span data-ttu-id="d150a-144">字符度量</span><span class="sxs-lookup"><span data-stu-id="d150a-144">Glyph Metrics</span></span>  
 <span data-ttu-id="d150a-145">每個字元都會定義度量, 以指定其與<xref:System.Windows.Documents.Glyphs>其他的對齊方式。</span><span class="sxs-lookup"><span data-stu-id="d150a-145">Each glyph defines metrics that specify how it aligns with other <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="d150a-146">下圖定義兩個不同字符字元的各種印刷品質。</span><span class="sxs-lookup"><span data-stu-id="d150a-146">The following graphic defines the various typographic qualities of two different glyph characters.</span></span>  
  
 <span data-ttu-id="d150a-147">![字符測量的繪圖器](./media/glyph-example.png "glyph_example")</span><span class="sxs-lookup"><span data-stu-id="d150a-147">![Diagraph of glyph measurements](./media/glyph-example.png "glyph_example")</span></span>  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a><span data-ttu-id="d150a-148">字符標記</span><span class="sxs-lookup"><span data-stu-id="d150a-148">Glyphs Markup</span></span>  
 <span data-ttu-id="d150a-149">下列程式碼範例示範如何在中<xref:System.Windows.Documents.Glyphs> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]使用元素的各種屬性。</span><span class="sxs-lookup"><span data-stu-id="d150a-149">The following code example shows how to use various properties of the <xref:System.Windows.Documents.Glyphs> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d150a-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d150a-150">See also</span></span>

- [<span data-ttu-id="d150a-151">WPF 中的印刷樣式</span><span class="sxs-lookup"><span data-stu-id="d150a-151">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="d150a-152">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="d150a-152">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="d150a-153">Text</span><span class="sxs-lookup"><span data-stu-id="d150a-153">Text</span></span>](optimizing-performance-text.md)
