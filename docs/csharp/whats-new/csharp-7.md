---
title: C# 7.0 的新功能 - C# 指南
description: 取得 C# 語言版本 7.0 中新功能的概觀。
ms.date: 02/20/2019
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: 81d06d2e2079e04948ad5e93eefadb1bc11d855a
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654181"
---
# <a name="whats-new-in-c-70"></a><span data-ttu-id="111c2-103">C# 7.0 的新功能</span><span class="sxs-lookup"><span data-stu-id="111c2-103">What's new in C# 7.0</span></span>

<span data-ttu-id="111c2-104">C# 7.0 新增許多新功能至 C# 語言：</span><span class="sxs-lookup"><span data-stu-id="111c2-104">C# 7.0 adds a number of new features to the C# language:</span></span>
* [<span data-ttu-id="111c2-105">`out` 變數</span><span class="sxs-lookup"><span data-stu-id="111c2-105">`out` variables</span></span>](#out-variables)
    - <span data-ttu-id="111c2-106">您可以宣告 `out` 內嵌值作為使用它們之方法的引數。</span><span class="sxs-lookup"><span data-stu-id="111c2-106">You can declare `out` values inline as arguments to the method where they're used.</span></span>
* [<span data-ttu-id="111c2-107">元組</span><span class="sxs-lookup"><span data-stu-id="111c2-107">Tuples</span></span>](#tuples)
    - <span data-ttu-id="111c2-108">您可以建立包含多個公用欄位的輕量、未具名的類型。</span><span class="sxs-lookup"><span data-stu-id="111c2-108">You can create lightweight, unnamed types that contain multiple public fields.</span></span> <span data-ttu-id="111c2-109">編譯器和 IDE 工具了解這些類型的語意。</span><span class="sxs-lookup"><span data-stu-id="111c2-109">Compilers and IDE tools understand the semantics of these types.</span></span>
* [<span data-ttu-id="111c2-110">捨棄</span><span class="sxs-lookup"><span data-stu-id="111c2-110">Discards</span></span>](#discards)
    - <span data-ttu-id="111c2-111">捨棄是當您不在意指派的值時，於指派內使用的僅限寫入且暫時之變數。</span><span class="sxs-lookup"><span data-stu-id="111c2-111">Discards are temporary, write-only variables used in assignments when you don't care about the value assigned.</span></span> <span data-ttu-id="111c2-112">解構 Tuple 及使用者定義型別，以及使用 `out` 參數呼叫方法時，捨棄最為實用。</span><span class="sxs-lookup"><span data-stu-id="111c2-112">They're most useful when deconstructing tuples and user-defined types, as well as when calling methods with `out` parameters.</span></span>
* [<span data-ttu-id="111c2-113">模式比對</span><span class="sxs-lookup"><span data-stu-id="111c2-113">Pattern Matching</span></span>](#pattern-matching)
    - <span data-ttu-id="111c2-114">您可以建立以任意類型和這些類型成員的值為基礎的分支邏輯。</span><span class="sxs-lookup"><span data-stu-id="111c2-114">You can create branching logic based on arbitrary types and values of the members of those types.</span></span>
* [<span data-ttu-id="111c2-115">`ref` 區域變數和傳回</span><span class="sxs-lookup"><span data-stu-id="111c2-115">`ref` locals and returns</span></span>](#ref-locals-and-returns)
    - <span data-ttu-id="111c2-116">方法區域變數和傳回值可以是其他儲存體的參考。</span><span class="sxs-lookup"><span data-stu-id="111c2-116">Method local variables and return values can be references to other storage.</span></span>
* [<span data-ttu-id="111c2-117">區域函式</span><span class="sxs-lookup"><span data-stu-id="111c2-117">Local Functions</span></span>](#local-functions)
    - <span data-ttu-id="111c2-118">您可以將函式巢狀放置在其他函式內，限制其範圍和可視性。</span><span class="sxs-lookup"><span data-stu-id="111c2-118">You can nest functions inside other functions to limit their scope and visibility.</span></span>
* [<span data-ttu-id="111c2-119">更多運算式主體成員</span><span class="sxs-lookup"><span data-stu-id="111c2-119">More expression-bodied members</span></span>](#more-expression-bodied-members)
    - <span data-ttu-id="111c2-120">可以使用運算式來撰寫的成員清單已經增長。</span><span class="sxs-lookup"><span data-stu-id="111c2-120">The list of members that can be authored using expressions has grown.</span></span>
* [<span data-ttu-id="111c2-121">`throw`運算式</span><span class="sxs-lookup"><span data-stu-id="111c2-121">`throw` Expressions</span></span>](#throw-expressions)
    - <span data-ttu-id="111c2-122">您可以在程式碼建構中擲回例外狀況 (因為先前 `throw` 是陳述式，所以您無法這麼做)。</span><span class="sxs-lookup"><span data-stu-id="111c2-122">You can throw exceptions in code constructs that previously weren't allowed because `throw` was a statement.</span></span> 
* [<span data-ttu-id="111c2-123">通用的非同步傳回型別</span><span class="sxs-lookup"><span data-stu-id="111c2-123">Generalized async return types</span></span>](#generalized-async-return-types)
    - <span data-ttu-id="111c2-124">使用 `async` 修飾詞宣告的方法除了 `Task` 和 `Task<T>` 之外，也能傳回其他類型。</span><span class="sxs-lookup"><span data-stu-id="111c2-124">Methods declared with the `async` modifier can return other types in addition to `Task` and `Task<T>`.</span></span>
* [<span data-ttu-id="111c2-125">數值常值語法增強功能</span><span class="sxs-lookup"><span data-stu-id="111c2-125">Numeric literal syntax improvements</span></span>](#numeric-literal-syntax-improvements)
    - <span data-ttu-id="111c2-126">新的語彙基元改善了數值常數的可讀性。</span><span class="sxs-lookup"><span data-stu-id="111c2-126">New tokens improve readability for numeric constants.</span></span>

<span data-ttu-id="111c2-127">此文章的其餘部分將概述各個功能。</span><span class="sxs-lookup"><span data-stu-id="111c2-127">The remainder of this article provides an overview of each feature.</span></span> <span data-ttu-id="111c2-128">您將了解每項功能背後的原因。</span><span class="sxs-lookup"><span data-stu-id="111c2-128">For each feature, you'll learn the reasoning behind it.</span></span> <span data-ttu-id="111c2-129">您將了解語法。</span><span class="sxs-lookup"><span data-stu-id="111c2-129">You'll learn the syntax.</span></span> <span data-ttu-id="111c2-130">您可以在這些功能的[互動式探索](../tutorials/exploration/csharp-7.yml)中探索這些功能。</span><span class="sxs-lookup"><span data-stu-id="111c2-130">You can explore these features in our [interactive exploration](../tutorials/exploration/csharp-7.yml) of these features.</span></span>

## <a name="out-variables"></a><span data-ttu-id="111c2-131">`out` 變數</span><span class="sxs-lookup"><span data-stu-id="111c2-131">`out` variables</span></span>

<span data-ttu-id="111c2-132">在這個版本中，支援 `out` 參數的現有語法已經過改善。</span><span class="sxs-lookup"><span data-stu-id="111c2-132">The existing syntax that supports `out` parameters has been improved in this version.</span></span> <span data-ttu-id="111c2-133">您現在可以在方法呼叫的引數清單中宣告 `out` 變數，而不是撰寫個別的宣告陳述式︰</span><span class="sxs-lookup"><span data-stu-id="111c2-133">You can now declare `out` variables in the argument list of a method call, rather than writing a separate declaration statement:</span></span>

[!code-csharp[OutVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVariableDeclarations "Out variable declarations")]

<span data-ttu-id="111c2-134">為了清楚起見，您可能想要指定 `out` 變數的類型，如上所示。</span><span class="sxs-lookup"><span data-stu-id="111c2-134">You may want to specify the type of the `out` variable for clarity, as shown above.</span></span> <span data-ttu-id="111c2-135">不過，語言有支援使用隱含型別區域變數︰</span><span class="sxs-lookup"><span data-stu-id="111c2-135">However, the language does support using an implicitly typed local variable:</span></span>

[!code-csharp[OutVarVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVarVariableDeclarations "Implicitly typed Out variable")]

* <span data-ttu-id="111c2-136">程式碼更容易閱讀與理解。</span><span class="sxs-lookup"><span data-stu-id="111c2-136">The code is easier to read.</span></span> 
    - <span data-ttu-id="111c2-137">您在使用之處宣告 out 變數，而不是在上方另一行。</span><span class="sxs-lookup"><span data-stu-id="111c2-137">You declare the out variable where you use it, not on another line above.</span></span>
* <span data-ttu-id="111c2-138">不需要指派初始值。</span><span class="sxs-lookup"><span data-stu-id="111c2-138">No need to assign an initial value.</span></span>
    - <span data-ttu-id="111c2-139">藉由在方法呼叫中使用所在宣告 `out` 變數，就不會在指派它之前意外使用它。</span><span class="sxs-lookup"><span data-stu-id="111c2-139">By declaring the `out` variable where it's used in a method call, you can't accidentally use it before it is assigned.</span></span>

## <a name="tuples"></a><span data-ttu-id="111c2-140">Tuple</span><span class="sxs-lookup"><span data-stu-id="111c2-140">Tuples</span></span>

<span data-ttu-id="111c2-141">C# 為類別和結構提供豐富的語法，可用來解釋您的設計目的。</span><span class="sxs-lookup"><span data-stu-id="111c2-141">C# provides a rich syntax for classes and structs that is used to explain your design intent.</span></span> <span data-ttu-id="111c2-142">但有時候豐富的語法需要額外的工作才能得到最少的好處。</span><span class="sxs-lookup"><span data-stu-id="111c2-142">But sometimes that rich syntax requires extra work with minimal benefit.</span></span> <span data-ttu-id="111c2-143">您可能經常撰寫需要包含多個資料項目之簡單結構的方法。</span><span class="sxs-lookup"><span data-stu-id="111c2-143">You may often write methods that need a simple structure containing more than one data element.</span></span> <span data-ttu-id="111c2-144">為了支援這些案例，C# 已新增 *Tuple*。</span><span class="sxs-lookup"><span data-stu-id="111c2-144">To support these scenarios *tuples* were added to C#.</span></span> <span data-ttu-id="111c2-145">Tuple 是輕量的資料結構，其中包含多個欄位來代表資料成員。</span><span class="sxs-lookup"><span data-stu-id="111c2-145">Tuples are lightweight data structures that contain multiple fields to represent the data members.</span></span>
<span data-ttu-id="111c2-146">這些欄位不會經過驗證，且您無法定義自己的方法</span><span class="sxs-lookup"><span data-stu-id="111c2-146">The fields aren't validated, and you can't define your own methods</span></span>

> [!NOTE]
> <span data-ttu-id="111c2-147">Tuple 在 C# 7.0 之前即可使用，但效率不彰且沒有語言支援。</span><span class="sxs-lookup"><span data-stu-id="111c2-147">Tuples were available before C# 7.0, but they were inefficient and had no language support.</span></span>
> <span data-ttu-id="111c2-148">這表示元組元素只能參考為 `Item1`及 `Item2` 等等。</span><span class="sxs-lookup"><span data-stu-id="111c2-148">This meant that tuple elements could only be referenced as `Item1`, `Item2` and so on.</span></span> <span data-ttu-id="111c2-149">C# 7.0 加入了 Tuple 的語言支援，讓 Tuple 欄位的語意名稱能使用全新且更具效率的 Tuple 型別。</span><span class="sxs-lookup"><span data-stu-id="111c2-149">C# 7.0 introduces language support for tuples, which enables semantic names for the fields of a tuple using new, more efficient tuple types.</span></span>

<span data-ttu-id="111c2-150">您可以將值指派給每個成員，並選擇性地提供語意名稱給每個 Tuple 的成員，以建立 Tuple：</span><span class="sxs-lookup"><span data-stu-id="111c2-150">You can create a tuple by assigning a value to each member, and optionally providing semantic names to each of the members of the tuple:</span></span>

[!code-csharp[NamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#NamedTuple "Named tuple")]

<span data-ttu-id="111c2-151">`namedLetters` Tuple 包含稱為 `Alpha` 和 `Beta` 的欄位。</span><span class="sxs-lookup"><span data-stu-id="111c2-151">The `namedLetters` tuple contains fields referred to as `Alpha` and `Beta`.</span></span> <span data-ttu-id="111c2-152">這些名稱只會在編譯時間存在而不會保留 (例如，在執行階段使用反映調查 Tuple 時)。</span><span class="sxs-lookup"><span data-stu-id="111c2-152">Those names exist only at compile time and aren't preserved, for example when inspecting the tuple using reflection at runtime.</span></span>

<span data-ttu-id="111c2-153">在 Tuple 指派中，您也可以在指派的右邊，指定欄位的名稱︰</span><span class="sxs-lookup"><span data-stu-id="111c2-153">In a tuple assignment, you can also specify the names of the fields on the right-hand side of the assignment:</span></span>

[!code-csharp[ImplicitNamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#ImplicitNamedTuple "Implicitly named tuple")]

<span data-ttu-id="111c2-154">有時候您可能會想要解除封裝已從方法傳回的 Tuple 成員。</span><span class="sxs-lookup"><span data-stu-id="111c2-154">There may be times when you want to unpackage the members of a tuple that were returned from a method.</span></span>  <span data-ttu-id="111c2-155">您可以藉由為 Tuple 中的每個值宣告不同變數來這麼做。</span><span class="sxs-lookup"><span data-stu-id="111c2-155">You can do that by declaring separate variables for each of the values in the tuple.</span></span> <span data-ttu-id="111c2-156">這種解除封裝稱為*解構* Tuple：</span><span class="sxs-lookup"><span data-stu-id="111c2-156">This unpackaging is called *deconstructing* the tuple:</span></span>

[!code-csharp[CallingWithDeconstructor](~/samples/snippets/csharp/new-in-7/program.cs#CallingWithDeconstructor "Deconstructing a tuple")]

<span data-ttu-id="111c2-157">您也可以在 .NET 中為任何類型提供類似的解構。</span><span class="sxs-lookup"><span data-stu-id="111c2-157">You can also provide a similar deconstruction for any type in .NET.</span></span> <span data-ttu-id="111c2-158">您可以將 `Deconstruct` 方法撰寫為類別的成員。</span><span class="sxs-lookup"><span data-stu-id="111c2-158">You write a `Deconstruct` method as a member of the class.</span></span> <span data-ttu-id="111c2-159">`Deconstruct` 方法為您想要擷取的每個屬性提供一組 `out` 引數。</span><span class="sxs-lookup"><span data-stu-id="111c2-159">That `Deconstruct` method provides a set of `out` arguments for each of the properties you want to extract.</span></span> <span data-ttu-id="111c2-160">請考慮這個 `Point` 類別，它會提供 deconstructor 方法，擷取 `X` 和 `Y` 座標︰</span><span class="sxs-lookup"><span data-stu-id="111c2-160">Consider this `Point` class that provides a deconstructor method that extracts the `X` and `Y` coordinates:</span></span>

[!code-csharp[PointWithDeconstruction](~/samples/snippets/csharp/new-in-7/point.cs#PointWithDeconstruction "Point with deconstruction method")]
 
<span data-ttu-id="111c2-161">您可以藉由將 `Point` 指派給 Tuple 來擷取個別的欄位：</span><span class="sxs-lookup"><span data-stu-id="111c2-161">You can extract the individual fields by assigning a `Point` to a tuple:</span></span>

[!code-csharp[DeconstructPoint](~/samples/snippets/csharp/new-in-7/program.cs#DeconstructPoint "Deconstruct a point")]

<span data-ttu-id="111c2-162">您可以在 [Tuple 文章](../tuples.md)中深入了解 Tuple。</span><span class="sxs-lookup"><span data-stu-id="111c2-162">You can learn more in depth about tuples in the [tuples article](../tuples.md).</span></span>

## <a name="discards"></a><span data-ttu-id="111c2-163">捨棄</span><span class="sxs-lookup"><span data-stu-id="111c2-163">Discards</span></span>

<span data-ttu-id="111c2-164">通常在您解構元組或以 `out` 參數呼叫方法時，會強制您要定義變數，而您無須在意變數的值也沒有使用該值的打算。</span><span class="sxs-lookup"><span data-stu-id="111c2-164">Often when deconstructing a tuple or calling a method with `out` parameters, you're forced to define a variable whose value you don't care about and don't intend to use.</span></span> <span data-ttu-id="111c2-165">C# 新增了對*捨棄*的支援，來應付這種狀況。</span><span class="sxs-lookup"><span data-stu-id="111c2-165">C# adds support for *discards* to handle this scenario.</span></span> <span data-ttu-id="111c2-166">捨棄是僅限寫入的變數，其名稱為 `_` (底線字元)；您可將所有想要捨棄的值指派到單一變數。</span><span class="sxs-lookup"><span data-stu-id="111c2-166">A discard is a write-only variable whose name is `_` (the underscore character); you can assign all of the values that you intend to discard to the single variable.</span></span> <span data-ttu-id="111c2-167">捨棄類似於未經指派的變數；和指派陳述式一樣，都不能用於程式碼中。</span><span class="sxs-lookup"><span data-stu-id="111c2-167">A discard is like an unassigned variable; apart from the assignment statement, the discard can't be used in code.</span></span>

<span data-ttu-id="111c2-168">下列情況中支援捨棄：</span><span class="sxs-lookup"><span data-stu-id="111c2-168">Discards are supported in the following scenarios:</span></span>

* <span data-ttu-id="111c2-169">解構元組或使用者定義型別時。</span><span class="sxs-lookup"><span data-stu-id="111c2-169">When deconstructing tuples or user-defined types.</span></span>
* <span data-ttu-id="111c2-170">以 [out](../language-reference/keywords/out-parameter-modifier.md) 參數呼叫方法時。</span><span class="sxs-lookup"><span data-stu-id="111c2-170">When calling methods with [out](../language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>
* <span data-ttu-id="111c2-171">執行 [is](../language-reference/keywords/is.md) 及 [switch](../language-reference/keywords/switch.md) 陳述式的模式比對作業時。</span><span class="sxs-lookup"><span data-stu-id="111c2-171">In a pattern matching operation with the [is](../language-reference/keywords/is.md) and [switch](../language-reference/keywords/switch.md) statements.</span></span>
* <span data-ttu-id="111c2-172">作為獨立識別項，當您想要將指派的值明確識別為捨棄時。</span><span class="sxs-lookup"><span data-stu-id="111c2-172">As a standalone identifier when you want to explicitly identify the value of an assignment as a discard.</span></span>

<span data-ttu-id="111c2-173">下列範例定義的 `QueryCityDataForYears` 方法，會傳回包含兩個不同年份的城市資料之 6 元組。</span><span class="sxs-lookup"><span data-stu-id="111c2-173">The following example defines a `QueryCityDataForYears` method that returns a 6-tuple that contains a data for a city for two different years.</span></span> <span data-ttu-id="111c2-174">範例中的方法呼叫只有對方法傳回的兩個母體有效，所以會在解構元組時，將元組中剩餘的值視作捨棄處理。</span><span class="sxs-lookup"><span data-stu-id="111c2-174">The method call in the example is concerned only with the two population values returned by the method and so treats the remaining values in the tuple as discards when it deconstructs the tuple.</span></span>

[!code-csharp[Tuple-discard](~/samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

<span data-ttu-id="111c2-175">如需詳細資訊，請參閱[捨棄](../discards.md)。</span><span class="sxs-lookup"><span data-stu-id="111c2-175">For more information, see [Discards](../discards.md).</span></span>

## <a name="pattern-matching"></a><span data-ttu-id="111c2-176">模式比對</span><span class="sxs-lookup"><span data-stu-id="111c2-176">Pattern matching</span></span>

<span data-ttu-id="111c2-177">「模式比對」是一項功能，可讓您對物件類型以外的屬性實作方法分派。</span><span class="sxs-lookup"><span data-stu-id="111c2-177">*Pattern matching* is a feature that allows you to implement method dispatch on properties other than the type of an object.</span></span> <span data-ttu-id="111c2-178">您可能已經熟悉根據物件類型的方法分派。</span><span class="sxs-lookup"><span data-stu-id="111c2-178">You're probably already familiar with method dispatch based on the type of an object.</span></span> <span data-ttu-id="111c2-179">在物件導向程式設計中，虛擬和覆寫方法可提供語言語法，以根據物件的類型實作方法分派。</span><span class="sxs-lookup"><span data-stu-id="111c2-179">In object-oriented programming, virtual and override methods provide language syntax to implement method dispatching based on an object's type.</span></span> <span data-ttu-id="111c2-180">基底和衍生類別能提供不同的實作。</span><span class="sxs-lookup"><span data-stu-id="111c2-180">Base and Derived classes provide different implementations.</span></span> <span data-ttu-id="111c2-181">模式比對運算式會擴充這個概念，讓您可以輕鬆地為不是透過繼承階層架構而關聯的類型和資料元素實作類似的分派模式。</span><span class="sxs-lookup"><span data-stu-id="111c2-181">Pattern matching expressions extend this concept so that you can easily implement similar dispatch patterns for types and data elements that aren't related through an inheritance hierarchy.</span></span> 

<span data-ttu-id="111c2-182">模式比對支援 `is` 運算式和 `switch` 運算式。</span><span class="sxs-lookup"><span data-stu-id="111c2-182">Pattern matching supports `is` expressions and `switch` expressions.</span></span> <span data-ttu-id="111c2-183">每個都讓您能檢查物件和其屬性，以判斷該物件是否符合搜尋的模式。</span><span class="sxs-lookup"><span data-stu-id="111c2-183">Each enables inspecting an object and its properties to determine if that object satisfies the sought pattern.</span></span> <span data-ttu-id="111c2-184">您使用 `when` 關鍵字來指定其他規則給該模式。</span><span class="sxs-lookup"><span data-stu-id="111c2-184">You use the `when` keyword to specify additional rules to the pattern.</span></span>

<span data-ttu-id="111c2-185">`is` 模式運算式會擴充熟悉的 [`is` 運算子](../language-reference/keywords/is.md#pattern-matching-with-is)，來查詢其類型的相關物件，並使用一個指令指派結果。</span><span class="sxs-lookup"><span data-stu-id="111c2-185">The `is` pattern expression extends the familiar [`is` operator](../language-reference/keywords/is.md#pattern-matching-with-is) to query an object about its type and assign the result in one instruction.</span></span> <span data-ttu-id="111c2-186">下列程式碼會檢查變數是否為 `int`，如果是，則將其加入至目前的總和：</span><span class="sxs-lookup"><span data-stu-id="111c2-186">The following code checks if a variable is an `int`, and if so, adds it to the current sum:</span></span>

```csharp
if (input is int count)
    sum += count;
```

<span data-ttu-id="111c2-187">上述的小範例示範 `is` 運算式的增強功能。</span><span class="sxs-lookup"><span data-stu-id="111c2-187">The preceding small example demonstrates the enhancements to the `is` expression.</span></span> <span data-ttu-id="111c2-188">您可以對實值型別以及參考型別進行測試，而且您可以將成功的結果指派給正確型別的新變數。</span><span class="sxs-lookup"><span data-stu-id="111c2-188">You can test against value types as well as reference types, and you can assign the successful result to a new variable of the correct type.</span></span>

<span data-ttu-id="111c2-189">switch 比對運算式的語法很熟悉，是以已屬於 C# 語言一部分的 `switch` 陳述式為基礎。</span><span class="sxs-lookup"><span data-stu-id="111c2-189">The switch match expression has a familiar syntax, based on the `switch` statement already part of the C# language.</span></span> <span data-ttu-id="111c2-190">更新的 switch 陳述式有數個新的建構：</span><span class="sxs-lookup"><span data-stu-id="111c2-190">The updated switch statement has several new constructs:</span></span>

- <span data-ttu-id="111c2-191">`switch` 運算式的控管型別不再限於整數型別、`Enum` 型別、`string`，或對應至這些其中一種類型的可為 Null 的型別。</span><span class="sxs-lookup"><span data-stu-id="111c2-191">The governing type of a `switch` expression is no longer restricted to integral types, `Enum` types, `string`, or a nullable type corresponding to one of those types.</span></span> <span data-ttu-id="111c2-192">可以使用任何型別。</span><span class="sxs-lookup"><span data-stu-id="111c2-192">Any type may be used.</span></span>
- <span data-ttu-id="111c2-193">您可以測試每個 `case` 標籤中的 `switch` 運算式型別。</span><span class="sxs-lookup"><span data-stu-id="111c2-193">You can test the type of the `switch` expression in each `case` label.</span></span> <span data-ttu-id="111c2-194">如同使用 `is` 運算式，您可以將新的變數指派給該型別。</span><span class="sxs-lookup"><span data-stu-id="111c2-194">As with the `is` expression, you may assign a new variable to that type.</span></span>
- <span data-ttu-id="111c2-195">您可以加入 `when` 子句，以進一步測試該變數的條件。</span><span class="sxs-lookup"><span data-stu-id="111c2-195">You may add a `when` clause to further test conditions on that variable.</span></span>
- <span data-ttu-id="111c2-196">`case` 標籤的順序現在很重要。</span><span class="sxs-lookup"><span data-stu-id="111c2-196">The order of `case` labels is now important.</span></span> <span data-ttu-id="111c2-197">系統會執行要比對的第一個分支；其他則會略過。</span><span class="sxs-lookup"><span data-stu-id="111c2-197">The first branch to match is executed; others are skipped.</span></span>

<span data-ttu-id="111c2-198">下列程式碼可示範這些新功能：</span><span class="sxs-lookup"><span data-stu-id="111c2-198">The following code demonstrates these new features:</span></span>

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
            null:
                throw new NullReferenceException("Null found in sequence");
            default:
                throw new InvalidOperationException("Unrecognized type");
        }
    }
    return sum;
}
```

- <span data-ttu-id="111c2-199">`case 0:` 是熟悉的常數模式。</span><span class="sxs-lookup"><span data-stu-id="111c2-199">`case 0:` is the familiar constant pattern.</span></span> 
- <span data-ttu-id="111c2-200">`case IEnumerable<int> childSequence:` 是一種型別模式。</span><span class="sxs-lookup"><span data-stu-id="111c2-200">`case IEnumerable<int> childSequence:` is a type pattern.</span></span>
- <span data-ttu-id="111c2-201">`case int n when n > 0:` 是一種具有其他 `when` 條件的型別模式。</span><span class="sxs-lookup"><span data-stu-id="111c2-201">`case int n when n > 0:` is a type pattern with an additional `when` condition.</span></span>
- <span data-ttu-id="111c2-202">`case null:` 是 Null 模式。</span><span class="sxs-lookup"><span data-stu-id="111c2-202">`case null:` is the null pattern.</span></span>
- <span data-ttu-id="111c2-203">`default:` 是熟悉的預設案例。</span><span class="sxs-lookup"><span data-stu-id="111c2-203">`default:` is the familiar default case.</span></span>

<span data-ttu-id="111c2-204">您可以在 [C# 中的模式比對](../pattern-matching.md)中深入了解模式比對。</span><span class="sxs-lookup"><span data-stu-id="111c2-204">You can learn more about pattern matching in [Pattern Matching in C#](../pattern-matching.md).</span></span>

## <a name="ref-locals-and-returns"></a><span data-ttu-id="111c2-205">Ref 區域變數和傳回</span><span class="sxs-lookup"><span data-stu-id="111c2-205">Ref locals and returns</span></span>

<span data-ttu-id="111c2-206">這項功能可以啟用使用和傳回在其他地方定義之變數參考的演算法。</span><span class="sxs-lookup"><span data-stu-id="111c2-206">This feature enables algorithms that use and return references to variables defined elsewhere.</span></span> <span data-ttu-id="111c2-207">其中一個範例是使用大型矩陣，並尋找具有特定特性的單一位置。</span><span class="sxs-lookup"><span data-stu-id="111c2-207">One example is working with large matrices, and finding a single location with certain characteristics.</span></span> <span data-ttu-id="111c2-208">下列方法會傳回矩陣中該儲存體的**參考**：</span><span class="sxs-lookup"><span data-stu-id="111c2-208">The following method returns a **reference** to that storage in the matrix:</span></span>

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

<span data-ttu-id="111c2-209">您可以將傳回值宣告為 `ref`，並在矩陣中修改該值，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="111c2-209">You can declare the return value as a `ref` and modify that value in the matrix, as shown in the following code:</span></span>

[!code-csharp[AssignRefReturn](~/samples/snippets/csharp/new-in-7/program.cs#AssignRefReturn "Assign ref return")]

<span data-ttu-id="111c2-210">C# 語言具備數個規則，可防止您濫用 `ref` 區域變數並傳回︰</span><span class="sxs-lookup"><span data-stu-id="111c2-210">The C# language has several rules that protect you from misusing the `ref` locals and returns:</span></span>

* <span data-ttu-id="111c2-211">您必須將 `ref` 關鍵字加入至方法特徵標記，以及某個方法中的所有 `return` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="111c2-211">You must add the `ref` keyword to the method signature and to all `return` statements in a method.</span></span>
    - <span data-ttu-id="111c2-212">如此可透過整個方法的參考，清除方法傳回。</span><span class="sxs-lookup"><span data-stu-id="111c2-212">That makes it clear the method returns by reference throughout the method.</span></span>
* <span data-ttu-id="111c2-213">`ref return` 可能會指派給值變數，或 `ref` 變數。</span><span class="sxs-lookup"><span data-stu-id="111c2-213">A `ref return` may be assigned to a value variable, or a `ref` variable.</span></span>
    - <span data-ttu-id="111c2-214">呼叫端會控制是否要複製傳回值。</span><span class="sxs-lookup"><span data-stu-id="111c2-214">The caller controls whether the return value is copied or not.</span></span> <span data-ttu-id="111c2-215">指派傳回值時省略 `ref` 修飾詞表示呼叫端需要值的複本，而不是儲存體的參考。</span><span class="sxs-lookup"><span data-stu-id="111c2-215">Omitting the `ref` modifier when assigning the return value indicates that the caller wants a copy of the value, not a reference to the storage.</span></span>
* <span data-ttu-id="111c2-216">您無法將標準方法傳回值指派到 `ref` 區域變數。</span><span class="sxs-lookup"><span data-stu-id="111c2-216">You can't assign a standard method return value to a `ref` local variable.</span></span>
    - <span data-ttu-id="111c2-217">這可杜絕類似 `ref int i = sequence.Count();` 的陳述式</span><span class="sxs-lookup"><span data-stu-id="111c2-217">That disallows statements like `ref int i = sequence.Count();`</span></span>
* <span data-ttu-id="111c2-218">您無法將 `ref` 傳回給其存留期不超過方法執行的變數。</span><span class="sxs-lookup"><span data-stu-id="111c2-218">You can't return a `ref` to a variable whose lifetime doesn't extend beyond the execution of the method.</span></span>
    - <span data-ttu-id="111c2-219">這表示您無法將參考傳回區域變數或具有類似範圍的變數。</span><span class="sxs-lookup"><span data-stu-id="111c2-219">That means you can't return a reference to a local variable or a variable with a similar scope.</span></span>
* <span data-ttu-id="111c2-220">`ref` 區域變數及傳回值無法配合非同步方法使用。</span><span class="sxs-lookup"><span data-stu-id="111c2-220">`ref` locals and returns can't be used with async methods.</span></span>
    - <span data-ttu-id="111c2-221">當非同步方法傳回時，編譯器無法確定參考的變數是否已設定為其最終的值。</span><span class="sxs-lookup"><span data-stu-id="111c2-221">The compiler can't know if the referenced variable has been set to its final value when the async method returns.</span></span>

<span data-ttu-id="111c2-222">新增 ref 區域變數和 ref 傳回能啟用更有效率的演算法，因為可以避免複製值，或是多次執行取值作業。</span><span class="sxs-lookup"><span data-stu-id="111c2-222">The addition of ref locals and ref returns enables algorithms that are more efficient by avoiding copying values, or performing dereferencing operations multiple times.</span></span>

<span data-ttu-id="111c2-223">將 `ref` 新增至傳回值是[來源相容變更](version-update-considerations.md#source-compatible-changes)。</span><span class="sxs-lookup"><span data-stu-id="111c2-223">Adding `ref` to the return value is a [source compatible change](version-update-considerations.md#source-compatible-changes).</span></span> <span data-ttu-id="111c2-224">現有程式碼會編譯，但是 ref 傳回值是在指派時複製。</span><span class="sxs-lookup"><span data-stu-id="111c2-224">Existing code compiles, but the ref return value is copied when assigned.</span></span> <span data-ttu-id="111c2-225">呼叫端必須將傳回值的儲存體更新為 `ref` 區域變數，將傳回項目儲存為參考。</span><span class="sxs-lookup"><span data-stu-id="111c2-225">Callers must update the storage for the return value to a `ref` local variable to store the return as a reference.</span></span>

<span data-ttu-id="111c2-226">如需詳細資訊，請參閱 [ref 關鍵字](../language-reference/keywords/ref.md)一文。</span><span class="sxs-lookup"><span data-stu-id="111c2-226">For more information, see the [ref keyword](../language-reference/keywords/ref.md) article.</span></span>

## <a name="local-functions"></a><span data-ttu-id="111c2-227">區域函式</span><span class="sxs-lookup"><span data-stu-id="111c2-227">Local functions</span></span>

<span data-ttu-id="111c2-228">類別的許多設計都包括從唯一一個位置呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="111c2-228">Many designs for classes include methods that are called from only one location.</span></span> <span data-ttu-id="111c2-229">這些額外的私用方法會使每一種方法維持小而聚焦。</span><span class="sxs-lookup"><span data-stu-id="111c2-229">These additional private methods keep each method small and focused.</span></span> <span data-ttu-id="111c2-230">「區域函式」可讓您在另一個方法的內容中宣告方法。</span><span class="sxs-lookup"><span data-stu-id="111c2-230">*Local functions* enable you to declare methods inside the context of another method.</span></span> <span data-ttu-id="111c2-231">區域函式可讓類別的讀者更容易看到區域方法只會從它宣告所在的內容呼叫。</span><span class="sxs-lookup"><span data-stu-id="111c2-231">Local functions make it easier for readers of the class to see that the local method is only called from the context in which is it declared.</span></span>

<span data-ttu-id="111c2-232">有兩個常見的區域函式使用案例︰公用迭代器方法和公用非同步方法。</span><span class="sxs-lookup"><span data-stu-id="111c2-232">There are two common use cases for local functions: public iterator methods and public async methods.</span></span> <span data-ttu-id="111c2-233">這兩種方法都會產生程式碼，比程式設計人員想像更晚才報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="111c2-233">Both types of methods generate code that reports errors later than programmers might expect.</span></span> <span data-ttu-id="111c2-234">在迭代器方法中，任何例外狀況只會在呼叫列舉傳回序列的程式碼時觀察到。</span><span class="sxs-lookup"><span data-stu-id="111c2-234">In iterator methods, any exceptions are observed only when calling code that enumerates the returned sequence.</span></span> <span data-ttu-id="111c2-235">在非同步方法中，任何例外狀況只會在傳回的 `Task` 等候時觀察到。</span><span class="sxs-lookup"><span data-stu-id="111c2-235">In async methods, any exceptions are only observed when the returned `Task` is awaited.</span></span> <span data-ttu-id="111c2-236">下列範例示範使用區域函式分隔參數驗證和迭代器實作：</span><span class="sxs-lookup"><span data-stu-id="111c2-236">The following example demonstrates separating parameter validation from the iterator implementation using a local function:</span></span>

[!code-csharp[22_IteratorMethodLocal](~/samples/snippets/csharp/new-in-7/Iterator.cs#IteratorMethodLocal "Iterator method with local function")]

<span data-ttu-id="111c2-237">相同的技巧也可以運用在 `async` 方法，以確保在非同步工作開始之前，會擲回引數驗證所引發的例外狀況︰</span><span class="sxs-lookup"><span data-stu-id="111c2-237">The same technique can be employed with `async` methods to ensure that exceptions arising from argument validation are thrown before the asynchronous work begins:</span></span>

[!code-csharp[TaskExample](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

> [!NOTE]
> <span data-ttu-id="111c2-238">區域函式支援的部分設計也可以使用「Lambda 運算式」完成。</span><span class="sxs-lookup"><span data-stu-id="111c2-238">Some of the designs that are supported by local functions could also be accomplished using *lambda expressions*.</span></span> <span data-ttu-id="111c2-239">有興趣的人可以[進一步了解差異](../local-functions-vs-lambdas.md)</span><span class="sxs-lookup"><span data-stu-id="111c2-239">Those interested can [read more about the differences](../local-functions-vs-lambdas.md)</span></span>

## <a name="more-expression-bodied-members"></a><span data-ttu-id="111c2-240">更多運算式主體成員</span><span class="sxs-lookup"><span data-stu-id="111c2-240">More expression-bodied members</span></span>

<span data-ttu-id="111c2-241">C# 6 引進了成員函式的[運算式主體成員](csharp-6.md#expression-bodied-function-members)和唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="111c2-241">C# 6 introduced [expression-bodied members](csharp-6.md#expression-bodied-function-members) for member functions, and read-only properties.</span></span> <span data-ttu-id="111c2-242">C# 7.0 擴充了可以實作為運算式的允許成員。</span><span class="sxs-lookup"><span data-stu-id="111c2-242">C# 7.0 expands the allowed members that can be implemented as expressions.</span></span> <span data-ttu-id="111c2-243">在 C# 7.0 中，您可以實作「建構函式」、「完成項」，以及「屬性」和「索引子」上的 `get` 和 `set` 存取子。</span><span class="sxs-lookup"><span data-stu-id="111c2-243">In C# 7.0, you can implement *constructors*, *finalizers*, and `get` and `set` accessors on *properties* and *indexers*.</span></span> <span data-ttu-id="111c2-244">下列程式碼將示範各項的範例：</span><span class="sxs-lookup"><span data-stu-id="111c2-244">The following code shows examples of each:</span></span>

[!code-csharp[ExpressionBodiedMembers](~/samples/snippets/csharp/new-in-7/expressionmembers.cs#ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> <span data-ttu-id="111c2-245">這個範例不需要完成項，但仍加以顯示以示範語法。</span><span class="sxs-lookup"><span data-stu-id="111c2-245">This example does not need a finalizer, but it is shown to demonstrate the syntax.</span></span> <span data-ttu-id="111c2-246">除非為釋放 Unmanaged 資源所需，否則不應該在類別中實作完成項。</span><span class="sxs-lookup"><span data-stu-id="111c2-246">You should not implement a finalizer in your class unless it is necessary to  release unmanaged resources.</span></span> <span data-ttu-id="111c2-247">您也應該考慮使用 <xref:System.Runtime.InteropServices.SafeHandle> 類別而不是直接管理 Unmanaged 資源。</span><span class="sxs-lookup"><span data-stu-id="111c2-247">You should also consider using the <xref:System.Runtime.InteropServices.SafeHandle> class instead of managing unmanaged resources directly.</span></span>

<span data-ttu-id="111c2-248">這些運算式主體成員的新位置代表 C# 語言的重要里程碑︰這些功能是由參與開放原始碼 [Roslyn](https://github.com/dotnet/Roslyn) 專案的社群成員所實作。</span><span class="sxs-lookup"><span data-stu-id="111c2-248">These new locations for expression-bodied members represent an important milestone for the C# language: These features were implemented by community members working on the open-source [Roslyn](https://github.com/dotnet/Roslyn) project.</span></span>

<span data-ttu-id="111c2-249">將方法變更為運算式主體成員是[二進位相容](version-update-considerations.md#binary-compatible-changes)變更。</span><span class="sxs-lookup"><span data-stu-id="111c2-249">Changing a method to an expression bodied member is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="throw-expressions"></a><span data-ttu-id="111c2-250">throw 運算式</span><span class="sxs-lookup"><span data-stu-id="111c2-250">Throw expressions</span></span>

<span data-ttu-id="111c2-251">在 C# 中，`throw` 一直都是陳述式。</span><span class="sxs-lookup"><span data-stu-id="111c2-251">In C#, `throw` has always been a statement.</span></span> <span data-ttu-id="111c2-252">因為 `throw` 是陳述式，而不是運算式，所以有您無法在其中使用它的 C# 建構。</span><span class="sxs-lookup"><span data-stu-id="111c2-252">Because `throw` is a statement, not an expression, there were C# constructs where you couldn't use it.</span></span> <span data-ttu-id="111c2-253">這些包含條件運算式、Null 聯合運算式和一些 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="111c2-253">These included conditional expressions, null coalescing expressions, and some lambda expressions.</span></span> <span data-ttu-id="111c2-254">新增運算式主體成員會新增 `throw` 運算式適用的更多位置。</span><span class="sxs-lookup"><span data-stu-id="111c2-254">The addition of expression-bodied members adds more locations where `throw` expressions would be useful.</span></span> <span data-ttu-id="111c2-255">為了讓您可以撰寫任何這些建構，C# 7.0 引進了「throw 運算式」。</span><span class="sxs-lookup"><span data-stu-id="111c2-255">So that you can write any of these constructs, C# 7.0 introduces *throw expressions*.</span></span> 

<span data-ttu-id="111c2-256">此新增可讓您更輕鬆地撰寫更多以運算式為基礎的程式碼。</span><span class="sxs-lookup"><span data-stu-id="111c2-256">This addition makes it easier to write more expression-based code.</span></span> <span data-ttu-id="111c2-257">您不需要額外的陳述式就可以進行錯誤檢查。</span><span class="sxs-lookup"><span data-stu-id="111c2-257">You don't need additional statements for error checking.</span></span>

## <a name="generalized-async-return-types"></a><span data-ttu-id="111c2-258">通用的非同步傳回型別</span><span class="sxs-lookup"><span data-stu-id="111c2-258">Generalized async return types</span></span>

<span data-ttu-id="111c2-259">從非同步方法傳回 `Task` 物件可能會造成在特定路徑的效能瓶頸。</span><span class="sxs-lookup"><span data-stu-id="111c2-259">Returning a `Task` object from async methods can introduce performance bottlenecks in certain paths.</span></span> <span data-ttu-id="111c2-260">`Task` 是參考型別，因此使用它表示要配置物件。</span><span class="sxs-lookup"><span data-stu-id="111c2-260">`Task` is a reference type, so using it means allocating an object.</span></span> <span data-ttu-id="111c2-261">當使用 `async` 修飾詞宣告的方法傳回快取的結果時，或是以同步方式完成，額外配置可能會在效能關鍵的程式碼區段中變成一項重要的時間成本。</span><span class="sxs-lookup"><span data-stu-id="111c2-261">In cases where a method declared with the `async` modifier returns a cached result, or completes synchronously, the extra allocations can become a significant time cost in performance critical sections of code.</span></span> <span data-ttu-id="111c2-262">如果這些配置發生在緊密迴圈中，它可能會變得成本很高。</span><span class="sxs-lookup"><span data-stu-id="111c2-262">It can become costly if those allocations occur in tight loops.</span></span>

<span data-ttu-id="111c2-263">新的語言功能表示 async 方法傳回型別不限於 `Task`、`Task<T>` 和 `void`。</span><span class="sxs-lookup"><span data-stu-id="111c2-263">The new language feature means that async method return types aren't limited to `Task`, `Task<T>`, and `void`.</span></span> <span data-ttu-id="111c2-264">傳回的型別仍然必須滿足非同步模式，也就是表示 `GetAwaiter` 方法必須可存取。</span><span class="sxs-lookup"><span data-stu-id="111c2-264">The returned type must still satisfy the async pattern, meaning a `GetAwaiter` method must be accessible.</span></span> <span data-ttu-id="111c2-265">具體的範例就是，`ValueTask` 類型已新增到 .NET Framework，才便利用這項新的語言功能︰</span><span class="sxs-lookup"><span data-stu-id="111c2-265">As one concrete example, the `ValueTask` type has been added to the .NET framework to make use of this new language feature:</span></span> 

[!code-csharp[UsingValueTask](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#UsingValueTask "Using ValueTask")]

> [!NOTE]
> <span data-ttu-id="111c2-266">您必須新增 NuGet 套件 [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/)，才可使用 <xref:System.Threading.Tasks.ValueTask%601> 類型。</span><span class="sxs-lookup"><span data-stu-id="111c2-266">You need to add the NuGet package [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) in order to use the <xref:System.Threading.Tasks.ValueTask%601> type.</span></span>

<span data-ttu-id="111c2-267">這項增強功能最能幫助程式庫作者避免在效能關鍵的程式碼中配置 `Task`。</span><span class="sxs-lookup"><span data-stu-id="111c2-267">This enhancement is most useful for library authors to avoid allocating a `Task` in performance critical code.</span></span>

## <a name="numeric-literal-syntax-improvements"></a><span data-ttu-id="111c2-268">數值常值的語法增強功能</span><span class="sxs-lookup"><span data-stu-id="111c2-268">Numeric literal syntax improvements</span></span>

<span data-ttu-id="111c2-269">錯譯數值常數，可能會使得在第一次閱讀它時，更加難以了解程式碼。</span><span class="sxs-lookup"><span data-stu-id="111c2-269">Misreading numeric constants can make it harder to understand code when reading it for the first time.</span></span> <span data-ttu-id="111c2-270">位元遮罩或其他符號值容易遭到誤解。</span><span class="sxs-lookup"><span data-stu-id="111c2-270">Bit masks or other symbolic values are prone to misunderstanding.</span></span> <span data-ttu-id="111c2-271">C# 7.0 包含兩項新功能，可以用預期用途最容易閱讀的方式來撰寫數字︰「二進位常值」和「數字分隔符號」。</span><span class="sxs-lookup"><span data-stu-id="111c2-271">C# 7.0 includes two new features to write numbers in the most readable fashion for the intended use: *binary literals*, and *digit separators*.</span></span>

<span data-ttu-id="111c2-272">當您在建立位元遮罩時，或是每當數字的二進位表示法構成最容易閱讀的程式碼時，請以二進位撰寫該數字︰</span><span class="sxs-lookup"><span data-stu-id="111c2-272">For those times when you're creating bit masks, or whenever a binary representation of a number makes the most readable code, write that number in binary:</span></span>

[!code-csharp[ThousandSeparators](~/samples/snippets/csharp/new-in-7/Program.cs#ThousandSeparators "Thousands separators")]

<span data-ttu-id="111c2-273">常數開頭的 `0b` 表示數字是撰寫為二進位數字。</span><span class="sxs-lookup"><span data-stu-id="111c2-273">The `0b` at the beginning of the constant indicates that the number is written as a binary number.</span></span> <span data-ttu-id="111c2-274">二進位數字可能會很長，因此引進 `_` 作為數字分隔符號通常能夠更輕鬆地查看位元模式，如上述的二進位常數所示。</span><span class="sxs-lookup"><span data-stu-id="111c2-274">Binary numbers can get long, so it's often easier to see the bit patterns by introducing the `_` as a digit separator, as shown above in the binary constant.</span></span> <span data-ttu-id="111c2-275">千位分隔符號可以出現在常數的任何位置。</span><span class="sxs-lookup"><span data-stu-id="111c2-275">The digit separator can appear anywhere in the constant.</span></span> <span data-ttu-id="111c2-276">對於以 10 為底的數字，通常會使用它作為千位分隔符號︰</span><span class="sxs-lookup"><span data-stu-id="111c2-276">For base 10 numbers, it is common to use it as a thousands separator:</span></span>

[!code-csharp[LargeIntegers](~/samples/snippets/csharp/new-in-7/Program.cs#LargeIntegers "Large integer")]

<span data-ttu-id="111c2-277">千位分隔符號也可以搭配 `decimal`、`float` 和 `double` 類型使用︰</span><span class="sxs-lookup"><span data-stu-id="111c2-277">The digit separator can be used with `decimal`, `float`, and `double` types as well:</span></span>

[!code-csharp[OtherConstants](~/samples/snippets/csharp/new-in-7/Program.cs#OtherConstants "non-integral constants")]

<span data-ttu-id="111c2-278">結合起來，您在宣告數值常數時可以有更多的可讀性。</span><span class="sxs-lookup"><span data-stu-id="111c2-278">Taken together, you can declare numeric constants with much more readability.</span></span>
