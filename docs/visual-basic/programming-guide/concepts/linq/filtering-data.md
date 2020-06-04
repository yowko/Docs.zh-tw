---
title: 篩選資料
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: f7a1aa76dc93cc03952e55f5f8fc3f75176a3f9f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84383413"
---
# <a name="filtering-data-visual-basic"></a>篩選資料（Visual Basic）

篩選指的是將結果集限制為只包含符合指定條件之元素的作業， 也稱為選取。

下圖顯示字元序列的篩選結果。 篩選作業的述詞指定字元必須為 'A'。

![顯示 LINQ 篩選作業的圖表](./media/filtering-data/linq-filter-operation.png)

執行選取的標準查詢運算子方法詳列於下一節。

## <a name="methods"></a>方法

|方法名稱|Description|Visual Basic 查詢運算式語法|相關資訊|
|-----------------|-----------------|------------------------------------------|----------------------|
|OfType|根據可轉換為所指定類型的能力來選取值。|不適用。|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|Where|根據述詞函式來選取值。|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a>查詢運算式語法範例

下列範例會使用， `Where` 從陣列中篩選具有特定長度的字串。

```vb
Dim words() As String = {"the", "quick", "brown", "fox", "jumps"}

Dim query = From word In words
            Where word.Length = 3
            Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In query
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' fox
```

## <a name="see-also"></a>另請參閱

- <xref:System.Linq>
- [標準查詢運算子概觀 (Visual Basic)](standard-query-operators-overview.md)
- [Where 子句](../../../language-reference/queries/where-clause.md)
- [如何：篩選查詢結果](../../language-features/linq/how-to-filter-query-results-by-using-linq.md)
- [如何：使用反映查詢元件的中繼資料（LINQ）（Visual Basic）](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [如何：查詢具有指定之屬性或名稱的檔案（Visual Basic）](how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [如何：依任何字或欄位排序或篩選文字資料 (LINQ) (Visual Basic)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
