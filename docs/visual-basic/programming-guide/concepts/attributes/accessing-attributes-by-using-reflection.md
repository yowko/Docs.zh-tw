---
title: "使用反映 (Visual Basic) 存取屬性 |Microsoft 文件"
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
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
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
ms.openlocfilehash: ac1e017ae13fc1291fd41e5747171160a9d70238
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a><span data-ttu-id="7b299-102">使用反映 (Visual Basic) 存取屬性</span><span class="sxs-lookup"><span data-stu-id="7b299-102">Accessing Attributes by Using Reflection (Visual Basic)</span></span>
<span data-ttu-id="7b299-103">您可以用來定義自訂屬性，並將它們放在原始程式碼中的事實是價值擷取資訊並加以執行的方法不大。</span><span class="sxs-lookup"><span data-stu-id="7b299-103">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="7b299-104">使用反映，您可以擷取的已定義的自訂屬性的資訊。</span><span class="sxs-lookup"><span data-stu-id="7b299-104">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="7b299-105">重要的方法是`GetCustomAttributes`，它會傳回所對應之來源的程式碼屬性的執行階段物件的陣列。</span><span class="sxs-lookup"><span data-stu-id="7b299-105">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="7b299-106">這個方法有數個多載的版本。</span><span class="sxs-lookup"><span data-stu-id="7b299-106">This method has several overloaded versions.</span></span> <span data-ttu-id="7b299-107">如需詳細資訊，請參閱<xref:System.Attribute>。</xref:System.Attribute></span><span class="sxs-lookup"><span data-stu-id="7b299-107">For more information, see <xref:System.Attribute>.</span></span>  
  
 <span data-ttu-id="7b299-108">屬性規格，例如︰</span><span class="sxs-lookup"><span data-stu-id="7b299-108">An attribute specification such as:</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 <span data-ttu-id="7b299-109">在概念上等同於此︰</span><span class="sxs-lookup"><span data-stu-id="7b299-109">is conceptually equivalent to this:</span></span>  
  
```vb  
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")  
anonymousAuthorObject.version = 1.1  
```  
  
 <span data-ttu-id="7b299-110">不過，程式碼將會等到執行`SampleClass`查詢的屬性。</span><span class="sxs-lookup"><span data-stu-id="7b299-110">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="7b299-111">呼叫`GetCustomAttributes`上`SampleClass`造成`Author`物件建構和初始化與以上所述。</span><span class="sxs-lookup"><span data-stu-id="7b299-111">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="7b299-112">如果類別有其他屬性，其他屬性的物件是類似的方式建構。</span><span class="sxs-lookup"><span data-stu-id="7b299-112">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="7b299-113">`GetCustomAttributes`然後傳回`Author`物件和陣列中的其他屬性物件。</span><span class="sxs-lookup"><span data-stu-id="7b299-113">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="7b299-114">然後您可以逐一查看陣列、 判斷哪些屬性已套用的每個陣列項目類型和從屬性物件擷取資訊。</span><span class="sxs-lookup"><span data-stu-id="7b299-114">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b299-115">範例</span><span class="sxs-lookup"><span data-stu-id="7b299-115">Example</span></span>  
 <span data-ttu-id="7b299-116">以下是完整的範例。</span><span class="sxs-lookup"><span data-stu-id="7b299-116">Here is a complete example.</span></span> <span data-ttu-id="7b299-117">定義、 套用至數個項目，並經由反映來擷取自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="7b299-117">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>  
  
```vb  
' Multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
    Private name As String  
    Public version As Double  
    Sub New(ByVal authorName As String)  
        name = authorName  
  
        ' Default value  
        version = 1.0  
    End Sub  
  
    Function GetName() As String  
        Return name  
    End Function          
End Class  
  
' Class with the Author attribute  
<Author("P. Ackerman")>   
Public Class FirstClass  
End Class  
  
' Class without the Author attribute  
Public Class SecondClass  
End Class  
  
' Class with multiple Author attributes.  
<Author("P. Ackerman"), Author("R. Koch", Version:=2.0)>   
Public Class ThirdClass  
End Class  
  
Class TestAuthorAttribute  
    Sub Main()  
        PrintAuthorInfo(GetType(FirstClass))  
        PrintAuthorInfo(GetType(SecondClass))  
        PrintAuthorInfo(GetType(ThirdClass))  
    End Sub  
  
    Private Shared Sub PrintAuthorInfo(ByVal t As System.Type)  
        System.Console.WriteLine("Author information for {0}", t)  
  
        ' Using reflection  
        Dim attrs() As System.Attribute = System.Attribute.GetCustomAttributes(t)  
  
        ' Displaying output  
        For Each attr In attrs  
            Dim a As Author = CType(attr, Author)  
            System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version)  
        Next              
    End Sub  
  
    ' Output:  
    '   Author information for FirstClass  
    '     P. Ackerman, version 1.00  
    ' Author information for SecondClass  
    ' Author information for ThirdClass  
    '  R. Koch, version 2.00  
    '  P. Ackerman, version 1.00  
  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b299-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b299-118">See Also</span></span>  
 <span data-ttu-id="7b299-119"><xref:System.Reflection></xref:System.Reflection></span><span class="sxs-lookup"><span data-stu-id="7b299-119"><xref:System.Reflection></span></span>   
 <span data-ttu-id="7b299-120"><xref:System.Attribute></xref:System.Attribute></span><span class="sxs-lookup"><span data-stu-id="7b299-120"><xref:System.Attribute></span></span>   
<span data-ttu-id="7b299-121"> [Visual Basic 程式設計指南](../../../../visual-basic/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="7b299-121"> [Visual Basic Programming Guide](../../../../visual-basic/programming-guide/index.md) </span></span>  
<span data-ttu-id="7b299-122"> [擷取儲存於屬性中的資訊](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c) </span><span class="sxs-lookup"><span data-stu-id="7b299-122"> [Retrieving Information Stored in Attributes](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c) </span></span>  
<span data-ttu-id="7b299-123"> [反映 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="7b299-123"> [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span></span>  
<span data-ttu-id="7b299-124"> [屬性 (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span><span class="sxs-lookup"><span data-stu-id="7b299-124"> [Attributes (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span></span>  
<span data-ttu-id="7b299-125"> [建立自訂屬性 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)</span><span class="sxs-lookup"><span data-stu-id="7b299-125"> [Creating Custom Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)</span></span>
