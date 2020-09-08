---
title: " (c # ) 的連鎖查詢範例-LINQ to XML"
description: 瞭解當您將兩個同時使用延後執行和延遲評估的查詢串聯在一起時，會發生什麼事。
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: c0bbab9061b98eda15523f8a8e64e997bde8b307
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552271"
---
# <a name="chain-queries-example-c-linq-to-xml"></a> (c # )  (LINQ to XML 的連鎖查詢範例) 

此範例以 [延後執行範例](deferred-execution-example.md) 中的範例為基礎，並顯示當您將兩個同時使用延後執行和延遲評估的查詢串連在一起時，會發生什麼事。

## <a name="example-add-a-second-extension-method-that-uses-yield-return-to-defer-execution"></a>範例：新增第二個使用的擴充方法 `yield return` 來順延強制

在此範例中，會引進另一個擴充方法，此方法會將 `AppendString` 指定的字串附加至來源集合中的每個字串，然後產生已變更的字串。

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
AppendString: source >ABC<
Main: str >ABC!!!<

ToUpper: source >def<
AppendString: source >DEF<
Main: str >DEF!!!<

ToUpper: source >ghi<
AppendString: source >GHI<
Main: str >GHI!!!<
```

在此範例中，您可以看到每個擴充方法會針對來源集合中的每個項目，一次運算一個。

從這個範例應該清楚知道的是，即使我們已經將產生集合的查詢鏈結在一起，還是不會具體化任何中繼集合。 但是，每個項目都會從一個延遲方法傳遞到下一個延遲方法。 這會使記憶體使用量比先取得一個字串陣列，然後建立已經轉換為大寫的另一個字串陣列，最後建立每個字串都已經附加驚嘆號的第三個字串陣列這種方法小很多。

本教學課程的下一篇文章說明中繼具體化：

- [中繼具體化 (c # ) ](intermediate-materialization.md)

## <a name="see-also"></a>另請參閱

- [延後執行和延遲評估](deferred-execution-lazy-evaluation.md)
