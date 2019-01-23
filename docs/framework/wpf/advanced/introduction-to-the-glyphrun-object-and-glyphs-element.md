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
ms.openlocfilehash: 27cecf3c50737e8d6c18f8505d8ec1d8393dbe33
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619674"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a><span data-ttu-id="ea6a9-102">GlyphRun 物件和 Glyphs 項目簡介</span><span class="sxs-lookup"><span data-stu-id="ea6a9-102">Introduction to the GlyphRun Object and Glyphs Element</span></span>
<span data-ttu-id="ea6a9-103">本主題描述<xref:System.Windows.Media.GlyphRun>物件和<xref:System.Windows.Documents.Glyphs>項目。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-103">This topic describes the <xref:System.Windows.Media.GlyphRun> object and the <xref:System.Windows.Documents.Glyphs> element.</span></span>  
  
  
<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a><span data-ttu-id="ea6a9-104">GlyphRun 簡介</span><span class="sxs-lookup"><span data-stu-id="ea6a9-104">Introduction to GlyphRun</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="ea6a9-105">提供進階的文字支援包括圖像層級標記，直接存取<xref:System.Windows.Documents.Glyphs>客戶想要攔截和保存格式化之後的文字。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-105">provides advanced text support including glyph-level markup with direct access to <xref:System.Windows.Documents.Glyphs> for customers who want to intercept and persist text after formatting.</span></span> <span data-ttu-id="ea6a9-106">這些功能可針對下列每個案例中的不同文字轉譯需求提供重要支援。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-106">These features provide critical support for the different text rendering requirements in each of the following scenarios.</span></span>  
  
1.  <span data-ttu-id="ea6a9-107">固定格式文件的螢幕顯示。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-107">Screen display of fixed-format documents.</span></span>  
  
2.  <span data-ttu-id="ea6a9-108">列印案例。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-108">Print scenarios.</span></span>  
  
    -   <span data-ttu-id="ea6a9-109">使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 作為裝置印表機語言。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-109">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] as a device printer language.</span></span>  
  
    -   [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)]<span data-ttu-id="ea6a9-110">.</span><span class="sxs-lookup"><span data-stu-id="ea6a9-110">.</span></span>  
  
    -   <span data-ttu-id="ea6a9-111">先前的印表機驅動程式，從 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 應用程式輸出為固定格式。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-111">Previous printer drivers, output from [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications to the fixed format.</span></span>  
  
    -   <span data-ttu-id="ea6a9-112">列印多工緩衝處理格式。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-112">Print spool format.</span></span>  
  
