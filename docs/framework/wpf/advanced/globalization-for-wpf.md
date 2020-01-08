---
title: WPF 的全球化
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
ms.openlocfilehash: 769afe4d301a7b0fafd26018255f98b6faa29887
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559431"
---
# <a name="globalization-for-wpf"></a><span data-ttu-id="9f829-102">WPF 的全球化</span><span class="sxs-lookup"><span data-stu-id="9f829-102">Globalization for WPF</span></span>
<span data-ttu-id="9f829-103">本主題將介紹在為全球市場撰寫 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式時，您應該注意的問題。</span><span class="sxs-lookup"><span data-stu-id="9f829-103">This topic introduces issues that you should be aware of when writing [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications for the global market.</span></span> <span data-ttu-id="9f829-104">全球化程式設計項目會在 .NET 的 <xref:System.Globalization> 命名空間中定義。</span><span class="sxs-lookup"><span data-stu-id="9f829-104">The globalization programming elements are defined in .NET in the <xref:System.Globalization> namespace.</span></span>

<a name="xaml_globalization"></a>
## <a name="xaml-globalization"></a><span data-ttu-id="9f829-105">XAML 全球化</span><span class="sxs-lookup"><span data-stu-id="9f829-105">XAML Globalization</span></span>
 <span data-ttu-id="9f829-106">Extensible Application Markup Language （XAML）是以 XML 為基礎，並利用 XML 規格中定義的全球化支援。</span><span class="sxs-lookup"><span data-stu-id="9f829-106">Extensible Application Markup Language (XAML) is based on XML and takes advantage of the globalization support defined in the XML specification.</span></span> <span data-ttu-id="9f829-107">下列各節將說明一些您應該注意的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="9f829-107">The following sections describe some [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] features that you should be aware of.</span></span>

<a name="char_reference"></a>
### <a name="character-references"></a><span data-ttu-id="9f829-108">字元參考</span><span class="sxs-lookup"><span data-stu-id="9f829-108">Character References</span></span>
<span data-ttu-id="9f829-109">字元參考會提供它所代表之特定 Unicode 字元的 UTF16 程式碼單位（以十進位或十六進位表示）。</span><span class="sxs-lookup"><span data-stu-id="9f829-109">A character reference gives the UTF16 code unit of the particular Unicode character it represents, in either decimal or hexadecimal.</span></span> <span data-ttu-id="9f829-110">下列範例會顯示「哥英數位元」或「Ϩ」的十進位字元參考：</span><span class="sxs-lookup"><span data-stu-id="9f829-110">The following example shows a decimal character reference for the COPTIC CAPITAL LETTER HORI, or 'Ϩ':</span></span>

```
&#1000;
```

<span data-ttu-id="9f829-111">下列範例顯示十六進位字元參考。</span><span class="sxs-lookup"><span data-stu-id="9f829-111">The following example shows a hexadecimal character reference.</span></span> <span data-ttu-id="9f829-112">請注意，它在十六進位數位前面有一個**x** 。</span><span class="sxs-lookup"><span data-stu-id="9f829-112">Notice that it has an **x** in front of the hexadecimal number.</span></span>

```
&#x3E8;
```

<a name="encoding"></a>
### <a name="encoding"></a><span data-ttu-id="9f829-113">Encoding</span><span class="sxs-lookup"><span data-stu-id="9f829-113">Encoding</span></span>
 <span data-ttu-id="9f829-114">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 支援的編碼為 ASCII、Unicode UTF-16 和 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="9f829-114">The encoding supported by [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] are ASCII, Unicode UTF-16, and UTF-8.</span></span> <span data-ttu-id="9f829-115">編碼語句位於 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔的開頭。</span><span class="sxs-lookup"><span data-stu-id="9f829-115">The encoding statement is at the beginning of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] document.</span></span> <span data-ttu-id="9f829-116">如果沒有任何編碼屬性，而且沒有位元組順序，則剖析器預設為 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="9f829-116">If no encoding attribute exists and there is no byte-order, the parser defaults to UTF-8.</span></span> <span data-ttu-id="9f829-117">UTF-8 和 UTF-16 是慣用的編碼。</span><span class="sxs-lookup"><span data-stu-id="9f829-117">UTF-8 and UTF-16 are the preferred encodings.</span></span> <span data-ttu-id="9f829-118">不支援 UTF-7。</span><span class="sxs-lookup"><span data-stu-id="9f829-118">UTF-7 is not supported.</span></span> <span data-ttu-id="9f829-119">下列範例示範如何在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案中指定 UTF-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="9f829-119">The following example demonstrates how to specify a UTF-8 encoding in a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.</span></span>

