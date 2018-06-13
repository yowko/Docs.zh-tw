---
title: 自動產生 (F#)
description: '了解如何 F # 自動一般化的引數和類型的函式，讓它們能夠以盡可能多個類型。'
ms.date: 05/16/2016
ms.openlocfilehash: 858c8bab4a1a37f44a700744e70ebfa8a5abf12c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565071"
---
# <a name="automatic-generalization"></a><span data-ttu-id="88e41-103">自動一般化</span><span class="sxs-lookup"><span data-stu-id="88e41-103">Automatic Generalization</span></span>

<span data-ttu-id="88e41-104">F # 使用類型推斷來評估函式和運算式的類型。</span><span class="sxs-lookup"><span data-stu-id="88e41-104">F# uses type inference to evaluate the types of functions and expressions.</span></span> <span data-ttu-id="88e41-105">本主題描述如何 F # 自動一般化的引數和類型的函式，讓它們能夠以多個類型時，這是可行的。</span><span class="sxs-lookup"><span data-stu-id="88e41-105">This topic describes how F# automatically generalizes the arguments and types of functions so that they work with multiple types when this is possible.</span></span>


## <a name="automatic-generalization"></a><span data-ttu-id="88e41-106">自動一般化</span><span class="sxs-lookup"><span data-stu-id="88e41-106">Automatic Generalization</span></span>
<span data-ttu-id="88e41-107">F # 編譯器，函式上執行類型推斷時判斷給定的參數是否為泛型。</span><span class="sxs-lookup"><span data-stu-id="88e41-107">The F# compiler, when it performs type inference on a function, determines whether a given parameter can be generic.</span></span> <span data-ttu-id="88e41-108">編譯器會檢查每個參數，並判斷函式是否有該參數的特定類型上相依性。</span><span class="sxs-lookup"><span data-stu-id="88e41-108">The compiler examines each parameter and determines whether the function has a dependency on the specific type of that parameter.</span></span> <span data-ttu-id="88e41-109">如果不存在，推斷的類型是泛型。</span><span class="sxs-lookup"><span data-stu-id="88e41-109">If it does not, the type is inferred to be generic.</span></span>

<span data-ttu-id="88e41-110">下列程式碼範例說明的函式，編譯器會推斷為泛型。</span><span class="sxs-lookup"><span data-stu-id="88e41-110">The following code example illustrates a function that the compiler infers to be generic.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

<span data-ttu-id="88e41-111">型別就會推斷`'a -> 'a -> 'a`。</span><span class="sxs-lookup"><span data-stu-id="88e41-111">The type is inferred to be `'a -> 'a -> 'a`.</span></span>

<span data-ttu-id="88e41-112">類型表示這是函數會採用相同的類型不明的兩個引數並傳回該相同類型的值。</span><span class="sxs-lookup"><span data-stu-id="88e41-112">The type indicates that this is a function that takes two arguments of the same unknown type and returns a value of that same type.</span></span> <span data-ttu-id="88e41-113">其中一個原因可能是先前的函式，一般是較大-運算子 (`>`) 本身為泛型。</span><span class="sxs-lookup"><span data-stu-id="88e41-113">One of the reasons that the previous function can be generic is that the greater-than operator (`>`) is itself generic.</span></span> <span data-ttu-id="88e41-114">較大者為非運算子具有的簽章`'a -> 'a -> bool`。</span><span class="sxs-lookup"><span data-stu-id="88e41-114">The greater-than operator has the signature `'a -> 'a -> bool`.</span></span> <span data-ttu-id="88e41-115">並非所有運算子都是泛型，並無法一般化函式中的程式碼會使用參數型別與非泛型函式或運算子，如果該參數的型別。</span><span class="sxs-lookup"><span data-stu-id="88e41-115">Not all operators are generic, and if the code in a function uses a parameter type together with a non-generic function or operator, that parameter type cannot be generalized.</span></span>

<span data-ttu-id="88e41-116">因為`max`是泛型，它可以與類型搭配使用這類`int`， `float`，依此類推，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="88e41-116">Because `max` is generic, it can be used with types such as `int`, `float`, and so on, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

<span data-ttu-id="88e41-117">不過，兩個引數必須是相同的型別。</span><span class="sxs-lookup"><span data-stu-id="88e41-117">However, the two arguments must be of the same type.</span></span> <span data-ttu-id="88e41-118">簽章`'a -> 'a -> 'a`，而非`'a -> 'b -> 'a`。</span><span class="sxs-lookup"><span data-stu-id="88e41-118">The signature is `'a -> 'a -> 'a`, not `'a -> 'b -> 'a`.</span></span> <span data-ttu-id="88e41-119">因此，下列程式碼產生的錯誤，因為類型不相符。</span><span class="sxs-lookup"><span data-stu-id="88e41-119">Therefore, the following code produces an error because the types do not match.</span></span>

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

<span data-ttu-id="88e41-120">`max`函式也可以搭配任何支援較大的類型-高於運算子。</span><span class="sxs-lookup"><span data-stu-id="88e41-120">The `max` function also works with any type that supports the greater-than operator.</span></span> <span data-ttu-id="88e41-121">因此，您也可以使用它來處理字串，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="88e41-121">Therefore, you could also use it on a string, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet104.fs)]
    
