---
title: "如何︰ 使用 LINQ (Visual Basic) 查詢 ArrayList |Microsoft 文件"
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
ms.assetid: 176358a9-d765-4b57-9557-7feb4428138d
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 59dd2fb9af093e2e27d5db75e0e7b886f47f2a57
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a><span data-ttu-id="f87dd-102">如何︰ 使用 LINQ (Visual Basic) 查詢 ArrayList</span><span class="sxs-lookup"><span data-stu-id="f87dd-102">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>
<span data-ttu-id="f87dd-103">當您使用 LINQ 查詢的非泛型時<xref:System.Collections.IEnumerable>集合，例如<xref:System.Collections.ArrayList>，您必須明確宣告的範圍變數，以反映在集合中物件的特定類型的類型。</xref:System.Collections.ArrayList> </xref:System.Collections.IEnumerable></span><span class="sxs-lookup"><span data-stu-id="f87dd-103">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="f87dd-104">例如，如果您有<xref:System.Collections.ArrayList>的`Student`物件，您[From 子句](../../../../visual-basic/language-reference/queries/from-clause.md)應該看起來像這樣︰</xref:System.Collections.ArrayList></span><span class="sxs-lookup"><span data-stu-id="f87dd-104">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md) should look like this:</span></span>  
  
```  
Dim query = From student As Student In arrList   
...  
```  
  
 <span data-ttu-id="f87dd-105">藉由指定的範圍變數的類型，您正在轉換中的每個項目<xref:System.Collections.ArrayList>到`Student`。</xref:System.Collections.ArrayList></span><span class="sxs-lookup"><span data-stu-id="f87dd-105">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>  
  
 <span data-ttu-id="f87dd-106">在查詢運算式中明確指定型別的的範圍變數的用途就相當於呼叫<xref:System.Linq.Enumerable.Cast%2A>方法。</xref:System.Linq.Enumerable.Cast%2A></span><span class="sxs-lookup"><span data-stu-id="f87dd-106">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="f87dd-107"><xref:System.Linq.Enumerable.Cast%2A>如果無法執行指定的轉型，則會擲回例外狀況。</xref:System.Linq.Enumerable.Cast%2A></span><span class="sxs-lookup"><span data-stu-id="f87dd-107"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="f87dd-108"><xref:System.Linq.Enumerable.Cast%2A>和<xref:System.Linq.Enumerable.OfType%2A>對非泛型的兩個標準查詢運算子方法<xref:System.Collections.IEnumerable>型別。</xref:System.Collections.IEnumerable> </xref:System.Linq.Enumerable.OfType%2A></xref:System.Linq.Enumerable.Cast%2A></span><span class="sxs-lookup"><span data-stu-id="f87dd-108"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="f87dd-109">在 Visual Basic 中，您必須明確地呼叫<xref:System.Linq.Enumerable.Cast%2A>方法上的資料來源，以確保特定範圍的變數型別。</xref:System.Linq.Enumerable.Cast%2A></span><span class="sxs-lookup"><span data-stu-id="f87dd-109">In Visual Basic, you must explicitly call the <xref:System.Linq.Enumerable.Cast%2A> method on the data source to ensure a specific range variable type.</span></span> <span data-ttu-id="f87dd-110">如需詳細資訊，請參閱[查詢作業 (Visual Basic) 中的型別關聯性](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="f87dd-110">For more information, see[Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f87dd-111">範例</span><span class="sxs-lookup"><span data-stu-id="f87dd-111">Example</span></span>  
 <span data-ttu-id="f87dd-112">下列範例顯示簡單的查詢，透過<xref:System.Collections.ArrayList>.</xref:System.Collections.ArrayList></span><span class="sxs-lookup"><span data-stu-id="f87dd-112">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="f87dd-113">請注意，此範例會使用物件初始設定式時，程式碼呼叫<xref:System.Collections.ArrayList.Add%2A>方法，但這不一定。</xref:System.Collections.ArrayList.Add%2A></span><span class="sxs-lookup"><span data-stu-id="f87dd-113">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>  
  
```vb  
Imports System.Collections  
Imports System.Linq  
  
Module Module1  
  
    Public Class Student  
        Public Property FirstName As String  
        Public Property LastName As String  
        Public Property Scores As Integer()  
    End Class  
  
    Sub Main()  
  
        Dim student1 As New Student With {.FirstName = "Svetlana",   
                                     .LastName = "Omelchenko",   
                                     .Scores = New Integer() {98, 92, 81, 60}}  
        Dim student2 As New Student With {.FirstName = "Claire",   
                                    .LastName = "O'Donnell",   
                                    .Scores = New Integer() {75, 84, 91, 39}}  
        Dim student3 As New Student With {.FirstName = "Cesar",   
                                    .LastName = "Garcia",   
                                    .Scores = New Integer() {97, 89, 85, 82}}  
        Dim student4 As New Student With {.FirstName = "Sven",   
                                    .LastName = "Mortensen",   
                                    .Scores = New Integer() {88, 94, 65, 91}}  
  
        Dim arrList As New ArrayList()  
        arrList.Add(student1)  
        arrList.Add(student2)  
        arrList.Add(student3)  
        arrList.Add(student4)  
  
        ' Use an explicit type for non-generic collections  
        Dim query = From student As Student In arrList   
                    Where student.Scores(0) > 95   
                    Select student  
  
        For Each student As Student In query  
            Console.WriteLine(student.LastName & ": " & student.Scores(0))  
        Next  
        ' Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
End Module  
' Output:  
'   Omelchenko: 98  
'   Garcia: 97  
```  
  
## <a name="see-also"></a><span data-ttu-id="f87dd-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f87dd-114">See Also</span></span>  
 [<span data-ttu-id="f87dd-115">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f87dd-115">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)

