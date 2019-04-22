---
title: 建立自訂屬性 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: 90e8e9b9a3fa8e0b488f41d035b017d6113213b5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814350"
---
# <a name="creating-custom-attributes-visual-basic"></a><span data-ttu-id="f1b21-102">建立自訂屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1b21-102">Creating Custom Attributes (Visual Basic)</span></span>
<span data-ttu-id="f1b21-103">您可以建立自己的自訂屬性，方法是定義屬性類別，這是直接或間接衍生自 <xref:System.Attribute> 的類別，它能快速且簡單地在中繼資料中識別屬性定義。</span><span class="sxs-lookup"><span data-stu-id="f1b21-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="f1b21-104">假設您想要用撰寫類型的程式設計人員姓名來標記類型。</span><span class="sxs-lookup"><span data-stu-id="f1b21-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="f1b21-105">您可能會定義自訂的 `Author` 屬性類別：</span><span class="sxs-lookup"><span data-stu-id="f1b21-105">You might define a custom `Author` attribute class:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct)>   
Public Class Author  
    Inherits System.Attribute  
    Private name As String  
    Public version As Double  
    Sub New(ByVal authorName As String)  
        name = authorName  
        version = 1.0  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="f1b21-106">類別名稱是屬性的名稱，亦即 `Author`。</span><span class="sxs-lookup"><span data-stu-id="f1b21-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="f1b21-107">它衍生自 `System.Attribute`，因此它是自訂屬性類別。</span><span class="sxs-lookup"><span data-stu-id="f1b21-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="f1b21-108">建構函式的參數是自訂屬性的位置參數。</span><span class="sxs-lookup"><span data-stu-id="f1b21-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="f1b21-109">在此範例中，`name` 是位置參數。</span><span class="sxs-lookup"><span data-stu-id="f1b21-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="f1b21-110">任何公用讀寫欄位或屬性都是具名參數。</span><span class="sxs-lookup"><span data-stu-id="f1b21-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="f1b21-111">在此情況下，`version` 是唯一的具名參數。</span><span class="sxs-lookup"><span data-stu-id="f1b21-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="f1b21-112">請注意，使用了 `AttributeUsage` 屬性讓 `Author` 屬性只有對類別和 `Structure` 宣告有效。</span><span class="sxs-lookup"><span data-stu-id="f1b21-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `Structure` declarations.</span></span>  
  
 <span data-ttu-id="f1b21-113">您可以如下所示使用這個新屬性︰</span><span class="sxs-lookup"><span data-stu-id="f1b21-113">You could use this new attribute as follows:</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 <span data-ttu-id="f1b21-114">`AttributeUsage` 有一個具名參數 `AllowMultiple`，您可以用它讓自訂屬性僅單次使用或是多次使用。</span><span class="sxs-lookup"><span data-stu-id="f1b21-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="f1b21-115">在下列程式碼範例中，建立了多次使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="f1b21-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```vb  
' multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
```  
  
 <span data-ttu-id="f1b21-116">在下列程式碼範例中，相同類型的多個屬性會套用至類別。</span><span class="sxs-lookup"><span data-stu-id="f1b21-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1),   
Author("R. Koch", Version:=1.2)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
    ' R. Koch's code goes here...  
End Class  
```  
  
> [!NOTE]
>  <span data-ttu-id="f1b21-117">如果您的屬性類別包含屬性，則該屬性必須是讀寫。</span><span class="sxs-lookup"><span data-stu-id="f1b21-117">If your attribute class contains a property, that property must be read-write.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1b21-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1b21-118">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="f1b21-119">Visual Basic 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="f1b21-119">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="f1b21-120">撰寫自訂屬性</span><span class="sxs-lookup"><span data-stu-id="f1b21-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="f1b21-121">反映 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1b21-121">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="f1b21-122">屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1b21-122">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="f1b21-123">使用反映存取屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1b21-123">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="f1b21-124">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1b21-124">AttributeUsage (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
