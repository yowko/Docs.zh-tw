---
title: 轉換資料型別 (C#)
description: '轉換方法會變更輸入物件的類型。 請參閱 c # 中的 LINQ 查詢中的轉換作業，例如可列舉的 Enumerable.asenumerable 和可列舉的 OfType。'
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 3291690f9aaee945ca7feb04ebbc676db2612894
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105490"
---
# <a name="converting-data-types-c"></a>轉換資料型別 (C#)
轉換方法會變更輸入物件的類型。

 LINQ 查詢中的轉換作業可用於各種應用程式。 下列是一些範例：

- <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> 方法可以用來隱藏類型之標準查詢運算子的自訂實作。

- <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> 方法可以用來啟用非參數化集合以進行 LINQ 查詢。

- <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>、<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>、<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 和 <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> 方法可以用來強制立即執行查詢，而不是延後到列舉查詢。

## <a name="methods"></a>方法
 下表列出執行資料型別轉換的標準查詢運算子方法。

 此表格中名稱開頭為"As" 的轉換方法會變更來源集合的靜態類型，而不是列舉它。 名稱開頭為 "To" 的方法會列舉來源集合，並將項目放入對應的集合類型。

|方法名稱|說明|C# 查詢運算式語法|相關資訊|
|-----------------|-----------------|---------------------------------|----------------------|
|AsEnumerable|傳回 <xref:System.Collections.Generic.IEnumerable%601> 類型的輸入。|不適用。|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|AsQueryable|將 (泛型) <xref:System.Collections.IEnumerable> 轉換成 (泛型) <xref:System.Linq.IQueryable>。|不適用。|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|轉換|將集合的項目轉型為指定的類型。|使用類型明確的範圍變數。 例如:<br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|OfType|根據可轉型為所指定類型的能力來篩選值。|不適用。|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|ToArray|將集合轉換為陣列。 這個方法會強制執行查詢。|不適用。|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|ToDictionary|根據索引鍵選取器函式，將項目放入 <xref:System.Collections.Generic.Dictionary%602>。 這個方法會強制執行查詢。|不適用。|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|ToList|將集合轉換成 <xref:System.Collections.Generic.List%601>。 這個方法會強制執行查詢。|不適用。|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|ToLookup|根據索引鍵選取器函式，將項目放入 <xref:System.Linq.Lookup%602> (一對多字典)。 這個方法會強制執行查詢。|不適用。|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a>查詢運算式語法範例

下列程式碼範例會使用明確類型的範圍變數，將類型轉換成子類型，然後才存取僅適用于子類型的成員。

```csharp
class Plant
{
    public string Name { get; set; }
}

class CarnivorousPlant : Plant
{
    public string TrapType { get; set; }
}

static void Cast()
{
    Plant[] plants = new Plant[] {
        new CarnivorousPlant { Name = "Venus Fly Trap", TrapType = "Snap Trap" },
        new CarnivorousPlant { Name = "Pitcher Plant", TrapType = "Pitfall Trap" },
        new CarnivorousPlant { Name = "Sundew", TrapType = "Flypaper Trap" },
        new CarnivorousPlant { Name = "Waterwheel Plant", TrapType = "Snap Trap" }
    };

    var query = from CarnivorousPlant cPlant in plants
                where cPlant.TrapType == "Snap Trap"
                select cPlant;

    foreach (Plant plant in query)
        Console.WriteLine(plant.Name);

    /* This code produces the following output:

        Venus Fly Trap
        Waterwheel Plant
    */
}
```

## <a name="see-also"></a>請參閱

- <xref:System.Linq>
- [標準查詢運算子概觀 (C#)](./standard-query-operators-overview.md)
- [from 子句](../../../language-reference/keywords/from-clause.md)
- [LINQ 查詢運算式](../../../linq/index.md)
- [如何使用 LINQ 查詢 ArrayList （c #）](./how-to-query-an-arraylist-with-linq.md)