```xaml
?xml encoding="UTF-8"?
```

<a name="lang_attrib"></a>
### <a name="language-attribute"></a><span data-ttu-id="9f829-120">語言屬性</span><span class="sxs-lookup"><span data-stu-id="9f829-120">Language Attribute</span></span>
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <span data-ttu-id="9f829-121">使用[xml： lang](../../../desktop-wpf/xaml-services/xml-language-handling.md)來代表元素的 language 屬性。</span><span class="sxs-lookup"><span data-stu-id="9f829-121">uses [xml:lang](../../../desktop-wpf/xaml-services/xml-language-handling.md) to represent the language attribute of an element.</span></span>  <span data-ttu-id="9f829-122">若要利用 <xref:System.Globalization.CultureInfo> 類別，語言屬性值必須是 <xref:System.Globalization.CultureInfo>預先定義的其中一個文化特性名稱。</span><span class="sxs-lookup"><span data-stu-id="9f829-122">To take advantage of the <xref:System.Globalization.CultureInfo> class, the language attribute value needs to be one of the culture names predefined by <xref:System.Globalization.CultureInfo>.</span></span> <span data-ttu-id="9f829-123">[xml:lang](../../../desktop-wpf/xaml-services/xml-language-handling.md) 在項目樹狀結構中為可繼承 (依 XML 規則，不一定是因為相依性屬性繼承)，如未明確指派，其預設值為空字串。</span><span class="sxs-lookup"><span data-stu-id="9f829-123">[xml:lang](../../../desktop-wpf/xaml-services/xml-language-handling.md) is inheritable in the element tree (by XML rules, not necessarily because of dependency property inheritance) and its default value is an empty string if it is not assigned explicitly.</span></span>

 <span data-ttu-id="9f829-124">語言屬性在指定方言方面非常有用。</span><span class="sxs-lookup"><span data-stu-id="9f829-124">The language attribute is very useful for specifying dialects.</span></span> <span data-ttu-id="9f829-125">例如，法國、魁北克、比利時和瑞士的法文拼字、字彙和發音不同。</span><span class="sxs-lookup"><span data-stu-id="9f829-125">For example, French has different spelling, vocabulary, and pronunciation in France, Quebec, Belgium, and Switzerland.</span></span> <span data-ttu-id="9f829-126">中文、日文和韓文也會以 Unicode 共用程式碼點，但表意形狀不同，而且會使用完全不同的字型。</span><span class="sxs-lookup"><span data-stu-id="9f829-126">Also Chinese, Japanese, and Korean share code points in Unicode, but the ideographic shapes are different and they use totally different fonts.</span></span>

 <span data-ttu-id="9f829-127">下列 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 範例會使用 `fr-CA` language 屬性來指定加拿大法文。</span><span class="sxs-lookup"><span data-stu-id="9f829-127">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example uses the `fr-CA` language attribute to specify Canadian French.</span></span>

```xaml
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>
```

