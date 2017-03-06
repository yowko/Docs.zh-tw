---
title: "泛型型別 (泛型) 概觀"
description: "泛型型別 (泛型) 概觀"
keywords: .NET, .NET Core
author: kuhlenh
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: a315b111-8e48-446c-ab19-acb6405894a7
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 9827f9f37ce198b23bfd4e5fbca41cd86d5885a4
ms.lasthandoff: 03/02/2017

---

# <a name="generic-types-generics-overview"></a>泛型型別 (泛型) 概觀

我們經常會在 C# 中使用泛型，不論是隱含使用或明確使用。 當您在 C# 中使用 LINQ 時，您是否曾注意到您正在使用 IEnumerable<T>？ 如果您曾經看過使用 Entity Framework 與資料庫通訊的「一般儲存機制」線上範例，您是否注意到大部分的方法會傳回 IQueryable<T>？ 您可能想知道這些範例中的 **T** 為何，以及它出現在這裡的原因。

泛型是在 .NET Framework 2.0 中第一次引入，需要變更 C# 語言和 Common Language Runtime (CLR)。 **泛型**基本上是「程式碼範本」，可讓開發人員定義[型別安全](https://msdn.microsoft.com/library/hbzz1a9a.aspx)資料結構，而不需要認可至實際資料類型。 例如，`List<T>` 是可宣告的[泛型集合](https://msdn.microsoft.com/library/System.Collections.Generic.aspx)，並可搭配任何類型使用：`List<int>`、`List<string>`、`List<Person>` 等等。

重點到底是什麼？ 為什麼泛型很有用？ 若要了解這一點，我們必須看看加入泛型前後的特定類別。 以 `ArrayList` 為例。 在 C# 1.0 中，`ArrayList` 項目的類型是 `object`。 這表示任何加入的項目都會以無訊息模式轉換成 `object`；讀取清單中的項目時也會發生相同的情況 (此程序分別稱為 [Boxing](https://msdn.microsoft.com/library/yz2be5wk.aspx) 和 Unboxing)。 Boxing 和 Unboxing 會影響效能。 此外，您無法在編譯時期判斷清單中資料的實際類型。 因此很容易產生一些易損壞的程式碼。 泛型可以解決這個問題，它提供額外的資訊，也就是每個清單執行個體將包含之資料的類型。 簡單來說，您只能將整數加入 `List<int>`、只能將 Persons 加入 `List<Person>`，依此類推。

泛型也可用於執行階段，或加以**具體化**。 這表示執行階段知道您要使用的資料結構類型，因此可更有效率地將它儲存在記憶體中。

以下是一個小程式，說明如何有效率地得知執行階段的資料結構類型：

```cs
  using System;
  using System.Collections;
  using System.Collections.Generic;
  using System.Diagnostics;

  namespace GenericsExample {
    class Program {
      static void Main(string[] args) {
        //generic list
        List<int> ListGeneric = new List<int> { 5, 9, 1, 4 };
        //non-generic list
        ArrayList ListNonGeneric = new ArrayList { 5, 9, 1, 4 };
        // timer for generic list sort
        Stopwatch s = Stopwatch.StartNew();
        ListGeneric.Sort();
        s.Stop();
        Console.WriteLine($"Generic Sort: {ListGeneric}  \n Time taken: {s.Elapsed.TotalMilliseconds}ms");

        //timer for non-generic list sort
        Stopwatch s2 = Stopwatch.StartNew();
        ListNonGeneric.Sort();
        s2.Stop();
        Console.WriteLine($"Non-Generic Sort: {ListNonGeneric}  \n Time taken: {s2.Elapsed.TotalMilliseconds}ms");
        Console.ReadLine();
      }
    }
  }

```

此程式會產生下列輸出：

```console
Generic Sort: System.Collections.Generic.List\`1[System.Int32] Time taken: 0.0789ms
Non-Generic Sort: System.Collections.ArrayList Time taken: 2.4324ms

```

您在此首先會注意到，泛型清單的排序速度比非泛型清單的排序速度明顯更快。 您也可能注意到，泛型清單的類型是獨特的 ([System.Int32])，而非泛型清單的類型則是一般化。 因為執行階段知道泛型 `List<int>` 的類型是 int，所以它可以將清單項目儲存為記憶體中的基礎整數陣列，但非泛型 `ArrayList` 則必須將每個清單項目轉換成物件，再儲存為記憶體中的物件陣列。 如此範例所示，額外的轉換需要時間，因此會使清單排序速度變慢。

有關執行階段知道您的泛型類型的最後一個用處是改進偵錯體驗。 當您偵錯 C# 中的泛型時，您知道資料結構中的每個項目是何種類型。 如果沒有泛型，您就無法得知每個項目是何種類型。

## <a name="further-reading-and-resources"></a>延伸閱讀和資源

*   [C# 泛型簡介](https://msdn.microsoft.com/library/ms379564.aspx)
*   [C# 程式設計手冊 - 泛型](https://msdn.microsoft.com/library/512aeb7t.aspx)

