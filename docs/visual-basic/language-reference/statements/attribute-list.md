---
title: 屬性清單 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: 35d031722a5eddd6adce5e32df62b86c500d305b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604066"
---
# <a name="attribute-list-visual-basic"></a><span data-ttu-id="3393b-102">屬性清單 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3393b-102">Attribute List (Visual Basic)</span></span>
<span data-ttu-id="3393b-103">指定要套用至程式設計項目宣告的屬性。</span><span class="sxs-lookup"><span data-stu-id="3393b-103">Specifies the attributes to be applied to a declared programming element.</span></span> <span data-ttu-id="3393b-104">以逗號分隔多個屬性。</span><span class="sxs-lookup"><span data-stu-id="3393b-104">Multiple attributes are separated by commas.</span></span> <span data-ttu-id="3393b-105">以下是一個屬性的語法。</span><span class="sxs-lookup"><span data-stu-id="3393b-105">Following is the syntax for one attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3393b-106">語法</span><span class="sxs-lookup"><span data-stu-id="3393b-106">Syntax</span></span>  
  
```  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="3393b-107">組件</span><span class="sxs-lookup"><span data-stu-id="3393b-107">Parts</span></span>  
 `attributemodifier`  
 <span data-ttu-id="3393b-108">需要套用的原始程式檔開頭的屬性。</span><span class="sxs-lookup"><span data-stu-id="3393b-108">Required for attributes applied at the beginning of a source file.</span></span> <span data-ttu-id="3393b-109">可以是[組件](../../../visual-basic/language-reference/modifiers/assembly.md)或[模組](../../../visual-basic/language-reference/modifiers/module-keyword.md)。</span><span class="sxs-lookup"><span data-stu-id="3393b-109">Can be [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) or [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md).</span></span>  
  
 `attributename`  
 <span data-ttu-id="3393b-110">必要。</span><span class="sxs-lookup"><span data-stu-id="3393b-110">Required.</span></span> <span data-ttu-id="3393b-111">屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="3393b-111">Name of the attribute.</span></span>  
  
 `attributearguments`  
 <span data-ttu-id="3393b-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3393b-112">Optional.</span></span> <span data-ttu-id="3393b-113">這個屬性的位置引數的清單。</span><span class="sxs-lookup"><span data-stu-id="3393b-113">List of positional arguments for this attribute.</span></span> <span data-ttu-id="3393b-114">以逗號分隔多個引數。</span><span class="sxs-lookup"><span data-stu-id="3393b-114">Multiple arguments are separated by commas.</span></span>  
  
 `attributeinitializer`  
 <span data-ttu-id="3393b-115">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3393b-115">Optional.</span></span> <span data-ttu-id="3393b-116">這個屬性的變數或屬性初始設定式清單。</span><span class="sxs-lookup"><span data-stu-id="3393b-116">List of variable or property initializers for this attribute.</span></span> <span data-ttu-id="3393b-117">以逗號分隔多個初始設定式。</span><span class="sxs-lookup"><span data-stu-id="3393b-117">Multiple initializers are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3393b-118">備註</span><span class="sxs-lookup"><span data-stu-id="3393b-118">Remarks</span></span>  
 <span data-ttu-id="3393b-119">您可以將一或多個屬性套用至幾乎任何程式設計項目 （類型、 程序、 屬性和其他等等）。</span><span class="sxs-lookup"><span data-stu-id="3393b-119">You can apply one or more attributes to nearly any programming element (types, procedures, properties, and so forth).</span></span> <span data-ttu-id="3393b-120">屬性出現在組件的中繼資料，而且它們可以協助您標註程式碼，或指定如何使用特定的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="3393b-120">Attributes appear in your assembly's metadata, and they can help you annotate your code or specify how to use a particular programming element.</span></span> <span data-ttu-id="3393b-121">您可以套用 Visual Basic 和.NET Framework 中，所定義的屬性，而且您可以定義您自己的屬性。</span><span class="sxs-lookup"><span data-stu-id="3393b-121">You can apply attributes defined by Visual Basic and the .NET Framework, and you can define your own attributes.</span></span>  

 <span data-ttu-id="3393b-122">如需何時使用屬性的詳細資訊，請參閱[屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="3393b-122">For more information on when to use attributes, see [Attributes overview](../../../visual-basic/programming-guide/concepts/attributes/index.md).</span></span> <span data-ttu-id="3393b-123">如需屬性名稱的資訊，請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="3393b-123">For information on attribute names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="3393b-124">規則</span><span class="sxs-lookup"><span data-stu-id="3393b-124">Rules</span></span>  
  
-   <span data-ttu-id="3393b-125">**放置。**</span><span class="sxs-lookup"><span data-stu-id="3393b-125">**Placement.**</span></span> <span data-ttu-id="3393b-126">您可以將屬性套用至大部分已宣告的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="3393b-126">You can apply attributes to most declared programming elements.</span></span> <span data-ttu-id="3393b-127">若要套用一個或多個屬性，您將*屬性區塊*項目宣告的開頭。</span><span class="sxs-lookup"><span data-stu-id="3393b-127">To apply one or more attributes, you place an *attribute block* at the beginning of the element declaration.</span></span> <span data-ttu-id="3393b-128">在屬性清單中的每個項目會指定您想要套用的屬性的修飾詞和您使用這個引動過程屬性的引數。</span><span class="sxs-lookup"><span data-stu-id="3393b-128">Each entry in the attribute list specifies an attribute you wish to apply, and the modifier and arguments you are using for this invocation of the attribute.</span></span>  
  
-   <span data-ttu-id="3393b-129">**角括號。**</span><span class="sxs-lookup"><span data-stu-id="3393b-129">**Angle Brackets.**</span></span> <span data-ttu-id="3393b-130">如果您提供的屬性清單時，您必須將它括在角括號 ("`<`"和"`>`")。</span><span class="sxs-lookup"><span data-stu-id="3393b-130">If you supply an attribute list, you must enclose it in angle brackets ("`<`" and "`>`").</span></span>  
  
-   <span data-ttu-id="3393b-131">**宣告的一部分。**</span><span class="sxs-lookup"><span data-stu-id="3393b-131">**Part of the Declaration.**</span></span> <span data-ttu-id="3393b-132">屬性必須是項目宣告，而不是個別的陳述式的一部分。</span><span class="sxs-lookup"><span data-stu-id="3393b-132">The attribute must be part of the element declaration, not a separate statement.</span></span> <span data-ttu-id="3393b-133">您可以使用行接續序列 (" `_`」) 來擴充宣告陳述式分成多個原始程式行。</span><span class="sxs-lookup"><span data-stu-id="3393b-133">You can use the line-continuation sequence (" `_`") to extend the declaration statement onto multiple source-code lines.</span></span>  
  
-   <span data-ttu-id="3393b-134">**修飾詞。**</span><span class="sxs-lookup"><span data-stu-id="3393b-134">**Modifiers.**</span></span> <span data-ttu-id="3393b-135">屬性修飾詞 (`Assembly`或`Module`) 需要在每個套用至程式設計項目在原始程式檔開頭的屬性。</span><span class="sxs-lookup"><span data-stu-id="3393b-135">An attribute modifier (`Assembly` or `Module`) is required on every attribute applied to a programming element at the beginning of a source file.</span></span> <span data-ttu-id="3393b-136">在屬性套用至不在原始程式檔開頭的項目上不允許屬性修飾詞。</span><span class="sxs-lookup"><span data-stu-id="3393b-136">Attribute modifiers are not allowed on attributes applied to elements that are not at the beginning of a source file.</span></span>  
  
-   <span data-ttu-id="3393b-137">**引數。**</span><span class="sxs-lookup"><span data-stu-id="3393b-137">**Arguments.**</span></span> <span data-ttu-id="3393b-138">屬性的所有位置引數必須在前面的任何變數或屬性初始設定式。</span><span class="sxs-lookup"><span data-stu-id="3393b-138">All positional arguments for an attribute must precede any variable or property initializers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3393b-139">範例</span><span class="sxs-lookup"><span data-stu-id="3393b-139">Example</span></span>  
 <span data-ttu-id="3393b-140">下列範例會套用<xref:System.Runtime.InteropServices.DllImportAttribute>屬性的基本架構定義`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="3393b-140">The following example applies the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to a skeleton definition of a `Function` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/attribute-list_1.vb)]  
  
 <span data-ttu-id="3393b-141"><xref:System.Runtime.InteropServices.DllImportAttribute> 表示屬性化的程序會表示 unmanaged 動態連結程式庫 (DLL) 中的進入點。</span><span class="sxs-lookup"><span data-stu-id="3393b-141"><xref:System.Runtime.InteropServices.DllImportAttribute> indicates that the attributed procedure represents an entry point in an unmanaged dynamic-link library (DLL).</span></span> <span data-ttu-id="3393b-142">屬性會提供 DLL 名稱做為位置的引數和變數初始設定式的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="3393b-142">The attribute supplies the DLL name as a positional argument and the other information as variable initializers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3393b-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3393b-143">See Also</span></span>  
 [<span data-ttu-id="3393b-144">Assembly</span><span class="sxs-lookup"><span data-stu-id="3393b-144">Assembly</span></span>](../../../visual-basic/language-reference/modifiers/assembly.md)  
 [<span data-ttu-id="3393b-145">Module \<鍵字></span><span class="sxs-lookup"><span data-stu-id="3393b-145">Module \<keyword></span></span>](../../../visual-basic/language-reference/modifiers/module-keyword.md)  
 [<span data-ttu-id="3393b-146">屬性概觀</span><span class="sxs-lookup"><span data-stu-id="3393b-146">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="3393b-147">操作說明：在程式碼內中斷和合併陳述式</span><span class="sxs-lookup"><span data-stu-id="3393b-147">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
