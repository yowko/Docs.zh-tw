---
title: HOW TO：判斷兩個物件是否相關 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: 2b17be4ef5a7dabfc4779ab6f5675cc2baec9c3c
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626563"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a><span data-ttu-id="2b913-102">作法：判斷兩個物件是否相關 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b913-102">How to: Determine Whether Two Objects Are Related (Visual Basic)</span></span>

<span data-ttu-id="2b913-103">您可以比較兩個物件來判斷其建立所在的類別之間的關聯性 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="2b913-103">You can compare two objects to determine the relationship, if any, between the classes from which they are created.</span></span> <span data-ttu-id="2b913-104">如果指定的類別<xref:System.Type?displayProperty=nameWithType>繼承自目前的類別, 或如果目前的類型是指定類別所支援的介面, 則類別<xref:System.Type.IsInstanceOfType%2A>的方法`True`會傳回。</span><span class="sxs-lookup"><span data-stu-id="2b913-104">The <xref:System.Type.IsInstanceOfType%2A> method of the <xref:System.Type?displayProperty=nameWithType> class returns `True` if the specified class inherits from the current class, or if the current type is an interface supported by the specified class.</span></span>

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a><span data-ttu-id="2b913-105">判斷其中一個物件是否繼承自另一個物件的類別或介面</span><span class="sxs-lookup"><span data-stu-id="2b913-105">To determine if one object inherits from another object's class or interface</span></span>

1. <span data-ttu-id="2b913-106">在您認為可能是基底類型的物件上, <xref:System.Object.GetType%2A>叫用方法。</span><span class="sxs-lookup"><span data-stu-id="2b913-106">On the object you think might be of the base type, invoke the <xref:System.Object.GetType%2A> method.</span></span>

2. <span data-ttu-id="2b913-107">在所<xref:System.Type?displayProperty=nameWithType>傳回的物件<xref:System.Object.GetType%2A>上, <xref:System.Type.IsInstanceOfType%2A>叫用方法。</span><span class="sxs-lookup"><span data-stu-id="2b913-107">On the <xref:System.Type?displayProperty=nameWithType> object returned by <xref:System.Object.GetType%2A>, invoke the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>

3. <span data-ttu-id="2b913-108">在的引數清單<xref:System.Type.IsInstanceOfType%2A>中, 指定您認為可能是衍生類型的物件。</span><span class="sxs-lookup"><span data-stu-id="2b913-108">In the argument list for <xref:System.Type.IsInstanceOfType%2A>, specify the object you think might be of the derived type.</span></span>

    <span data-ttu-id="2b913-109"><xref:System.Type.IsInstanceOfType%2A>如果其引數型別繼承自<xref:System.Type?displayProperty=nameWithType>物件型別, 則傳回。 `True`</span><span class="sxs-lookup"><span data-stu-id="2b913-109"><xref:System.Type.IsInstanceOfType%2A> returns `True` if its argument type inherits from the <xref:System.Type?displayProperty=nameWithType> object type.</span></span>

## <a name="example"></a><span data-ttu-id="2b913-110">範例</span><span class="sxs-lookup"><span data-stu-id="2b913-110">Example</span></span>
 <span data-ttu-id="2b913-111">下列範例會判斷其中一個物件是否代表衍生自另一個物件類別的類別。</span><span class="sxs-lookup"><span data-stu-id="2b913-111">The following example determines whether one object represents a class derived from another object's class.</span></span>

```vb
Public Class baseClass
End Class
Public Class derivedClass : Inherits baseClass
End Class
Public Class testTheseClasses
    Public Sub seeIfRelated()
        Dim baseObj As Object = New baseClass()
        Dim derivedObj As Object = New derivedClass()
        Dim related As Boolean
        related = baseObj.GetType().IsInstanceOfType(derivedObj)
        MsgBox(CStr(related))
    End Sub
End Class
```

<span data-ttu-id="2b913-112">請注意呼叫<xref:System.Type.IsInstanceOfType%2A>中的兩個物件變數未預期的位置。</span><span class="sxs-lookup"><span data-stu-id="2b913-112">Note the unexpected placement of the two object variables in the call to <xref:System.Type.IsInstanceOfType%2A>.</span></span> <span data-ttu-id="2b913-113">預期的基底類型是用來產生<xref:System.Type?displayProperty=nameWithType>類別, 而預期的衍生型別會當做引數傳遞<xref:System.Type.IsInstanceOfType%2A>給方法。</span><span class="sxs-lookup"><span data-stu-id="2b913-113">The supposed base type is used to generate the <xref:System.Type?displayProperty=nameWithType> class, and the supposed derived type is passed as an argument to the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="2b913-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b913-114">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [<span data-ttu-id="2b913-115">Object 資料類型</span><span class="sxs-lookup"><span data-stu-id="2b913-115">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="2b913-116">物件變數</span><span class="sxs-lookup"><span data-stu-id="2b913-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="2b913-117">物件變數值</span><span class="sxs-lookup"><span data-stu-id="2b913-117">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="2b913-118">如何：判斷兩個物件是否相同</span><span class="sxs-lookup"><span data-stu-id="2b913-118">How to: Determine Whether Two Objects Are Identical</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