<a name="unicode"></a>
### <a name="unicode"></a><span data-ttu-id="9f829-128">Unicode</span><span class="sxs-lookup"><span data-stu-id="9f829-128">Unicode</span></span>
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <span data-ttu-id="9f829-129">支援包括代理的所有 Unicode 功能。</span><span class="sxs-lookup"><span data-stu-id="9f829-129">supports all Unicode features including surrogates.</span></span> <span data-ttu-id="9f829-130">只要字元集可以對應到 Unicode，就會受到支援。</span><span class="sxs-lookup"><span data-stu-id="9f829-130">As long as the character set can be mapped to Unicode, it is supported.</span></span> <span data-ttu-id="9f829-131">例如，GB18030 推出可對應至中文、日文和韓文 (CFK) 延伸模組 A 和 B 及 surrogate 字組的某些字元，因此受到完整支援。</span><span class="sxs-lookup"><span data-stu-id="9f829-131">For example, GB18030 introduces some characters that are mapped to the Chinese, Japanese, and Korean (CFK) extension A and B and surrogate pairs, therefore it is fully supported.</span></span> <span data-ttu-id="9f829-132">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的應用程式可以使用 <xref:System.Globalization.StringInfo> 來操作字串，而不需要瞭解它們是否有代理項配對或合併字元。</span><span class="sxs-lookup"><span data-stu-id="9f829-132">A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application can use <xref:System.Globalization.StringInfo> to manipulate strings without understanding whether they have surrogate pairs or combining characters.</span></span>

<a name="design_intl_ui_with_xaml"></a>
## <a name="designing-an-international-user-interface-with-xaml"></a><span data-ttu-id="9f829-133">使用 XAML 設計國際化的使用者介面</span><span class="sxs-lookup"><span data-stu-id="9f829-133">Designing an International User Interface with XAML</span></span>
 <span data-ttu-id="9f829-134">本節說明撰寫應用程式時，您應該考慮的 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="9f829-134">This section describes [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] features that you should consider when writing an application.</span></span>

<a name="intl_text"></a>
### <a name="international-text"></a><span data-ttu-id="9f829-135">國際文字</span><span class="sxs-lookup"><span data-stu-id="9f829-135">International Text</span></span>
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="9f829-136">包括所有 Microsoft .NET Framework 支援的書寫系統的內建處理。</span><span class="sxs-lookup"><span data-stu-id="9f829-136">includes built-in processing for all Microsoft .NET Framework supported writing systems.</span></span>

 <span data-ttu-id="9f829-137">目前支援下列指令碼︰</span><span class="sxs-lookup"><span data-stu-id="9f829-137">The following scripts are currently supported:</span></span>

- <span data-ttu-id="9f829-138">阿拉伯文</span><span class="sxs-lookup"><span data-stu-id="9f829-138">Arabic</span></span>

- <span data-ttu-id="9f829-139">孟加拉文</span><span class="sxs-lookup"><span data-stu-id="9f829-139">Bengali</span></span>

- <span data-ttu-id="9f829-140">梵文字母</span><span class="sxs-lookup"><span data-stu-id="9f829-140">Devanagari</span></span>

- <span data-ttu-id="9f829-141">斯拉夫文</span><span class="sxs-lookup"><span data-stu-id="9f829-141">Cyrillic</span></span>

- <span data-ttu-id="9f829-142">希臘文</span><span class="sxs-lookup"><span data-stu-id="9f829-142">Greek</span></span>

- <span data-ttu-id="9f829-143">古吉拉特文</span><span class="sxs-lookup"><span data-stu-id="9f829-143">Gujarati</span></span>

- <span data-ttu-id="9f829-144">果魯穆奇文</span><span class="sxs-lookup"><span data-stu-id="9f829-144">Gurmukhi</span></span>

- <span data-ttu-id="9f829-145">希伯來文</span><span class="sxs-lookup"><span data-stu-id="9f829-145">Hebrew</span></span>

- <span data-ttu-id="9f829-146">表意指令碼</span><span class="sxs-lookup"><span data-stu-id="9f829-146">Ideographic scripts</span></span>

