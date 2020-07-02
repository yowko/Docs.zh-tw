---
title: 在適用于 Apache Spark 的 .NET 中建立使用者定義函數（UDF）
description: 瞭解如何在 .NET 中針對 Apache Spark 應用程式執行使用者定義函數（UDF）。
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 97afda8ed17d3719c534d72ad3ad026745a70922
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620920"
---
# <a name="create-user-defined-functions-udf-in-net-for-apache-spark"></a><span data-ttu-id="37f88-103">在適用于 Apache Spark 的 .NET 中建立使用者定義函數（UDF）</span><span class="sxs-lookup"><span data-stu-id="37f88-103">Create user-defined functions (UDF) in .NET for Apache Spark</span></span>

<span data-ttu-id="37f88-104">在本文中，您將瞭解如何在 .NET 中使用使用者定義函數（UDF）來進行 Apache Spark。</span><span class="sxs-lookup"><span data-stu-id="37f88-104">In this article, you learn how to use user-defined functions (UDF) in .NET for Apache Spark.</span></span> <span data-ttu-id="37f88-105">[Udf）](https://spark.apache.org/docs/latest/api/java/org/apache/spark/sql/expressions/UserDefinedFunction.html)是一項 Spark 功能，可讓您使用自訂函式來擴充系統的內建功能。</span><span class="sxs-lookup"><span data-stu-id="37f88-105">[UDFs)](https://spark.apache.org/docs/latest/api/java/org/apache/spark/sql/expressions/UserDefinedFunction.html) are a Spark feature that allow you to use custom functions to extend the system's built-in functionality.</span></span> <span data-ttu-id="37f88-106">Udf 會從資料表內的單一資料列轉換值，以根據 UDF 中定義的邏輯，為每個資料列產生一個對應的輸出值。</span><span class="sxs-lookup"><span data-stu-id="37f88-106">UDFs transform values from a single row within a table to produce a single corresponding output value per row based on the logic defined in the UDF.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="define-udfs"></a><span data-ttu-id="37f88-107">定義 Udf</span><span class="sxs-lookup"><span data-stu-id="37f88-107">Define UDFs</span></span>

<span data-ttu-id="37f88-108">請參閱下列 UDF 定義：</span><span class="sxs-lookup"><span data-stu-id="37f88-108">Review the following UDF definition:</span></span>

```csharp
string s1 = "hello";
Func<Column, Column> udf = Udf<string, string>(
    str => $"{s1} {str}");
```

<span data-ttu-id="37f88-109">UDF 會使用 `string` 做為[資料框架](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L24)資料[行](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Column.cs#L14)形式的輸入，並傳回 `string` `hello` 在輸入前面附加的。</span><span class="sxs-lookup"><span data-stu-id="37f88-109">The UDF takes a `string` as an input in the form of a [Column](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Column.cs#L14) of a [Dataframe](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L24)) and returns a `string` with `hello` appended in front of the input.</span></span>

<span data-ttu-id="37f88-110">下列資料框架 `df` 包含名稱清單：</span><span class="sxs-lookup"><span data-stu-id="37f88-110">The following DataFrame `df` contains a list of names:</span></span>

```text
+-------+
|   name|
+-------+
|Michael|
|   Andy|
| Justin|
+-------+
```

<span data-ttu-id="37f88-111">現在，讓我們將上述定義的套用 `udf` 至資料框架 `df` ：</span><span class="sxs-lookup"><span data-stu-id="37f88-111">Now let's apply the above defined `udf` to the DataFrame `df`:</span></span>

```csharp
DataFrame udfResult = df.Select(udf(df["name"]));
```

<span data-ttu-id="37f88-112">下列資料框架 `udfResult` 是 UDF 的結果：</span><span class="sxs-lookup"><span data-stu-id="37f88-112">The following DataFrame `udfResult` is the result of the UDF:</span></span>

```text
+-------------+
|         name|
+-------------+
|hello Michael|
|   hello Andy|
| hello Justin|
+-------------+
```

<span data-ttu-id="37f88-113">若要進一步瞭解如何執行 Udf，請參閱 GitHub 上的[UDF helper](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Functions.cs#L3616)函式和[範例](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark.E2ETest/UdfTests/UdfSimpleTypesTests.cs#L49)。</span><span class="sxs-lookup"><span data-stu-id="37f88-113">To better understand how to implement UDFs, review the [UDF helper functions](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Functions.cs#L3616) and [examples](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark.E2ETest/UdfTests/UdfSimpleTypesTests.cs#L49) on GitHub.</span></span>

## <a name="udf-serialization"></a><span data-ttu-id="37f88-114">UDF 序列化</span><span class="sxs-lookup"><span data-stu-id="37f88-114">UDF serialization</span></span>

<span data-ttu-id="37f88-115">因為 Udf 是需要在背景工作角色上執行的函式，所以必須將它們序列化並傳送至背景工作角色，做為來自驅動程式的承載的一部分。</span><span class="sxs-lookup"><span data-stu-id="37f88-115">Because UDFs are functions that need to be executed on workers, they have to be serialized and sent to the workers as part of the payload from the driver.</span></span> <span data-ttu-id="37f88-116">[委派](../../csharp/programming-guide/delegates/index.md)（這是方法的參考）必須序列化以及其[目標](xref:System.Delegate.Target%2A)，這是目前的委派叫用實例方法的類別實例。</span><span class="sxs-lookup"><span data-stu-id="37f88-116">The [delegate](../../csharp/programming-guide/delegates/index.md), which is a reference to the method, needs to be serialized as well as its [target](xref:System.Delegate.Target%2A), which is the class instance on which the current delegate invokes the instance method.</span></span> <span data-ttu-id="37f88-117">請參閱[GitHub 中](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Utils/CommandSerDe.cs#L149)的此程式碼範例，以深入瞭解 UDF 序列化的執行方式。</span><span class="sxs-lookup"><span data-stu-id="37f88-117">Review this [code example in GitHub](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Utils/CommandSerDe.cs#L149) to get a better understanding of how UDF serialization is being done.</span></span>

<span data-ttu-id="37f88-118">適用于 Apache Spark 的 .NET 會使用 .NET Core，這不支援序列化委派。</span><span class="sxs-lookup"><span data-stu-id="37f88-118">.NET for Apache Spark uses .NET Core, which doesn't support serializing delegates.</span></span> <span data-ttu-id="37f88-119">取而代之的是，反映是用來序列化定義委派的目標。</span><span class="sxs-lookup"><span data-stu-id="37f88-119">Instead, reflection is used to serialize the target where the delegate is defined.</span></span> <span data-ttu-id="37f88-120">在通用範圍中定義多個委派時，它們會有一個共用的關閉，而成為序列化的反映目標。</span><span class="sxs-lookup"><span data-stu-id="37f88-120">When multiple delegates are defined in a common scope, they have a shared closure that becomes the target of reflection for serialization.</span></span>

### <a name="serialization-example"></a><span data-ttu-id="37f88-121">序列化範例</span><span class="sxs-lookup"><span data-stu-id="37f88-121">Serialization example</span></span>

<span data-ttu-id="37f88-122">下列程式碼片段會定義兩個會在兩個函式委派中參考的字串變數，以傳回各自的字串做為結果：</span><span class="sxs-lookup"><span data-stu-id="37f88-122">The following code snippet defines two string variables that are being referenced in two function delegates that return the respective strings as a result:</span></span>

```csharp
using System;

public class C {
    public void M() {
        string s1 = "s1";
        string s2 = "s2";
        Func<string, string> a = str => s1;
        Func<string, string> b = str => s2;
    }
}
```

<span data-ttu-id="37f88-123">上述 c # 程式碼會從編譯器產生下列 c # 反組解碼（信用來源： [sharplab.io](https://sharplab.io)）程式碼：</span><span class="sxs-lookup"><span data-stu-id="37f88-123">The above C# code generates the following C# disassembly (credit source: [sharplab.io](https://sharplab.io)) code from the compiler:</span></span>

```csharp
public class C
{
    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_0
    {
        public string s1;

        public string s2;

        internal string <M>b__0(string str)
        {
            return s1;
        }

        internal string <M>b__1(string str)
        {
            return s2;
        }
    }

    public void M()
    {
        <>c__DisplayClass0_0 <>c__DisplayClass0_ = new <>c__DisplayClass0_0();
        <>c__DisplayClass0_.s1 = "s1";
        <>c__DisplayClass0_.s2 = "s2";
        Func<string, string> func = new Func<string, string>(<>c__DisplayClass0_.<M>b__0);
        Func<string, string> func2 = new Func<string, string>(<>c__DisplayClass0_.<M>b__1);
    }
}
```

<span data-ttu-id="37f88-124">`func`和都會 `func2` 共用相同的關閉 `<>c__DisplayClass0_0` ，也就是序列化委派和時，會序列化的 `func` 目標 `func2` 。</span><span class="sxs-lookup"><span data-stu-id="37f88-124">Both `func` and `func2` share the same closure `<>c__DisplayClass0_0`, which is the target that is serialized when serializing the delegates `func` and `func2`.</span></span> <span data-ttu-id="37f88-125">即使 `Func<string, string> a` 只參考 `s1` ， `s2` 當位元組傳送給背景工作時，也會序列化。</span><span class="sxs-lookup"><span data-stu-id="37f88-125">Even though `Func<string, string> a` is only referencing `s1`, `s2` is also serialized when the bytes are sent to the workers.</span></span>

<span data-ttu-id="37f88-126">這可能會在執行時間導致某些非預期的行為（例如，在使用[廣播變數](broadcast-guide.md)的情況下），這也是為什麼我們建議您將函式中使用之變數的可見度限制為該函式的範圍。</span><span class="sxs-lookup"><span data-stu-id="37f88-126">This can lead to some unexpected behaviors at runtime (like in the case of using [broadcast variables](broadcast-guide.md)), which is why we recommend that you restrict the visibility of the variables used in a function to that function's scope.</span></span>

<span data-ttu-id="37f88-127">下列程式碼片段是建議的方法，用來執行所需的序列化行為：</span><span class="sxs-lookup"><span data-stu-id="37f88-127">The following code snippet is the recommended way to implement the desired serialization behavior:</span></span>

```csharp
using System;

public class C {
    public void M() {
        {
            string s1 = "s1";
            Func<string, string> a = str => s1;
        }
        {
            string s2 = "s2";
            Func<string, string> b = str => s2;
        }
    }
}
```

<span data-ttu-id="37f88-128">上述 c # 程式碼會從編譯器產生下列 c # 反組解碼（信用來源： [sharplab.io](https://sharplab.io)）程式碼：</span><span class="sxs-lookup"><span data-stu-id="37f88-128">The above C# code generates the following C# disassembly (credit source: [sharplab.io](https://sharplab.io)) code from the compiler:</span></span>

```csharp
public class C
{
    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_0
    {
        public string s1;

        internal string <M>b__0(string str)
        {
            return s1;
        }
    }

    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_1
    {
        public string s2;

        internal string <M>b__1(string str)
        {
            return s2;
        }
    }

    public void M()
    {
        <>c__DisplayClass0_0 <>c__DisplayClass0_ = new <>c__DisplayClass0_0();
        <>c__DisplayClass0_.s1 = "s1";
        Func<string, string> func = new Func<string, string>(<>c__DisplayClass0_.<M>b__0);
        <>c__DisplayClass0_1 <>c__DisplayClass0_2 = new <>c__DisplayClass0_1();
        <>c__DisplayClass0_2.s2 = "s2";
        Func<string, string> func2 = new Func<string, string>(<>c__DisplayClass0_2.<M>b__1);
    }
}
```

<span data-ttu-id="37f88-129">請注意， `func` 和 `func2` 不再共用關閉，而且它們分別擁有個別的閉包 `<>c__DisplayClass0_0` 和 `<>c__DisplayClass0_1` 。</span><span class="sxs-lookup"><span data-stu-id="37f88-129">Notice that `func` and `func2` no longer share a closure, and they have their own separate closures `<>c__DisplayClass0_0` and `<>c__DisplayClass0_1` respectively.</span></span> <span data-ttu-id="37f88-130">當做序列化的目標使用時，不會針對委派序列化參考變數以外的任何內容。</span><span class="sxs-lookup"><span data-stu-id="37f88-130">When used as the target for serialization, nothing other than the referenced variables will get serialized for the delegate.</span></span> <span data-ttu-id="37f88-131">在共同的範圍中執行多個 Udf 時，請務必記住這種行為。</span><span class="sxs-lookup"><span data-stu-id="37f88-131">This behavior is important to keep in mind while implementing multiple UDFs in a common scope.</span></span>

## <a name="some-spark-udf-caveats"></a><span data-ttu-id="37f88-132">一些 Spark UDF 注意事項</span><span class="sxs-lookup"><span data-stu-id="37f88-132">Some Spark UDF caveats</span></span>

* <span data-ttu-id="37f88-133">Udf 中的 Null 值可能會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="37f88-133">Null values in UDFs can throw exceptions.</span></span> <span data-ttu-id="37f88-134">開發人員必須負責處理這些問題。</span><span class="sxs-lookup"><span data-stu-id="37f88-134">It's the responsibility of the developer to handle them.</span></span>
* <span data-ttu-id="37f88-135">Udf 不會利用 Spark 的內建函數所提供的優化，因此建議您盡可能使用內建函數。</span><span class="sxs-lookup"><span data-stu-id="37f88-135">UDFs don't leverage the optimizations provided by Spark's built-in functions, so it's recommended to use built-in functions where possible.</span></span>

## <a name="next-steps"></a><span data-ttu-id="37f88-136">後續步驟</span><span class="sxs-lookup"><span data-stu-id="37f88-136">Next steps</span></span>

* [<span data-ttu-id="37f88-137">開始使用 .NET for Apache Spark</span><span class="sxs-lookup"><span data-stu-id="37f88-137">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="37f88-138">對 Windows 上的 .NET for Apache Spark 應用程式進行偵錯</span><span class="sxs-lookup"><span data-stu-id="37f88-138">Debug a .NET for Apache Spark application on Windows</span></span>](debug.md)
