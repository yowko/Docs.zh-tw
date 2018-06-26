---
title: C# 7.1 中的新增功能
description: C# 7.1 新功能的概觀。
ms.date: 08/16/2017
ms.openlocfilehash: 565db102284424f9d8f6fa04ec9c74b52c9da0e6
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728650"
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="f7f68-103">C# 7.1 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="f7f68-103">What's new in C# 7.1</span></span>

<span data-ttu-id="f7f68-104">C# 7.1 是 C# 語言的第一個發行的小數點版本。</span><span class="sxs-lookup"><span data-stu-id="f7f68-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="f7f68-105">這表示這個語言的版本發行速度將會越來越快。</span><span class="sxs-lookup"><span data-stu-id="f7f68-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="f7f68-106">您很快能使用下列新功能。理想情況下，這些新功能只要一就緒，您就能開始使用。
</span><span class="sxs-lookup"><span data-stu-id="f7f68-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="f7f68-107">C# 7.1 加入了新功能，可將編譯器加以設定，使其符合指定的語言版本。
</span><span class="sxs-lookup"><span data-stu-id="f7f68-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="f7f68-108">這使得工具的升級與語言版本的升級能夠分開來決定。
</span><span class="sxs-lookup"><span data-stu-id="f7f68-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="f7f68-109">C# 7.1 也新增了[語言版本選擇](../language-reference/configure-language-version.md)組態項目、三種新的語言功能和新的編譯器行為。</span><span class="sxs-lookup"><span data-stu-id="f7f68-109">C# 7.1 adds the [language version selection](../language-reference/configure-language-version.md) configuration element, three new language features and new compiler behavior.</span></span>

<span data-ttu-id="f7f68-110">此版本的新款語言功能包括：</span><span class="sxs-lookup"><span data-stu-id="f7f68-110">The new language features in this release are:</span></span>

* [<span data-ttu-id="f7f68-111">`async``Main`方法</span><span class="sxs-lookup"><span data-stu-id="f7f68-111">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="f7f68-112">應用程式的進入點允許使用`async`修飾詞。</span><span class="sxs-lookup"><span data-stu-id="f7f68-112">The entry point for an application can have the `async` modifier.</span></span>
* [<span data-ttu-id="f7f68-113">`default`常值運算式</span><span class="sxs-lookup"><span data-stu-id="f7f68-113">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="f7f68-114">目標類型可以推斷時，可以在預設值運算式中使用預設常值運算式。</span><span class="sxs-lookup"><span data-stu-id="f7f68-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
* [<span data-ttu-id="f7f68-115">推斷的元組項目名稱</span><span class="sxs-lookup"><span data-stu-id="f7f68-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="f7f68-116">在許多情況下，Tuple 項目的名稱均可從 Tuple 初始化推斷來加以推斷。
</span><span class="sxs-lookup"><span data-stu-id="f7f68-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>

<span data-ttu-id="f7f68-117">最後，編譯器有兩個選項 `/refout` 和 `/refonly`，它們控制了[參考組件產生](#reference-assembly-generation)。</span><span class="sxs-lookup"><span data-stu-id="f7f68-117">Finally, the compiler has two options `/refout` and `/refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

<span data-ttu-id="f7f68-118">若要使用小數點版本中的最新功能，您需要[設定編譯器語言版本](../language-reference/configure-language-version.md)並選取該版本。</span><span class="sxs-lookup"><span data-stu-id="f7f68-118">To use the latest features in a point release, you need to [configure the compiler language version](../language-reference/configure-language-version.md) and select the version.</span></span>

## <a name="async-main"></a><span data-ttu-id="f7f68-119">非同步主要</span><span class="sxs-lookup"><span data-stu-id="f7f68-119">Async main</span></span>

<span data-ttu-id="f7f68-120">「非同步主要」方法可讓您在 `Main` 方法中使用 `await`。</span><span class="sxs-lookup"><span data-stu-id="f7f68-120">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="f7f68-121">在過去您必須這樣寫：</span><span class="sxs-lookup"><span data-stu-id="f7f68-121">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="f7f68-122">現在您可以這樣寫：</span><span class="sxs-lookup"><span data-stu-id="f7f68-122">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="f7f68-123">如果您的程式不會傳回結束代碼，您可以宣告傳回 <xref:System.Threading.Tasks.Task> 的 `Main` 方法：</span><span class="sxs-lookup"><span data-stu-id="f7f68-123">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="f7f68-124">您可以在程式設計指南的[非同步主要](../programming-guide/main-and-command-args/index.md)主題中閱讀更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="f7f68-124">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) topic in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="f7f68-125">預設常值運算式</span><span class="sxs-lookup"><span data-stu-id="f7f68-125">Default literal expressions</span></span>

<span data-ttu-id="f7f68-126">預設常值運算式是預設值運算式的增強功能。</span><span class="sxs-lookup"><span data-stu-id="f7f68-126">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="f7f68-127">這些運算式會將變數初始化為預設值。</span><span class="sxs-lookup"><span data-stu-id="f7f68-127">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="f7f68-128">在過去您必須這樣寫：</span><span class="sxs-lookup"><span data-stu-id="f7f68-128">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="f7f68-129">您現在可以略過初始化右側的類型：</span><span class="sxs-lookup"><span data-stu-id="f7f68-129">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="f7f68-130">您可以在關於[預設值運算式](../programming-guide/statements-expressions-operators/default-value-expressions.md)的 C# 程式設計手冊主題進一步了解這項增強功能。</span><span class="sxs-lookup"><span data-stu-id="f7f68-130">You can learn more about this enhancement in the C# Programming Guide topic on [default value expressions](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span></span>

<span data-ttu-id="f7f68-131">這項增強功能也會變更 [default 關鍵字](../language-reference/keywords/default.md)的部分剖析規則。</span><span class="sxs-lookup"><span data-stu-id="f7f68-131">This enhancement also changes some of the parsing rules for the [default keyword](../language-reference/keywords/default.md).</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="f7f68-132">Tuple 型別推導</span><span class="sxs-lookup"><span data-stu-id="f7f68-132">Inferred tuple element names</span></span>

<span data-ttu-id="f7f68-133">本方法為 C# 7.0 版本 Tuple 方法的改進，</span><span class="sxs-lookup"><span data-stu-id="f7f68-133">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="f7f68-134">許多時候，當您初始化 Tuple 時，用於指派右側的變數會與您想要的元組項目名稱相同：</span><span class="sxs-lookup"><span data-stu-id="f7f68-134">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="f7f68-135">元組項目的名稱可以從用來在 C# 7.1 中初始化元組的變數加以推斷：</span><span class="sxs-lookup"><span data-stu-id="f7f68-135">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="f7f68-136">您可以在[元組](../tuples.md)主題中深入了解此功能。</span><span class="sxs-lookup"><span data-stu-id="f7f68-136">You can learn more about this feature in the [Tuples](../tuples.md) topic.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="f7f68-137">參考組件產生</span><span class="sxs-lookup"><span data-stu-id="f7f68-137">Reference assembly generation</span></span>

<span data-ttu-id="f7f68-138">有兩個新的編譯器選項會產生「僅參考的組件」：[/refout](../language-reference/compiler-options/refout-compiler-option.md) 和 [/refonly](../language-reference/compiler-options/refonly-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="f7f68-138">There are two new compiler options that generate *reference-only assemblies*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) and [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="f7f68-139">連結的主題將更詳細地說明這些選項和參考組件。</span><span class="sxs-lookup"><span data-stu-id="f7f68-139">The linked topics explain these options and reference assemblies in more detail.</span></span>
