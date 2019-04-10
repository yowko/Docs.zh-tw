---
title: HOW TO：判斷兩個物件是否關聯 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: f59e00d80d28fc4bf24874d25b5c12643649c834
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59342093"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a><span data-ttu-id="a2ac0-102">HOW TO：判斷兩個物件是否關聯 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2ac0-102">How to: Determine Whether Two Objects Are Related (Visual Basic)</span></span>
<span data-ttu-id="a2ac0-103">您可以比較來決定關聯性，如果有的話，建立的類別之間的兩個物件。</span><span class="sxs-lookup"><span data-stu-id="a2ac0-103">You can compare two objects to determine the relationship, if any, between the classes from which they are created.</span></span> <span data-ttu-id="a2ac0-104"><xref:System.Type.IsInstanceOfType%2A>方法<xref:System.Type?displayProperty=nameWithType>類別會傳回`True`如果指定的類別繼承自目前的類別，或目前的類型是否支援指定的類別介面。</span><span class="sxs-lookup"><span data-stu-id="a2ac0-104">The <xref:System.Type.IsInstanceOfType%2A> method of the <xref:System.Type?displayProperty=nameWithType> class returns `True` if the specified class inherits from the current class, or if the current type is an interface supported by the specified class.</span></span>  
  
### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a><span data-ttu-id="a2ac0-105">若要判斷一個物件是否繼承自另一個物件的類別或介面</span><span class="sxs-lookup"><span data-stu-id="a2ac0-105">To determine if one object inherits from another object's class or interface</span></span>  
  
1. <span data-ttu-id="a2ac0-106">您認為在物件上可能是基底型別，會叫用<xref:System.Object.GetType%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="a2ac0-106">On the object you think might be of the base type, invoke the <xref:System.Object.GetType%2A> method.</span></span>  
  
2. <span data-ttu-id="a2ac0-107">在 <xref:System.Type?displayProperty=nameWithType>所傳回的物件<xref:System.Object.GetType%2A>，叫用<xref:System.Type.IsInstanceOfType%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="a2ac0-107">On the <xref:System.Type?displayProperty=nameWithType> object returned by <xref:System.Object.GetType%2A>, invoke the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>  
  
3. <span data-ttu-id="a2ac0-108">中的引數清單<xref:System.Type.IsInstanceOfType%2A>，指定您認為的物件可能是衍生型別。</span><span class="sxs-lookup"><span data-stu-id="a2ac0-108">In the argument list for <xref:System.Type.IsInstanceOfType%2A>, specify the object you think might be of the derived type.</span></span>  
  
     <xref:System.Type.IsInstanceOfType%2A> <span data-ttu-id="a2ac0-109">會傳回`True`如果其引數型別是繼承自<xref:System.Type?displayProperty=nameWithType>物件類型。</span><span class="sxs-lookup"><span data-stu-id="a2ac0-109">returns `True` if its argument type inherits from the <xref:System.Type?displayProperty=nameWithType> object type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2ac0-110">範例</span><span class="sxs-lookup"><span data-stu-id="a2ac0-110">Example</span></span>  
 <span data-ttu-id="a2ac0-111">下列範例會判斷物件是否代表從另一個物件的類別衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="a2ac0-111">The following example determines whether one object represents a class derived from another object's class.</span></span>  
  
```  
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
  
 <span data-ttu-id="a2ac0-112">請注意兩個物件變數的呼叫中的非預期的放置<xref:System.Type.IsInstanceOfType%2A>。</span><span class="sxs-lookup"><span data-stu-id="a2ac0-112">Note the unexpected placement of the two object variables in the call to <xref:System.Type.IsInstanceOfType%2A>.</span></span> <span data-ttu-id="a2ac0-113">基底型別應該用來產生<xref:System.Type?displayProperty=nameWithType>類別，而應該衍生的型別傳遞做為引數<xref:System.Type.IsInstanceOfType%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="a2ac0-113">The supposed base type is used to generate the <xref:System.Type?displayProperty=nameWithType> class, and the supposed derived type is passed as an argument to the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2ac0-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2ac0-114">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [<span data-ttu-id="a2ac0-115">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="a2ac0-115">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="a2ac0-116">物件變數</span><span class="sxs-lookup"><span data-stu-id="a2ac0-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="a2ac0-117">物件變數值</span><span class="sxs-lookup"><span data-stu-id="a2ac0-117">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="a2ac0-118">HOW TO：判斷兩個物件是否相同</span><span class="sxs-lookup"><span data-stu-id="a2ac0-118">How to: Determine Whether Two Objects Are Identical</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