## <a name="value-restriction"></a><span data-ttu-id="88e41-122">值限制</span><span class="sxs-lookup"><span data-stu-id="88e41-122">Value Restriction</span></span>
<span data-ttu-id="88e41-123">只有完整的函式定義，具有明確的引數，與簡單不可變的值，編譯器會執行自動一般化。</span><span class="sxs-lookup"><span data-stu-id="88e41-123">The compiler performs automatic generalization only on complete function definitions that have explicit arguments, and on simple immutable values.</span></span>

<span data-ttu-id="88e41-124">這表示編譯器會發出錯誤，如果您嘗試編譯的程式碼完全不被限制為特定的類型，但是也不是一般化。</span><span class="sxs-lookup"><span data-stu-id="88e41-124">This means that the compiler issues an error if you try to compile code that is not sufficiently constrained to be a specific type, but is also not generalizable.</span></span> <span data-ttu-id="88e41-125">這個問題的錯誤訊息是指在自動產生的值做為這項限制*值限制*。</span><span class="sxs-lookup"><span data-stu-id="88e41-125">The error message for this problem refers to this restriction on automatic generalization for values as the *value restriction*.</span></span>

<span data-ttu-id="88e41-126">通常，當您想要的建構泛型，但編譯器有足夠的資訊來一般化，或當您不小心省略足夠的類型資訊的非泛型建構時，就會發生值限制的錯誤。</span><span class="sxs-lookup"><span data-stu-id="88e41-126">Typically, the value restriction error occurs either when you want a construct to be generic but the compiler has insufficient information to generalize it, or when you unintentionally omit sufficient type information in a nongeneric construct.</span></span> <span data-ttu-id="88e41-127">值限制錯誤解決方法是提供更明確的資訊，以更完整限制類型推斷問題，請以下列方式之一：</span><span class="sxs-lookup"><span data-stu-id="88e41-127">The solution to the value restriction error is to provide more explicit information to more fully constrain the type inference problem, in one of the following ways:</span></span>


- <span data-ttu-id="88e41-128">限制為非泛型的值或參數中加入明確的型別註解的類型。</span><span class="sxs-lookup"><span data-stu-id="88e41-128">Constrain a type to be nongeneric by adding an explicit type annotation to a value or parameter.</span></span>

