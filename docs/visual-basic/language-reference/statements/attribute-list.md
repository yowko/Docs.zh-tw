---
title: 屬性清單
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: f2400334182d373ea49c130fd17bc4f9943248d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408441"
---
# <a name="attribute-list-visual-basic"></a><span data-ttu-id="5a8cb-102">屬性清單 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a8cb-102">Attribute List (Visual Basic)</span></span>
<span data-ttu-id="5a8cb-103">指定要套用至宣告的程式設計項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-103">Specifies the attributes to be applied to a declared programming element.</span></span> <span data-ttu-id="5a8cb-104">以逗號分隔多個屬性。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-104">Multiple attributes are separated by commas.</span></span> <span data-ttu-id="5a8cb-105">以下是一個屬性的語法。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-105">Following is the syntax for one attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a8cb-106">語法</span><span class="sxs-lookup"><span data-stu-id="5a8cb-106">Syntax</span></span>  
  
```vb  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="5a8cb-107">組件</span><span class="sxs-lookup"><span data-stu-id="5a8cb-107">Parts</span></span>  
|||
|---|---|
|`attributemodifier`|<span data-ttu-id="5a8cb-108">在原始程式檔開頭套用之屬性的必要項。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-108">Required for attributes applied at the beginning of a source file.</span></span> <span data-ttu-id="5a8cb-109">可以是[元件](../modifiers/assembly.md)或[模組](../modifiers/module-keyword.md)。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-109">Can be [Assembly](../modifiers/assembly.md) or [Module](../modifiers/module-keyword.md).</span></span>|
|`attributename`| <span data-ttu-id="5a8cb-110">必要。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-110">Required.</span></span> <span data-ttu-id="5a8cb-111">屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-111">Name of the attribute.</span></span>|
|`attributearguments`|<span data-ttu-id="5a8cb-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-112">Optional.</span></span> <span data-ttu-id="5a8cb-113">這個屬性的位置引數清單。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-113">List of positional arguments for this attribute.</span></span> <span data-ttu-id="5a8cb-114">以逗號分隔多個引數。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-114">Multiple arguments are separated by commas.</span></span>|
|`attributeinitializer`|<span data-ttu-id="5a8cb-115">選擇性。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-115">Optional.</span></span> <span data-ttu-id="5a8cb-116">這個屬性的變數或屬性初始化運算式清單。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-116">List of variable or property initializers for this attribute.</span></span> <span data-ttu-id="5a8cb-117">多個初始化運算式會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-117">Multiple initializers are separated by commas.</span></span>|
  
## <a name="remarks"></a><span data-ttu-id="5a8cb-118">備註</span><span class="sxs-lookup"><span data-stu-id="5a8cb-118">Remarks</span></span>  
 <span data-ttu-id="5a8cb-119">您可以將一個或多個屬性套用至幾乎任何程式設計項目（類型、程式、屬性等等）。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-119">You can apply one or more attributes to nearly any programming element (types, procedures, properties, and so forth).</span></span> <span data-ttu-id="5a8cb-120">屬性會出現在元件的中繼資料中，並可協助您標注程式碼，或指定如何使用特定的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-120">Attributes appear in your assembly's metadata, and they can help you annotate your code or specify how to use a particular programming element.</span></span> <span data-ttu-id="5a8cb-121">您可以套用 Visual Basic 和 .NET Framework 所定義的屬性，而且您可以定義自己的屬性。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-121">You can apply attributes defined by Visual Basic and the .NET Framework, and you can define your own attributes.</span></span>  

 <span data-ttu-id="5a8cb-122">如需何時使用屬性的詳細資訊，請參閱[屬性總覽](../../programming-guide/concepts/attributes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-122">For more information on when to use attributes, see [Attributes overview](../../programming-guide/concepts/attributes/index.md).</span></span> <span data-ttu-id="5a8cb-123">如需屬性名稱的資訊，請參閱宣告的[元素名稱](../../programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-123">For information on attribute names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="5a8cb-124">規則</span><span class="sxs-lookup"><span data-stu-id="5a8cb-124">Rules</span></span>  
  
- <span data-ttu-id="5a8cb-125">**粘貼.**</span><span class="sxs-lookup"><span data-stu-id="5a8cb-125">**Placement.**</span></span> <span data-ttu-id="5a8cb-126">您可以將屬性（attribute）套用至大部分宣告的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-126">You can apply attributes to most declared programming elements.</span></span> <span data-ttu-id="5a8cb-127">若要套用一個或多個屬性，您可以將*屬性區塊*放在元素宣告的開頭。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-127">To apply one or more attributes, you place an *attribute block* at the beginning of the element declaration.</span></span> <span data-ttu-id="5a8cb-128">[屬性] 清單中的每個專案會指定您想要套用的屬性，以及您在此屬性調用中使用的修飾詞和引數。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-128">Each entry in the attribute list specifies an attribute you wish to apply, and the modifier and arguments you are using for this invocation of the attribute.</span></span>  
  
- <span data-ttu-id="5a8cb-129">**角括弧。**</span><span class="sxs-lookup"><span data-stu-id="5a8cb-129">**Angle Brackets.**</span></span> <span data-ttu-id="5a8cb-130">如果您提供屬性清單，則必須將它括在角括弧（" `<` " 和 " `>` "）中。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-130">If you supply an attribute list, you must enclose it in angle brackets ("`<`" and "`>`").</span></span>  
  
- <span data-ttu-id="5a8cb-131">**宣告的一部分。**</span><span class="sxs-lookup"><span data-stu-id="5a8cb-131">**Part of the Declaration.**</span></span> <span data-ttu-id="5a8cb-132">屬性必須是元素宣告的一部分，而不是個別的語句。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-132">The attribute must be part of the element declaration, not a separate statement.</span></span> <span data-ttu-id="5a8cb-133">您可以使用行接續序列（" `_` "），將宣告語句擴充到多個源程式碼。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-133">You can use the line-continuation sequence (" `_`") to extend the declaration statement onto multiple source-code lines.</span></span>  
  
- <span data-ttu-id="5a8cb-134">**修改.**</span><span class="sxs-lookup"><span data-stu-id="5a8cb-134">**Modifiers.**</span></span> <span data-ttu-id="5a8cb-135">在原始程式檔 `Assembly` 開頭套用至程式設計專案的 `Module` 每個屬性上，都需要屬性修飾詞（或）。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-135">An attribute modifier (`Assembly` or `Module`) is required on every attribute applied to a programming element at the beginning of a source file.</span></span> <span data-ttu-id="5a8cb-136">屬性修飾詞不能用於套用至不在原始程式檔開頭之元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-136">Attribute modifiers are not allowed on attributes applied to elements that are not at the beginning of a source file.</span></span>  
  
- <span data-ttu-id="5a8cb-137">**參量.**</span><span class="sxs-lookup"><span data-stu-id="5a8cb-137">**Arguments.**</span></span> <span data-ttu-id="5a8cb-138">屬性的所有位置引數都必須在任何變數或屬性初始化運算式之前。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-138">All positional arguments for an attribute must precede any variable or property initializers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a8cb-139">範例</span><span class="sxs-lookup"><span data-stu-id="5a8cb-139">Example</span></span>  
 <span data-ttu-id="5a8cb-140">下列範例會將屬性套用至程式的基本架構 <xref:System.Runtime.InteropServices.DllImportAttribute> 定義 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-140">The following example applies the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to a skeleton definition of a `Function` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]  
  
 <span data-ttu-id="5a8cb-141"><xref:System.Runtime.InteropServices.DllImportAttribute>指出屬性化程式代表非受控動態連結程式庫（DLL）中的進入點。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-141"><xref:System.Runtime.InteropServices.DllImportAttribute> indicates that the attributed procedure represents an entry point in an unmanaged dynamic-link library (DLL).</span></span> <span data-ttu-id="5a8cb-142">屬性會提供 DLL 名稱做為位置引數，並將其他資訊當做變數初始化運算式。</span><span class="sxs-lookup"><span data-stu-id="5a8cb-142">The attribute supplies the DLL name as a positional argument and the other information as variable initializers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a8cb-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a8cb-143">See also</span></span>

- [<span data-ttu-id="5a8cb-144">組件</span><span class="sxs-lookup"><span data-stu-id="5a8cb-144">Assembly</span></span>](../modifiers/assembly.md)
- [<span data-ttu-id="5a8cb-145">Module\<keyword></span><span class="sxs-lookup"><span data-stu-id="5a8cb-145">Module \<keyword></span></span>](../modifiers/module-keyword.md)
- [<span data-ttu-id="5a8cb-146">屬性概觀</span><span class="sxs-lookup"><span data-stu-id="5a8cb-146">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="5a8cb-147">作法：程式碼中的 Break 及 Combine 陳述式</span><span class="sxs-lookup"><span data-stu-id="5a8cb-147">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
