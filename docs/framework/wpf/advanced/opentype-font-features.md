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
ms.openlocfilehash: 3f1f0698afce6e64711e37ac60d0662d65bbee6b
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016132"
---
# <a name="opentype-font-features"></a><span data-ttu-id="ebeb5-102">OpenType 字型功能</span><span class="sxs-lookup"><span data-stu-id="ebeb5-102">OpenType Font Features</span></span>

<span data-ttu-id="ebeb5-103">本主題提供中[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]OpenType 字型技術的部分主要功能總覽。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-103">This topic provides an overview of some of the key features of OpenType font technology in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
<a name="overview"></a>   
## <a name="opentype-font-format"></a><span data-ttu-id="ebeb5-104">OpenType 字型格式</span><span class="sxs-lookup"><span data-stu-id="ebeb5-104">OpenType Font Format</span></span>  
 <span data-ttu-id="ebeb5-105">OpenType 字型格式是[!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)]字型格式的延伸模組, 加入 PostScript 字型資料的支援。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-105">The OpenType font format is an extension of the [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] font format, adding support for PostScript font data.</span></span> <span data-ttu-id="ebeb5-106">OpenType 字型格式是由 Microsoft 和 Adobe Corporation 共同開發。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-106">The OpenType font format was developed jointly by Microsoft and Adobe Corporation.</span></span> <span data-ttu-id="ebeb5-107">Opentype 字型和支援 OpenType 字型的作業系統服務, 可讓使用者使用簡單的方式來安裝和使用字型, 無論字型包含[!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)]外框或 CFF (PostScript) 外框。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-107">OpenType fonts and the operating system services which support OpenType fonts provide users with a simple way to install and use fonts, whether the fonts contain [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] outlines or CFF (PostScript) outlines.</span></span>  
  
 <span data-ttu-id="ebeb5-108">OpenType 字型格式解決下列開發人員的挑戰:</span><span class="sxs-lookup"><span data-stu-id="ebeb5-108">The OpenType font format addresses the following developer challenges:</span></span>  
  
- <span data-ttu-id="ebeb5-109">更廣泛的多平台支援。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-109">Broader multi-platform support.</span></span>  
  
- <span data-ttu-id="ebeb5-110">更好的國際字元集支援。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-110">Better support for international character sets.</span></span>  
  
- <span data-ttu-id="ebeb5-111">更好的字型資料保護。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-111">Better protection for font data.</span></span>  
  
- <span data-ttu-id="ebeb5-112">較小的檔案大小，讓字型發佈更有效率。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-112">Smaller file sizes to make font distribution more efficient.</span></span>  
  
