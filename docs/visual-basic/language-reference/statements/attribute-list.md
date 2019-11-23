---
title: 屬性清單
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: f9332f52622551bb6b944242f71bd80f439982e9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354067"
---
# <a name="attribute-list-visual-basic"></a><span data-ttu-id="7b331-102">屬性清單 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b331-102">Attribute List (Visual Basic)</span></span>
<span data-ttu-id="7b331-103">Specifies the attributes to be applied to a declared programming element.</span><span class="sxs-lookup"><span data-stu-id="7b331-103">Specifies the attributes to be applied to a declared programming element.</span></span> <span data-ttu-id="7b331-104">以逗號分隔多個屬性。</span><span class="sxs-lookup"><span data-stu-id="7b331-104">Multiple attributes are separated by commas.</span></span> <span data-ttu-id="7b331-105">Following is the syntax for one attribute.</span><span class="sxs-lookup"><span data-stu-id="7b331-105">Following is the syntax for one attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b331-106">語法</span><span class="sxs-lookup"><span data-stu-id="7b331-106">Syntax</span></span>  
  
```vb  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="7b331-107">組件</span><span class="sxs-lookup"><span data-stu-id="7b331-107">Parts</span></span>  
|||
|---|---|
|`attributemodifier`|<span data-ttu-id="7b331-108">Required for attributes applied at the beginning of a source file.</span><span class="sxs-lookup"><span data-stu-id="7b331-108">Required for attributes applied at the beginning of a source file.</span></span> <span data-ttu-id="7b331-109">Can be [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) or [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="7b331-109">Can be [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) or [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md).</span></span>|
|`attributename`| <span data-ttu-id="7b331-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="7b331-110">Required.</span></span> <span data-ttu-id="7b331-111">屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="7b331-111">Name of the attribute.</span></span>|
|`attributearguments`|<span data-ttu-id="7b331-112">選擇項。</span><span class="sxs-lookup"><span data-stu-id="7b331-112">Optional.</span></span> <span data-ttu-id="7b331-113">List of positional arguments for this attribute.</span><span class="sxs-lookup"><span data-stu-id="7b331-113">List of positional arguments for this attribute.</span></span> <span data-ttu-id="7b331-114">Multiple arguments are separated by commas.</span><span class="sxs-lookup"><span data-stu-id="7b331-114">Multiple arguments are separated by commas.</span></span>|
|`attributeinitializer`|<span data-ttu-id="7b331-115">選擇項。</span><span class="sxs-lookup"><span data-stu-id="7b331-115">Optional.</span></span> <span data-ttu-id="7b331-116">List of variable or property initializers for this attribute.</span><span class="sxs-lookup"><span data-stu-id="7b331-116">List of variable or property initializers for this attribute.</span></span> <span data-ttu-id="7b331-117">Multiple initializers are separated by commas.</span><span class="sxs-lookup"><span data-stu-id="7b331-117">Multiple initializers are separated by commas.</span></span>|
  
## <a name="remarks"></a><span data-ttu-id="7b331-118">備註</span><span class="sxs-lookup"><span data-stu-id="7b331-118">Remarks</span></span>  
 <span data-ttu-id="7b331-119">You can apply one or more attributes to nearly any programming element (types, procedures, properties, and so forth).</span><span class="sxs-lookup"><span data-stu-id="7b331-119">You can apply one or more attributes to nearly any programming element (types, procedures, properties, and so forth).</span></span> <span data-ttu-id="7b331-120">Attributes appear in your assembly's metadata, and they can help you annotate your code or specify how to use a particular programming element.</span><span class="sxs-lookup"><span data-stu-id="7b331-120">Attributes appear in your assembly's metadata, and they can help you annotate your code or specify how to use a particular programming element.</span></span> <span data-ttu-id="7b331-121">You can apply attributes defined by Visual Basic and the .NET Framework, and you can define your own attributes.</span><span class="sxs-lookup"><span data-stu-id="7b331-121">You can apply attributes defined by Visual Basic and the .NET Framework, and you can define your own attributes.</span></span>  

 <span data-ttu-id="7b331-122">For more information on when to use attributes, see [Attributes overview](../../../visual-basic/programming-guide/concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="7b331-122">For more information on when to use attributes, see [Attributes overview](../../../visual-basic/programming-guide/concepts/attributes/index.md).</span></span> <span data-ttu-id="7b331-123">For information on attribute names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="7b331-123">For information on attribute names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="7b331-124">規則</span><span class="sxs-lookup"><span data-stu-id="7b331-124">Rules</span></span>  
  
- <span data-ttu-id="7b331-125">**Placement.**</span><span class="sxs-lookup"><span data-stu-id="7b331-125">**Placement.**</span></span> <span data-ttu-id="7b331-126">You can apply attributes to most declared programming elements.</span><span class="sxs-lookup"><span data-stu-id="7b331-126">You can apply attributes to most declared programming elements.</span></span> <span data-ttu-id="7b331-127">To apply one or more attributes, you place an *attribute block* at the beginning of the element declaration.</span><span class="sxs-lookup"><span data-stu-id="7b331-127">To apply one or more attributes, you place an *attribute block* at the beginning of the element declaration.</span></span> <span data-ttu-id="7b331-128">Each entry in the attribute list specifies an attribute you wish to apply, and the modifier and arguments you are using for this invocation of the attribute.</span><span class="sxs-lookup"><span data-stu-id="7b331-128">Each entry in the attribute list specifies an attribute you wish to apply, and the modifier and arguments you are using for this invocation of the attribute.</span></span>  
  
- <span data-ttu-id="7b331-129">**Angle Brackets.**</span><span class="sxs-lookup"><span data-stu-id="7b331-129">**Angle Brackets.**</span></span> <span data-ttu-id="7b331-130">If you supply an attribute list, you must enclose it in angle brackets ("`<`" and "`>`").</span><span class="sxs-lookup"><span data-stu-id="7b331-130">If you supply an attribute list, you must enclose it in angle brackets ("`<`" and "`>`").</span></span>  
  
- <span data-ttu-id="7b331-131">**Part of the Declaration.**</span><span class="sxs-lookup"><span data-stu-id="7b331-131">**Part of the Declaration.**</span></span> <span data-ttu-id="7b331-132">The attribute must be part of the element declaration, not a separate statement.</span><span class="sxs-lookup"><span data-stu-id="7b331-132">The attribute must be part of the element declaration, not a separate statement.</span></span> <span data-ttu-id="7b331-133">You can use the line-continuation sequence (" `_`") to extend the declaration statement onto multiple source-code lines.</span><span class="sxs-lookup"><span data-stu-id="7b331-133">You can use the line-continuation sequence (" `_`") to extend the declaration statement onto multiple source-code lines.</span></span>  
  
- <span data-ttu-id="7b331-134">**Modifiers.**</span><span class="sxs-lookup"><span data-stu-id="7b331-134">**Modifiers.**</span></span> <span data-ttu-id="7b331-135">An attribute modifier (`Assembly` or `Module`) is required on every attribute applied to a programming element at the beginning of a source file.</span><span class="sxs-lookup"><span data-stu-id="7b331-135">An attribute modifier (`Assembly` or `Module`) is required on every attribute applied to a programming element at the beginning of a source file.</span></span> <span data-ttu-id="7b331-136">Attribute modifiers are not allowed on attributes applied to elements that are not at the beginning of a source file.</span><span class="sxs-lookup"><span data-stu-id="7b331-136">Attribute modifiers are not allowed on attributes applied to elements that are not at the beginning of a source file.</span></span>  
  
- <span data-ttu-id="7b331-137">**Arguments.**</span><span class="sxs-lookup"><span data-stu-id="7b331-137">**Arguments.**</span></span> <span data-ttu-id="7b331-138">All positional arguments for an attribute must precede any variable or property initializers.</span><span class="sxs-lookup"><span data-stu-id="7b331-138">All positional arguments for an attribute must precede any variable or property initializers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b331-139">範例</span><span class="sxs-lookup"><span data-stu-id="7b331-139">Example</span></span>  
 <span data-ttu-id="7b331-140">The following example applies the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to a skeleton definition of a `Function` procedure.</span><span class="sxs-lookup"><span data-stu-id="7b331-140">The following example applies the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to a skeleton definition of a `Function` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]  
  
 <span data-ttu-id="7b331-141"><xref:System.Runtime.InteropServices.DllImportAttribute> indicates that the attributed procedure represents an entry point in an unmanaged dynamic-link library (DLL).</span><span class="sxs-lookup"><span data-stu-id="7b331-141"><xref:System.Runtime.InteropServices.DllImportAttribute> indicates that the attributed procedure represents an entry point in an unmanaged dynamic-link library (DLL).</span></span> <span data-ttu-id="7b331-142">The attribute supplies the DLL name as a positional argument and the other information as variable initializers.</span><span class="sxs-lookup"><span data-stu-id="7b331-142">The attribute supplies the DLL name as a positional argument and the other information as variable initializers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b331-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="7b331-143">See also</span></span>

- [<span data-ttu-id="7b331-144">Assembly</span><span class="sxs-lookup"><span data-stu-id="7b331-144">Assembly</span></span>](../../../visual-basic/language-reference/modifiers/assembly.md)
- [<span data-ttu-id="7b331-145">Module \<鍵字></span><span class="sxs-lookup"><span data-stu-id="7b331-145">Module \<keyword></span></span>](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [<span data-ttu-id="7b331-146">屬性概觀</span><span class="sxs-lookup"><span data-stu-id="7b331-146">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="7b331-147">操作說明：在程式碼內中斷和合併陳述式</span><span class="sxs-lookup"><span data-stu-id="7b331-147">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
