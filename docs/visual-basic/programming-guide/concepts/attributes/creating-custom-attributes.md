---
title: "建立自訂屬性 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: fbfc3f84f6287d233d475f01869dab63b937a521
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="creating-custom-attributes-visual-basic"></a><span data-ttu-id="60c38-102">建立自訂屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60c38-102">Creating Custom Attributes (Visual Basic)</span></span>
<span data-ttu-id="60c38-103">您可以建立您自己的自訂屬性定義的屬性類別，而是直接或間接衍生自類別<xref:System.Attribute>，因此可以快速又簡單的中繼資料中的屬性定義用來識別。</xref:System.Attribute></span><span class="sxs-lookup"><span data-stu-id="60c38-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="60c38-104">假設您想要撰寫此類型的程式設計人員的名稱的標記類型。</span><span class="sxs-lookup"><span data-stu-id="60c38-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="60c38-105">您可以定義自訂`Author`屬性類別︰</span><span class="sxs-lookup"><span data-stu-id="60c38-105">You might define a custom `Author` attribute class:</span></span>  
  
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
  
 <span data-ttu-id="60c38-106">類別名稱是屬性的名稱， `Author`。</span><span class="sxs-lookup"><span data-stu-id="60c38-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="60c38-107">它衍生自`System.Attribute`，因此它是自訂屬性類別。</span><span class="sxs-lookup"><span data-stu-id="60c38-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="60c38-108">建構函式的參數是位置參數的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="60c38-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="60c38-109">在此範例中，`name`是位置參數。</span><span class="sxs-lookup"><span data-stu-id="60c38-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="60c38-110">任何公用讀寫欄位或屬性都被具名參數。</span><span class="sxs-lookup"><span data-stu-id="60c38-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="60c38-111">在此情況下，`version`唯一具名參數。</span><span class="sxs-lookup"><span data-stu-id="60c38-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="60c38-112">請注意使用`AttributeUsage`屬性，讓`Author`屬性只有在類別上有效和`Structure`宣告。</span><span class="sxs-lookup"><span data-stu-id="60c38-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `Structure` declarations.</span></span>  
  
 <span data-ttu-id="60c38-113">您可以使用這個新屬性，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="60c38-113">You could use this new attribute as follows:</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 <span data-ttu-id="60c38-114">`AttributeUsage`具有具名的參數， `AllowMultiple`，這可以讓自訂屬性單次使用或多重與。</span><span class="sxs-lookup"><span data-stu-id="60c38-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="60c38-115">在下列程式碼範例中，建立多重的屬性。</span><span class="sxs-lookup"><span data-stu-id="60c38-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```vb  
' multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
```  
  
 <span data-ttu-id="60c38-116">在下列程式碼範例中，相同型別的多個屬性會套用至類別。</span><span class="sxs-lookup"><span data-stu-id="60c38-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1),   
Author("R. Koch", Version:=1.2)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
    ' R. Koch's code goes here...  
End Class  
```  
  
> [!NOTE]
>  <span data-ttu-id="60c38-117">如果屬性類別包含屬性，該屬性必須是讀寫。</span><span class="sxs-lookup"><span data-stu-id="60c38-117">If your attribute class contains a property, that property must be read-write.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60c38-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60c38-118">See Also</span></span>  
 <span data-ttu-id="60c38-119"><xref:System.Reflection></xref:System.Reflection></span><span class="sxs-lookup"><span data-stu-id="60c38-119"><xref:System.Reflection></span></span>   
<span data-ttu-id="60c38-120"> [Visual Basic 程式設計指南](../../../../visual-basic/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="60c38-120"> [Visual Basic Programming Guide](../../../../visual-basic/programming-guide/index.md) </span></span>  
<span data-ttu-id="60c38-121"> [撰寫自訂屬性](http://msdn.microsoft.com/library/97216f69-bde8-49fd-ac40-f18c500ef5dc) </span><span class="sxs-lookup"><span data-stu-id="60c38-121"> [Writing Custom Attributes](http://msdn.microsoft.com/library/97216f69-bde8-49fd-ac40-f18c500ef5dc) </span></span>  
<span data-ttu-id="60c38-122"> [反映 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="60c38-122"> [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span></span>  
<span data-ttu-id="60c38-123"> [屬性 (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span><span class="sxs-lookup"><span data-stu-id="60c38-123"> [Attributes (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span></span>  
<span data-ttu-id="60c38-124"> [使用反映 (Visual Basic) 存取屬性](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md) </span><span class="sxs-lookup"><span data-stu-id="60c38-124"> [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md) </span></span>  
<span data-ttu-id="60c38-125"> [AttributeUsage (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)</span><span class="sxs-lookup"><span data-stu-id="60c38-125"> [AttributeUsage (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)</span></span>
