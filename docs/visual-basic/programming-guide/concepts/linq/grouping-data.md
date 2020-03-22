---
title: 分組資料
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: 9a4011b77f91ff241d23f7aeca95925a1e170483
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266816"
---
# <a name="grouping-data-visual-basic"></a>分組資料（可視基礎）
分組指的是將資料放在群組中，好讓每一個群組中的項目共用共同的屬性。  
  
 下圖顯示一系列字元的分組結果。 每個群組的索引鍵是字元。  
  
 ![顯示 LINQ 群組作業的圖表。](./media/grouping-data/linq-group-operation.png)  
  
 分組資料項目的標準查詢運算子方法詳列於下一節。  
  
## <a name="methods"></a>方法  
  
|方法名稱|描述|可視基本查詢運算式語法|相關資訊|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|GroupBy|共用共同屬性的群組項目。 每個群組都由一個 <xref:System.Linq.IGrouping%602> 物件代表。|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|ToLookup|根據索引鍵選取器函式，將元素插入 <xref:System.Linq.Lookup%602> (一對多字典)。|不適用。|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>查詢運算式語法範例  
 下列程式碼範例使用 `Group By` 子句，將整數依奇偶數分組至清單。  
  
```vb  
Dim numbers As New System.Collections.Generic.List(Of Integer)(  
     New Integer() {35, 44, 200, 84, 3987, 4, 199, 329, 446, 208})  
  
Dim query = From number In numbers
            Group By Remainder = (number Mod 2) Into Group  
  
Dim sb As New System.Text.StringBuilder()  
For Each group In query  
    sb.AppendLine(If(group.Remainder = 0, vbCrLf & "Even numbers:", vbCrLf & "Odd numbers:"))  
    For Each num In group.Group  
        sb.AppendLine(num)  
    Next  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' Odd numbers:  
' 35  
' 3987  
' 199  
' 329  
  
' Even numbers:  
' 44  
' 200  
' 84  
' 4  
' 446  
' 208  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Linq>
- [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [按子項分組](../../../../visual-basic/language-reference/queries/group-by-clause.md)
- [如何：按副檔名分組檔 （LINQ） （可視基本）](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)
- [如何：通過使用組 （LINQ） 將檔拆分為多個檔（可視基本）](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
