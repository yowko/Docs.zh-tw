---
title: '元組類型-c # 參考'
description: '深入瞭解 c # 元組：可用來將鬆散相關的資料元素分組的輕量資料結構'
ms.date: 07/09/2020
helpviewer_keywords:
- value tuples [C#]
ms.openlocfilehash: d996c7afecba1b58bfd8337fa444fd71790dd482
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471768"
---
# <a name="tuple-types-c-reference"></a><span data-ttu-id="b002d-103">元組類型 (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="b002d-103">Tuple types (C# reference)</span></span>

<span data-ttu-id="b002d-104">在 c # 7.0 和更新版本中提供， *元組* 功能提供簡潔的語法，以將輕量資料結構中的多個資料元素群組在一起。</span><span class="sxs-lookup"><span data-stu-id="b002d-104">Available in C# 7.0 and later, the *tuples* feature provides concise syntax to group multiple data elements in a lightweight data structure.</span></span> <span data-ttu-id="b002d-105">下列範例會示範如何宣告元組變數、將它初始化，以及存取其資料成員：</span><span class="sxs-lookup"><span data-stu-id="b002d-105">The following example shows how you can declare a tuple variable, initialize it, and access its data members:</span></span>

[!code-csharp-interactive[tuple intro](snippets/shared/ValueTuples.cs#Introduction)]

<span data-ttu-id="b002d-106">如先前的範例所示，若要定義元組類型，請指定其所有資料成員的類型，並選擇性地指定 [功能變數名稱](#tuple-field-names)。</span><span class="sxs-lookup"><span data-stu-id="b002d-106">As the preceding example shows, to define a tuple type, you specify types of all its data members and, optionally, the [field names](#tuple-field-names).</span></span> <span data-ttu-id="b002d-107">您無法在元組類型中定義方法，但您可以使用 .NET 提供的方法，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="b002d-107">You cannot define methods in a tuple type, but you can use the methods provided by .NET, as the following example shows:</span></span>

[!code-csharp-interactive[tuple methods](snippets/shared/ValueTuples.cs#MethodOnTuples)]

<span data-ttu-id="b002d-108">從 c # 7.3 開始，元組類型支援 [等號比較運算子](../operators/equality-operators.md) `==` 和 `!=` 。</span><span class="sxs-lookup"><span data-stu-id="b002d-108">Beginning with C# 7.3, tuple types support [equality operators](../operators/equality-operators.md) `==` and `!=`.</span></span> <span data-ttu-id="b002d-109">如需詳細資訊，請參閱 [元組相等](#tuple-equality) 區段。</span><span class="sxs-lookup"><span data-stu-id="b002d-109">For more information, see the [Tuple equality](#tuple-equality) section.</span></span>

<span data-ttu-id="b002d-110">元組類型為實 [數值型別](value-types.md);元組元素為公用欄位。</span><span class="sxs-lookup"><span data-stu-id="b002d-110">Tuple types are [value types](value-types.md); tuple elements are public fields.</span></span> <span data-ttu-id="b002d-111">這會讓元組 *可變* 的實值型別。</span><span class="sxs-lookup"><span data-stu-id="b002d-111">That makes tuples *mutable* value types.</span></span>

> [!NOTE]
> <span data-ttu-id="b002d-112">元組功能需要 <xref:System.ValueTuple?displayProperty=nameWithType> 類型和相關的泛型型別 (例如， <xref:System.ValueTuple%602?displayProperty=nameWithType>) ，可在 .net Core 和 .NET Framework 4.7 和更新版本中使用。</span><span class="sxs-lookup"><span data-stu-id="b002d-112">The tuples feature requires the <xref:System.ValueTuple?displayProperty=nameWithType> type and related generic types (for example, <xref:System.ValueTuple%602?displayProperty=nameWithType>), which are available in .NET Core and .NET Framework 4.7 and later.</span></span> <span data-ttu-id="b002d-113">若要在以 .NET Framework 4.6.2 或更早版本為目標的專案中使用元組，請將 NuGet 套件新增 [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) 至專案。</span><span class="sxs-lookup"><span data-stu-id="b002d-113">To use tuples in a project that targets .NET Framework 4.6.2 or earlier, add the NuGet package [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) to the project.</span></span>

<span data-ttu-id="b002d-114">您可以定義具有任意大量元素的元組：</span><span class="sxs-lookup"><span data-stu-id="b002d-114">You can define tuples with an arbitrary large number of elements:</span></span>

[!code-csharp-interactive[large tuple](snippets/shared/ValueTuples.cs#LargeTuple)]

## <a name="use-cases-of-tuples"></a><span data-ttu-id="b002d-115">元組的使用案例</span><span class="sxs-lookup"><span data-stu-id="b002d-115">Use cases of tuples</span></span>

<span data-ttu-id="b002d-116">元組最常見的其中一個使用案例是做為方法傳回型別。</span><span class="sxs-lookup"><span data-stu-id="b002d-116">One of the most common use cases of tuples is as a method return type.</span></span> <span data-ttu-id="b002d-117">也就是說，您可以將方法結果分組為元組傳回型別，而不是定義[ `out` 方法參數](../keywords/out-parameter-modifier.md)，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="b002d-117">That is, instead of defining [`out` method parameters](../keywords/out-parameter-modifier.md), you can group method results in a tuple return type, as the following example shows:</span></span>

[!code-csharp-interactive[multiple method outputs](snippets/shared/ValueTuples.cs#MultipleReturns)]

<span data-ttu-id="b002d-118">如先前的範例所示，您可以直接使用傳回的元組實例，或在不同的變數中 [解構](#tuple-assignment-and-deconstruction) 它。</span><span class="sxs-lookup"><span data-stu-id="b002d-118">As the preceding example shows, you can work with the returned tuple instance directly or [deconstruct](#tuple-assignment-and-deconstruction) it in separate variables.</span></span>

<span data-ttu-id="b002d-119">您也可以使用元組類型，而不是 [匿名型別](../../programming-guide/classes-and-structs/anonymous-types.md);例如，在 LINQ 查詢中。</span><span class="sxs-lookup"><span data-stu-id="b002d-119">You can also use tuple types instead of [anonymous types](../../programming-guide/classes-and-structs/anonymous-types.md); for example, in LINQ queries.</span></span> <span data-ttu-id="b002d-120">如需詳細資訊，請參閱 [在匿名和元組類型之間選擇](../../../standard/base-types/choosing-between-anonymous-and-tuple.md)。</span><span class="sxs-lookup"><span data-stu-id="b002d-120">For more information, see [Choosing between anonymous and tuple types](../../../standard/base-types/choosing-between-anonymous-and-tuple.md).</span></span>

<span data-ttu-id="b002d-121">一般而言，您會使用元組來分組鬆散相關的資料元素。</span><span class="sxs-lookup"><span data-stu-id="b002d-121">Typically, you use tuples to group loosely related data elements.</span></span> <span data-ttu-id="b002d-122">這在私用和內部公用程式方法中通常很有用。</span><span class="sxs-lookup"><span data-stu-id="b002d-122">That is usually useful within private and internal utility methods.</span></span> <span data-ttu-id="b002d-123">在公用 API 的情況下，請考慮定義 [類別](../keywords/class.md) 或 [結構](struct.md) 類型。</span><span class="sxs-lookup"><span data-stu-id="b002d-123">In the case of public API, consider defining a [class](../keywords/class.md) or a [structure](struct.md) type.</span></span>

## <a name="tuple-field-names"></a><span data-ttu-id="b002d-124">元組功能變數名稱</span><span class="sxs-lookup"><span data-stu-id="b002d-124">Tuple field names</span></span>

<span data-ttu-id="b002d-125">您可以在元組初始化運算式或元組類型的定義中，明確指定元組欄位的名稱，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="b002d-125">You can explicitly specify the names of tuple fields either in a tuple initialization expression or in the definition of a tuple type, as the following example shows:</span></span>

[!code-csharp-interactive[explicit field names](snippets/shared/ValueTuples.cs#ExplicitFieldNames)]

<span data-ttu-id="b002d-126">從 c # 7.1 開始，如果您未指定功能變數名稱，它可能會從元組初始化運算式中對應的變數名稱推斷，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="b002d-126">Beginning with C# 7.1, if you don't specify a field name, it may be inferred from the name of the corresponding variable in a tuple initialization expression, as the following example shows:</span></span>

[!code-csharp-interactive[inferred field names](snippets/shared/ValueTuples.cs#InferFieldNames)]

<span data-ttu-id="b002d-127">這就是所謂的元組投影初始化運算式。</span><span class="sxs-lookup"><span data-stu-id="b002d-127">That's known as tuple projection initializers.</span></span> <span data-ttu-id="b002d-128">在下列情況中，不會將變數的名稱投射到元組功能變數名稱：</span><span class="sxs-lookup"><span data-stu-id="b002d-128">The name of a variable isn't projected onto a tuple field name in the following cases:</span></span>

- <span data-ttu-id="b002d-129">候選名稱是元組類型的成員名稱，例如、 `Item3` `ToString` 或 `Rest` 。</span><span class="sxs-lookup"><span data-stu-id="b002d-129">The candidate name is a member name of a tuple type, for example, `Item3`, `ToString`, or `Rest`.</span></span>
- <span data-ttu-id="b002d-130">候選名稱是另一個元組功能變數名稱（明確或隱含）的複本。</span><span class="sxs-lookup"><span data-stu-id="b002d-130">The candidate name is a duplicate of another tuple field name, either explicit or implicit.</span></span>

<span data-ttu-id="b002d-131">在這些情況下，您可以明確指定欄位的名稱，或依預設名稱存取欄位。</span><span class="sxs-lookup"><span data-stu-id="b002d-131">In those cases you either explicitly specify the name of a field or access a field by its default name.</span></span>

<span data-ttu-id="b002d-132">元組欄位的預設名稱是 `Item1` 、 `Item2` 等等 `Item3` 。</span><span class="sxs-lookup"><span data-stu-id="b002d-132">The default names of tuple fields are `Item1`, `Item2`, `Item3` and so on.</span></span> <span data-ttu-id="b002d-133">您一律可以使用欄位的預設名稱，即使是明確或推斷的功能變數名稱，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="b002d-133">You can always use the default name of a field, even when a field name is specified explicitly or inferred, as the following example shows:</span></span>

[!code-csharp-interactive[default field names](snippets/shared/ValueTuples.cs#DefaultFieldNames)]

<span data-ttu-id="b002d-134">[元組指派](#tuple-assignment-and-deconstruction) 和 [元組相等比較](#tuple-equality) 不會將欄位名稱列入考慮。</span><span class="sxs-lookup"><span data-stu-id="b002d-134">[Tuple assignment](#tuple-assignment-and-deconstruction) and [tuple equality comparisons](#tuple-equality) don't take field names into account.</span></span>

<span data-ttu-id="b002d-135">在編譯時期，編譯器會以對應的預設名稱取代非預設的功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="b002d-135">At compile time, the compiler replaces non-default field names with the corresponding default names.</span></span> <span data-ttu-id="b002d-136">因此，在執行時間無法使用明確指定或推斷的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="b002d-136">As a result, explicitly specified or inferred field names aren't available at run time.</span></span>

## <a name="tuple-assignment-and-deconstruction"></a><span data-ttu-id="b002d-137">元組指派和解構</span><span class="sxs-lookup"><span data-stu-id="b002d-137">Tuple assignment and deconstruction</span></span>

<span data-ttu-id="b002d-138">C # 支援在符合下列兩個條件的元組類型之間進行指派：</span><span class="sxs-lookup"><span data-stu-id="b002d-138">C# supports assignment between tuple types that satisfy both of the following conditions:</span></span>

- <span data-ttu-id="b002d-139">這兩個元組類型都有相同數目的元素</span><span class="sxs-lookup"><span data-stu-id="b002d-139">both tuple types have the same number of elements</span></span>
- <span data-ttu-id="b002d-140">針對每個元組位置，右邊元組專案的型別會與或隱含轉換成對應的左邊元組元素類型。</span><span class="sxs-lookup"><span data-stu-id="b002d-140">for each tuple position, the type of the right-hand tuple element is the same as or implicitly convertible to the type of the corresponding left-hand tuple element</span></span>

<span data-ttu-id="b002d-141">元組元素值會依照元組專案的順序指派。</span><span class="sxs-lookup"><span data-stu-id="b002d-141">Tuple element values are assigned following the order of tuple elements.</span></span> <span data-ttu-id="b002d-142">元組欄位的名稱會被忽略且未指派，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="b002d-142">The names of tuple fields are ignored and not assigned, as the following example shows:</span></span>

[!code-csharp-interactive[tuple assignment](snippets/shared/ValueTuples.cs#Assignment)]

<span data-ttu-id="b002d-143">您也可以使用指派運算子 `=` ，在不同的變數中 *解構* 元組實例。</span><span class="sxs-lookup"><span data-stu-id="b002d-143">You can also use the assignment operator `=` to *deconstruct* a tuple instance in separate variables.</span></span> <span data-ttu-id="b002d-144">您可以透過下列其中一種方式來執行此動作：</span><span class="sxs-lookup"><span data-stu-id="b002d-144">You can do that in one of the following ways:</span></span>

- <span data-ttu-id="b002d-145">在括弧內明確宣告每個變數的類型：</span><span class="sxs-lookup"><span data-stu-id="b002d-145">Explicitly declare the type of each variable inside parentheses:</span></span>

  [!code-csharp-interactive[specify types of variables](snippets/shared/ValueTuples.cs#DeconstructExplicit)]

- <span data-ttu-id="b002d-146">使用 `var` 括弧外的關鍵字宣告隱含型別變數，並讓編譯器推斷其類型：</span><span class="sxs-lookup"><span data-stu-id="b002d-146">Use the `var` keyword outside the parentheses to declare implicitly typed variables and let the compiler infer their types:</span></span>

  [!code-csharp-interactive[implicitly typed variables](snippets/shared/ValueTuples.cs#DeconstructVar)]

- <span data-ttu-id="b002d-147">使用現有的變數：</span><span class="sxs-lookup"><span data-stu-id="b002d-147">Use existing variables:</span></span>

  [!code-csharp-interactive[existing variables](snippets/shared/ValueTuples.cs#DeconstructExisting)]

<span data-ttu-id="b002d-148">如需解構元組和其他類型的詳細資訊，請參閱 [解構元組和其他類型](../../deconstruct.md)。</span><span class="sxs-lookup"><span data-stu-id="b002d-148">For more information about deconstruction of tuples and other types, see [Deconstructing tuples and other types](../../deconstruct.md).</span></span>

## <a name="tuple-equality"></a><span data-ttu-id="b002d-149">元組相等</span><span class="sxs-lookup"><span data-stu-id="b002d-149">Tuple equality</span></span>

<span data-ttu-id="b002d-150">從 C# 7.3 開始，Tuple 型別支援 `==` 和 `!=` 運算子。</span><span class="sxs-lookup"><span data-stu-id="b002d-150">Beginning with C# 7.3, tuple types support the `==` and `!=` operators.</span></span> <span data-ttu-id="b002d-151">這些運算子會比較左邊運算元的成員與右邊運算元的對應成員（依照元組元素的順序）。</span><span class="sxs-lookup"><span data-stu-id="b002d-151">These operators compare members of the left-hand operand with the corresponding members of the right-hand operand following the order of tuple elements.</span></span>

[!code-csharp-interactive[tuple equality](snippets/shared/ValueTuples.cs#TupleEquality)]

<span data-ttu-id="b002d-152">如先前的範例所示， `==` 和 `!=` 作業不會考慮元組功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="b002d-152">As the preceding example shows, the `==` and `!=` operations don't take into account tuple field names.</span></span>

<span data-ttu-id="b002d-153">當滿足下列兩個條件時，可以比較兩個元組：</span><span class="sxs-lookup"><span data-stu-id="b002d-153">Two tuples are comparable when both of the following conditions are satisfied:</span></span>

- <span data-ttu-id="b002d-154">這兩個元組都有相同數目的元素。</span><span class="sxs-lookup"><span data-stu-id="b002d-154">Both tuples have the same number of elements.</span></span> <span data-ttu-id="b002d-155">例如， `t1 != t2` 如果 `t1` 和 `t2` 具有不同數目的元素，則不會編譯。</span><span class="sxs-lookup"><span data-stu-id="b002d-155">For example, `t1 != t2` doesn't compile if `t1` and `t2` have different numbers of elements.</span></span>
- <span data-ttu-id="b002d-156">針對每個元組位置，左側和右邊元組運算元中的對應元素可與 `==` 和 `!=` 運算子比較。</span><span class="sxs-lookup"><span data-stu-id="b002d-156">For each tuple position, the corresponding elements from the left-hand and right-hand tuple operands are comparable with the `==` and `!=` operators.</span></span> <span data-ttu-id="b002d-157">例如，不會進行 `(1, (2, 3)) == ((1, 2), 3)` 編譯，因為 `1` 無法比較 `(1, 2)` 。</span><span class="sxs-lookup"><span data-stu-id="b002d-157">For example, `(1, (2, 3)) == ((1, 2), 3)` doesn't compile because `1` is not comparable with `(1, 2)`.</span></span>

<span data-ttu-id="b002d-158">和運算子會以最少運算 `==` `!=` 的方式比較元組。</span><span class="sxs-lookup"><span data-stu-id="b002d-158">The `==` and `!=` operators compare tuples in short-circuiting way.</span></span> <span data-ttu-id="b002d-159">也就是說，當作業符合一對不相等的元素或達到元組的結尾時，就會停止作業。</span><span class="sxs-lookup"><span data-stu-id="b002d-159">That is, an operation stops as soon as it meets a pair of non equal elements or reaches the ends of tuples.</span></span> <span data-ttu-id="b002d-160">不過，在進行任何比較之前，會評估 *所有* 元組元素，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="b002d-160">However, before any comparison, *all* tuple elements are evaluated, as the following example shows:</span></span>

[!code-csharp-interactive[tuple element evaluation](snippets/shared/ValueTuples.cs#TupleEvaluationForEquality)]

## <a name="tuples-as-out-parameters"></a><span data-ttu-id="b002d-161">元組作為 out 參數</span><span class="sxs-lookup"><span data-stu-id="b002d-161">Tuples as out parameters</span></span>

<span data-ttu-id="b002d-162">通常，您會將具有[ `out` 參數](../keywords/out-parameter-modifier.md)的方法重構為傳回元組的方法。</span><span class="sxs-lookup"><span data-stu-id="b002d-162">Typically, you refactor a method that has [`out` parameters](../keywords/out-parameter-modifier.md) into a method that returns a tuple.</span></span> <span data-ttu-id="b002d-163">不過，在某些情況下， `out` 參數可以是元組類型。</span><span class="sxs-lookup"><span data-stu-id="b002d-163">However, there are cases in which an `out` parameter can be of a tuple type.</span></span> <span data-ttu-id="b002d-164">下列範例顯示如何使用元組作為 `out` 參數：</span><span class="sxs-lookup"><span data-stu-id="b002d-164">The following example shows how to work with tuples as `out` parameters:</span></span>

[!code-csharp-interactive[tuple as out parameter](snippets/shared/ValueTuples.cs#TupleAsOutParameter)]

## <a name="tuples-vs-systemtuple"></a><span data-ttu-id="b002d-165">元組與 `System.Tuple`</span><span class="sxs-lookup"><span data-stu-id="b002d-165">Tuples vs `System.Tuple`</span></span>

<span data-ttu-id="b002d-166">由型別所支援的 c # 元組， <xref:System.ValueTuple?displayProperty=nameWithType> 與以類型表示的元組不同 <xref:System.Tuple?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="b002d-166">C# tuples, which are backed by <xref:System.ValueTuple?displayProperty=nameWithType> types, are different from tuples that are represented by <xref:System.Tuple?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="b002d-167">主要的差異如下：</span><span class="sxs-lookup"><span data-stu-id="b002d-167">The main differences are as follows:</span></span>

- <span data-ttu-id="b002d-168">`ValueTuple` 類型是實 [數值型別](value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="b002d-168">`ValueTuple` types are [value types](value-types.md).</span></span> <span data-ttu-id="b002d-169">`Tuple` 類型為 [參考型別](../keywords/reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="b002d-169">`Tuple` types are [reference types](../keywords/reference-types.md).</span></span>
- <span data-ttu-id="b002d-170">`ValueTuple` 類型是可變動的。</span><span class="sxs-lookup"><span data-stu-id="b002d-170">`ValueTuple` types are mutable.</span></span> <span data-ttu-id="b002d-171">`Tuple` 類型是不可變的。</span><span class="sxs-lookup"><span data-stu-id="b002d-171">`Tuple` types are immutable.</span></span>
- <span data-ttu-id="b002d-172">類型的資料成員 `ValueTuple` 為欄位。</span><span class="sxs-lookup"><span data-stu-id="b002d-172">Data members of `ValueTuple` types are fields.</span></span> <span data-ttu-id="b002d-173">類型的資料成員 `Tuple` 為屬性。</span><span class="sxs-lookup"><span data-stu-id="b002d-173">Data members of `Tuple` types are properties.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b002d-174">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="b002d-174">C# language specification</span></span>

<span data-ttu-id="b002d-175">如需詳細資訊，請參閱下列功能提案附注：</span><span class="sxs-lookup"><span data-stu-id="b002d-175">For more information, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="b002d-176"> (也會推斷元組名。元組投影初始化運算式) </span><span class="sxs-lookup"><span data-stu-id="b002d-176">Infer tuple names (aka. tuple projection initializers)</span></span>](~/_csharplang/proposals/csharp-7.1/infer-tuple-names.md)
- [<span data-ttu-id="b002d-177">對 `==` `!=` 元組類型的支援</span><span class="sxs-lookup"><span data-stu-id="b002d-177">Support for `==` and `!=` on tuple types</span></span>](~/_csharplang/proposals/csharp-7.3/tuple-equality.md)

## <a name="see-also"></a><span data-ttu-id="b002d-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b002d-178">See also</span></span>

- [<span data-ttu-id="b002d-179">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="b002d-179">C# reference</span></span>](../index.md)
- [<span data-ttu-id="b002d-180">值類型</span><span class="sxs-lookup"><span data-stu-id="b002d-180">Value types</span></span>](value-types.md)
- [<span data-ttu-id="b002d-181">在匿名和元組類型之間選擇</span><span class="sxs-lookup"><span data-stu-id="b002d-181">Choosing between anonymous and tuple types</span></span>](../../../standard/base-types/choosing-between-anonymous-and-tuple.md)
- <xref:System.ValueTuple?displayProperty=nameWithType>
