---
title: 字串插補 - C#
description: 了解字串插補在 C# 6 中如何運作
keywords: .NET, .NET Core, C#, 字串
author: mgroves
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: f8806f6b-3ac7-4ee6-9b3e-c524d5301ae9
ms.openlocfilehash: a9578d006861b987871071961437345c378a5b58
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="string-interpolation-in-c"></a><span data-ttu-id="372d4-104">C# 中的字串插值</span><span class="sxs-lookup"><span data-stu-id="372d4-104">String Interpolation in C#</span></span> #

<span data-ttu-id="372d4-105">「字串插補」是以字串變數的值取代字串中預留位置的方式。</span><span class="sxs-lookup"><span data-stu-id="372d4-105">String Interpolation is the way that placeholders in a string are replaced by the value of a string variable.</span></span> <span data-ttu-id="372d4-106">在 C# 6 之前，是透過 <xref:System.String.Format%2A?displayProperty=nameWithType> 來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="372d4-106">Before C# 6, the way to do this is with <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="372d4-107">這個運作方式還行，但由於它使用已編號的預留位置，因此更難以閱讀也更冗長。</span><span class="sxs-lookup"><span data-stu-id="372d4-107">This works okay, but since it uses numbered placeholders, it can be harder to read and more verbose.</span></span>

<span data-ttu-id="372d4-108">其他程式設計語言已經在語言中內建字串插補有一段時間。</span><span class="sxs-lookup"><span data-stu-id="372d4-108">Other programming languages have had string interpolation built into the language for a while.</span></span> <span data-ttu-id="372d4-109">例如，在 PHP 中：</span><span class="sxs-lookup"><span data-stu-id="372d4-109">For instance, in PHP:</span></span>

```php
$name = "Jonas";
echo "My name is $name.";
// This will output "My name is Jonas."
```