- <span data-ttu-id="ebeb5-113">進階印刷樣式控制項的廣泛支援。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-113">Broader support for advanced typographic control.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ebeb5-114">Windows SDK 包含一組您可以搭配[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式使用的範例 OpenType 字型。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-114">The Windows SDK contains a set of sample OpenType fonts that you can use with [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications.</span></span> <span data-ttu-id="ebeb5-115">本主題後文會說明這些字型提供的大部分功能。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-115">These fonts provide most of the features illustrated in the rest of this topic.</span></span> <span data-ttu-id="ebeb5-116">如需詳細資訊，請參閱[範例 OpenType 字型套件](sample-opentype-font-pack.md)。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-116">For more information, see [Sample OpenType Font Pack](sample-opentype-font-pack.md).</span></span>  
  
 <span data-ttu-id="ebeb5-117">如需 OpenType 字型格式的詳細資訊, 請參閱[Opentype 規格](https://go.microsoft.com/fwlink/?LinkId=96731)。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-117">See the [OpenType Specification](https://go.microsoft.com/fwlink/?LinkId=96731) for details of the OpenType font format.</span></span>  
  
### <a name="advanced-typographic-extensions"></a><span data-ttu-id="ebeb5-118">進階的印刷樣式延伸模組</span><span class="sxs-lookup"><span data-stu-id="ebeb5-118">Advanced Typographic Extensions</span></span>  
 <span data-ttu-id="ebeb5-119">「先進的印刷樣式表」 (OpenType 版面配置資料表) 使用[!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)]或 CFF 外框來擴充字型的功能。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-119">The Advanced Typographic tables (OpenType Layout tables) extend the functionality of fonts with either [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] or CFF outlines.</span></span> <span data-ttu-id="ebeb5-120">OpenType 版面配置字型包含額外的資訊, 可延伸字型的功能, 以支援高品質的國際印刷樣式。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-120">OpenType Layout fonts contain additional information that extends the capabilities of the fonts to support high-quality international typography.</span></span> <span data-ttu-id="ebeb5-121">大部分的 OpenType 字型只會公開可用的全部 OpenType 功能子集。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-121">Most OpenType fonts expose only a subset of the total OpenType features available.</span></span> <span data-ttu-id="ebeb5-122">OpenType 字型提供下列功能。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-122">OpenType fonts provide the following features.</span></span>  
  
- <span data-ttu-id="ebeb5-123">字元與字符之間的豐富對應，支援連音符號、位置形式、替代項目，以及其他字型替代項目。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-123">Rich mapping between characters and glyphs that support ligatures, positional forms, alternates, and other font substitutions.</span></span>  
  
- <span data-ttu-id="ebeb5-124">支援二維定位與字符附件。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-124">Support for two-dimensional positioning and glyph attachment.</span></span>  
  
- <span data-ttu-id="ebeb5-125">字型中包含明確的指令碼和語言資訊，因此文字處理應用程式可據以調整其行為。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-125">Explicit script and language information contained in font, so a text-processing application can adjust its behavior accordingly.</span></span>  
  
 <span data-ttu-id="ebeb5-126">Opentype 版面配置資料表的詳細說明請參閱 OpenType 規格的「[字型檔案資料表](https://www.microsoft.com/typography/otspec/otff.htm)」一節。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-126">The OpenType Layout tables are described in more detail in the ["Font File Tables"](https://www.microsoft.com/typography/otspec/otff.htm) section of the OpenType specification.</span></span>  
  
 <span data-ttu-id="ebeb5-127">本總覽的其餘部分將介紹由<xref:System.Windows.Documents.Typography>物件的屬性所公開的一些視覺上有趣的 OpenType 功能的廣度和彈性。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-127">The remainder of this overview introduces the breadth and flexibility of some of the visually-interesting OpenType features that are exposed by the properties of the <xref:System.Windows.Documents.Typography> object.</span></span> <span data-ttu-id="ebeb5-128">如需此物件的詳細資訊，請參閱[印刷樣式類別](#typography_class)。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-128">For more information on this object, see [Typography Class](#typography_class).</span></span>  
  
<a name="variants"></a>   
## <a name="variants"></a><span data-ttu-id="ebeb5-129">變異</span><span class="sxs-lookup"><span data-stu-id="ebeb5-129">Variants</span></span>  
 <span data-ttu-id="ebeb5-130">用來轉譯不同印刷樣式的變數，例如上標和下標。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-130">Variants are used to render different typographic styles, such as superscripts and subscripts.</span></span>  
  
### <a name="superscripts-and-subscripts"></a><span data-ttu-id="ebeb5-131">上標和下標</span><span class="sxs-lookup"><span data-stu-id="ebeb5-131">Superscripts and Subscripts</span></span>  
 <span data-ttu-id="ebeb5-132"><xref:System.Windows.Documents.Typography.Variants%2A>屬性可讓您設定 OpenType 字型的上標和下標值。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-132">The <xref:System.Windows.Documents.Typography.Variants%2A> property allows you to set superscript and subscript values for an OpenType font.</span></span>  
  
 <span data-ttu-id="ebeb5-133">下列文字顯示上標 Palatino Linotype 字型。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-133">The following text displays superscripts for the Palatino Linotype font.</span></span>  
  
 <span data-ttu-id="ebeb5-134">![使用 OpenType 上標的文字](./media/opentype-font-features/opentype-superscripts.gif "使用 OpenType 上標的文字")</span><span class="sxs-lookup"><span data-stu-id="ebeb5-134">![Text using OpenType superscripts](./media/opentype-font-features/opentype-superscripts.gif "Text using OpenType superscripts")</span></span>  
  
 <span data-ttu-id="ebeb5-135">下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 為 Palatino Linotype 字型定義上標。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-135">The following markup example shows how to define superscripts for the Palatino Linotype font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 <span data-ttu-id="ebeb5-136">下列文字顯示下標 Palatino Linotype 字型。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-136">The following text displays subscripts for the Palatino Linotype font.</span></span>  
  
 <span data-ttu-id="ebeb5-137">![使用 OpenType]注標的文字(./media/opentype-font-features/opentype-subscripts.gif "使用 OpenType")注標的文字</span><span class="sxs-lookup"><span data-stu-id="ebeb5-137">![Text using OpenType subscripts](./media/opentype-font-features/opentype-subscripts.gif "Text using OpenType subscripts")</span></span>  
  
 <span data-ttu-id="ebeb5-138">下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 定義 Palatino Linotype 字型的注標。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-138">The following markup example shows how to define subscripts for the Palatino Linotype font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a><span data-ttu-id="ebeb5-139">上標和下標的裝飾性用途</span><span class="sxs-lookup"><span data-stu-id="ebeb5-139">Decorative Uses of Superscripts and Subscripts</span></span>  
 <span data-ttu-id="ebeb5-140">您也可以使用上標和下標建立混合大小寫文字的裝飾效果。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-140">You can also use superscripts and subscripts to create decorative effects of mixed case text.</span></span> <span data-ttu-id="ebeb5-141">下列文字顯示 Palatino Linotype 字型的上下標文字。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-141">The following text displays superscript and subscript text for the Palatino Linotype font.</span></span> <span data-ttu-id="ebeb5-142">請注意，大寫字不受影響。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-142">Note that the capitals are not affected.</span></span>  
  
 <span data-ttu-id="ebeb5-143">![使用 OpenType 上標和下標的文字](./media/opentype-font-features/opentype-superscripts-subscripts.gif "使用 OpenType 上標和下標的文字")</span><span class="sxs-lookup"><span data-stu-id="ebeb5-143">![Text using OpenType superscripts and subscripts](./media/opentype-font-features/opentype-superscripts-subscripts.gif "Text using OpenType superscripts and subscripts")</span></span>  

 <span data-ttu-id="ebeb5-144">下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 為字型定義上標和下標。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-144">The following markup example shows how to define superscripts and subscripts for a font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>   
## <a name="capitals"></a><span data-ttu-id="ebeb5-145">大寫字</span><span class="sxs-lookup"><span data-stu-id="ebeb5-145">Capitals</span></span>  
 <span data-ttu-id="ebeb5-146">大寫字是一組以大寫樣式字符轉譯文字的印刷格式。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-146">Capitals are a set of typographical forms that render text in capital-styled glyphs.</span></span> <span data-ttu-id="ebeb5-147">一般而言，當文字全部轉譯為大寫時，字母之間的間距可能太近，字母的加權和比例會過重。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-147">Typically, when text is rendered as all capitals, the spacing between letters can appear too tight, and the weight and proportion of the letters too heavy.</span></span> <span data-ttu-id="ebeb5-148">OpenType 支援數個大寫字母的樣式設定格式, 包括 small 大寫字母、特小大大寫字母、標題和大寫字母間距。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-148">OpenType supports a number of styling formats for capitals, including small capitals, petite capitals, titling, and capital spacing.</span></span> <span data-ttu-id="ebeb5-149">這些樣式格式可讓您控制大寫字的外觀。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-149">These styling formats allow you to control the appearance of capitals.</span></span>  
  
 <span data-ttu-id="ebeb5-150">下列文字顯示 Pescadero 字型的標準大寫字母，後面接著樣式設定為 "SmallCaps" 和 "AllSmallCaps" 的字母。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-150">The following text displays standard capital letters for the Pescadero font, followed by the letters styled as "SmallCaps" and "AllSmallCaps".</span></span> <span data-ttu-id="ebeb5-151">在此情況下，三個單字全都使用相同的字型大小。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-151">In this case, the same font size is used for all three words.</span></span>  
  
 <span data-ttu-id="ebeb5-152">![使用 OpenType 大寫的文字](./media/opentype-font-features/opentype-capitals.gif "使用 OpenType 大寫的文字")</span><span class="sxs-lookup"><span data-stu-id="ebeb5-152">![Text using OpenType capitals](./media/opentype-font-features/opentype-capitals.gif "Text using OpenType capitals")</span></span>  
  
 <span data-ttu-id="ebeb5-153">下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 定義 Pescadero 字型的大寫字母。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-153">The following markup example shows how to define capitals for the Pescadero font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span> <span data-ttu-id="ebeb5-154">使用 "SmallCaps" 格式時會略過任何開頭的大寫字母。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-154">When the "SmallCaps" format is used, any leading capital letter is ignored.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a><span data-ttu-id="ebeb5-155">標題大寫字</span><span class="sxs-lookup"><span data-stu-id="ebeb5-155">Titling Capitals</span></span>  
 <span data-ttu-id="ebeb5-156">標題大寫字的加權和比例較輕，設計目的是為了比正常大寫字母看起來更雅緻。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-156">Titling capitals are lighter in weight and proportion and designed to give a more elegant look than normal capitals.</span></span> <span data-ttu-id="ebeb5-157">標題大寫字通常用於較大的字型大小作為標題。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-157">Titling capitals are typically used in larger font sizes as headings.</span></span> <span data-ttu-id="ebeb5-158">下列文字顯示 Pescadero 字型的正常和標題大寫字。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-158">The following text displays normal and titling capitals for the Pescadero font.</span></span> <span data-ttu-id="ebeb5-159">請注意第二行文字較窄的主體寬度。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-159">Notice the narrower stem widths of the text on the second line.</span></span>  
  
 <span data-ttu-id="ebeb5-160">![使用 OpenType 標題大寫的文字](./media/opentype-font-features/opentype-titling-capitals.gif "使用 OpenType 標題大寫的文字")</span><span class="sxs-lookup"><span data-stu-id="ebeb5-160">![Text using OpenType titling capitals](./media/opentype-font-features/opentype-titling-capitals.gif "Text using OpenType titling capitals")</span></span>  
  
 <span data-ttu-id="ebeb5-161">下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 定義 Pescadero 字型的標題大寫。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-161">The following markup example shows how to define titling capitals for the Pescadero font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet17](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a><span data-ttu-id="ebeb5-162">大寫字母間距</span><span class="sxs-lookup"><span data-stu-id="ebeb5-162">Capital Spacing</span></span>  
 <span data-ttu-id="ebeb5-163">大寫字母間距功能可讓您在全部使用大寫字的文字中，提供更多的間距。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-163">Capital spacing is a feature that allows you to provide more spacing when using all capitals in text.</span></span> <span data-ttu-id="ebeb5-164">大寫字母通常會設計為與小寫字母混合在一起。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-164">Capital letters are typically designed to blend with lowercase letters.</span></span> <span data-ttu-id="ebeb5-165">大寫字母和小寫字母間看起來很不錯的間距，在全部使用大寫字母時會看起來很擠。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-165">Spacing that appears attractive between and a capital letter and a lowercase letter may look too tight when all capital letters are used.</span></span> <span data-ttu-id="ebeb5-166">下列文字顯示 Pescadero 字型的正常和大寫字間距。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-166">The following text displays normal and capital spacing for the Pescadero font.</span></span>  
  
 <span data-ttu-id="ebeb5-167">![使用 OpenType 大寫間距的文字](./media/opentype-font-features/opentype-capital-spacing.gif "使用 OpenType 大寫間距的文字")</span><span class="sxs-lookup"><span data-stu-id="ebeb5-167">![Text using OpenType capital spacing](./media/opentype-font-features/opentype-capital-spacing.gif "Text using OpenType capital spacing ")</span></span>  
 
 <span data-ttu-id="ebeb5-168">下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 定義 Pescadero 字型的大寫字母間距。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-168">The following markup example shows how to define capital spacing for the Pescadero font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet18](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>   
## <a name="ligatures"></a><span data-ttu-id="ebeb5-169">連音符號</span><span class="sxs-lookup"><span data-stu-id="ebeb5-169">Ligatures</span></span>  
 <span data-ttu-id="ebeb5-170">連音符號是兩個或以上的字符，形成單一字符以建立更清晰或更美觀的文字。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-170">Ligatures are two or more glyphs that are formed into a single glyph in order to create more readable or attractive text.</span></span> <span data-ttu-id="ebeb5-171">OpenType 字型支援四種類型的連字:</span><span class="sxs-lookup"><span data-stu-id="ebeb5-171">OpenType fonts support four types of ligatures:</span></span>  
  
- <span data-ttu-id="ebeb5-172">**標準連音符號**。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-172">**Standard ligatures**.</span></span> <span data-ttu-id="ebeb5-173">設計目的旨在增進可讀性。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-173">Designed to enhance readability.</span></span> <span data-ttu-id="ebeb5-174">標準連音符號包括 "fi"、"fl" 和 "ff"。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-174">Standard ligatures include "fi", "fl", and "ff".</span></span>  
  
- <span data-ttu-id="ebeb5-175">**內容連音符號**。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-175">**Contextual ligatures**.</span></span> <span data-ttu-id="ebeb5-176">設計目的旨在提供組成連音符號的字元間更好的聯結行為，以提升可讀性。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-176">Designed to enhance readability by providing better joining behavior between the characters that make up the ligature.</span></span>  
  
- <span data-ttu-id="ebeb5-177">**Discretionary 連音符號**。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-177">**Discretionary ligatures**.</span></span> <span data-ttu-id="ebeb5-178">設計成裝飾之用，並不是特別針對可讀性設計。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-178">Designed to be ornamental, and not specifically designed for readability.</span></span>  
  
- <span data-ttu-id="ebeb5-179">**過往連音符號**。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-179">**Historical ligatures**.</span></span> <span data-ttu-id="ebeb5-180">設計成記錄之用，並不是特別針對可讀性所設計。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-180">Designed to be historical, and not specifically designed for readability.</span></span>  
  
 <span data-ttu-id="ebeb5-181">下列文字顯示 Pericles 字型的標準連音符號字符。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-181">The following text displays standard ligature glyphs for the Pericles font.</span></span>  
  
 <span data-ttu-id="ebeb5-182">![使用 OpenType 標準連字的文字](./media/opentype-font-features/opentype-standard-ligatures.gif "使用 OpenType 標準連字的文字")</span><span class="sxs-lookup"><span data-stu-id="ebeb5-182">![Text using OpenType standard ligatures](./media/opentype-font-features/opentype-standard-ligatures.gif "Text using OpenType standard ligatures")</span></span>  
  
 <span data-ttu-id="ebeb5-183">下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 為 Pericles 字型定義標準的連字號圖像。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-183">The following markup example shows how to define standard ligature glyphs for the Pericles font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 <span data-ttu-id="ebeb5-184">下列文字顯示 Pericles 字型 Discretionary 連音符號。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-184">The following text displays discretionary ligature glyphs for the Pericles font.</span></span>  
  
 <span data-ttu-id="ebeb5-185">![使用 OpenType 任意連字的文字](./media/opentype-font-features/opentype-discretionary-ligatures.gif "使用 OpenType 任意連字的文字")</span><span class="sxs-lookup"><span data-stu-id="ebeb5-185">![Text using OpenType discretionary ligatures](./media/opentype-font-features/opentype-discretionary-ligatures.gif "Text using OpenType discretionary ligatures")</span></span>  
  
 <span data-ttu-id="ebeb5-186">下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 為 Pericles 字型定義任意的連字號圖像。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-186">The following markup example shows how to define discretionary ligature glyphs for the Pericles font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 <span data-ttu-id="ebeb5-187">根據預設, 中[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]的 OpenType 字型會啟用標準連字。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-187">By default, OpenType fonts in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] enable standard ligatures.</span></span> <span data-ttu-id="ebeb5-188">例如，如果您使用 Palatino Linotype 字型，標準連音符號 "fi"、"ff" 和 "fl" 會顯示為合併的字元字符。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-188">For example, if you use the Palatino Linotype font, the standard ligatures "fi", "ff", and "fl" appear as a combined character glyph.</span></span> <span data-ttu-id="ebeb5-189">請注意，每個標準連音符號的成對字元都彼此相鄰。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-189">Notice that the pair of characters for each standard ligature touch each other.</span></span>  
  
 <span data-ttu-id="ebeb5-190">搭配![Palatino Linotype 使用 OpenType 標準連字的文字]搭配(./media/opentype-font-features/opentype-standard-ligatures-palatino.gif "Palatino Linotype 使用 OpenType 標準連字的文字")</span><span class="sxs-lookup"><span data-stu-id="ebeb5-190">![Text using OpenType standard ligatures with Palatino Linotype](./media/opentype-font-features/opentype-standard-ligatures-palatino.gif "Text using OpenType standard ligatures with Palatino Linotype")</span></span>    
   
 <span data-ttu-id="ebeb5-191">不過，您可以停用標準連音符號功能，讓 "ff" 等標準連音符號顯示為兩個分開的字符，而不是合併的字元字符。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-191">However, you can disable standard ligature features so that a standard ligature such as "ff" displays as two separate glyphs, rather than as a combined character glyph.</span></span>  
  
 <span data-ttu-id="ebeb5-192">![使用已停用之 OpenType 標準連字的文字](./media/opentype-font-features/disabled-opentype-standard-ligatures.gif "使用已停用之 OpenType 標準連字的文字")</span><span class="sxs-lookup"><span data-stu-id="ebeb5-192">![Text using disabled OpenType standard ligatures](./media/opentype-font-features/disabled-opentype-standard-ligatures.gif "Text using disabled OpenType standard ligatures")</span></span>  
    
 <span data-ttu-id="ebeb5-193">下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 停用 Palatino Linotype 字型的標準連字號符號。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-193">The following markup example shows how to disable standard ligature glyphs for the Palatino Linotype font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>   
## <a name="swashes"></a><span data-ttu-id="ebeb5-194">花飾字</span><span class="sxs-lookup"><span data-stu-id="ebeb5-194">Swashes</span></span>  
 <span data-ttu-id="ebeb5-195">花飾字是裝飾性字符，使用精心設計且通常與書寫體相關聯的裝飾。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-195">Swashes are decorative glyphs that use elaborate ornamentation often associated with calligraphy.</span></span> <span data-ttu-id="ebeb5-196">下列文字顯示 Pescadero 字型的標準和花飾字字符。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-196">The following text displays standard and swash glyphs for the Pescadero font.</span></span>  
  
 <span data-ttu-id="ebeb5-197">![使用 OpenType 標準和花飾字字元的文字](./media/opentype-font-features/opentype-standard-swash-glyphs.gif "使用 OpenType 標準和花飾字字元的文字")</span><span class="sxs-lookup"><span data-stu-id="ebeb5-197">![Text using OpenType standard and swash glyphs](./media/opentype-font-features/opentype-standard-swash-glyphs.gif "Text using OpenType standard and swash glyphs")</span></span>  

 <span data-ttu-id="ebeb5-198">花飾字通常用為簡短片語中的裝飾項目，例如事件宣告。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-198">Swashes are often used as decorative elements in short phrases such as event announcements.</span></span> <span data-ttu-id="ebeb5-199">下列文字使用花飾字強調大寫字母的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-199">The following text uses swashes to emphasize the capital letters of the name of the event.</span></span>  
  
 <span data-ttu-id="ebeb5-200">![使用 OpenType 花飾字的文字](./media/opentype-font-features/opentype-swashes.gif "使用 OpenType 花飾字的文字")</span><span class="sxs-lookup"><span data-stu-id="ebeb5-200">![Text using OpenType swashes](./media/opentype-font-features/opentype-swashes.gif "Text using OpenType swashes")</span></span>  
  
 <span data-ttu-id="ebeb5-201">下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 為字型定義花飾字。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-201">The following markup example shows how to define swashes for a font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a><span data-ttu-id="ebeb5-202">內容花飾字</span><span class="sxs-lookup"><span data-stu-id="ebeb5-202">Contextual Swashes</span></span>  
 <span data-ttu-id="ebeb5-203">某些花飾字字符的組合會導致不討喜的外觀，例如相鄰字母的伸尾部分重疊。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-203">Certain combinations of swash glyphs can cause an unattractive appearance, such as overlapping descenders on adjacent letters.</span></span> <span data-ttu-id="ebeb5-204">使用內容花飾字可讓您使用會產生更佳外觀的替代花飾字字符。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-204">Using a contextual swash allows you to use a substitute swash glyph that produces a better appearance.</span></span> <span data-ttu-id="ebeb5-205">下列文字顯示套用內容花飾字之前和之後的相同字組。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-205">The following text shows the same word before and after a contextual swash is applied.</span></span>  
  
 <span data-ttu-id="ebeb5-206">![使用 OpenType 內容花飾字的文字](./media/opentype-font-features/opentype-contextual-swashes.gif "使用 OpenType 內容花飾字的文字")</span><span class="sxs-lookup"><span data-stu-id="ebeb5-206">![Text using OpenType contextual swashes](./media/opentype-font-features/opentype-contextual-swashes.gif "Text using OpenType contextual swashes")</span></span>  
  
 <span data-ttu-id="ebeb5-207">下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 定義 Pescadero 字型的內容花飾字。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-207">The following markup example shows how to define a contextual swash for the Pescadero font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet16](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>   
## <a name="alternates"></a><span data-ttu-id="ebeb5-208">替代項目</span><span class="sxs-lookup"><span data-stu-id="ebeb5-208">Alternates</span></span>  
 <span data-ttu-id="ebeb5-209">替代項目是可以取代標準字符的字符。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-209">Alternates are glyphs that can be substituted for a standard glyph.</span></span> <span data-ttu-id="ebeb5-210">OpenType 字型 (例如下列範例中使用的 Pericles 字型) 可以包含替代字元, 您可以用來建立不同的文字外觀。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-210">OpenType fonts, such as the Pericles font used in the following examples, can contain alternate glyphs that you can use to create different appearances for text.</span></span> <span data-ttu-id="ebeb5-211">下列文字顯示 Pericles 字型的標準字符。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-211">The following text displays standard glyphs for the Pericles font.</span></span>  
  
 <span data-ttu-id="ebeb5-212">![使用 OpenType 標準字元的文字](./media/opentype-font-features/opentype-standard-glyphs.gif "使用 OpenType 標準字元的文字")</span><span class="sxs-lookup"><span data-stu-id="ebeb5-212">![Text using OpenType standard glyphs](./media/opentype-font-features/opentype-standard-glyphs.gif "Text using OpenType standard glyphs")</span></span>  

 <span data-ttu-id="ebeb5-213">Pericles OpenType 字型包含額外的圖像, 可為標準的圖像集提供樣式替代。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-213">The Pericles OpenType font contains additional glyphs that provide stylistic alternates to the standard set of glyphs.</span></span> <span data-ttu-id="ebeb5-214">下列文字顯示文體替代字符。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-214">The following text displays stylistic alternate glyphs.</span></span>  
  
 <span data-ttu-id="ebeb5-215">![使用 OpenType 樣式替代字元的文字](./media/opentype-font-features/opentype-stylistic-alternate-glyphs.gif "使用 OpenType 樣式替代字元的文字")</span><span class="sxs-lookup"><span data-stu-id="ebeb5-215">![Text using OpenType stylistic alternate glyphs](./media/opentype-font-features/opentype-stylistic-alternate-glyphs.gif "Text using OpenType stylistic alternate glyphs")</span></span>  
  
 <span data-ttu-id="ebeb5-216">下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 定義 Pericles 字型的樣式替代字元。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-216">The following markup example shows how to define stylistic alternate glyphs for the Pericles font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 <span data-ttu-id="ebeb5-217">下列文字顯示數個 Pericles 字型的其他文體替代字符。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-217">The following text displays several other stylistic alternate glyphs for the Pericles font.</span></span>  
  
 <span data-ttu-id="ebeb5-218">![針對 Pericles 字型使用 OpenType 樣式替代字元的文字](./media/opentype-font-features/opentype-stylistic-alternate-glyphs-pericles.gif "針對 Pericles 字型使用 OpenType 樣式替代字元的文字")</span><span class="sxs-lookup"><span data-stu-id="ebeb5-218">![Text using OpenType stylistic alternate glyphs  for the Pericles font](./media/opentype-font-features/opentype-stylistic-alternate-glyphs-pericles.gif "Text using OpenType stylistic alternate glyphs  for the Pericles font")</span></span>

 <span data-ttu-id="ebeb5-219">下列標記範例示範如何定義這些其他文體替代字符。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-219">The following markup example shows how to define these other stylistic alternate glyphs.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a><span data-ttu-id="ebeb5-220">隨機內容替代項目</span><span class="sxs-lookup"><span data-stu-id="ebeb5-220">Random Contextual Alternates</span></span>  
 <span data-ttu-id="ebeb5-221">隨機內容替代項目提供單一字元的多個替代字符。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-221">Random contextual alternates provide multiple substitute glyphs for a single character.</span></span> <span data-ttu-id="ebeb5-222">以書寫體字型實作時，這項功能可以使用一組隨機選擇的字符，在外觀上略加變動來模擬手寫。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-222">When implemented with script-type fonts, this feature can simulate handwriting by using of a set of randomly chosen glyphs with slight differences in appearance.</span></span> <span data-ttu-id="ebeb5-223">下列文字使用 Lindsey 字型的隨機內容替代項目。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-223">The following text uses random contextual alternates for the Lindsey font.</span></span> <span data-ttu-id="ebeb5-224">請注意，字母 "a" 的外觀略有不同。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-224">Notice that the letter "a" varies slightly in appearance</span></span>  
  
 <span data-ttu-id="ebeb5-225">![使用 OpenType 隨機內容替代的文字](./media/opentype-font-features/opentype-random-contextual-alternates.gif "使用 OpenType 隨機內容替代的文字")</span><span class="sxs-lookup"><span data-stu-id="ebeb5-225">![Text using OpenType random contextual alternates](./media/opentype-font-features/opentype-random-contextual-alternates.gif "Text using OpenType random contextual alternates")</span></span>  
  
 <span data-ttu-id="ebeb5-226">下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 為 Lindsey 字型定義隨機內容的替代項。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-226">The following markup example shows how to define random contextual alternates for the Lindsey font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet20](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a><span data-ttu-id="ebeb5-227">古體形式</span><span class="sxs-lookup"><span data-stu-id="ebeb5-227">Historical Forms</span></span>  
 <span data-ttu-id="ebeb5-228">古體形式是過去常用的印刷樣式慣例。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-228">Historical forms are typographic conventions that were common in the past.</span></span> <span data-ttu-id="ebeb5-229">下列文字使用 Palatino Linotype 字型的古體形式字符顯示 "Boston, Massachusetts" 片語。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-229">The following text displays the phrase, "Boston, Massachusetts", using an historical form of glyphs for the Palatino Linotype font.</span></span>  
  
 <span data-ttu-id="ebeb5-230">![使用 OpenType 歷程記錄表單的文字](./media/opentype-font-features/opentype-historical-forms.gif "使用 OpenType 歷程記錄表單的文字")</span><span class="sxs-lookup"><span data-stu-id="ebeb5-230">![Text using OpenType historical forms](./media/opentype-font-features/opentype-historical-forms.gif "Text using OpenType historical forms")</span></span>  
   
 <span data-ttu-id="ebeb5-231">下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 定義 Palatino Linotype 字型的歷程記錄表單。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-231">The following markup example shows how to define historical forms for the Palatino Linotype font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>   
## <a name="numerical-styles"></a><span data-ttu-id="ebeb5-232">數字的樣式</span><span class="sxs-lookup"><span data-stu-id="ebeb5-232">Numerical Styles</span></span>  
 <span data-ttu-id="ebeb5-233">OpenType 字型支援大量可搭配文字中數值使用的功能。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-233">OpenType fonts support a large number of features that can be used with numerical values in text.</span></span>  
  
### <a name="fractions"></a><span data-ttu-id="ebeb5-234">分數</span><span class="sxs-lookup"><span data-stu-id="ebeb5-234">Fractions</span></span>  
 <span data-ttu-id="ebeb5-235">OpenType 字型支援分數的樣式, 包括斜線和堆疊。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-235">OpenType fonts support styles for fractions, including slashed and stacked.</span></span>  
  
 <span data-ttu-id="ebeb5-236">下列文字顯示 Palatino Linotype 字型的分數樣式。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-236">The following text displays fraction styles for the Palatino Linotype font.</span></span>  
  
 <span data-ttu-id="ebeb5-237">![使用 OpenType 斜線和堆疊分數的文字](./media/opentype-font-features/opentype-slashed-stacked-fractions.gif "使用 OpenType 斜線和堆疊分數的文字")</span><span class="sxs-lookup"><span data-stu-id="ebeb5-237">![Text using OpenType slashed and stacked fractions](./media/opentype-font-features/opentype-slashed-stacked-fractions.gif "Text using OpenType slashed and stacked fractions")</span></span>  
   
 <span data-ttu-id="ebeb5-238">下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 定義 Palatino Linotype 字型的分數樣式。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-238">The following markup example shows how to define fraction styles for the Palatino Linotype font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a><span data-ttu-id="ebeb5-239">舊樣式數字</span><span class="sxs-lookup"><span data-stu-id="ebeb5-239">Old Style Numerals</span></span>  
 <span data-ttu-id="ebeb5-240">OpenType 字型支援舊的樣式數位格式。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-240">OpenType fonts support an old style numeral format.</span></span> <span data-ttu-id="ebeb5-241">此格式適用於顯示樣式不再標準的數字。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-241">This format is useful for displaying numerals in styles that are no longer standard.</span></span> <span data-ttu-id="ebeb5-242">下列文字使用 Palatino Linotype 字型的標準和舊樣式數字格式顯示 18 世紀的日期。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-242">The following text displays an 18th century date in standard and old style numeral formats for the Palatino Linotype font.</span></span>  
  
 <span data-ttu-id="ebeb5-243">![使用 OpenType 舊樣式數位的文字](./media/opentype-font-features/opentype-old-style-numerals.gif "使用 OpenType 舊樣式數位的文字")</span><span class="sxs-lookup"><span data-stu-id="ebeb5-243">![Text using OpenType old style numerals](./media/opentype-font-features/opentype-old-style-numerals.gif "Text using OpenType old style numerals")</span></span>  
    
 <span data-ttu-id="ebeb5-244">下列文字顯示 Palatino Linotype 字型的標準數字，後面接著舊樣式數字的數字。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-244">The following text displays standard numerals for the Palatino Linotype font, followed by old style numerals.</span></span>  
  
 <span data-ttu-id="ebeb5-245">![使用 OpenType 舊樣式數位集的文字](./media/opentype-font-features/opentype-old-style-numeral-sets.gif "使用 OpenType 舊樣式數位集的文字")</span><span class="sxs-lookup"><span data-stu-id="ebeb5-245">![Text using OpenType old style numeral sets](./media/opentype-font-features/opentype-old-style-numeral-sets.gif "Text using OpenType old style numeral sets")</span></span>  
  
 <span data-ttu-id="ebeb5-246">下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 為 Palatino Linotype 字型定義舊的樣式數位。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-246">The following markup example shows how to define old style numerals for the Palatino Linotype font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a><span data-ttu-id="ebeb5-247">調和間距與表格式數字</span><span class="sxs-lookup"><span data-stu-id="ebeb5-247">Proportional and Tabular Figures</span></span>  
 <span data-ttu-id="ebeb5-248">OpenType 字型支援以比例和表格式圖表功能, 在使用數位時控制寬度的對齊方式。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-248">OpenType fonts support a proportional and tabular figure feature to control the alignment of widths when using numerals.</span></span> <span data-ttu-id="ebeb5-249">調和間距數字會將每一個數字視為具有不同的寬度，"1" 比 "5" 窄。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-249">Proportional figures treat each numeral as having a different width—"1" is narrower than "5".</span></span> <span data-ttu-id="ebeb5-250">表格式數字則視為等寬數字，以便垂直對齊，可提高財務類資訊的可讀性。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-250">Tabular figures are treated as equal-width numerals so that they align vertically, which increases the readability of financial type information.</span></span>  
  
 <span data-ttu-id="ebeb5-251">下列文字在第一個資料行中顯示使用 Miramonte 字型的兩個調和間距數字。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-251">The following text displays two proportional figures in the first column using the Miramonte font.</span></span> <span data-ttu-id="ebeb5-252">請注意數字 "5" 和 "1" 之間的寬度差異。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-252">Note the difference in width between the numerals "5" and "1".</span></span> <span data-ttu-id="ebeb5-253">第二個資料行顯示相同的兩個數值，使用表格式數字功能調整其寬度。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-253">The second column shows the same two numeric values with the widths adjusted by using the tabular figure feature.</span></span>  
  
 <span data-ttu-id="ebeb5-254">![使用 OpenType 比例 & 表格式數位的文字](./media/opentype-font-features/opentype-proportional-tabular-figures.gif "使用 OpenType 比例和表格式數位的文字")</span><span class="sxs-lookup"><span data-stu-id="ebeb5-254">![Text using OpenType proportional & tabular figures](./media/opentype-font-features/opentype-proportional-tabular-figures.gif "Text using OpenType proportional and tabular figures")</span></span>  
    
 <span data-ttu-id="ebeb5-255">下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 定義 Miramonte 字型的比例和表格式數位。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-255">The following markup example shows how to define proportional and tabular figures for the Miramonte font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet19](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a><span data-ttu-id="ebeb5-256">加斜線的零</span><span class="sxs-lookup"><span data-stu-id="ebeb5-256">Slashed Zero</span></span>  
 <span data-ttu-id="ebeb5-257">OpenType 字型支援斜線零數位格式, 以強調字母 "O" 與數位 "0" 之間的差異。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-257">OpenType fonts support a slashed zero numeral format to emphasize the difference between the letter "O" and the numeral "0".</span></span> <span data-ttu-id="ebeb5-258">加斜線的零數字通常用於財務和商務資訊中的識別碼。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-258">The slashed zero numeral is often used for identifiers in financial and business information.</span></span>  
  
 <span data-ttu-id="ebeb5-259">下列文字顯示使用 Miramonte 字型的範例訂單識別碼。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-259">The following text displays a sample order identifier using the Miramonte font.</span></span> <span data-ttu-id="ebeb5-260">第一行使用標準的數字。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-260">The first line uses standard numerals.</span></span> <span data-ttu-id="ebeb5-261">第二行使用加斜線的零數字，以突顯與大寫字母 "O" 的對比。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-261">The second line used slashed zero numerals to provide better contrast with the uppercase "O" letter.</span></span>  
  
 <span data-ttu-id="ebeb5-262">![使用 OpenType 斜線零數位的文字](./media/opentype-font-features/opentype-slashed-zero-numerals.gif "使用 OpenType 斜線零數位的文字")</span><span class="sxs-lookup"><span data-stu-id="ebeb5-262">![Text using OpenType slashed zero numerals](./media/opentype-font-features/opentype-slashed-zero-numerals.gif "Text using OpenType slashed zero numerals")</span></span>  
    
 <span data-ttu-id="ebeb5-263">下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 為 Miramonte 字型定義以斜線為零的數位。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-263">The following markup example shows how to define slashed zero numerals for the Miramonte font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>   
## <a name="typography-class"></a><span data-ttu-id="ebeb5-264">印刷樣式類別</span><span class="sxs-lookup"><span data-stu-id="ebeb5-264">Typography Class</span></span>  
 <span data-ttu-id="ebeb5-265"><xref:System.Windows.Documents.Typography>物件會公開 OpenType 字型支援的一組功能。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-265">The <xref:System.Windows.Documents.Typography> object exposes the set of features that an OpenType font supports.</span></span> <span data-ttu-id="ebeb5-266">藉由在標記中<xref:System.Windows.Documents.Typography>設定的屬性, 您可以輕鬆地撰寫利用 OpenType 功能的檔。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-266">By setting the properties of <xref:System.Windows.Documents.Typography> in markup, you can easily author documents that take advantage of OpenType features.</span></span>  
  
 <span data-ttu-id="ebeb5-267">下列文字顯示 Pescadero 字型的標準大寫字母，後面接著樣式設定為 "SmallCaps" 和 "AllSmallCaps" 的字母。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-267">The following text displays standard capital letters for the Pescadero font, followed by the letters styled as "SmallCaps" and "AllSmallCaps".</span></span> <span data-ttu-id="ebeb5-268">在此情況下，三個單字全都使用相同的字型大小。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-268">In this case, the same font size is used for all three words.</span></span>  
  
 <span data-ttu-id="ebeb5-269">![使用 OpenType 大寫的文字](./media/opentype-font-features/opentype-capitals.gif "使用 OpenType 大寫的文字")</span><span class="sxs-lookup"><span data-stu-id="ebeb5-269">![Text using OpenType capitals](./media/opentype-font-features/opentype-capitals.gif "Text using OpenType capitals")</span></span>  
    
 <span data-ttu-id="ebeb5-270">下列標記範例示範如何使用<xref:System.Windows.Documents.Typography>物件的屬性, 定義 Pescadero 字型的大寫字母。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-270">The following markup example shows how to define capitals for the Pescadero font, using properties of the <xref:System.Windows.Documents.Typography> object.</span></span> <span data-ttu-id="ebeb5-271">使用 "SmallCaps" 格式時會略過任何開頭的大寫字母。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-271">When the "SmallCaps" format is used, any leading capital letter is ignored.</span></span>  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 <span data-ttu-id="ebeb5-272">下列程式碼範例可以完成與先前標記範例相同的工作。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-272">The following code example accomplishes the same task as the previous markup example.</span></span>  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a><span data-ttu-id="ebeb5-273">印刷樣式類別屬性</span><span class="sxs-lookup"><span data-stu-id="ebeb5-273">Typography Class Properties</span></span>  
 <span data-ttu-id="ebeb5-274">下表列出<xref:System.Windows.Documents.Typography>物件的屬性、值和預設設定。</span><span class="sxs-lookup"><span data-stu-id="ebeb5-274">The following table lists the properties, values, and default settings of the <xref:System.Windows.Documents.Typography> object.</span></span>  
  
|<span data-ttu-id="ebeb5-275">屬性</span><span class="sxs-lookup"><span data-stu-id="ebeb5-275">Property</span></span>|<span data-ttu-id="ebeb5-276">值</span><span class="sxs-lookup"><span data-stu-id="ebeb5-276">Value(s)</span></span>|<span data-ttu-id="ebeb5-277">預設值</span><span class="sxs-lookup"><span data-stu-id="ebeb5-277">Default Value</span></span>|  
|--------------|----------------|-------------------|  
|<xref:System.Windows.Documents.Typography.AnnotationAlternates%2A>|<span data-ttu-id="ebeb5-278">數值 - 位元組</span><span class="sxs-lookup"><span data-stu-id="ebeb5-278">Numeric value - byte</span></span>|<span data-ttu-id="ebeb5-279">0</span><span class="sxs-lookup"><span data-stu-id="ebeb5-279">0</span></span>|  
|<xref:System.Windows.Documents.Typography.Capitals%2A>|<span data-ttu-id="ebeb5-280"><xref:System.Windows.FontCapitals.AllPetiteCaps> &#124; <xref:System.Windows.FontCapitals.AllSmallCaps> &#124; <xref:System.Windows.FontCapitals.Normal> &#124; <xref:System.Windows.FontCapitals.PetiteCaps> &#124; <xref:System.Windows.FontCapitals.SmallCaps> &#124; <xref:System.Windows.FontCapitals.Titling> &#124; <xref:System.Windows.FontCapitals.Unicase></span><span class="sxs-lookup"><span data-stu-id="ebeb5-280"><xref:System.Windows.FontCapitals.AllPetiteCaps> &#124; <xref:System.Windows.FontCapitals.AllSmallCaps> &#124; <xref:System.Windows.FontCapitals.Normal> &#124; <xref:System.Windows.FontCapitals.PetiteCaps> &#124; <xref:System.Windows.FontCapitals.SmallCaps> &#124; <xref:System.Windows.FontCapitals.Titling> &#124; <xref:System.Windows.FontCapitals.Unicase></span></span>|<xref:System.Windows.FontCapitals.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.CapitalSpacing%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.CaseSensitiveForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.ContextualAlternates%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualSwashes%2A>|<span data-ttu-id="ebeb5-281">數值 - 位元組</span><span class="sxs-lookup"><span data-stu-id="ebeb5-281">Numeric value - byte</span></span>|<span data-ttu-id="ebeb5-282">0</span><span class="sxs-lookup"><span data-stu-id="ebeb5-282">0</span></span>|  
|<xref:System.Windows.Documents.Typography.DiscretionaryLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianExpertForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianLanguage%2A>|<span data-ttu-id="ebeb5-283"><xref:System.Windows.FontEastAsianLanguage.HojoKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis04> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis78> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis83> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis90> &#124; <xref:System.Windows.FontEastAsianLanguage.NlcKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Normal> &#124; <xref:System.Windows.FontEastAsianLanguage.Simplified> &#124; <xref:System.Windows.FontEastAsianLanguage.Traditional> &#124; <xref:System.Windows.FontEastAsianLanguage.TraditionalNames></span><span class="sxs-lookup"><span data-stu-id="ebeb5-283"><xref:System.Windows.FontEastAsianLanguage.HojoKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis04> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis78> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis83> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis90> &#124; <xref:System.Windows.FontEastAsianLanguage.NlcKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Normal> &#124; <xref:System.Windows.FontEastAsianLanguage.Simplified> &#124; <xref:System.Windows.FontEastAsianLanguage.Traditional> &#124; <xref:System.Windows.FontEastAsianLanguage.TraditionalNames></span></span>|<xref:System.Windows.FontEastAsianLanguage.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.EastAsianWidths%2A>|<span data-ttu-id="ebeb5-284"><xref:System.Windows.FontEastAsianWidths.Full> &#124; <xref:System.Windows.FontEastAsianWidths.Half> &#124; <xref:System.Windows.FontEastAsianWidths.Normal> &#124; <xref:System.Windows.FontEastAsianWidths.Proportional> &#124; <xref:System.Windows.FontEastAsianWidths.Quarter> &#124; <xref:System.Windows.FontEastAsianWidths.Third></span><span class="sxs-lookup"><span data-stu-id="ebeb5-284"><xref:System.Windows.FontEastAsianWidths.Full> &#124; <xref:System.Windows.FontEastAsianWidths.Half> &#124; <xref:System.Windows.FontEastAsianWidths.Normal> &#124; <xref:System.Windows.FontEastAsianWidths.Proportional> &#124; <xref:System.Windows.FontEastAsianWidths.Quarter> &#124; <xref:System.Windows.FontEastAsianWidths.Third></span></span>|<xref:System.Windows.FontEastAsianWidths.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.Fraction%2A>|<span data-ttu-id="ebeb5-285"><xref:System.Windows.FontFraction.Normal> &#124; <xref:System.Windows.FontFraction.Slashed> &#124; <xref:System.Windows.FontFraction.Stacked></span><span class="sxs-lookup"><span data-stu-id="ebeb5-285"><xref:System.Windows.FontFraction.Normal> &#124; <xref:System.Windows.FontFraction.Slashed> &#124; <xref:System.Windows.FontFraction.Stacked></span></span>|<xref:System.Windows.FontFraction.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.HistoricalForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.HistoricalLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Kerning%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.MathematicalGreek%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.NumeralAlignment%2A>|<span data-ttu-id="ebeb5-286"><xref:System.Windows.FontNumeralAlignment.Normal> &#124; <xref:System.Windows.FontNumeralAlignment.Proportional> &#124; <xref:System.Windows.FontNumeralAlignment.Tabular></span><span class="sxs-lookup"><span data-stu-id="ebeb5-286"><xref:System.Windows.FontNumeralAlignment.Normal> &#124; <xref:System.Windows.FontNumeralAlignment.Proportional> &#124; <xref:System.Windows.FontNumeralAlignment.Tabular></span></span>|<xref:System.Windows.FontNumeralAlignment.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.NumeralStyle%2A>|<xref:System.Boolean>|<xref:System.Windows.FontNumeralStyle.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.SlashedZero%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StandardLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.StandardSwashes%2A>|<span data-ttu-id="ebeb5-287">數值 - 位元組</span><span class="sxs-lookup"><span data-stu-id="ebeb5-287">numeric value – byte</span></span>|<span data-ttu-id="ebeb5-288">0</span><span class="sxs-lookup"><span data-stu-id="ebeb5-288">0</span></span>|  
|<xref:System.Windows.Documents.Typography.StylisticAlternates%2A>|<span data-ttu-id="ebeb5-289">數值 - 位元組</span><span class="sxs-lookup"><span data-stu-id="ebeb5-289">numeric value – byte</span></span>|<span data-ttu-id="ebeb5-290">0</span><span class="sxs-lookup"><span data-stu-id="ebeb5-290">0</span></span>|  
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
|<xref:System.Windows.Documents.Typography.Variants%2A>|<span data-ttu-id="ebeb5-291"><xref:System.Windows.FontVariants.Inferior> &#124; <xref:System.Windows.FontVariants.Normal> &#124; <xref:System.Windows.FontVariants.Ordinal> &#124; <xref:System.Windows.FontVariants.Ruby> &#124; <xref:System.Windows.FontVariants.Subscript> &#124; <xref:System.Windows.FontVariants.Superscript></span><span class="sxs-lookup"><span data-stu-id="ebeb5-291"><xref:System.Windows.FontVariants.Inferior> &#124; <xref:System.Windows.FontVariants.Normal> &#124; <xref:System.Windows.FontVariants.Ordinal> &#124; <xref:System.Windows.FontVariants.Ruby> &#124; <xref:System.Windows.FontVariants.Subscript> &#124; <xref:System.Windows.FontVariants.Superscript></span></span>|<xref:System.Windows.FontVariants.Normal?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="ebeb5-292">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebeb5-292">See also</span></span>

- <xref:System.Windows.Documents.Typography>
- [<span data-ttu-id="ebeb5-293">OpenType 規格</span><span class="sxs-lookup"><span data-stu-id="ebeb5-293">OpenType Specification</span></span>](https://go.microsoft.com/fwlink/?LinkId=96731)
- [<span data-ttu-id="ebeb5-294">WPF 中的印刷樣式</span><span class="sxs-lookup"><span data-stu-id="ebeb5-294">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="ebeb5-295">範例 OpenType 字型套件</span><span class="sxs-lookup"><span data-stu-id="ebeb5-295">Sample OpenType Font Pack</span></span>](sample-opentype-font-pack.md)
- [<span data-ttu-id="ebeb5-296">將字型與應用程式一起封裝</span><span class="sxs-lookup"><span data-stu-id="ebeb5-296">Packaging Fonts with Applications</span></span>](packaging-fonts-with-applications.md)