- <span data-ttu-id="9f829-147">坎那達文</span><span class="sxs-lookup"><span data-stu-id="9f829-147">Kannada</span></span>

- <span data-ttu-id="9f829-148">寮文</span><span class="sxs-lookup"><span data-stu-id="9f829-148">Lao</span></span>

- <span data-ttu-id="9f829-149">拉丁文</span><span class="sxs-lookup"><span data-stu-id="9f829-149">Latin</span></span>

- <span data-ttu-id="9f829-150">馬來亞拉姆文</span><span class="sxs-lookup"><span data-stu-id="9f829-150">Malayalam</span></span>

- <span data-ttu-id="9f829-151">蒙古文</span><span class="sxs-lookup"><span data-stu-id="9f829-151">Mongolian</span></span>

- <span data-ttu-id="9f829-152">歐迪亞文</span><span class="sxs-lookup"><span data-stu-id="9f829-152">Odia</span></span>

- <span data-ttu-id="9f829-153">敘利亞文</span><span class="sxs-lookup"><span data-stu-id="9f829-153">Syriac</span></span>

- <span data-ttu-id="9f829-154">坦米爾文</span><span class="sxs-lookup"><span data-stu-id="9f829-154">Tamil</span></span>

- <span data-ttu-id="9f829-155">特拉古文</span><span class="sxs-lookup"><span data-stu-id="9f829-155">Telugu</span></span>

- <span data-ttu-id="9f829-156">塔安那文</span><span class="sxs-lookup"><span data-stu-id="9f829-156">Thaana</span></span>

- <span data-ttu-id="9f829-157">泰文\*</span><span class="sxs-lookup"><span data-stu-id="9f829-157">Thai\*</span></span>

- <span data-ttu-id="9f829-158">西藏文</span><span class="sxs-lookup"><span data-stu-id="9f829-158">Tibetan</span></span>

 <span data-ttu-id="9f829-159">\*本版支援泰文文字的顯示和編輯，不支援斷詞。</span><span class="sxs-lookup"><span data-stu-id="9f829-159">\*In this release the display and editing of Thai text is supported; word breaking is not.</span></span>

 <span data-ttu-id="9f829-160">目前不支援下列指令碼︰</span><span class="sxs-lookup"><span data-stu-id="9f829-160">The following scripts are not currently supported:</span></span>

- <span data-ttu-id="9f829-161">高棉文</span><span class="sxs-lookup"><span data-stu-id="9f829-161">Khmer</span></span>

- <span data-ttu-id="9f829-162">古韓文</span><span class="sxs-lookup"><span data-stu-id="9f829-162">Korean Old Hangul</span></span>

- <span data-ttu-id="9f829-163">緬甸文</span><span class="sxs-lookup"><span data-stu-id="9f829-163">Myanmar</span></span>

