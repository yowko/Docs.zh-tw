---
title: OpenType 字型功能
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], OpenType
- typography [WPF], OpenType font technology
- OpenType font technology [WPF]
ms.assetid: 4061a9d1-fe8b-4921-9e17-18ec7d2e3ea2
ms.openlocfilehash: 5751efe0c6621425b8b54c642d51127118c0b6bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529776"
---
# <a name="opentype-font-features"></a><span data-ttu-id="82419-102">OpenType 字型功能</span><span class="sxs-lookup"><span data-stu-id="82419-102">OpenType Font Features</span></span>
<span data-ttu-id="82419-103">本主題提供 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 的 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型技術重要功能概觀。</span><span class="sxs-lookup"><span data-stu-id="82419-103">This topic provides an overview of some of the key features of [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] font technology in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  

  
<a name="overview"></a>   
## <a name="opentype-font-format"></a><span data-ttu-id="82419-104">OpenType 字型格式</span><span class="sxs-lookup"><span data-stu-id="82419-104">OpenType Font Format</span></span>  
 <span data-ttu-id="82419-105">[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型格式是 [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] 字型格式的延伸模組，新增 PostScript 字型資料的支援。</span><span class="sxs-lookup"><span data-stu-id="82419-105">The [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] font format is an extension of the [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] font format, adding support for PostScript font data.</span></span> <span data-ttu-id="82419-106">[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型格式是由 [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] 和 Adobe Corporation 共同開發。</span><span class="sxs-lookup"><span data-stu-id="82419-106">The [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] font format was developed jointly by [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] and Adobe Corporation.</span></span> <span data-ttu-id="82419-107">支援 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型的 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型和作業系統服務，提供使用者簡單的字型安裝與使用方式，無論字型包含 [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] 外框或 CFF (PostScript) 外框。</span><span class="sxs-lookup"><span data-stu-id="82419-107">[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fonts and the operating system services which support [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fonts provide users with a simple way to install and use fonts, whether the fonts contain [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] outlines or CFF (PostScript) outlines.</span></span>  
  
 <span data-ttu-id="82419-108">[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型格式解決下列開發人員難題︰</span><span class="sxs-lookup"><span data-stu-id="82419-108">The [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] font format addresses the following developer challenges:</span></span>  
  
-   <span data-ttu-id="82419-109">更廣泛的多平台支援。</span><span class="sxs-lookup"><span data-stu-id="82419-109">Broader multi-platform support.</span></span>  
  
-   <span data-ttu-id="82419-110">更好的國際字元集支援。</span><span class="sxs-lookup"><span data-stu-id="82419-110">Better support for international character sets.</span></span>  
  
-   <span data-ttu-id="82419-111">更好的字型資料保護。</span><span class="sxs-lookup"><span data-stu-id="82419-111">Better protection for font data.</span></span>  
  
-   <span data-ttu-id="82419-112">較小的檔案大小，讓字型發佈更有效率。</span><span class="sxs-lookup"><span data-stu-id="82419-112">Smaller file sizes to make font distribution more efficient.</span></span>  
  
-   <span data-ttu-id="82419-113">進階印刷樣式控制項的廣泛支援。</span><span class="sxs-lookup"><span data-stu-id="82419-113">Broader support for advanced typographic control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82419-114">此 Windows SDK 包含一組範例 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型，可與 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式搭配使用。</span><span class="sxs-lookup"><span data-stu-id="82419-114">The Windows SDK contains a set of sample [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fonts that you can use with [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications.</span></span> <span data-ttu-id="82419-115">本主題後文會說明這些字型提供的大部分功能。</span><span class="sxs-lookup"><span data-stu-id="82419-115">These fonts provide most of the features illustrated in the rest of this topic.</span></span> <span data-ttu-id="82419-116">如需詳細資訊，請參閱[範例 OpenType 字型套件](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)。</span><span class="sxs-lookup"><span data-stu-id="82419-116">For more information, see [Sample OpenType Font Pack](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md).</span></span>  
  
 <span data-ttu-id="82419-117">如需 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型格式的詳細資訊，請參閱 [OpenType 規格](https://go.microsoft.com/fwlink/?LinkId=96731)。</span><span class="sxs-lookup"><span data-stu-id="82419-117">See the [OpenType Specification](https://go.microsoft.com/fwlink/?LinkId=96731) for details of the [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] font format.</span></span>  
  
### <a name="advanced-typographic-extensions"></a><span data-ttu-id="82419-118">進階的印刷樣式延伸模組</span><span class="sxs-lookup"><span data-stu-id="82419-118">Advanced Typographic Extensions</span></span>  
 <span data-ttu-id="82419-119">進階印刷樣式資料表 ([!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 版面配置表格) 使用 [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] 或 CFF 外框來擴充字型功能。</span><span class="sxs-lookup"><span data-stu-id="82419-119">The Advanced Typographic tables ([!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Layout tables) extend the functionality of fonts with either [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] or CFF outlines.</span></span> [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] <span data-ttu-id="82419-120">版面配置字型包含延伸字型功能的其他資訊，支援高品質的國際印刷樣式。</span><span class="sxs-lookup"><span data-stu-id="82419-120">Layout fonts contain additional information that extends the capabilities of the fonts to support high-quality international typography.</span></span> <span data-ttu-id="82419-121">大部分 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型只公開總計的 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 可用功能子集。</span><span class="sxs-lookup"><span data-stu-id="82419-121">Most [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fonts expose only a subset of the total [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] features available.</span></span> [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] <span data-ttu-id="82419-122">字型提供下列功能。</span><span class="sxs-lookup"><span data-stu-id="82419-122">fonts provide the following features.</span></span>  
  
-   <span data-ttu-id="82419-123">字元與字符之間的豐富對應，支援連音符號、位置形式、替代項目，以及其他字型替代項目。</span><span class="sxs-lookup"><span data-stu-id="82419-123">Rich mapping between characters and glyphs that support ligatures, positional forms, alternates, and other font substitutions.</span></span>  
  
-   <span data-ttu-id="82419-124">支援二維定位與字符附件。</span><span class="sxs-lookup"><span data-stu-id="82419-124">Support for two-dimensional positioning and glyph attachment.</span></span>  
  
-   <span data-ttu-id="82419-125">字型中包含明確的指令碼和語言資訊，因此文字處理應用程式可據以調整其行為。</span><span class="sxs-lookup"><span data-stu-id="82419-125">Explicit script and language information contained in font, so a text-processing application can adjust its behavior accordingly.</span></span>  
  
 <span data-ttu-id="82419-126">在 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 規格的[字型檔案表格＞](https://www.microsoft.com/typography/otspec/otff.htm)一節中，會詳細說明 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 版面配置表格。</span><span class="sxs-lookup"><span data-stu-id="82419-126">The [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Layout tables are described in more detail in the ["Font File Tables"](https://www.microsoft.com/typography/otspec/otff.htm) section of the [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] specification.</span></span>  
  
 <span data-ttu-id="82419-127">本概觀的其餘部分會介紹一些視覺有趣的彈性與廣度[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]的屬性所公開的功能<xref:System.Windows.Documents.Typography>物件。</span><span class="sxs-lookup"><span data-stu-id="82419-127">The remainder of this overview introduces the breadth and flexibility of some of the visually-interesting [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] features that are exposed by the properties of the <xref:System.Windows.Documents.Typography> object.</span></span> <span data-ttu-id="82419-128">如需此物件的詳細資訊，請參閱[印刷樣式類別](#typography_class)。</span><span class="sxs-lookup"><span data-stu-id="82419-128">For more information on this object, see [Typography Class](#typography_class).</span></span>  
  
<a name="variants"></a>   
## <a name="variants"></a><span data-ttu-id="82419-129">變異</span><span class="sxs-lookup"><span data-stu-id="82419-129">Variants</span></span>  
 <span data-ttu-id="82419-130">用來轉譯不同印刷樣式的變數，例如上標和下標。</span><span class="sxs-lookup"><span data-stu-id="82419-130">Variants are used to render different typographic styles, such as superscripts and subscripts.</span></span>  
  
### <a name="superscripts-and-subscripts"></a><span data-ttu-id="82419-131">上標和下標</span><span class="sxs-lookup"><span data-stu-id="82419-131">Superscripts and Subscripts</span></span>  
 <span data-ttu-id="82419-132"><xref:System.Windows.Documents.Typography.Variants%2A>屬性可讓您設定的上標和下標值[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字型。</span><span class="sxs-lookup"><span data-stu-id="82419-132">The <xref:System.Windows.Documents.Typography.Variants%2A> property allows you to set superscript and subscript values for an [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] font.</span></span>  
  
 <span data-ttu-id="82419-133">下列文字顯示上標 Palatino Linotype 字型。</span><span class="sxs-lookup"><span data-stu-id="82419-133">The following text displays superscripts for the Palatino Linotype font.</span></span>  
  
 <span data-ttu-id="82419-134">![使用 OpenType 上標的文字](../../../../docs/framework/wpf/advanced/media/opentypefont14.gif "opentypefont14")</span><span class="sxs-lookup"><span data-stu-id="82419-134">![Text using OpenType superscripts](../../../../docs/framework/wpf/advanced/media/opentypefont14.gif "opentypefont14")</span></span>  
<span data-ttu-id="82419-135">使用 OpenType 上標的文字</span><span class="sxs-lookup"><span data-stu-id="82419-135">Text using OpenType superscripts</span></span>  
  
 <span data-ttu-id="82419-136">下列標記範例示範如何定義上標 Palatino Linotype 字型，使用的屬性<xref:System.Windows.Documents.Typography>物件。</span><span class="sxs-lookup"><span data-stu-id="82419-136">The following markup example shows how to define superscripts for the Palatino Linotype font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 <span data-ttu-id="82419-137">下列文字顯示下標 Palatino Linotype 字型。</span><span class="sxs-lookup"><span data-stu-id="82419-137">The following text displays subscripts for the Palatino Linotype font.</span></span>  
  
 <span data-ttu-id="82419-138">![使用 OpenType 下標的文字](../../../../docs/framework/wpf/advanced/media/opentypefont15.gif "opentypefont15")</span><span class="sxs-lookup"><span data-stu-id="82419-138">![Text using OpenType subscripts](../../../../docs/framework/wpf/advanced/media/opentypefont15.gif "opentypefont15")</span></span>  
<span data-ttu-id="82419-139">使用 OpenType 下標的文字</span><span class="sxs-lookup"><span data-stu-id="82419-139">Text using OpenType subscripts</span></span>  
  
 <span data-ttu-id="82419-140">下列標記範例示範如何定義下標 Palatino Linotype 字型，使用的屬性<xref:System.Windows.Documents.Typography>物件。</span><span class="sxs-lookup"><span data-stu-id="82419-140">The following markup example shows how to define subscripts for the Palatino Linotype font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a><span data-ttu-id="82419-141">上標和下標的裝飾性用途</span><span class="sxs-lookup"><span data-stu-id="82419-141">Decorative Uses of Superscripts and Subscripts</span></span>  
 <span data-ttu-id="82419-142">您也可以使用上標和下標建立混合大小寫文字的裝飾效果。</span><span class="sxs-lookup"><span data-stu-id="82419-142">You can also use superscripts and subscripts to create decorative effects of mixed case text.</span></span> <span data-ttu-id="82419-143">下列文字顯示 Palatino Linotype 字型的上下標文字。</span><span class="sxs-lookup"><span data-stu-id="82419-143">The following text displays superscript and subscript text for the Palatino Linotype font.</span></span> <span data-ttu-id="82419-144">請注意，大寫字不受影響。</span><span class="sxs-lookup"><span data-stu-id="82419-144">Note that the capitals are not affected.</span></span>  
  
 <span data-ttu-id="82419-145">![使用 OpenType 上標和下標的文字](../../../../docs/framework/wpf/advanced/media/opentypefont16.gif "opentypefont16")</span><span class="sxs-lookup"><span data-stu-id="82419-145">![Text using OpenType superscripts and subscripts](../../../../docs/framework/wpf/advanced/media/opentypefont16.gif "opentypefont16")</span></span>  
<span data-ttu-id="82419-146">使用 OpenType 上標和下標的文字</span><span class="sxs-lookup"><span data-stu-id="82419-146">Text using OpenType superscripts and subscripts</span></span>  
  
 <span data-ttu-id="82419-147">下列標記範例示範如何定義上標和下標的字型，使用的屬性<xref:System.Windows.Documents.Typography>物件。</span><span class="sxs-lookup"><span data-stu-id="82419-147">The following markup example shows how to define superscripts and subscripts for a font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>   
## <a name="capitals"></a><span data-ttu-id="82419-148">大寫字</span><span class="sxs-lookup"><span data-stu-id="82419-148">Capitals</span></span>  
 <span data-ttu-id="82419-149">大寫字是一組以大寫樣式字符轉譯文字的印刷格式。</span><span class="sxs-lookup"><span data-stu-id="82419-149">Capitals are a set of typographical forms that render text in capital-styled glyphs.</span></span> <span data-ttu-id="82419-150">一般而言，當文字全部轉譯為大寫時，字母之間的間距可能太近，字母的加權和比例會過重。</span><span class="sxs-lookup"><span data-stu-id="82419-150">Typically, when text is rendered as all capitals, the spacing between letters can appear too tight, and the weight and proportion of the letters too heavy.</span></span> [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] <span data-ttu-id="82419-151">支援數種大寫字樣式格式，包括小型大寫字、特小大寫字、標題和大寫字母間距。</span><span class="sxs-lookup"><span data-stu-id="82419-151">supports a number of styling formats for capitals, including small capitals, petite capitals, titling, and capital spacing.</span></span> <span data-ttu-id="82419-152">這些樣式格式可讓您控制大寫字的外觀。</span><span class="sxs-lookup"><span data-stu-id="82419-152">These styling formats allow you to control the appearance of capitals.</span></span>  
  
 <span data-ttu-id="82419-153">下列文字顯示 Pescadero 字型的標準大寫字母，後面接著樣式設定為 "SmallCaps" 和 "AllSmallCaps" 的字母。</span><span class="sxs-lookup"><span data-stu-id="82419-153">The following text displays standard capital letters for the Pescadero font, followed by the letters styled as "SmallCaps" and "AllSmallCaps".</span></span> <span data-ttu-id="82419-154">在此情況下，三個單字全都使用相同的字型大小。</span><span class="sxs-lookup"><span data-stu-id="82419-154">In this case, the same font size is used for all three words.</span></span>  
  
 <span data-ttu-id="82419-155">![使用 OpenType 大寫的文字](../../../../docs/framework/wpf/advanced/media/opentypefont11.gif "opentypefont11")</span><span class="sxs-lookup"><span data-stu-id="82419-155">![Text using OpenType capitals](../../../../docs/framework/wpf/advanced/media/opentypefont11.gif "opentypefont11")</span></span>  
<span data-ttu-id="82419-156">使用 OpenType 大寫的文字</span><span class="sxs-lookup"><span data-stu-id="82419-156">Text using OpenType capitals</span></span>  
  
 <span data-ttu-id="82419-157">下列標記範例示範如何定義使用的屬性 Pescadero 字型的大寫字<xref:System.Windows.Documents.Typography>物件。</span><span class="sxs-lookup"><span data-stu-id="82419-157">The following markup example shows how to define capitals for the Pescadero font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span> <span data-ttu-id="82419-158">使用 "SmallCaps" 格式時會略過任何開頭的大寫字母。</span><span class="sxs-lookup"><span data-stu-id="82419-158">When the "SmallCaps" format is used, any leading capital letter is ignored.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a><span data-ttu-id="82419-159">標題大寫字</span><span class="sxs-lookup"><span data-stu-id="82419-159">Titling Capitals</span></span>  
 <span data-ttu-id="82419-160">標題大寫字的加權和比例較輕，設計目的是為了比正常大寫字母看起來更雅緻。</span><span class="sxs-lookup"><span data-stu-id="82419-160">Titling capitals are lighter in weight and proportion and designed to give a more elegant look than normal capitals.</span></span> <span data-ttu-id="82419-161">標題大寫字通常用於較大的字型大小作為標題。</span><span class="sxs-lookup"><span data-stu-id="82419-161">Titling capitals are typically used in larger font sizes as headings.</span></span> <span data-ttu-id="82419-162">下列文字顯示 Pescadero 字型的正常和標題大寫字。</span><span class="sxs-lookup"><span data-stu-id="82419-162">The following text displays normal and titling capitals for the Pescadero font.</span></span> <span data-ttu-id="82419-163">請注意第二行文字較窄的主體寬度。</span><span class="sxs-lookup"><span data-stu-id="82419-163">Notice the narrower stem widths of the text on the second line.</span></span>  
  
 <span data-ttu-id="82419-164">![使用 OpenType 標題用大寫的文字](../../../../docs/framework/wpf/advanced/media/opentypefont20.gif "OpenTypeFont20")</span><span class="sxs-lookup"><span data-stu-id="82419-164">![Text using OpenType titling capitals](../../../../docs/framework/wpf/advanced/media/opentypefont20.gif "OpenTypeFont20")</span></span>  
<span data-ttu-id="82419-165">使用 OpenType 標題用大寫的文字</span><span class="sxs-lookup"><span data-stu-id="82419-165">Text using OpenType titling capitals</span></span>  
  
 <span data-ttu-id="82419-166">下列標記範例示範如何定義 Pescadero 字型，使用的屬性標題大寫字<xref:System.Windows.Documents.Typography>物件。</span><span class="sxs-lookup"><span data-stu-id="82419-166">The following markup example shows how to define titling capitals for the Pescadero font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a><span data-ttu-id="82419-167">大寫字母間距</span><span class="sxs-lookup"><span data-stu-id="82419-167">Capital Spacing</span></span>  
 <span data-ttu-id="82419-168">大寫字母間距功能可讓您在全部使用大寫字的文字中，提供更多的間距。</span><span class="sxs-lookup"><span data-stu-id="82419-168">Capital spacing is a feature that allows you to provide more spacing when using all capitals in text.</span></span> <span data-ttu-id="82419-169">大寫字母通常會設計為與小寫字母混合在一起。</span><span class="sxs-lookup"><span data-stu-id="82419-169">Capital letters are typically designed to blend with lowercase letters.</span></span> <span data-ttu-id="82419-170">大寫字母和小寫字母間看起來很不錯的間距，在全部使用大寫字母時會看起來很擠。</span><span class="sxs-lookup"><span data-stu-id="82419-170">Spacing that appears attractive between and a capital letter and a lowercase letter may look too tight when all capital letters are used.</span></span> <span data-ttu-id="82419-171">下列文字顯示 Pescadero 字型的正常和大寫字間距。</span><span class="sxs-lookup"><span data-stu-id="82419-171">The following text displays normal and capital spacing for the Pescadero font.</span></span>  
  
 <span data-ttu-id="82419-172">![使用 opentype 大寫留空的文字](../../../../docs/framework/wpf/advanced/media/opentypefont21.gif "OpenTypeFont21")</span><span class="sxs-lookup"><span data-stu-id="82419-172">![Text using OpenType capital spacing](../../../../docs/framework/wpf/advanced/media/opentypefont21.gif "OpenTypeFont21")</span></span>  
<span data-ttu-id="82419-173">使用 OpenType 大寫留空的文字</span><span class="sxs-lookup"><span data-stu-id="82419-173">Text using OpenType capital spacing</span></span>  
  
 <span data-ttu-id="82419-174">下列標記範例示範如何定義 Pescadero 字型，使用的屬性的大寫字母間距<xref:System.Windows.Documents.Typography>物件。</span><span class="sxs-lookup"><span data-stu-id="82419-174">The following markup example shows how to define capital spacing for the Pescadero font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>   
## <a name="ligatures"></a><span data-ttu-id="82419-175">連音符號</span><span class="sxs-lookup"><span data-stu-id="82419-175">Ligatures</span></span>  
 <span data-ttu-id="82419-176">連音符號是兩個或以上的字符，形成單一字符以建立更清晰或更美觀的文字。</span><span class="sxs-lookup"><span data-stu-id="82419-176">Ligatures are two or more glyphs that are formed into a single glyph in order to create more readable or attractive text.</span></span> [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] <span data-ttu-id="82419-177">字型支援四種連音符號︰</span><span class="sxs-lookup"><span data-stu-id="82419-177">fonts support four types of ligatures:</span></span>  
  
-   <span data-ttu-id="82419-178">**標準連音符號**。</span><span class="sxs-lookup"><span data-stu-id="82419-178">**Standard ligatures**.</span></span> <span data-ttu-id="82419-179">設計目的旨在增進可讀性。</span><span class="sxs-lookup"><span data-stu-id="82419-179">Designed to enhance readability.</span></span> <span data-ttu-id="82419-180">標準連音符號包括 "fi"、"fl" 和 "ff"。</span><span class="sxs-lookup"><span data-stu-id="82419-180">Standard ligatures include "fi", "fl", and "ff".</span></span>  
  
-   <span data-ttu-id="82419-181">**內容連音符號**。</span><span class="sxs-lookup"><span data-stu-id="82419-181">**Contextual ligatures**.</span></span> <span data-ttu-id="82419-182">設計目的旨在提供組成連音符號的字元間更好的聯結行為，以提升可讀性。</span><span class="sxs-lookup"><span data-stu-id="82419-182">Designed to enhance readability by providing better joining behavior between the characters that make up the ligature.</span></span>  
  
-   <span data-ttu-id="82419-183">**Discretionary 連音符號**。</span><span class="sxs-lookup"><span data-stu-id="82419-183">**Discretionary ligatures**.</span></span> <span data-ttu-id="82419-184">設計成裝飾之用，並不是特別針對可讀性設計。</span><span class="sxs-lookup"><span data-stu-id="82419-184">Designed to be ornamental, and not specifically designed for readability.</span></span>  
  
-   <span data-ttu-id="82419-185">**過往連音符號**。</span><span class="sxs-lookup"><span data-stu-id="82419-185">**Historical ligatures**.</span></span> <span data-ttu-id="82419-186">設計成記錄之用，並不是特別針對可讀性所設計。</span><span class="sxs-lookup"><span data-stu-id="82419-186">Designed to be historical, and not specifically designed for readability.</span></span>  
  
 <span data-ttu-id="82419-187">下列文字顯示 Pericles 字型的標準連音符號字符。</span><span class="sxs-lookup"><span data-stu-id="82419-187">The following text displays standard ligature glyphs for the Pericles font.</span></span>  
  
 <span data-ttu-id="82419-188">![使用 OpenType 標準連音符號的文字](../../../../docs/framework/wpf/advanced/media/opentypefont04.gif "opentypefont04")</span><span class="sxs-lookup"><span data-stu-id="82419-188">![Text using OpenType standard ligatures](../../../../docs/framework/wpf/advanced/media/opentypefont04.gif "opentypefont04")</span></span>  
<span data-ttu-id="82419-189">使用 OpenType 標準連字的文字</span><span class="sxs-lookup"><span data-stu-id="82419-189">Text using OpenType standard ligatures</span></span>  
  
 <span data-ttu-id="82419-190">下列標記範例示範如何定義 Pericles 字型，使用的屬性的標準連音符號字符<xref:System.Windows.Documents.Typography>物件。</span><span class="sxs-lookup"><span data-stu-id="82419-190">The following markup example shows how to define standard ligature glyphs for the Pericles font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 <span data-ttu-id="82419-191">下列文字顯示 Pericles 字型 Discretionary 連音符號。</span><span class="sxs-lookup"><span data-stu-id="82419-191">The following text displays discretionary ligature glyphs for the Pericles font.</span></span>  
  
 <span data-ttu-id="82419-192">![使用 OpenType discretionary 連音符號的文字](../../../../docs/framework/wpf/advanced/media/opentypefont05.gif "opentypefont05")</span><span class="sxs-lookup"><span data-stu-id="82419-192">![Text using OpenType discretionary ligatures](../../../../docs/framework/wpf/advanced/media/opentypefont05.gif "opentypefont05")</span></span>  
<span data-ttu-id="82419-193">使用 OpenType Discretionary 連字的文字</span><span class="sxs-lookup"><span data-stu-id="82419-193">Text using OpenType discretionary ligatures</span></span>  
  
 <span data-ttu-id="82419-194">下列標記範例示範如何定義使用的屬性 Pericles 字型 discretionary 連音符號字符<xref:System.Windows.Documents.Typography>物件。</span><span class="sxs-lookup"><span data-stu-id="82419-194">The following markup example shows how to define discretionary ligature glyphs for the Pericles font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 <span data-ttu-id="82419-195">根據預設，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型會啟用標準連音符號。</span><span class="sxs-lookup"><span data-stu-id="82419-195">By default, [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fonts in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] enable standard ligatures.</span></span> <span data-ttu-id="82419-196">例如，如果您使用 Palatino Linotype 字型，標準連音符號 "fi"、"ff" 和 "fl" 會顯示為合併的字元字符。</span><span class="sxs-lookup"><span data-stu-id="82419-196">For example, if you use the Palatino Linotype font, the standard ligatures "fi", "ff", and "fl" appear as a combined character glyph.</span></span> <span data-ttu-id="82419-197">請注意，每個標準連音符號的成對字元都彼此相鄰。</span><span class="sxs-lookup"><span data-stu-id="82419-197">Notice that the pair of characters for each standard ligature touch each other.</span></span>  
  
 <span data-ttu-id="82419-198">![使用 OpenType 標準連音符號的文字](../../../../docs/framework/wpf/advanced/media/opentypefont06.gif "opentypefont06")</span><span class="sxs-lookup"><span data-stu-id="82419-198">![Text using OpenType standard ligatures](../../../../docs/framework/wpf/advanced/media/opentypefont06.gif "opentypefont06")</span></span>  
<span data-ttu-id="82419-199">使用 OpenType 標準連字的文字</span><span class="sxs-lookup"><span data-stu-id="82419-199">Text using OpenType standard ligatures</span></span>  
  
 <span data-ttu-id="82419-200">不過，您可以停用標準連音符號功能，讓 "ff" 等標準連音符號顯示為兩個分開的字符，而不是合併的字元字符。</span><span class="sxs-lookup"><span data-stu-id="82419-200">However, you can disable standard ligature features so that a standard ligature such as "ff" displays as two separate glyphs, rather than as a combined character glyph.</span></span>  
  
 <span data-ttu-id="82419-201">![文字使用已停用 OpenType 標準連音符號](../../../../docs/framework/wpf/advanced/media/opentypefont07.gif "opentypefont07")</span><span class="sxs-lookup"><span data-stu-id="82419-201">![Text using disabled OpenType standard ligatures](../../../../docs/framework/wpf/advanced/media/opentypefont07.gif "opentypefont07")</span></span>  
<span data-ttu-id="82419-202">使用已停用之 OpenType 標準連字的文字</span><span class="sxs-lookup"><span data-stu-id="82419-202">Text using disabled OpenType standard ligatures</span></span>  
  
 <span data-ttu-id="82419-203">下列標記範例示範如何停用 Palatino Linotype 字型，使用的屬性的標準連音符號字符<xref:System.Windows.Documents.Typography>物件。</span><span class="sxs-lookup"><span data-stu-id="82419-203">The following markup example shows how to disable standard ligature glyphs for the Palatino Linotype font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>   
## <a name="swashes"></a><span data-ttu-id="82419-204">花飾字</span><span class="sxs-lookup"><span data-stu-id="82419-204">Swashes</span></span>  
 <span data-ttu-id="82419-205">花飾字是裝飾性字符，使用精心設計且通常與書寫體相關聯的裝飾。</span><span class="sxs-lookup"><span data-stu-id="82419-205">Swashes are decorative glyphs that use elaborate ornamentation often associated with calligraphy.</span></span> <span data-ttu-id="82419-206">下列文字顯示 Pescadero 字型的標準和花飾字字符。</span><span class="sxs-lookup"><span data-stu-id="82419-206">The following text displays standard and swash glyphs for the Pescadero font.</span></span>  
  
 <span data-ttu-id="82419-207">![使用 OpenType 標準和花飾字字符的文字](../../../../docs/framework/wpf/advanced/media/opentypefont08.gif "opentypefont08")</span><span class="sxs-lookup"><span data-stu-id="82419-207">![Text using OpenType standard and swash glyphs](../../../../docs/framework/wpf/advanced/media/opentypefont08.gif "opentypefont08")</span></span>  
<span data-ttu-id="82419-208">使用 OpenType 標準和勾耳圖像的文字</span><span class="sxs-lookup"><span data-stu-id="82419-208">Text using OpenType standard and swash glyphs</span></span>  
  
 <span data-ttu-id="82419-209">花飾字通常用為簡短片語中的裝飾項目，例如事件宣告。</span><span class="sxs-lookup"><span data-stu-id="82419-209">Swashes are often used as decorative elements in short phrases such as event announcements.</span></span> <span data-ttu-id="82419-210">下列文字使用花飾字強調大寫字母的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="82419-210">The following text uses swashes to emphasize the capital letters of the name of the event.</span></span>  
  
 <span data-ttu-id="82419-211">![使用 OpenType 花飾字的文字](../../../../docs/framework/wpf/advanced/media/opentypefont09.gif "opentypefont09")</span><span class="sxs-lookup"><span data-stu-id="82419-211">![Text using OpenType swashes](../../../../docs/framework/wpf/advanced/media/opentypefont09.gif "opentypefont09")</span></span>  
<span data-ttu-id="82419-212">使用 OpenType 勾耳的文字</span><span class="sxs-lookup"><span data-stu-id="82419-212">Text using OpenType swashes</span></span>  
  
 <span data-ttu-id="82419-213">下列標記範例示範如何定義使用的內容的字型的花飾字<xref:System.Windows.Documents.Typography>物件。</span><span class="sxs-lookup"><span data-stu-id="82419-213">The following markup example shows how to define swashes for a font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a><span data-ttu-id="82419-214">內容花飾字</span><span class="sxs-lookup"><span data-stu-id="82419-214">Contextual Swashes</span></span>  
 <span data-ttu-id="82419-215">某些花飾字字符的組合會導致不討喜的外觀，例如相鄰字母的伸尾部分重疊。</span><span class="sxs-lookup"><span data-stu-id="82419-215">Certain combinations of swash glyphs can cause an unattractive appearance, such as overlapping descenders on adjacent letters.</span></span> <span data-ttu-id="82419-216">使用內容花飾字可讓您使用會產生更佳外觀的替代花飾字字符。</span><span class="sxs-lookup"><span data-stu-id="82419-216">Using a contextual swash allows you to use a substitute swash glyph that produces a better appearance.</span></span> <span data-ttu-id="82419-217">下列文字顯示套用內容花飾字之前和之後的相同字組。</span><span class="sxs-lookup"><span data-stu-id="82419-217">The following text shows the same word before and after a contextual swash is applied.</span></span>  
  
 <span data-ttu-id="82419-218">![使用 OpenType 內容花飾字的文字](../../../../docs/framework/wpf/advanced/media/opentypefont19.gif "OpenTypeFont19")</span><span class="sxs-lookup"><span data-stu-id="82419-218">![Text using OpenType contextual swashes](../../../../docs/framework/wpf/advanced/media/opentypefont19.gif "OpenTypeFont19")</span></span>  
<span data-ttu-id="82419-219">使用 OpenType 視內容來勾耳的文字</span><span class="sxs-lookup"><span data-stu-id="82419-219">Text using OpenType contextual swashes</span></span>  
  
 <span data-ttu-id="82419-220">下列標記範例示範如何定義 Pescadero 字型，使用的屬性的內容花飾字<xref:System.Windows.Documents.Typography>物件。</span><span class="sxs-lookup"><span data-stu-id="82419-220">The following markup example shows how to define a contextual swash for the Pescadero font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>   
## <a name="alternates"></a><span data-ttu-id="82419-221">替代項目</span><span class="sxs-lookup"><span data-stu-id="82419-221">Alternates</span></span>  
 <span data-ttu-id="82419-222">替代項目是可以取代標準字符的字符。</span><span class="sxs-lookup"><span data-stu-id="82419-222">Alternates are glyphs that can be substituted for a standard glyph.</span></span> [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] <span data-ttu-id="82419-223">字型，例如下例使用的 Pericles 字型，可以包含替代字符，您可用來建立不同的文字外觀。</span><span class="sxs-lookup"><span data-stu-id="82419-223">fonts, such as the Pericles font used in the following examples, can contain alternate glyphs that you can use to create different appearances for text.</span></span> <span data-ttu-id="82419-224">下列文字顯示 Pericles 字型的標準字符。</span><span class="sxs-lookup"><span data-stu-id="82419-224">The following text displays standard glyphs for the Pericles font.</span></span>  
  
 <span data-ttu-id="82419-225">![使用 OpenType 標準字符的文字](../../../../docs/framework/wpf/advanced/media/opentypefont01.gif "opentypefont01")</span><span class="sxs-lookup"><span data-stu-id="82419-225">![Text using OpenType standard glyphs](../../../../docs/framework/wpf/advanced/media/opentypefont01.gif "opentypefont01")</span></span>  
<span data-ttu-id="82419-226">使用 OpenType 標準圖像的文字</span><span class="sxs-lookup"><span data-stu-id="82419-226">Text using OpenType standard glyphs</span></span>  
  
 <span data-ttu-id="82419-227">Pericles [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字型包含其他字符，可為標準字符集提供文體替代項目。</span><span class="sxs-lookup"><span data-stu-id="82419-227">The Pericles [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] font contains additional glyphs that provide stylistic alternates to the standard set of glyphs.</span></span> <span data-ttu-id="82419-228">下列文字顯示文體替代字符。</span><span class="sxs-lookup"><span data-stu-id="82419-228">The following text displays stylistic alternate glyphs.</span></span>  
  
 <span data-ttu-id="82419-229">![使用 OpenType 文體替代字符的文字](../../../../docs/framework/wpf/advanced/media/opentypefont02.gif "opentypefont02")</span><span class="sxs-lookup"><span data-stu-id="82419-229">![Text using OpenType stylistic alternate glyphs](../../../../docs/framework/wpf/advanced/media/opentypefont02.gif "opentypefont02")</span></span>  
<span data-ttu-id="82419-230">使用 OpenType 文體替代圖像的文字</span><span class="sxs-lookup"><span data-stu-id="82419-230">Text using OpenType stylistic alternate glyphs</span></span>  
  
 <span data-ttu-id="82419-231">下列標記範例示範如何定義使用的屬性 Pericles 字型的文體替代字符<xref:System.Windows.Documents.Typography>物件。</span><span class="sxs-lookup"><span data-stu-id="82419-231">The following markup example shows how to define stylistic alternate glyphs for the Pericles font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 <span data-ttu-id="82419-232">下列文字顯示數個 Pericles 字型的其他文體替代字符。</span><span class="sxs-lookup"><span data-stu-id="82419-232">The following text displays several other stylistic alternate glyphs for the Pericles font.</span></span>  
  
 <span data-ttu-id="82419-233">![使用 OpenType 文體替代字符的文字](../../../../docs/framework/wpf/advanced/media/opentypefont03.gif "opentypefont03")</span><span class="sxs-lookup"><span data-stu-id="82419-233">![Text using OpenType stylistic alternate glyphs](../../../../docs/framework/wpf/advanced/media/opentypefont03.gif "opentypefont03")</span></span>  
<span data-ttu-id="82419-234">使用 OpenType 文體替代圖像的文字</span><span class="sxs-lookup"><span data-stu-id="82419-234">Text using OpenType stylistic alternate glyphs</span></span>  
  
 <span data-ttu-id="82419-235">下列標記範例示範如何定義這些其他文體替代字符。</span><span class="sxs-lookup"><span data-stu-id="82419-235">The following markup example shows how to define these other stylistic alternate glyphs.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a><span data-ttu-id="82419-236">隨機內容替代項目</span><span class="sxs-lookup"><span data-stu-id="82419-236">Random Contextual Alternates</span></span>  
 <span data-ttu-id="82419-237">隨機內容替代項目提供單一字元的多個替代字符。</span><span class="sxs-lookup"><span data-stu-id="82419-237">Random contextual alternates provide multiple substitute glyphs for a single character.</span></span> <span data-ttu-id="82419-238">以書寫體字型實作時，這項功能可以使用一組隨機選擇的字符，在外觀上略加變動來模擬手寫。</span><span class="sxs-lookup"><span data-stu-id="82419-238">When implemented with script-type fonts, this feature can simulate handwriting by using of a set of randomly chosen glyphs with slight differences in appearance.</span></span> <span data-ttu-id="82419-239">下列文字使用 Lindsey 字型的隨機內容替代項目。</span><span class="sxs-lookup"><span data-stu-id="82419-239">The following text uses random contextual alternates for the Lindsey font.</span></span> <span data-ttu-id="82419-240">請注意，字母 "a" 的外觀略有不同。</span><span class="sxs-lookup"><span data-stu-id="82419-240">Notice that the letter "a" varies slightly in appearance</span></span>  
  
 <span data-ttu-id="82419-241">![使用 OpenType 隨機內容替代的文字](../../../../docs/framework/wpf/advanced/media/opentypefont23.gif "OpenTypeFont23")</span><span class="sxs-lookup"><span data-stu-id="82419-241">![Text using OpenType random contextual alternates](../../../../docs/framework/wpf/advanced/media/opentypefont23.gif "OpenTypeFont23")</span></span>  
<span data-ttu-id="82419-242">使用 OpenType 隨機內容替代的文字</span><span class="sxs-lookup"><span data-stu-id="82419-242">Text using OpenType random contextual alternates</span></span>  
  
 <span data-ttu-id="82419-243">下列標記範例示範如何定義 Lindsey 字型，使用的屬性的隨機內容替代項目<xref:System.Windows.Documents.Typography>物件。</span><span class="sxs-lookup"><span data-stu-id="82419-243">The following markup example shows how to define random contextual alternates for the Lindsey font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a><span data-ttu-id="82419-244">古體形式</span><span class="sxs-lookup"><span data-stu-id="82419-244">Historical Forms</span></span>  
 <span data-ttu-id="82419-245">古體形式是過去常用的印刷樣式慣例。</span><span class="sxs-lookup"><span data-stu-id="82419-245">Historical forms are typographic conventions that were common in the past.</span></span> <span data-ttu-id="82419-246">下列文字使用 Palatino Linotype 字型的古體形式字符顯示 "Boston, Massachusetts" 片語。</span><span class="sxs-lookup"><span data-stu-id="82419-246">The following text displays the phrase, "Boston, Massachusetts", using an historical form of glyphs for the Palatino Linotype font.</span></span>  
  
 <span data-ttu-id="82419-247">![使用 opentype 古體形式的文字](../../../../docs/framework/wpf/advanced/media/opentypefont10.gif "opentypefont10")</span><span class="sxs-lookup"><span data-stu-id="82419-247">![Text using OpenType historical forms](../../../../docs/framework/wpf/advanced/media/opentypefont10.gif "opentypefont10")</span></span>  
<span data-ttu-id="82419-248">使用 OpenType 古體形式的文字</span><span class="sxs-lookup"><span data-stu-id="82419-248">Text using OpenType historical forms</span></span>  
  
 <span data-ttu-id="82419-249">下列標記範例示範如何定義 Palatino Linotype 字型，請使用屬性的古體形式<xref:System.Windows.Documents.Typography>物件。</span><span class="sxs-lookup"><span data-stu-id="82419-249">The following markup example shows how to define historical forms for the Palatino Linotype font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>   
## <a name="numerical-styles"></a><span data-ttu-id="82419-250">數字的樣式</span><span class="sxs-lookup"><span data-stu-id="82419-250">Numerical Styles</span></span>  
 <span data-ttu-id="82419-251">OpenType 字型支援大量可搭配文字中數值使用的功能。</span><span class="sxs-lookup"><span data-stu-id="82419-251">OpenType fonts support a large number of features that can be used with numerical values in text.</span></span>  
  
### <a name="fractions"></a><span data-ttu-id="82419-252">分數</span><span class="sxs-lookup"><span data-stu-id="82419-252">Fractions</span></span>  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] <span data-ttu-id="82419-253">字型支援分數樣式，包括斜式和直式。</span><span class="sxs-lookup"><span data-stu-id="82419-253">fonts support styles for fractions, including slashed and stacked.</span></span>  
  
 <span data-ttu-id="82419-254">下列文字顯示 Palatino Linotype 字型的分數樣式。</span><span class="sxs-lookup"><span data-stu-id="82419-254">The following text displays fraction styles for the Palatino Linotype font.</span></span>  
  
 <span data-ttu-id="82419-255">![使用 OpenType 斜式和直式分數](../../../../docs/framework/wpf/advanced/media/opentypefont12.gif "opentypefont12")</span><span class="sxs-lookup"><span data-stu-id="82419-255">![Text using OpenType slashed and stacked fractions](../../../../docs/framework/wpf/advanced/media/opentypefont12.gif "opentypefont12")</span></span>  
<span data-ttu-id="82419-256">使用 OpenType 斜式和直式分數的文字</span><span class="sxs-lookup"><span data-stu-id="82419-256">Text using OpenType slashed and stacked fractions</span></span>  
  
 <span data-ttu-id="82419-257">下列標記範例示範如何定義 Palatino Linotype 字型，使用的屬性的分數樣式<xref:System.Windows.Documents.Typography>物件。</span><span class="sxs-lookup"><span data-stu-id="82419-257">The following markup example shows how to define fraction styles for the Palatino Linotype font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a><span data-ttu-id="82419-258">舊樣式數字</span><span class="sxs-lookup"><span data-stu-id="82419-258">Old Style Numerals</span></span>  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] <span data-ttu-id="82419-259">字型支援舊樣式數字格式。</span><span class="sxs-lookup"><span data-stu-id="82419-259">fonts support an old style numeral format.</span></span> <span data-ttu-id="82419-260">此格式適用於顯示樣式不再標準的數字。</span><span class="sxs-lookup"><span data-stu-id="82419-260">This format is useful for displaying numerals in styles that are no longer standard.</span></span> <span data-ttu-id="82419-261">下列文字使用 Palatino Linotype 字型的標準和舊樣式數字格式顯示 18 世紀的日期。</span><span class="sxs-lookup"><span data-stu-id="82419-261">The following text displays an 18th century date in standard and old style numeral formats for the Palatino Linotype font.</span></span>  
  
 <span data-ttu-id="82419-262">![使用 OpenType 舊樣式數字的文字](../../../../docs/framework/wpf/advanced/media/opentypefont24.gif "OpenTypeFont24")</span><span class="sxs-lookup"><span data-stu-id="82419-262">![Text using OpenType old style numerals](../../../../docs/framework/wpf/advanced/media/opentypefont24.gif "OpenTypeFont24")</span></span>  
<span data-ttu-id="82419-263">使用 OpenType 舊樣式數字的文字</span><span class="sxs-lookup"><span data-stu-id="82419-263">Text using OpenType old style numerals</span></span>  
  
 <span data-ttu-id="82419-264">下列文字顯示 Palatino Linotype 字型的標準數字，後面接著舊樣式數字的數字。</span><span class="sxs-lookup"><span data-stu-id="82419-264">The following text displays standard numerals for the Palatino Linotype font, followed by old style numerals.</span></span>  
  
 <span data-ttu-id="82419-265">![使用 OpenType 舊樣式數字集的文字](../../../../docs/framework/wpf/advanced/media/opentypefont13.gif "opentypefont13")</span><span class="sxs-lookup"><span data-stu-id="82419-265">![Text using OpenType old style numeral sets](../../../../docs/framework/wpf/advanced/media/opentypefont13.gif "opentypefont13")</span></span>  
<span data-ttu-id="82419-266">使用 OpenType 舊樣式數字集的文字</span><span class="sxs-lookup"><span data-stu-id="82419-266">Text using OpenType old style numeral sets</span></span>  
  
 <span data-ttu-id="82419-267">下列標記範例示範如何定義 Palatino Linotype 字型，使用的屬性的舊樣式數字<xref:System.Windows.Documents.Typography>物件。</span><span class="sxs-lookup"><span data-stu-id="82419-267">The following markup example shows how to define old style numerals for the Palatino Linotype font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a><span data-ttu-id="82419-268">調和間距與表格式數字</span><span class="sxs-lookup"><span data-stu-id="82419-268">Proportional and Tabular Figures</span></span>  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] <span data-ttu-id="82419-269">字型支援在使用數字時，以調和間距與表格式數字功能控制寬度對齊。</span><span class="sxs-lookup"><span data-stu-id="82419-269">fonts support a proportional and tabular figure feature to control the alignment of widths when using numerals.</span></span> <span data-ttu-id="82419-270">調和間距數字會將每一個數字視為具有不同的寬度，"1" 比 "5" 窄。</span><span class="sxs-lookup"><span data-stu-id="82419-270">Proportional figures treat each numeral as having a different width—"1" is narrower than "5".</span></span> <span data-ttu-id="82419-271">表格式數字則視為等寬數字，以便垂直對齊，可提高財務類資訊的可讀性。</span><span class="sxs-lookup"><span data-stu-id="82419-271">Tabular figures are treated as equal-width numerals so that they align vertically, which increases the readability of financial type information.</span></span>  
  
 <span data-ttu-id="82419-272">下列文字在第一個資料行中顯示使用 Miramonte 字型的兩個調和間距數字。</span><span class="sxs-lookup"><span data-stu-id="82419-272">The following text displays two proportional figures in the first column using the Miramonte font.</span></span> <span data-ttu-id="82419-273">請注意數字 "5" 和 "1" 之間的寬度差異。</span><span class="sxs-lookup"><span data-stu-id="82419-273">Note the difference in width between the numerals "5" and "1".</span></span> <span data-ttu-id="82419-274">第二個資料行顯示相同的兩個數值，使用表格式數字功能調整其寬度。</span><span class="sxs-lookup"><span data-stu-id="82419-274">The second column shows the same two numeric values with the widths adjusted by using the tabular figure feature.</span></span>  
  
 <span data-ttu-id="82419-275">![使用 OpenType 調和間距與表格式數字的文字](../../../../docs/framework/wpf/advanced/media/opentypefont22.gif "OpenTypeFont22")</span><span class="sxs-lookup"><span data-stu-id="82419-275">![Text using OpenType proportional & tabular figures](../../../../docs/framework/wpf/advanced/media/opentypefont22.gif "OpenTypeFont22")</span></span>  
<span data-ttu-id="82419-276">使用 OpenType 調和間距與表格式數字的文字</span><span class="sxs-lookup"><span data-stu-id="82419-276">Text using OpenType proportional and tabular figures</span></span>  
  
 <span data-ttu-id="82419-277">下列標記範例示範如何定義 Miramonte 字型，使用的屬性的調和間距與表格式數字<xref:System.Windows.Documents.Typography>物件。</span><span class="sxs-lookup"><span data-stu-id="82419-277">The following markup example shows how to define proportional and tabular figures for the Miramonte font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a><span data-ttu-id="82419-278">加斜線的零</span><span class="sxs-lookup"><span data-stu-id="82419-278">Slashed Zero</span></span>  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] <span data-ttu-id="82419-279">字型支援加斜線的零數字格式，以強調字母 "O" 與數字 "0" 之間的差異。</span><span class="sxs-lookup"><span data-stu-id="82419-279">fonts support a slashed zero numeral format to emphasize the difference between the letter "O" and the numeral "0".</span></span> <span data-ttu-id="82419-280">加斜線的零數字通常用於財務和商務資訊中的識別碼。</span><span class="sxs-lookup"><span data-stu-id="82419-280">The slashed zero numeral is often used for identifiers in financial and business information.</span></span>  
  
 <span data-ttu-id="82419-281">下列文字顯示使用 Miramonte 字型的範例訂單識別碼。</span><span class="sxs-lookup"><span data-stu-id="82419-281">The following text displays a sample order identifier using the Miramonte font.</span></span> <span data-ttu-id="82419-282">第一行使用標準的數字。</span><span class="sxs-lookup"><span data-stu-id="82419-282">The first line uses standard numerals.</span></span> <span data-ttu-id="82419-283">第二行使用加斜線的零數字，以突顯與大寫字母 "O" 的對比。</span><span class="sxs-lookup"><span data-stu-id="82419-283">The second line used slashed zero numerals to provide better contrast with the uppercase "O" letter.</span></span>  
  
 <span data-ttu-id="82419-284">![使用 OpenType 斜式零的數字](../../../../docs/framework/wpf/advanced/media/opentypefont17.gif "OpenTypeFont17")</span><span class="sxs-lookup"><span data-stu-id="82419-284">![Text using OpenType slashed zero numerals](../../../../docs/framework/wpf/advanced/media/opentypefont17.gif "OpenTypeFont17")</span></span>  
<span data-ttu-id="82419-285">使用 OpenType 零帶有斜線之數字的文字</span><span class="sxs-lookup"><span data-stu-id="82419-285">Text using OpenType slashed zero numerals</span></span>  
  
 <span data-ttu-id="82419-286">下列標記範例示範如何定義斜線零數字 Miramonte 字型，使用的屬性<xref:System.Windows.Documents.Typography>物件。</span><span class="sxs-lookup"><span data-stu-id="82419-286">The following markup example shows how to define slashed zero numerals for the Miramonte font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>   
## <a name="typography-class"></a><span data-ttu-id="82419-287">印刷樣式類別</span><span class="sxs-lookup"><span data-stu-id="82419-287">Typography Class</span></span>  
 <span data-ttu-id="82419-288"><xref:System.Windows.Documents.Typography>物件會公開一組功能，[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字型支援。</span><span class="sxs-lookup"><span data-stu-id="82419-288">The <xref:System.Windows.Documents.Typography> object exposes the set of features that an [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] font supports.</span></span> <span data-ttu-id="82419-289">藉由設定的屬性<xref:System.Windows.Documents.Typography>在標記中，您可以輕鬆撰寫充分利用的文件[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]功能。</span><span class="sxs-lookup"><span data-stu-id="82419-289">By setting the properties of <xref:System.Windows.Documents.Typography> in markup, you can easily author documents that take advantage of [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] features.</span></span>  
  
 <span data-ttu-id="82419-290">下列文字顯示 Pescadero 字型的標準大寫字母，後面接著樣式設定為 "SmallCaps" 和 "AllSmallCaps" 的字母。</span><span class="sxs-lookup"><span data-stu-id="82419-290">The following text displays standard capital letters for the Pescadero font, followed by the letters styled as "SmallCaps" and "AllSmallCaps".</span></span> <span data-ttu-id="82419-291">在此情況下，三個單字全都使用相同的字型大小。</span><span class="sxs-lookup"><span data-stu-id="82419-291">In this case, the same font size is used for all three words.</span></span>  
  
 <span data-ttu-id="82419-292">![使用 OpenType 大寫的文字](../../../../docs/framework/wpf/advanced/media/opentypefont11.gif "opentypefont11")</span><span class="sxs-lookup"><span data-stu-id="82419-292">![Text using OpenType capitals](../../../../docs/framework/wpf/advanced/media/opentypefont11.gif "opentypefont11")</span></span>  
<span data-ttu-id="82419-293">使用 OpenType 大寫的文字</span><span class="sxs-lookup"><span data-stu-id="82419-293">Text using OpenType capitals</span></span>  
  
 <span data-ttu-id="82419-294">下列標記範例示範如何定義使用的屬性 Pescadero 字型的大寫字<xref:System.Windows.Documents.Typography>物件。</span><span class="sxs-lookup"><span data-stu-id="82419-294">The following markup example shows how to define capitals for the Pescadero font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span> <span data-ttu-id="82419-295">使用 "SmallCaps" 格式時會略過任何開頭的大寫字母。</span><span class="sxs-lookup"><span data-stu-id="82419-295">When the "SmallCaps" format is used, any leading capital letter is ignored.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 <span data-ttu-id="82419-296">下列程式碼範例可以完成與先前標記範例相同的工作。</span><span class="sxs-lookup"><span data-stu-id="82419-296">The following code example accomplishes the same task as the previous markup example.</span></span>  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a><span data-ttu-id="82419-297">印刷樣式類別屬性</span><span class="sxs-lookup"><span data-stu-id="82419-297">Typography Class Properties</span></span>  
 <span data-ttu-id="82419-298">下表列出的屬性、 值和預設設定<xref:System.Windows.Documents.Typography>物件。</span><span class="sxs-lookup"><span data-stu-id="82419-298">The following table lists the properties, values, and default settings of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
|<span data-ttu-id="82419-299">屬性</span><span class="sxs-lookup"><span data-stu-id="82419-299">Property</span></span>|<span data-ttu-id="82419-300">值</span><span class="sxs-lookup"><span data-stu-id="82419-300">Value(s)</span></span>|<span data-ttu-id="82419-301">預設值</span><span class="sxs-lookup"><span data-stu-id="82419-301">Default Value</span></span>|  
|--------------|----------------|-------------------|  
|<xref:System.Windows.Documents.Typography.AnnotationAlternates%2A>|<span data-ttu-id="82419-302">數值 - 位元組</span><span class="sxs-lookup"><span data-stu-id="82419-302">Numeric value - byte</span></span>|<span data-ttu-id="82419-303">0</span><span class="sxs-lookup"><span data-stu-id="82419-303">0</span></span>|  
|<xref:System.Windows.Documents.Typography.Capitals%2A>|<span data-ttu-id="82419-304"><xref:System.Windows.FontCapitals.AllPetiteCaps> &#124; <xref:System.Windows.FontCapitals.AllSmallCaps> &#124; <xref:System.Windows.FontCapitals.Normal> &#124; <xref:System.Windows.FontCapitals.PetiteCaps> &#124; <xref:System.Windows.FontCapitals.SmallCaps> &#124; <xref:System.Windows.FontCapitals.Titling> &#124; <xref:System.Windows.FontCapitals.Unicase></span><span class="sxs-lookup"><span data-stu-id="82419-304"><xref:System.Windows.FontCapitals.AllPetiteCaps> &#124; <xref:System.Windows.FontCapitals.AllSmallCaps> &#124; <xref:System.Windows.FontCapitals.Normal> &#124; <xref:System.Windows.FontCapitals.PetiteCaps> &#124; <xref:System.Windows.FontCapitals.SmallCaps> &#124; <xref:System.Windows.FontCapitals.Titling> &#124; <xref:System.Windows.FontCapitals.Unicase></span></span>|<xref:System.Windows.FontCapitals.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.CapitalSpacing%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.CaseSensitiveForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.ContextualAlternates%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualSwashes%2A>|<span data-ttu-id="82419-305">數值 - 位元組</span><span class="sxs-lookup"><span data-stu-id="82419-305">Numeric value - byte</span></span>|<span data-ttu-id="82419-306">0</span><span class="sxs-lookup"><span data-stu-id="82419-306">0</span></span>|  
|<xref:System.Windows.Documents.Typography.DiscretionaryLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianExpertForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianLanguage%2A>|<span data-ttu-id="82419-307"><xref:System.Windows.FontEastAsianLanguage.HojoKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis04> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis78> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis83> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis90> &#124; <xref:System.Windows.FontEastAsianLanguage.NlcKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Normal> &#124; <xref:System.Windows.FontEastAsianLanguage.Simplified> &#124; <xref:System.Windows.FontEastAsianLanguage.Traditional> &#124; <xref:System.Windows.FontEastAsianLanguage.TraditionalNames></span><span class="sxs-lookup"><span data-stu-id="82419-307"><xref:System.Windows.FontEastAsianLanguage.HojoKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis04> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis78> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis83> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis90> &#124; <xref:System.Windows.FontEastAsianLanguage.NlcKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Normal> &#124; <xref:System.Windows.FontEastAsianLanguage.Simplified> &#124; <xref:System.Windows.FontEastAsianLanguage.Traditional> &#124; <xref:System.Windows.FontEastAsianLanguage.TraditionalNames></span></span>|<xref:System.Windows.FontEastAsianLanguage.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.EastAsianWidths%2A>|<span data-ttu-id="82419-308"><xref:System.Windows.FontEastAsianWidths.Full> &#124; <xref:System.Windows.FontEastAsianWidths.Half> &#124; <xref:System.Windows.FontEastAsianWidths.Normal> &#124; <xref:System.Windows.FontEastAsianWidths.Proportional> &#124; <xref:System.Windows.FontEastAsianWidths.Quarter> &#124; <xref:System.Windows.FontEastAsianWidths.Third></span><span class="sxs-lookup"><span data-stu-id="82419-308"><xref:System.Windows.FontEastAsianWidths.Full> &#124; <xref:System.Windows.FontEastAsianWidths.Half> &#124; <xref:System.Windows.FontEastAsianWidths.Normal> &#124; <xref:System.Windows.FontEastAsianWidths.Proportional> &#124; <xref:System.Windows.FontEastAsianWidths.Quarter> &#124; <xref:System.Windows.FontEastAsianWidths.Third></span></span>|<xref:System.Windows.FontEastAsianWidths.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.Fraction%2A>|<span data-ttu-id="82419-309"><xref:System.Windows.FontFraction.Normal> &#124; <xref:System.Windows.FontFraction.Slashed> &#124; <xref:System.Windows.FontFraction.Stacked></span><span class="sxs-lookup"><span data-stu-id="82419-309"><xref:System.Windows.FontFraction.Normal> &#124; <xref:System.Windows.FontFraction.Slashed> &#124; <xref:System.Windows.FontFraction.Stacked></span></span>|<xref:System.Windows.FontFraction.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.HistoricalForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.HistoricalLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Kerning%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.MathematicalGreek%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.NumeralAlignment%2A>|<span data-ttu-id="82419-310"><xref:System.Windows.FontNumeralAlignment.Normal> &#124; <xref:System.Windows.FontNumeralAlignment.Proportional> &#124; <xref:System.Windows.FontNumeralAlignment.Tabular></span><span class="sxs-lookup"><span data-stu-id="82419-310"><xref:System.Windows.FontNumeralAlignment.Normal> &#124; <xref:System.Windows.FontNumeralAlignment.Proportional> &#124; <xref:System.Windows.FontNumeralAlignment.Tabular></span></span>|<xref:System.Windows.FontNumeralAlignment.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.NumeralStyle%2A>|<xref:System.Boolean>|<xref:System.Windows.FontNumeralStyle.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.SlashedZero%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StandardLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.StandardSwashes%2A>|<span data-ttu-id="82419-311">數值 - 位元組</span><span class="sxs-lookup"><span data-stu-id="82419-311">numeric value – byte</span></span>|<span data-ttu-id="82419-312">0</span><span class="sxs-lookup"><span data-stu-id="82419-312">0</span></span>|  
|<xref:System.Windows.Documents.Typography.StylisticAlternates%2A>|<span data-ttu-id="82419-313">數值 - 位元組</span><span class="sxs-lookup"><span data-stu-id="82419-313">numeric value – byte</span></span>|<span data-ttu-id="82419-314">0</span><span class="sxs-lookup"><span data-stu-id="82419-314">0</span></span>|  
|<xref:System.Windows.Documents.Typography.StylisticSet1%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet2%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet3%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet4%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet5%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet6%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet7%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet8%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet9%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet10%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet11%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet12%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet13%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet14%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet15%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet16%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet17%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet18%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet19%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet20%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Variants%2A>|<span data-ttu-id="82419-315"><xref:System.Windows.FontVariants.Inferior> &#124; <xref:System.Windows.FontVariants.Normal> &#124; <xref:System.Windows.FontVariants.Ordinal> &#124; <xref:System.Windows.FontVariants.Ruby> &#124; <xref:System.Windows.FontVariants.Subscript> &#124; <xref:System.Windows.FontVariants.Superscript></span><span class="sxs-lookup"><span data-stu-id="82419-315"><xref:System.Windows.FontVariants.Inferior> &#124; <xref:System.Windows.FontVariants.Normal> &#124; <xref:System.Windows.FontVariants.Ordinal> &#124; <xref:System.Windows.FontVariants.Ruby> &#124; <xref:System.Windows.FontVariants.Subscript> &#124; <xref:System.Windows.FontVariants.Superscript></span></span>|<xref:System.Windows.FontVariants.Normal?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="82419-316">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82419-316">See also</span></span>
- <xref:System.Windows.Documents.Typography>
- [<span data-ttu-id="82419-317">OpenType 規格</span><span class="sxs-lookup"><span data-stu-id="82419-317">OpenType Specification</span></span>](https://go.microsoft.com/fwlink/?LinkId=96731)
- [<span data-ttu-id="82419-318">WPF 中的印刷樣式</span><span class="sxs-lookup"><span data-stu-id="82419-318">Typography in WPF</span></span>](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)
- [<span data-ttu-id="82419-319">範例 OpenType 字型套件</span><span class="sxs-lookup"><span data-stu-id="82419-319">Sample OpenType Font Pack</span></span>](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)
- [<span data-ttu-id="82419-320">將字型與應用程式一起封裝</span><span class="sxs-lookup"><span data-stu-id="82419-320">Packaging Fonts with Applications</span></span>](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md)
