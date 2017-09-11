---
title: "屬性清單 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: dc1c456c71efb3cc6e60a8fdc77384e65975f110
ms.openlocfilehash: 6aea239e2e0d8a266b8eb6ba2876fb109e077c46
ms.contentlocale: zh-tw
ms.lasthandoff: 05/15/2017

---
# <a name="attribute-list-visual-basic"></a><span data-ttu-id="1cd60-102">屬性清單 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1cd60-102">Attribute List (Visual Basic)</span></span>
<span data-ttu-id="1cd60-103">指定要套用至宣告的程式設計項目屬性。</span><span class="sxs-lookup"><span data-stu-id="1cd60-103">Specifies the attributes to be applied to a declared programming element.</span></span> <span data-ttu-id="1cd60-104">以逗號分隔多個屬性。</span><span class="sxs-lookup"><span data-stu-id="1cd60-104">Multiple attributes are separated by commas.</span></span> <span data-ttu-id="1cd60-105">以下是一個屬性的語法。</span><span class="sxs-lookup"><span data-stu-id="1cd60-105">Following is the syntax for one attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cd60-106">語法</span><span class="sxs-lookup"><span data-stu-id="1cd60-106">Syntax</span></span>  
  
```  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="1cd60-107">組件</span><span class="sxs-lookup"><span data-stu-id="1cd60-107">Parts</span></span>  
 `attributemodifier`  
 <span data-ttu-id="1cd60-108">所需的原始程式檔的開頭套用的屬性。</span><span class="sxs-lookup"><span data-stu-id="1cd60-108">Required for attributes applied at the beginning of a source file.</span></span> <span data-ttu-id="1cd60-109">可以是[組件](../../../visual-basic/language-reference/modifiers/assembly.md)或[模組](../../../visual-basic/language-reference/modifiers/module-keyword.md)。</span><span class="sxs-lookup"><span data-stu-id="1cd60-109">Can be [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) or [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md).</span></span>  
  
 `attributename`  
 <span data-ttu-id="1cd60-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="1cd60-110">Required.</span></span> <span data-ttu-id="1cd60-111">屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="1cd60-111">Name of the attribute.</span></span>  
  
 `attributearguments`  
 <span data-ttu-id="1cd60-112">選擇項。</span><span class="sxs-lookup"><span data-stu-id="1cd60-112">Optional.</span></span> <span data-ttu-id="1cd60-113">這個屬性的位置引數的清單。</span><span class="sxs-lookup"><span data-stu-id="1cd60-113">List of positional arguments for this attribute.</span></span> <span data-ttu-id="1cd60-114">以逗號分隔多個引數。</span><span class="sxs-lookup"><span data-stu-id="1cd60-114">Multiple arguments are separated by commas.</span></span>  
  
 `attributeinitializer`  
 <span data-ttu-id="1cd60-115">選擇項。</span><span class="sxs-lookup"><span data-stu-id="1cd60-115">Optional.</span></span> <span data-ttu-id="1cd60-116">這個屬性的變數或屬性初始設定式清單。</span><span class="sxs-lookup"><span data-stu-id="1cd60-116">List of variable or property initializers for this attribute.</span></span> <span data-ttu-id="1cd60-117">以逗號分隔多個初始設定式。</span><span class="sxs-lookup"><span data-stu-id="1cd60-117">Multiple initializers are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cd60-118">備註</span><span class="sxs-lookup"><span data-stu-id="1cd60-118">Remarks</span></span>  
 <span data-ttu-id="1cd60-119">您可以套用一個或多個屬性，大部分的程式設計項目 （類型、 程序、 屬性和其他等等）。</span><span class="sxs-lookup"><span data-stu-id="1cd60-119">You can apply one or more attributes to nearly any programming element (types, procedures, properties, and so forth).</span></span> <span data-ttu-id="1cd60-120">屬性會顯示在您的組件中繼資料，並可協助您加上註解您的程式碼，或指定如何使用特定的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="1cd60-120">Attributes appear in your assembly's metadata, and they can help you annotate your code or specify how to use a particular programming element.</span></span> <span data-ttu-id="1cd60-121">您可以套用 Visual Basic 和.NET Framework 中，所定義的屬性，而且您可以定義自己的屬性。</span><span class="sxs-lookup"><span data-stu-id="1cd60-121">You can apply attributes defined by Visual Basic and the .NET Framework, and you can define your own attributes.</span></span>  

 <span data-ttu-id="1cd60-122">如需何時使用屬性的詳細資訊，請參閱[屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="1cd60-122">For more information on when to use attributes, see [Attributes overview](../../../visual-basic/programming-guide/concepts/attributes/index.md).</span></span> <span data-ttu-id="1cd60-123">如需屬性名稱的資訊，請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="1cd60-123">For information on attribute names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="1cd60-124">規則</span><span class="sxs-lookup"><span data-stu-id="1cd60-124">Rules</span></span>  
  
-   <span data-ttu-id="1cd60-125">**放置。**</span><span class="sxs-lookup"><span data-stu-id="1cd60-125">**Placement.**</span></span> <span data-ttu-id="1cd60-126">您可以將屬性套用至大部分已宣告的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="1cd60-126">You can apply attributes to most declared programming elements.</span></span> <span data-ttu-id="1cd60-127">若要套用一或多個屬性，您將*屬性區塊*項目宣告的開頭。</span><span class="sxs-lookup"><span data-stu-id="1cd60-127">To apply one or more attributes, you place an *attribute block* at the beginning of the element declaration.</span></span> <span data-ttu-id="1cd60-128">屬性清單中的每個項目會指定您想要套用的屬性和修飾詞和您要用於屬性的這個引動過程的引數。</span><span class="sxs-lookup"><span data-stu-id="1cd60-128">Each entry in the attribute list specifies an attribute you wish to apply, and the modifier and arguments you are using for this invocation of the attribute.</span></span>  
  
-   <span data-ttu-id="1cd60-129">**角括號。**</span><span class="sxs-lookup"><span data-stu-id="1cd60-129">**Angle Brackets.**</span></span> <span data-ttu-id="1cd60-130">如果您提供的屬性清單，您必須將它括在角括弧 ("`<`"和"`>`")。</span><span class="sxs-lookup"><span data-stu-id="1cd60-130">If you supply an attribute list, you must enclose it in angle brackets ("`<`" and "`>`").</span></span>  
  
-   <span data-ttu-id="1cd60-131">**宣告的一部分。**</span><span class="sxs-lookup"><span data-stu-id="1cd60-131">**Part of the Declaration.**</span></span> <span data-ttu-id="1cd60-132">屬性必須是項目宣告，而不是個別的陳述式的一部分。</span><span class="sxs-lookup"><span data-stu-id="1cd60-132">The attribute must be part of the element declaration, not a separate statement.</span></span> <span data-ttu-id="1cd60-133">您可以使用行接續序列 (「 `_`」) 來延伸到多個原始程式行的宣告陳述式。</span><span class="sxs-lookup"><span data-stu-id="1cd60-133">You can use the line-continuation sequence (" `_`") to extend the declaration statement onto multiple source-code lines.</span></span>  
  
-   <span data-ttu-id="1cd60-134">**修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="1cd60-134">**Modifiers.**</span></span> <span data-ttu-id="1cd60-135">屬性修飾詞 (`Assembly`或`Module`) 需要在每個屬性套用至原始程式檔的開頭的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="1cd60-135">An attribute modifier (`Assembly` or `Module`) is required on every attribute applied to a programming element at the beginning of a source file.</span></span> <span data-ttu-id="1cd60-136">不允許屬性修飾詞套用至不在原始程式檔開頭的項目。</span><span class="sxs-lookup"><span data-stu-id="1cd60-136">Attribute modifiers are not allowed on attributes applied to elements that are not at the beginning of a source file.</span></span>  
  
-   <span data-ttu-id="1cd60-137">**引數。**</span><span class="sxs-lookup"><span data-stu-id="1cd60-137">**Arguments.**</span></span> <span data-ttu-id="1cd60-138">屬性的所有位置引數必須在之前的任何變數或屬性初始設定式。</span><span class="sxs-lookup"><span data-stu-id="1cd60-138">All positional arguments for an attribute must precede any variable or property initializers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cd60-139">範例</span><span class="sxs-lookup"><span data-stu-id="1cd60-139">Example</span></span>  
 <span data-ttu-id="1cd60-140">下列範例會套用<xref:System.Runtime.InteropServices.DllImportAttribute>屬性的基本架構定義`Function`程序。</xref:System.Runtime.InteropServices.DllImportAttribute></span><span class="sxs-lookup"><span data-stu-id="1cd60-140">The following example applies the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to a skeleton definition of a `Function` procedure.</span></span>  
  
 <span data-ttu-id="1cd60-141">[!code-vb[VbVbalrStatements #&1;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/attribute-list_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="1cd60-141">[!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/attribute-list_1.vb)]</span></span>  
  
 <span data-ttu-id="1cd60-142"><xref:System.Runtime.InteropServices.DllImportAttribute>表示屬性化的程序會表示 unmanaged 動態連結程式庫 (DLL) 中的進入點。</xref:System.Runtime.InteropServices.DllImportAttribute></span><span class="sxs-lookup"><span data-stu-id="1cd60-142"><xref:System.Runtime.InteropServices.DllImportAttribute> indicates that the attributed procedure represents an entry point in an unmanaged dynamic-link library (DLL).</span></span> <span data-ttu-id="1cd60-143">屬性會提供 DLL 名稱做為位置引數和變數初始設定式的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="1cd60-143">The attribute supplies the DLL name as a positional argument and the other information as variable initializers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cd60-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cd60-144">See Also</span></span>  
 <span data-ttu-id="1cd60-145">[組件](../../../visual-basic/language-reference/modifiers/assembly.md) </span><span class="sxs-lookup"><span data-stu-id="1cd60-145">[Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) </span></span>  
<span data-ttu-id="1cd60-146"> [模組\<關鍵字 >](../../../visual-basic/language-reference/modifiers/module-keyword.md) </span><span class="sxs-lookup"><span data-stu-id="1cd60-146"> [Module \<keyword>](../../../visual-basic/language-reference/modifiers/module-keyword.md) </span></span>  
<span data-ttu-id="1cd60-147"> [屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md) </span><span class="sxs-lookup"><span data-stu-id="1cd60-147"> [Attributes overview](../../../visual-basic/programming-guide/concepts/attributes/index.md) </span></span>  
<span data-ttu-id="1cd60-148"> [如何：在程式碼內中斷和合併陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)</span><span class="sxs-lookup"><span data-stu-id="1cd60-148"> [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)</span></span>

