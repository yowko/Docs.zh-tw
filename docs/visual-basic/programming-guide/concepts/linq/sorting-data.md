---
title: "排序資料 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8f17c6ecad721dd3a48a01c09693b0a1cf723a5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="sorting-data-visual-basic"></a>排序資料 (Visual Basic)
排序作業會根據一個或多個屬性來排序序列的項目。 第一個排序準則會執行元素的主要排序； 您可以藉由指定第二個排序準則來排序每一個主要排序群組內的元素。  
  
 下圖顯示對一系列字元執行字母順序排序作業的結果。  
  
 ![LINQ 排序作業](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")  
  
 下節列出可排序資料的標準查詢運算子方法。  
  
## <a name="methods"></a>方法  
  
|方法名稱|說明|Visual Basic 查詢運算式語法|更多資訊|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|OrderBy|依遞增順序排序值。|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|OrderByDescending|依遞減順序排序值。|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|ThenBy|依遞增順序執行次要排序。|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|ThenByDescending|依遞減順序執行次要排序。|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|Reverse|反轉集合中項目的順序。|不適用。|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>查詢運算式語法範例  
  
### <a name="primary-sort-examples"></a>主要排序範例  
  
#### <a name="primary-ascending-sort"></a>主要遞增排序  
 下列範例示範如何在 LINQ 查詢中使用 `Order By` 子句，依字串長度以遞增順序來排序陣列中的字串。  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' fox  
' quick  
' brown  
' jumps  
```  
  
#### <a name="primary-descending-sort"></a>主要遞減排序  
 下一個範例示範如何在 LINQ 查詢中使用 `Order By Descending` 子句，依其第一個字母以遞減順序來排序字串。  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Substring(0, 1) Descending   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' quick  
' jumps  
' fox  
' brown  
```  
  
### <a name="secondary-sort-examples"></a>次要排序範例  
  
#### <a name="secondary-ascending-sort"></a>次要遞增排序  
 下列範例示範如何在 LINQ 查詢中使用 `Order By` 子句，對陣列中的字串執行主要和次要排序。 字串主要是依長度進行排序，其次依字串的第一個字母進行排序，而兩者都是遞增排序。  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length, word.Substring(0, 1)   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' fox  
' the  
' brown  
' jumps  
' quick  
```  
  
#### <a name="secondary-descending-sort"></a>次要遞減排序  
 下一個範例示範如何在 LINQ 查詢中使用 `Order By Descending` 子句，執行依遞增順序的主要排序以及依遞減順序的次要排序。 字串主要是依長度進行排序，其次依字串的第一個字母進行排序。  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length, word.Substring(0, 1) Descending   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' fox  
' the  
' quick  
' jumps  
' brown  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Linq>  
 [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Order By 子句](../../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [如何：排序查詢結果](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md)  
 [如何： 排序或篩選文字資料，依任何字或欄位 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
