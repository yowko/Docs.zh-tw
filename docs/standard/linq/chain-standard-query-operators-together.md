---
title: '將標準查詢運算子一起 (c # ) -LINQ to XML'
description: 瞭解如何將查詢運算子串聯在一起。
ms.date: 07/20/2015
dev_langs:
- csharp
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: ed3ca44c853ebbeee690cb31232a13e35b383d1b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552101"
---
# <a name="chain-standard-query-operators-together-c-linq-to-xml"></a>將標準查詢運算子一起 (c # )  (LINQ to XML) 

標準查詢運算子可以連結在一起。 例如，您可以插入子句所叫 <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> 用的運算子 (`where`) ，它會以延遲的方式運作，也就是說，它不會具體化中繼結果。

## <a name="example-interject-a-where-clause"></a>範例：插入 where 子句

在此範例中，呼叫 <xref:System.Linq.Enumerable.Where%2A> 前，會先呼叫 `ConvertCollectionToUpperCase` 方法。 <xref:System.Linq.Enumerable.Where%2A> 方法會使用與本教學課程之前範例、`ConvertCollectionToUpperCase` 和 `AppendString` 中所使用之延遲方法幾乎完全相同的方式操作。

其中一個差異是，在此情況下， <xref:System.Linq.Enumerable.Where%2A> 方法會逐一查看其來源集合，判斷第一個專案不會通過述詞，然後取得下一個專案，而該專案會通過。 它接著會產生第二個項目。

不過，基本概念是相同的：不會具體化中繼集合，除非它們必須是。

使用查詢運算式時，會將它們轉換為對標準查詢運算子的呼叫，並套用相同的原則。

本節中，查詢 Office Open XML 文件的所有範例都使用相同的原則。 延後執行和延遲評估是一些基本概念，您必須瞭解這些概念才能使用 LINQ，並有效 LINQ to XML。

```csharp
public static class LocalExtensions
{
    public static IEnumerable<string>
      ConvertCollectionToUpperCase(this IEnumerable<string> source)
    {
        foreach (string str in source)
        {
            Console.WriteLine("ToUpper: source >{0}<", str);
            yield return str.ToUpper();
        }
    }

    public static IEnumerable<string>
      AppendString(this IEnumerable<string> source, string stringToAppend)
    {
        foreach (string str in source)
        {
            Console.WriteLine("AppendString: source >{0}<", str);
            yield return str + stringToAppend;
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        string[] stringArray = { "abc", "def", "ghi" };

        IEnumerable<string> q1 =
            from s in stringArray.ConvertCollectionToUpperCase()
            where s.CompareTo("D") >= 0
            select s;

        IEnumerable<string> q2 =
            from s in q1.AppendString("!!!")
            select s;

        foreach (string str in q2)
        {
            Console.WriteLine("Main: str >{0}<", str);
            Console.WriteLine();
        }
    }
}
```

這個範例會產生下列輸出：

```output
ToUpper: source >abc<
ToUpper: source >def<
AppendString: source >DEF<
Main: str >DEF!!!<

ToUpper: source >ghi<
AppendString: source >GHI<
Main: str >GHI!!!<
```

這是本教學課程中的最後一篇文章 [： (c # ) ](chain-queries-example.md) 教學課程將查詢連結在一起。
