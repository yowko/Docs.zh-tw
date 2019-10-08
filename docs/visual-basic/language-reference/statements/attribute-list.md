---
title: 屬性清單 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: 771757afe214919649e13fda3990e1154be8e1e1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004521"
---
# <a name="attribute-list-visual-basic"></a><span data-ttu-id="3372e-102">屬性清單 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3372e-102">Attribute List (Visual Basic)</span></span>
<span data-ttu-id="3372e-103">指定要套用至宣告的程式設計項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="3372e-103">Specifies the attributes to be applied to a declared programming element.</span></span> <span data-ttu-id="3372e-104">以逗號分隔多個屬性。</span><span class="sxs-lookup"><span data-stu-id="3372e-104">Multiple attributes are separated by commas.</span></span> <span data-ttu-id="3372e-105">以下是一個屬性的語法。</span><span class="sxs-lookup"><span data-stu-id="3372e-105">Following is the syntax for one attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3372e-106">語法</span><span class="sxs-lookup"><span data-stu-id="3372e-106">Syntax</span></span>  
  
```vb  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="3372e-107">組件</span><span class="sxs-lookup"><span data-stu-id="3372e-107">Parts</span></span>  
|||
|---|---|
|`attributemodifier`|<span data-ttu-id="3372e-108">在原始程式檔開頭套用之屬性的必要項。</span><span class="sxs-lookup"><span data-stu-id="3372e-108">Required for attributes applied at the beginning of a source file.</span></span> <span data-ttu-id="3372e-109">可以是[元件](../../../visual-basic/language-reference/modifiers/assembly.md)或[模組](../../../visual-basic/language-reference/modifiers/module-keyword.md)。</span><span class="sxs-lookup"><span data-stu-id="3372e-109">Can be [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) or [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md).</span></span>|
|`attributename`| <span data-ttu-id="3372e-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="3372e-110">Required.</span></span> <span data-ttu-id="3372e-111">屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="3372e-111">Name of the attribute.</span></span>|
|`attributearguments`|<span data-ttu-id="3372e-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3372e-112">Optional.</span></span> <span data-ttu-id="3372e-113">這個屬性的位置引數清單。</span><span class="sxs-lookup"><span data-stu-id="3372e-113">List of positional arguments for this attribute.</span></span> <span data-ttu-id="3372e-114">以逗號分隔多個引數。</span><span class="sxs-lookup"><span data-stu-id="3372e-114">Multiple arguments are separated by commas.</span></span>|
|`attributeinitializer`|<span data-ttu-id="3372e-115">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3372e-115">Optional.</span></span> <span data-ttu-id="3372e-116">這個屬性的變數或屬性初始化運算式清單。</span><span class="sxs-lookup"><span data-stu-id="3372e-116">List of variable or property initializers for this attribute.</span></span> <span data-ttu-id="3372e-117">多個初始化運算式會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="3372e-117">Multiple initializers are separated by commas.</span></span>|
  
## <a name="remarks"></a><span data-ttu-id="3372e-118">備註</span><span class="sxs-lookup"><span data-stu-id="3372e-118">Remarks</span></span>  
 <span data-ttu-id="3372e-119">您可以將一個或多個屬性套用至幾乎任何程式設計項目（類型、程式、屬性等等）。</span><span class="sxs-lookup"><span data-stu-id="3372e-119">You can apply one or more attributes to nearly any programming element (types, procedures, properties, and so forth).</span></span> <span data-ttu-id="3372e-120">屬性會出現在元件的中繼資料中，並可協助您標注程式碼，或指定如何使用特定的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="3372e-120">Attributes appear in your assembly's metadata, and they can help you annotate your code or specify how to use a particular programming element.</span></span> <span data-ttu-id="3372e-121">您可以套用 Visual Basic 和 .NET Framework 所定義的屬性，而且您可以定義自己的屬性。</span><span class="sxs-lookup"><span data-stu-id="3372e-121">You can apply attributes defined by Visual Basic and the .NET Framework, and you can define your own attributes.</span></span>  

 <span data-ttu-id="3372e-122">如需何時使用屬性的詳細資訊，請參閱[屬性總覽](../../../visual-basic/programming-guide/concepts/attributes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="3372e-122">For more information on when to use attributes, see [Attributes overview](../../../visual-basic/programming-guide/concepts/attributes/index.md).</span></span> <span data-ttu-id="3372e-123">如需屬性名稱的資訊，請參閱宣告的[元素名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="3372e-123">For information on attribute names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="3372e-124">規則</span><span class="sxs-lookup"><span data-stu-id="3372e-124">Rules</span></span>  
  
- <span data-ttu-id="3372e-125">**粘貼.**</span><span class="sxs-lookup"><span data-stu-id="3372e-125">**Placement.**</span></span> <span data-ttu-id="3372e-126">您可以將屬性（attribute）套用至大部分宣告的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="3372e-126">You can apply attributes to most declared programming elements.</span></span> <span data-ttu-id="3372e-127">若要套用一個或多個屬性，您可以將*屬性區塊*放在元素宣告的開頭。</span><span class="sxs-lookup"><span data-stu-id="3372e-127">To apply one or more attributes, you place an *attribute block* at the beginning of the element declaration.</span></span> <span data-ttu-id="3372e-128">[屬性] 清單中的每個專案會指定您想要套用的屬性，以及您在此屬性調用中使用的修飾詞和引數。</span><span class="sxs-lookup"><span data-stu-id="3372e-128">Each entry in the attribute list specifies an attribute you wish to apply, and the modifier and arguments you are using for this invocation of the attribute.</span></span>  
  
- <span data-ttu-id="3372e-129">**角括弧。**</span><span class="sxs-lookup"><span data-stu-id="3372e-129">**Angle Brackets.**</span></span> <span data-ttu-id="3372e-130">如果您提供屬性清單，則必須將它括在角括弧中（"`<`" 和 "`>`"）。</span><span class="sxs-lookup"><span data-stu-id="3372e-130">If you supply an attribute list, you must enclose it in angle brackets ("`<`" and "`>`").</span></span>  
  
- <span data-ttu-id="3372e-131">**宣告的一部分。**</span><span class="sxs-lookup"><span data-stu-id="3372e-131">**Part of the Declaration.**</span></span> <span data-ttu-id="3372e-132">屬性必須是元素宣告的一部分，而不是個別的語句。</span><span class="sxs-lookup"><span data-stu-id="3372e-132">The attribute must be part of the element declaration, not a separate statement.</span></span> <span data-ttu-id="3372e-133">您可以使用行接續序列（"`_`"），將宣告語句擴充到多個源程式碼。</span><span class="sxs-lookup"><span data-stu-id="3372e-133">You can use the line-continuation sequence (" `_`") to extend the declaration statement onto multiple source-code lines.</span></span>  
  
- <span data-ttu-id="3372e-134">**修改.**</span><span class="sxs-lookup"><span data-stu-id="3372e-134">**Modifiers.**</span></span> <span data-ttu-id="3372e-135">在原始程式檔開頭套用至程式設計專案的每個屬性上，都需要屬性修飾詞（`Assembly` 或 `Module`）。</span><span class="sxs-lookup"><span data-stu-id="3372e-135">An attribute modifier (`Assembly` or `Module`) is required on every attribute applied to a programming element at the beginning of a source file.</span></span> <span data-ttu-id="3372e-136">屬性修飾詞不能用於套用至不在原始程式檔開頭之元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="3372e-136">Attribute modifiers are not allowed on attributes applied to elements that are not at the beginning of a source file.</span></span>  
  
- <span data-ttu-id="3372e-137">**參量.**</span><span class="sxs-lookup"><span data-stu-id="3372e-137">**Arguments.**</span></span> <span data-ttu-id="3372e-138">屬性的所有位置引數都必須在任何變數或屬性初始化運算式之前。</span><span class="sxs-lookup"><span data-stu-id="3372e-138">All positional arguments for an attribute must precede any variable or property initializers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3372e-139">範例</span><span class="sxs-lookup"><span data-stu-id="3372e-139">Example</span></span>  
 <span data-ttu-id="3372e-140">下列範例會將 <xref:System.Runtime.InteropServices.DllImportAttribute> 屬性套用至 @no__t 1 程式的基本架構定義。</span><span class="sxs-lookup"><span data-stu-id="3372e-140">The following example applies the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to a skeleton definition of a `Function` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]  
  
 <span data-ttu-id="3372e-141"><xref:System.Runtime.InteropServices.DllImportAttribute> 表示屬性化程式代表非受控動態連結程式庫（DLL）中的進入點。</span><span class="sxs-lookup"><span data-stu-id="3372e-141"><xref:System.Runtime.InteropServices.DllImportAttribute> indicates that the attributed procedure represents an entry point in an unmanaged dynamic-link library (DLL).</span></span> <span data-ttu-id="3372e-142">屬性會提供 DLL 名稱做為位置引數，並將其他資訊當做變數初始化運算式。</span><span class="sxs-lookup"><span data-stu-id="3372e-142">The attribute supplies the DLL name as a positional argument and the other information as variable initializers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3372e-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3372e-143">See also</span></span>

- [<span data-ttu-id="3372e-144">Assembly</span><span class="sxs-lookup"><span data-stu-id="3372e-144">Assembly</span></span>](../../../visual-basic/language-reference/modifiers/assembly.md)
- [<span data-ttu-id="3372e-145">Module \<鍵字></span><span class="sxs-lookup"><span data-stu-id="3372e-145">Module \<keyword></span></span>](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [<span data-ttu-id="3372e-146">屬性概觀</span><span class="sxs-lookup"><span data-stu-id="3372e-146">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="3372e-147">如何：在程式碼內中斷和合併陳述式</span><span class="sxs-lookup"><span data-stu-id="3372e-147">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
