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
# <a name="use-broadcast-variables-in-net-for-apache-spark"></a><span data-ttu-id="80714-103">在 .NET 中使用廣播變數以進行 Apache Spark</span><span class="sxs-lookup"><span data-stu-id="80714-103">Use broadcast variables in .NET for Apache Spark</span></span>

<span data-ttu-id="80714-104">在本文中，您將瞭解如何在 .NET 中使用廣播變數以進行 Apache Spark。</span><span class="sxs-lookup"><span data-stu-id="80714-104">In this article, you learn how to use broadcast variables in .NET for Apache Spark.</span></span> <span data-ttu-id="80714-105">[Apache Spark 中的廣播變數](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables)是跨多個執行程式共用變數的機制，這些都是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="80714-105">[Broadcast variables in Apache Spark](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) are mechanisms for sharing variables across executors that are meant to be read-only.</span></span> <span data-ttu-id="80714-106">廣播變數可讓您保留在每部電腦上快取的唯讀變數，而不是使用工作傳送它的複本。</span><span class="sxs-lookup"><span data-stu-id="80714-106">Broadcast variables allow you to keep a read-only variable cached on each machine rather than shipping a copy of it with tasks.</span></span> <span data-ttu-id="80714-107">您可以使用廣播變數，以有效率的方式為每個節點提供大型輸入資料集的複本。</span><span class="sxs-lookup"><span data-stu-id="80714-107">You can use broadcast variables to give every node a copy of a large input dataset in an efficient manner.</span></span>

<span data-ttu-id="80714-108">由於資料只會傳送一次，因此，相較于每個工作隨附于執行程式的本機變數，廣播變數的效能優勢。</span><span class="sxs-lookup"><span data-stu-id="80714-108">Because the data is sent only once, broadcast variables have performance benefits when compared to local variables that are shipped to the executors with each task.</span></span> <span data-ttu-id="80714-109">請參閱[官方廣播變數檔](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables)，以更深入瞭解廣播變數及其使用原因。</span><span class="sxs-lookup"><span data-stu-id="80714-109">Refer to the [official broadcast variable documentation](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) to get a deeper understanding of broadcast variables and why they are used.</span></span>

## <a name="create-broadcast-variables"></a><span data-ttu-id="80714-110">建立廣播變數</span><span class="sxs-lookup"><span data-stu-id="80714-110">Create broadcast variables</span></span>

<span data-ttu-id="80714-111">若要建立廣播變數，請 `SparkContext.Broadcast(v)` 針對任何變數呼叫 `v` 。</span><span class="sxs-lookup"><span data-stu-id="80714-111">To create a broadcast variable, call `SparkContext.Broadcast(v)` for any variable `v`.</span></span> <span data-ttu-id="80714-112">廣播變數是變數周圍的包裝函式 `v` ，而其值可以藉由呼叫方法來存取 `Value()` 。</span><span class="sxs-lookup"><span data-stu-id="80714-112">The broadcast variable is a wrapper around the variable `v`, and its value can be accessed by calling the `Value()` method.</span></span>

<span data-ttu-id="80714-113">在下列程式碼片段中，會建立一個字串變數 `v` ，並 `bv` 在呼叫時建立廣播變數 `SparkContext.Broadcast(v)` 。</span><span class="sxs-lookup"><span data-stu-id="80714-113">In the following code snippet, a string variable `v` is created, and a broadcast variable `bv` is created when `SparkContext.Broadcast(v)`is called.</span></span> <span data-ttu-id="80714-114">請注意，string 的類型參數會 `Broadcast` 符合所要廣播的變數類型。</span><span class="sxs-lookup"><span data-stu-id="80714-114">Notice the type parameter for `Broadcast`, string, matches the type of the variable being broadcasted.</span></span> <span data-ttu-id="80714-115">使用者定義函數（UDF）會傳回的值 `bv` 。</span><span class="sxs-lookup"><span data-stu-id="80714-115">The user-defined function (UDF) returns the value of `bv`.</span></span>

```csharp
string v = "Variable to be broadcasted";
Broadcast<string> bv = SparkContext.Broadcast(v);

Func<Column, Column> udf = Udf<string, string>(
    str => $"{str}: {bv.Value()}");
```

