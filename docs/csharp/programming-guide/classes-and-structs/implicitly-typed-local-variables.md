---
title: 隱含類型區域變數 - C# 程式設計手冊
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: d39e4c4dd180ba35b7555d61211a34d696b04f50
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399823"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="291d1-102">隱含類型區域變數 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="291d1-102">Implicitly typed local variables (C# Programming Guide)</span></span>

<span data-ttu-id="291d1-103">您可以宣告區域變數而不提供明確類型。</span><span class="sxs-lookup"><span data-stu-id="291d1-103">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="291d1-104">`var` 關鍵字會指示編譯器從初始化陳述式右側的運算式推斷變數的類型。</span><span class="sxs-lookup"><span data-stu-id="291d1-104">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="291d1-105">推斷類型可能是內建類型、匿名型別、使用者定義型別，或 .NET Framework 類別庫中定義的類型。</span><span class="sxs-lookup"><span data-stu-id="291d1-105">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET Framework class library.</span></span> <span data-ttu-id="291d1-106">如需如何使用 `var` 初始化陣列的詳細資訊，請參閱[隱含型別陣列](../arrays/implicitly-typed-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="291d1-106">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../arrays/implicitly-typed-arrays.md).</span></span>

<span data-ttu-id="291d1-107">下列範例顯示可以使用 `var` 宣告區域變數的各種方法：</span><span class="sxs-lookup"><span data-stu-id="291d1-107">The following examples show various ways in which local variables can be declared with `var`:</span></span>

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

<span data-ttu-id="291d1-108">請務必了解 `var` 關鍵字不代表 "variant"，也不代表變數是不嚴格規定類型或晚期繫結的。</span><span class="sxs-lookup"><span data-stu-id="291d1-108">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="291d1-109">只代表編譯器會判斷並指派最適當的類型。</span><span class="sxs-lookup"><span data-stu-id="291d1-109">It just means that the compiler determines and assigns the most appropriate type.</span></span>

<span data-ttu-id="291d1-110">`var` 關鍵字可在下列內容中使用：</span><span class="sxs-lookup"><span data-stu-id="291d1-110">The `var` keyword may be used in the following contexts:</span></span>

- <span data-ttu-id="291d1-111">在區域變數 (方法範圍中宣告的變數) 上，如前述範例所示。</span><span class="sxs-lookup"><span data-stu-id="291d1-111">On local variables (variables declared at method scope) as shown in the previous example.</span></span>

- <span data-ttu-id="291d1-112">在 [for](../../language-reference/keywords/for.md) 初始化陳述式中。</span><span class="sxs-lookup"><span data-stu-id="291d1-112">In a [for](../../language-reference/keywords/for.md) initialization statement.</span></span>

    ```csharp
    for (var x = 1; x < 10; x++)
    ```

- <span data-ttu-id="291d1-113">在 [foreach](../../language-reference/keywords/foreach-in.md) 初始化陳述式中。</span><span class="sxs-lookup"><span data-stu-id="291d1-113">In a [foreach](../../language-reference/keywords/foreach-in.md) initialization statement.</span></span>

    ```csharp
    foreach (var item in list) {...}
    ```

- <span data-ttu-id="291d1-114">在 [using](../../language-reference/keywords/using-statement.md) 陳述式中。</span><span class="sxs-lookup"><span data-stu-id="291d1-114">In a [using](../../language-reference/keywords/using-statement.md) statement.</span></span>

    ```csharp
    using (var file = new StreamReader("C:\\myfile.txt")) {...}
    ```

