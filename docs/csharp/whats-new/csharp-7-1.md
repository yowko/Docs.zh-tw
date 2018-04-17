---
title: C# 7.1 中的新增功能
description: 7.1 C# 中的新功能的概觀。
keywords: C# 語言設計，7.1，Visual Studio 2017，
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: 02f1f8fc8f0a3221e00e2a3c43ce06423ca43672
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="6a665-104">C# 7.1 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="6a665-104">What's new in C# 7.1</span></span>

<span data-ttu-id="6a665-105">C# 7.1 是 C# 語言的第一個發行的小數點版本。</span><span class="sxs-lookup"><span data-stu-id="6a665-105">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="6a665-106">這表示這個語言的版本發行速度將會越來越快。</span><span class="sxs-lookup"><span data-stu-id="6a665-106">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="6a665-107">您很快能使用下列新功能。理想情況下，這些新功能只要一就緒，您就能開始使用。
</span><span class="sxs-lookup"><span data-stu-id="6a665-107">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="6a665-108">C# 7.1 加入了新功能，可將編譯器加以設定，使其符合指定的語言版本。
</span><span class="sxs-lookup"><span data-stu-id="6a665-108">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="6a665-109">這使得工具的升級與語言版本的升級能夠分開來決定。
</span><span class="sxs-lookup"><span data-stu-id="6a665-109">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="6a665-110">C# 7.1 也新增了[語言版本選擇](#language-version-selection)組態項目、三種新的語言功能和新的編譯器行為。</span><span class="sxs-lookup"><span data-stu-id="6a665-110">C# 7.1 adds the [language version selection](#language-version-selection) configuration element, three new language features and new compiler behavior.</span></span>

<span data-ttu-id="6a665-111">在此版本中的新語言功能包括：</span><span class="sxs-lookup"><span data-stu-id="6a665-111">The new language features in this release are:</span></span>

