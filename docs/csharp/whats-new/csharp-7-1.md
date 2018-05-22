---
title: C# 7.1 中的新增功能
description: C# 7.1 新功能的概觀。
ms.date: 08/16/2017
ms.openlocfilehash: 00baec45d7582d3ac12c7b0865241f5cd8159246
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="b43aa-103">C# 7.1 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="b43aa-103">What's new in C# 7.1</span></span>

<span data-ttu-id="b43aa-104">C# 7.1 是 C# 語言的第一個發行的小數點版本。</span><span class="sxs-lookup"><span data-stu-id="b43aa-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="b43aa-105">這表示這個語言的版本發行速度將會越來越快。</span><span class="sxs-lookup"><span data-stu-id="b43aa-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="b43aa-106">您很快能使用下列新功能。理想情況下，這些新功能只要一就緒，您就能開始使用。
</span><span class="sxs-lookup"><span data-stu-id="b43aa-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="b43aa-107">C# 7.1 加入了新功能，可將編譯器加以設定，使其符合指定的語言版本。
</span><span class="sxs-lookup"><span data-stu-id="b43aa-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="b43aa-108">這使得工具的升級與語言版本的升級能夠分開來決定。
</span><span class="sxs-lookup"><span data-stu-id="b43aa-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="b43aa-109">C# 7.1 也新增了[語言版本選擇](#language-version-selection)組態項目、三種新的語言功能和新的編譯器行為。</span><span class="sxs-lookup"><span data-stu-id="b43aa-109">C# 7.1 adds the [language version selection](#language-version-selection) configuration element, three new language features and new compiler behavior.</span></span>

<span data-ttu-id="b43aa-110">此版本的新款語言功能包括：</span><span class="sxs-lookup"><span data-stu-id="b43aa-110">The new language features in this release are:</span></span>

