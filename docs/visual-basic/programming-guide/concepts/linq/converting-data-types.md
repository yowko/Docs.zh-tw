---
title: "轉換資料類型 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
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
ms.openlocfilehash: 53d8ad292891a567e13ec8a5396bcc114b379351
ms.lasthandoff: 03/13/2017

---
# <a name="converting-data-types-visual-basic"></a>轉換資料類型 (Visual Basic)
轉換方法變更輸入物件的類型。  
  
 LINQ 查詢中的轉換作業可用於各種不同的應用程式。 以下是一些範例︰  
  
-   <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName>方法可用來隱藏的類型的標準查詢運算子的自訂實作。</xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName>  
  
-   <xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName>方法可用來啟用非參數化的 LINQ 查詢的集合。</xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName>  
  
-   <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>， <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>， <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>，和<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName>方法可以用來強制立即執行查詢而不是等到列舉查詢的延後。</xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName> </xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> </xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName> </xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>  
  
## <a name="methods"></a>方法  
 下表列出執行資料型別轉換的標準查詢運算子方法。  
  
 此表格中名稱開頭為"As"變更來源集合的靜態型別，但不是會列舉它的轉換方法。 方法名稱開頭為 「 目標 」 列舉來源集合，並將項目放入對應的集合型別。  
  
|方法名稱|說明|Visual Basic 查詢運算式語法|更多資訊|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|AsEnumerable|傳回輸入型別為<xref:System.Collections.Generic.IEnumerable%601>。</xref:System.Collections.Generic.IEnumerable%601>|不適用。|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName></xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName>|  
|AsQueryable|將轉換 （一般）<xref:System.Collections.IEnumerable>到 （一般） <xref:System.Linq.IQueryable>。</xref:System.Linq.IQueryable> </xref:System.Collections.IEnumerable>|不適用。|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName></xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName>|  
|Cast|將轉換為指定型別集合的項目。|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName></xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName>|  
|OfType|篩選值，視其可以轉換為指定型別而定。|不適用。|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName>|  
|ToArray|將集合轉換成陣列。 這個方法會強制執行查詢。|不適用。|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>|  
|ToDictionary|將元素插入<xref:System.Collections.Generic.Dictionary%602>根據索引鍵選取器函式。</xref:System.Collections.Generic.Dictionary%602> 這個方法會強制執行查詢。|不適用。|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>|  
|ToList|將集合轉換成<xref:System.Collections.Generic.List%601>。</xref:System.Collections.Generic.List%601> 這個方法會強制執行查詢。|不適用。|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>|  
|ToLookup|將元素插入<xref:System.Linq.Lookup%602>（一對多字典） 會根據索引鍵選取器函式。</xref:System.Linq.Lookup%602> 這個方法會強制執行查詢。|不適用。|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-example"></a>查詢運算式語法範例  
 下列程式碼範例使用`From As`子句，才能存取的成員為僅適用於子型別轉換子的型別。  
  
```vb  
Class Plant  
    Public Property Name As String  
End Class  
  
Class CarnivorousPlant  
    Inherits Plant  
    Public Property TrapType As String  
End Class  
  
Sub Cast()  
  
    Dim plants() As Plant = {   
        New CarnivorousPlant With {.Name = "Venus Fly Trap", .TrapType = "Snap Trap"},   
        New CarnivorousPlant With {.Name = "Pitcher Plant", .TrapType = "Pitfall Trap"},   
        New CarnivorousPlant With {.Name = "Sundew", .TrapType = "Flypaper Trap"},   
        New CarnivorousPlant With {.Name = "Waterwheel Plant", .TrapType = "Snap Trap"}}  
  
    Dim query = From plant As CarnivorousPlant In plants   
                Where plant.TrapType = "Snap Trap"   
                Select plant  
  
    Dim sb As New System.Text.StringBuilder()  
    For Each plant In query  
        sb.AppendLine(plant.Name)  
    Next  
  
    ' Display the results.  
    MsgBox(sb.ToString())  
  
    ' This code produces the following output:  
  
    ' Venus Fly Trap  
    ' Waterwheel Plant  
  
End Sub  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Linq></xref:System.Linq>   
 [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [From 子句](../../../../visual-basic/language-reference/queries/from-clause.md)   
 [如何︰ 使用 LINQ (Visual Basic) 查詢 ArrayList](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
