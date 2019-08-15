---
title: C# 7.1 中的新增功能
description: C# 7.1 新功能的概觀。
ms.date: 04/09/2019
ms.openlocfilehash: 18306da709ea30f03f6c42b4a917e9b39695eb16
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796604"
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="ebf66-103">C# 7.1 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="ebf66-103">What's new in C# 7.1</span></span>

<span data-ttu-id="ebf66-104">C# 7.1 是 C# 語言的第一個發行的小數點版本。</span><span class="sxs-lookup"><span data-stu-id="ebf66-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="ebf66-105">這表示這個語言的版本發行速度將會越來越快。</span><span class="sxs-lookup"><span data-stu-id="ebf66-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="ebf66-106">您很快能使用下列新功能。理想情況下，這些新功能只要一就緒，您就能開始使用。</span><span class="sxs-lookup"><span data-stu-id="ebf66-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="ebf66-107">C# 7.1 加入了新功能，可將編譯器加以設定，使其符合指定的語言版本。</span><span class="sxs-lookup"><span data-stu-id="ebf66-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="ebf66-108">這使得工具的升級與語言版本的升級能夠分開來決定。</span><span class="sxs-lookup"><span data-stu-id="ebf66-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="ebf66-109">C# 7.1 也新增了[語言版本選擇](../language-reference/configure-language-version.md)設定元素、三種新的語言功能和新的編譯器行為。</span><span class="sxs-lookup"><span data-stu-id="ebf66-109">C# 7.1 adds the [language version selection](../language-reference/configure-language-version.md) configuration element, three new language features, and new compiler behavior.</span></span>

<span data-ttu-id="ebf66-110">此版本的新款語言功能包括：</span><span class="sxs-lookup"><span data-stu-id="ebf66-110">The new language features in this release are:</span></span>

