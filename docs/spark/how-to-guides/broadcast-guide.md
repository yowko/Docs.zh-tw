---
title: 在 .NET 中使用廣播變數以進行 Apache Spark
description: 瞭解如何在 .NET 中針對 Apache Spark 應用程式使用廣播變數。
ms.date: 06/11/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 391e32cda14a9b3186ac96800351ddcb39a3d359
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105590"
---
# <a name="use-broadcast-variables-in-net-for-apache-spark"></a>在 .NET 中使用廣播變數以進行 Apache Spark

在本文中，您將瞭解如何在 .NET 中使用廣播變數以進行 Apache Spark。 [Apache Spark 中的廣播變數](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables)是跨多個執行程式共用變數的機制，這些都是唯讀的。 廣播變數可讓您保留在每部電腦上快取的唯讀變數，而不是使用工作傳送它的複本。 您可以使用廣播變數，以有效率的方式為每個節點提供大型輸入資料集的複本。

由於資料只會傳送一次，因此，相較于每個工作隨附于執行程式的本機變數，廣播變數的效能優勢。 請參閱[官方廣播變數檔](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables)，以更深入瞭解廣播變數及其使用原因。

## <a name="create-broadcast-variables"></a>建立廣播變數

若要建立廣播變數，請 `SparkContext.Broadcast(v)` 針對任何變數呼叫 `v` 。 廣播變數是變數周圍的包裝函式 `v` ，而其值可以藉由呼叫方法來存取 `Value()` 。

在下列程式碼片段中，會建立一個字串變數 `v` ，並 `bv` 在呼叫時建立廣播變數 `SparkContext.Broadcast(v)` 。 請注意，string 的類型參數會 `Broadcast` 符合所要廣播的變數類型。 使用者定義函數（UDF）會傳回的值 `bv` 。

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

`Destroy()`刪除與廣播變數相關的所有資料和中繼資料，並謹慎使用。 一旦廣播變數損毀，就無法再次使用。

## <a name="limit-broadcast-variable-scope-in-udfs"></a>限制 Udf 中的廣播變數範圍

當您在 Udf 中使用廣播變數時，您必須將變數的範圍限制為只有參考該變數的 UDF。 [使用 udf 的指南](udf-guide.md)會詳細說明這種現象。 當您 `Destroy()` 在廣播變數上呼叫時，範圍特別重要。

如果已終結的廣播變數可在其他 Udf 看到或可供存取，則所有 Udf 都會挑選它進行序列化，即使它們未被參考。 適用于 Apache Spark 的 .NET 無法序列化已終結的廣播變數，這會導致錯誤。 下列程式碼片段示範此錯誤：

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

下列程式碼片段示範如何確保終結 `bv` `udf2` 因非預期的序列化行為而不會影響：

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
* [針對 Apache Spark 的背景工作角色和使用者定義的函數二進位檔部署 .NET](deploy-worker-udf-binaries.md)
