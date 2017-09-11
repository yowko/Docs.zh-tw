---
title: "在介面中使用變異數的泛型集合 (Visual Basic) |Microsoft 文件"
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
ms.assetid: c867fcea-7462-4995-b9c5-542feec74036
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 86184c7de3fe16148bf954b16d703ca682216337
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="using-variance-in-interfaces-for-generic-collections-visual-basic"></a><span data-ttu-id="49d58-102">在介面中使用變異數的泛型集合 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49d58-102">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>
<span data-ttu-id="49d58-103">Covariant 介面可讓方法來傳回更比介面中指定的衍生型別。</span><span class="sxs-lookup"><span data-stu-id="49d58-103">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="49d58-104">Contravariant 介面可讓它接受比所指定的介面中較少衍生型別參數的方法。</span><span class="sxs-lookup"><span data-stu-id="49d58-104">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>  
  
 <span data-ttu-id="49d58-105">在.NET Framework 4 中，有數個現有介面成為 covariant 和 contravariant。</span><span class="sxs-lookup"><span data-stu-id="49d58-105">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="49d58-106">這些包括<xref:System.Collections.Generic.IEnumerable%601>和<xref:System.IComparable%601>。</xref:System.IComparable%601> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="49d58-106">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="49d58-107">這可讓您重複使用與衍生型別集合的基底型別的泛型集合上運算。</span><span class="sxs-lookup"><span data-stu-id="49d58-107">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>  
  
 <span data-ttu-id="49d58-108">如需.NET Framework 中的 variant 介面，請參閱[泛型介面 (Visual Basic) 中的變異數](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)。</span><span class="sxs-lookup"><span data-stu-id="49d58-108">For a list of variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>  
  
## <a name="converting-generic-collections"></a><span data-ttu-id="49d58-109">轉換泛型集合</span><span class="sxs-lookup"><span data-stu-id="49d58-109">Converting Generic Collections</span></span>  
 <span data-ttu-id="49d58-110">下列範例說明中的共變數支援優點<xref:System.Collections.Generic.IEnumerable%601>介面。</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="49d58-110">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="49d58-111">`PrintFullName`方法可接受的集合`IEnumerable(Of Person)`做為參數的型別。</span><span class="sxs-lookup"><span data-stu-id="49d58-111">The `PrintFullName` method accepts a collection of the `IEnumerable(Of Person)` type as a parameter.</span></span> <span data-ttu-id="49d58-112">不過，您可以重複使用該集合的`IEnumerable(Of Person)`型別，因為`Employee`繼承`Person`。</span><span class="sxs-lookup"><span data-stu-id="49d58-112">However, you can reuse it for a collection of the `IEnumerable(Of Person)` type because `Employee` inherits `Person`.</span></span>  
  
<span data-ttu-id="49d58-113"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="49d58-113"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
## <a name="comparing-generic-collections"></a><span data-ttu-id="49d58-114">比較泛型集合</span><span class="sxs-lookup"><span data-stu-id="49d58-114">Comparing Generic Collections</span></span>  
 <span data-ttu-id="49d58-115">下列範例說明反變數中的支援權益<xref:System.Collections.Generic.IComparer%601>介面。</xref:System.Collections.Generic.IComparer%601></span><span class="sxs-lookup"><span data-stu-id="49d58-115">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="49d58-116">`PersonComparer` 類別會實作 `IComparer(Of Person)` 介面。</span><span class="sxs-lookup"><span data-stu-id="49d58-116">The `PersonComparer` class implements the `IComparer(Of Person)` interface.</span></span> <span data-ttu-id="49d58-117">不過，您可以重複使用這個類別，以比較之物件的序列`Employee`型別，因為`Employee`繼承`Person`。</span><span class="sxs-lookup"><span data-stu-id="49d58-117">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>  
  
```vb  
' Simple hierarhcy of classes.  
Public Class Person  
    Public Property FirstName As String  
    Public Property LastName As String  
End Class  
  
Public Class Employee  
    Inherits Person  
End Class  
' The custom comparer for the Person type  
' with standard implementations of Equals()  
' and GetHashCode() methods.  
Class PersonComparer  
    Implements IEqualityComparer(Of Person)  
  
    Public Function Equals1(  
        ByVal x As Person,  
        ByVal y As Person) As Boolean _  
        Implements IEqualityComparer(Of Person).Equals  
  
        If x Is y Then Return True  
        If x Is Nothing OrElse y Is Nothing Then Return False  
        Return (x.FirstName = y.FirstName) AndAlso  
            (x.LastName = y.LastName)  
    End Function  
    Public Function GetHashCode1(  
        ByVal person As Person) As Integer _  
        Implements IEqualityComparer(Of Person).GetHashCode  
  
        If person Is Nothing Then Return 0  
        Dim hashFirstName =  
            If(person.FirstName Is Nothing,  
            0, person.FirstName.GetHashCode())  
        Dim hashLastName = person.LastName.GetHashCode()  
        Return hashFirstName Xor hashLastName  
    End Function  
End Class  
  
Sub Main()  
    Dim employees = New List(Of Employee) From {  
        New Employee With {.FirstName = "Michael", .LastName = "Alexander"},  
        New Employee With {.FirstName = "Jeff", .LastName = "Price"}  
    }  
  
    ' You can pass PersonComparer,   
    ' which implements IEqualityComparer(Of Person),  
    ' although the method expects IEqualityComparer(Of Employee)  
  
    Dim noduplicates As IEnumerable(Of Employee) = employees.Distinct(New PersonComparer())  
  
    For Each employee In noduplicates  
        Console.WriteLine(employee.FirstName & " " & employee.LastName)  
    Next  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="49d58-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49d58-118">See Also</span></span>  
 [<span data-ttu-id="49d58-119">泛型介面 (Visual Basic) 中的變異數</span><span class="sxs-lookup"><span data-stu-id="49d58-119">Variance in Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
