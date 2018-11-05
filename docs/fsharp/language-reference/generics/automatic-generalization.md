---
title: 自動產生 (F#)
description: 了解如何 F# 自動一般化的引數和類型的函式，讓它們能夠具有多個類型，可能的話。
ms.date: 05/16/2016
ms.openlocfilehash: 84de9cbb2b9fcf2488393f7dbdfc3b610cdcffb0
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "43855773"
---
# <a name="automatic-generalization"></a><span data-ttu-id="8bc59-103">自動一般化</span><span class="sxs-lookup"><span data-stu-id="8bc59-103">Automatic Generalization</span></span>

<span data-ttu-id="8bc59-104">F# 使用類型推斷來評估函式和運算式的類型。</span><span class="sxs-lookup"><span data-stu-id="8bc59-104">F# uses type inference to evaluate the types of functions and expressions.</span></span> <span data-ttu-id="8bc59-105">本主題描述如何 F# 自動一般化的引數和類型的函式，讓它們能夠具有多個類型如果這麼做。</span><span class="sxs-lookup"><span data-stu-id="8bc59-105">This topic describes how F# automatically generalizes the arguments and types of functions so that they work with multiple types when this is possible.</span></span>

## <a name="automatic-generalization"></a><span data-ttu-id="8bc59-106">自動一般化</span><span class="sxs-lookup"><span data-stu-id="8bc59-106">Automatic Generalization</span></span>

<span data-ttu-id="8bc59-107">F# 編譯器，函式上執行型別推斷時決定是否指定的參數可以是泛型。</span><span class="sxs-lookup"><span data-stu-id="8bc59-107">The F# compiler, when it performs type inference on a function, determines whether a given parameter can be generic.</span></span> <span data-ttu-id="8bc59-108">編譯器會檢查每個參數，並判斷函數是否有該參數的特定類型的相依性。</span><span class="sxs-lookup"><span data-stu-id="8bc59-108">The compiler examines each parameter and determines whether the function has a dependency on the specific type of that parameter.</span></span> <span data-ttu-id="8bc59-109">如果不存在，會推斷型別為泛型。</span><span class="sxs-lookup"><span data-stu-id="8bc59-109">If it does not, the type is inferred to be generic.</span></span>

<span data-ttu-id="8bc59-110">下列程式碼範例會說明編譯器會推斷為泛型的函式。</span><span class="sxs-lookup"><span data-stu-id="8bc59-110">The following code example illustrates a function that the compiler infers to be generic.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

<span data-ttu-id="8bc59-111">型別推斷為`'a -> 'a -> 'a`。</span><span class="sxs-lookup"><span data-stu-id="8bc59-111">The type is inferred to be `'a -> 'a -> 'a`.</span></span>

<span data-ttu-id="8bc59-112">類型表示這是函式會採用相同的未知類型的兩個引數並傳回該相同類型的值。</span><span class="sxs-lookup"><span data-stu-id="8bc59-112">The type indicates that this is a function that takes two arguments of the same unknown type and returns a value of that same type.</span></span> <span data-ttu-id="8bc59-113">其中一個原因，先前的函式可以是泛型是較大者-運算子 (`>`) 本身是泛型。</span><span class="sxs-lookup"><span data-stu-id="8bc59-113">One of the reasons that the previous function can be generic is that the greater-than operator (`>`) is itself generic.</span></span> <span data-ttu-id="8bc59-114">較大者為非運算子的簽章`'a -> 'a -> bool`。</span><span class="sxs-lookup"><span data-stu-id="8bc59-114">The greater-than operator has the signature `'a -> 'a -> bool`.</span></span> <span data-ttu-id="8bc59-115">並非所有運算子都是泛型，和如果函式中的程式碼會使用與非泛型函式或運算子的參數類型，該參數的類型無法一般化。</span><span class="sxs-lookup"><span data-stu-id="8bc59-115">Not all operators are generic, and if the code in a function uses a parameter type together with a non-generic function or operator, that parameter type cannot be generalized.</span></span>

<span data-ttu-id="8bc59-116">因為`max`是泛型，它可以與類型搭配使用這類`int`，`float`等等，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="8bc59-116">Because `max` is generic, it can be used with types such as `int`, `float`, and so on, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

<span data-ttu-id="8bc59-117">不過，兩個引數必須是相同的型別。</span><span class="sxs-lookup"><span data-stu-id="8bc59-117">However, the two arguments must be of the same type.</span></span> <span data-ttu-id="8bc59-118">簽章`'a -> 'a -> 'a`，而非`'a -> 'b -> 'a`。</span><span class="sxs-lookup"><span data-stu-id="8bc59-118">The signature is `'a -> 'a -> 'a`, not `'a -> 'b -> 'a`.</span></span> <span data-ttu-id="8bc59-119">因此，下列程式碼產生錯誤，因為類型不相符。</span><span class="sxs-lookup"><span data-stu-id="8bc59-119">Therefore, the following code produces an error because the types do not match.</span></span>

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

<span data-ttu-id="8bc59-120">`max`函式也適用於任何支援較大的類型-than 運算子。</span><span class="sxs-lookup"><span data-stu-id="8bc59-120">The `max` function also works with any type that supports the greater-than operator.</span></span> <span data-ttu-id="8bc59-121">因此，您也可以使用它來處理字串，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="8bc59-121">Therefore, you could also use it on a string, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet104.fs)]

