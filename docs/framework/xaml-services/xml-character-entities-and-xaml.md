---
title: "XML 字元實體和 XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- '&'
- '&amp'
- '&gt'
- '&lt'
helpviewer_keywords:
- XAML [XAML Services], special characters
- ampersand (&) [XAML Services]
- special characters [XAML Services]
- apostrophe (') [XAML Services]
- greater-than (>) character [XAML Services]
- XAML [XAML Services], quotation mark (")
- XAML [XAML Services], apostrophe (')
- '& (ampersand) [XAML Services]'
- XAML [XAML Services], & (ampersand)
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- less-than (<) character [XAML Services]
ms.assetid: 6896d0ce-74f7-420a-9ab4-de9bbf390e8d
caps.latest.revision: "23"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 5973c67b26e07bba69383cc625ff34493d825a41
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="xml-character-entities-and-xaml"></a><span data-ttu-id="9edff-102">XML 字元實體和 XAML</span><span class="sxs-lookup"><span data-stu-id="9edff-102">XML Character Entities and XAML</span></span>
<span data-ttu-id="9edff-103">XAML 使用 XML 中針對特殊字元定義的字元實體。</span><span class="sxs-lookup"><span data-stu-id="9edff-103">XAML uses character entities defined in XML for special characters.</span></span> <span data-ttu-id="9edff-104">本主題說明一些特定字元實體，以及針對 XAML 中其他 XML 概念的一般考量。</span><span class="sxs-lookup"><span data-stu-id="9edff-104">This topic describes some specific character entities and general considerations for other XML concepts in XAML.</span></span>  
  
<a name="character_entities_and_escaping_issues_that_are_unique_to_xaml"></a>   
## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a><span data-ttu-id="9edff-105">XAML 特有的字元實體和逸出問題</span><span class="sxs-lookup"><span data-stu-id="9edff-105">Character Entities and Escaping Issues That Are Unique to XAML</span></span>  
 <span data-ttu-id="9edff-106">XAML 標記通常會使用 XML 中定義的相同字元實體和逸出序列。</span><span class="sxs-lookup"><span data-stu-id="9edff-106">XAML markup typically uses the same character entities and escape sequences that are defined in XML.</span></span>  
  
 <span data-ttu-id="9edff-107">主要的差異在於大括號 ({ 和 }) 在 XAML 中具有顯著意義，因為這些字元會通知 XAML 處理器，包含在大括號內的字元序列必須解譯為標記延伸。</span><span class="sxs-lookup"><span data-stu-id="9edff-107">The main exception is that braces ({ and }) have significance in XAML because these characters inform a XAML processor that a character sequence enclosed by braces must be interpreted as a markup extension.</span></span> <span data-ttu-id="9edff-108">如需標記延伸的詳細資訊，請參閱 [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9edff-108">For more information about markup extensions, see [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).</span></span>  
  
 <span data-ttu-id="9edff-109">不過，您還是可以使用 XAML (而不是 XML) 特有的逸出序列，將大括號顯示為常值字元。</span><span class="sxs-lookup"><span data-stu-id="9edff-109">However, you can still display the braces as literal characters by using an escape sequence that is particular to XAML instead of XML.</span></span> <span data-ttu-id="9edff-110">如需詳細資訊，請參閱[{} 逸出序列的標記延伸](escape-sequence-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="9edff-110">For more information, see [{} Escape Sequence - Markup Extension](escape-sequence-markup-extension.md).</span></span>  
  
 <span data-ttu-id="9edff-111">請注意，反斜線 (\\) 處理做為字串時，不需要逸出序列。</span><span class="sxs-lookup"><span data-stu-id="9edff-111">Note that a backslash (\\) does not require an escape sequence when it is handled as a string.</span></span>  
  
<a name="xml_character_entities"></a>   
## <a name="xml-character-entities"></a><span data-ttu-id="9edff-112">XML 字元實體</span><span class="sxs-lookup"><span data-stu-id="9edff-112">XML Character Entities</span></span>  
 <span data-ttu-id="9edff-113">如前所述，通常用於撰寫 XAML 標記的大多數字元實體和逸出序列都是由 XML 定義的。</span><span class="sxs-lookup"><span data-stu-id="9edff-113">As mentioned previously, most character entities and escape sequences that are typically used to write XAML markup are defined by XML.</span></span> <span data-ttu-id="9edff-114">本主題並未提供這些實體的完整清單，您可以在外部文件 (例如 XML 規格) 中找到這些實體的詳細參考資料。</span><span class="sxs-lookup"><span data-stu-id="9edff-114">This topic does not provide the complete list of these entities; a detailed reference for the entities can be found in external documentation, such as in XML specifications.</span></span> <span data-ttu-id="9edff-115">不過，為了方便起見，本主題會列出 XAML 標記中常用的 XML 字元實體。</span><span class="sxs-lookup"><span data-stu-id="9edff-115">However, for convenience, this topic lists some of the specific XML character entities that are typically used in XAML markup.</span></span>  
  
|<span data-ttu-id="9edff-116">字元</span><span class="sxs-lookup"><span data-stu-id="9edff-116">Character</span></span>|<span data-ttu-id="9edff-117">實體</span><span class="sxs-lookup"><span data-stu-id="9edff-117">Entity</span></span>|<span data-ttu-id="9edff-118">備註</span><span class="sxs-lookup"><span data-stu-id="9edff-118">Notes</span></span>|  
|---------------|------------|-----------|  
|<span data-ttu-id="9edff-119">& (連字號)</span><span class="sxs-lookup"><span data-stu-id="9edff-119">& (ampersand)</span></span>|&amp;|<span data-ttu-id="9edff-120">必須用於屬性值和項目內容。</span><span class="sxs-lookup"><span data-stu-id="9edff-120">Must be used both for attribute values and for content of an element.</span></span>|  
|<span data-ttu-id="9edff-121">> (大於字元)</span><span class="sxs-lookup"><span data-stu-id="9edff-121">> (greater-than character)</span></span>|&gt;|<span data-ttu-id="9edff-122">必須用於屬性值，但可接受 > 做為項目內容，只要前面沒有 < 即可。</span><span class="sxs-lookup"><span data-stu-id="9edff-122">Must be used for an attribute value, but > is acceptable as the content of an element as long as < does not precede it.</span></span>|  
|<span data-ttu-id="9edff-123">< (小於字元)</span><span class="sxs-lookup"><span data-stu-id="9edff-123">< (less-than character)</span></span>|&lt;|<span data-ttu-id="9edff-124">必須用於屬性值，但\<是只要項目的內容可接受 > 未遵循。</span><span class="sxs-lookup"><span data-stu-id="9edff-124">Must be used for an attribute value, but \< is acceptable as the content of an element as long as > does not follow it.</span></span>|  
|<span data-ttu-id="9edff-125">" (雙引號)</span><span class="sxs-lookup"><span data-stu-id="9edff-125">" (straight quotation mark)</span></span>|&quot;|<span data-ttu-id="9edff-126">必須用於屬性值，但可接受雙引號 (") 做為項目內容。</span><span class="sxs-lookup"><span data-stu-id="9edff-126">Must be used for an attribute value, but a straight quotation mark (") is acceptable as the content of an element.</span></span> <span data-ttu-id="9edff-127">請注意，屬性值可以使用單引號 (') 或雙引號 ('') 括住；先出現的字元會定義括住的屬性值，而另一種引號則可以接著用來括住值內的常值。</span><span class="sxs-lookup"><span data-stu-id="9edff-127">Note that attribute values may be enclosed either by a single straight quotation mark (') or by a straight quotation mark ("); whichever character appears first defines the attribute value enclosure, and the alternative quote can then be used as a literal within the value.</span></span>|  
|<span data-ttu-id="9edff-128">' (單引號)</span><span class="sxs-lookup"><span data-stu-id="9edff-128">' (single straight quotation mark)</span></span>|&apos;|<span data-ttu-id="9edff-129">必須用於屬性值，但可接受單引號 (') 做為項目內容。</span><span class="sxs-lookup"><span data-stu-id="9edff-129">Must be used for an attribute value, but a single straight quotation mark (') is acceptable as the content of an element.</span></span> <span data-ttu-id="9edff-130">請注意，屬性值可以使用單引號 (') 或雙引號 ('') 括住；先出現的字元會定義括住的屬性值，而另一種引號則可以接著用來括住值內的常值。</span><span class="sxs-lookup"><span data-stu-id="9edff-130">Note that attribute values may be enclosed either by a single straight quotation mark (') or by a straight quotation mark ("); whichever character appears first defines the attribute value enclosure, and the alternative quote can then be used as a literal within the value.</span></span>|  
|<span data-ttu-id="9edff-131">(數字字元對應)</span><span class="sxs-lookup"><span data-stu-id="9edff-131">(numeric character mappings)</span></span>|<span data-ttu-id="9edff-132">&#*[整數]*; 或 （& s) #x*[十六進位]*;</span><span class="sxs-lookup"><span data-stu-id="9edff-132">&#*[integer]*; or &#x*[hex]*;</span></span>|<span data-ttu-id="9edff-133">XAML 支援將數字字元對應至使用中的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="9edff-133">XAML supports numeric character mappings into the encoding that is active.</span></span>|  
|<span data-ttu-id="9edff-134">(不分行空格)</span><span class="sxs-lookup"><span data-stu-id="9edff-134">(nonbreaking space)</span></span>|<span data-ttu-id="9edff-135">&\#160;（假設 utf-8 編碼）</span><span class="sxs-lookup"><span data-stu-id="9edff-135">&\#160; (assuming UTF-8 encoding)</span></span>|<span data-ttu-id="9edff-136">對於非固定格式文件項目，或是接受文字的項目 (例如 WPF <xref:System.Windows.Controls.TextBox>)，即使 `xml:space="default"`，也不會在標記外部將不分行空格標準化。</span><span class="sxs-lookup"><span data-stu-id="9edff-136">For flow document elements, or elements that take text such as the WPF <xref:System.Windows.Controls.TextBox>, nonbreaking spaces are not normalized out of the markup, even for `xml:space="default"`.</span></span> <span data-ttu-id="9edff-137">(如需詳細資訊，請參閱[XAML 中的空白字元處理](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)。)</span><span class="sxs-lookup"><span data-stu-id="9edff-137">(For more information, see [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).)</span></span>|  
  
<a name="xml_comment_format"></a>   
## <a name="xml-comment-format"></a><span data-ttu-id="9edff-138">XML 註解格式</span><span class="sxs-lookup"><span data-stu-id="9edff-138">XML Comment Format</span></span>  
 <span data-ttu-id="9edff-139">XAML 使用 XML 註解格式：註解的開頭為 `<!--`，註解的結尾為 `-->,`，而且在註解內不能出現 `--` 序列。</span><span class="sxs-lookup"><span data-stu-id="9edff-139">XAML uses the XML comment format: the start of the comment is `<!--`, the end of comment is `-->,` and the sequence `--` must not occur within the comment.</span></span>  
  
<a name="xml_processing_instructions"></a>   
## <a name="xml-processing-instructions"></a><span data-ttu-id="9edff-140">XML 處理指令</span><span class="sxs-lookup"><span data-stu-id="9edff-140">XML Processing Instructions</span></span>  
 <span data-ttu-id="9edff-141">XAML 會根據 XML 規格來處理 XML 處理指令，該規格表示必須將指令傳遞通過。</span><span class="sxs-lookup"><span data-stu-id="9edff-141">XAML handles XML processing instructions according to XML specifications, which state that the instructions must be passed through.</span></span> <span data-ttu-id="9edff-142">.NET Framework XAML 服務中的 XAML 處理不使用任何處理指示。</span><span class="sxs-lookup"><span data-stu-id="9edff-142">XAML processing in .NET Framework XAML Services  does not use any processing instructions.</span></span> <span data-ttu-id="9edff-143">其他使用 XAML 的現有架構，也都不會使用 XAML 的處理指令。</span><span class="sxs-lookup"><span data-stu-id="9edff-143">Other existing frameworks that use XAML also do not use processing instructions from XAML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9edff-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9edff-144">See Also</span></span>  
 [<span data-ttu-id="9edff-145">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="9edff-145">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="9edff-146">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="9edff-146">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="9edff-147">XamlName 文法</span><span class="sxs-lookup"><span data-stu-id="9edff-147">XamlName Grammar</span></span>](../../../docs/framework/xaml-services/xamlname-grammar.md)  
 [<span data-ttu-id="9edff-148">XAML 中的泛空白字元處理</span><span class="sxs-lookup"><span data-stu-id="9edff-148">Whitespace Processing in XAML</span></span>](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)
