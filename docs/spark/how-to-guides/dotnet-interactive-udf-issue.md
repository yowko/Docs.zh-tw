---
title: 針對 Apache Spark 的互動式環境，在 .NET 中撰寫和呼叫 Udf。
description: 瞭解如何在 .NET 中撰寫和呼叫 Udf 來 Apache Spark 互動式 shell。
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 8fb729a0b8220d15af641f916383bbd6146e2e33
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94441072"
---
# <a name="write-and-call-udfs-in-net-for-apache-spark-interactive-environments"></a><span data-ttu-id="96cd3-103">針對 Apache Spark 互動式環境在 .NET 中撰寫和呼叫 Udf</span><span class="sxs-lookup"><span data-stu-id="96cd3-103">Write and call UDFs in .NET for Apache Spark interactive environments</span></span>

<span data-ttu-id="96cd3-104">在本文中，您將瞭解如何在 .NET 中使用 (Udf) 的使用者定義函數，以 Apache Spark 互動式環境。</span><span class="sxs-lookup"><span data-stu-id="96cd3-104">In this article, you will learn how to use user-defined functions (UDFs) in a .NET for Apache Spark interactive environment.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="96cd3-105">先決條件</span><span class="sxs-lookup"><span data-stu-id="96cd3-105">Prerequisites</span></span>