- <span data-ttu-id="9f829-164">錫蘭文</span><span class="sxs-lookup"><span data-stu-id="9f829-164">Sinhala</span></span>

 <span data-ttu-id="9f829-165">所有的書寫系統引擎都支援 OpenType 字型。</span><span class="sxs-lookup"><span data-stu-id="9f829-165">All the writing system engines support OpenType fonts.</span></span> <span data-ttu-id="9f829-166">OpenType 字型可以包含 OpenType 版面配置資料表，讓字型建立者能夠設計更好的國際和高階印刷樣式。</span><span class="sxs-lookup"><span data-stu-id="9f829-166">OpenType fonts can include the OpenType layout tables that enable font creators to design better international and high-end typographic fonts.</span></span> <span data-ttu-id="9f829-167">OpenType 字型版面配置表包含圖像替換、圖像定位、對齊和基準定位的相關資訊，可讓文字處理應用程式改善文字版面配置。</span><span class="sxs-lookup"><span data-stu-id="9f829-167">The OpenType font layout tables contain information about glyph substitutions, glyph positioning, justification, and baseline positioning, enabling text-processing applications to improve text layout.</span></span>

 <span data-ttu-id="9f829-168">OpenType 字型允許使用 Unicode 編碼來處理大型圖像集。</span><span class="sxs-lookup"><span data-stu-id="9f829-168">OpenType fonts allow the handling of large glyph sets using Unicode encoding.</span></span> <span data-ttu-id="9f829-169">這類編碼促進廣泛的國際支援以及各種印刷樣式字符。</span><span class="sxs-lookup"><span data-stu-id="9f829-169">Such encoding enables broad international support as well as for typographic glyph variants.</span></span>

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="9f829-170">文字轉譯是由支援解析度獨立性的 Microsoft ClearType 子圖元技術提供技術支援。</span><span class="sxs-lookup"><span data-stu-id="9f829-170">text rendering is powered by Microsoft ClearType sub-pixel technology that supports resolution independence.</span></span> <span data-ttu-id="9f829-171">這會大幅改善可讀性，並可讓您支援所有指令碼的高品質雜誌樣式文件。</span><span class="sxs-lookup"><span data-stu-id="9f829-171">This significantly improves legibility and provides the ability to support high quality magazine style documents for all scripts.</span></span>

<a name="intl_layout"></a>
### <a name="international-layout"></a><span data-ttu-id="9f829-172">國際版面配置</span><span class="sxs-lookup"><span data-stu-id="9f829-172">International Layout</span></span>
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="9f829-173">提供非常方便的方式來支援水平、雙向和垂直版面配置。</span><span class="sxs-lookup"><span data-stu-id="9f829-173">provides a very convenient way to support horizontal, bidirectional, and vertical layouts.</span></span> <span data-ttu-id="9f829-174">在展示架構中，<xref:System.Windows.FrameworkElement.FlowDirection%2A> 屬性可以用來定義版面配置。</span><span class="sxs-lookup"><span data-stu-id="9f829-174">In presentation framework the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property can be used to define layout.</span></span> <span data-ttu-id="9f829-175">流程方向模式有︰</span><span class="sxs-lookup"><span data-stu-id="9f829-175">The flow direction patterns are:</span></span>

- <span data-ttu-id="9f829-176">*LeftToRight* - 拉丁文、東亞等的水平配置。</span><span class="sxs-lookup"><span data-stu-id="9f829-176">*LeftToRight* - horizontal layout for Latin, East Asian and so forth.</span></span>

- <span data-ttu-id="9f829-177">*RightToLeft* - 阿拉伯文、希伯來文等的雙向配置。</span><span class="sxs-lookup"><span data-stu-id="9f829-177">*RightToLeft* - bidirectional for Arabic, Hebrew and so forth.</span></span>

<a name="developing_localizable_apps"></a>
## <a name="developing-localizable-applications"></a><span data-ttu-id="9f829-178">開發可當地語系化的應用程式</span><span class="sxs-lookup"><span data-stu-id="9f829-178">Developing Localizable Applications</span></span>
 <span data-ttu-id="9f829-179">當您撰寫供全域使用的應用程式時，您應該記住應用程式必須是可當地語系化。</span><span class="sxs-lookup"><span data-stu-id="9f829-179">When you write an application for global consumption you should keep in mind that the application must be localizable.</span></span> <span data-ttu-id="9f829-180">下列主題指出要考量的事項。</span><span class="sxs-lookup"><span data-stu-id="9f829-180">The following topics point out things to consider.</span></span>