* [<span data-ttu-id="6a665-112">`async``Main`方法</span><span class="sxs-lookup"><span data-stu-id="6a665-112">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="6a665-113">應用程式的進入點允許使用`async`修飾詞。</span><span class="sxs-lookup"><span data-stu-id="6a665-113">The entry point for an application can have the `async` modifier.</span></span>
* [<span data-ttu-id="6a665-114">`default`常值運算式</span><span class="sxs-lookup"><span data-stu-id="6a665-114">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="6a665-115">目標類型可以推斷時，可以在預設值運算式中使用預設常值運算式。</span><span class="sxs-lookup"><span data-stu-id="6a665-115">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
* [<span data-ttu-id="6a665-116">推斷的 tuple 項目名稱</span><span class="sxs-lookup"><span data-stu-id="6a665-116">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="6a665-117">在許多情況下，Tuple 項目的名稱均可從 Tuple 初始化推斷來加以推斷。
</span><span class="sxs-lookup"><span data-stu-id="6a665-117">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>

<span data-ttu-id="6a665-118">最後，編譯器會有兩個選項`/refout`和`/refonly`該控制項[參考組件產生](#reference-assembly-generation)。</span><span class="sxs-lookup"><span data-stu-id="6a665-118">Finally, the compiler has two options `/refout` and `/refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

## <a name="language-version-selection"></a><span data-ttu-id="6a665-119">語言版本選取項目</span><span class="sxs-lookup"><span data-stu-id="6a665-119">Language version selection</span></span>

<span data-ttu-id="6a665-120">C# 編譯器自 Visual Studio 2017 15.3 與 .NET Core SDK 2.0 起開始支援 C# 7.1。</span><span class="sxs-lookup"><span data-stu-id="6a665-120">The C# compiler supports C# 7.1 starting with Visual Studio 2017 version 15.3, or the .NET Core SDK 2.0.</span></span> <span data-ttu-id="6a665-121">不過，7.1 的功能預設為關閉。</span><span class="sxs-lookup"><span data-stu-id="6a665-121">However, the 7.1 features are turned off by default.</span></span> <span data-ttu-id="6a665-122">若要啟用 7.1 功能，您需要變更您的專案的語言版本設定。</span><span class="sxs-lookup"><span data-stu-id="6a665-122">To enable the 7.1 features, you need to change the language version setting for your project.</span></span>

<span data-ttu-id="6a665-123">在 Visual Studio 中，以滑鼠右鍵按一下方案總管 中的專案節點，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="6a665-123">In Visual Studio, right-click on the project node in Solution Explorer and select **Properties**.</span></span> <span data-ttu-id="6a665-124">選取**建置**索引標籤並選取**進階** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6a665-124">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="6a665-125">在下拉式清單中選取**C# 最新次要版本 （最新版）**，或特定版本**C# 7.1**映像下列所示。</span><span class="sxs-lookup"><span data-stu-id="6a665-125">In the dropdown, select **C# latest minor version (latest)**, or the specific version **C# 7.1** as shown in the image following.</span></span> <span data-ttu-id="6a665-126">`latest`值表示您想要使用目前電腦上的最新的次要版本。</span><span class="sxs-lookup"><span data-stu-id="6a665-126">The `latest` value means you want to use the latest minor version on the current machine.</span></span> <span data-ttu-id="6a665-127">`C# 7.1`表示您想要使用 C# 7.1，即使有較新的次要版本發行。</span><span class="sxs-lookup"><span data-stu-id="6a665-127">The `C# 7.1` means that you want to use C# 7.1, even after newer minor versions are released.</span></span>

![設定的語言版本](./media/csharp-7-1/advanced-build-settings.png)

<span data-ttu-id="6a665-129">或者，您可以編輯"csproj 「 檔案和新增或修改下列行：</span><span class="sxs-lookup"><span data-stu-id="6a665-129">Alternatively, you can edit the "csproj" file and add or modify the following lines:</span></span>

```xml
<PropertyGroup>
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="6a665-130">如果您使用 Visual Studio IDE 來更新 csproj 檔時，IDE 會建立個別的節點，每個組建組態。</span><span class="sxs-lookup"><span data-stu-id="6a665-130">If you use the Visual Studio IDE to update your csproj files, the IDE creates separate nodes for each build configuration.</span></span> <span data-ttu-id="6a665-131">您將一般設定中的值相同所有組建組態，但您需要明確設定每個組建組態，或當您修改此設定時，請選取 「 所有的組態 >。</span><span class="sxs-lookup"><span data-stu-id="6a665-131">You'll typically set the value the same in all build configurations, but you need to set it explicitly for each build configuration, or select "All Configurations" when you modify this setting.</span></span> <span data-ttu-id="6a665-132">您會看到下列於 csproj 檔案中：</span><span class="sxs-lookup"><span data-stu-id="6a665-132">You'll see the following in your csproj file:</span></span>

```xml
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="6a665-133">有效的設定，如`LangVersion`項目：</span><span class="sxs-lookup"><span data-stu-id="6a665-133">Valid settings for the `LangVersion` element are:</span></span>

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

<span data-ttu-id="6a665-134">特殊字串`default`和`latest`解析成最新的主要和次要語言版本分別安裝在組建電腦上。</span><span class="sxs-lookup"><span data-stu-id="6a665-134">The special strings `default` and `latest` resolve to the latest major and minor language versions installed on the build machine, respectively.</span></span>

<span data-ttu-id="6a665-135">此設定以減少在您選擇要在專案中的新語言功能的開發環境中安裝新版本的 SDK 和工具。</span><span class="sxs-lookup"><span data-stu-id="6a665-135">This setting decouples installing new versions of the SDK and tools in your development environment from choosing to incorporate new language features in a project.</span></span> <span data-ttu-id="6a665-136">您可以在組建電腦上安裝最新的 SDK 和工具。</span><span class="sxs-lookup"><span data-stu-id="6a665-136">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="6a665-137">每個專案可以設定為使用其建立的特定版本的語言。</span><span class="sxs-lookup"><span data-stu-id="6a665-137">Each project can be configured to use a specific version of the language for its build.</span></span>

## <a name="async-main"></a><span data-ttu-id="6a665-138">主要的非同步處理</span><span class="sxs-lookup"><span data-stu-id="6a665-138">Async main</span></span>

<span data-ttu-id="6a665-139">*非同步主要*方法可讓您使用`await`中您`Main`方法。</span><span class="sxs-lookup"><span data-stu-id="6a665-139">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="6a665-140">在過去您必須這樣寫：</span><span class="sxs-lookup"><span data-stu-id="6a665-140">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="6a665-141">現在您可以這樣寫：</span><span class="sxs-lookup"><span data-stu-id="6a665-141">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="6a665-142">如果您的程式不會傳回結束代碼，您可以宣告`Main`方法會傳回<xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="6a665-142">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="6a665-143">閱讀更多詳細資料中的相關[非同步主要](../programming-guide/main-and-command-args/index.md)程式設計指南中的主題。</span><span class="sxs-lookup"><span data-stu-id="6a665-143">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) topic in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="6a665-144">預設常值運算式</span><span class="sxs-lookup"><span data-stu-id="6a665-144">Default literal expressions</span></span>

<span data-ttu-id="6a665-145">預設常值運算式是預設值運算式的增強功能。</span><span class="sxs-lookup"><span data-stu-id="6a665-145">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="6a665-146">這些運算式初始化的變數預設值。</span><span class="sxs-lookup"><span data-stu-id="6a665-146">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="6a665-147">在過去您必須這樣寫：</span><span class="sxs-lookup"><span data-stu-id="6a665-147">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="6a665-148">您現在可以略過初始化右手邊的類型：</span><span class="sxs-lookup"><span data-stu-id="6a665-148">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="6a665-149">您可以進一步了解 C# 程式設計手冊 > 主題中的這項增強功能上[預設值運算式](../programming-guide/statements-expressions-operators/default-value-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="6a665-149">You can learn more about this enhancement in the C# Programming Guide topic on [default value expressions](../programming-guide/statements-expressions-operators/default-value-expressions.md).</span></span>

<span data-ttu-id="6a665-150">這項增強功能也會變更部分的剖析規則[default 關鍵字](../language-reference/keywords/default.md)。</span><span class="sxs-lookup"><span data-stu-id="6a665-150">This enhancement also changes some of the parsing rules for the [default keyword](../language-reference/keywords/default.md).</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="6a665-151">Tuple 型別推導</span><span class="sxs-lookup"><span data-stu-id="6a665-151">Inferred tuple element names</span></span>

<span data-ttu-id="6a665-152">本方法為 C# 7.0 版本 Tuple 方法的改進，</span><span class="sxs-lookup"><span data-stu-id="6a665-152">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="6a665-153">許多次當您初始化 tuple，用於指派的右側的變數是您想要的 tuple 項目名稱相同：</span><span class="sxs-lookup"><span data-stu-id="6a665-153">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="6a665-154">Tuple 元素的名稱來推斷從用來初始化在 C# 7.1 tuple 的變數：</span><span class="sxs-lookup"><span data-stu-id="6a665-154">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="6a665-155">您可以進一步了解這項功能[Tuple](../tuples.md)主題。</span><span class="sxs-lookup"><span data-stu-id="6a665-155">You can learn more about this feature in the [Tuples](../tuples.md) topic.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="6a665-156">產生參考組件</span><span class="sxs-lookup"><span data-stu-id="6a665-156">Reference assembly generation</span></span>

<span data-ttu-id="6a665-157">有兩個新的編譯器選項產生*僅參考的組件*: [/refout](../language-reference/compiler-options/refout-compiler-option.md)和[/refonly](../language-reference/compiler-options/refonly-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="6a665-157">There are two new compiler options that generate *reference-only assemblies*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) and [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="6a665-158">連結的主題將說明這些選項和更詳細的參考組件。</span><span class="sxs-lookup"><span data-stu-id="6a665-158">The linked topics explain these options and reference assemblies in more detail.</span></span>