- <span data-ttu-id="88e41-129">如果問題使用定義的泛型函式，例如函式複合 nongeneralizable 建構，或是完全套用局部調用函式引數，請重寫為一般函式定義函式。</span><span class="sxs-lookup"><span data-stu-id="88e41-129">If the problem is using a nongeneralizable construct to define a generic function, such as a function composition or incompletely applied curried function arguments, try to rewrite the function as an ordinary function definition.</span></span>

- <span data-ttu-id="88e41-130">如果問題太複雜，一般化的運算式，讓它成為函式加入額外的、 未使用的參數。</span><span class="sxs-lookup"><span data-stu-id="88e41-130">If the problem is an expression that is too complex to be generalized, make it into a function by adding an extra, unused parameter.</span></span>

- <span data-ttu-id="88e41-131">新增明確的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="88e41-131">Add explicit generic type parameters.</span></span> <span data-ttu-id="88e41-132">很少使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="88e41-132">This option is rarely used.</span></span>

- <span data-ttu-id="88e41-133">下列程式碼範例將說明每個案例。</span><span class="sxs-lookup"><span data-stu-id="88e41-133">The following code examples illustrate each of these scenarios.</span></span>

<span data-ttu-id="88e41-134">案例 1： 太複雜的運算式。</span><span class="sxs-lookup"><span data-stu-id="88e41-134">Case 1: Too complex an expression.</span></span> <span data-ttu-id="88e41-135">在此範例中，清單`counter`將`int option ref`，但它不定義為簡單的不變值。</span><span class="sxs-lookup"><span data-stu-id="88e41-135">In this example, the list `counter` is intended to be `int option ref`, but it is not defined as a simple immutable value.</span></span>

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

<span data-ttu-id="88e41-136">案例 2： 使用 nongeneralizable 建構的泛型函式定義。</span><span class="sxs-lookup"><span data-stu-id="88e41-136">Case 2: Using a nongeneralizable construct to define a generic function.</span></span> <span data-ttu-id="88e41-137">在此範例中，建構是 nongeneralizable，因為它涉及套用部分函式引數。</span><span class="sxs-lookup"><span data-stu-id="88e41-137">In this example, the construct is nongeneralizable because it involves partial application of function arguments.</span></span>

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

<span data-ttu-id="88e41-138">案例 3： 加入額外的、 未使用的參數。</span><span class="sxs-lookup"><span data-stu-id="88e41-138">Case 3: Adding an extra, unused parameter.</span></span> <span data-ttu-id="88e41-139">因為此運算式不是簡單的一般化，編譯器會發出值限制的錯誤。</span><span class="sxs-lookup"><span data-stu-id="88e41-139">Because this expression is not simple enough for generalization, the compiler issues the value restriction error.</span></span>

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

<span data-ttu-id="88e41-140">案例 4： 加入型別參數。</span><span class="sxs-lookup"><span data-stu-id="88e41-140">Case 4: Adding type parameters.</span></span>

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

<span data-ttu-id="88e41-141">在最後一個案例中，這個值會成為類型函式，可用於建立值的許多不同的型別，例如，如下所示：</span><span class="sxs-lookup"><span data-stu-id="88e41-141">In the last case, the value becomes a type function, which may be used to create values of many different types, for example as follows:</span></span>

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a><span data-ttu-id="88e41-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88e41-142">See Also</span></span>
[<span data-ttu-id="88e41-143">類型推斷</span><span class="sxs-lookup"><span data-stu-id="88e41-143">Type Inference</span></span>](../type-inference.md)

[<span data-ttu-id="88e41-144">泛型</span><span class="sxs-lookup"><span data-stu-id="88e41-144">Generics</span></span>](index.md)

[<span data-ttu-id="88e41-145">以統計方式解析的類型參數</span><span class="sxs-lookup"><span data-stu-id="88e41-145">Statically Resolved Type Parameters</span></span>](statically-resolved-type-parameters.md)

[<span data-ttu-id="88e41-146">條件約束</span><span class="sxs-lookup"><span data-stu-id="88e41-146">Constraints</span></span>](constraints.md)