## <a name="value-restriction"></a><span data-ttu-id="8bc59-122">值限制</span><span class="sxs-lookup"><span data-stu-id="8bc59-122">Value Restriction</span></span>

<span data-ttu-id="8bc59-123">編譯器會執行自動一般化，只有具有明確的引數的完整的函式定義和簡單的不可變值。</span><span class="sxs-lookup"><span data-stu-id="8bc59-123">The compiler performs automatic generalization only on complete function definitions that have explicit arguments, and on simple immutable values.</span></span>

<span data-ttu-id="8bc59-124">這表示編譯器會發出錯誤，如果您嘗試編譯夠未限制為特定的類型，但也不是一般化的程式碼。</span><span class="sxs-lookup"><span data-stu-id="8bc59-124">This means that the compiler issues an error if you try to compile code that is not sufficiently constrained to be a specific type, but is also not generalizable.</span></span> <span data-ttu-id="8bc59-125">此問題的錯誤訊息指的是這項限制的值做為自動一般化*值限制*。</span><span class="sxs-lookup"><span data-stu-id="8bc59-125">The error message for this problem refers to this restriction on automatic generalization for values as the *value restriction*.</span></span>

<span data-ttu-id="8bc59-126">通常，當您想要為泛型的建構，但編譯器有足夠的資訊進行一般化，或當您不小心省略足夠在非泛型建構的類型資訊時，就會發生值限制的錯誤。</span><span class="sxs-lookup"><span data-stu-id="8bc59-126">Typically, the value restriction error occurs either when you want a construct to be generic but the compiler has insufficient information to generalize it, or when you unintentionally omit sufficient type information in a nongeneric construct.</span></span> <span data-ttu-id="8bc59-127">值限制錯誤的解決方案是以提供更完整其中一種以下列方式限制型別推斷問題，更明確的資訊：</span><span class="sxs-lookup"><span data-stu-id="8bc59-127">The solution to the value restriction error is to provide more explicit information to more fully constrain the type inference problem, in one of the following ways:</span></span>

- <span data-ttu-id="8bc59-128">將為非泛型的值或參數中加入明確的型別註解類型的限制。</span><span class="sxs-lookup"><span data-stu-id="8bc59-128">Constrain a type to be nongeneric by adding an explicit type annotation to a value or parameter.</span></span>

- <span data-ttu-id="8bc59-129">如果問題使用 nongeneralizable 建構來定義的泛型函式，例如函式組合，或完全套用局部調用的函式引數，請嘗試重寫為一般函式定義函式。</span><span class="sxs-lookup"><span data-stu-id="8bc59-129">If the problem is using a nongeneralizable construct to define a generic function, such as a function composition or incompletely applied curried function arguments, try to rewrite the function as an ordinary function definition.</span></span>

