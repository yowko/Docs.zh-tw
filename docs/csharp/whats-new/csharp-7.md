---
title: "C# 7 的新功能 - C# 指南"
description: "取得 C# 語言未來版本 7 的新功能概觀。"
keywords: "C#, .NET, .NET Core, 最新功能, 新功能"
author: BillWagner
ms.author: wiwagn
ms.date: 12/21/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: 374ac9917464a7e83566440abab10eda8a9c8683
ms.sourcegitcommit: 32172ca05d5dcce7ef3d327b9c8639c736e0fe2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2018
---
# <a name="whats-new-in-c-7"></a><span data-ttu-id="96b8f-104">C# 7 的新功能</span><span class="sxs-lookup"><span data-stu-id="96b8f-104">What's new in C# 7</span></span>

<span data-ttu-id="96b8f-105">C# 7 新增許多新功能至 C# 語言︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-105">C# 7 adds a number of new features to the C# language:</span></span>
* [<span data-ttu-id="96b8f-106">`out` 變數</span><span class="sxs-lookup"><span data-stu-id="96b8f-106">`out` variables</span></span>](#out-variables)
    - <span data-ttu-id="96b8f-107">您可以宣告 `out` 內嵌值作為使用它們之方法的引數。</span><span class="sxs-lookup"><span data-stu-id="96b8f-107">You can declare `out` values inline as arguments to the method where they are used.</span></span>
* [<span data-ttu-id="96b8f-108">元組</span><span class="sxs-lookup"><span data-stu-id="96b8f-108">Tuples</span></span>](#tuples)
    - <span data-ttu-id="96b8f-109">您可以建立包含多個公用欄位的輕量、未具名的類型。</span><span class="sxs-lookup"><span data-stu-id="96b8f-109">You can create lightweight, unnamed types that contain multiple public fields.</span></span> <span data-ttu-id="96b8f-110">編譯器和 IDE 工具了解這些類型的語意。</span><span class="sxs-lookup"><span data-stu-id="96b8f-110">Compilers and IDE tools understand the semantics of these types.</span></span>
* [<span data-ttu-id="96b8f-111">捨棄</span><span class="sxs-lookup"><span data-stu-id="96b8f-111">Discards</span></span>](#discards)
    - <span data-ttu-id="96b8f-112">捨棄是當您不在意指派的值時，於指派內使用的僅限寫入且暫時之變數。</span><span class="sxs-lookup"><span data-stu-id="96b8f-112">Discards are temporary, write-only variables used in assignments when you don't care about the value assigned.</span></span> <span data-ttu-id="96b8f-113">解構元組及使用者定義型別，以及使用 `out` 參數呼叫方法時，捨棄特別實用。</span><span class="sxs-lookup"><span data-stu-id="96b8f-113">They are particularly useful when deconstructing tuples and user-defined types, as well as when calling methods with `out` parameters.</span></span>
* [<span data-ttu-id="96b8f-114">模式比對</span><span class="sxs-lookup"><span data-stu-id="96b8f-114">Pattern Matching</span></span>](#pattern-matching)
    - <span data-ttu-id="96b8f-115">您可以建立以任意類型和這些類型成員的值為基礎的分支邏輯。</span><span class="sxs-lookup"><span data-stu-id="96b8f-115">You can create branching logic based on arbitrary types and values of the members of those types.</span></span>
* [<span data-ttu-id="96b8f-116">`ref` 區域變數和傳回</span><span class="sxs-lookup"><span data-stu-id="96b8f-116">`ref` locals and returns</span></span>](#ref-locals-and-returns)
    - <span data-ttu-id="96b8f-117">方法引數和區域變數可以是其他儲存體的參考。</span><span class="sxs-lookup"><span data-stu-id="96b8f-117">Method arguments and local variables can be references to other storage.</span></span>
* [<span data-ttu-id="96b8f-118">區域函式</span><span class="sxs-lookup"><span data-stu-id="96b8f-118">Local Functions</span></span>](#local-functions)
    - <span data-ttu-id="96b8f-119">您可以將函式巢狀放置在其他函式內，限制其範圍和可視性。</span><span class="sxs-lookup"><span data-stu-id="96b8f-119">You can nest functions inside other functions to limit their scope and visibility.</span></span>
* [<span data-ttu-id="96b8f-120">更多運算式主體成員</span><span class="sxs-lookup"><span data-stu-id="96b8f-120">More expression-bodied members</span></span>](#more-expression-bodied-members)
    - <span data-ttu-id="96b8f-121">可以使用運算式來撰寫的成員清單已經增長。</span><span class="sxs-lookup"><span data-stu-id="96b8f-121">The list of members that can be authored using expressions has grown.</span></span>
* [<span data-ttu-id="96b8f-122">`throw`運算式</span><span class="sxs-lookup"><span data-stu-id="96b8f-122">`throw` Expressions</span></span>](#throw-expressions)
    - <span data-ttu-id="96b8f-123">您可以在程式碼建構中擲回先前因為 `throw` 是陳述式而不允許的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="96b8f-123">You can throw exceptions in code constructs that previously were not allowed because `throw` was a statement.</span></span> 
* [<span data-ttu-id="96b8f-124">通用的非同步傳回型別</span><span class="sxs-lookup"><span data-stu-id="96b8f-124">Generalized async return types</span></span>](#generalized-async-return-types)
    - <span data-ttu-id="96b8f-125">使用 `async` 修飾詞宣告的方法除了 `Task` 和 `Task<T>` 之外，也能傳回其他類型。</span><span class="sxs-lookup"><span data-stu-id="96b8f-125">Methods declared with the `async` modifier can return other types in addition to `Task` and `Task<T>`.</span></span>
* [<span data-ttu-id="96b8f-126">數值常值語法增強功能</span><span class="sxs-lookup"><span data-stu-id="96b8f-126">Numeric literal syntax improvements</span></span>](#numeric-literal-syntax-improvements)
    - <span data-ttu-id="96b8f-127">新的語彙基元改善了數值常數的可讀性。</span><span class="sxs-lookup"><span data-stu-id="96b8f-127">New tokens improve readability for numeric constants.</span></span>

<span data-ttu-id="96b8f-128">本主題的其餘部分將討論每項功能。</span><span class="sxs-lookup"><span data-stu-id="96b8f-128">The remainder of this topic discusses each of the features.</span></span> <span data-ttu-id="96b8f-129">您將了解每項功能背後的原因。</span><span class="sxs-lookup"><span data-stu-id="96b8f-129">For each feature, you'll learn the reasoning behind it.</span></span> <span data-ttu-id="96b8f-130">您將了解語法。</span><span class="sxs-lookup"><span data-stu-id="96b8f-130">You'll learn the syntax.</span></span> <span data-ttu-id="96b8f-131">您會看到一些範例案例，其中使用新的功能可讓身為開發人員的您提高生產力。</span><span class="sxs-lookup"><span data-stu-id="96b8f-131">You'll see some sample scenarios where using the new feature will make you more productive as a developer.</span></span> 

## <a name="out-variables"></a><span data-ttu-id="96b8f-132">`out` 變數</span><span class="sxs-lookup"><span data-stu-id="96b8f-132">`out` variables</span></span>

<span data-ttu-id="96b8f-133">在這個版本中，支援 `out` 參數的現有語法已經過改善。</span><span class="sxs-lookup"><span data-stu-id="96b8f-133">The existing syntax that supports `out` parameters has been improved in this version.</span></span>  

<span data-ttu-id="96b8f-134">過去，您需要將 out 變數和其初始化的宣告分為兩個不同的陳述式︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-134">Previously, you would need to separate the declaration of the out variable and its initialization into two different statements:</span></span>

[!code-csharp[OutVariableOldStyle](../../../samples/snippets/csharp/new-in-7/program.cs#03_OutVariableOldStyle "classic out variable declaration")]

<span data-ttu-id="96b8f-135">您現在可以在方法呼叫的引數清單中宣告 `out` 變數，而不是撰寫個別的宣告陳述式︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-135">You can now declare `out` variables in the argument list of a method call, rather than writing a separate declaration statement:</span></span>

[!code-csharp[OutVariableDeclarations](../../../samples/snippets/csharp/new-in-7/program.cs#01_OutVariableDeclarations "Out variable declarations")]

<span data-ttu-id="96b8f-136">為了清楚起見，您可能想要指定 `out` 變數的類型，如上所示。</span><span class="sxs-lookup"><span data-stu-id="96b8f-136">You may want to specify the type of the `out` variable for clarity, as shown above.</span></span> <span data-ttu-id="96b8f-137">不過，語言有支援使用隱含型別區域變數︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-137">However, the language does support using an implicitly typed local variable:</span></span>

[!code-csharp[OutVarVariableDeclarations](../../../samples/snippets/csharp/new-in-7/program.cs#02_OutVarVariableDeclarations "Implicitly typed Out variable")]

* <span data-ttu-id="96b8f-138">程式碼更容易閱讀與理解。</span><span class="sxs-lookup"><span data-stu-id="96b8f-138">The code is easier to read.</span></span> 
    - <span data-ttu-id="96b8f-139">您在使用之處宣告 out 變數，而不是在上方另一行。</span><span class="sxs-lookup"><span data-stu-id="96b8f-139">You declare the out variable where you use it, not on another line above.</span></span>
* <span data-ttu-id="96b8f-140">不需要指派初始值。</span><span class="sxs-lookup"><span data-stu-id="96b8f-140">No need to assign an initial value.</span></span>
    - <span data-ttu-id="96b8f-141">藉由在方法呼叫中使用之處宣告 `out` 變數，就無法在指派它之前意外使用它。</span><span class="sxs-lookup"><span data-stu-id="96b8f-141">By declaring the `out` variable where it is used in a method call, you can't accidentally use it before it is assigned.</span></span>

<span data-ttu-id="96b8f-142">這項功能最常見的用途是 `Try` 模式。</span><span class="sxs-lookup"><span data-stu-id="96b8f-142">The most common use for this feature will be the `Try` pattern.</span></span> <span data-ttu-id="96b8f-143">在此模式中，方法會傳回 `bool`，指出成功或失敗，以及一個 `out` 變數，提供方法成功時的結果。</span><span class="sxs-lookup"><span data-stu-id="96b8f-143">In this pattern, a method returns a `bool` indicating success or failure and an `out` variable that provides the result if the method succeeds.</span></span>

<span data-ttu-id="96b8f-144">當使用 `out` 變數宣告時，宣告的變數會「遺漏」到 if 陳述式的外部範圍。</span><span class="sxs-lookup"><span data-stu-id="96b8f-144">When using the `out` variable declaration, the declared variable "leaks" into the outer scope of the if statement.</span></span> <span data-ttu-id="96b8f-145">這可讓您在之後使用變數︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-145">This allows you to use the variable afterwards:</span></span>

```csharp
if (!int.TryParse(input, out int result))
{    
    return null;
}

return result;
```

## <a name="tuples"></a><span data-ttu-id="96b8f-146">Tuple</span><span class="sxs-lookup"><span data-stu-id="96b8f-146">Tuples</span></span>

> [!NOTE]
> <span data-ttu-id="96b8f-147">新的 Tuple 功能需要 <xref:System.ValueTuple> 類型。</span><span class="sxs-lookup"><span data-stu-id="96b8f-147">The new tuples features require the <xref:System.ValueTuple> types.</span></span>
> <span data-ttu-id="96b8f-148">您必須新增 NuGet 套件 [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/)，以將它用於不包含類型的平台。</span><span class="sxs-lookup"><span data-stu-id="96b8f-148">You must add the NuGet package [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) in order to use it on platforms that do not include the types.</span></span>
>
> <span data-ttu-id="96b8f-149">這類似於依賴架構中所傳遞類型的其他語言功能。</span><span class="sxs-lookup"><span data-stu-id="96b8f-149">This is similar to other language features that rely on types delivered in the framework.</span></span> <span data-ttu-id="96b8f-150">範例包含依賴 `INotifyCompletion` 介面的 `async` 和 `await`，以及依賴 `IEnumerable<T>` 的 LINQ。</span><span class="sxs-lookup"><span data-stu-id="96b8f-150">Example include `async` and `await` relying on the `INotifyCompletion` interface, and LINQ relying on `IEnumerable<T>`.</span></span> <span data-ttu-id="96b8f-151">不過，傳遞機制會變更，因為 .NET 變得與平台更為無關。</span><span class="sxs-lookup"><span data-stu-id="96b8f-151">However, the delivery mechanism is changing as .NET is becoming more platform independent.</span></span> <span data-ttu-id="96b8f-152">.NET Framework 可能不會永遠隨附於相同的步調，作為語言編譯器。</span><span class="sxs-lookup"><span data-stu-id="96b8f-152">The .NET Framework may not always ship on the same cadence as the language compiler.</span></span> <span data-ttu-id="96b8f-153">如果新語言功能依賴新類型，則在提供語言功能時，會以 NuGet 套件形式提供這些類型。</span><span class="sxs-lookup"><span data-stu-id="96b8f-153">When new language features rely on new types, those types will be available as NuGet packages when the language features ship.</span></span> <span data-ttu-id="96b8f-154">因為這些新類型會新增至 .NET Standard API 並傳遞為架構的一部分，所以將會移除 NuGet 套件需求。</span><span class="sxs-lookup"><span data-stu-id="96b8f-154">As these new types get added to the .NET Standard API and delivered as part of the framework, the NuGet package requirement will be removed.</span></span>

<span data-ttu-id="96b8f-155">C# 為類別和結構提供豐富的語法，可用來解釋您的設計目的。</span><span class="sxs-lookup"><span data-stu-id="96b8f-155">C# provides a rich syntax for classes and structs that is used to explain your design intent.</span></span> <span data-ttu-id="96b8f-156">但有時候豐富的語法需要額外的工作才能得到最少的好處。</span><span class="sxs-lookup"><span data-stu-id="96b8f-156">But sometimes that rich syntax requires extra work with minimal benefit.</span></span> <span data-ttu-id="96b8f-157">您可能經常撰寫需要包含多個資料項目之簡單結構的方法。</span><span class="sxs-lookup"><span data-stu-id="96b8f-157">You may often write methods that need a simple structure containing more than one data element.</span></span> <span data-ttu-id="96b8f-158">為了支援這些案例，C# 已新增 *Tuple*。</span><span class="sxs-lookup"><span data-stu-id="96b8f-158">To support these scenarios *tuples* were added to C#.</span></span> <span data-ttu-id="96b8f-159">Tuple 是輕量的資料結構，其中包含多個欄位來代表資料成員。</span><span class="sxs-lookup"><span data-stu-id="96b8f-159">Tuples are lightweight data structures that contain multiple fields to represent the data members.</span></span>
<span data-ttu-id="96b8f-160">不會驗證這些欄位，且您不能定義自己的方法</span><span class="sxs-lookup"><span data-stu-id="96b8f-160">The fields are not validated, and you cannot define your own methods</span></span>

> [!NOTE]
> <span data-ttu-id="96b8f-161">元組在 C# 7 之前即可使用，但效率不彰且沒有語言支援。</span><span class="sxs-lookup"><span data-stu-id="96b8f-161">Tuples were available before C# 7, but they were inefficient and had no language support.</span></span>
> <span data-ttu-id="96b8f-162">這表示元組元素只能參考為 `Item1`及 `Item2` 等等。</span><span class="sxs-lookup"><span data-stu-id="96b8f-162">This meant that tuple elements could only be referenced as `Item1`, `Item2` and so on.</span></span> <span data-ttu-id="96b8f-163">C# 7 加入了元組的語言支援，讓元組欄位的語意名稱能使用全新且更具效率的元組型別。</span><span class="sxs-lookup"><span data-stu-id="96b8f-163">C# 7 introduces language support for tuples, which enables semantic names for the fields of a tuple using new, more efficient tuple types.</span></span>

<span data-ttu-id="96b8f-164">您可以指派每個成員到一個值，以建立 Tuple︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-164">You can create a tuple by assigning each member to a value:</span></span>

[!code-csharp[UnnamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#04_UnnamedTuple "Unnamed tuple")]

<span data-ttu-id="96b8f-165">指派會建立成員為 `Item1` 與 `Item2` 的元組，而您能使用與 <xref:System.Tuple> 相同的方式加以使用。您可以變更語法，以建立能夠為元組中每位成員提供語意名稱的元組：</span><span class="sxs-lookup"><span data-stu-id="96b8f-165">That assignment creates a tuple whose members are `Item1` and `Item2`, which you can use in the same way as <xref:System.Tuple> You can change the syntax to create a tuple that provides semantic names to each of the members of the tuple:</span></span>

[!code-csharp[NamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#05_NamedTuple "Named tuple")]

<span data-ttu-id="96b8f-166">`namedLetters` Tuple 包含稱為 `Alpha` 和 `Beta` 的欄位。</span><span class="sxs-lookup"><span data-stu-id="96b8f-166">The `namedLetters` tuple contains fields referred to as `Alpha` and `Beta`.</span></span> <span data-ttu-id="96b8f-167">這些名稱只會在編譯時間出現而不會保留，例如在執行階段使用反映調查元組時。</span><span class="sxs-lookup"><span data-stu-id="96b8f-167">Those names exist only at compile time and are not preserved for example when inspecting the tuple using reflection at runtime.</span></span>

<span data-ttu-id="96b8f-168">在 Tuple 指派中，您也可以在指派的右邊，指定欄位的名稱︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-168">In a tuple assignment, you can also specify the names of the fields on the right-hand side of the assignment:</span></span>

[!code-csharp[ImplicitNamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#06_ImplicitNamedTuple "Implicitly named tuple")]

<span data-ttu-id="96b8f-169">您可以在指定指派左側及右側的欄位名稱︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-169">You can specify names for the fields on both the left and right-hand side of the assignment:</span></span>

[!code-csharp[NamedTupleConflict](../../../samples/snippets/csharp/new-in-7/program.cs#07_NamedTupleConflict "Named tuple conflict")]

<span data-ttu-id="96b8f-170">上述列會產生警告 `CS8123`，告訴您指派右邊的名稱 `Alpha` 和 `Beta` 會被忽略，因為它們與左邊的名稱 `First` 和 `Second` 發生衝突。</span><span class="sxs-lookup"><span data-stu-id="96b8f-170">The line above generates a warning, `CS8123`, telling you that the names on the right side of the assignment, `Alpha` and `Beta` are ignored because they conflict with the names on the left side, `First` and `Second`.</span></span>

<span data-ttu-id="96b8f-171">上述範例顯示宣告 Tuple 的基本語法。</span><span class="sxs-lookup"><span data-stu-id="96b8f-171">The examples above show the basic syntax to declare tuples.</span></span> <span data-ttu-id="96b8f-172">Tuple 最適合用作 `private` 和 `internal` 方法的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="96b8f-172">Tuples are most useful as return types for `private` and `internal` methods.</span></span> <span data-ttu-id="96b8f-173">Tuple 提供簡單的語法，可讓方法傳回多個離散值︰您節省了撰寫定義傳回型別之 `class` 或 `struct` 的工作。</span><span class="sxs-lookup"><span data-stu-id="96b8f-173">Tuples provide a simple syntax for those methods to return multiple discrete values: You save the work of authoring a `class` or a `struct` that defines the type returned.</span></span> <span data-ttu-id="96b8f-174">不需要建立新的類型。</span><span class="sxs-lookup"><span data-stu-id="96b8f-174">There is no need for creating a new type.</span></span>

<span data-ttu-id="96b8f-175">建立 Tuple 更有效率且更具生產力。</span><span class="sxs-lookup"><span data-stu-id="96b8f-175">Creating a tuple is more efficient and more productive.</span></span>
<span data-ttu-id="96b8f-176">它是一個更簡單的輕量語法，可定義攜帶多個值的資料結構。</span><span class="sxs-lookup"><span data-stu-id="96b8f-176">It is a simpler, lightweight syntax to define a data structure that carries more than one value.</span></span> <span data-ttu-id="96b8f-177">下列範例方法會傳回在一個整數序列中找到的最小和最大值︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-177">The example method below returns the minimum and maximum values found in a sequence of integers:</span></span>

[!code-csharp[TupleReturningMethod](../../../samples/snippets/csharp/new-in-7/program.cs#08_TupleReturningMethod "Tuple returning method")]

<span data-ttu-id="96b8f-178">如此來使用 Tuple 可提供數個優點︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-178">Using tuples in this way offers several advantages:</span></span>

* <span data-ttu-id="96b8f-179">您節省了撰寫定義傳回型別之 `class` 或 `struct` 的工作。</span><span class="sxs-lookup"><span data-stu-id="96b8f-179">You save the work of authoring a `class` or a `struct` that defines the type returned.</span></span> 
* <span data-ttu-id="96b8f-180">您不需要建立新的類型。</span><span class="sxs-lookup"><span data-stu-id="96b8f-180">You do not need to create new type.</span></span>
* <span data-ttu-id="96b8f-181">語言的增強功能可讓您免於呼叫 <xref:System.Tuple.Create``1(``0)> 方法。</span><span class="sxs-lookup"><span data-stu-id="96b8f-181">The language enhancements removes the need to call the <xref:System.Tuple.Create``1(``0)> methods.</span></span>

<span data-ttu-id="96b8f-182">方法的宣告提供所傳回 Tuple 欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="96b8f-182">The declaration for the method provides the names for the fields of the tuple that is returned.</span></span> <span data-ttu-id="96b8f-183">當您呼叫的方法時，傳回值是一個 Tuple，其欄位為 `Max` 和 `Min`：</span><span class="sxs-lookup"><span data-stu-id="96b8f-183">When you call the method, the return value is a tuple whose fields are `Max` and `Min`:</span></span>

[!code-csharp[CallingTupleMethod](../../../samples/snippets/csharp/new-in-7/program.cs#09_CallingTupleMethod "Calling a tuple returning method")]

<span data-ttu-id="96b8f-184">有時候您可能會想要解除封裝已從方法傳回的 Tuple 成員。</span><span class="sxs-lookup"><span data-stu-id="96b8f-184">There may be times when you want to unpackage the members of a tuple that were returned from a method.</span></span>  <span data-ttu-id="96b8f-185">您可以藉由為 Tuple 中的每個值宣告不同變數來這麼做。</span><span class="sxs-lookup"><span data-stu-id="96b8f-185">You can do that by declaring separate variables for each of the values in the tuple.</span></span> <span data-ttu-id="96b8f-186">這稱為「解構」Tuple：</span><span class="sxs-lookup"><span data-stu-id="96b8f-186">This is called *deconstructing* the tuple:</span></span>

[!code-csharp[CallingWithDeconstructor](../../../samples/snippets/csharp/new-in-7/program.cs#10_CallingWithDeconstructor "Deconstructing a tuple")]

<!-- Add wildcards here, if they are in C# 7
-->

<span data-ttu-id="96b8f-187">您也可以在 .NET 中為任何類型提供類似的解構。</span><span class="sxs-lookup"><span data-stu-id="96b8f-187">You can also provide a similar deconstruction for any type in .NET.</span></span> <span data-ttu-id="96b8f-188">這是藉由撰寫 `Deconstruct` 方法作為類別的成員而達成。</span><span class="sxs-lookup"><span data-stu-id="96b8f-188">This is done by writing a `Deconstruct` method as a member of the class.</span></span> <span data-ttu-id="96b8f-189">`Deconstruct` 方法為您想要擷取的每個屬性提供一組 `out` 引數。</span><span class="sxs-lookup"><span data-stu-id="96b8f-189">That `Deconstruct` method provides a set of `out` arguments for each of the properties you want to extract.</span></span> <span data-ttu-id="96b8f-190">請考慮這個 `Point` 類別，它會提供 deconstructor 方法，擷取 `X` 和 `Y` 座標︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-190">Consider this `Point` class that provides a deconstructor method that extracts the `X` and `Y` coordinates:</span></span>

[!code-csharp[PointWithDeconstruction](../../../samples/snippets/csharp/new-in-7/point.cs#11_PointWithDeconstruction "Point with deconstruction method")]
 
<span data-ttu-id="96b8f-191">您可以藉由指派 Tuple 至 `Point` 來擷取個別的欄位：</span><span class="sxs-lookup"><span data-stu-id="96b8f-191">You can extract the individual fields by assigning a tuple to a `Point`:</span></span>

[!code-csharp[DeconstructPoint](../../../samples/snippets/csharp/new-in-7/program.cs#12_DeconstructPoint "Deconstruct a point")]

<span data-ttu-id="96b8f-192">您不受限於 `Deconstruct` 方法中定義的名稱。</span><span class="sxs-lookup"><span data-stu-id="96b8f-192">You are not bound by the names defined in the `Deconstruct` method.</span></span> <span data-ttu-id="96b8f-193">您可以在指派過程中將擷取變數重新命名︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-193">You can rename the extract variables as part of the assignment:</span></span>  

[!code-csharp[DeconstructNames](../../../samples/snippets/csharp/new-in-7/program.cs#13_DeconstructNames "Deconstruct with new names")]

<span data-ttu-id="96b8f-194">您可以在 [Tuple 主題](../tuples.md)中深入了解 Tuple。</span><span class="sxs-lookup"><span data-stu-id="96b8f-194">You can learn more in depth about tuples in the [tuples topic](../tuples.md).</span></span>

## <a name="discards"></a><span data-ttu-id="96b8f-195">捨棄</span><span class="sxs-lookup"><span data-stu-id="96b8f-195">Discards</span></span>

<span data-ttu-id="96b8f-196">通常在您解構元組或以 `out` 參數呼叫方法時，會強制您要定義變數，而您無須在意變數的值也沒有使用該值的打算。</span><span class="sxs-lookup"><span data-stu-id="96b8f-196">Often when deconstructing a tuple or calling a method with `out` parameters, you're forced to define a variable whose value you don't care about and don't intend to use.</span></span> <span data-ttu-id="96b8f-197">C# 新增了對*捨棄*的支援，來應付這種狀況。</span><span class="sxs-lookup"><span data-stu-id="96b8f-197">C# adds support for *discards* to handle this scenario.</span></span> <span data-ttu-id="96b8f-198">捨棄是僅限寫入的變數，其名稱為 `_` (底線字元)；您可將所有想要捨棄的值指派到單一變數。</span><span class="sxs-lookup"><span data-stu-id="96b8f-198">A discard is a write-only variable whose name is `_` (the underscore character); you can assign all of the values that you intend to discard to the single variable.</span></span> <span data-ttu-id="96b8f-199">捨棄類似於未經指派的變數；和指派陳述式一樣，都不能用於程式碼中。</span><span class="sxs-lookup"><span data-stu-id="96b8f-199">A discard is like an unassigned variable; apart from the assignment statement, the discard can't be used in code.</span></span>

<span data-ttu-id="96b8f-200">下列情況中支援捨棄：</span><span class="sxs-lookup"><span data-stu-id="96b8f-200">Discards are supported in the following scenarios:</span></span>

* <span data-ttu-id="96b8f-201">解構元組或使用者定義型別時。</span><span class="sxs-lookup"><span data-stu-id="96b8f-201">When deconstructing tuples or user-defined types.</span></span>

* <span data-ttu-id="96b8f-202">以 [out](../language-reference/keywords/out-parameter-modifier.md) 參數呼叫方法時。</span><span class="sxs-lookup"><span data-stu-id="96b8f-202">When calling methods with [out](../language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>

* <span data-ttu-id="96b8f-203">執行 [is](../language-reference/keywords/is.md) 及 [switch](../language-reference/keywords/switch.md) 陳述式的模式比對作業時。</span><span class="sxs-lookup"><span data-stu-id="96b8f-203">In a pattern matching operation with the [is](../language-reference/keywords/is.md) and [switch](../language-reference/keywords/switch.md) statements.</span></span>

* <span data-ttu-id="96b8f-204">作為獨立識別項，當您想要將指派的值明確識別為捨棄時。</span><span class="sxs-lookup"><span data-stu-id="96b8f-204">As a standalone identifier when you want to explicitly identify the value of an assignment as a discard.</span></span>

<span data-ttu-id="96b8f-205">下列範例定義的 `QueryCityDataForYears` 方法，會傳回包含兩個不同年份的城市資料之 6 元組。</span><span class="sxs-lookup"><span data-stu-id="96b8f-205">The following example defines a `QueryCityDataForYears` method that returns a 6-tuple that contains a data for a city for two different years.</span></span> <span data-ttu-id="96b8f-206">範例中的方法呼叫只有對方法傳回的兩個母體有效，所以會在解構元組時，將元組中剩餘的值視作捨棄處理。</span><span class="sxs-lookup"><span data-stu-id="96b8f-206">The method call in the example is concerned only with the two population values returned by the method and so treats the remaining values in the tuple as discards when it deconstructs the tuple.</span></span>

[!code-csharp[Tuple-discard](../../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

<span data-ttu-id="96b8f-207">如需詳細資訊，請參閱[捨棄](../discards.md)。</span><span class="sxs-lookup"><span data-stu-id="96b8f-207">For more information, see [Discards](../discards.md).</span></span>
 
## <a name="pattern-matching"></a><span data-ttu-id="96b8f-208">模式比對</span><span class="sxs-lookup"><span data-stu-id="96b8f-208">Pattern matching</span></span>

<span data-ttu-id="96b8f-209">「模式比對」是一項功能，可讓您對物件類型以外的屬性實作方法分派。</span><span class="sxs-lookup"><span data-stu-id="96b8f-209">*Pattern matching* is a feature that allows you to implement method dispatch on properties other than the type of an object.</span></span> <span data-ttu-id="96b8f-210">您可能已經熟悉根據物件類型的方法分派。</span><span class="sxs-lookup"><span data-stu-id="96b8f-210">You're probably already familiar with method dispatch based on the type of an object.</span></span> <span data-ttu-id="96b8f-211">在物件導向程式設計中，虛擬和覆寫方法可提供語言語法，以實作根據物件類型的方法分派。</span><span class="sxs-lookup"><span data-stu-id="96b8f-211">In Object Oriented programming, virtual and override methods provide language syntax to implement method dispatching based on an object's type.</span></span> <span data-ttu-id="96b8f-212">基底和衍生類別能提供不同的實作。</span><span class="sxs-lookup"><span data-stu-id="96b8f-212">Base and Derived classes provide different implementations.</span></span> <span data-ttu-id="96b8f-213">模式比對運算式會擴充這個概念，讓您可以輕鬆地為不是透過繼承階層架構而關聯的類型和資料項目實作類似的分派模式。</span><span class="sxs-lookup"><span data-stu-id="96b8f-213">Pattern matching expressions extend this concept so that you can easily implement similar dispatch patterns for types and data elements that are not related through an inheritance hierarchy.</span></span> 

<span data-ttu-id="96b8f-214">模式比對支援 `is` 運算式和 `switch` 運算式。</span><span class="sxs-lookup"><span data-stu-id="96b8f-214">Pattern matching supports `is` expressions and `switch` expressions.</span></span> <span data-ttu-id="96b8f-215">每個都讓您能檢查物件和其屬性，以判斷該物件是否符合搜尋的模式。</span><span class="sxs-lookup"><span data-stu-id="96b8f-215">Each enables inspecting an object and its properties to determine if that object satisfies the sought pattern.</span></span> <span data-ttu-id="96b8f-216">您使用 `when` 關鍵字來指定其他規則給該模式。</span><span class="sxs-lookup"><span data-stu-id="96b8f-216">You use the `when` keyword to specify additional rules to the pattern.</span></span>

### <a name="is-expression"></a><span data-ttu-id="96b8f-217">`is` 運算式</span><span class="sxs-lookup"><span data-stu-id="96b8f-217">`is` expression</span></span>

<span data-ttu-id="96b8f-218">`is` 模式運算式會擴充熟悉的 `is` 運算子，來查詢其類型之外的物件。</span><span class="sxs-lookup"><span data-stu-id="96b8f-218">The `is` pattern expression extends the familiar `is` operator to query an object beyond its type.</span></span>

<span data-ttu-id="96b8f-219">舉個簡單的案例。</span><span class="sxs-lookup"><span data-stu-id="96b8f-219">Let's start with a simple scenario.</span></span> <span data-ttu-id="96b8f-220">我們會將功能加入此案例中，示範模式比對運算式如何讓處理非相關類型的演算法變簡單。</span><span class="sxs-lookup"><span data-stu-id="96b8f-220">We'll add capabilities to this scenario that demonstrate how pattern matching expressions make algorithms that work with unrelated types easy.</span></span> <span data-ttu-id="96b8f-221">我們將從計算數次擲骰子總和的方法開始︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-221">We'll start with a method that computes the sum of a number of die rolls:</span></span>

[!code-csharp[SumDieRolls](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#14_SumDieRolls "Sum die rolls")]

<span data-ttu-id="96b8f-222">您可能會很快發現您需要找出部分擲骰情況是以多個骰子所擲出的擲骰子總和。</span><span class="sxs-lookup"><span data-stu-id="96b8f-222">You might quickly find that you need to find the sum of die rolls where some of the rolls are made with multiple dice (dice is the plural of die).</span></span> <span data-ttu-id="96b8f-223">輸入序列的一部分可能是多個結果，而不是單一數字︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-223">Part of the input sequence may be multiple results instead of a single number:</span></span>

[!code-csharp[SumDieRollsWithGroups](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#15_SumDieRollsWithGroups "Sum die rolls with groups")]

<span data-ttu-id="96b8f-224">`is` 模式運算式非常適合此案例。</span><span class="sxs-lookup"><span data-stu-id="96b8f-224">The `is` pattern expression works quite well in this scenario.</span></span> <span data-ttu-id="96b8f-225">在檢查類型時，您可以撰寫變數的初始化。</span><span class="sxs-lookup"><span data-stu-id="96b8f-225">As part of checking the type, you write a variable initialization.</span></span> <span data-ttu-id="96b8f-226">這會為已驗證的執行階段型別建立新的變數。</span><span class="sxs-lookup"><span data-stu-id="96b8f-226">This creates a new variable of the validated runtime type.</span></span>

<span data-ttu-id="96b8f-227">當您繼續擴充這些案例時，您可能會發現您建立了更多 `if` 和 `else if` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="96b8f-227">As you keep extending these scenarios, you may find that you build more `if` and `else if` statements.</span></span> <span data-ttu-id="96b8f-228">變得不便之後，您可能會想要切換至 `switch` 模式運算式。</span><span class="sxs-lookup"><span data-stu-id="96b8f-228">Once that becomes unwieldy, you'll likely want to switch to `switch` pattern expressions.</span></span>

### <a name="switch-statement-updates"></a><span data-ttu-id="96b8f-229">`switch` 陳述式更新</span><span class="sxs-lookup"><span data-stu-id="96b8f-229">`switch` statement updates</span></span>

<span data-ttu-id="96b8f-230">「比對運算式」的語法很熟悉，是根據已屬於 C# 語言一部分的 `switch` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="96b8f-230">The *match expression* has a familiar syntax, based on the `switch` statement already part of the C# language.</span></span> <span data-ttu-id="96b8f-231">讓我們先轉譯現有程式碼，使用比對運算式，之後才新增案例︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-231">Let's translate the existing code to use a match expression before adding new cases:</span></span> 

[!code-csharp[SumUsingSwitch](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#16_SumUsingSwitch "Sum using switch")]

<span data-ttu-id="96b8f-232">比對運算式的語法與 `is` 運算式稍微不同，您可在 `case` 運算式的開頭宣告類型和變數。</span><span class="sxs-lookup"><span data-stu-id="96b8f-232">The match expressions have a slightly different syntax than the `is` expressions, where you declare the type and variable at the beginning of the `case` expression.</span></span>

<span data-ttu-id="96b8f-233">比對運算式也支援常數。</span><span class="sxs-lookup"><span data-stu-id="96b8f-233">The match expressions also support constants.</span></span> <span data-ttu-id="96b8f-234">如此可以節省時間，因為已隔離簡單的案例︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-234">This can save time by factoring out simple cases:</span></span>

[!code-csharp[SwitchWithConstants](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#17_SwitchWithConstants "Switch with constants")]

<span data-ttu-id="96b8f-235">上述程式碼會新增 `0` 的案例作為 `int` 的特殊案例，並新增 `null` 作為沒有輸入時的特殊案例。</span><span class="sxs-lookup"><span data-stu-id="96b8f-235">The code above adds cases for `0` as a special case of `int`, and `null` as a special case when there is no input.</span></span> <span data-ttu-id="96b8f-236">這示範了參數模式運算式中的一個重要新功能︰`case` 運算式的順序現在有其重要性。</span><span class="sxs-lookup"><span data-stu-id="96b8f-236">This demonstrates one important new feature in switch pattern expressions: the order of the `case` expressions now matters.</span></span> <span data-ttu-id="96b8f-237">`0` 案例必須出現在一般 `int` 案例之前。</span><span class="sxs-lookup"><span data-stu-id="96b8f-237">The `0` case must appear before the general `int` case.</span></span> <span data-ttu-id="96b8f-238">否則，第一個符合的模式將是 `int` 案例，即使值是 `0`。</span><span class="sxs-lookup"><span data-stu-id="96b8f-238">Otherwise, the first pattern to match would be the `int` case, even when the value is `0`.</span></span> <span data-ttu-id="96b8f-239">如果您意外排列比對運算式，以致排列較後的案例已經過處理，則編譯器會將其加上旗標並產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="96b8f-239">If you accidentally order match expressions such that a later case has already been handled, the compiler will flag that and generate an error.</span></span>

<span data-ttu-id="96b8f-240">這個相同的行為可啟用空輸入序列的特殊案例。</span><span class="sxs-lookup"><span data-stu-id="96b8f-240">This same behavior enables the special case for an empty input sequence.</span></span>
<span data-ttu-id="96b8f-241">您可以看到，具有項目之 `IEnumerable` 項目的案例，必須出現在一般 `IEnumerable` 案例之前。</span><span class="sxs-lookup"><span data-stu-id="96b8f-241">You can see that the case for an `IEnumerable` item that has elements must appear before the general `IEnumerable` case.</span></span>

<span data-ttu-id="96b8f-242">此版本也新增了 `default` 案例。</span><span class="sxs-lookup"><span data-stu-id="96b8f-242">This version has also added a `default` case.</span></span> <span data-ttu-id="96b8f-243">`default` 案例一律會最後評估，不論它出現在來源中的順序為何。</span><span class="sxs-lookup"><span data-stu-id="96b8f-243">The `default` case is always evaluated last, regardless of the order it appears in the source.</span></span> <span data-ttu-id="96b8f-244">因此，慣例是將 `default` 案例放到最後。</span><span class="sxs-lookup"><span data-stu-id="96b8f-244">For that reason, convention is to put the `default` case last.</span></span>

<span data-ttu-id="96b8f-245">最後，我們要新增最後一個新骰子樣式的 `case`。</span><span class="sxs-lookup"><span data-stu-id="96b8f-245">Finally, let's add one last `case` for a new style of die.</span></span> <span data-ttu-id="96b8f-246">某些遊戲使用百分位數骰子來代表更大範圍的數字。</span><span class="sxs-lookup"><span data-stu-id="96b8f-246">Some games use percentile dice to represent larger ranges of numbers.</span></span> 

> [!NOTE]
> <span data-ttu-id="96b8f-247">兩個 10 面的百分位數骰子可以代表從 0 到 99 的每個數字。</span><span class="sxs-lookup"><span data-stu-id="96b8f-247">Two 10-sided percentile dice can represent every number from 0 through 99.</span></span> <span data-ttu-id="96b8f-248">一顆骰子的邊已標示為 `00`、`10`、`20`...`90`。</span><span class="sxs-lookup"><span data-stu-id="96b8f-248">One die has sides labelled `00`, `10`, `20`, ... `90`.</span></span> <span data-ttu-id="96b8f-249">另一顆骰子的邊已標示為 `0`、`1`、`2`...`9`。</span><span class="sxs-lookup"><span data-stu-id="96b8f-249">The other die has sides labeled `0`, `1`, `2`, ... `9`.</span></span> <span data-ttu-id="96b8f-250">將兩個骰子值相加，您就可以得到 0 到 99 的每個數字。</span><span class="sxs-lookup"><span data-stu-id="96b8f-250">Add the two die values together and you can get every number from 0 through 99.</span></span>

<span data-ttu-id="96b8f-251">若要將這種骰子新增至集合，請先定義代表百分位數骰子的類型。</span><span class="sxs-lookup"><span data-stu-id="96b8f-251">To add this kind of die to your collection, first define a type to represent the percentile dice.</span></span> <span data-ttu-id="96b8f-252">`TensDigit` 屬性可儲存值 `0`、`10`、`20`，最高到 `90`：</span><span class="sxs-lookup"><span data-stu-id="96b8f-252">The `TensDigit` property stores values `0`, `10`, `20`, up to `90`:</span></span>

[!code-csharp[18_PercentileDice](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#18_PercentileDice "Percentile Die type")]

<span data-ttu-id="96b8f-253">然後，新增新類型的 `case` 比對運算式︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-253">Then, add a `case` match expression for the new type:</span></span>

[!code-csharp[SwitchWithNewTypes](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#19_SwitchWithNewTypes "Include Percentile Die type")]

<span data-ttu-id="96b8f-254">模式比對運算式的新語法可讓您更輕鬆地根據物件的類型或其他屬性建立分派演算法，並使用清楚且簡潔的語法。</span><span class="sxs-lookup"><span data-stu-id="96b8f-254">The new syntax for pattern matching expressions makes it easier to create dispatch algorithms based on an object's type, or other properties, using a clear and concise syntax.</span></span> <span data-ttu-id="96b8f-255">模式比對運算式可讓在繼承方面不相關的資料類型上啟用這些建構。</span><span class="sxs-lookup"><span data-stu-id="96b8f-255">Pattern matching expressions enable these constructs on data types that are unrelated by inheritance.</span></span>

<span data-ttu-id="96b8f-256">您可以在 [C# 中的模式比對](../pattern-matching.md)專門主題中深入了解模式比對。</span><span class="sxs-lookup"><span data-stu-id="96b8f-256">You can learn more about pattern matching in the topic dedicated to [pattern matching in C#](../pattern-matching.md).</span></span>

## <a name="ref-locals-and-returns"></a><span data-ttu-id="96b8f-257">Ref 區域變數和傳回</span><span class="sxs-lookup"><span data-stu-id="96b8f-257">Ref locals and returns</span></span>

<span data-ttu-id="96b8f-258">這項功能可以啟用使用和傳回在其他地方定義之變數參考的演算法。</span><span class="sxs-lookup"><span data-stu-id="96b8f-258">This feature enables algorithms that use and return references to variables defined elsewhere.</span></span> <span data-ttu-id="96b8f-259">其中一個範例是使用大型矩陣，並尋找具有特定特性的單一位置。</span><span class="sxs-lookup"><span data-stu-id="96b8f-259">One example is working with large matrices, and finding a single location with certain characteristics.</span></span> <span data-ttu-id="96b8f-260">一種方法會傳回矩陣中單一位置的兩個索引︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-260">One method would return the two indices for a single location in the matrix:</span></span>

[!code-csharp[FindReturningIndices](../../../samples/snippets/csharp/new-in-7/MatrixSearch.cs#20_FindReturningIndices "Find returning indices")]

<span data-ttu-id="96b8f-261">這個程式碼有許多問題。</span><span class="sxs-lookup"><span data-stu-id="96b8f-261">There are many issues with this code.</span></span> <span data-ttu-id="96b8f-262">首先，它是傳回 Tuple 的公用方法。</span><span class="sxs-lookup"><span data-stu-id="96b8f-262">First of all, it's a public method that's returning a tuple.</span></span> <span data-ttu-id="96b8f-263">語言支援此做法，但公用 API 是慣用的使用者定義型別 (類別或結構)。</span><span class="sxs-lookup"><span data-stu-id="96b8f-263">The language supports this, but user defined types (either classes or structs) are preferred for public APIs.</span></span>

<span data-ttu-id="96b8f-264">第二，這個方法會傳回矩陣中之項目的索引。</span><span class="sxs-lookup"><span data-stu-id="96b8f-264">Second, this method is returning the indices to the item in the matrix.</span></span>
<span data-ttu-id="96b8f-265">那會導致呼叫端撰寫程式碼，使用那些索引來對矩陣進行取值，並修改單一項目︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-265">That leads callers to write code that uses those indices to dereference the matrix and modify a single element:</span></span>

[!code-csharp[UpdateItemFromIndices](../../../samples/snippets/csharp/new-in-7/program.cs#21_UpdateItemFromIndices "Update Item From Indices")]

<span data-ttu-id="96b8f-266">相反地，您可以撰寫方法，傳回對您想要變更之矩陣項目的「參考」。</span><span class="sxs-lookup"><span data-stu-id="96b8f-266">You'd rather write a method that returns a *reference* to the element of the matrix that you want to change.</span></span> <span data-ttu-id="96b8f-267">在舊版本中，您只能使用不安全的程式碼，並傳回對 `int` 的指標來完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="96b8f-267">You could only accomplish this by using unsafe code and returning a pointer to an `int` in previous versions.</span></span>

<span data-ttu-id="96b8f-268">讓我們逐步解說一系列的變更，以展示 ref 區域功能，並示範如何建立傳回對內部儲存體之參考的方法。</span><span class="sxs-lookup"><span data-stu-id="96b8f-268">Let's walk through a series of changes to demonstrate the ref local feature and show how to create a method that returns a reference to internal storage.</span></span>
<span data-ttu-id="96b8f-269">在過程中，您將了解 ref 傳回和 ref 區域功能的規則，避免您不小心誤用。</span><span class="sxs-lookup"><span data-stu-id="96b8f-269">Along the way, you'll learn the rules of the ref return and ref local feature that protects you from accidentally misusing it.</span></span>

<span data-ttu-id="96b8f-270">一開始先修改 `Find` 方法宣告，讓它傳回 `ref int` 而不是 Tuple。</span><span class="sxs-lookup"><span data-stu-id="96b8f-270">Start by modifying the `Find` method declaration so that it returns a `ref int` instead of a tuple.</span></span> <span data-ttu-id="96b8f-271">然後，修改 return 陳述式，讓它傳回儲存在矩陣中的值，而不是兩個索引︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-271">Then, modify the return statement so it returns the value stored in the matrix instead of the two indices:</span></span>

```csharp
// Note that this won't compile. 
// Method declaration indicates ref return,
// but return statement specifies a value return.
public static ref int Find2(int[,] matrix, Func<int, bool> predicate)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
        for (int j = 0; j < matrix.GetLength(1); j++)
            if (predicate(matrix[i, j]))
                return matrix[i, j];
    throw new InvalidOperationException("Not found");
}
```

<span data-ttu-id="96b8f-272">當您宣告方法會傳回 `ref` 變數時，您也必須將 `ref` 關鍵字加入每個 return 陳述式。</span><span class="sxs-lookup"><span data-stu-id="96b8f-272">When you declare that a method returns a `ref` variable, you must also add the `ref` keyword to each return statement.</span></span> <span data-ttu-id="96b8f-273">那表示是以傳址方式傳回，並可協助稍後閱讀程式碼的開發人員記得該方法會以傳址方式傳回︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-273">That indicates return by reference, and helps developers reading the code later remember that the method returns by reference:</span></span>

[!code-csharp[FindReturningRef](../../../samples/snippets/csharp/new-in-7/MatrixSearch.cs#22_FindReturningRef "Find returning by reference")]

<span data-ttu-id="96b8f-274">既然方法會傳回矩陣中整數值的參考，您需要修改呼叫它的位置。</span><span class="sxs-lookup"><span data-stu-id="96b8f-274">Now that the method returns a reference to the integer value in the matrix, you need to modify where it's called.</span></span>  <span data-ttu-id="96b8f-275">`var` 宣告表示 `valItem` 現在是 `int`，而不是 Tuple：</span><span class="sxs-lookup"><span data-stu-id="96b8f-275">The `var` declaration means that `valItem` is now an `int` rather than a tuple:</span></span>

[!code-csharp[AssignRefReturnToValue](../../../samples/snippets/csharp/new-in-7/program.cs#23_AssignRefReturnToValue "Assign ref return to value")]

<span data-ttu-id="96b8f-276">在上述範例中的第二個 `WriteLine` 陳述式會列印出值 `42`，而非 `24`。</span><span class="sxs-lookup"><span data-stu-id="96b8f-276">The second `WriteLine` statement in the example above prints out the value `42`, not `24`.</span></span> <span data-ttu-id="96b8f-277">變數 `valItem` 是 `int`，而非 `ref int`。</span><span class="sxs-lookup"><span data-stu-id="96b8f-277">The variable `valItem` is an `int`, not a `ref int`.</span></span> <span data-ttu-id="96b8f-278">`var` 關鍵字可讓編譯器指定類型，但不會隱含地新增 `ref` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="96b8f-278">The `var` keyword enables the compiler to specify the type, but will not implicitly add the `ref` modifier.</span></span> <span data-ttu-id="96b8f-279">相反地，`ref return` 所指的值會「複製」到指派左手邊的變數。</span><span class="sxs-lookup"><span data-stu-id="96b8f-279">Instead, the value referred to by the `ref return` is *copied* to the variable on the left-hand side of the assignment.</span></span> <span data-ttu-id="96b8f-280">變數不是 `ref` 區域變數。</span><span class="sxs-lookup"><span data-stu-id="96b8f-280">The variable is not a `ref` local.</span></span>

<span data-ttu-id="96b8f-281">若要取得您想要的結果，您需要將 `ref` 修飾詞加入區域變數宣告，當傳回值是參考時，讓變數成為參考︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-281">In order to get the result you want, you need to add the `ref` modifier to the local variable declaration to make the variable a reference when the return value is a reference:</span></span>

[!code-csharp[AssignRefReturn](../../../samples/snippets/csharp/new-in-7/program.cs#24_AssignRefReturn "Assign ref return")]

<span data-ttu-id="96b8f-282">現在，在上述範例中的第二個 `WriteLine` 陳述式會印出值 `24`，表示已修改矩陣中的儲存體。</span><span class="sxs-lookup"><span data-stu-id="96b8f-282">Now, the second `WriteLine` statement in the example above will print out the value `24`, indicating that the storage in the matrix has been modified.</span></span> <span data-ttu-id="96b8f-283">區域變數已使用 `ref` 修飾詞宣告，而且它需要 `ref` 傳回。</span><span class="sxs-lookup"><span data-stu-id="96b8f-283">The local variable has been declared with the `ref` modifier, and it will take a `ref` return.</span></span> <span data-ttu-id="96b8f-284">您必須在宣告 `ref` 變數時先初始化，您無法分割宣告和初始化。</span><span class="sxs-lookup"><span data-stu-id="96b8f-284">You must initialize a `ref` variable when it is declared, you cannot split the declaration and the initialization.</span></span>

<span data-ttu-id="96b8f-285">C# 語言有三個其他的規則可保護您免於濫用 `ref` 區域變數和傳回值︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-285">The C# language has three other rules that protect you from misusing the `ref` locals and returns:</span></span>

* <span data-ttu-id="96b8f-286">您無法將標準方法傳回值指派到 `ref` 區域變數。</span><span class="sxs-lookup"><span data-stu-id="96b8f-286">You cannot assign a standard method return value to a `ref` local variable.</span></span>
    - <span data-ttu-id="96b8f-287">這可杜絕類似 `ref int i = sequence.Count();` 的陳述式</span><span class="sxs-lookup"><span data-stu-id="96b8f-287">That disallows statements like `ref int i = sequence.Count();`</span></span>
* <span data-ttu-id="96b8f-288">您不能傳回 `ref` 給變數，而該變數存留期不超過方法的執行。</span><span class="sxs-lookup"><span data-stu-id="96b8f-288">You cannot return a `ref` to a variable whose lifetime does not extend beyond the execution of the method.</span></span>
    - <span data-ttu-id="96b8f-289">這表示您無法將參考傳回區域變數或類似範圍的變數。</span><span class="sxs-lookup"><span data-stu-id="96b8f-289">That means you cannot return a reference to a local variable or a variable with a similar scope.</span></span>
* <span data-ttu-id="96b8f-290">`ref` 區域變數及傳回值無法配合非同步方法使用。</span><span class="sxs-lookup"><span data-stu-id="96b8f-290">`ref` locals and returns can't be used with async methods.</span></span>
    - <span data-ttu-id="96b8f-291">當非同步方法傳回時，編譯器無法確定參考的變數是否已設定為其最終的值。</span><span class="sxs-lookup"><span data-stu-id="96b8f-291">The compiler can't know if the referenced variable has been set to its final value when the async method returns.</span></span>

<span data-ttu-id="96b8f-292">新增 ref 區域變數和 ref 傳回能啟用更有效率的演算法，因為可以避免複製值，或是多次執行取值作業。</span><span class="sxs-lookup"><span data-stu-id="96b8f-292">The addition of ref locals and ref returns enable algorithms that are more efficient by avoiding copying values, or performing dereferencing operations multiple times.</span></span> 

## <a name="local-functions"></a><span data-ttu-id="96b8f-293">區域函式</span><span class="sxs-lookup"><span data-stu-id="96b8f-293">Local functions</span></span>

<span data-ttu-id="96b8f-294">類別的許多設計都包括從唯一一個位置呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="96b8f-294">Many designs for classes include methods that are called from only one location.</span></span> <span data-ttu-id="96b8f-295">這些額外的私用方法會使每一種方法維持小而聚焦。</span><span class="sxs-lookup"><span data-stu-id="96b8f-295">These additional private methods keep each method small and focused.</span></span> <span data-ttu-id="96b8f-296">然而，它們可能使得在第一次閱讀時更難了解類別。</span><span class="sxs-lookup"><span data-stu-id="96b8f-296">However, they can make it harder to understand a class when reading it the first time.</span></span> <span data-ttu-id="96b8f-297">您必須在單一呼叫位置的內容之外了解這些方法。</span><span class="sxs-lookup"><span data-stu-id="96b8f-297">These methods must be understood outside of the context of the single calling location.</span></span>

<span data-ttu-id="96b8f-298">對於這些設計，「區域函式」可讓您在另個方法的內容中宣告方法。</span><span class="sxs-lookup"><span data-stu-id="96b8f-298">For those designs, *local functions* enable you to declare methods inside the context of another method.</span></span> <span data-ttu-id="96b8f-299">這使得類別的讀者比較容易看到區域方法只會從它宣告之處的內容呼叫。</span><span class="sxs-lookup"><span data-stu-id="96b8f-299">This makes it easier for readers of the class to see that the local method is only called from the context in which is it declared.</span></span>

<span data-ttu-id="96b8f-300">有兩個很常見的區域函式使用案例︰公用 Iterator 方法和公用非同步方法。</span><span class="sxs-lookup"><span data-stu-id="96b8f-300">There are two very common use cases for local functions: public iterator methods and public async methods.</span></span> <span data-ttu-id="96b8f-301">這兩種方法都會產生程式碼，比程式設計人員想像更晚才報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="96b8f-301">Both types of methods generate code that reports errors later than programmers might expect.</span></span> <span data-ttu-id="96b8f-302">在 Iterator 方法的情況下，任何例外狀況只會在呼叫列舉傳回序列的程式碼時觀察到。</span><span class="sxs-lookup"><span data-stu-id="96b8f-302">In the case of iterator methods, any exceptions are observed only when calling code that enumerates the returned sequence.</span></span> <span data-ttu-id="96b8f-303">若是非同步方法，任何例外狀況只會在傳回的 `Task` 等候時觀察到。</span><span class="sxs-lookup"><span data-stu-id="96b8f-303">In the case of async methods, any exceptions are only observed when the returned `Task` is awaited.</span></span>

<span data-ttu-id="96b8f-304">讓我們從 Iterator 方法開始︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-304">Let's start with an iterator method:</span></span>

[!code-csharp[IteratorMethod](../../../samples/snippets/csharp/new-in-7/Iterator.cs#25_IteratorMethod "Iterator method")]

<span data-ttu-id="96b8f-305">檢查不正確地呼叫 Iterator 方法的下列程式碼︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-305">Examine the code below that calls the iterator method incorrectly:</span></span>

[!code-csharp[CallIteratorMethod](../../../samples/snippets/csharp/new-in-7/program.cs#26_CallIteratorMethod "Call iterator method")]

<span data-ttu-id="96b8f-306">`resultSet` 反覆執行時會擲回例外狀況，而不是在建立 `resultSet` 時。</span><span class="sxs-lookup"><span data-stu-id="96b8f-306">The exception is thrown when `resultSet` is iterated, not when `resultSet` is created.</span></span>
<span data-ttu-id="96b8f-307">在這個包含的範例中，大部分開發人員可以快速地診斷問題。</span><span class="sxs-lookup"><span data-stu-id="96b8f-307">In this contained example, most developers could quickly diagnose the problem.</span></span> <span data-ttu-id="96b8f-308">不過，在較大的程式碼基底中，建立迭代器的程式碼經常不那麼接近列舉結果的程式碼。</span><span class="sxs-lookup"><span data-stu-id="96b8f-308">However, in larger codebases, the code that creates an iterator often isn't as close to the code that enumerates the result.</span></span> <span data-ttu-id="96b8f-309">您可以重構程式碼，使公用方法驗證所有引數，而私用方法則產生列舉︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-309">You can refactor the code so that the public method validates all arguments, and a private method generates the enumeration:</span></span>

[!code-csharp[IteratorMethodRefactored](../../../samples/snippets/csharp/new-in-7/Iterator.cs#27_IteratorMethodRefactored "Iterator method refactored")]

<span data-ttu-id="96b8f-310">這個重構的版本會立即擲回例外狀況，因為公用方法不是 Iterator 方法。只有私用方法會使用 `yield return` 語法。</span><span class="sxs-lookup"><span data-stu-id="96b8f-310">This refactored version will throw exceptions immediately because the public method is not an iterator method; only the private method uses the `yield return` syntax.</span></span> <span data-ttu-id="96b8f-311">不過，這項重構功能有潛在問題。</span><span class="sxs-lookup"><span data-stu-id="96b8f-311">However, there are potential problems with this refactoring.</span></span> <span data-ttu-id="96b8f-312">私用方法應該只從公用介面方法呼叫，因為否則會略過所有引數的驗證。</span><span class="sxs-lookup"><span data-stu-id="96b8f-312">The private method should only be called from the public interface method, because otherwise all argument validation is skipped.</span></span>
<span data-ttu-id="96b8f-313">類別的讀者必須閱讀整個類別，並尋找對 `alphabetSubsetImplementation` 方法的任何其他參考，以探索這項事實。</span><span class="sxs-lookup"><span data-stu-id="96b8f-313">Readers of the class must discover this fact by reading the entire class and searching for any other references to the `alphabetSubsetImplementation` method.</span></span>

<span data-ttu-id="96b8f-314">您可以藉由宣告 `alphabetSubsetImplementation` 為公用 API 方法內的區域函式，讓該項設計目的更清楚︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-314">You can make that design intent more clear by declaring the `alphabetSubsetImplementation` as a local function inside the public API method:</span></span>

[!code-csharp[22_IteratorMethodLocal](../../../samples/snippets/csharp/new-in-7/Iterator.cs#28_IteratorMethodLocal "Iterator method with local function")]

<span data-ttu-id="96b8f-315">上述的版本已闡明區域方法只會在外部方法的內容中參考。</span><span class="sxs-lookup"><span data-stu-id="96b8f-315">The version above makes it clear that the local method is referenced only in the context of the outer method.</span></span> <span data-ttu-id="96b8f-316">區域函式的規則也確保開發人員無法意外從類別中的另一個位置呼叫區域函式，並略過引數的驗證。</span><span class="sxs-lookup"><span data-stu-id="96b8f-316">The rules for local functions also ensure that a developer can't accidentally call the local function from another location in the class and bypass the argument validation.</span></span>

<span data-ttu-id="96b8f-317">相同的技巧也可以運用在 `async` 方法，以確保在非同步工作開始之前，會擲回引數驗證所引發的例外狀況︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-317">The same technique can be employed with `async` methods to ensure that exceptions arising from argument validation are thrown before the asynchronous work begins:</span></span>

[!code-csharp[TaskExample](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]

> [!NOTE]
> <span data-ttu-id="96b8f-318">區域函式支援的部分設計也可以使用「Lambda 運算式」完成。</span><span class="sxs-lookup"><span data-stu-id="96b8f-318">Some of the designs that are supported by local functions could also be accomplished using *lambda expressions*.</span></span> <span data-ttu-id="96b8f-319">有興趣的人可以[進一步了解差異](../local-functions-vs-lambdas.md)</span><span class="sxs-lookup"><span data-stu-id="96b8f-319">Those interested can [read more about the differences](../local-functions-vs-lambdas.md)</span></span>

## <a name="more-expression-bodied-members"></a><span data-ttu-id="96b8f-320">更多運算式主體成員</span><span class="sxs-lookup"><span data-stu-id="96b8f-320">More expression-bodied members</span></span>

<span data-ttu-id="96b8f-321">C# 6 引進了成員函式的[運算式主體成員](csharp-6.md#expression-bodied-function-members)和唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="96b8f-321">C# 6 introduced [expression-bodied members](csharp-6.md#expression-bodied-function-members) for member functions, and read-only properties.</span></span> <span data-ttu-id="96b8f-322">C# 7 展開了可以實作為運算式的允許成員。</span><span class="sxs-lookup"><span data-stu-id="96b8f-322">C# 7 expands the allowed members that can be implemented as expressions.</span></span> <span data-ttu-id="96b8f-323">在 C# 7 中，您可以實作「建構函式」、「完成項」，以及「屬性」和「索引子」上的 `get` 和 `set` 存取子。</span><span class="sxs-lookup"><span data-stu-id="96b8f-323">In C# 7, you can implement *constructors*, *finalizers*, and `get` and `set` accessors on *properties* and *indexers*.</span></span> <span data-ttu-id="96b8f-324">下列程式碼將示範各項的範例：</span><span class="sxs-lookup"><span data-stu-id="96b8f-324">The following code shows examples of each:</span></span>

[!code-csharp[ExpressionBodiedMembers](../../../samples/snippets/csharp/new-in-7/expressionmembers.cs#36_ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> <span data-ttu-id="96b8f-325">這個範例不需要完成項，但仍加以顯示以示範語法。</span><span class="sxs-lookup"><span data-stu-id="96b8f-325">This example does not need a finalizer, but it is shown to demonstrate the syntax.</span></span> <span data-ttu-id="96b8f-326">除非為釋放 Unmanaged 資源所需，否則不應該在類別中實作完成項。</span><span class="sxs-lookup"><span data-stu-id="96b8f-326">You should not implement a finalizer in your class unless it is necessary to  release unmanaged resources.</span></span> <span data-ttu-id="96b8f-327">您也應該考慮使用 <xref:System.Runtime.InteropServices.SafeHandle> 類別而不是直接管理 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="96b8f-327">You should also consider using the <xref:System.Runtime.InteropServices.SafeHandle> class instead of managing unmanaged resources directly.</span></span>

<span data-ttu-id="96b8f-328">這些運算式主體成員的新位置代表 C# 語言的重要里程碑︰這些功能是由參與開放原始碼 [Roslyn](https://github.com/dotnet/Roslyn) 專案的社群成員所實作。</span><span class="sxs-lookup"><span data-stu-id="96b8f-328">These new locations for expression-bodied members represent an important milestone for the C# language: These features were implemented by community members working on the open-source [Roslyn](https://github.com/dotnet/Roslyn) project.</span></span>

## <a name="throw-expressions"></a><span data-ttu-id="96b8f-329">throw 運算式</span><span class="sxs-lookup"><span data-stu-id="96b8f-329">Throw expressions</span></span>

<span data-ttu-id="96b8f-330">在 C# 中，`throw` 一直都是陳述式。</span><span class="sxs-lookup"><span data-stu-id="96b8f-330">In C#, `throw` has always been a statement.</span></span> <span data-ttu-id="96b8f-331">因為 `throw` 是陳述式，而不是運算式，所以有您無法在其中使用它的 C# 建構。</span><span class="sxs-lookup"><span data-stu-id="96b8f-331">Because `throw` is a statement, not an expression, there were C# constructs where you could not use it.</span></span> <span data-ttu-id="96b8f-332">這些包含條件運算式、Null 聯合運算式和一些 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="96b8f-332">These included conditional expressions, null coalescing expressions, and some lambda expressions.</span></span> <span data-ttu-id="96b8f-333">新增運算式主體成員會新增 `throw` 運算式適用的更多位置。</span><span class="sxs-lookup"><span data-stu-id="96b8f-333">The addition of expression-bodied members adds more locations where `throw` expressions would be useful.</span></span> <span data-ttu-id="96b8f-334">為了讓您可以撰寫任何這些建構，C# 7 引進了「Throw 運算式」。</span><span class="sxs-lookup"><span data-stu-id="96b8f-334">So that you can write any of these constructs, C# 7 introduces *throw expressions*.</span></span>

<span data-ttu-id="96b8f-335">語法與您一直用於 `throw` 陳述式的語法相同。</span><span class="sxs-lookup"><span data-stu-id="96b8f-335">The syntax is the same as you've always used for `throw` statements.</span></span> <span data-ttu-id="96b8f-336">唯一的差別在於現在您可以將它們放在新位置，例如在條件運算式中︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-336">The only difference is that now you can place them in new locations, such as in a conditional expression:</span></span>

[!code-csharp[Throw_ExpressionExample](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#37_Throw_ExpressionExample "conditional throw expressions")]

<span data-ttu-id="96b8f-337">此功能可讓您在初始化運算式中使用 throw 運算式︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-337">This features enables using throw expressions in initialization expressions:</span></span>

[!code-csharp[ThrowInInitialization](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#38_ThrowInInitialization "conditional throw expressions")]

<span data-ttu-id="96b8f-338">過去，這些初始設定需要在建構函式中，且 throw 陳述式在建構函式主體中︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-338">Previously, those initializations would need to be in a constructor, with the throw statements in the body of the constructor:</span></span>


[!code-csharp[ThrowInConstructor](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#39_ThrowInConstructor "throw statements")]

> [!NOTE]
> <span data-ttu-id="96b8f-339">上述兩個建構會造成在物件建構期間擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="96b8f-339">Both of the preceding constructs will cause exceptions to be thrown during the construction of an object.</span></span> <span data-ttu-id="96b8f-340">這些通常很難復原。</span><span class="sxs-lookup"><span data-stu-id="96b8f-340">Those are often difficult to recover from.</span></span>
> <span data-ttu-id="96b8f-341">因此，不建議使用會在建構期間擲回例外狀況的設計。</span><span class="sxs-lookup"><span data-stu-id="96b8f-341">For that reason, designs that throw exceptions during construction are discouraged.</span></span>

## <a name="generalized-async-return-types"></a><span data-ttu-id="96b8f-342">通用的非同步傳回型別</span><span class="sxs-lookup"><span data-stu-id="96b8f-342">Generalized async return types</span></span>

<span data-ttu-id="96b8f-343">從非同步方法傳回 `Task` 物件可能會造成在特定路徑的效能瓶頸。</span><span class="sxs-lookup"><span data-stu-id="96b8f-343">Returning a `Task` object from async methods can introduce performance bottlenecks in certain paths.</span></span> <span data-ttu-id="96b8f-344">`Task` 是參考型別，因此使用它表示要配置物件。</span><span class="sxs-lookup"><span data-stu-id="96b8f-344">`Task` is a reference type, so using it means allocating an object.</span></span> <span data-ttu-id="96b8f-345">當使用 `async` 修飾詞宣告的方法傳回快取的結果時，或是以同步方式完成，額外配置可能會在效能關鍵的程式碼區段中變成一項重要的時間成本。</span><span class="sxs-lookup"><span data-stu-id="96b8f-345">In cases where a method declared with the `async` modifier returns a cached result, or completes synchronously, the extra allocations can become a significant time cost in performance critical sections of code.</span></span> <span data-ttu-id="96b8f-346">如果這些配置發生在緊密迴圈中的話，它可能會變得成本很高。</span><span class="sxs-lookup"><span data-stu-id="96b8f-346">It can become very costly if those allocations occur in tight loops.</span></span>

<span data-ttu-id="96b8f-347">新語言功能表示非同步方法除了 `Task`、`Task<T>` 和 `void` 之外，可能還會傳回其他型別。</span><span class="sxs-lookup"><span data-stu-id="96b8f-347">The new language feature means that async methods may return other types in addition to `Task`, `Task<T>` and `void`.</span></span> <span data-ttu-id="96b8f-348">傳回的型別仍然必須滿足非同步模式，也就是表示 `GetAwaiter` 方法必須可存取。</span><span class="sxs-lookup"><span data-stu-id="96b8f-348">The returned type must still satisfy the async pattern, meaning a `GetAwaiter` method must be accessible.</span></span> <span data-ttu-id="96b8f-349">具體的範例就是，`ValueTask` 類型已新增到 .NET Framework，才便利用這項新的語言功能︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-349">As one concrete example, the `ValueTask` type has been added to the .NET framework to make use of this new language feature:</span></span> 

[!code-csharp[UsingValueTask](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#30_UsingValueTask "Using ValueTask")]

> [!NOTE]
> <span data-ttu-id="96b8f-350">您必須新增 NuGet 套件 [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/)，才可使用 <xref:System.Threading.Tasks.ValueTask%601> 類型。</span><span class="sxs-lookup"><span data-stu-id="96b8f-350">You need to add the NuGet package [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) in order to use the <xref:System.Threading.Tasks.ValueTask%601> type.</span></span>

<span data-ttu-id="96b8f-351">簡單的最佳化就是使用 `ValueTask` 取代過去使用 `Task` 之處。</span><span class="sxs-lookup"><span data-stu-id="96b8f-351">A simple optimization would be to use `ValueTask` in places where `Task` would be used before.</span></span> <span data-ttu-id="96b8f-352">不過，如果您想要以手動方式執行額外的最佳化，可以快取來自非同步工作的結果，並在後續的呼叫中重複使用結果。</span><span class="sxs-lookup"><span data-stu-id="96b8f-352">However, if you want to perform extra optimizations by hand, you can cache results from async work and reuse the result in subsequent calls.</span></span> <span data-ttu-id="96b8f-353">`ValueTask` 結構有一個具有 `Task` 參數的建構函式，讓您可以從任何現有非同步方法的傳回值來建構 `ValueTask`︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-353">The `ValueTask` struct has a constructor with a `Task` parameter so that you can construct a `ValueTask` from the return value of any existing async method:</span></span>

[!code-csharp[AsyncOptimizedValueTask](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#31_AsyncOptimizedValueTask "Return async result or cached value")]
 
<span data-ttu-id="96b8f-354">如同所有的效能建議，您應該先評定這兩個版本，再進行大規模的程式碼變更。</span><span class="sxs-lookup"><span data-stu-id="96b8f-354">As with all performance recommendations, you should benchmark both versions before making large scale changes to your code.</span></span>

## <a name="numeric-literal-syntax-improvements"></a><span data-ttu-id="96b8f-355">數值常值的語法增強功能</span><span class="sxs-lookup"><span data-stu-id="96b8f-355">Numeric literal syntax improvements</span></span>

<span data-ttu-id="96b8f-356">錯譯數值常數，可能會使得在第一次閱讀它時，更加難以了解程式碼。</span><span class="sxs-lookup"><span data-stu-id="96b8f-356">Misreading numeric constants can make it harder to understand code when reading it for the first time.</span></span> <span data-ttu-id="96b8f-357">這通常發生於那些數字用作位元遮罩或其他符號而不是數字值的時候。</span><span class="sxs-lookup"><span data-stu-id="96b8f-357">This often occurs when those numbers are used as bit masks or other symbolic rather than numeric values.</span></span> <span data-ttu-id="96b8f-358">C# 7 包含兩項新功能，可以更輕鬆地以預期用途最容易閱讀的方式來撰寫數字︰「二進位常值」和「數字分隔符號」。</span><span class="sxs-lookup"><span data-stu-id="96b8f-358">C# 7 includes two new features to make it easier to write numbers in the most readable fashion for the intended use: *binary literals*, and *digit separators*.</span></span>

<span data-ttu-id="96b8f-359">當您在建立位元遮罩時，或是每當數字的二進位表示法構成最容易閱讀的程式碼時，請以二進位撰寫該數字︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-359">For those times when you are creating bit masks, or whenever a binary representation of a number makes the most readable code, write that number in binary:</span></span>

[!code-csharp[BinaryConstants](../../../samples/snippets/csharp/new-in-7/Program.cs#32_BinaryConstants "Binary constants")]

<span data-ttu-id="96b8f-360">常數開頭的 `0b` 表示數字是撰寫為二進位數字。</span><span class="sxs-lookup"><span data-stu-id="96b8f-360">The `0b` at the beginning of the constant indicates that the number is written as a binary number.</span></span>

<span data-ttu-id="96b8f-361">二進位數字可能會很長，因此引進 `_` 作為千位分隔符號通常能夠更輕鬆地查看位元模式︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-361">Binary numbers can get very long, so it's often easier to see the bit patterns by introducing the `_` as a digit separator:</span></span>

[!code-csharp[ThousandSeparators](../../../samples/snippets/csharp/new-in-7/Program.cs#33_ThousandSeparators "Thousands separators")]

<span data-ttu-id="96b8f-362">千位分隔符號可以出現在常數的任何位置。</span><span class="sxs-lookup"><span data-stu-id="96b8f-362">The digit separator can appear anywhere in the constant.</span></span> <span data-ttu-id="96b8f-363">對於以 10 為底的數字，通常會使用它作為千位分隔符號︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-363">For base 10 numbers, it would be common to use it as a thousands separator:</span></span>

[!code-csharp[LargeIntegers](../../../samples/snippets/csharp/new-in-7/Program.cs#34_LargeIntegers "Large integer")]

<span data-ttu-id="96b8f-364">千位分隔符號也可以搭配 `decimal`、`float` 和 `double` 類型︰</span><span class="sxs-lookup"><span data-stu-id="96b8f-364">The digit separator can be used with `decimal`, `float` and `double` types as well:</span></span>

[!code-csharp[OtherConstants](../../../samples/snippets/csharp/new-in-7/Program.cs#35_OtherConstants "non-integral constants")]

<span data-ttu-id="96b8f-365">結合起來，您在宣告數值常數時可以有更多的可讀性。</span><span class="sxs-lookup"><span data-stu-id="96b8f-365">Taken together, you can declare numeric constants with much more readability.</span></span>