* [<span data-ttu-id="b43aa-111">`async``Main`方法</span><span class="sxs-lookup"><span data-stu-id="b43aa-111">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="b43aa-112">應用程式的進入點允許使用`async`修飾詞。</span><span class="sxs-lookup"><span data-stu-id="b43aa-112">The entry point for an application can have the `async` modifier.</span></span>
* [<span data-ttu-id="b43aa-113">`default`常值運算式</span><span class="sxs-lookup"><span data-stu-id="b43aa-113">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="b43aa-114">目標類型可以推斷時，可以在預設值運算式中使用預設常值運算式。</span><span class="sxs-lookup"><span data-stu-id="b43aa-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
* [<span data-ttu-id="b43aa-115">推斷的元組項目名稱</span><span class="sxs-lookup"><span data-stu-id="b43aa-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="b43aa-116">在許多情況下，Tuple 項目的名稱均可從 Tuple 初始化推斷來加以推斷。
</span><span class="sxs-lookup"><span data-stu-id="b43aa-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>

<span data-ttu-id="b43aa-117">最後，編譯器有兩個選項 `/refout` 和 `/refonly`，它們控制了[參考組件產生](#reference-assembly-generation)。</span><span class="sxs-lookup"><span data-stu-id="b43aa-117">Finally, the compiler has two options `/refout` and `/refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

## <a name="language-version-selection"></a><span data-ttu-id="b43aa-118">版本選取項目</span><span class="sxs-lookup"><span data-stu-id="b43aa-118">Language version selection</span></span>

<span data-ttu-id="b43aa-119">C# 編譯器自 Visual Studio 2017 15.3 與 .NET Core SDK 2.0 起開始支援 C# 7.1。</span><span class="sxs-lookup"><span data-stu-id="b43aa-119">The C# compiler supports C# 7.1 starting with Visual Studio 2017 version 15.3, or the .NET Core SDK 2.0.</span></span> <span data-ttu-id="b43aa-120">不過，7.1 的功能預設為關閉。</span><span class="sxs-lookup"><span data-stu-id="b43aa-120">However, the 7.1 features are turned off by default.</span></span> <span data-ttu-id="b43aa-121">若要啟用 7.1 功能，您需要變更專案的語言版本設定。</span><span class="sxs-lookup"><span data-stu-id="b43aa-121">To enable the 7.1 features, you need to change the language version setting for your project.</span></span>

<span data-ttu-id="b43aa-122">在 [方案總管]的專案節點上按一下滑鼠右鍵，並選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="b43aa-122">In Visual Studio, right-click on the project node in Solution Explorer and select **Properties**.</span></span> <span data-ttu-id="b43aa-123">選取 [建置] 索引標籤並選取 [進階] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b43aa-123">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="b43aa-124">在下拉式清單中選取 [C# 最新的次要版本 (最新版)]，或特定版本 [C# 7.1]，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="b43aa-124">In the dropdown, select **C# latest minor version (latest)**, or the specific version **C# 7.1** as shown in the image following.</span></span> <span data-ttu-id="b43aa-125">`latest` 值表示您想要使用目前電腦上的最新次要版本。</span><span class="sxs-lookup"><span data-stu-id="b43aa-125">The `latest` value means you want to use the latest minor version on the current machine.</span></span> <span data-ttu-id="b43aa-126">`C# 7.1` 表示您想要使用 C# 7.1，即使是已有較新的次要版本發行。</span><span class="sxs-lookup"><span data-stu-id="b43aa-126">The `C# 7.1` means that you want to use C# 7.1, even after newer minor versions are released.</span></span>

![設定語言版本](./media/csharp-7-1/advanced-build-settings.png)

<span data-ttu-id="b43aa-128">或者，您可以編輯 "csproj" 檔案，並新增或修改下列行：</span><span class="sxs-lookup"><span data-stu-id="b43aa-128">Alternatively, you can edit the "csproj" file and add or modify the following lines:</span></span>

```xml
<PropertyGroup>
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="b43aa-129">如果您使用 Visual Studio IDE 來更新 csproj 檔，IDE 會為每個組建組態建立個別的節點。</span><span class="sxs-lookup"><span data-stu-id="b43aa-129">If you use the Visual Studio IDE to update your csproj files, the IDE creates separate nodes for each build configuration.</span></span> <span data-ttu-id="b43aa-130">您一般會在所有組建組態中設定相同的值，但您需要針對每個組建組態明確設定，或在修改此設定時選取 [所有組態]。</span><span class="sxs-lookup"><span data-stu-id="b43aa-130">You'll typically set the value the same in all build configurations, but you need to set it explicitly for each build configuration, or select "All Configurations" when you modify this setting.</span></span> <span data-ttu-id="b43aa-131">您會在 csproj 檔案中看到下列內容：</span><span class="sxs-lookup"><span data-stu-id="b43aa-131">You'll see the following in your csproj file:</span></span>

```xml
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="b43aa-132">`LangVersion` 項目的有效設定為：</span><span class="sxs-lookup"><span data-stu-id="b43aa-132">Valid settings for the `LangVersion` element are:</span></span>

* `ISO-1`
* `ISO-2`
* `3`
* `4`
* `5`
* `6`
* `7`
* `7.1`
* `default`
* `latest`

<span data-ttu-id="b43aa-133">特殊字串 `default` 和 `latest` 會分別解析成安裝在組建電腦上的最新主要和次要語言版本。</span><span class="sxs-lookup"><span data-stu-id="b43aa-133">The special strings `default` and `latest` resolve to the latest major and minor language versions installed on the build machine, respectively.</span></span>

<span data-ttu-id="b43aa-134">此設定能讓在您開發環境中安裝新版本的 SDK 和工具與在專案中選擇納入新語言功能這兩件事分開。</span><span class="sxs-lookup"><span data-stu-id="b43aa-134">This setting decouples installing new versions of the SDK and tools in your development environment from choosing to incorporate new language features in a project.</span></span> <span data-ttu-id="b43aa-135">您可以在組建電腦上安裝最新的 SDK 和工具。</span><span class="sxs-lookup"><span data-stu-id="b43aa-135">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="b43aa-136">每個專案可以設定為針對其組建使用特定版本的語言。</span><span class="sxs-lookup"><span data-stu-id="b43aa-136">Each project can be configured to use a specific version of the language for its build.</span></span>

## <a name="async-main"></a><span data-ttu-id="b43aa-137">非同步主要</span><span class="sxs-lookup"><span data-stu-id="b43aa-137">Async main</span></span>

<span data-ttu-id="b43aa-138">「非同步主要」方法可讓您在 `Main` 方法中使用 `await`。</span><span class="sxs-lookup"><span data-stu-id="b43aa-138">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="b43aa-139">在過去您必須這樣寫：</span><span class="sxs-lookup"><span data-stu-id="b43aa-139">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="b43aa-140">現在您可以這樣寫：</span><span class="sxs-lookup"><span data-stu-id="b43aa-140">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="b43aa-141">如果您的程式不會傳回結束代碼，您可以宣告傳回 <xref:System.Threading.Tasks.Task> 的 `Main` 方法：</span><span class="sxs-lookup"><span data-stu-id="b43aa-141">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="b43aa-142">您可以在程式設計指南的[非同步主要](../programming-guide/main-and-command-args/index.md)主題中閱讀更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="b43aa-142">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) topic in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="b43aa-143">預設常值運算式</span><span class="sxs-lookup"><span data-stu-id="b43aa-143">Default literal expressions</span></span>

<span data-ttu-id="b43aa-144">預設常值運算式是預設值運算式的增強功能。</span><span class="sxs-lookup"><span data-stu-id="b43aa-144">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="b43aa-145">這些運算式會將變數初始化為預設值。</span><span class="sxs-lookup"><span data-stu-id="b43aa-145">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="b43aa-146">在過去您必須這樣寫：</span><span class="sxs-lookup"><span data-stu-id="b43aa-146">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="b43aa-147">您現在可以略過初始化右側的類型：</span><span class="sxs-lookup"><span data-stu-id="b43aa-147">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="b43aa-148">您可以在關於[預設值運算式](../programming-guide/statements-expressions-operators/default-value-expressions.md)的 C# 程式設計手冊主題進一步了解這項增強功能。</span><span class="sxs-lookup"><span data-stu-id="b43aa-148">You can learn more about this enhancement in the C# Programming Guide topic on [default value expressions](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span></span>

<span data-ttu-id="b43aa-149">這項增強功能也會變更 [default 關鍵字](../language-reference/keywords/default.md)的部分剖析規則。</span><span class="sxs-lookup"><span data-stu-id="b43aa-149">This enhancement also changes some of the parsing rules for the [default keyword](../language-reference/keywords/default.md).</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="b43aa-150">Tuple 型別推導</span><span class="sxs-lookup"><span data-stu-id="b43aa-150">Inferred tuple element names</span></span>

<span data-ttu-id="b43aa-151">本方法為 C# 7.0 版本 Tuple 方法的改進，</span><span class="sxs-lookup"><span data-stu-id="b43aa-151">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="b43aa-152">許多時候，當您初始化 Tuple 時，用於指派右側的變數會與您想要的元組項目名稱相同：</span><span class="sxs-lookup"><span data-stu-id="b43aa-152">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="b43aa-153">元組項目的名稱可以從用來在 C# 7.1 中初始化元組的變數加以推斷：</span><span class="sxs-lookup"><span data-stu-id="b43aa-153">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="b43aa-154">您可以在[元組](../tuples.md)主題中深入了解此功能。</span><span class="sxs-lookup"><span data-stu-id="b43aa-154">You can learn more about this feature in the [Tuples](../tuples.md) topic.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="b43aa-155">參考組件產生</span><span class="sxs-lookup"><span data-stu-id="b43aa-155">Reference assembly generation</span></span>

<span data-ttu-id="b43aa-156">有兩個新的編譯器選項會產生「僅參考的組件」：[/refout](../language-reference/compiler-options/refout-compiler-option.md) 和 [/refonly](../language-reference/compiler-options/refonly-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="b43aa-156">There are two new compiler options that generate *reference-only assemblies*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) and [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="b43aa-157">連結的主題將更詳細地說明這些選項和參考組件。</span><span class="sxs-lookup"><span data-stu-id="b43aa-157">The linked topics explain these options and reference assemblies in more detail.</span></span>
