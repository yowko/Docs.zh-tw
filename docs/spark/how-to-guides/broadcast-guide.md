---
title: 使用 .NET 中的廣播變數進行 Apache Spark
description: 瞭解如何在 .NET 中使用廣播變數來 Apache Spark 應用程式。
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: ca6dab01cbd639594da0b51f145272a9a150e93c
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687749"
---
# <a name="use-broadcast-variables-in-net-for-apache-spark"></a><span data-ttu-id="7f773-103">使用 .NET 中的廣播變數進行 Apache Spark</span><span class="sxs-lookup"><span data-stu-id="7f773-103">Use broadcast variables in .NET for Apache Spark</span></span>

<span data-ttu-id="7f773-104">在本文中，您將瞭解如何在 .NET 中使用廣播變數進行 Apache Spark。</span><span class="sxs-lookup"><span data-stu-id="7f773-104">In this article, you learn how to use broadcast variables in .NET for Apache Spark.</span></span> <span data-ttu-id="7f773-105">[Apache Spark 中的廣播變數](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) 是在應為唯讀的執行程式之間共用變數的機制。</span><span class="sxs-lookup"><span data-stu-id="7f773-105">[Broadcast variables in Apache Spark](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) are mechanisms for sharing variables across executors that are meant to be read-only.</span></span> <span data-ttu-id="7f773-106">廣播變數可讓您將唯讀變數保持在每部電腦上快取，而不是使用工作來傳送它的複本。</span><span class="sxs-lookup"><span data-stu-id="7f773-106">Broadcast variables allow you to keep a read-only variable cached on each machine rather than shipping a copy of it with tasks.</span></span> <span data-ttu-id="7f773-107">您可以使用廣播變數，以有效率的方式為每個節點提供大型輸入資料集的複本。</span><span class="sxs-lookup"><span data-stu-id="7f773-107">You can use broadcast variables to give every node a copy of a large input dataset in an efficient manner.</span></span>

<span data-ttu-id="7f773-108">因為資料只會傳送一次，所以相較于每項工作的執行程式所附的區域變數，廣播變數有效能優勢。</span><span class="sxs-lookup"><span data-stu-id="7f773-108">Because the data is sent only once, broadcast variables have performance benefits when compared to local variables that are shipped to the executors with each task.</span></span> <span data-ttu-id="7f773-109">請參閱 [官方廣播變數檔](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) ，以更深入瞭解廣播變數和使用的原因。</span><span class="sxs-lookup"><span data-stu-id="7f773-109">Refer to the [official broadcast variable documentation](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) to get a deeper understanding of broadcast variables and why they are used.</span></span>

## <a name="create-broadcast-variables"></a><span data-ttu-id="7f773-110">建立廣播變數</span><span class="sxs-lookup"><span data-stu-id="7f773-110">Create broadcast variables</span></span>

<span data-ttu-id="7f773-111">若要建立廣播變數，請呼叫 `SparkContext.Broadcast(v)` 任何變數 `v` 。</span><span class="sxs-lookup"><span data-stu-id="7f773-111">To create a broadcast variable, call `SparkContext.Broadcast(v)` for any variable `v`.</span></span> <span data-ttu-id="7f773-112">廣播變數是變數周圍的包裝函式 `v` ，其值可透過呼叫方法來存取 `Value()` 。</span><span class="sxs-lookup"><span data-stu-id="7f773-112">The broadcast variable is a wrapper around the variable `v`, and its value can be accessed by calling the `Value()` method.</span></span>

<span data-ttu-id="7f773-113">在下列程式碼片段中， `v` 會建立字串變數，並 `bv` 在呼叫時建立廣播變數 `SparkContext.Broadcast(v)` 。</span><span class="sxs-lookup"><span data-stu-id="7f773-113">In the following code snippet, a string variable `v` is created, and a broadcast variable `bv` is created when `SparkContext.Broadcast(v)`is called.</span></span> <span data-ttu-id="7f773-114">請注意，字串的型別參數會比對 `Broadcast` 要廣播之變數的型別。</span><span class="sxs-lookup"><span data-stu-id="7f773-114">Notice the type parameter for `Broadcast`, string, matches the type of the variable being broadcasted.</span></span> <span data-ttu-id="7f773-115"> (UDF) 的使用者定義函數會傳回的值 `bv` 。</span><span class="sxs-lookup"><span data-stu-id="7f773-115">The user-defined function (UDF) returns the value of `bv`.</span></span>

```csharp
string v = "Variable to be broadcasted";
Broadcast<string> bv = SparkContext.Broadcast(v);

Func<Column, Column> udf = Udf<string, string>(
    str => $"{str}: {bv.Value()}");
```

## <a name="delete-broadcast-variables"></a><span data-ttu-id="7f773-116">刪除廣播變數</span><span class="sxs-lookup"><span data-stu-id="7f773-116">Delete broadcast variables</span></span>

<span data-ttu-id="7f773-117">您可以藉由呼叫方法，從所有執行程式中刪除廣播變數 `Destroy()` 。</span><span class="sxs-lookup"><span data-stu-id="7f773-117">The broadcast variable can be deleted from all executors by calling the `Destroy()` method.</span></span>