<a name="mui"></a>
### <a name="multilingual-user-interface"></a><span data-ttu-id="9f829-181">多語系使用者介面</span><span class="sxs-lookup"><span data-stu-id="9f829-181">Multilingual User Interface</span></span>
 <span data-ttu-id="9f829-182">多語系使用者介面（MUI）是一種 Microsoft 支援，可將 Ui 從某種語言切換成另一種語言。</span><span class="sxs-lookup"><span data-stu-id="9f829-182">Multilingual User Interfaces (MUI) is a Microsoft support for switching UIs from one language to another.</span></span> <span data-ttu-id="9f829-183">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式會使用元件模型來支援 MUI。</span><span class="sxs-lookup"><span data-stu-id="9f829-183">A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application uses the assembly model to support MUI.</span></span> <span data-ttu-id="9f829-184">一個應用程式包含語言中性的組件以及語言相關的附屬資源組件。</span><span class="sxs-lookup"><span data-stu-id="9f829-184">One application contains language-neutral assemblies as well as language-dependent satellite resource assemblies.</span></span> <span data-ttu-id="9f829-185">進入點是主要組件中的 Managed .EXE。</span><span class="sxs-lookup"><span data-stu-id="9f829-185">The entry point is a managed .EXE in the main assembly.</span></span>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="9f829-186">資源載入器會利用架構的資源管理員來支援資源查閱和回溯。</span><span class="sxs-lookup"><span data-stu-id="9f829-186">resource loader takes advantage of the Framework's resource manager to support resource lookup and fallback.</span></span> <span data-ttu-id="9f829-187">多語言附屬組件使用相同的主要組件。</span><span class="sxs-lookup"><span data-stu-id="9f829-187">Multiple language satellite assemblies work with the same main assembly.</span></span> <span data-ttu-id="9f829-188">載入的資源元件取決於目前線程的 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A>。</span><span class="sxs-lookup"><span data-stu-id="9f829-188">The resource assembly that is loaded depends on the <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> of the current thread.</span></span>

