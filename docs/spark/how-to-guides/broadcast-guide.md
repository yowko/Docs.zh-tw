---
title: 使用 .NET 中的廣播變數進行 Apache Spark
description: 瞭解如何在 .NET 中使用廣播變數來 Apache Spark 應用程式。
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 55a52754439020bd2a925aa3e987fb4ad99c9c3d
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224003"
---
# <a name="use-broadcast-variables-in-net-for-apache-spark"></a>使用 .NET 中的廣播變數進行 Apache Spark

在本文中，您將瞭解如何在 .NET 中使用廣播變數進行 Apache Spark。 [Apache Spark 中的廣播變數](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) 是在應為唯讀的執行程式之間共用變數的機制。 廣播變數可讓您將唯讀變數保持在每部電腦上快取，而不是使用工作來傳送它的複本。 您可以使用廣播變數，以有效率的方式為每個節點提供大型輸入資料集的複本。

因為資料只會傳送一次，所以相較于每項工作的執行程式所附的區域變數，廣播變數有效能優勢。 請參閱 [官方廣播變數檔](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) ，以更深入瞭解廣播變數和使用的原因。

## <a name="create-broadcast-variables"></a>建立廣播變數

若要建立廣播變數，請呼叫 `SparkContext.Broadcast(v)` 任何變數 `v` 。 廣播變數是變數周圍的包裝函式 `v` ，其值可透過呼叫方法來存取 `Value()` 。

在下列程式碼片段中， `v` 會建立字串變數，並 `bv` 在呼叫時建立廣播變數 `SparkContext.Broadcast(v)` 。 請注意，字串的型別參數會比對 `Broadcast` 要廣播之變數的型別。  (UDF) 的使用者定義函數會傳回的值 `bv` 。

```csharp
string v = "Variable to be broadcasted";
Broadcast<string> bv = SparkContext.Broadcast(v);

Func<Column, Column> udf = Udf<string, string>(
    str => $"{str}: {bv.Value()}");
```

## <a name="delete-broadcast-variables"></a>刪除廣播變數

您可以藉由呼叫方法，從所有執行程式中刪除廣播變數 `Destroy()` 。

```csharp
bv.Destroy();
```

`Destroy()` 刪除與廣播變數相關的所有資料和中繼資料，而且應該謹慎使用。 一旦廣播變數損毀，就無法再使用。

## <a name="limit-broadcast-variable-scope-in-udfs"></a>限制 Udf 中的廣播變數範圍

當您在 Udf 中使用廣播變數時，您需要將變數的範圍限制為只有參考該變數的 UDF。 [使用 udf 的指南](udf-guide.md)會詳細說明這種現象。 當您 `Destroy()` 在廣播變數上呼叫時，範圍特別重要。

如果可從其他 Udf 看到或存取已終結的廣播變數，則所有 Udf 都會挑選它進行序列化，即使它們並未被參考也一樣。 .NET for Apache Spark 無法序列化終結的廣播變數，這會導致錯誤。 下列程式碼片段示範此錯誤：

```csharp
string v = "Variable to be broadcasted";
Broadcast<string> bv = SparkContext.Broadcast(v);

// Using the broadcast variable in a UDF:
Func<Column, Column> udf1 = Udf<string, string>(
    str => $"{str}: {bv.Value()}");

// Destroying bv
bv.Destroy();

// Calling udf1 after destroying bv throws the following expected exception:
// org.apache.spark.SparkException: Attempted to use Broadcast(0) after it was destroyed
df.Select(udf1(df["_1"])).Show();

// Different UDF udf2 that is not referencing bv
Func<Column, Column> udf2 = Udf<string, string>(
    str => $"{str}: not referencing broadcast variable");

// Calling udf2 throws the following (unexpected) exception:
// [Error] [JvmBridge] org.apache.spark.SparkException: Task not serializable
df.Select(udf2(df["_1"])).Show();
```

下列程式碼片段示範如何確保終結 `bv` `udf2` 因為未預期的序列化行為而不會受到影響：

```csharp
string v = "Variable to be broadcasted";
// Restricting the visibility of bv to only the UDF referencing it
{
    Broadcast<string> bv = SparkContext.Broadcast(v);

    // Using the broadcast variable in a UDF:
    Func<Column, Column> udf1 = Udf<string, string>(
        str => $"{str}: {bv.Value()}");

    // Destroying bv
    bv.Destroy();
}

// Different UDF udf2 that is not referencing bv
Func<Column, Column> udf2 = Udf<string, string>(
    str => $"{str}: not referencing broadcast variable");

// Calling udf2 works fine as expected
df.Select(udf2(df["_1"])).Show();
```

## <a name="next-steps"></a>後續步驟

* [開始使用 .NET for Apache Spark](../tutorials/get-started.md)
* [對 Windows 上的 .NET for Apache Spark 應用程式進行偵錯](debug.md)
* [針對 Apache Spark 背景工作角色和使用者定義函數二進位檔部署 .NET](deploy-worker-udf-binaries.md)