- <span data-ttu-id="8bc59-130">如果問題是一般化，讓它執行函式，方法是新增額外的、 未使用的參數太複雜的運算式。</span><span class="sxs-lookup"><span data-stu-id="8bc59-130">If the problem is an expression that is too complex to be generalized, make it into a function by adding an extra, unused parameter.</span></span>

- <span data-ttu-id="8bc59-131">新增明確的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="8bc59-131">Add explicit generic type parameters.</span></span> <span data-ttu-id="8bc59-132">此選項很少使用。</span><span class="sxs-lookup"><span data-stu-id="8bc59-132">This option is rarely used.</span></span>

- <span data-ttu-id="8bc59-133">下列程式碼範例將說明每個案例。</span><span class="sxs-lookup"><span data-stu-id="8bc59-133">The following code examples illustrate each of these scenarios.</span></span>

<span data-ttu-id="8bc59-134">案例 1： 太複雜的運算式。</span><span class="sxs-lookup"><span data-stu-id="8bc59-134">Case 1: Too complex an expression.</span></span> <span data-ttu-id="8bc59-135">在此範例中，清單`counter`就是要`int option ref`，但它並未定義為簡單的不可變值。</span><span class="sxs-lookup"><span data-stu-id="8bc59-135">In this example, the list `counter` is intended to be `int option ref`, but it is not defined as a simple immutable value.</span></span>

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

<span data-ttu-id="8bc59-136">案例 2： 使用 nongeneralizable 建構來定義的泛型函式。</span><span class="sxs-lookup"><span data-stu-id="8bc59-136">Case 2: Using a nongeneralizable construct to define a generic function.</span></span> <span data-ttu-id="8bc59-137">在此範例中，建構會是 nongeneralizable，因為它牽涉到部分套用函式引數。</span><span class="sxs-lookup"><span data-stu-id="8bc59-137">In this example, the construct is nongeneralizable because it involves partial application of function arguments.</span></span>

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

<span data-ttu-id="8bc59-138">案例 3： 新增額外的、 未使用的參數。</span><span class="sxs-lookup"><span data-stu-id="8bc59-138">Case 3: Adding an extra, unused parameter.</span></span> <span data-ttu-id="8bc59-139">因為此運算式不是簡單的一般化，編譯器會發出值限制的錯誤。</span><span class="sxs-lookup"><span data-stu-id="8bc59-139">Because this expression is not simple enough for generalization, the compiler issues the value restriction error.</span></span>

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

<span data-ttu-id="8bc59-140">案例 4： 加入型別參數。</span><span class="sxs-lookup"><span data-stu-id="8bc59-140">Case 4: Adding type parameters.</span></span>

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

<span data-ttu-id="8bc59-141">在最後一個案例中，值會成為類型函式，可用來建立值的許多不同的類型，例如，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8bc59-141">In the last case, the value becomes a type function, which may be used to create values of many different types, for example as follows:</span></span>

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a><span data-ttu-id="8bc59-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8bc59-142">See also</span></span>

- [<span data-ttu-id="8bc59-143">類型推斷</span><span class="sxs-lookup"><span data-stu-id="8bc59-143">Type Inference</span></span>](../type-inference.md)
- [<span data-ttu-id="8bc59-144">泛型</span><span class="sxs-lookup"><span data-stu-id="8bc59-144">Generics</span></span>](index.md)
- [<span data-ttu-id="8bc59-145">以統計方式解析的類型參數</span><span class="sxs-lookup"><span data-stu-id="8bc59-145">Statically Resolved Type Parameters</span></span>](statically-resolved-type-parameters.md)
- [<span data-ttu-id="8bc59-146">條件約束</span><span class="sxs-lookup"><span data-stu-id="8bc59-146">Constraints</span></span>](constraints.md)