<a name="localizable_ui"></a>
### <a name="localizable-user-interface"></a><span data-ttu-id="9f829-189">可當地語系化的使用者介面</span><span class="sxs-lookup"><span data-stu-id="9f829-189">Localizable User Interface</span></span>
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="9f829-190">應用程式會使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 來定義其 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9f829-190">applications use [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to define their [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <span data-ttu-id="9f829-191">可讓開發人員使用一組屬性和邏輯指定物件的階層。</span><span class="sxs-lookup"><span data-stu-id="9f829-191">allows developers to specify a hierarchy of objects with a set of properties and logic.</span></span> <span data-ttu-id="9f829-192">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的主要用途是開發 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的應用程式，但它可以用來指定任何 common language runtime （CLR）物件的階層架構。</span><span class="sxs-lookup"><span data-stu-id="9f829-192">The primary use of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is to develop [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications but it can be used to specify a hierarchy of any common language runtime (CLR) objects.</span></span> <span data-ttu-id="9f829-193">大部分的開發人員會使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 來指定其應用程式的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，並使用C#之類的程式設計語言來回應使用者互動。</span><span class="sxs-lookup"><span data-stu-id="9f829-193">Most developers use [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to specify their application's [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] and use a programming language such as C# to react to user interaction.</span></span>

 <span data-ttu-id="9f829-194">從資源的觀點來看，設計用來描述與語言相關 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案是資源元素，因此最終的散發格式必須可以當地語系化以支援國際語言。</span><span class="sxs-lookup"><span data-stu-id="9f829-194">From a resource point of view, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file designed to describe a language-dependent [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] is a resource element and therefore its final distribution format must be localizable to support international languages.</span></span> <span data-ttu-id="9f829-195">因為 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 無法處理事件，所以許多 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的應用程式都包含執行這項工作的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="9f829-195">Because [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] cannot handle events many [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] applications contain blocks of code to do this.</span></span> <span data-ttu-id="9f829-196">如需詳細資訊，請參閱[XAML 總覽（WPF）](../../../desktop-wpf/fundamentals/xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="9f829-196">For more information, see [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md).</span></span> <span data-ttu-id="9f829-197">當 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案標記為 XAML 的 BAML 形式時，會將程式碼去除並編譯成不同的二進位檔。</span><span class="sxs-lookup"><span data-stu-id="9f829-197">Code is stripped out and compiled into different binaries when a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is tokenized into the BAML form of XAML.</span></span> <span data-ttu-id="9f829-198">BAML 格式的 XAML 檔案、映像和其他類型的 Managed 資源物件會內嵌到附屬資源組件中，以當地語系化為其他語言，或在不需要當地語系化時內嵌到主要組件中。</span><span class="sxs-lookup"><span data-stu-id="9f829-198">The BAML form of XAML files, images, and other types of managed resource objects are embedded in the satellite resource assembly, which can be localized into other languages, or the main assembly when localization is not required.</span></span>

> [!NOTE]
> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="9f829-199">應用程式支援所有 FrameworkCLR 資源，包括字串資料表、影像等等。</span><span class="sxs-lookup"><span data-stu-id="9f829-199">applications support all the FrameworkCLR resources including string tables, images, and so forth.</span></span>

<a name="building_localizable_apps"></a>
### <a name="building-localizable-applications"></a><span data-ttu-id="9f829-200">組建可當地語系化的應用程式</span><span class="sxs-lookup"><span data-stu-id="9f829-200">Building Localizable Applications</span></span>
 <span data-ttu-id="9f829-201">當地語系化表示要將 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 調整成不同的文化特性。</span><span class="sxs-lookup"><span data-stu-id="9f829-201">Localization means to adapt a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to different cultures.</span></span> <span data-ttu-id="9f829-202">若要讓 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式當地語系化，開發人員需要將所有可當地語系化的資源建立到資源元件中。</span><span class="sxs-lookup"><span data-stu-id="9f829-202">To make a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application localizable, developers need to build all the localizable resources into a resource assembly.</span></span> <span data-ttu-id="9f829-203">資源元件已當地語系化成不同的語言，而程式碼後置使用資源管理 API 來載入。</span><span class="sxs-lookup"><span data-stu-id="9f829-203">The resource assembly is localized into different languages, and the code-behind uses resource management API to load.</span></span> <span data-ttu-id="9f829-204">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式所需的其中一個檔案是專案檔（proj）。</span><span class="sxs-lookup"><span data-stu-id="9f829-204">One of the files required for a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application is a project file (.proj).</span></span> <span data-ttu-id="9f829-205">專案檔案應該包含您在應用程式中使用的所有資源。</span><span class="sxs-lookup"><span data-stu-id="9f829-205">All resources that you use in your application should be included in the project file.</span></span> <span data-ttu-id="9f829-206">以下的 .csproj 檔案範例示範如何執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="9f829-206">The following example from a .csproj file shows how to do this.</span></span>

```xml
<Resource Include="data\picture1.jpg"/>
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

 <span data-ttu-id="9f829-207">若要在您的應用程式中使用資源，請具現化 <xref:System.Resources.ResourceManager> 並載入您想要使用的資源。</span><span class="sxs-lookup"><span data-stu-id="9f829-207">To use a resource in your application instantiate a <xref:System.Resources.ResourceManager> and load the resource you want to use.</span></span> <span data-ttu-id="9f829-208">下列範例示範如何進行這項操作。</span><span class="sxs-lookup"><span data-stu-id="9f829-208">The following example demonstrates how to do this.</span></span>

 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

<a name="using_clickonce"></a>
## <a name="using-clickonce-with-localized-applications"></a><span data-ttu-id="9f829-209">使用 ClickOnce 與當地語系化的應用程式</span><span class="sxs-lookup"><span data-stu-id="9f829-209">Using ClickOnce with Localized Applications</span></span>
 <span data-ttu-id="9f829-210">ClickOnce 是一種新的 Windows Forms 部署技術，會 Visual Studio 2005 發行。</span><span class="sxs-lookup"><span data-stu-id="9f829-210">ClickOnce is a new Windows Forms deployment technology that will ship with Visual Studio 2005.</span></span> <span data-ttu-id="9f829-211">它能讓應用程式安裝及升級 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9f829-211">It enables application installation and upgrading of Web applications.</span></span> <span data-ttu-id="9f829-212">當地語系化使用 ClickOnce 部署的應用程式時，只能在已當地語系化的文化特性中檢視它。</span><span class="sxs-lookup"><span data-stu-id="9f829-212">When an application that was deployed with ClickOnce is localized it can only be viewed on the localized culture.</span></span> <span data-ttu-id="9f829-213">例如，如果已部署的應用程式已當地語系化為日文，則只能在日文 Microsoft Windows 上查看，而不是在英文版的 Windows 上。</span><span class="sxs-lookup"><span data-stu-id="9f829-213">For example, if a deployed application is localized to Japanese it can only be viewed on Japanese Microsoft Windows not on English Windows.</span></span> <span data-ttu-id="9f829-214">這會造成問題，因為這是日文使用者執行英文版 Windows 的常見案例。</span><span class="sxs-lookup"><span data-stu-id="9f829-214">This presents a problem because it is a common scenario for Japanese users to run an English version of Windows.</span></span>

 <span data-ttu-id="9f829-215">此問題的解決方案是設定中性的語言後援屬性。</span><span class="sxs-lookup"><span data-stu-id="9f829-215">The solution to this problem is setting the neutral language fallback attribute.</span></span> <span data-ttu-id="9f829-216">應用程式開發人員可以選擇性地從主要組件中移除資源，指定可在附屬組件中找到的資源對應至特定的文化特性。</span><span class="sxs-lookup"><span data-stu-id="9f829-216">An application developer can optionally remove resources from the main assembly and specify that the resources can be found in a satellite assembly corresponding to a specific culture.</span></span> <span data-ttu-id="9f829-217">若要控制此進程，請使用 <xref:System.Resources.NeutralResourcesLanguageAttribute>。</span><span class="sxs-lookup"><span data-stu-id="9f829-217">To control this process use the <xref:System.Resources.NeutralResourcesLanguageAttribute>.</span></span> <span data-ttu-id="9f829-218"><xref:System.Resources.NeutralResourcesLanguageAttribute> 類別的函式有兩個簽章，其中一個會採用 <xref:System.Resources.UltimateResourceFallbackLocation> 參數來指定 <xref:System.Resources.ResourceManager> 應將 fallback 資源解壓縮的位置：主要元件或附屬元件。</span><span class="sxs-lookup"><span data-stu-id="9f829-218">The constructor of the <xref:System.Resources.NeutralResourcesLanguageAttribute> class has two signatures, one that takes an <xref:System.Resources.UltimateResourceFallbackLocation> parameter to specify the location where the <xref:System.Resources.ResourceManager> should extract the fallback resources: main assembly or satellite assembly.</span></span> <span data-ttu-id="9f829-219">下列範例顯示如何使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="9f829-219">The following example shows how to use the attribute.</span></span> <span data-ttu-id="9f829-220">對於最終的回溯位置，程式碼會讓 <xref:System.Resources.ResourceManager> 在目前執行之元件的目錄 "de" 子目錄中尋找資源。</span><span class="sxs-lookup"><span data-stu-id="9f829-220">For the ultimate fallback location, the code causes the <xref:System.Resources.ResourceManager> to look for the resources in the "de" subdirectory of the directory of the currently executing assembly.</span></span>

```csharp
[assembly: NeutralResourcesLanguageAttribute(
    "de" , UltimateResourceFallbackLocation.Satellite)]
```

## <a name="see-also"></a><span data-ttu-id="9f829-221">請參閱</span><span class="sxs-lookup"><span data-stu-id="9f829-221">See also</span></span>

- [<span data-ttu-id="9f829-222">WPF 全球化和當地語系化概觀</span><span class="sxs-lookup"><span data-stu-id="9f829-222">WPF Globalization and Localization Overview</span></span>](wpf-globalization-and-localization-overview.md)