```csharp
bv.Destroy();
```

<span data-ttu-id="7f773-118">`Destroy()` 刪除與廣播變數相關的所有資料和中繼資料，而且應該謹慎使用。</span><span class="sxs-lookup"><span data-stu-id="7f773-118">`Destroy()` deletes all data and metadata related to the broadcast variable and should be used with caution.</span></span> <span data-ttu-id="7f773-119">一旦廣播變數損毀，就無法再使用。</span><span class="sxs-lookup"><span data-stu-id="7f773-119">Once a broadcast variable is destroyed, it can't be used again.</span></span>

## <a name="limit-broadcast-variable-scope-in-udfs"></a><span data-ttu-id="7f773-120">限制 Udf 中的廣播變數範圍</span><span class="sxs-lookup"><span data-stu-id="7f773-120">Limit broadcast variable scope in UDFs</span></span>

<span data-ttu-id="7f773-121">當您在 Udf 中使用廣播變數時，您需要將變數的範圍限制為只有參考該變數的 UDF。</span><span class="sxs-lookup"><span data-stu-id="7f773-121">When you use broadcast variables in UDFs, you need to limit the scope of the variable to only the UDF that is referencing the variable.</span></span> <span data-ttu-id="7f773-122">[使用 udf 的指南](udf-guide.md)會詳細說明這種現象。</span><span class="sxs-lookup"><span data-stu-id="7f773-122">The [guide to using UDFs](udf-guide.md) describes this phenomenon in detail.</span></span> <span data-ttu-id="7f773-123">當您 `Destroy()` 在廣播變數上呼叫時，範圍特別重要。</span><span class="sxs-lookup"><span data-stu-id="7f773-123">Scope is especially crucial when you call `Destroy()` on the broadcast variable.</span></span>

<span data-ttu-id="7f773-124">如果可從其他 Udf 看到或存取已終結的廣播變數，則所有 Udf 都會挑選它進行序列化，即使它們並未被參考也一樣。</span><span class="sxs-lookup"><span data-stu-id="7f773-124">If the broadcast variable that has been destroyed is visible to or accessible from other UDFs, it gets picked up for serialization by all of the UDFs, even if it is not being referenced by them.</span></span> <span data-ttu-id="7f773-125">.NET for Apache Spark 無法序列化終結的廣播變數，這會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="7f773-125">.NET for Apache Spark is unable to serialize the destroyed broadcast variable, which results in an error.</span></span> <span data-ttu-id="7f773-126">下列程式碼片段示範此錯誤：</span><span class="sxs-lookup"><span data-stu-id="7f773-126">The following code snippet demonstrates this error:</span></span>

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

<span data-ttu-id="7f773-127">下列程式碼片段示範如何確保終結 `bv` `udf2` 因為未預期的序列化行為而不會受到影響：</span><span class="sxs-lookup"><span data-stu-id="7f773-127">The following code snippet demonstrates how to ensure that destroying `bv` doesn't affect `udf2` because of an unexpected serialization behavior:</span></span>

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

## <a name="faqs"></a><span data-ttu-id="7f773-128">常見問題集</span><span class="sxs-lookup"><span data-stu-id="7f773-128">FAQs</span></span>

<span data-ttu-id="7f773-129">**為什麼廣播變數適用于 .NET Interactive？**</span><span class="sxs-lookup"><span data-stu-id="7f773-129">**Why don't Broadcast Variables work with .NET Interactive?**</span></span>  
<span data-ttu-id="7f773-130">廣播變數不適用於互動式案例，因為 .NET 互動的設計會附加儲存格所定義的每個物件及其資料格提交類別，因為它不會標示為可序列化，所以會因為先前所示的相同例外狀況而失敗。</span><span class="sxs-lookup"><span data-stu-id="7f773-130">Broadcast variables don't work with interactive scenarios because of .NET interactive's design of appending each object defined in a cell with its cell submission class, which since is not marked serializable, fails with the same exception as shown previously.</span></span> <span data-ttu-id="7f773-131">如需詳細資訊，請參閱 [這篇文章](dotnet-interactive-udf-issue.md)。</span><span class="sxs-lookup"><span data-stu-id="7f773-131">For more information, please check out [this article](dotnet-interactive-udf-issue.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="7f773-132">後續步驟</span><span class="sxs-lookup"><span data-stu-id="7f773-132">Next steps</span></span>

* [<span data-ttu-id="7f773-133">開始使用 .NET for Apache Spark</span><span class="sxs-lookup"><span data-stu-id="7f773-133">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="7f773-134">對 Windows 上的 .NET for Apache Spark 應用程式進行偵錯</span><span class="sxs-lookup"><span data-stu-id="7f773-134">Debug a .NET for Apache Spark application on Windows</span></span>](debug.md)
* [<span data-ttu-id="7f773-135">針對 Apache Spark 背景工作角色和使用者定義函數二進位檔部署 .NET</span><span class="sxs-lookup"><span data-stu-id="7f773-135">Deploy .NET for Apache Spark worker and user-defined function binaries</span></span>](deploy-worker-udf-binaries.md)
