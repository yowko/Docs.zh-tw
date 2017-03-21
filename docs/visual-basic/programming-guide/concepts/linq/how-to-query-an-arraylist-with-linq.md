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
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f48b06c23b1e28fccb953638954a8d9afefe574e
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a>如何︰ 使用 LINQ (Visual Basic) 查詢 ArrayList
當您使用 LINQ 查詢的非泛型時<xref:System.Collections.IEnumerable>集合，例如<xref:System.Collections.ArrayList>，您必須明確宣告的範圍變數，以反映在集合中物件的特定類型的類型。</xref:System.Collections.ArrayList> </xref:System.Collections.IEnumerable> 例如，如果您有<xref:System.Collections.ArrayList>的`Student`物件，您[From 子句](../../../../visual-basic/language-reference/queries/from-clause.md)應該看起來像這樣︰</xref:System.Collections.ArrayList>  
  
```  
  
Dim query = From student As Student In arrList   
...  
  
```  
  
 藉由指定的範圍變數的類型，您正在轉換中的每個項目<xref:System.Collections.ArrayList>到`Student`。</xref:System.Collections.ArrayList>  
  
 在查詢運算式中明確指定型別的的範圍變數的用途就相當於呼叫<xref:System.Linq.Enumerable.Cast%2A>方法。</xref:System.Linq.Enumerable.Cast%2A> <xref:System.Linq.Enumerable.Cast%2A>如果無法執行指定的轉型，則會擲回例外狀況。</xref:System.Linq.Enumerable.Cast%2A> <xref:System.Linq.Enumerable.Cast%2A>和<xref:System.Linq.Enumerable.OfType%2A>對非泛型的兩個標準查詢運算子方法<xref:System.Collections.IEnumerable>型別。</xref:System.Collections.IEnumerable> </xref:System.Linq.Enumerable.OfType%2A></xref:System.Linq.Enumerable.Cast%2A> 在 Visual Basic 中，您必須明確地呼叫<xref:System.Linq.Enumerable.Cast%2A>方法上的資料來源，以確保特定範圍的變數型別。</xref:System.Linq.Enumerable.Cast%2A> 如需詳細資訊，請參閱[查詢作業 (Visual Basic) 中的型別關聯性](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)。  
  
## <a name="example"></a>範例  
 下列範例顯示簡單的查詢，透過<xref:System.Collections.ArrayList>.</xref:System.Collections.ArrayList> 請注意，此範例會使用物件初始設定式時，程式碼呼叫<xref:System.Collections.ArrayList.Add%2A>方法，但這不一定。</xref:System.Collections.ArrayList.Add%2A>  
  
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
  
## <a name="see-also"></a>另請參閱  
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
