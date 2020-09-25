---
title: 分組資料 (C#)
description: '群組會將資料放入共用屬性的元素群組中。 深入瞭解 c # 中的標準查詢運算子方法（以 c # 分組資料元素）。'
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: 584d50fc15dd8b4ce1cfdf4766f3bc8b8383eb12
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202561"
---
# <a name="grouping-data-c"></a>分組資料 (C#)

分組指的是將資料放在群組中，好讓每一個群組中的項目共用共同的屬性。  
  
 下圖顯示一系列字元的分組結果。 每個群組的索引鍵是字元。  
  
 ![顯示 LINQ 群組作業的圖表。](./media/grouping-data/linq-group-operation.png)  
  
 分組資料項目的標準查詢運算子方法詳列於下一節。  
  
## <a name="methods"></a>方法  
  
|方法名稱|描述|C# 查詢運算式語法|相關資訊|  
|-----------------|-----------------|---------------------------------|----------------------|  
|GroupBy|共用共同屬性的群組項目。 每個群組都由一個 <xref:System.Linq.IGrouping%602> 物件代表。|`group … by`<br /><br /> -或-<br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|ToLookup|根據索引鍵選取器函式，將元素插入 <xref:System.Linq.Lookup%602> (一對多字典)。|不適用。|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>查詢運算式語法範例  

 下列程式碼範例使用 `group by` 子句，將整數依奇偶數分組至清單。  
  
```csharp  
List<int> numbers = new List<int>() { 35, 44, 200, 84, 3987, 4, 199, 329, 446, 208 };  
  
IEnumerable<IGrouping<int, int>> query = from number in numbers  
                                         group number by number % 2;  
  
foreach (var group in query)  
{  
    Console.WriteLine(group.Key == 0 ? "\nEven numbers:" : "\nOdd numbers:");  
    foreach (int i in group)  
        Console.WriteLine(i);  
}  
  
/* This code produces the following output:  
  
    Odd numbers:  
    35  
    3987  
    199  
    329  
  
    Even numbers:  
    44  
    200  
    84  
    4  
    446  
    208  
*/  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Linq>
- [標準查詢運算子概觀 (C#)](./standard-query-operators-overview.md)
- [group 子句](../../../language-reference/keywords/group-clause.md)
- [建立巢狀群組](../../../linq/create-a-nested-group.md)
- [如何依擴充功能將檔案分組 (LINQ)  (c # ) ](./how-to-group-files-by-extension-linq.md)
- [將查詢結果分組](../../../linq/group-query-results.md)
- [在分組作業上執行子查詢](../../../linq/perform-a-subquery-on-a-grouping-operation.md)
- [如何使用群組 (LINQ)  (c # 將檔案分割成許多檔案 ) ](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
