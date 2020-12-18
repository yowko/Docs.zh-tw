---
title: C# 7.0 的新功能 - C# 指南
description: 取得 C# 語言版本 7.0 中新功能的概觀。
ms.date: 10/02/2020
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: c238439b0f435e579d932b3b1eb13e9b0061fa5f
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678231"
---
# <a name="whats-new-in-c-70-through-c-73"></a><span data-ttu-id="fba4f-103">C # 7.0 到 c # 7.3 的新功能</span><span class="sxs-lookup"><span data-stu-id="fba4f-103">What's new in C# 7.0 through C# 7.3</span></span>

<span data-ttu-id="fba4f-104">C # 7.0 到 c # 7.3 針對您使用 c # 的開發體驗引進了許多功能和累加的改進。</span><span class="sxs-lookup"><span data-stu-id="fba4f-104">C# 7.0 through C# 7.3 brought a number of features and incremental improvements to your development experience with C#.</span></span> <span data-ttu-id="fba4f-105">本文概要說明新的語言功能和編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="fba4f-105">This article provides an overview of the new language features and compiler options.</span></span> <span data-ttu-id="fba4f-106">描述說明 c # 7.3 的行為，這是 .NET Framework 架構應用程式所支援的最新版本。</span><span class="sxs-lookup"><span data-stu-id="fba4f-106">The descriptions describe the behavior for C# 7.3, which is the most recent version supported for .NET Framework-based applications.</span></span>

<span data-ttu-id="fba4f-107">[語言版本選取](../language-reference/configure-language-version.md)設定專案是使用 c # 7.1 新增的，可讓您在專案檔中指定編譯器語言版本。</span><span class="sxs-lookup"><span data-stu-id="fba4f-107">The [language version selection](../language-reference/configure-language-version.md) configuration element was added with C# 7.1, which enables you to specify the compiler language version in your project file.</span></span>

<span data-ttu-id="fba4f-108">C # 7.0-7.3 將這些功能和主題新增至 c # 語言：</span><span class="sxs-lookup"><span data-stu-id="fba4f-108">C# 7.0-7.3 adds these features and themes to the C# language:</span></span>