## <a name="delete-broadcast-variables"></a><span data-ttu-id="80714-116">刪除廣播變數</span><span class="sxs-lookup"><span data-stu-id="80714-116">Delete broadcast variables</span></span>

<span data-ttu-id="80714-117">您可以藉由呼叫方法，從所有執行程式中刪除廣播變數 `Destroy()` 。</span><span class="sxs-lookup"><span data-stu-id="80714-117">The broadcast variable can be deleted from all executors by calling the `Destroy()` method.</span></span>

```csharp
bv.Destroy();
```

<span data-ttu-id="80714-118">`Destroy()`刪除與廣播變數相關的所有資料和中繼資料，並謹慎使用。</span><span class="sxs-lookup"><span data-stu-id="80714-118">`Destroy()` deletes all data and metadata related to the broadcast variable and should be used with caution.</span></span> <span data-ttu-id="80714-119">一旦廣播變數損毀，就無法再次使用。</span><span class="sxs-lookup"><span data-stu-id="80714-119">Once a broadcast variable is destroyed, it can't be used again.</span></span>

## <a name="limit-broadcast-variable-scope-in-udfs"></a><span data-ttu-id="80714-120">限制 Udf 中的廣播變數範圍</span><span class="sxs-lookup"><span data-stu-id="80714-120">Limit broadcast variable scope in UDFs</span></span>

<span data-ttu-id="80714-121">當您在 Udf 中使用廣播變數時，您必須將變數的範圍限制為只有參考該變數的 UDF。</span><span class="sxs-lookup"><span data-stu-id="80714-121">When you use broadcast variables in UDFs, you need to limit the scope of the variable to only the UDF that is referencing the variable.</span></span> <span data-ttu-id="80714-122">[使用 udf 的指南](udf-guide.md)會詳細說明這種現象。</span><span class="sxs-lookup"><span data-stu-id="80714-122">The [guide to using UDFs](udf-guide.md) describes this phenomenon in detail.</span></span> <span data-ttu-id="80714-123">當您 `Destroy()` 在廣播變數上呼叫時，範圍特別重要。</span><span class="sxs-lookup"><span data-stu-id="80714-123">Scope is especially crucial when you call `Destroy()` on the broadcast variable.</span></span>

<span data-ttu-id="80714-124">如果已終結的廣播變數可在其他 Udf 看到或可供存取，則所有 Udf 都會挑選它進行序列化，即使它們未被參考。</span><span class="sxs-lookup"><span data-stu-id="80714-124">If the broadcast variable that has been destroyed is visible to or accessible from other UDFs, it gets picked up for serialization by all of the UDFs, even if it is not being referenced by them.</span></span> <span data-ttu-id="80714-125">適用于 Apache Spark 的 .NET 無法序列化已終結的廣播變數，這會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="80714-125">.NET for Apache Spark is unable to serialize the destroyed broadcast variable, which results in an error.</span></span> <span data-ttu-id="80714-126">下列程式碼片段示範此錯誤：</span><span class="sxs-lookup"><span data-stu-id="80714-126">The following code snippet demonstrates this error:</span></span>

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

<span data-ttu-id="80714-127">下列程式碼片段示範如何確保終結 `bv` `udf2` 因非預期的序列化行為而不會影響：</span><span class="sxs-lookup"><span data-stu-id="80714-127">The following code snippet demonstrates how to ensure that destroying `bv` doesn't affect `udf2` because of an unexpected serialization behavior:</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="80714-128">後續步驟</span><span class="sxs-lookup"><span data-stu-id="80714-128">Next steps</span></span>

* [<span data-ttu-id="80714-129">開始使用 .NET for Apache Spark</span><span class="sxs-lookup"><span data-stu-id="80714-129">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="80714-130">對 Windows 上的 .NET for Apache Spark 應用程式進行偵錯</span><span class="sxs-lookup"><span data-stu-id="80714-130">Debug a .NET for Apache Spark application on Windows</span></span>](debug.md)
* [<span data-ttu-id="80714-131">針對 Apache Spark 的背景工作角色和使用者定義的函數二進位檔部署 .NET</span><span class="sxs-lookup"><span data-stu-id="80714-131">Deploy .NET for Apache Spark worker and user-defined function binaries</span></span>](deploy-worker-udf-binaries.md)
