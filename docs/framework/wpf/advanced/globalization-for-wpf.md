---
title: WPF 的全球化
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
ms.openlocfilehash: d2bb4c9a00f31cb87ad8890591aa190fac6384f9
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2018
ms.locfileid: "48261533"
---
# <a name="globalization-for-wpf"></a><span data-ttu-id="e5191-102">WPF 的全球化</span><span class="sxs-lookup"><span data-stu-id="e5191-102">Globalization for WPF</span></span>
<span data-ttu-id="e5191-103">本主題將介紹您應留意撰寫時的問題[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]全球市場的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e5191-103">This topic introduces issues that you should be aware of when writing [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications for the global market.</span></span> <span data-ttu-id="e5191-104">全球化的程式設計項目中定義[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)]在`System.Globalization`。</span><span class="sxs-lookup"><span data-stu-id="e5191-104">The globalization programming elements are defined in [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] in `System.Globalization`.</span></span>



<a name="xaml_globalization"></a>
## <a name="xaml-globalization"></a><span data-ttu-id="e5191-105">XAML 全球化</span><span class="sxs-lookup"><span data-stu-id="e5191-105">XAML Globalization</span></span>
 [!INCLUDE[TLA#tla_xaml#initcap](../../../../includes/tlasharptla-xamlsharpinitcap-md.md)] <span data-ttu-id="e5191-106">根據[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]並利用中定義的全球化支援[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]規格。</span><span class="sxs-lookup"><span data-stu-id="e5191-106"> is based on [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] and takes advantage of the globalization support defined in the [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] specification.</span></span> <span data-ttu-id="e5191-107">下列各節說明一些[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]您應該要注意的功能。</span><span class="sxs-lookup"><span data-stu-id="e5191-107">The following sections describe some [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] features that you should be aware of.</span></span>

<a name="char_reference"></a>
### <a name="character-references"></a><span data-ttu-id="e5191-108">字元參考</span><span class="sxs-lookup"><span data-stu-id="e5191-108">Character References</span></span>
<span data-ttu-id="e5191-109">字元參考提供特定的 UTF16 程式碼單位[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]字元它代表，以十進位或十六進位。</span><span class="sxs-lookup"><span data-stu-id="e5191-109">A character reference gives the UTF16 code unit of the particular [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] character it represents, in either decimal or hexadecimal.</span></span> <span data-ttu-id="e5191-110">下列範例會顯示十進位字元參考科普特文大寫字母水，或 'Ϩ':</span><span class="sxs-lookup"><span data-stu-id="e5191-110">The following example shows a decimal character reference for the COPTIC CAPITAL LETTER HORI, or 'Ϩ':</span></span>

```
&#1000;
```

<span data-ttu-id="e5191-111">下列範例會顯示十六進位字元參考。</span><span class="sxs-lookup"><span data-stu-id="e5191-111">The following example shows a hexadecimal character reference.</span></span> <span data-ttu-id="e5191-112">請注意，它有**x**前面的十六進位數字。</span><span class="sxs-lookup"><span data-stu-id="e5191-112">Notice that it has an **x** in front of the hexadecimal number.</span></span>

```
&#x3E8;
```

<a name="encoding"></a>
### <a name="encoding"></a><span data-ttu-id="e5191-113">編碼</span><span class="sxs-lookup"><span data-stu-id="e5191-113">Encoding</span></span>
 <span data-ttu-id="e5191-114">所支援的編碼方式[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]都[!INCLUDE[TLA#tla_ascii](../../../../includes/tlasharptla-ascii-md.md)]， [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] UTF-16 和 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="e5191-114">The encoding supported by [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] are [!INCLUDE[TLA#tla_ascii](../../../../includes/tlasharptla-ascii-md.md)], [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] UTF-16, and UTF-8.</span></span> <span data-ttu-id="e5191-115">編碼陳述式是在開頭[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]文件。</span><span class="sxs-lookup"><span data-stu-id="e5191-115">The encoding statement is at the beginning of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] document.</span></span> <span data-ttu-id="e5191-116">如果沒有任何編碼屬性，而且沒有位元組順序，則剖析器預設為 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="e5191-116">If no encoding attribute exists and there is no byte-order, the parser defaults to UTF-8.</span></span> <span data-ttu-id="e5191-117">UTF-8 和 UTF-16 是慣用的編碼。</span><span class="sxs-lookup"><span data-stu-id="e5191-117">UTF-8 and UTF-16 are the preferred encodings.</span></span> <span data-ttu-id="e5191-118">不支援 UTF-7。</span><span class="sxs-lookup"><span data-stu-id="e5191-118">UTF-7 is not supported.</span></span> <span data-ttu-id="e5191-119">下列範例示範如何指定 utf-8 編碼方式在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案。</span><span class="sxs-lookup"><span data-stu-id="e5191-119">The following example demonstrates how to specify a UTF-8 encoding in a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.</span></span>

```
?xml encoding="UTF-8"?
```

<a name="lang_attrib"></a>
### <a name="language-attribute"></a><span data-ttu-id="e5191-120">語言屬性</span><span class="sxs-lookup"><span data-stu-id="e5191-120">Language Attribute</span></span>
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <span data-ttu-id="e5191-121">會使用[xml: lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md)來代表項目的 language 屬性。</span><span class="sxs-lookup"><span data-stu-id="e5191-121"> uses [xml:lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) to represent the language attribute of an element.</span></span>  <span data-ttu-id="e5191-122">若要善用<xref:System.Globalization.CultureInfo>類別，語言屬性值必須是其中一個預先定義的文化特性名稱<xref:System.Globalization.CultureInfo>。</span><span class="sxs-lookup"><span data-stu-id="e5191-122">To take advantage of the <xref:System.Globalization.CultureInfo> class, the language attribute value needs to be one of the culture names predefined by <xref:System.Globalization.CultureInfo>.</span></span> <span data-ttu-id="e5191-123">[xml:lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) 在項目樹狀結構中為可繼承 (依 XML 規則，不一定是因為相依性屬性繼承)，如未明確指派，其預設值為空字串。</span><span class="sxs-lookup"><span data-stu-id="e5191-123">[xml:lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) is inheritable in the element tree (by XML rules, not necessarily because of dependency property inheritance) and its default value is an empty string if it is not assigned explicitly.</span></span>

 <span data-ttu-id="e5191-124">語言屬性在指定方言方面非常有用。</span><span class="sxs-lookup"><span data-stu-id="e5191-124">The language attribute is very useful for specifying dialects.</span></span> <span data-ttu-id="e5191-125">例如，法國、魁北克、比利時和瑞士的法文拼字、字彙和發音不同。</span><span class="sxs-lookup"><span data-stu-id="e5191-125">For example, French has different spelling, vocabulary, and pronunciation in France, Quebec, Belgium, and Switzerland.</span></span> <span data-ttu-id="e5191-126">也中文、 日文和韓文共用中的字碼指標[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]，但表意圖形不同，他們使用完全不同的字型。</span><span class="sxs-lookup"><span data-stu-id="e5191-126">Also Chinese, Japanese, and Korean share code points in [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], but the ideographic shapes are different and they use totally different fonts.</span></span>

 <span data-ttu-id="e5191-127">下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]範例會使用`fr-CA`語言屬性來指定加拿大法文。</span><span class="sxs-lookup"><span data-stu-id="e5191-127">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example uses the `fr-CA` language attribute to specify Canadian French.</span></span>

```xml
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>
```

<a name="unicode"></a>
### <a name="unicode"></a><span data-ttu-id="e5191-128">Unicode</span><span class="sxs-lookup"><span data-stu-id="e5191-128">Unicode</span></span>
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <span data-ttu-id="e5191-129">支援所有[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]功能，包括 surrogate。</span><span class="sxs-lookup"><span data-stu-id="e5191-129"> supports all [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] features including surrogates.</span></span> <span data-ttu-id="e5191-130">只要字元集可以對應到[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]，支援它。</span><span class="sxs-lookup"><span data-stu-id="e5191-130">As long as the character set can be mapped to [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], it is supported.</span></span> <span data-ttu-id="e5191-131">例如，GB18030 推出可對應至中文、日文和韓文 (CFK) 延伸模組 A 和 B 及 surrogate 字組的某些字元，因此受到完整支援。</span><span class="sxs-lookup"><span data-stu-id="e5191-131">For example, GB18030 introduces some characters that are mapped to the Chinese, Japanese, and Korean (CFK) extension A and B and surrogate pairs, therefore it is fully supported.</span></span> <span data-ttu-id="e5191-132">A[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式可以使用<xref:System.Globalization.StringInfo>來操作不需要了解他們是否有 surrogate 字組或組合字元的字串。</span><span class="sxs-lookup"><span data-stu-id="e5191-132">A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application can use <xref:System.Globalization.StringInfo> to manipulate strings without understanding whether they have surrogate pairs or combining characters.</span></span>

<a name="design_intl_ui_with_xaml"></a>
## <a name="designing-an-international-user-interface-with-xaml"></a><span data-ttu-id="e5191-133">使用 XAML 設計國際化的使用者介面</span><span class="sxs-lookup"><span data-stu-id="e5191-133">Designing an International User Interface with XAML</span></span>
 <span data-ttu-id="e5191-134">本章節描述[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]撰寫的應用程式時，您應該考慮的功能。</span><span class="sxs-lookup"><span data-stu-id="e5191-134">This section describes [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] features that you should consider when writing an application.</span></span>

<a name="intl_text"></a>
### <a name="international-text"></a><span data-ttu-id="e5191-135">國際文字</span><span class="sxs-lookup"><span data-stu-id="e5191-135">International Text</span></span>
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="e5191-136">包含適用於所有支援的 Microsoft.NET Framework 的書寫系統的內建處理。</span><span class="sxs-lookup"><span data-stu-id="e5191-136"> includes built-in processing for all Microsoft .NET Framework supported writing systems.</span></span>

 <span data-ttu-id="e5191-137">目前支援下列指令碼︰</span><span class="sxs-lookup"><span data-stu-id="e5191-137">The following scripts are currently supported:</span></span>

-   <span data-ttu-id="e5191-138">阿拉伯文</span><span class="sxs-lookup"><span data-stu-id="e5191-138">Arabic</span></span>

-   <span data-ttu-id="e5191-139">孟加拉文</span><span class="sxs-lookup"><span data-stu-id="e5191-139">Bengali</span></span>

-   <span data-ttu-id="e5191-140">梵文字母</span><span class="sxs-lookup"><span data-stu-id="e5191-140">Devanagari</span></span>

-   <span data-ttu-id="e5191-141">斯拉夫文</span><span class="sxs-lookup"><span data-stu-id="e5191-141">Cyrillic</span></span>

-   <span data-ttu-id="e5191-142">希臘文</span><span class="sxs-lookup"><span data-stu-id="e5191-142">Greek</span></span>

-   <span data-ttu-id="e5191-143">古吉拉特文</span><span class="sxs-lookup"><span data-stu-id="e5191-143">Gujarati</span></span>

-   <span data-ttu-id="e5191-144">果魯穆奇文</span><span class="sxs-lookup"><span data-stu-id="e5191-144">Gurmukhi</span></span>

-   <span data-ttu-id="e5191-145">希伯來文</span><span class="sxs-lookup"><span data-stu-id="e5191-145">Hebrew</span></span>

-   <span data-ttu-id="e5191-146">表意指令碼</span><span class="sxs-lookup"><span data-stu-id="e5191-146">Ideographic scripts</span></span>

-   <span data-ttu-id="e5191-147">坎那達文</span><span class="sxs-lookup"><span data-stu-id="e5191-147">Kannada</span></span>

-   <span data-ttu-id="e5191-148">寮文</span><span class="sxs-lookup"><span data-stu-id="e5191-148">Lao</span></span>

-   <span data-ttu-id="e5191-149">拉丁文</span><span class="sxs-lookup"><span data-stu-id="e5191-149">Latin</span></span>

-   <span data-ttu-id="e5191-150">馬來亞拉姆文</span><span class="sxs-lookup"><span data-stu-id="e5191-150">Malayalam</span></span>

-   <span data-ttu-id="e5191-151">蒙古文</span><span class="sxs-lookup"><span data-stu-id="e5191-151">Mongolian</span></span>

-   <span data-ttu-id="e5191-152">歐迪亞文</span><span class="sxs-lookup"><span data-stu-id="e5191-152">Odia</span></span>

-   <span data-ttu-id="e5191-153">敘利亞文</span><span class="sxs-lookup"><span data-stu-id="e5191-153">Syriac</span></span>

-   <span data-ttu-id="e5191-154">坦米爾文</span><span class="sxs-lookup"><span data-stu-id="e5191-154">Tamil</span></span>

-   <span data-ttu-id="e5191-155">特拉古文</span><span class="sxs-lookup"><span data-stu-id="e5191-155">Telugu</span></span>

-   <span data-ttu-id="e5191-156">塔安那文</span><span class="sxs-lookup"><span data-stu-id="e5191-156">Thaana</span></span>

-   <span data-ttu-id="e5191-157">泰文\*</span><span class="sxs-lookup"><span data-stu-id="e5191-157">Thai\*</span></span>

-   <span data-ttu-id="e5191-158">西藏文</span><span class="sxs-lookup"><span data-stu-id="e5191-158">Tibetan</span></span>

 <span data-ttu-id="e5191-159">\*本版支援泰文文字的顯示和編輯，不支援斷詞。</span><span class="sxs-lookup"><span data-stu-id="e5191-159">\*In this release the display and editing of Thai text is supported; word breaking is not.</span></span>

 <span data-ttu-id="e5191-160">目前不支援下列指令碼︰</span><span class="sxs-lookup"><span data-stu-id="e5191-160">The following scripts are not currently supported:</span></span>

-   <span data-ttu-id="e5191-161">高棉文</span><span class="sxs-lookup"><span data-stu-id="e5191-161">Khmer</span></span>

-   <span data-ttu-id="e5191-162">古韓文</span><span class="sxs-lookup"><span data-stu-id="e5191-162">Korean Old Hangul</span></span>

-   <span data-ttu-id="e5191-163">緬甸文</span><span class="sxs-lookup"><span data-stu-id="e5191-163">Myanmar</span></span>

-   <span data-ttu-id="e5191-164">僧伽羅文</span><span class="sxs-lookup"><span data-stu-id="e5191-164">Sinhala</span></span>

 <span data-ttu-id="e5191-165">所有的書寫系統引擎都支援[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字型。</span><span class="sxs-lookup"><span data-stu-id="e5191-165">All the writing system engines support [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fonts.</span></span> [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] <span data-ttu-id="e5191-166">字型可以包括[!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]版面配置表格，讓字型建立者設計更好國際和高階的印刷樣式字型。</span><span class="sxs-lookup"><span data-stu-id="e5191-166"> fonts can include the [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] layout tables that enable font creators to design better international and high-end typographic fonts.</span></span> <span data-ttu-id="e5191-167">[!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]字型版面配置表格包含字符替代、 字符定位、 對齊和定位基準等相關資訊讓文字處理應用程式，以改善文字版面配置。</span><span class="sxs-lookup"><span data-stu-id="e5191-167">The [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] font layout tables contain information about glyph substitutions, glyph positioning, justification, and baseline positioning, enabling text-processing applications to improve text layout.</span></span>

 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] <span data-ttu-id="e5191-168">字型允許使用處理大型字符集[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]編碼方式。</span><span class="sxs-lookup"><span data-stu-id="e5191-168"> fonts allow the handling of large glyph sets using [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] encoding.</span></span> <span data-ttu-id="e5191-169">這類編碼促進廣泛的國際支援以及各種印刷樣式字符。</span><span class="sxs-lookup"><span data-stu-id="e5191-169">Such encoding enables broad international support as well as for typographic glyph variants.</span></span>

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="e5191-170">文字轉譯由[!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)]支援解析度獨立性的子像素技術。</span><span class="sxs-lookup"><span data-stu-id="e5191-170"> text rendering is powered by [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] sub-pixel technology that supports resolution independence.</span></span> <span data-ttu-id="e5191-171">這會大幅改善可讀性，並可讓您支援所有指令碼的高品質雜誌樣式文件。</span><span class="sxs-lookup"><span data-stu-id="e5191-171">This significantly improves legibility and provides the ability to support high quality magazine style documents for all scripts.</span></span>

<a name="intl_layout"></a>
### <a name="international-layout"></a><span data-ttu-id="e5191-172">國際版面配置</span><span class="sxs-lookup"><span data-stu-id="e5191-172">International Layout</span></span>
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="e5191-173">提供非常方便的方式來支援水平、雙向和垂直版面配置。</span><span class="sxs-lookup"><span data-stu-id="e5191-173"> provides a very convenient way to support horizontal, bidirectional, and vertical layouts.</span></span> <span data-ttu-id="e5191-174">在展示架構<xref:System.Windows.FrameworkElement.FlowDirection%2A>屬性可用來定義版面配置。</span><span class="sxs-lookup"><span data-stu-id="e5191-174">In presentation framework the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property can be used to define layout.</span></span> <span data-ttu-id="e5191-175">流程方向模式有︰</span><span class="sxs-lookup"><span data-stu-id="e5191-175">The flow direction patterns are:</span></span>

-   <span data-ttu-id="e5191-176">*LeftToRight* - 拉丁文、東亞等的水平配置。</span><span class="sxs-lookup"><span data-stu-id="e5191-176">*LeftToRight* - horizontal layout for Latin, East Asian and so forth.</span></span>

-   <span data-ttu-id="e5191-177">*RightToLeft* - 阿拉伯文、希伯來文等的雙向配置。</span><span class="sxs-lookup"><span data-stu-id="e5191-177">*RightToLeft* - bidirectional for Arabic, Hebrew and so forth.</span></span>

<a name="developing_localizable_apps"></a>
## <a name="developing-localizable-applications"></a><span data-ttu-id="e5191-178">開發可當地語系化的應用程式</span><span class="sxs-lookup"><span data-stu-id="e5191-178">Developing Localizable Applications</span></span>
 <span data-ttu-id="e5191-179">當您撰寫供全域使用的應用程式時，您應該記住應用程式必須是可當地語系化。</span><span class="sxs-lookup"><span data-stu-id="e5191-179">When you write an application for global consumption you should keep in mind that the application must be localizable.</span></span> <span data-ttu-id="e5191-180">下列主題指出要考量的事項。</span><span class="sxs-lookup"><span data-stu-id="e5191-180">The following topics point out things to consider.</span></span>

<a name="mui"></a>
### <a name="multilingual-user-interface"></a><span data-ttu-id="e5191-181">多語系使用者介面</span><span class="sxs-lookup"><span data-stu-id="e5191-181">Multilingual User Interface</span></span>
 <span data-ttu-id="e5191-182">多語系使用者介面 (MUI) 是[!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]支援切換[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]從到另一種語言。</span><span class="sxs-lookup"><span data-stu-id="e5191-182">Multilingual User Interfaces (MUI) is a [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] support for switching [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] from one language to another.</span></span> <span data-ttu-id="e5191-183">A[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式會使用組件模型支援 MUI。</span><span class="sxs-lookup"><span data-stu-id="e5191-183">A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application uses the assembly model to support MUI.</span></span> <span data-ttu-id="e5191-184">一個應用程式包含語言中性的組件以及語言相關的附屬資源組件。</span><span class="sxs-lookup"><span data-stu-id="e5191-184">One application contains language-neutral assemblies as well as language-dependent satellite resource assemblies.</span></span> <span data-ttu-id="e5191-185">進入點是主要組件中的 Managed .EXE。</span><span class="sxs-lookup"><span data-stu-id="e5191-185">The entry point is a managed .EXE in the main assembly.</span></span>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="e5191-186">資源載入器會利用[!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]的資源管理員支援資源查閱和後援。</span><span class="sxs-lookup"><span data-stu-id="e5191-186"> resource loader takes advantage of the [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]'s resource manager to support resource lookup and fallback.</span></span> <span data-ttu-id="e5191-187">多語言附屬組件使用相同的主要組件。</span><span class="sxs-lookup"><span data-stu-id="e5191-187">Multiple language satellite assemblies work with the same main assembly.</span></span> <span data-ttu-id="e5191-188">載入資源組件相依於<xref:System.Globalization.CultureInfo.CurrentUICulture%2A>目前執行緒。</span><span class="sxs-lookup"><span data-stu-id="e5191-188">The resource assembly that is loaded depends on the <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> of the current thread.</span></span>

<a name="localizable_ui"></a>
### <a name="localizable-user-interface"></a><span data-ttu-id="e5191-189">可當地語系化的使用者介面</span><span class="sxs-lookup"><span data-stu-id="e5191-189">Localizable User Interface</span></span>
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="e5191-190">應用程式會使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]來定義其[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e5191-190"> applications use [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to define their [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <span data-ttu-id="e5191-191">可讓開發人員使用一組屬性和邏輯指定物件的階層。</span><span class="sxs-lookup"><span data-stu-id="e5191-191"> allows developers to specify a hierarchy of objects with a set of properties and logic.</span></span> <span data-ttu-id="e5191-192">主要用法[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]是開發[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式，但它可以用來指定任何階層[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]物件。</span><span class="sxs-lookup"><span data-stu-id="e5191-192">The primary use of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is to develop [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications but it can be used to specify a hierarchy of any [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objects.</span></span> <span data-ttu-id="e5191-193">大部分的開發人員使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]來指定其應用程式的[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]並使用 C# 之類的程式設計語言回應使用者互動。</span><span class="sxs-lookup"><span data-stu-id="e5191-193">Most developers use [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to specify their application's [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] and use a programming language such as C# to react to user interaction.</span></span>

 <span data-ttu-id="e5191-194">從資源觀點而言[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]主要用來描述語言相依檔案[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]是資源項目，因此其最終發佈格式必須進行當地語系化，以支援國際語言。</span><span class="sxs-lookup"><span data-stu-id="e5191-194">From a resource point of view, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file designed to describe a language-dependent [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] is a resource element and therefore its final distribution format must be localizable to support international languages.</span></span> <span data-ttu-id="e5191-195">因為[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]無法處理事件許多[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]應用程式包含執行這項操作的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="e5191-195">Because [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] cannot handle events many [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] applications contain blocks of code to do this.</span></span> <span data-ttu-id="e5191-196">如需詳細資訊，請參閱 < [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)。</span><span class="sxs-lookup"><span data-stu-id="e5191-196">For more information, see [XAML Overview (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).</span></span> <span data-ttu-id="e5191-197">程式碼會被清除並編譯成不同的二進位檔時[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案語彙基元化成 BAML 形式的 XAML。</span><span class="sxs-lookup"><span data-stu-id="e5191-197">Code is stripped out and compiled into different binaries when a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is tokenized into the BAML form of XAML.</span></span> <span data-ttu-id="e5191-198">BAML 格式的 XAML 檔案、映像和其他類型的 Managed 資源物件會內嵌到附屬資源組件中，以當地語系化為其他語言，或在不需要當地語系化時內嵌到主要組件中。</span><span class="sxs-lookup"><span data-stu-id="e5191-198">The BAML form of XAML files, images, and other types of managed resource objects are embedded in the satellite resource assembly, which can be localized into other languages, or the main assembly when localization is not required.</span></span>

> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="e5191-199">應用程式支援所有[!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)][!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]資源，包括字串資料表、 影像和其他等等。</span><span class="sxs-lookup"><span data-stu-id="e5191-199"> applications support all the [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)][!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] resources including string tables, images, and so forth.</span></span>

<a name="building_localizable_apps"></a>
### <a name="building-localizable-applications"></a><span data-ttu-id="e5191-200">組建可當地語系化的應用程式</span><span class="sxs-lookup"><span data-stu-id="e5191-200">Building Localizable Applications</span></span>
 <span data-ttu-id="e5191-201">當地語系化表示適應[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]不同文化特性。</span><span class="sxs-lookup"><span data-stu-id="e5191-201">Localization means to adapt a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to different cultures.</span></span> <span data-ttu-id="e5191-202">若要讓[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式當地語系化，開發人員建置成資源組件的所有可當地語系化的資源。</span><span class="sxs-lookup"><span data-stu-id="e5191-202">To make a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application localizable, developers need to build all the localizable resources into a resource assembly.</span></span> <span data-ttu-id="e5191-203">資源組件已當地語系化成不同的語言和程式碼後置使用資源管理[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]載入。</span><span class="sxs-lookup"><span data-stu-id="e5191-203">The resource assembly is localized into different languages, and the code-behind uses resource management [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] to load.</span></span> <span data-ttu-id="e5191-204">其中一個所需的檔案[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式是專案檔 (.proj)。</span><span class="sxs-lookup"><span data-stu-id="e5191-204">One of the files required for a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application is a project file (.proj).</span></span> <span data-ttu-id="e5191-205">專案檔案應該包含您在應用程式中使用的所有資源。</span><span class="sxs-lookup"><span data-stu-id="e5191-205">All resources that you use in your application should be included in the project file.</span></span> <span data-ttu-id="e5191-206">以下的 .csproj 檔案範例示範如何執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="e5191-206">The following example from a .csproj file shows how to do this.</span></span>

```xml
<Resource Include="data\picture1.jpg"/>
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

 <span data-ttu-id="e5191-207">若要使用的資源，在您的應用程式中具現化<xref:System.Resources.ResourceManager>並載入您想要使用的資源。</span><span class="sxs-lookup"><span data-stu-id="e5191-207">To use a resource in your application instantiate a <xref:System.Resources.ResourceManager> and load the resource you want to use.</span></span> <span data-ttu-id="e5191-208">下列範例示範如何進行這項操作。</span><span class="sxs-lookup"><span data-stu-id="e5191-208">The following example demonstrates how to do this.</span></span>

 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

<a name="using_clickonce"></a>
## <a name="using-clickonce-with-localized-applications"></a><span data-ttu-id="e5191-209">使用 ClickOnce 與當地語系化的應用程式</span><span class="sxs-lookup"><span data-stu-id="e5191-209">Using ClickOnce with Localized Applications</span></span>
 <span data-ttu-id="e5191-210">ClickOnce 是新的 Windows Forms 部署技術，將隨附於 Visual Studio 2005。</span><span class="sxs-lookup"><span data-stu-id="e5191-210">ClickOnce is a new Windows Forms deployment technology that will ship with Visual Studio 2005.</span></span> <span data-ttu-id="e5191-211">它能讓應用程式安裝及升級 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e5191-211">It enables application installation and upgrading of Web applications.</span></span> <span data-ttu-id="e5191-212">當地語系化使用 ClickOnce 部署的應用程式時，只能在已當地語系化的文化特性中檢視它。</span><span class="sxs-lookup"><span data-stu-id="e5191-212">When an application that was deployed with ClickOnce is localized it can only be viewed on the localized culture.</span></span> <span data-ttu-id="e5191-213">例如，如果部署的應用程式已當地語系化為日文就可以只檢視上日文[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]不能在英文版的 Windows。</span><span class="sxs-lookup"><span data-stu-id="e5191-213">For example, if a deployed application is localized to Japanese it can only be viewed on Japanese [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] not on English Windows.</span></span> <span data-ttu-id="e5191-214">這會帶來問題，因為它是日文使用者執行英文版的 Windows 的常見案例。</span><span class="sxs-lookup"><span data-stu-id="e5191-214">This presents a problem because it is a common scenario for Japanese users to run an English version of Windows.</span></span>

 <span data-ttu-id="e5191-215">此問題的解決方案是設定中性的語言後援屬性。</span><span class="sxs-lookup"><span data-stu-id="e5191-215">The solution to this problem is setting the neutral language fallback attribute.</span></span> <span data-ttu-id="e5191-216">應用程式開發人員可以選擇性地從主要組件中移除資源，指定可在附屬組件中找到的資源對應至特定的文化特性。</span><span class="sxs-lookup"><span data-stu-id="e5191-216">An application developer can optionally remove resources from the main assembly and specify that the resources can be found in a satellite assembly corresponding to a specific culture.</span></span> <span data-ttu-id="e5191-217">若要控制這個程序使用<xref:System.Resources.NeutralResourcesLanguageAttribute>。</span><span class="sxs-lookup"><span data-stu-id="e5191-217">To control this process use the <xref:System.Resources.NeutralResourcesLanguageAttribute>.</span></span> <span data-ttu-id="e5191-218">建構函式<xref:System.Resources.NeutralResourcesLanguageAttribute>類別具有兩個簽章，另一個會採用<xref:System.Resources.UltimateResourceFallbackLocation>參數來指定位置其中<xref:System.Resources.ResourceManager>應該擷取後援資源： 主要組件或附屬組件。</span><span class="sxs-lookup"><span data-stu-id="e5191-218">The constructor of the <xref:System.Resources.NeutralResourcesLanguageAttribute> class has two signatures, one that takes an <xref:System.Resources.UltimateResourceFallbackLocation> parameter to specify the location where the <xref:System.Resources.ResourceManager> should extract the fallback resources: main assembly or satellite assembly.</span></span> <span data-ttu-id="e5191-219">下列範例顯示如何使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="e5191-219">The following example shows how to use the attribute.</span></span> <span data-ttu-id="e5191-220">針對最終後援位置，此程式碼造成<xref:System.Resources.ResourceManager>來尋找目前正在執行的組件的目錄的"de"子目錄中的資源。</span><span class="sxs-lookup"><span data-stu-id="e5191-220">For the ultimate fallback location, the code causes the <xref:System.Resources.ResourceManager> to look for the resources in the "de" subdirectory of the directory of the currently executing assembly.</span></span>

```
[assembly: NeutralResourcesLanguageAttribute(
    "de" , UltimateResourceFallbackLocation.Satellite)]
```

## <a name="see-also"></a><span data-ttu-id="e5191-221">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5191-221">See Also</span></span>
 [<span data-ttu-id="e5191-222">WPF 全球化和當地語系化概觀</span><span class="sxs-lookup"><span data-stu-id="e5191-222">WPF Globalization and Localization Overview</span></span>](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)
