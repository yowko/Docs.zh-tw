---
title: 延後執行範例-LINQ to XML
description: 瞭解延後執行和延遲評估如何影響 LINQ to XML 查詢的執行。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: 59784db895211aecbd263b5ee050734ecd16fa4b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552266"
---
# <a name="deferred-execution-example-linq-to-xml"></a>延後執行範例 (LINQ to XML) 

本文說明延後執行和延遲評估如何影響 LINQ to XML 查詢的執行。

## <a name="example-use-the-yield-return-construct-in-an-extension-method-to-defer-execution"></a>範例： `yield return` 在擴充方法中使用結構來順延強制

下列範例顯示利用使用延後執行的擴充方法時的執行順序。 此範例會宣告三個字串的陣列。 接著，它會逐一查看 `ConvertCollectionToUpperCase` 所傳回的集合。

```csharp
public static class LocalExtensions
{
    public static IEnumerable<string>
      ConvertCollectionToUpperCase(this IEnumerable<string> source)
    {
        foreach (string str in source)
        {
            Console.WriteLine("ToUpper: source {0}", str);
            yield return str.ToUpper();
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        string[] stringArray = { "abc", "def", "ghi" };

        var q = from str in stringArray.ConvertCollectionToUpperCase()
                select str;

        foreach (string str in q)
            Console.WriteLine("Main: str {0}", str);
    }
}
```

```vb
Imports System.Runtime.CompilerServices

Module Module1

    <Extension()>
    Private Iterator Function ConvertCollectionToUpperCase(
    ByVal source As IEnumerable(Of String)) _
    As IEnumerable(Of String)
        For Each str As String In source
            Console.WriteLine("ToUpper: source {0}", str)
            Yield str.ToUpper()
        Next
    End Function

    Sub Main()
        Dim stringArray = New String() {"abc", "def", "ghi"}

        Dim q = From str In stringArray.ConvertCollectionToUpperCase()
                Select str

        For Each Str As String In q
            Console.WriteLine("Main: str {0}", Str)
        Next
    End Sub

End Module
```

這個範例會產生下列輸出：

```output
ToUpper: source abc
Main: str ABC
ToUpper: source def
Main: str DEF
ToUpper: source ghi
Main: str GHI
```

請注意，逐一查看 `ConvertCollectionToUpperCase` 所傳回的集合時，會從來源字串陣列擷取每個項目，並在下一個項目從來源字串陣列擷取前，轉換為大寫。

您可以看到，在中的迴圈中處理傳回集合中的每個專案之前，字串的整個陣列都不會轉換成大寫 `foreach` `Main` 。

## <a name="see-also"></a>另請參閱

- [延後執行和延遲評估](deferred-execution-lazy-evaluation.md)
- [教學課程：搭配 (c # ) 的連鎖查詢 ](chain-queries-example.md)