3.  <span data-ttu-id="ea6a9-113">固定格式文件呈現，包括舊版 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 和其他電腦裝置的用戶端。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-113">Fixed-format document representation, including clients for previous versions of [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] and other computing devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea6a9-114"><xref:System.Windows.Documents.Glyphs> 和<xref:System.Windows.Media.GlyphRun>專為固定格式文件展示及列印案例。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-114"><xref:System.Windows.Documents.Glyphs> and <xref:System.Windows.Media.GlyphRun> are designed for fixed-format document presentation and print scenarios.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="ea6a9-115">提供數個項目用於一般配置和[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]運用於如下案例<xref:System.Windows.Controls.Label>和<xref:System.Windows.Controls.TextBlock>。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-115">provides several elements for general layout and [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenarios such as <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="ea6a9-116">如需配置和 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 案例的詳細資訊，請參閱 [WPF 中的印刷樣式](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-116">For more information on layout and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenarios, see the [Typography in WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md).</span></span>  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a><span data-ttu-id="ea6a9-117">GlyphRun 物件</span><span class="sxs-lookup"><span data-stu-id="ea6a9-117">The GlyphRun Object</span></span>  
 <span data-ttu-id="ea6a9-118"><xref:System.Windows.Media.GlyphRun>物件都代表一系列字符具有單一大小且具有單一轉譯樣式之單一字型單一字體。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-118">The <xref:System.Windows.Media.GlyphRun> object represents a sequence of glyphs from a single face of a single font at a single size, and with a single rendering style.</span></span>  
  
 <span data-ttu-id="ea6a9-119"><xref:System.Windows.Media.GlyphRun> 包含這兩個字型詳細資料，例如圖像 （glyph）<xref:System.Windows.Documents.Glyphs.Indices%2A>和個別字符位置。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-119"><xref:System.Windows.Media.GlyphRun> includes both font details such as glyph <xref:System.Windows.Documents.Glyphs.Indices%2A> and individual glyph positions.</span></span> <span data-ttu-id="ea6a9-120">它也包含原始[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]字碼的指標產生執行從字元到字符緩衝區位移的對應資訊，以及每個字元和每個字符旗標。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-120">It also includes the original [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] code points the run was generated from, character-to-glyph buffer offset mapping information, and per-character and per-glyph flags.</span></span>  
  
 <span data-ttu-id="ea6a9-121"><xref:System.Windows.Media.GlyphRun> 具有對應的高階<xref:System.Windows.FrameworkElement>， <xref:System.Windows.Documents.Glyphs>。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-121"><xref:System.Windows.Media.GlyphRun> has a corresponding high-level <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="ea6a9-122"><xref:System.Windows.Documents.Glyphs> 可用項目樹狀結構中，並在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]標記，以代表<xref:System.Windows.Media.GlyphRun>輸出。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-122"><xref:System.Windows.Documents.Glyphs> can be used in the element tree and in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup to represent <xref:System.Windows.Media.GlyphRun> output.</span></span>  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a><span data-ttu-id="ea6a9-123">Glyphs 項目</span><span class="sxs-lookup"><span data-stu-id="ea6a9-123">The Glyphs Element</span></span>  
 <span data-ttu-id="ea6a9-124"><xref:System.Windows.Documents.Glyphs>項目代表的輸出<xref:System.Windows.Media.GlyphRun>在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-124">The <xref:System.Windows.Documents.Glyphs> element represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="ea6a9-125">下列標記語法用來描述<xref:System.Windows.Documents.Glyphs>項目。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-125">The following markup syntax is used to describe the <xref:System.Windows.Documents.Glyphs> element.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="ea6a9-126">下列屬性定義對應至範例標記中的前四個屬性。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-126">The following property definitions correspond to the first four attributes in the sample markup.</span></span>  
  
|<span data-ttu-id="ea6a9-127">屬性</span><span class="sxs-lookup"><span data-stu-id="ea6a9-127">Property</span></span>|<span data-ttu-id="ea6a9-128">描述</span><span class="sxs-lookup"><span data-stu-id="ea6a9-128">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|<span data-ttu-id="ea6a9-129">指定資源識別碼︰ 檔案名稱、 Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]，或在應用程式.exe 或容器的資源參考。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-129">Specifies a resource identifier: file name, Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], or resource reference in the application .exe or container.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|<span data-ttu-id="ea6a9-130">指定字型大小 (以繪圖介面單位為單位) (預設值為 .96 英吋)。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-130">Specifies the font size in drawing surface units (default is .96 inches).</span></span>|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|<span data-ttu-id="ea6a9-131">指定粗體和斜體樣式的旗標。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-131">Specifies flags for bold and Italic styles.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|<span data-ttu-id="ea6a9-132">指定雙向配置層級。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-132">Specifies the bidirectional layout level.</span></span> <span data-ttu-id="ea6a9-133">偶數值和零值表示由左至右的版面配置，奇數值則表示由右至左的版面配置。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-133">Even-numbered and zero values imply left-to-right layout; odd-numbered values imply right-to-left layout.</span></span>|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a><span data-ttu-id="ea6a9-134">Indices 屬性</span><span class="sxs-lookup"><span data-stu-id="ea6a9-134">Indices property</span></span>  
 <span data-ttu-id="ea6a9-135"><xref:System.Windows.Documents.Glyphs.Indices%2A>屬性是一個字串的字符規格。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-135">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property is a string of glyph specifications.</span></span> <span data-ttu-id="ea6a9-136">如果由一系列字符形成單一叢集，則會先指定叢集中的第一個字符，再指定合併多少字符和多少字碼指標來形成叢集。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-136">Where a sequence of glyphs forms a single cluster, the specification of the first glyph in the cluster is preceded by a specification of how many glyphs and how many code points combine to form the cluster.</span></span> <span data-ttu-id="ea6a9-137"><xref:System.Windows.Documents.Glyphs.Indices%2A>屬性收集在一個字串中的下列屬性。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-137">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property collects in one string the following properties.</span></span>  
  
-   <span data-ttu-id="ea6a9-138">字符索引</span><span class="sxs-lookup"><span data-stu-id="ea6a9-138">Glyph indices</span></span>  
  
-   <span data-ttu-id="ea6a9-139">字符遞增寬度</span><span class="sxs-lookup"><span data-stu-id="ea6a9-139">Glyph advance widths</span></span>  
  
-   <span data-ttu-id="ea6a9-140">合併字符附加向量</span><span class="sxs-lookup"><span data-stu-id="ea6a9-140">Combining glyph attachment vectors</span></span>  
  
-   <span data-ttu-id="ea6a9-141">從字碼指標到字符的叢集對應</span><span class="sxs-lookup"><span data-stu-id="ea6a9-141">Cluster mapping from code points to glyphs</span></span>  
  
-   <span data-ttu-id="ea6a9-142">字符旗標</span><span class="sxs-lookup"><span data-stu-id="ea6a9-142">Glyph flags</span></span>  
  
 <span data-ttu-id="ea6a9-143">每個字符規格的形式如下。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-143">Each glyph specification has the following form.</span></span>  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a><span data-ttu-id="ea6a9-144">字符度量</span><span class="sxs-lookup"><span data-stu-id="ea6a9-144">Glyph Metrics</span></span>  
 <span data-ttu-id="ea6a9-145">每個字符都會定義度量，以指定與其他的對齊方式<xref:System.Windows.Documents.Glyphs>。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-145">Each glyph defines metrics that specify how it aligns with other <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="ea6a9-146">下圖定義兩個不同字符字元的各種印刷品質。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-146">The following graphic defines the various typographic qualities of two different glyph characters.</span></span>  
  
 <span data-ttu-id="ea6a9-147">![字符測量的繪圖器](../../../../docs/framework/wpf/advanced/media/glyph-example.png "glyph_example")</span><span class="sxs-lookup"><span data-stu-id="ea6a9-147">![Diagraph of glyph measurements](../../../../docs/framework/wpf/advanced/media/glyph-example.png "glyph_example")</span></span>  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a><span data-ttu-id="ea6a9-148">字符標記</span><span class="sxs-lookup"><span data-stu-id="ea6a9-148">Glyphs Markup</span></span>  
 <span data-ttu-id="ea6a9-149">下列程式碼範例示範如何使用的各種屬性<xref:System.Windows.Documents.Glyphs>中的項目[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ea6a9-149">The following code example shows how to use various properties of the <xref:System.Windows.Documents.Glyphs> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ea6a9-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea6a9-150">See also</span></span>
- [<span data-ttu-id="ea6a9-151">WPF 中的印刷樣式</span><span class="sxs-lookup"><span data-stu-id="ea6a9-151">Typography in WPF</span></span>](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)
- [<span data-ttu-id="ea6a9-152">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="ea6a9-152">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
- [<span data-ttu-id="ea6a9-153">Text</span><span class="sxs-lookup"><span data-stu-id="ea6a9-153">Text</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)