<span data-ttu-id="291d1-115">有關詳細資訊，請參閱[如何在查詢運算式中使用隱式鍵入的區域變數和陣列](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="291d1-115">For more information, see [How to use implicitly typed local variables and arrays in a query expression](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>

## <a name="var-and-anonymous-types"></a><span data-ttu-id="291d1-116">var 和匿名型別</span><span class="sxs-lookup"><span data-stu-id="291d1-116">var and anonymous types</span></span>

<span data-ttu-id="291d1-117">在許多情況下，使用 `var` 是選擇性的，只是為了在語法上便於使用。</span><span class="sxs-lookup"><span data-stu-id="291d1-117">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="291d1-118">不過，當變數以匿名型別初始化時，如果您稍後需要存取物件的屬性，則必須宣告該變數為 `var`。</span><span class="sxs-lookup"><span data-stu-id="291d1-118">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="291d1-119">這是 LINQ 查詢運算式中的常見方案。</span><span class="sxs-lookup"><span data-stu-id="291d1-119">This is a common scenario in LINQ query expressions.</span></span> <span data-ttu-id="291d1-120">有關詳細資訊，請參閱[匿名型別](anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="291d1-120">For more information, see [Anonymous Types](anonymous-types.md).</span></span>

<span data-ttu-id="291d1-121">從原始程式碼的觀點來看，匿名型別沒有名稱。</span><span class="sxs-lookup"><span data-stu-id="291d1-121">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="291d1-122">因此，如果已使用 `var` 初始化查詢變數，則存取傳回的物件序列中屬性的唯一方法，就是使用 `var` 作為 `foreach` 陳述式中反覆運算變數的類型。</span><span class="sxs-lookup"><span data-stu-id="291d1-122">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a><span data-ttu-id="291d1-123">備註</span><span class="sxs-lookup"><span data-stu-id="291d1-123">Remarks</span></span>

<span data-ttu-id="291d1-124">下列限制適用於隱含型別變數宣告：</span><span class="sxs-lookup"><span data-stu-id="291d1-124">The following restrictions apply to implicitly-typed variable declarations:</span></span>

- <span data-ttu-id="291d1-125">`var` 只能在區域變數於相同的陳述式中宣告和初始化時使用；此變數無法初始化為 null、方法群組或匿名函式。</span><span class="sxs-lookup"><span data-stu-id="291d1-125">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>

- <span data-ttu-id="291d1-126">`var` 無法在類別範圍的欄位中使用。</span><span class="sxs-lookup"><span data-stu-id="291d1-126">`var` cannot be used on fields at class scope.</span></span>

- <span data-ttu-id="291d1-127">使用 `var` 宣告的變數無法在初始化運算式中使用。</span><span class="sxs-lookup"><span data-stu-id="291d1-127">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="291d1-128">換句話說，此運算式是合法的：`int i = (i = 20);`但此運算式會產生編譯時間錯誤：`var i = (i = 20);`</span><span class="sxs-lookup"><span data-stu-id="291d1-128">In other words, this expression is legal: `int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>

- <span data-ttu-id="291d1-129">無法在相同的陳述式中初始化多個隱含型別變數。</span><span class="sxs-lookup"><span data-stu-id="291d1-129">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>

- <span data-ttu-id="291d1-130">如果名為 `var` 的類型在範圍之內，則 `var` 關鍵字會解析成該類型名稱，而且不會視為隱含型別區域變數宣告的一部分。</span><span class="sxs-lookup"><span data-stu-id="291d1-130">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>

<span data-ttu-id="291d1-131">使用 `var` 關鍵字的隱含類型只能套用至本機方法範圍的變數。</span><span class="sxs-lookup"><span data-stu-id="291d1-131">Implicit typing with the `var` keyword can only be applied to variables at local method scope.</span></span> <span data-ttu-id="291d1-132">隱含類型不適用於類別欄位，因為 C# 編譯器會在處理程式碼時發生邏輯矛盾：編譯器需要了解欄位的類型，但是它無法在分析指派運算式之前判斷類型，而運算式無法在不了解類型的情況下進行評估。</span><span class="sxs-lookup"><span data-stu-id="291d1-132">Implicit typing is not available for class fields as the C# compiler would encounter a logical paradox as it processed the code: the compiler needs to know the type of the field, but it cannot determine the type until the assignment expression is analyzed, and the expression cannot be evaluated without knowing the type.</span></span> <span data-ttu-id="291d1-133">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="291d1-133">Consider the following code:</span></span>

```csharp
private var bookTitles;
```

<span data-ttu-id="291d1-134">`bookTitles` 是類型為 `var` 的類別欄位。</span><span class="sxs-lookup"><span data-stu-id="291d1-134">`bookTitles` is a class field given the type `var`.</span></span> <span data-ttu-id="291d1-135">因為欄位沒有能評估的運算式，所以編譯器無法推斷 `bookTitles` 的類型為何。</span><span class="sxs-lookup"><span data-stu-id="291d1-135">As the field has no expression to evaluate, it is impossible for the compiler to infer what type `bookTitles` is supposed to be.</span></span> <span data-ttu-id="291d1-136">此外，將運算式新增至欄位 (如同你對區域變數進行的操作) 也不足夠：</span><span class="sxs-lookup"><span data-stu-id="291d1-136">In addition, adding an expression to the field (like you would for a local variable) is also insufficient:</span></span>

```csharp
private var bookTitles = new List<string>();
```

<span data-ttu-id="291d1-137">當編譯器在編譯程式碼期間遇到欄位時，它會記錄每個欄位的類型，再處理任何與其建立關聯的運算式。</span><span class="sxs-lookup"><span data-stu-id="291d1-137">When the compiler encounters fields during code compilation, it records each field's type before processing any expressions associated with it.</span></span> <span data-ttu-id="291d1-138">編譯器會在嘗試剖析 `bookTitles` 時發生相同的矛盾：它需要了解欄位的類型，但是編譯器通常會透過分析運算式來判斷 `var` 的類型，而這無法在不事先了解類型的情況下進行。</span><span class="sxs-lookup"><span data-stu-id="291d1-138">The compiler encounters the same paradox trying to parse `bookTitles`: it needs to know the type of the field, but the compiler would normally determine `var`'s type by analyzing the expression, which isn't possible without knowing the type beforehand.</span></span>

<span data-ttu-id="291d1-139">您會發現在難以判斷查詢運算式中查詢變數的確切建構類型時，`var` 也相當有用。</span><span class="sxs-lookup"><span data-stu-id="291d1-139">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="291d1-140">這會在群組與排序作業時發生。</span><span class="sxs-lookup"><span data-stu-id="291d1-140">This can occur with grouping and ordering operations.</span></span>

<span data-ttu-id="291d1-141">當您不想要老是在鍵盤上鍵入變數的特定類型，或是此特定類型很明顯或不會增加程式碼的可讀性時，`var` 關鍵字也相當有用。</span><span class="sxs-lookup"><span data-stu-id="291d1-141">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="291d1-142">`var` 有用的其中一個範例是用於巢狀泛型型別時，例如用於群組作業的類型。</span><span class="sxs-lookup"><span data-stu-id="291d1-142">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="291d1-143">在下列查詢中，查詢變數的類型是 `IEnumerable<IGrouping<string, Student>>`。</span><span class="sxs-lookup"><span data-stu-id="291d1-143">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="291d1-144">只要您及維護程式碼的其他使用者了解這點，為求便利和簡潔而使用隱含型別就不會有問題。</span><span class="sxs-lookup"><span data-stu-id="291d1-144">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

<span data-ttu-id="291d1-145">使用`var`有助於簡化代碼，但應將其使用僅限於需要代碼的情況，或者它使代碼更易於閱讀的情況。</span><span class="sxs-lookup"><span data-stu-id="291d1-145">The use of `var` helps simplify your code, but its use should be restricted to cases where it is required, or when it makes your code easier to read.</span></span> <span data-ttu-id="291d1-146">有關何時正確使用`var`的詳細資訊，請參閱 C# 編碼指南一文上的[隱式鍵入的區域變數](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables)部分。</span><span class="sxs-lookup"><span data-stu-id="291d1-146">For more information about when to use `var` properly, see the [Implicitly typed local variables](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables) section on the C# Coding Guidelines article.</span></span>

## <a name="see-also"></a><span data-ttu-id="291d1-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="291d1-147">See also</span></span>

- [<span data-ttu-id="291d1-148">C# 參考</span><span class="sxs-lookup"><span data-stu-id="291d1-148">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="291d1-149">隱含型別陣列</span><span class="sxs-lookup"><span data-stu-id="291d1-149">Implicitly Typed Arrays</span></span>](../arrays/implicitly-typed-arrays.md)
- [<span data-ttu-id="291d1-150">如何在查詢運算式中使用隱式鍵入的區域變數和陣列</span><span class="sxs-lookup"><span data-stu-id="291d1-150">How to use implicitly typed local variables and arrays in a query expression</span></span>](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [<span data-ttu-id="291d1-151">匿名型別</span><span class="sxs-lookup"><span data-stu-id="291d1-151">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="291d1-152">物件和集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="291d1-152">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
- [<span data-ttu-id="291d1-153">無 功</span><span class="sxs-lookup"><span data-stu-id="291d1-153">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="291d1-154">C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="291d1-154">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="291d1-155">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="291d1-155">LINQ (Language-Integrated Query)</span></span>](../../linq/index.md)
- [<span data-ttu-id="291d1-156">對於</span><span class="sxs-lookup"><span data-stu-id="291d1-156">for</span></span>](../../language-reference/keywords/for.md)
- [<span data-ttu-id="291d1-157">foreach、in</span><span class="sxs-lookup"><span data-stu-id="291d1-157">foreach, in</span></span>](../../language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="291d1-158">使用語句</span><span class="sxs-lookup"><span data-stu-id="291d1-158">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
