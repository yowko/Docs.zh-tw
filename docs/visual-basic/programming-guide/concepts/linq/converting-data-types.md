---
title: 轉換資料類型 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: 9821b2d6caad8feeac856185b92518c25de88da3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="converting-data-types-visual-basic"></a>轉換資料類型 (Visual Basic)
轉換方法會變更輸入物件的類型。  
  
 LINQ 查詢中的轉換作業可用於各種應用程式。 下列是一些範例：  
  
-   <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> 方法可以用來隱藏類型之標準查詢運算子的自訂實作。  
  
-   <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> 方法可以用來啟用非參數化集合以進行 LINQ 查詢。  
  
-   <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>、<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>、<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 和 <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> 方法可以用來強制立即執行查詢，而不是延後到列舉查詢。  
  
## <a name="methods"></a>方法  
 下表列出執行資料型別轉換的標準查詢運算子方法。  
  
 此表格中名稱開頭為"As" 的轉換方法會變更來源集合的靜態類型，而不是列舉它。 名稱開頭為 "To" 的方法會列舉來源集合，並將項目放入對應的集合類型。  
  
|方法名稱|描述|Visual Basic 查詢運算式語法|更多資訊|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|AsEnumerable|傳回 <xref:System.Collections.Generic.IEnumerable%601> 類型的輸入。|不適用。|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|AsQueryable|將 (泛型) <xref:System.Collections.IEnumerable> 轉換成 (泛型) <xref:System.Linq.IQueryable>。|不適用。|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|Cast|將集合的項目轉型為指定的類型。|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|OfType|根據可轉型為所指定類型的能力來篩選值。|不適用。|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|ToArray|將集合轉換為陣列。 這個方法會強制執行查詢。|不適用。|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|ToDictionary|根據索引鍵選取器函式，將項目放入 <xref:System.Collections.Generic.Dictionary%602>。 這個方法會強制執行查詢。|不適用。|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|ToList|將集合轉換成 <xref:System.Collections.Generic.List%601>。 這個方法會強制執行查詢。|不適用。|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|ToLookup|根據索引鍵選取器函式，將項目放入 <xref:System.Linq.Lookup%602> (一對多字典)。 這個方法會強制執行查詢。|不適用。|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>查詢運算式語法範例  
 下列程式碼範例使用`From As`子句，以存取僅適用於子型別成員之前的子型別類型轉型。  
  
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
 <xref:System.Linq>  
 [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [From 子句](../../../../visual-basic/language-reference/queries/from-clause.md)  
 [如何： 查詢 ArrayList 使用 LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