1. <span data-ttu-id="96cd3-106">安裝 [.Net Interactive](https://github.com/dotnet/interactive)</span><span class="sxs-lookup"><span data-stu-id="96cd3-106">Install [.NET Interactive](https://github.com/dotnet/interactive)</span></span>
2. <span data-ttu-id="96cd3-107">安裝 [Jupyter lab](https://jupyter.org/)</span><span class="sxs-lookup"><span data-stu-id="96cd3-107">Install [Jupyter lab](https://jupyter.org/)</span></span>

## <a name="net-for-apache-spark-interactive-experience"></a><span data-ttu-id="96cd3-108">適用于 Apache Spark 互動式體驗的 .NET</span><span class="sxs-lookup"><span data-stu-id="96cd3-108">.NET for Apache Spark Interactive experience</span></span>

<span data-ttu-id="96cd3-109">[.Net for Apache Spark](https://github.com/dotnet/spark) 使用 [.Net Interactive](https://devblogs.microsoft.com/dotnet/net-interactive-is-here-net-notebooks-preview-2/) 提供 Spark 內互動式體驗的 .net 支援。</span><span class="sxs-lookup"><span data-stu-id="96cd3-109">[.NET for Apache Spark](https://github.com/dotnet/spark) uses [.NET Interactive](https://devblogs.microsoft.com/dotnet/net-interactive-is-here-net-notebooks-preview-2/) to provide .NET support for interactive experience inside Spark.</span></span> <span data-ttu-id="96cd3-110">若要瞭解如何設定環境以嘗試搭配 Jupyter 筆記本使用 .NET Interactive，請參閱 [.Net 互動式儲存](https://github.com/dotnet/interactive)機制。</span><span class="sxs-lookup"><span data-stu-id="96cd3-110">To understand how to set up the environment to try .NET Interactive with Jupyter notebooks, see the [.NET Interactive repository](https://github.com/dotnet/interactive).</span></span>

<span data-ttu-id="96cd3-111">此外，建議您 [在 .net 中進行 UDF 序列化 Apache Spark 的相關文章](udf-guide.md) ，以瞭解什麼是 udf，以及它們如何在 .net 中序列化以進行 Apache Spark。</span><span class="sxs-lookup"><span data-stu-id="96cd3-111">Also, it is recommended to go through [this article about UDF serialization in .NET for Apache Spark](udf-guide.md) to understand what UDFs are and how they are serialized in .NET for Apache Spark.</span></span>
<span data-ttu-id="96cd3-112">本指南使用 Jupyter 筆記本來說明如何在互動式體驗中使用 Udf。</span><span class="sxs-lookup"><span data-stu-id="96cd3-112">This guide uses Jupyter Notebooks to illustrate how to use UDFs in an interactive experience.</span></span>

## <a name="define-a-udf-in-net-interactive"></a><span data-ttu-id="96cd3-113">以 .NET 互動定義 UDF</span><span class="sxs-lookup"><span data-stu-id="96cd3-113">Define a UDF in .NET Interactive</span></span>

<span data-ttu-id="96cd3-114">在互動式體驗中，您可以將資料格視為在 [複寫的某個](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop)反復專案中提交的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="96cd3-114">In the interactive experience, a cell can be thought of as the code snippet being submitted as part of one iteration of the [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop).</span></span> <span data-ttu-id="96cd3-115">例如，看看下列筆記本以瞭解這代表什麼意思：</span><span class="sxs-lookup"><span data-stu-id="96cd3-115">For example, take a look at the following notebook to understand what that means:</span></span>

![Jupyter Notebook 資料格](./media/dotnet-interactive/dotnet-interactive-cells.png)

<span data-ttu-id="96cd3-117">以紅色箭號標記的每個區塊都是一個資料格或一個將程式碼提交至 Spark 的資料格。</span><span class="sxs-lookup"><span data-stu-id="96cd3-117">Each of those blocks marked by the red arrow is one cell, or one submission of code to Spark.</span></span> <span data-ttu-id="96cd3-118">現在，定義參考自訂使用者定義物件的 UDF 時，必須在定義其所參考物件的相同資料格中定義 UDF。</span><span class="sxs-lookup"><span data-stu-id="96cd3-118">Now when defining a UDF that references a custom user-defined object, it is required that the UDF be defined in the same cell where the object it references is defined.</span></span> <span data-ttu-id="96cd3-119">讓我們看看看起來像這樣的範例：</span><span class="sxs-lookup"><span data-stu-id="96cd3-119">Let's look at what that looks like as an example:</span></span>

![正常運作的 UDF](./media/dotnet-interactive/working-udf.png)

## <a name="call-a-udf-on-a-dataframe"></a><span data-ttu-id="96cd3-121">呼叫資料框架上的 UDF</span><span class="sxs-lookup"><span data-stu-id="96cd3-121">Call a UDF on a DataFrame</span></span>

<span data-ttu-id="96cd3-122">在上呼叫之前定義的 UDF 時， `DataFrame` 請務必確定 UDF 是在先前提交的儲存格中定義，然後再呼叫它，如先前範例中所示。</span><span class="sxs-lookup"><span data-stu-id="96cd3-122">When calling a previously defined UDF on a `DataFrame` it is important to make sure the UDF is defined in a previously submitted cell, before calling it, as can be seen in the previous example.</span></span>

<span data-ttu-id="96cd3-123">現在讓我們看看在定義該 UDF 的相同儲存格中呼叫 UDF 會發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="96cd3-123">Now let's see what happens if we call the UDF in the same cell where it is defined.</span></span>

![失敗的 UDF 呼叫](./media/dotnet-interactive/udf_fails.png)

<span data-ttu-id="96cd3-125">上述反白顯示的錯誤是因為 UDF 元件必須先經過編譯並傳送給背景工作角色，才能在資料框架上呼叫。</span><span class="sxs-lookup"><span data-stu-id="96cd3-125">The above highlighted error is because the UDF assemblies need to first be compiled and shipped to the workers before it can be called on a DataFrame.</span></span>

<span data-ttu-id="96cd3-126">當您在 .NET 中為 Apache Spark 的互動式體驗 (（例如 [Azure Synapse 筆記本](/azure/synapse-analytics/spark/apache-spark-development-using-notebooks)) ）執行 udf 時，必須牢記一些重要事項。</span><span class="sxs-lookup"><span data-stu-id="96cd3-126">These are a few important things to keep in mind while implementing UDFs in .NET for Apache Spark interactive experience (such as [Azure Synapse Notebooks](/azure/synapse-analytics/spark/apache-spark-development-using-notebooks)).</span></span>

## <a name="faqs"></a><span data-ttu-id="96cd3-127">常見問題集</span><span class="sxs-lookup"><span data-stu-id="96cd3-127">FAQs</span></span>

1. <span data-ttu-id="96cd3-128">**為什麼我的 UDF 參考自訂使用者定義物件會擲回錯誤 `Type Submission#_ is not marked as serializable` ？**</span><span class="sxs-lookup"><span data-stu-id="96cd3-128">**Why does my UDF referencing a custom user-defined object throw the error `Type Submission#_ is not marked as serializable`?**</span></span>
    <span data-ttu-id="96cd3-129">.NET Interactive 會使用資料格提交編號的包裝函式類別來包裝每個資料格，以唯一識別所提交的每個資料格。</span><span class="sxs-lookup"><span data-stu-id="96cd3-129">.NET Interactive wraps each of these cells with a wrapper class of the cell submission number, to uniquely identify each cell being submitted.</span></span> <span data-ttu-id="96cd3-130">現在依照 [本指南](udf-guide.md)中的詳細說明，當參考自訂物件的 UDF 序列化時，也會挑選其目標來進行序列化，在 .net Interactive 的情況下，會由定義自訂物件的資料格包裝函式類別來包裝。</span><span class="sxs-lookup"><span data-stu-id="96cd3-130">Now as explained in detail in [this guide](udf-guide.md), when a UDF that references a custom object is being serialized its target is also picked up for serialization, which in the case of .NET Interactive gets wrapped by the wrapper class of the cell where the custom object is defined.</span></span>
    <span data-ttu-id="96cd3-131">現在讓我們來看看這會如何影響我們在筆記本中的 UDF 定義：</span><span class="sxs-lookup"><span data-stu-id="96cd3-131">Now let's see how that affects our UDF definition in the notebook:</span></span>

    ![UDF 序列化錯誤](./media/dotnet-interactive/udf-serialization-error.png)

    <span data-ttu-id="96cd3-133">如同在案例中所見 `udf2_fails` ，我們看到的錯誤訊息指出型別未 `Submission#7` 標示為可序列化，這是因為 .net Interactive 會將資料格中定義的每個物件與其類別一起包裝 `Submission#` ，而這會在即時產生，因此未標示為 `Serializable` 。</span><span class="sxs-lookup"><span data-stu-id="96cd3-133">As can be seen in the case of `udf2_fails`, we see the error message that says Type `Submission#7` is not marked as serializable, this is because .NET Interactive wraps every object defined in a cell with its `Submission#` class, which is generated on the fly and hence is not marked as `Serializable`.</span></span>

    <span data-ttu-id="96cd3-134">基於這個理由，必須將 **參考自訂物件的 UDF 定義在與該物件相同的資料格中** 。</span><span class="sxs-lookup"><span data-stu-id="96cd3-134">For this reason, it is **required that a UDF referencing a custom object is defined in the same cell as that object**.</span></span>

2. <span data-ttu-id="96cd3-135">**為什麼廣播變數適用于 .NET Interactive？**</span><span class="sxs-lookup"><span data-stu-id="96cd3-135">**Why don't Broadcast Variables work with .NET Interactive?**</span></span>
    <span data-ttu-id="96cd3-136">基於先前所述的原因，廣播變數不適用於 .NET Interactive。</span><span class="sxs-lookup"><span data-stu-id="96cd3-136">For the reasons explained previously, broadcast variables don't work with .NET Interactive.</span></span> <span data-ttu-id="96cd3-137">最好是 [在廣播變數上進行這份指南](broadcast-guide.md) ，以深入瞭解廣播變數是什麼，以及如何使用它們。</span><span class="sxs-lookup"><span data-stu-id="96cd3-137">It is a good idea to go through [this guide on broadcast variables](broadcast-guide.md) to get a deeper understanding of what broadcast variables are and how to use them.</span></span> <span data-ttu-id="96cd3-138">廣播變數無法搭配互動式案例使用的原因，是因為 .NET 互動的設計會附加儲存格所定義的每個物件及其資料格提交類別（因為未標記為可序列化），但先前所示的例外狀況會失敗。</span><span class="sxs-lookup"><span data-stu-id="96cd3-138">The reason broadcast variables don't work with interactive scenarios is because of .NET interactive's design of appending each object defined in a cell with its cell submission class, which since is not marked serializable, fails with the same exception as shown previously.</span></span>
    <span data-ttu-id="96cd3-139">讓我們更深入瞭解下列範例：</span><span class="sxs-lookup"><span data-stu-id="96cd3-139">Let's dive a little deeper with the following example:</span></span>

    ![廣播變數失敗](./media/dotnet-interactive/broadcast-fails.png)

    <span data-ttu-id="96cd3-141">如先前章節中的建議，我們會在此案例中定義 UDF 與其參考的物件 (廣播變數) 在相同的資料格中，但是仍 `SerializationException` 會看到錯誤抱怨 `Microsoft.Spark.Sql.Session` 未標示為可序列化。</span><span class="sxs-lookup"><span data-stu-id="96cd3-141">As recommended in the previous sections, we define both the UDF and the object it is referencing (broadcast variable in this case) in the same cell, but we still see the `SerializationException` error complaining about `Microsoft.Spark.Sql.Session` not being marked as serializable.</span></span> <span data-ttu-id="96cd3-142">這是因為當編譯器嘗試序列化廣播變數物件時 `bv` ，它會尋找要附加至物件的名稱 [`SparkSession`](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/SparkSession.cs#L20) `spark` ，而這需要標記為可序列化。</span><span class="sxs-lookup"><span data-stu-id="96cd3-142">This is because when the compiler tries to serialize the broadcast variable object `bv`, it finds its name to be appended with [`SparkSession`](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/SparkSession.cs#L20) object `spark`, which it requires to be marked as serializable.</span></span> <span data-ttu-id="96cd3-143">藉由查看此儲存格提交的反向組譯元件，可讓您更輕鬆地進行示範：</span><span class="sxs-lookup"><span data-stu-id="96cd3-143">This can be demonstrated with more ease by taking a peek at the decompiled assembly of this cell submission:</span></span>

    ![反向組譯元件碼](./media/dotnet-interactive/decompiledAssembly.png)

    <span data-ttu-id="96cd3-145">如果我們將此 [`SparkSession`](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/SparkSession.cs#L20) 類別標示為 `[Serializable]` ，我們可以讓它正常運作，但這並不是理想的解決方案，因為我們不想要讓使用者能夠序列化 SparkSession 物件，因為這可能會導致一些奇怪、非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="96cd3-145">If we mark the [`SparkSession`](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/SparkSession.cs#L20) class as `[Serializable]`, we can get this to work, but this is not an ideal solution as we don't want to give the user the ability to serialize a SparkSession object, as that could lead to some weird, undesirable behavior.</span></span> <span data-ttu-id="96cd3-146">這是 [已知的問題](https://github.com/dotnet/spark/issues/619) ，將在未來的版本中解決。</span><span class="sxs-lookup"><span data-stu-id="96cd3-146">This is a [known issue](https://github.com/dotnet/spark/issues/619) and will be resolved in future versions.</span></span>
