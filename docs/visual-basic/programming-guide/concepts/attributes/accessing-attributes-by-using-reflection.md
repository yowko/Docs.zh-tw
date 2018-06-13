---
title: 使用反映 (Visual Basic) 存取屬性
ms.date: 07/20/2015
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
ms.openlocfilehash: dca476eef392a2f57d0c66727c53e0e53310d679
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642008"
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a><span data-ttu-id="e8b42-102">使用反映 (Visual Basic) 存取屬性</span><span class="sxs-lookup"><span data-stu-id="e8b42-102">Accessing Attributes by Using Reflection (Visual Basic)</span></span>
<span data-ttu-id="e8b42-103">您可以定義自訂屬性並將它們放在原始程式碼的事實，對於擷取並處理該項資訊並沒有什麼幫助。</span><span class="sxs-lookup"><span data-stu-id="e8b42-103">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="e8b42-104">使用反射，即可擷取已使用自訂屬性所定義的資訊。</span><span class="sxs-lookup"><span data-stu-id="e8b42-104">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="e8b42-105">重要方法是 `GetCustomAttributes`，這會傳回為來源程式碼屬性的執行階段對等項目的物件陣列。</span><span class="sxs-lookup"><span data-stu-id="e8b42-105">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="e8b42-106">這個方法有數個多載的版本。</span><span class="sxs-lookup"><span data-stu-id="e8b42-106">This method has several overloaded versions.</span></span> <span data-ttu-id="e8b42-107">如需詳細資訊，請參閱<xref:System.Attribute>。</span><span class="sxs-lookup"><span data-stu-id="e8b42-107">For more information, see <xref:System.Attribute>.</span></span>  
  
 <span data-ttu-id="e8b42-108">屬性規格，例如︰</span><span class="sxs-lookup"><span data-stu-id="e8b42-108">An attribute specification such as:</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 <span data-ttu-id="e8b42-109">概念上相當於這個：</span><span class="sxs-lookup"><span data-stu-id="e8b42-109">is conceptually equivalent to this:</span></span>  
  
```vb  
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")  
anonymousAuthorObject.version = 1.1  
```  
  
 <span data-ttu-id="e8b42-110">不過，程式碼會等到查詢 `SampleClass` 的屬性才會執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="e8b42-110">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="e8b42-111">在 `SampleClass` 上呼叫 `GetCustomAttributes`，會如上建構和初始化 `Author` 物件。</span><span class="sxs-lookup"><span data-stu-id="e8b42-111">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="e8b42-112">如果類別有其他屬性，則以類似的方式建構其他屬性物件。</span><span class="sxs-lookup"><span data-stu-id="e8b42-112">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="e8b42-113">`GetCustomAttributes` 接著會傳回 `Author` 物件以及陣列中的任何其他屬性物件。</span><span class="sxs-lookup"><span data-stu-id="e8b42-113">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="e8b42-114">您接著可以逐一查看這個陣列、根據每個陣列項目的類型來決定已套用的屬性，以及從屬性物件擷取資訊。</span><span class="sxs-lookup"><span data-stu-id="e8b42-114">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8b42-115">範例</span><span class="sxs-lookup"><span data-stu-id="e8b42-115">Example</span></span>  
 <span data-ttu-id="e8b42-116">以下是完整範例。</span><span class="sxs-lookup"><span data-stu-id="e8b42-116">Here is a complete example.</span></span> <span data-ttu-id="e8b42-117">定義、套用至數個實體並透過反射來擷取自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="e8b42-117">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e8b42-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8b42-118">See Also</span></span>  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [<span data-ttu-id="e8b42-119">Visual Basic 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="e8b42-119">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="e8b42-120">擷取儲存於屬性中的資訊</span><span class="sxs-lookup"><span data-stu-id="e8b42-120">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
 [<span data-ttu-id="e8b42-121">反映 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8b42-121">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="e8b42-122">屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8b42-122">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)  
 [<span data-ttu-id="e8b42-123">建立自訂屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8b42-123">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