<span data-ttu-id="372d4-110">在 C# 6 中，我們終於也有該樣式的字串插補。</span><span class="sxs-lookup"><span data-stu-id="372d4-110">In C# 6, we finally have that style of string interpolation.</span></span> <span data-ttu-id="372d4-111">您可以在字串前使用 `$` 來指出它應該以變數/運算式來替代其值。</span><span class="sxs-lookup"><span data-stu-id="372d4-111">You can use a `$` before a string to indicate that it should substitute variables/expressions for their values.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="372d4-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="372d4-112">Prerequisites</span></span>
<span data-ttu-id="372d4-113">您將必須設定電腦以執行 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="372d4-113">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="372d4-114">您可以在 [.NET Core (英文)](https://www.microsoft.com/net/core) 頁面找到安裝指示。</span><span class="sxs-lookup"><span data-stu-id="372d4-114">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="372d4-115">您可以在 Windows、Ubuntu Linux、macOS 或是 Docker 容器中執行此應用程式。</span><span class="sxs-lookup"><span data-stu-id="372d4-115">You can run this application on Windows, Ubuntu Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="372d4-116">您將必須安裝慣用的程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="372d4-116">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="372d4-117">以下說明使用 [Visual Studio Code (英文)](https://code.visualstudio.com/)，這是開放原始碼的跨平台編輯器。</span><span class="sxs-lookup"><span data-stu-id="372d4-117">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="372d4-118">不過，您可以使用您熟悉的任何工具。</span><span class="sxs-lookup"><span data-stu-id="372d4-118">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="372d4-119">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="372d4-119">Create the Application</span></span>

<span data-ttu-id="372d4-120">現在您已安裝完所有工具，請建立新的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="372d4-120">Now that you've installed all the tools, create a new .NET Core application.</span></span> <span data-ttu-id="372d4-121">若要使用命令列產生器，請為您的專案建立一個目錄 (例如 `interpolated`)，然後在您慣用的殼層中執行下列命令︰</span><span class="sxs-lookup"><span data-stu-id="372d4-121">To use the command line generator, create a directory for your project, such as `interpolated`, and execute the following command in your favorite shell:</span></span>

```
dotnet new console
```

<span data-ttu-id="372d4-122">此命令會建立一個含有 *interpolated.csproj* 專案檔和 *Program.cs* 原始程式碼檔的準 .NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="372d4-122">This command creates a barebones .NET Core project with a project file, *interpolated.csproj*, and a source code file, *Program.cs*.</span></span> <span data-ttu-id="372d4-123">您將必須執行 `dotnet restore` 以還原編譯此專案所需的相依性。</span><span class="sxs-lookup"><span data-stu-id="372d4-123">You will need to execute `dotnet restore` to restore the dependencies needed to compile this project.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="372d4-124">若要執行這個程式，請使用 `dotnet run`。</span><span class="sxs-lookup"><span data-stu-id="372d4-124">To execute the program, use `dotnet run`.</span></span> <span data-ttu-id="372d4-125">您應該會在主控台看到 "Hello, World" 輸出。</span><span class="sxs-lookup"><span data-stu-id="372d4-125">You should see "Hello, World" output to the console.</span></span>



## <a name="intro-to-string-interpolation"></a><span data-ttu-id="372d4-126">字串插補簡介</span><span class="sxs-lookup"><span data-stu-id="372d4-126">Intro to String Interpolation</span></span>

<span data-ttu-id="372d4-127">使用 <xref:System.String.Format%2A?displayProperty=nameWithType> 時，您需要指定要由字串後的引數所取代字串中的「預留位置」。</span><span class="sxs-lookup"><span data-stu-id="372d4-127">With <xref:System.String.Format%2A?displayProperty=nameWithType>, you specify "placeholders" in a string that are replaced by the arguments following the string.</span></span> <span data-ttu-id="372d4-128">若是執行個體：</span><span class="sxs-lookup"><span data-stu-id="372d4-128">For instance:</span></span>

[!code-csharp[String.Format example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#StringFormatExample)]  

<span data-ttu-id="372d4-129">此範例將會輸出 "My name is Matt Groves"。</span><span class="sxs-lookup"><span data-stu-id="372d4-129">That will output "My name is Matt Groves".</span></span>

<span data-ttu-id="372d4-130">在 C# 6 中，您將不使用 `String.Format`，而是藉由在插補字串前加上 `$` 符號，然後直接在該字串中使用變數，來定義插捕字串。</span><span class="sxs-lookup"><span data-stu-id="372d4-130">In C# 6, instead of using `String.Format`, you define an interpolated string by prepending it with the `$` symbol, and then using the variables directly in the string.</span></span> <span data-ttu-id="372d4-131">若是執行個體：</span><span class="sxs-lookup"><span data-stu-id="372d4-131">For instance:</span></span>

[!code-csharp[Interpolation example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExample)]  

<span data-ttu-id="372d4-132">您不必只使用變數。</span><span class="sxs-lookup"><span data-stu-id="372d4-132">You don't have to use just variables.</span></span> <span data-ttu-id="372d4-133">您可以在括弧內使用任何運算式。</span><span class="sxs-lookup"><span data-stu-id="372d4-133">You can use any expression within the brackets.</span></span> <span data-ttu-id="372d4-134">若是執行個體：</span><span class="sxs-lookup"><span data-stu-id="372d4-134">For instance:</span></span>

[!code-csharp[Interpolation expression example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExpressionExample)]  

<span data-ttu-id="372d4-135">這會輸出：</span><span class="sxs-lookup"><span data-stu-id="372d4-135">Which would output:</span></span>

```
This is line number 1
This is line number 2
This is line number 3
This is line number 4
This is line number 5
```

## <a name="how-string-interpolation-works"></a><span data-ttu-id="372d4-136">字串插補如何運作</span><span class="sxs-lookup"><span data-stu-id="372d4-136">How string interpolation works</span></span>

<span data-ttu-id="372d4-137">在幕後，編譯器會將這個字串插補語法轉譯為 `String.Format`。</span><span class="sxs-lookup"><span data-stu-id="372d4-137">Behind the scenes, this string interpolation syntax is translated into `String.Format` by the compiler.</span></span> <span data-ttu-id="372d4-138">因此，您可以執行[之前對 `String.Format` 所進行的相同類型操作](../../standard/base-types/formatting-types.md)。</span><span class="sxs-lookup"><span data-stu-id="372d4-138">So, you can do the [same type of stuff you've done before with `String.Format`](../../standard/base-types/formatting-types.md).</span></span>

<span data-ttu-id="372d4-139">例如，您可以新增填補和設定數字格式：</span><span class="sxs-lookup"><span data-stu-id="372d4-139">For instance, you can add padding and numeric formatting:</span></span>

[!code-csharp[Interpolation formatting example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationFormattingExample)]  

<span data-ttu-id="372d4-140">上述範例會產生類似以下的輸出：</span><span class="sxs-lookup"><span data-stu-id="372d4-140">The above would output something like:</span></span>

```
998        5,177.67
999        6,719.30
1000       9,910.61
1001       529.34
1002       1,349.86
1003       2,660.82
1004       6,227.77
```

<span data-ttu-id="372d4-141">如果找不到變數名稱，則會產生編譯階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="372d4-141">If a variable name is not found, then a compile-time error is generated.</span></span>

<span data-ttu-id="372d4-142">若是執行個體：</span><span class="sxs-lookup"><span data-stu-id="372d4-142">For instance:</span></span>

```csharp
var animal = "fox";
var localizeMe = $"The {adj} brown {animal} jumped over the lazy {otheranimal}";
var adj = "quick";
Console.WriteLine(localizeMe);
```

<span data-ttu-id="372d4-143">如果您編譯它，則會收到錯誤：</span><span class="sxs-lookup"><span data-stu-id="372d4-143">If you compile this, you get errors:</span></span>
 
* <span data-ttu-id="372d4-144">`Cannot use local variable 'adj' before it is declared` - 在插補字串「之後」才宣告 `adj` 變數。</span><span class="sxs-lookup"><span data-stu-id="372d4-144">`Cannot use local variable 'adj' before it is declared` - the `adj` variable wasn't declared until *after* the interpolated string.</span></span>
* <span data-ttu-id="372d4-145">`The name 'otheranimal' does not exist in the current context` - 從未宣告名為 `otheranimal` 的變數</span><span class="sxs-lookup"><span data-stu-id="372d4-145">`The name 'otheranimal' does not exist in the current context` - a variable called `otheranimal` was never even declared</span></span>

## <a name="localization-and-internationalization"></a><span data-ttu-id="372d4-146">當地語系化和國際化</span><span class="sxs-lookup"><span data-stu-id="372d4-146">Localization and Internationalization</span></span>

<span data-ttu-id="372d4-147">插補字串支援 <xref:System.IFormattable?displayProperty=nameWithType> 和 <xref:System.FormattableString?displayProperty=nameWithType>，這對國際化相當有用。</span><span class="sxs-lookup"><span data-stu-id="372d4-147">An interpolated string supports <xref:System.IFormattable?displayProperty=nameWithType> and <xref:System.FormattableString?displayProperty=nameWithType>, which can be useful for internationalization.</span></span>

<span data-ttu-id="372d4-148">插補字串預設會使用目前的文化特性 (Culture)。</span><span class="sxs-lookup"><span data-stu-id="372d4-148">By default, an interpolated string uses the current culture.</span></span> <span data-ttu-id="372d4-149">若要使用不同的文化特性，請將字串插值轉換為 `IFormattable`。</span><span class="sxs-lookup"><span data-stu-id="372d4-149">To use a different culture, cast an interpolated string as `IFormattable`.</span></span> <span data-ttu-id="372d4-150">若是執行個體：</span><span class="sxs-lookup"><span data-stu-id="372d4-150">For instance:</span></span>

[!code-csharp[Interpolation internationalization example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationInternationalizationExample)]  

## <a name="conclusion"></a><span data-ttu-id="372d4-151">結論</span><span class="sxs-lookup"><span data-stu-id="372d4-151">Conclusion</span></span> 

<span data-ttu-id="372d4-152">在本教學課程中，您已了解如何使用 C# 6 的字串插補功能。</span><span class="sxs-lookup"><span data-stu-id="372d4-152">In this tutorial, you learned how to use string interpolation features of C# 6.</span></span> <span data-ttu-id="372d4-153">它基本上是一個撰寫簡單 `String.Format` 陳述式的更簡潔方式，但針對較進階的用法有一些注意事項。</span><span class="sxs-lookup"><span data-stu-id="372d4-153">It's basically a more concise way of writing simple `String.Format` statements, with some caveats for more advanced uses.</span></span> <span data-ttu-id="372d4-154">如需詳細資訊，請參閱[字串內插補點](../../csharp//language-reference/tokens/interpolated.md)主題。</span><span class="sxs-lookup"><span data-stu-id="372d4-154">For more information, see the [String interpolation](../../csharp//language-reference/tokens/interpolated.md) topic.</span></span>