- [<span data-ttu-id="fba4f-109">元組和捨棄</span><span class="sxs-lookup"><span data-stu-id="fba4f-109">Tuples and discards</span></span>](#tuples-and-discards)
  - <span data-ttu-id="fba4f-110">您可以建立包含多個公用欄位的輕量、未具名的類型。</span><span class="sxs-lookup"><span data-stu-id="fba4f-110">You can create lightweight, unnamed types that contain multiple public fields.</span></span> <span data-ttu-id="fba4f-111">編譯器和 IDE 工具了解這些類型的語意。</span><span class="sxs-lookup"><span data-stu-id="fba4f-111">Compilers and IDE tools understand the semantics of these types.</span></span>
  - <span data-ttu-id="fba4f-112">捨棄是當您不在意指派的值時，於指派內使用的僅限寫入且暫時之變數。</span><span class="sxs-lookup"><span data-stu-id="fba4f-112">Discards are temporary, write-only variables used in assignments when you don't care about the value assigned.</span></span> <span data-ttu-id="fba4f-113">解構 Tuple 及使用者定義型別，以及使用 `out` 參數呼叫方法時，捨棄最為實用。</span><span class="sxs-lookup"><span data-stu-id="fba4f-113">They're most useful when deconstructing tuples and user-defined types, as well as when calling methods with `out` parameters.</span></span>
- [<span data-ttu-id="fba4f-114">模式比對</span><span class="sxs-lookup"><span data-stu-id="fba4f-114">Pattern Matching</span></span>](#pattern-matching)
  - <span data-ttu-id="fba4f-115">您可以建立以任意類型和這些類型成員的值為基礎的分支邏輯。</span><span class="sxs-lookup"><span data-stu-id="fba4f-115">You can create branching logic based on arbitrary types and values of the members of those types.</span></span>
- [<span data-ttu-id="fba4f-116">`async``Main`方法</span><span class="sxs-lookup"><span data-stu-id="fba4f-116">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="fba4f-117">應用程式的進入點允許使用`async`修飾詞。</span><span class="sxs-lookup"><span data-stu-id="fba4f-117">The entry point for an application can have the `async` modifier.</span></span>
- [<span data-ttu-id="fba4f-118">區域函數</span><span class="sxs-lookup"><span data-stu-id="fba4f-118">Local Functions</span></span>](#local-functions)
  - <span data-ttu-id="fba4f-119">您可以將函式巢狀放置在其他函式內，限制其範圍和可視性。</span><span class="sxs-lookup"><span data-stu-id="fba4f-119">You can nest functions inside other functions to limit their scope and visibility.</span></span>
- [<span data-ttu-id="fba4f-120">更多運算式主體成員</span><span class="sxs-lookup"><span data-stu-id="fba4f-120">More expression-bodied members</span></span>](#more-expression-bodied-members)
  - <span data-ttu-id="fba4f-121">可以使用運算式來撰寫的成員清單已經增長。</span><span class="sxs-lookup"><span data-stu-id="fba4f-121">The list of members that can be authored using expressions has grown.</span></span>
- [<span data-ttu-id="fba4f-122">`throw` 表達 式</span><span class="sxs-lookup"><span data-stu-id="fba4f-122">`throw` Expressions</span></span>](#throw-expressions)
  - <span data-ttu-id="fba4f-123">您可以在程式碼建構中擲回例外狀況 (因為先前 `throw` 是陳述式，所以您無法這麼做)。</span><span class="sxs-lookup"><span data-stu-id="fba4f-123">You can throw exceptions in code constructs that previously weren't allowed because `throw` was a statement.</span></span>
- [<span data-ttu-id="fba4f-124">`default` 常值運算式</span><span class="sxs-lookup"><span data-stu-id="fba4f-124">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="fba4f-125">目標類型可以推斷時，可以在預設值運算式中使用預設常值運算式。</span><span class="sxs-lookup"><span data-stu-id="fba4f-125">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
- [<span data-ttu-id="fba4f-126">數值常值的語法增強功能</span><span class="sxs-lookup"><span data-stu-id="fba4f-126">Numeric literal syntax improvements</span></span>](#numeric-literal-syntax-improvements)
  - <span data-ttu-id="fba4f-127">新的語彙基元改善了數值常數的可讀性。</span><span class="sxs-lookup"><span data-stu-id="fba4f-127">New tokens improve readability for numeric constants.</span></span>
- [<span data-ttu-id="fba4f-128">`out` 變數</span><span class="sxs-lookup"><span data-stu-id="fba4f-128">`out` variables</span></span>](#out-variables)
  - <span data-ttu-id="fba4f-129">您可以宣告 `out` 內嵌值作為使用它們之方法的引數。</span><span class="sxs-lookup"><span data-stu-id="fba4f-129">You can declare `out` values inline as arguments to the method where they're used.</span></span>
- [<span data-ttu-id="fba4f-130">非後置具名引數</span><span class="sxs-lookup"><span data-stu-id="fba4f-130">Non-trailing named arguments</span></span>](#non-trailing-named-arguments)
  - <span data-ttu-id="fba4f-131">具名引數之後可以接著位置引數。</span><span class="sxs-lookup"><span data-stu-id="fba4f-131">Named arguments can be followed by positional arguments.</span></span>
- [<span data-ttu-id="fba4f-132">`private protected` 存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="fba4f-132">`private protected` access modifier</span></span>](#private-protected-access-modifier)
  - <span data-ttu-id="fba4f-133">您可利用 `private protected` 存取修飾詞，存取相同組件中的衍生類別。</span><span class="sxs-lookup"><span data-stu-id="fba4f-133">The `private protected` access modifier enables access for derived classes in the same assembly.</span></span>
- [<span data-ttu-id="fba4f-134">改進的多載解析</span><span class="sxs-lookup"><span data-stu-id="fba4f-134">Improved overload resolution</span></span>](#improved-overload-candidates)
  - <span data-ttu-id="fba4f-135">解決多載解析不明確的新規則。</span><span class="sxs-lookup"><span data-stu-id="fba4f-135">New rules to resolve overload resolution ambiguity.</span></span>
- [<span data-ttu-id="fba4f-136">撰寫安全、有效率之程式碼的技巧</span><span class="sxs-lookup"><span data-stu-id="fba4f-136">Techniques for writing safe efficient code</span></span>](#enabling-more-efficient-safe-code)
  - <span data-ttu-id="fba4f-137">此為語法改進功能組合，其可讓使用參考語意進行實質型別作業變得可能。</span><span class="sxs-lookup"><span data-stu-id="fba4f-137">A combination of syntax improvements that enable working with value types using reference semantics.</span></span>

<span data-ttu-id="fba4f-138">最後，編譯器有新的選項：</span><span class="sxs-lookup"><span data-stu-id="fba4f-138">Finally, the compiler has new options:</span></span>

- <span data-ttu-id="fba4f-139">`-refout` 以及 `-refonly` 該控制項 [參考元件的產生](#reference-assembly-generation)。</span><span class="sxs-lookup"><span data-stu-id="fba4f-139">`-refout` and `-refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>
- <span data-ttu-id="fba4f-140">`-publicsign`，用來啟用組件的開放原始碼軟體 (OSS) 簽署。</span><span class="sxs-lookup"><span data-stu-id="fba4f-140">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="fba4f-141">`-pathmap`，用來提供來源目錄的對應。</span><span class="sxs-lookup"><span data-stu-id="fba4f-141">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="fba4f-142">此文章的其餘部分將概述各個功能。</span><span class="sxs-lookup"><span data-stu-id="fba4f-142">The remainder of this article provides an overview of each feature.</span></span> <span data-ttu-id="fba4f-143">針對每項功能，您將瞭解其背後的原因和語法。</span><span class="sxs-lookup"><span data-stu-id="fba4f-143">For each feature, you'll learn the reasoning behind it and the syntax.</span></span> <span data-ttu-id="fba4f-144">您可以使用 `dotnet try` 全域工具，在您的環境中探索這些功能：</span><span class="sxs-lookup"><span data-stu-id="fba4f-144">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="fba4f-145">安裝 [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) 全域工具。</span><span class="sxs-lookup"><span data-stu-id="fba4f-145">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="fba4f-146">複製 [dotnet/try-samples](https://github.com/dotnet/try-samples) 存放庫。</span><span class="sxs-lookup"><span data-stu-id="fba4f-146">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="fba4f-147">將目前目錄設為 *try-samples* 存放庫的 *csharp7* 子目錄。</span><span class="sxs-lookup"><span data-stu-id="fba4f-147">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="fba4f-148">執行 `dotnet try`。</span><span class="sxs-lookup"><span data-stu-id="fba4f-148">Run `dotnet try`.</span></span>

## <a name="tuples-and-discards"></a><span data-ttu-id="fba4f-149">元組和捨棄</span><span class="sxs-lookup"><span data-stu-id="fba4f-149">Tuples and discards</span></span>

<span data-ttu-id="fba4f-150">C# 為類別和結構提供豐富的語法，可用來解釋您的設計目的。</span><span class="sxs-lookup"><span data-stu-id="fba4f-150">C# provides a rich syntax for classes and structs that is used to explain your design intent.</span></span> <span data-ttu-id="fba4f-151">但有時候豐富的語法需要額外的工作才能得到最少的好處。</span><span class="sxs-lookup"><span data-stu-id="fba4f-151">But sometimes that rich syntax requires extra work with minimal benefit.</span></span> <span data-ttu-id="fba4f-152">您可能經常撰寫需要包含多個資料項目之簡單結構的方法。</span><span class="sxs-lookup"><span data-stu-id="fba4f-152">You may often write methods that need a simple structure containing more than one data element.</span></span> <span data-ttu-id="fba4f-153">為了支援這些案例，C# 已新增 *Tuple*。</span><span class="sxs-lookup"><span data-stu-id="fba4f-153">To support these scenarios *tuples* were added to C#.</span></span> <span data-ttu-id="fba4f-154">Tuple 是輕量的資料結構，其中包含多個欄位來代表資料成員。</span><span class="sxs-lookup"><span data-stu-id="fba4f-154">Tuples are lightweight data structures that contain multiple fields to represent the data members.</span></span> <span data-ttu-id="fba4f-155">這些欄位不會經過驗證，且您無法定義自己的方法。</span><span class="sxs-lookup"><span data-stu-id="fba4f-155">The fields aren't validated, and you can't define your own methods.</span></span> <span data-ttu-id="fba4f-156">C # 元組類型支援 `==` 和 `!=` 。</span><span class="sxs-lookup"><span data-stu-id="fba4f-156">C# tuple types support `==` and `!=`.</span></span> <span data-ttu-id="fba4f-157">如需詳細資訊，</span><span class="sxs-lookup"><span data-stu-id="fba4f-157">For more information.</span></span>

> [!NOTE]
> <span data-ttu-id="fba4f-158">Tuple 在 C# 7.0 之前即可使用，但效率不彰且沒有語言支援。</span><span class="sxs-lookup"><span data-stu-id="fba4f-158">Tuples were available before C# 7.0, but they were inefficient and had no language support.</span></span> <span data-ttu-id="fba4f-159">這表示元組元素只能參考為 `Item1`及 `Item2` 等等。</span><span class="sxs-lookup"><span data-stu-id="fba4f-159">This meant that tuple elements could only be referenced as `Item1`, `Item2` and so on.</span></span> <span data-ttu-id="fba4f-160">C# 7.0 加入了 Tuple 的語言支援，讓 Tuple 欄位的語意名稱能使用全新且更具效率的 Tuple 型別。</span><span class="sxs-lookup"><span data-stu-id="fba4f-160">C# 7.0 introduces language support for tuples, which enables semantic names for the fields of a tuple using new, more efficient tuple types.</span></span>

<span data-ttu-id="fba4f-161">您可以將值指派給每個成員，並選擇性地提供語意名稱給每個 Tuple 的成員，以建立 Tuple：</span><span class="sxs-lookup"><span data-stu-id="fba4f-161">You can create a tuple by assigning a value to each member, and optionally providing semantic names to each of the members of the tuple:</span></span>

[!code-csharp[NamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#NamedTuple "Named tuple")]

<span data-ttu-id="fba4f-162">`namedLetters` Tuple 包含稱為 `Alpha` 和 `Beta` 的欄位。</span><span class="sxs-lookup"><span data-stu-id="fba4f-162">The `namedLetters` tuple contains fields referred to as `Alpha` and `Beta`.</span></span> <span data-ttu-id="fba4f-163">這些名稱只會在編譯時期存在，而且不會保留，例如在執行時間使用反映檢查元組時。</span><span class="sxs-lookup"><span data-stu-id="fba4f-163">Those names exist only at compile time and aren't preserved, for example when inspecting the tuple using reflection at run time.</span></span>

<span data-ttu-id="fba4f-164">在 Tuple 指派中，您也可以在指派的右邊，指定欄位的名稱︰</span><span class="sxs-lookup"><span data-stu-id="fba4f-164">In a tuple assignment, you can also specify the names of the fields on the right-hand side of the assignment:</span></span>

[!code-csharp[ImplicitNamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#ImplicitNamedTuple "Implicitly named tuple")]

<span data-ttu-id="fba4f-165">有時候您可能會想要解除封裝已從方法傳回的 Tuple 成員。</span><span class="sxs-lookup"><span data-stu-id="fba4f-165">There may be times when you want to unpackage the members of a tuple that were returned from a method.</span></span>  <span data-ttu-id="fba4f-166">您可以藉由為 Tuple 中的每個值宣告不同變數來這麼做。</span><span class="sxs-lookup"><span data-stu-id="fba4f-166">You can do that by declaring separate variables for each of the values in the tuple.</span></span> <span data-ttu-id="fba4f-167">這種解除封裝稱為 *解構* Tuple：</span><span class="sxs-lookup"><span data-stu-id="fba4f-167">This unpackaging is called *deconstructing* the tuple:</span></span>

[!code-csharp[CallingWithDeconstructor](~/samples/snippets/csharp/new-in-7/program.cs#CallingWithDeconstructor "Deconstructing a tuple")]

<span data-ttu-id="fba4f-168">您也可以在 .NET 中為任何類型提供類似的解構。</span><span class="sxs-lookup"><span data-stu-id="fba4f-168">You can also provide a similar deconstruction for any type in .NET.</span></span> <span data-ttu-id="fba4f-169">您可以將 `Deconstruct` 方法撰寫為類別的成員。</span><span class="sxs-lookup"><span data-stu-id="fba4f-169">You write a `Deconstruct` method as a member of the class.</span></span> <span data-ttu-id="fba4f-170">`Deconstruct` 方法為您想要擷取的每個屬性提供一組 `out` 引數。</span><span class="sxs-lookup"><span data-stu-id="fba4f-170">That `Deconstruct` method provides a set of `out` arguments for each of the properties you want to extract.</span></span> <span data-ttu-id="fba4f-171">請考慮這個 `Point` 類別，它會提供 deconstructor 方法，擷取 `X` 和 `Y` 座標︰</span><span class="sxs-lookup"><span data-stu-id="fba4f-171">Consider this `Point` class that provides a deconstructor method that extracts the `X` and `Y` coordinates:</span></span>

[!code-csharp[PointWithDeconstruction](~/samples/snippets/csharp/new-in-7/point.cs#PointWithDeconstruction "Point with deconstruction method")]

<span data-ttu-id="fba4f-172">您可以藉由將 `Point` 指派給 Tuple 來擷取個別的欄位：</span><span class="sxs-lookup"><span data-stu-id="fba4f-172">You can extract the individual fields by assigning a `Point` to a tuple:</span></span>

[!code-csharp[DeconstructPoint](~/samples/snippets/csharp/new-in-7/program.cs#DeconstructPoint "Deconstruct a point")]

<span data-ttu-id="fba4f-173">當您初始化元組時，所使用的變數會與您想要用於元組專案的名稱相同：可從用來初始化元組的變數推斷元組元素的名稱：</span><span class="sxs-lookup"><span data-stu-id="fba4f-173">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements: The names of tuple elements can be inferred from the variables used to initialize the tuple:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="fba4f-174">您可以在「 [元組類型](../language-reference/builtin-types/value-tuples.md) 」一文中深入瞭解這項功能。</span><span class="sxs-lookup"><span data-stu-id="fba4f-174">You can learn more about this feature in the [Tuple types](../language-reference/builtin-types/value-tuples.md) article.</span></span>

<span data-ttu-id="fba4f-175">通常在您解構元組或以 `out` 參數呼叫方法時，會強制您要定義變數，而您無須在意變數的值也沒有使用該值的打算。</span><span class="sxs-lookup"><span data-stu-id="fba4f-175">Often when deconstructing a tuple or calling a method with `out` parameters, you're forced to define a variable whose value you don't care about and don't intend to use.</span></span> <span data-ttu-id="fba4f-176">C# 新增了對 *捨棄* 的支援，來應付這種狀況。</span><span class="sxs-lookup"><span data-stu-id="fba4f-176">C# adds support for *discards* to handle this scenario.</span></span> <span data-ttu-id="fba4f-177">捨棄是僅限寫入的變數，其名稱為 `_` (底線字元)；您可將所有想要捨棄的值指派到單一變數。</span><span class="sxs-lookup"><span data-stu-id="fba4f-177">A discard is a write-only variable whose name is `_` (the underscore character); you can assign all of the values that you intend to discard to the single variable.</span></span> <span data-ttu-id="fba4f-178">捨棄類似於未經指派的變數；和指派陳述式一樣，都不能用於程式碼中。</span><span class="sxs-lookup"><span data-stu-id="fba4f-178">A discard is like an unassigned variable; apart from the assignment statement, the discard can't be used in code.</span></span>

<span data-ttu-id="fba4f-179">下列情況中支援捨棄：</span><span class="sxs-lookup"><span data-stu-id="fba4f-179">Discards are supported in the following scenarios:</span></span>

- <span data-ttu-id="fba4f-180">解構元組或使用者定義型別時。</span><span class="sxs-lookup"><span data-stu-id="fba4f-180">When deconstructing tuples or user-defined types.</span></span>
- <span data-ttu-id="fba4f-181">以 [out](../language-reference/keywords/out-parameter-modifier.md) 參數呼叫方法時。</span><span class="sxs-lookup"><span data-stu-id="fba4f-181">When calling methods with [out](../language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>
- <span data-ttu-id="fba4f-182">執行 [is](../language-reference/keywords/is.md) 及 [switch](../language-reference/keywords/switch.md) 陳述式的模式比對作業時。</span><span class="sxs-lookup"><span data-stu-id="fba4f-182">In a pattern matching operation with the [is](../language-reference/keywords/is.md) and [switch](../language-reference/keywords/switch.md) statements.</span></span>
- <span data-ttu-id="fba4f-183">作為獨立識別項，當您想要將指派的值明確識別為捨棄時。</span><span class="sxs-lookup"><span data-stu-id="fba4f-183">As a standalone identifier when you want to explicitly identify the value of an assignment as a discard.</span></span>

<span data-ttu-id="fba4f-184">下列範例定義的 `QueryCityDataForYears` 方法，會傳回包含兩個不同年份之城市資料的 6 元組。</span><span class="sxs-lookup"><span data-stu-id="fba4f-184">The following example defines a `QueryCityDataForYears` method that returns a 6-tuple that contains data for a city for two different years.</span></span> <span data-ttu-id="fba4f-185">範例中的方法呼叫只有對方法傳回的兩個母體有效，所以會在解構元組時，將元組中剩餘的值視作捨棄處理。</span><span class="sxs-lookup"><span data-stu-id="fba4f-185">The method call in the example is concerned only with the two population values returned by the method and so treats the remaining values in the tuple as discards when it deconstructs the tuple.</span></span>

[!code-csharp[Tuple-discard](~/samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

<span data-ttu-id="fba4f-186">如需詳細資訊，請參閱[捨棄](../discards.md)。</span><span class="sxs-lookup"><span data-stu-id="fba4f-186">For more information, see [Discards](../discards.md).</span></span>

## <a name="pattern-matching"></a><span data-ttu-id="fba4f-187">模式比對</span><span class="sxs-lookup"><span data-stu-id="fba4f-187">Pattern matching</span></span>

<span data-ttu-id="fba4f-188">*模式* 比對是一組功能，可讓您在程式碼中以新的方式表示控制流程。</span><span class="sxs-lookup"><span data-stu-id="fba4f-188">*Pattern matching* is a set of features that enable new ways to express control flow in your code.</span></span> <span data-ttu-id="fba4f-189">您可以針對其類型、值或其屬性的值來測試變數。</span><span class="sxs-lookup"><span data-stu-id="fba4f-189">You can test variables for their type, values or the values of their properties.</span></span> <span data-ttu-id="fba4f-190">這些技術可建立更容易閱讀的程式碼流程。</span><span class="sxs-lookup"><span data-stu-id="fba4f-190">These techniques create more readable code flow.</span></span>

<span data-ttu-id="fba4f-191">模式比對支援 `is` 運算式和 `switch` 運算式。</span><span class="sxs-lookup"><span data-stu-id="fba4f-191">Pattern matching supports `is` expressions and `switch` expressions.</span></span> <span data-ttu-id="fba4f-192">每個都讓您能檢查物件和其屬性，以判斷該物件是否符合搜尋的模式。</span><span class="sxs-lookup"><span data-stu-id="fba4f-192">Each enables inspecting an object and its properties to determine if that object satisfies the sought pattern.</span></span> <span data-ttu-id="fba4f-193">您使用 `when` 關鍵字來指定其他規則給該模式。</span><span class="sxs-lookup"><span data-stu-id="fba4f-193">You use the `when` keyword to specify additional rules to the pattern.</span></span>

<span data-ttu-id="fba4f-194">`is`模式運算式會擴充熟悉的[ `is` 運算子](../language-reference/keywords/is.md#pattern-matching-with-is)，以查詢其類型的物件，並在一個指令中指派結果。</span><span class="sxs-lookup"><span data-stu-id="fba4f-194">The `is` pattern expression extends the familiar [`is` operator](../language-reference/keywords/is.md#pattern-matching-with-is) to query an object about its type and assign the result in one instruction.</span></span> <span data-ttu-id="fba4f-195">下列程式碼會檢查變數是否為 `int`，如果是，則將其加入至目前的總和：</span><span class="sxs-lookup"><span data-stu-id="fba4f-195">The following code checks if a variable is an `int`, and if so, adds it to the current sum:</span></span>

```csharp
if (input is int count)
    sum += count;
```

<span data-ttu-id="fba4f-196">上述的小範例示範 `is` 運算式的增強功能。</span><span class="sxs-lookup"><span data-stu-id="fba4f-196">The preceding small example demonstrates the enhancements to the `is` expression.</span></span> <span data-ttu-id="fba4f-197">您可以對實值型別以及參考型別進行測試，而且您可以將成功的結果指派給正確型別的新變數。</span><span class="sxs-lookup"><span data-stu-id="fba4f-197">You can test against value types as well as reference types, and you can assign the successful result to a new variable of the correct type.</span></span>

<span data-ttu-id="fba4f-198">switch 比對運算式的語法很熟悉，是以已屬於 C# 語言一部分的 `switch` 陳述式為基礎。</span><span class="sxs-lookup"><span data-stu-id="fba4f-198">The switch match expression has a familiar syntax, based on the `switch` statement already part of the C# language.</span></span> <span data-ttu-id="fba4f-199">更新的 switch 陳述式有數個新的建構：</span><span class="sxs-lookup"><span data-stu-id="fba4f-199">The updated switch statement has several new constructs:</span></span>

- <span data-ttu-id="fba4f-200">`switch` 運算式的控管型別不再限於整數型別、`Enum` 型別、`string`，或對應至這些其中一種類型的可為 Null 的型別。</span><span class="sxs-lookup"><span data-stu-id="fba4f-200">The governing type of a `switch` expression is no longer restricted to integral types, `Enum` types, `string`, or a nullable type corresponding to one of those types.</span></span> <span data-ttu-id="fba4f-201">可以使用任何型別。</span><span class="sxs-lookup"><span data-stu-id="fba4f-201">Any type may be used.</span></span>
- <span data-ttu-id="fba4f-202">您可以測試每個 `case` 標籤中的 `switch` 運算式型別。</span><span class="sxs-lookup"><span data-stu-id="fba4f-202">You can test the type of the `switch` expression in each `case` label.</span></span> <span data-ttu-id="fba4f-203">如同使用 `is` 運算式，您可以將新的變數指派給該型別。</span><span class="sxs-lookup"><span data-stu-id="fba4f-203">As with the `is` expression, you may assign a new variable to that type.</span></span>
- <span data-ttu-id="fba4f-204">您可以加入 `when` 子句，以進一步測試該變數的條件。</span><span class="sxs-lookup"><span data-stu-id="fba4f-204">You may add a `when` clause to further test conditions on that variable.</span></span>
- <span data-ttu-id="fba4f-205">`case` 標籤的順序現在很重要。</span><span class="sxs-lookup"><span data-stu-id="fba4f-205">The order of `case` labels is now important.</span></span> <span data-ttu-id="fba4f-206">系統會執行要比對的第一個分支；其他則會略過。</span><span class="sxs-lookup"><span data-stu-id="fba4f-206">The first branch to match is executed; others are skipped.</span></span>

<span data-ttu-id="fba4f-207">下列程式碼可示範這些新功能：</span><span class="sxs-lookup"><span data-stu-id="fba4f-207">The following code demonstrates these new features:</span></span>

```csharp
public static int SumPositiveNumbers(IEnumerable<object> sequence)
{
    int sum = 0;
    foreach (var i in sequence)
    {
        switch (i)
        {
            case 0:
                break;
            case IEnumerable<int> childSequence:
            {
                foreach(var item in childSequence)
                    sum += (item > 0) ? item : 0;
                break;
            }
            case int n when n > 0:
                sum += n;
                break;
            case null:
                throw new NullReferenceException("Null found in sequence");
            default:
                throw new InvalidOperationException("Unrecognized type");
        }
    }
    return sum;
}
```

- <span data-ttu-id="fba4f-208">`case 0:` 是熟悉的常數模式。</span><span class="sxs-lookup"><span data-stu-id="fba4f-208">`case 0:` is the familiar constant pattern.</span></span>
- <span data-ttu-id="fba4f-209">`case IEnumerable<int> childSequence:` 是一種型別模式。</span><span class="sxs-lookup"><span data-stu-id="fba4f-209">`case IEnumerable<int> childSequence:` is a type pattern.</span></span>
- <span data-ttu-id="fba4f-210">`case int n when n > 0:` 是一種具有其他 `when` 條件的型別模式。</span><span class="sxs-lookup"><span data-stu-id="fba4f-210">`case int n when n > 0:` is a type pattern with an additional `when` condition.</span></span>
- <span data-ttu-id="fba4f-211">`case null:` 是 Null 模式。</span><span class="sxs-lookup"><span data-stu-id="fba4f-211">`case null:` is the null pattern.</span></span>
- <span data-ttu-id="fba4f-212">`default:` 是熟悉的預設案例。</span><span class="sxs-lookup"><span data-stu-id="fba4f-212">`default:` is the familiar default case.</span></span>

<span data-ttu-id="fba4f-213">從 C# 7.1 開始，`is` 和 `switch` 型別模式的模式運算式可能會有泛型型別參數的型別。</span><span class="sxs-lookup"><span data-stu-id="fba4f-213">Beginning with C# 7.1, the pattern expression for `is` and the `switch` type pattern may have the type of a generic type parameter.</span></span> <span data-ttu-id="fba4f-214">在檢查可能是 `struct` 或 `class` 型別的型別，以及您想要避免 boxing 時，這可能非常有用。</span><span class="sxs-lookup"><span data-stu-id="fba4f-214">This can be most useful when checking types that may be either `struct` or `class` types, and you want to avoid boxing.</span></span>

<span data-ttu-id="fba4f-215">您可以在 [C# 中的模式比對](../pattern-matching.md)中深入了解模式比對。</span><span class="sxs-lookup"><span data-stu-id="fba4f-215">You can learn more about pattern matching in [Pattern Matching in C#](../pattern-matching.md).</span></span>

## <a name="async-main"></a><span data-ttu-id="fba4f-216">非同步主要</span><span class="sxs-lookup"><span data-stu-id="fba4f-216">Async main</span></span>

<span data-ttu-id="fba4f-217">「非同步主要」方法可讓您在 `Main` 方法中使用 `await`。</span><span class="sxs-lookup"><span data-stu-id="fba4f-217">An *async main* method enables you to use `await` in your `Main` method.</span></span> <span data-ttu-id="fba4f-218">在過去您必須這樣寫：</span><span class="sxs-lookup"><span data-stu-id="fba4f-218">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="fba4f-219">現在您可以這樣寫：</span><span class="sxs-lookup"><span data-stu-id="fba4f-219">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="fba4f-220">如果您的程式不會傳回結束代碼，您可以宣告傳回 <xref:System.Threading.Tasks.Task> 的 `Main` 方法：</span><span class="sxs-lookup"><span data-stu-id="fba4f-220">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="fba4f-221">您可以在程式設計指南的[非同步主要](../programming-guide/main-and-command-args/index.md)文章中閱讀更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="fba4f-221">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) article in the programming guide.</span></span>

## <a name="local-functions"></a><span data-ttu-id="fba4f-222">區域函式</span><span class="sxs-lookup"><span data-stu-id="fba4f-222">Local functions</span></span>

<span data-ttu-id="fba4f-223">類別的許多設計都包括從唯一一個位置呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="fba4f-223">Many designs for classes include methods that are called from only one location.</span></span> <span data-ttu-id="fba4f-224">這些額外的私用方法會使每一種方法維持小而聚焦。</span><span class="sxs-lookup"><span data-stu-id="fba4f-224">These additional private methods keep each method small and focused.</span></span> <span data-ttu-id="fba4f-225">「區域函式」可讓您在另一個方法的內容中宣告方法。</span><span class="sxs-lookup"><span data-stu-id="fba4f-225">*Local functions* enable you to declare methods inside the context of another method.</span></span> <span data-ttu-id="fba4f-226">區域函式可讓類別讀者輕鬆查看區域方法只會從其宣告的內容中呼叫。</span><span class="sxs-lookup"><span data-stu-id="fba4f-226">Local functions make it easier for readers of the class to see that the local method is only called from the context in which it is declared.</span></span>

<span data-ttu-id="fba4f-227">有兩個常見的區域函式使用案例︰公用迭代器方法和公用非同步方法。</span><span class="sxs-lookup"><span data-stu-id="fba4f-227">There are two common use cases for local functions: public iterator methods and public async methods.</span></span> <span data-ttu-id="fba4f-228">這兩種方法都會產生程式碼，比程式設計人員想像更晚才報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="fba4f-228">Both types of methods generate code that reports errors later than programmers might expect.</span></span> <span data-ttu-id="fba4f-229">在迭代器方法中，任何例外狀況只會在呼叫列舉傳回序列的程式碼時觀察到。</span><span class="sxs-lookup"><span data-stu-id="fba4f-229">In iterator methods, any exceptions are observed only when calling code that enumerates the returned sequence.</span></span> <span data-ttu-id="fba4f-230">在非同步方法中，任何例外狀況只會在傳回的 `Task` 等候時觀察到。</span><span class="sxs-lookup"><span data-stu-id="fba4f-230">In async methods, any exceptions are only observed when the returned `Task` is awaited.</span></span> <span data-ttu-id="fba4f-231">下列範例示範使用區域函式分隔參數驗證和迭代器實作：</span><span class="sxs-lookup"><span data-stu-id="fba4f-231">The following example demonstrates separating parameter validation from the iterator implementation using a local function:</span></span>

[!code-csharp[22_IteratorMethodLocal](~/samples/snippets/csharp/new-in-7/Iterator.cs#IteratorMethodLocal "Iterator method with local function")]

<span data-ttu-id="fba4f-232">相同的技巧也可以運用在 `async` 方法，以確保在非同步工作開始之前，會擲回引數驗證所引發的例外狀況︰</span><span class="sxs-lookup"><span data-stu-id="fba4f-232">The same technique can be employed with `async` methods to ensure that exceptions arising from argument validation are thrown before the asynchronous work begins:</span></span>

[!code-csharp[TaskExample](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

<span data-ttu-id="fba4f-233">現在支援此語法：</span><span class="sxs-lookup"><span data-stu-id="fba4f-233">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="fba4f-234">屬性 `SomeThingAboutFieldAttribute` 套用至編譯器針對 `SomeProperty` 產生的支援欄位。</span><span class="sxs-lookup"><span data-stu-id="fba4f-234">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="fba4f-235">如需詳細資訊，請參閱 C# 程式設計指南中的[屬性](../programming-guide/concepts/attributes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="fba4f-235">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

> [!NOTE]
> <span data-ttu-id="fba4f-236">某些區域函數所支援的設計也可以使用 *lambda 運算式* 來完成。</span><span class="sxs-lookup"><span data-stu-id="fba4f-236">Some of the designs that are supported by local functions can also be accomplished using *lambda expressions*.</span></span> <span data-ttu-id="fba4f-237">如需詳細資訊，請參閱 [區域函數與 lambda 運算式](../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions)。</span><span class="sxs-lookup"><span data-stu-id="fba4f-237">For more information, see [Local functions vs. lambda expressions](../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions).</span></span>

## <a name="more-expression-bodied-members"></a><span data-ttu-id="fba4f-238">更多運算式主體成員</span><span class="sxs-lookup"><span data-stu-id="fba4f-238">More expression-bodied members</span></span>

<span data-ttu-id="fba4f-239">C # 6 引進了成員函式和唯讀屬性的運算式主體成員。</span><span class="sxs-lookup"><span data-stu-id="fba4f-239">C# 6 introduced expression-bodied members for member functions and read-only properties.</span></span> <span data-ttu-id="fba4f-240">C# 7.0 擴充了可以實作為運算式的允許成員。</span><span class="sxs-lookup"><span data-stu-id="fba4f-240">C# 7.0 expands the allowed members that can be implemented as expressions.</span></span> <span data-ttu-id="fba4f-241">在 C# 7.0 中，您可以實作「建構函式」、「完成項」，以及「屬性」和「索引子」上的 `get` 和 `set` 存取子。</span><span class="sxs-lookup"><span data-stu-id="fba4f-241">In C# 7.0, you can implement *constructors*, *finalizers*, and `get` and `set` accessors on *properties* and *indexers*.</span></span> <span data-ttu-id="fba4f-242">下列程式碼將示範各項的範例：</span><span class="sxs-lookup"><span data-stu-id="fba4f-242">The following code shows examples of each:</span></span>

[!code-csharp[ExpressionBodiedMembers](~/samples/snippets/csharp/new-in-7/expressionmembers.cs#ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> <span data-ttu-id="fba4f-243">這個範例不需要完成項，但仍加以顯示以示範語法。</span><span class="sxs-lookup"><span data-stu-id="fba4f-243">This example does not need a finalizer, but it is shown to demonstrate the syntax.</span></span> <span data-ttu-id="fba4f-244">除非為釋放 Unmanaged 資源所需，否則不應該在類別中實作完成項。</span><span class="sxs-lookup"><span data-stu-id="fba4f-244">You should not implement a finalizer in your class unless it is necessary to  release unmanaged resources.</span></span> <span data-ttu-id="fba4f-245">您也應該考慮使用 <xref:System.Runtime.InteropServices.SafeHandle> 類別而不是直接管理 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="fba4f-245">You should also consider using the <xref:System.Runtime.InteropServices.SafeHandle> class instead of managing unmanaged resources directly.</span></span>

<span data-ttu-id="fba4f-246">這些運算式主體成員的新位置代表 C# 語言的重要里程碑︰這些功能是由參與開放原始碼 [Roslyn](https://github.com/dotnet/Roslyn) 專案的社群成員所實作。</span><span class="sxs-lookup"><span data-stu-id="fba4f-246">These new locations for expression-bodied members represent an important milestone for the C# language: These features were implemented by community members working on the open-source [Roslyn](https://github.com/dotnet/Roslyn) project.</span></span>

<span data-ttu-id="fba4f-247">將方法變更為運算式主體成員是[二進位相容](version-update-considerations.md#binary-compatible-changes)變更。</span><span class="sxs-lookup"><span data-stu-id="fba4f-247">Changing a method to an expression bodied member is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="throw-expressions"></a><span data-ttu-id="fba4f-248">throw 運算式</span><span class="sxs-lookup"><span data-stu-id="fba4f-248">Throw expressions</span></span>

<span data-ttu-id="fba4f-249">在 C# 中，`throw` 一直都是陳述式。</span><span class="sxs-lookup"><span data-stu-id="fba4f-249">In C#, `throw` has always been a statement.</span></span> <span data-ttu-id="fba4f-250">因為 `throw` 是陳述式，而不是運算式，所以有您無法在其中使用它的 C# 建構。</span><span class="sxs-lookup"><span data-stu-id="fba4f-250">Because `throw` is a statement, not an expression, there were C# constructs where you couldn't use it.</span></span> <span data-ttu-id="fba4f-251">這些包含條件運算式、Null 聯合運算式和一些 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="fba4f-251">These included conditional expressions, null coalescing expressions, and some lambda expressions.</span></span> <span data-ttu-id="fba4f-252">新增運算式主體成員會新增 `throw` 運算式適用的更多位置。</span><span class="sxs-lookup"><span data-stu-id="fba4f-252">The addition of expression-bodied members adds more locations where `throw` expressions would be useful.</span></span> <span data-ttu-id="fba4f-253">您可以撰寫任何這些結構，c # 7.0 引進了 [*擲回運算式*](../language-reference/keywords/throw.md#the-throw-expression)。</span><span class="sxs-lookup"><span data-stu-id="fba4f-253">So that you can write any of these constructs, C# 7.0 introduces [*throw expressions*](../language-reference/keywords/throw.md#the-throw-expression).</span></span>

<span data-ttu-id="fba4f-254">此新增可讓您更輕鬆地撰寫更多以運算式為基礎的程式碼。</span><span class="sxs-lookup"><span data-stu-id="fba4f-254">This addition makes it easier to write more expression-based code.</span></span> <span data-ttu-id="fba4f-255">您不需要額外的陳述式就可以進行錯誤檢查。</span><span class="sxs-lookup"><span data-stu-id="fba4f-255">You don't need additional statements for error checking.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="fba4f-256">預設常值運算式</span><span class="sxs-lookup"><span data-stu-id="fba4f-256">Default literal expressions</span></span>

<span data-ttu-id="fba4f-257">預設常值運算式是預設值運算式的增強功能。</span><span class="sxs-lookup"><span data-stu-id="fba4f-257">Default literal expressions are an enhancement to default value expressions.</span></span> <span data-ttu-id="fba4f-258">這些運算式會將變數初始化為預設值。</span><span class="sxs-lookup"><span data-stu-id="fba4f-258">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="fba4f-259">在過去您必須這樣寫：</span><span class="sxs-lookup"><span data-stu-id="fba4f-259">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="fba4f-260">您現在可以略過初始化右側的類型：</span><span class="sxs-lookup"><span data-stu-id="fba4f-260">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="fba4f-261">如需詳細資訊，請參閱[預設運算子](../language-reference/operators/default.md)一文中的[預設常值](../language-reference/operators/default.md#default-literal)一節。</span><span class="sxs-lookup"><span data-stu-id="fba4f-261">For more information, see the [default literal](../language-reference/operators/default.md#default-literal) section of the [default operator](../language-reference/operators/default.md) article.</span></span>

## <a name="numeric-literal-syntax-improvements"></a><span data-ttu-id="fba4f-262">數值常值的語法增強功能</span><span class="sxs-lookup"><span data-stu-id="fba4f-262">Numeric literal syntax improvements</span></span>

<span data-ttu-id="fba4f-263">錯譯數值常數，可能會使得在第一次閱讀它時，更加難以了解程式碼。</span><span class="sxs-lookup"><span data-stu-id="fba4f-263">Misreading numeric constants can make it harder to understand code when reading it for the first time.</span></span> <span data-ttu-id="fba4f-264">位元遮罩或其他符號值容易遭到誤解。</span><span class="sxs-lookup"><span data-stu-id="fba4f-264">Bit masks or other symbolic values are prone to misunderstanding.</span></span> <span data-ttu-id="fba4f-265">C# 7.0 包含兩項新功能，可以用預期用途最容易閱讀的方式來撰寫數字︰「二進位常值」和「數字分隔符號」。</span><span class="sxs-lookup"><span data-stu-id="fba4f-265">C# 7.0 includes two new features to write numbers in the most readable fashion for the intended use: *binary literals*, and *digit separators*.</span></span>

<span data-ttu-id="fba4f-266">當您在建立位元遮罩時，或是每當數字的二進位表示法構成最容易閱讀的程式碼時，請以二進位撰寫該數字︰</span><span class="sxs-lookup"><span data-stu-id="fba4f-266">For those times when you're creating bit masks, or whenever a binary representation of a number makes the most readable code, write that number in binary:</span></span>

[!code-csharp[ThousandSeparators](~/samples/snippets/csharp/new-in-7/Program.cs#ThousandSeparators "Thousands separators")]

<span data-ttu-id="fba4f-267">常數開頭的 `0b` 表示數字是撰寫為二進位數字。</span><span class="sxs-lookup"><span data-stu-id="fba4f-267">The `0b` at the beginning of the constant indicates that the number is written as a binary number.</span></span> <span data-ttu-id="fba4f-268">二進位數可能會很長，因此藉由將作為數位分隔符號來查看位模式通常會更容易 `_` ，如上述範例中的二進位常數所示。</span><span class="sxs-lookup"><span data-stu-id="fba4f-268">Binary numbers can get long, so it's often easier to see the bit patterns by introducing the `_` as a digit separator, as shown in the binary constant in the preceding example.</span></span> <span data-ttu-id="fba4f-269">千位分隔符號可以出現在常數的任何位置。</span><span class="sxs-lookup"><span data-stu-id="fba4f-269">The digit separator can appear anywhere in the constant.</span></span> <span data-ttu-id="fba4f-270">若是以10為底數的數位，通常會使用它作為千位分隔符號。</span><span class="sxs-lookup"><span data-stu-id="fba4f-270">For base 10 numbers, it is common to use it as a thousands separator.</span></span> <span data-ttu-id="fba4f-271">十六進位和二進位數值常值的開頭可能是 `_` ：</span><span class="sxs-lookup"><span data-stu-id="fba4f-271">Hex and binary numeric literals may begin with an `_`:</span></span>

[!code-csharp[LargeIntegers](~/samples/snippets/csharp/new-in-7/Program.cs#LargeIntegers "Large integer")]

<span data-ttu-id="fba4f-272">千位分隔符號也可以搭配 `decimal`、`float` 和 `double` 類型使用︰</span><span class="sxs-lookup"><span data-stu-id="fba4f-272">The digit separator can be used with `decimal`, `float`, and `double` types as well:</span></span>

[!code-csharp[OtherConstants](~/samples/snippets/csharp/new-in-7/Program.cs#OtherConstants "non-integral constants")]

<span data-ttu-id="fba4f-273">結合起來，您在宣告數值常數時可以有更多的可讀性。</span><span class="sxs-lookup"><span data-stu-id="fba4f-273">Taken together, you can declare numeric constants with much more readability.</span></span>

## <a name="out-variables"></a><span data-ttu-id="fba4f-274">`out` 變數</span><span class="sxs-lookup"><span data-stu-id="fba4f-274">`out` variables</span></span>

<span data-ttu-id="fba4f-275">`out`在 c # 7 中已改善支援參數的現有語法。</span><span class="sxs-lookup"><span data-stu-id="fba4f-275">The existing syntax that supports `out` parameters has been improved in C# 7.</span></span> <span data-ttu-id="fba4f-276">您現在可以在方法呼叫的引數清單中宣告 `out` 變數，而不是撰寫個別的宣告陳述式︰</span><span class="sxs-lookup"><span data-stu-id="fba4f-276">You can now declare `out` variables in the argument list of a method call, rather than writing a separate declaration statement:</span></span>

[!code-csharp[OutVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVariableDeclarations "Out variable declarations")]

<span data-ttu-id="fba4f-277">您可能會想要明確指定變數的類型 `out` ，如上述範例所示。</span><span class="sxs-lookup"><span data-stu-id="fba4f-277">You may want to specify the type of the `out` variable for clarity, as shown in the preceding example.</span></span> <span data-ttu-id="fba4f-278">不過，語言有支援使用隱含型別區域變數︰</span><span class="sxs-lookup"><span data-stu-id="fba4f-278">However, the language does support using an implicitly typed local variable:</span></span>

[!code-csharp[OutVarVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVarVariableDeclarations "Implicitly typed Out variable")]

- <span data-ttu-id="fba4f-279">程式碼更容易閱讀與理解。</span><span class="sxs-lookup"><span data-stu-id="fba4f-279">The code is easier to read.</span></span>
  - <span data-ttu-id="fba4f-280">您可以在使用時宣告 out 變數，而不是在先前的程式程式碼上。</span><span class="sxs-lookup"><span data-stu-id="fba4f-280">You declare the out variable where you use it, not on a preceding line of code.</span></span>
- <span data-ttu-id="fba4f-281">不需要指派初始值。</span><span class="sxs-lookup"><span data-stu-id="fba4f-281">No need to assign an initial value.</span></span>
  - <span data-ttu-id="fba4f-282">藉由在方法呼叫中使用所在宣告 `out` 變數，就不會在指派它之前意外使用它。</span><span class="sxs-lookup"><span data-stu-id="fba4f-282">By declaring the `out` variable where it's used in a method call, you can't accidentally use it before it is assigned.</span></span>

<span data-ttu-id="fba4f-283">加入 C# 7.0 中以允許 `out` 變數宣告的語法已經擴充，以包含欄位初始設定式、屬性初始設定式、建構函式初始設定式和查詢子句。</span><span class="sxs-lookup"><span data-stu-id="fba4f-283">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="fba4f-284">它讓您能執行如下列範例的程式碼：</span><span class="sxs-lookup"><span data-stu-id="fba4f-284">It enables code such as the following example:</span></span>

```csharp
public class B
{
   public B(int i, out int j)
   {
      j = i;
   }
}

public class D : B
{
   public D(int i) : base(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

## <a name="non-trailing-named-arguments"></a><span data-ttu-id="fba4f-285">非後置具名引數</span><span class="sxs-lookup"><span data-stu-id="fba4f-285">Non-trailing named arguments</span></span>

<span data-ttu-id="fba4f-286">當具名引數位於正確位置時，方法呼叫現在可以在位置引數前面使用具名引數。</span><span class="sxs-lookup"><span data-stu-id="fba4f-286">Method calls may now use named arguments that precede positional arguments when those named arguments are in the correct positions.</span></span> <span data-ttu-id="fba4f-287">如需詳細資訊，請參閱 [指名的和選擇性引數](../programming-guide/classes-and-structs/named-and-optional-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="fba4f-287">For more information, see [Named and optional arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span></span>

## <a name="private-protected-access-modifier"></a><span data-ttu-id="fba4f-288">*private protected* 存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="fba4f-288">*private protected* access modifier</span></span>

<span data-ttu-id="fba4f-289">新的複合存取修飾詞：`private protected` 指出可藉由包含類別或在相同組件中宣告的衍生類別來存取成員。</span><span class="sxs-lookup"><span data-stu-id="fba4f-289">A new compound access modifier: `private protected` indicates that a member may be accessed by containing class or derived classes that are declared in the same assembly.</span></span> <span data-ttu-id="fba4f-290">`protected internal` 允許衍生類別或相同組件中的類別進行存取，而 `private protected` 則限制在相同組件中宣告的衍生類型進行存取。</span><span class="sxs-lookup"><span data-stu-id="fba4f-290">While `protected internal` allows access by derived classes or classes that are in the same assembly, `private protected` limits access to derived types declared in the same assembly.</span></span>

<span data-ttu-id="fba4f-291">如需詳細資訊，請參閱語言參考中的 [存取](../language-reference/keywords/access-modifiers.md) 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="fba4f-291">For more information, see [access modifiers](../language-reference/keywords/access-modifiers.md) in the language reference.</span></span>

## <a name="improved-overload-candidates"></a><span data-ttu-id="fba4f-292">改進的多載候選項目</span><span class="sxs-lookup"><span data-stu-id="fba4f-292">Improved overload candidates</span></span>

<span data-ttu-id="fba4f-293">在每個版本中，多載解析規則都會更新，以解決模稜兩可的方法引動過程具有「明確」選項的情況。</span><span class="sxs-lookup"><span data-stu-id="fba4f-293">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="fba4f-294">此版本新增三個新的規則，以協助編譯器挑選明確的選項：</span><span class="sxs-lookup"><span data-stu-id="fba4f-294">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="fba4f-295">當方法群組同時包含執行個體和靜態成員時，如果在沒有執行個體接收者或內容的情況下叫用方法，編譯器會捨棄執行個體成員。</span><span class="sxs-lookup"><span data-stu-id="fba4f-295">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="fba4f-296">如果使用執行個體接收者叫用方法，編譯器就會捨棄靜態成員。</span><span class="sxs-lookup"><span data-stu-id="fba4f-296">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="fba4f-297">沒有接收者時，編譯器只會在靜態內容中包含靜態成員，否則將同時包含靜態成員和執行個體成員。</span><span class="sxs-lookup"><span data-stu-id="fba4f-297">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="fba4f-298">當無法確定接收者是執行個體或型別時，編譯器會包含兩者。</span><span class="sxs-lookup"><span data-stu-id="fba4f-298">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="fba4f-299">無法使用隱含 `this` 執行個體接收者的靜態內容，包括未定義 `this` 的成員主體 (例如靜態成員)，以及不能使用 `this` 的位置 (例如欄位初始設定式和建構函式初始設定式)。</span><span class="sxs-lookup"><span data-stu-id="fba4f-299">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="fba4f-300">當方法群組包含某些型別引數不滿足其限制式的泛型方法時，這些成員將會從候選集合中移除。</span><span class="sxs-lookup"><span data-stu-id="fba4f-300">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="fba4f-301">針對方法群組轉換，其傳回型別與委派的傳回型別不符合的候選方法，將會從集合中移除。</span><span class="sxs-lookup"><span data-stu-id="fba4f-301">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="fba4f-302">您只會注意到此變更，因為若確定何種方法較佳，就會發現模稜兩可的方法多載會有較少的編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="fba4f-302">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="enabling-more-efficient-safe-code"></a><span data-ttu-id="fba4f-303">啟用更有效率的安全的程式碼</span><span class="sxs-lookup"><span data-stu-id="fba4f-303">Enabling more efficient safe code</span></span>

<span data-ttu-id="fba4f-304">您應該能夠安全地撰寫與不安全的程式碼一樣高效能的 C# 程式碼。</span><span class="sxs-lookup"><span data-stu-id="fba4f-304">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="fba4f-305">安全的程式碼可避免一些錯誤類別，例如緩衝區溢位、偏離的指標和其他記憶體存取錯誤。</span><span class="sxs-lookup"><span data-stu-id="fba4f-305">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="fba4f-306">這些新功能擴充了可驗證安全的程式碼的功能。</span><span class="sxs-lookup"><span data-stu-id="fba4f-306">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="fba4f-307">儘可能使用安全的建構來撰寫更多的程式碼。</span><span class="sxs-lookup"><span data-stu-id="fba4f-307">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="fba4f-308">這些功能都讓這變得更容易。</span><span class="sxs-lookup"><span data-stu-id="fba4f-308">These features make that easier.</span></span>

<span data-ttu-id="fba4f-309">下列新功能針對安全的程式碼支援較佳效能的佈景主題：</span><span class="sxs-lookup"><span data-stu-id="fba4f-309">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="fba4f-310">您可以在不釘選的情況下存取固定的欄位。</span><span class="sxs-lookup"><span data-stu-id="fba4f-310">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="fba4f-311">您可以重新指派 `ref` 區域變數。</span><span class="sxs-lookup"><span data-stu-id="fba4f-311">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="fba4f-312">您可以在 `stackalloc` 陣列上使用初始設定式。</span><span class="sxs-lookup"><span data-stu-id="fba4f-312">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="fba4f-313">您可以搭配支援模式的任何型別使用 `fixed` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="fba4f-313">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="fba4f-314">您可以使用其他的泛型限制式。</span><span class="sxs-lookup"><span data-stu-id="fba4f-314">You can use additional generic constraints.</span></span>
- <span data-ttu-id="fba4f-315">參數上的 `in` 修飾詞，可指定引數將以傳址方式傳遞，但不受呼叫的方法修改。</span><span class="sxs-lookup"><span data-stu-id="fba4f-315">The `in` modifier on parameters, to specify that an argument is passed by reference but not modified by the called method.</span></span> <span data-ttu-id="fba4f-316">將 `in` 修飾詞新增至引數是[來源相容變更](version-update-considerations.md#source-compatible-changes)。</span><span class="sxs-lookup"><span data-stu-id="fba4f-316">Adding the `in` modifier to an argument is a [source compatible change](version-update-considerations.md#source-compatible-changes).</span></span>
- <span data-ttu-id="fba4f-317">方法上 `ref readonly` 修飾詞的傳回內容，可指示方法要以傳址方式傳回其值，但不允許寫入該物件。</span><span class="sxs-lookup"><span data-stu-id="fba4f-317">The `ref readonly` modifier on method returns, to indicate that a method returns its value by reference but doesn't allow writes to that object.</span></span> <span data-ttu-id="fba4f-318">如果將傳回項目指派給值。則新增 `ref readonly` 修飾詞是[來源相容變更](version-update-considerations.md#source-compatible-changes)。</span><span class="sxs-lookup"><span data-stu-id="fba4f-318">Adding the `ref readonly` modifier is a [source compatible change](version-update-considerations.md#source-compatible-changes), if the return is assigned to a value.</span></span> <span data-ttu-id="fba4f-319">將 `readonly` 修飾詞新增至現有 `ref` 傳回陳述式是[不相容的變更](version-update-considerations.md#incompatible-changes)。</span><span class="sxs-lookup"><span data-stu-id="fba4f-319">Adding the `readonly` modifier to an existing `ref` return statement is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="fba4f-320">需要呼叫端更新 `ref` 本機變數的宣告，以包含 `readonly` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="fba4f-320">It requires callers to update the declaration of `ref` local variables to include the `readonly` modifier.</span></span>
- <span data-ttu-id="fba4f-321">`readonly struct` 宣告，可指示結構會固定，且應以 `in` 參數傳遞至其成員方法。</span><span class="sxs-lookup"><span data-stu-id="fba4f-321">The `readonly struct` declaration, to indicate that a struct is immutable and should be passed as an `in` parameter to its member methods.</span></span> <span data-ttu-id="fba4f-322">將 `readonly` 修飾詞新增至現有 struct 宣告是[二進位相容變更](version-update-considerations.md#binary-compatible-changes)。</span><span class="sxs-lookup"><span data-stu-id="fba4f-322">Adding the `readonly` modifier to an existing struct declaration is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>
- <span data-ttu-id="fba4f-323">`ref struct` 宣告，可指示結構類型會直接存取受控記憶體，且一律會配置堆疊。</span><span class="sxs-lookup"><span data-stu-id="fba4f-323">The `ref struct` declaration, to indicate that a struct type accesses managed memory directly and must always be stack allocated.</span></span> <span data-ttu-id="fba4f-324">將 `ref` 修飾詞新增至現有 `struct` 宣告是[不相容的變更](version-update-considerations.md#incompatible-changes)。</span><span class="sxs-lookup"><span data-stu-id="fba4f-324">Adding the `ref` modifier to an existing `struct` declaration is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="fba4f-325">`ref struct` 不能是類別的成員，或用於可能會在堆積上配置的其他位置。</span><span class="sxs-lookup"><span data-stu-id="fba4f-325">A `ref struct` cannot be a member of a class or used in other locations where it may be allocated on the heap.</span></span>

<span data-ttu-id="fba4f-326">您可以在[撰寫安全、有效率的程式碼](../write-safe-efficient-code.md)深入了解這些變更。</span><span class="sxs-lookup"><span data-stu-id="fba4f-326">You can read more about all these changes in [Write safe efficient code](../write-safe-efficient-code.md).</span></span>

### <a name="ref-locals-and-returns"></a><span data-ttu-id="fba4f-327">Ref 區域變數和傳回</span><span class="sxs-lookup"><span data-stu-id="fba4f-327">Ref locals and returns</span></span>

<span data-ttu-id="fba4f-328">這項功能可以啟用使用和傳回在其他地方定義之變數參考的演算法。</span><span class="sxs-lookup"><span data-stu-id="fba4f-328">This feature enables algorithms that use and return references to variables defined elsewhere.</span></span> <span data-ttu-id="fba4f-329">其中一個範例是使用大型矩陣，並尋找具有特定特性的單一位置。</span><span class="sxs-lookup"><span data-stu-id="fba4f-329">One example is working with large matrices, and finding a single location with certain characteristics.</span></span> <span data-ttu-id="fba4f-330">下列方法會傳回矩陣中該儲存體的 **參考**：</span><span class="sxs-lookup"><span data-stu-id="fba4f-330">The following method returns a **reference** to that storage in the matrix:</span></span>

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

<span data-ttu-id="fba4f-331">您可以將傳回值宣告為 `ref`，並在矩陣中修改該值，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="fba4f-331">You can declare the return value as a `ref` and modify that value in the matrix, as shown in the following code:</span></span>

[!code-csharp[AssignRefReturn](~/samples/snippets/csharp/new-in-7/Program.cs#AssignRefReturn "Assign ref return")]

<span data-ttu-id="fba4f-332">C# 語言具備數個規則，可防止您濫用 `ref` 區域變數並傳回︰</span><span class="sxs-lookup"><span data-stu-id="fba4f-332">The C# language has several rules that protect you from misusing the `ref` locals and returns:</span></span>

- <span data-ttu-id="fba4f-333">您必須將 `ref` 關鍵字加入至方法特徵標記，以及某個方法中的所有 `return` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="fba4f-333">You must add the `ref` keyword to the method signature and to all `return` statements in a method.</span></span>
  - <span data-ttu-id="fba4f-334">如此可透過整個方法的參考，清除方法傳回。</span><span class="sxs-lookup"><span data-stu-id="fba4f-334">That makes it clear the method returns by reference throughout the method.</span></span>
- <span data-ttu-id="fba4f-335">`ref return` 可能會指派給值變數，或 `ref` 變數。</span><span class="sxs-lookup"><span data-stu-id="fba4f-335">A `ref return` may be assigned to a value variable, or a `ref` variable.</span></span>
  - <span data-ttu-id="fba4f-336">呼叫端會控制是否要複製傳回值。</span><span class="sxs-lookup"><span data-stu-id="fba4f-336">The caller controls whether the return value is copied or not.</span></span> <span data-ttu-id="fba4f-337">指派傳回值時省略 `ref` 修飾詞表示呼叫端需要值的複本，而不是儲存體的參考。</span><span class="sxs-lookup"><span data-stu-id="fba4f-337">Omitting the `ref` modifier when assigning the return value indicates that the caller wants a copy of the value, not a reference to the storage.</span></span>
- <span data-ttu-id="fba4f-338">您無法將標準方法傳回值指派到 `ref` 區域變數。</span><span class="sxs-lookup"><span data-stu-id="fba4f-338">You can't assign a standard method return value to a `ref` local variable.</span></span>
  - <span data-ttu-id="fba4f-339">這可杜絕類似 `ref int i = sequence.Count();` 的陳述式</span><span class="sxs-lookup"><span data-stu-id="fba4f-339">That disallows statements like `ref int i = sequence.Count();`</span></span>
- <span data-ttu-id="fba4f-340">您無法將 `ref` 傳回給其存留期不超過方法執行的變數。</span><span class="sxs-lookup"><span data-stu-id="fba4f-340">You can't return a `ref` to a variable whose lifetime doesn't extend beyond the execution of the method.</span></span>
  - <span data-ttu-id="fba4f-341">這表示您無法將參考傳回區域變數或具有類似範圍的變數。</span><span class="sxs-lookup"><span data-stu-id="fba4f-341">That means you can't return a reference to a local variable or a variable with a similar scope.</span></span>
- <span data-ttu-id="fba4f-342">`ref` 區域變數及傳回值無法配合非同步方法使用。</span><span class="sxs-lookup"><span data-stu-id="fba4f-342">`ref` locals and returns can't be used with async methods.</span></span>
  - <span data-ttu-id="fba4f-343">當非同步方法傳回時，編譯器無法確定參考的變數是否已設定為其最終的值。</span><span class="sxs-lookup"><span data-stu-id="fba4f-343">The compiler can't know if the referenced variable has been set to its final value when the async method returns.</span></span>

<span data-ttu-id="fba4f-344">新增 ref 區域變數和 ref 傳回能啟用更有效率的演算法，因為可以避免複製值，或是多次執行取值作業。</span><span class="sxs-lookup"><span data-stu-id="fba4f-344">The addition of ref locals and ref returns enables algorithms that are more efficient by avoiding copying values, or performing dereferencing operations multiple times.</span></span>

<span data-ttu-id="fba4f-345">將 `ref` 新增至傳回值是[來源相容變更](version-update-considerations.md#source-compatible-changes)。</span><span class="sxs-lookup"><span data-stu-id="fba4f-345">Adding `ref` to the return value is a [source compatible change](version-update-considerations.md#source-compatible-changes).</span></span> <span data-ttu-id="fba4f-346">現有程式碼會編譯，但是 ref 傳回值是在指派時複製。</span><span class="sxs-lookup"><span data-stu-id="fba4f-346">Existing code compiles, but the ref return value is copied when assigned.</span></span> <span data-ttu-id="fba4f-347">呼叫端必須將傳回值的儲存體更新為 `ref` 區域變數，將傳回項目儲存為參考。</span><span class="sxs-lookup"><span data-stu-id="fba4f-347">Callers must update the storage for the return value to a `ref` local variable to store the return as a reference.</span></span>

<span data-ttu-id="fba4f-348">現在，`ref` 區域變數可能會在初始化之後被重新指派，以參照不同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="fba4f-348">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="fba4f-349">下列程式碼現在會編譯：</span><span class="sxs-lookup"><span data-stu-id="fba4f-349">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="fba4f-350">如需詳細資訊，請參閱有關傳回的[ `ref` 和 `ref` 區域變數](../programming-guide/classes-and-structs/ref-returns.md)的文章，以及的相關文章 [`foreach`](../language-reference/keywords/foreach-in.md) 。</span><span class="sxs-lookup"><span data-stu-id="fba4f-350">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md), and the article on [`foreach`](../language-reference/keywords/foreach-in.md).</span></span>

<span data-ttu-id="fba4f-351">如需詳細資訊，請參閱 [ref 關鍵字](../language-reference/keywords/ref.md)一文。</span><span class="sxs-lookup"><span data-stu-id="fba4f-351">For more information, see the [ref keyword](../language-reference/keywords/ref.md) article.</span></span>

### <a name="conditional-ref-expressions"></a><span data-ttu-id="fba4f-352">`ref` 條件運算式</span><span class="sxs-lookup"><span data-stu-id="fba4f-352">Conditional `ref` expressions</span></span>

<span data-ttu-id="fba4f-353">最後，條件運算式可能會產生參考結果，而不是實值結果。</span><span class="sxs-lookup"><span data-stu-id="fba4f-353">Finally, the conditional expression may produce a ref result instead of a value result.</span></span> <span data-ttu-id="fba4f-354">例如，您可以撰寫下列程式碼，在兩個陣列的其中一個上，擷取對第一個元素的參考：</span><span class="sxs-lookup"><span data-stu-id="fba4f-354">For example, you would write the following to retrieve a reference to the first element in one of two arrays:</span></span>

```csharp
ref var r = ref (arr != null ? ref arr[0] : ref otherArr[0]);
```

<span data-ttu-id="fba4f-355">變數 `r` 是 `arr` 或 `otherArr` 中對第一個值的參考。</span><span class="sxs-lookup"><span data-stu-id="fba4f-355">The variable `r` is a reference to the first value in either `arr` or `otherArr`.</span></span>

<span data-ttu-id="fba4f-356">如需詳細資訊，請參閱語言參考中的[條件運算子 (?:)](../language-reference/operators/conditional-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="fba4f-356">For more information, see [conditional operator (?:)](../language-reference/operators/conditional-operator.md) in the language reference.</span></span>

### <a name="in-parameter-modifier"></a><span data-ttu-id="fba4f-357">`in` 參數修飾詞</span><span class="sxs-lookup"><span data-stu-id="fba4f-357">`in` parameter modifier</span></span>

<span data-ttu-id="fba4f-358">`in`關鍵字會補充現有的 ref 和 out 關鍵字，以傳址方式傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="fba4f-358">The `in` keyword complements the existing ref and out keywords to pass arguments by reference.</span></span> <span data-ttu-id="fba4f-359">`in` 關鍵字會指定以參考型式傳遞引數，但呼叫的方法不會修改值。</span><span class="sxs-lookup"><span data-stu-id="fba4f-359">The `in` keyword specifies passing the argument by reference, but the called method doesn't modify the value.</span></span>

<span data-ttu-id="fba4f-360">您可以宣告以傳值方式或唯讀參考傳遞的多載，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="fba4f-360">You may declare overloads that pass by value or by readonly reference, as shown in the following code:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="fba4f-361">前一個範例中的 by 值 (先) 多載比唯讀參考版本更好。</span><span class="sxs-lookup"><span data-stu-id="fba4f-361">The by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="fba4f-362">若要呼叫具有唯讀參考引數的版本，您呼叫方法時必須包含 `in` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="fba4f-362">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

<span data-ttu-id="fba4f-363">如需詳細資訊，請參閱[ `in` 參數修飾](../language-reference/keywords/in-parameter-modifier.md)詞上的文章。</span><span class="sxs-lookup"><span data-stu-id="fba4f-363">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="fba4f-364">更多型別支援 `fixed` 陳述式</span><span class="sxs-lookup"><span data-stu-id="fba4f-364">More types support the `fixed` statement</span></span>

<span data-ttu-id="fba4f-365">`fixed` 陳述式支援一組有限的型別。</span><span class="sxs-lookup"><span data-stu-id="fba4f-365">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="fba4f-366">從 C# 7.3 開始，包含傳回 `ref T` 或 `ref readonly T` 之 `GetPinnableReference()` 方法的任何型別都可能是 `fixed`。</span><span class="sxs-lookup"><span data-stu-id="fba4f-366">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="fba4f-367">新增此功能表示 `fixed` 可以與 <xref:System.Span%601?displayProperty=nameWithType> 和相關型別一起使用。</span><span class="sxs-lookup"><span data-stu-id="fba4f-367">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="fba4f-368">如需詳細資訊，請參閱語言參考中的[ `fixed` 語句](../language-reference/keywords/fixed-statement.md)文章。</span><span class="sxs-lookup"><span data-stu-id="fba4f-368">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="fba4f-369">索引 `fixed` 欄位不需要釘選</span><span class="sxs-lookup"><span data-stu-id="fba4f-369">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="fba4f-370">請考量此建構：</span><span class="sxs-lookup"><span data-stu-id="fba4f-370">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="fba4f-371">在舊版的 C# 中，您需要釘選變數，才能存取屬於 `myFixedField` 的其中一個整數。</span><span class="sxs-lookup"><span data-stu-id="fba4f-371">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="fba4f-372">現在，下列程式碼會進行編譯而不將變數 `p` 固定在個別的 `fixed` 陳述式內：</span><span class="sxs-lookup"><span data-stu-id="fba4f-372">Now, the following code compiles without pinning the variable `p` inside a separate `fixed` statement:</span></span>

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        int p = s.myFixedField[5];
    }
}
```

<span data-ttu-id="fba4f-373">變數 `p` 會存取 `myFixedField` 中的一個元素。</span><span class="sxs-lookup"><span data-stu-id="fba4f-373">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="fba4f-374">您不需要宣告個別的 `int*` 變數。</span><span class="sxs-lookup"><span data-stu-id="fba4f-374">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="fba4f-375">您仍然需要 `unsafe` 內容。</span><span class="sxs-lookup"><span data-stu-id="fba4f-375">You still need an `unsafe` context.</span></span> <span data-ttu-id="fba4f-376">在舊版的 C# 中，您需要宣告第二個固定指標：</span><span class="sxs-lookup"><span data-stu-id="fba4f-376">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        fixed (int* ptr = s.myFixedField)
        {
            int p = ptr[5];
        }
    }
}
```

<span data-ttu-id="fba4f-377">如需詳細資訊，請參閱有關[ `fixed` 語句](../language-reference/keywords/fixed-statement.md)的文章。</span><span class="sxs-lookup"><span data-stu-id="fba4f-377">For more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="fba4f-378">`stackalloc` 陣列支援初始設定式</span><span class="sxs-lookup"><span data-stu-id="fba4f-378">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="fba4f-379">您可以在初始化陣列時，指定陣列中元素的值：</span><span class="sxs-lookup"><span data-stu-id="fba4f-379">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="fba4f-380">現在，相同的語法可以套用至使用 `stackalloc` 宣告的陣列：</span><span class="sxs-lookup"><span data-stu-id="fba4f-380">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="fba4f-381">如需詳細資訊，請參閱[ `stackalloc` 操作員](../language-reference/operators/stackalloc.md)文章。</span><span class="sxs-lookup"><span data-stu-id="fba4f-381">For more information, see the [`stackalloc` operator](../language-reference/operators/stackalloc.md) article.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="fba4f-382">增強泛型限制式</span><span class="sxs-lookup"><span data-stu-id="fba4f-382">Enhanced generic constraints</span></span>

<span data-ttu-id="fba4f-383">您現在可以指定型別 <xref:System.Enum?displayProperty=nameWithType> 或 <xref:System.Delegate?displayProperty=nameWithType> 作為型別參數的基底類別限制式。</span><span class="sxs-lookup"><span data-stu-id="fba4f-383">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="fba4f-384">您也可以使用新的 `unmanaged` 條件約束，指定型別參數必須是不可為 null 的 [非受控型](../language-reference/builtin-types/unmanaged-types.md)別。</span><span class="sxs-lookup"><span data-stu-id="fba4f-384">You can also use the new `unmanaged` constraint, to specify that a type parameter must be a non-nullable [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span>

<span data-ttu-id="fba4f-385">如需詳細資訊，請參閱[ `where` 泛型條件約束](../language-reference/keywords/where-generic-type-constraint.md)的相關文章和[類型參數的條件約束](../programming-guide/generics/constraints-on-type-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="fba4f-385">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="fba4f-386">將這些條件約束新增至現有型別是[不相容變更](version-update-considerations.md#incompatible-changes)。</span><span class="sxs-lookup"><span data-stu-id="fba4f-386">Adding these constraints to existing types is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="fba4f-387">封閉式泛型型別可能不再符合這些新的條件約束。</span><span class="sxs-lookup"><span data-stu-id="fba4f-387">Closed generic types may no longer meet these new constraints.</span></span>

### <a name="generalized-async-return-types"></a><span data-ttu-id="fba4f-388">通用的非同步傳回型別</span><span class="sxs-lookup"><span data-stu-id="fba4f-388">Generalized async return types</span></span>

<span data-ttu-id="fba4f-389">從非同步方法傳回 `Task` 物件可能會造成在特定路徑的效能瓶頸。</span><span class="sxs-lookup"><span data-stu-id="fba4f-389">Returning a `Task` object from async methods can introduce performance bottlenecks in certain paths.</span></span> <span data-ttu-id="fba4f-390">`Task` 是參考型別，因此使用它表示要配置物件。</span><span class="sxs-lookup"><span data-stu-id="fba4f-390">`Task` is a reference type, so using it means allocating an object.</span></span> <span data-ttu-id="fba4f-391">當使用 `async` 修飾詞宣告的方法傳回快取的結果時，或是以同步方式完成，額外配置可能會在效能關鍵的程式碼區段中變成一項重要的時間成本。</span><span class="sxs-lookup"><span data-stu-id="fba4f-391">In cases where a method declared with the `async` modifier returns a cached result, or completes synchronously, the extra allocations can become a significant time cost in performance critical sections of code.</span></span> <span data-ttu-id="fba4f-392">如果這些配置發生在緊密迴圈中，它可能會變得成本很高。</span><span class="sxs-lookup"><span data-stu-id="fba4f-392">It can become costly if those allocations occur in tight loops.</span></span>

<span data-ttu-id="fba4f-393">新的語言功能表示 async 方法傳回型別不限於 `Task`、`Task<T>` 和 `void`。</span><span class="sxs-lookup"><span data-stu-id="fba4f-393">The new language feature means that async method return types aren't limited to `Task`, `Task<T>`, and `void`.</span></span> <span data-ttu-id="fba4f-394">傳回的型別仍然必須滿足非同步模式，也就是表示 `GetAwaiter` 方法必須可存取。</span><span class="sxs-lookup"><span data-stu-id="fba4f-394">The returned type must still satisfy the async pattern, meaning a `GetAwaiter` method must be accessible.</span></span> <span data-ttu-id="fba4f-395">作為一個具體的範例， `ValueTask` 類型已新增至 .net 以利用這個新的語言功能：</span><span class="sxs-lookup"><span data-stu-id="fba4f-395">As one concrete example, the `ValueTask` type has been added to .NET to make use of this new language feature:</span></span>

[!code-csharp[UsingValueTask](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#UsingValueTask "Using ValueTask")]

> [!NOTE]
> <span data-ttu-id="fba4f-396">您需要新增 NuGet 套件 >，才能 [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) 使用 <xref:System.Threading.Tasks.ValueTask%601> 類型。</span><span class="sxs-lookup"><span data-stu-id="fba4f-396">You need to add the NuGet package [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) > in order to use the <xref:System.Threading.Tasks.ValueTask%601> type.</span></span>

<span data-ttu-id="fba4f-397">這項增強功能最能幫助程式庫作者避免在效能關鍵的程式碼中配置 `Task`。</span><span class="sxs-lookup"><span data-stu-id="fba4f-397">This enhancement is most useful for library authors to avoid allocating a `Task` in performance critical code.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="fba4f-398">新的編譯器選項</span><span class="sxs-lookup"><span data-stu-id="fba4f-398">New compiler options</span></span>

<span data-ttu-id="fba4f-399">新的編譯器選項支援 C# 程式的新組建和 DevOps 案例。</span><span class="sxs-lookup"><span data-stu-id="fba4f-399">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="reference-assembly-generation"></a><span data-ttu-id="fba4f-400">參考組件產生</span><span class="sxs-lookup"><span data-stu-id="fba4f-400">Reference assembly generation</span></span>

<span data-ttu-id="fba4f-401">有兩個新編譯器選項會產生「僅參考的組件」：[-refout](../language-reference/compiler-options/refout-compiler-option.md) 和 [-refonly](../language-reference/compiler-options/refonly-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="fba4f-401">There are two new compiler options that generate *reference-only assemblies*: [-refout](../language-reference/compiler-options/refout-compiler-option.md) and [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="fba4f-402">連結的文章將更詳細地說明這些選項和參考組件。</span><span class="sxs-lookup"><span data-stu-id="fba4f-402">The linked articles explain these options and reference assemblies in more detail.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="fba4f-403">公用或開放原始碼簽署</span><span class="sxs-lookup"><span data-stu-id="fba4f-403">Public or Open Source signing</span></span>

<span data-ttu-id="fba4f-404">`-publicsign` 編譯器選項會指示編譯器使用公開金鑰簽署組件。</span><span class="sxs-lookup"><span data-stu-id="fba4f-404">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="fba4f-405">該組件標示為已簽署，但簽章取自公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="fba4f-405">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="fba4f-406">此選項可讓您使用公開金鑰，從開放原始碼專案建置簽署的組件。</span><span class="sxs-lookup"><span data-stu-id="fba4f-406">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="fba4f-407">如需詳細資訊，請參閱 [-publicsign 編譯器選項](../language-reference/compiler-options/publicsign-compiler-option.md)一文。</span><span class="sxs-lookup"><span data-stu-id="fba4f-407">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="fba4f-408">pathmap</span><span class="sxs-lookup"><span data-stu-id="fba4f-408">pathmap</span></span>

<span data-ttu-id="fba4f-409">`-pathmap` 編譯器選項會指示編譯器使用對應的來源路徑取代建置環境的來源路徑。</span><span class="sxs-lookup"><span data-stu-id="fba4f-409">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="fba4f-410">`-pathmap` 選項控制編譯器寫入 PDB 檔案或 <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> 的來源路徑。</span><span class="sxs-lookup"><span data-stu-id="fba4f-410">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="fba4f-411">如需詳細資訊，請參閱 [-pathmap 編譯器選項](../language-reference/compiler-options/pathmap-compiler-option.md)一文。</span><span class="sxs-lookup"><span data-stu-id="fba4f-411">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span></span>