* [<span data-ttu-id="ebf66-111">`async``Main`方法</span><span class="sxs-lookup"><span data-stu-id="ebf66-111">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="ebf66-112">應用程式的進入點允許使用`async`修飾詞。</span><span class="sxs-lookup"><span data-stu-id="ebf66-112">The entry point for an application can have the `async` modifier.</span></span>
* [<span data-ttu-id="ebf66-113">`default`常值運算式</span><span class="sxs-lookup"><span data-stu-id="ebf66-113">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="ebf66-114">目標類型可以推斷時，可以在預設值運算式中使用預設常值運算式。</span><span class="sxs-lookup"><span data-stu-id="ebf66-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
* [<span data-ttu-id="ebf66-115">推斷的元組項目名稱</span><span class="sxs-lookup"><span data-stu-id="ebf66-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="ebf66-116">在許多情況下，Tuple 項目的名稱均可從 Tuple 初始化推斷來加以推斷。</span><span class="sxs-lookup"><span data-stu-id="ebf66-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>
* [<span data-ttu-id="ebf66-117">泛型型別參數的模式比對</span><span class="sxs-lookup"><span data-stu-id="ebf66-117">Pattern matching on generic type parameters</span></span>](#pattern-matching-on-generic-type-parameters)
  - <span data-ttu-id="ebf66-118">您可以對型別為泛型型別參數的變數使用模式比對運算式。</span><span class="sxs-lookup"><span data-stu-id="ebf66-118">You can use pattern match expressions on variables whose type is a generic type parameter.</span></span>

<span data-ttu-id="ebf66-119">最後，編譯器有兩個選項 `-refout` 和 `-refonly`，它們控制了[參考組件產生](#reference-assembly-generation)。</span><span class="sxs-lookup"><span data-stu-id="ebf66-119">Finally, the compiler has two options `-refout` and `-refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

<span data-ttu-id="ebf66-120">若要使用小數點版本中的最新功能，您需要[設定編譯器語言版本](../language-reference/configure-language-version.md)並選取該版本。</span><span class="sxs-lookup"><span data-stu-id="ebf66-120">To use the latest features in a point release, you need to [configure the compiler language version](../language-reference/configure-language-version.md) and select the version.</span></span>

<span data-ttu-id="ebf66-121">此文章的其餘部分將概述各個功能。</span><span class="sxs-lookup"><span data-stu-id="ebf66-121">The remainder of this article provides an overview of each feature.</span></span> <span data-ttu-id="ebf66-122">您將了解每項功能背後的原因。</span><span class="sxs-lookup"><span data-stu-id="ebf66-122">For each feature, you'll learn the reasoning behind it.</span></span> <span data-ttu-id="ebf66-123">您將了解語法。</span><span class="sxs-lookup"><span data-stu-id="ebf66-123">You'll learn the syntax.</span></span> <span data-ttu-id="ebf66-124">您可以使用 `dotnet try` 全域工具，在您的環境中探索這些功能：</span><span class="sxs-lookup"><span data-stu-id="ebf66-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="ebf66-125">安裝 [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) 全域工具。</span><span class="sxs-lookup"><span data-stu-id="ebf66-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="ebf66-126">複製 [dotnet/try-samples](https://github.com/dotnet/try-samples) 存放庫。</span><span class="sxs-lookup"><span data-stu-id="ebf66-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="ebf66-127">將目前目錄設為 *try-samples* 存放庫的 *csharp7* 子目錄。</span><span class="sxs-lookup"><span data-stu-id="ebf66-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="ebf66-128">執行 `dotnet try`。</span><span class="sxs-lookup"><span data-stu-id="ebf66-128">Run `dotnet try`.</span></span>

## <a name="async-main"></a><span data-ttu-id="ebf66-129">非同步主要</span><span class="sxs-lookup"><span data-stu-id="ebf66-129">Async main</span></span>

<span data-ttu-id="ebf66-130">「非同步主要」  方法可讓您在 `Main` 方法中使用 `await`。</span><span class="sxs-lookup"><span data-stu-id="ebf66-130">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="ebf66-131">在過去您必須這樣寫：</span><span class="sxs-lookup"><span data-stu-id="ebf66-131">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="ebf66-132">現在您可以這樣寫：</span><span class="sxs-lookup"><span data-stu-id="ebf66-132">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="ebf66-133">如果您的程式不會傳回結束代碼，您可以宣告傳回 <xref:System.Threading.Tasks.Task> 的 `Main` 方法：</span><span class="sxs-lookup"><span data-stu-id="ebf66-133">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="ebf66-134">您可以在程式設計指南的[非同步主要](../programming-guide/main-and-command-args/index.md)文章中閱讀更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ebf66-134">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) article in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="ebf66-135">預設常值運算式</span><span class="sxs-lookup"><span data-stu-id="ebf66-135">Default literal expressions</span></span>

<span data-ttu-id="ebf66-136">預設常值運算式是預設值運算式的增強功能。</span><span class="sxs-lookup"><span data-stu-id="ebf66-136">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="ebf66-137">這些運算式會將變數初始化為預設值。</span><span class="sxs-lookup"><span data-stu-id="ebf66-137">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="ebf66-138">在過去您必須這樣寫：</span><span class="sxs-lookup"><span data-stu-id="ebf66-138">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="ebf66-139">您現在可以略過初始化右側的類型：</span><span class="sxs-lookup"><span data-stu-id="ebf66-139">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="ebf66-140">如需詳細資訊，請參閱[預設運算子](../language-reference/operators/default.md)一文中的[預設常值](../language-reference/operators/default.md#default-literal)一節。</span><span class="sxs-lookup"><span data-stu-id="ebf66-140">For more information, see the [default literal](../language-reference/operators/default.md#default-literal) section of the [default operator](../language-reference/operators/default.md) article.</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="ebf66-141">推斷的 Tuple 元素名稱</span><span class="sxs-lookup"><span data-stu-id="ebf66-141">Inferred tuple element names</span></span>

<span data-ttu-id="ebf66-142">本方法為 C# 7.0 版本 Tuple 方法的改進，</span><span class="sxs-lookup"><span data-stu-id="ebf66-142">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="ebf66-143">許多時候，當您初始化 Tuple 時，用於指派右側的變數會與您想要的元組項目名稱相同：</span><span class="sxs-lookup"><span data-stu-id="ebf66-143">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="ebf66-144">元組項目的名稱可以從用來在 C# 7.1 中初始化元組的變數加以推斷：</span><span class="sxs-lookup"><span data-stu-id="ebf66-144">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="ebf66-145">您可以在[元組](../tuples.md)文章中深入了解此功能。</span><span class="sxs-lookup"><span data-stu-id="ebf66-145">You can learn more about this feature in the [Tuples](../tuples.md) article.</span></span>

## <a name="pattern-matching-on-generic-type-parameters"></a><span data-ttu-id="ebf66-146">泛型型別參數的模式比對</span><span class="sxs-lookup"><span data-stu-id="ebf66-146">Pattern matching on generic type parameters</span></span>

<span data-ttu-id="ebf66-147">從 C# 7.1 開始，`is` 和 `switch` 型別模式的模式運算式可能會有泛型型別參數的型別。</span><span class="sxs-lookup"><span data-stu-id="ebf66-147">Beginning with C# 7.1, the pattern expression for `is` and the `switch` type pattern may have the type of a generic type parameter.</span></span> <span data-ttu-id="ebf66-148">在檢查可能是 `struct` 或 `class` 型別的型別，以及您想要避免 boxing 時，這可能非常有用。</span><span class="sxs-lookup"><span data-stu-id="ebf66-148">This can be most useful when checking types that may be either `struct` or `class` types, and you want to avoid boxing.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="ebf66-149">參考組件產生</span><span class="sxs-lookup"><span data-stu-id="ebf66-149">Reference assembly generation</span></span>

<span data-ttu-id="ebf66-150">有兩個新編譯器選項會產生「僅參考的組件」  ：[-refout](../language-reference/compiler-options/refout-compiler-option.md) 和 [-refonly](../language-reference/compiler-options/refonly-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="ebf66-150">There are two new compiler options that generate *reference-only assemblies*: [-refout](../language-reference/compiler-options/refout-compiler-option.md) and [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="ebf66-151">連結的文章將更詳細地說明這些選項和參考組件。</span><span class="sxs-lookup"><span data-stu-id="ebf66-151">The linked articles explain these options and reference assemblies in more detail.</span></span>
