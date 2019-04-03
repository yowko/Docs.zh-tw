---
title: HOW TO：使用 LINQ (Visual Basic) 查詢 ArrayList
ms.date: 07/20/2015
ms.assetid: 176358a9-d765-4b57-9557-7feb4428138d
ms.openlocfilehash: ed440a7970d0ef1a49af36fa56b1c7ca74715e5f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837152"
---
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a>HOW TO：使用 LINQ (Visual Basic) 查詢 ArrayList
使用 LINQ 查詢非泛型 <xref:System.Collections.IEnumerable> 集合時 (例如 <xref:System.Collections.ArrayList>)，您必須明確宣告範圍變數的類型，以反映集合中特定類型的物件。 例如，如果您有<xref:System.Collections.ArrayList>的`Student`物件，您[From 子句](../../../../visual-basic/language-reference/queries/from-clause.md)應該看起來像這樣：  
  
```  
Dim query = From student As Student In arrList   
...  
```  
  
 藉由指定範圍變數的類型，您就可以將 <xref:System.Collections.ArrayList> 中的每個項目轉換為 `Student`。  
  
 在查詢運算式中使用具有明確類型的範圍變數，相當於呼叫 <xref:System.Linq.Enumerable.Cast%2A> 方法。 如果無法執行指定的轉換，則 <xref:System.Linq.Enumerable.Cast%2A> 會擲回例外狀況。 <xref:System.Linq.Enumerable.Cast%2A> 和 <xref:System.Linq.Enumerable.OfType%2A> 是對非泛型 <xref:System.Collections.IEnumerable> 類型執行的兩個標準查詢運算子方法。 在 Visual Basic 中，您必須明確呼叫<xref:System.Linq.Enumerable.Cast%2A>資料來源，以確保特定範圍的變數類型上的方法。 如需詳細資訊，請參閱 <<c0> [ 查詢作業 (Visual Basic) 中的型別關聯性](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)。  
  
## <a name="example"></a>範例  
 下列範例將顯示 <xref:System.Collections.ArrayList> 的簡單查詢。 請注意，此範例會在程式碼呼叫 <xref:System.Collections.ArrayList.Add%2A> 方法時使用物件初始設定式，但這不是必要的。  
  
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

- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
