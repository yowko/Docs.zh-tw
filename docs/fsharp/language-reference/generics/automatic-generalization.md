---
title: 自動一般化
description: 瞭解如何F#自動一般化引數和類型的函式, 以便在可能的情況下使用多個類型。
ms.date: 05/16/2016
ms.openlocfilehash: 501749a190d9770cbcd9848e3d528cba32fe6762
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630633"
---
# <a name="automatic-generalization"></a><span data-ttu-id="35e6b-103">自動一般化</span><span class="sxs-lookup"><span data-stu-id="35e6b-103">Automatic Generalization</span></span>

<span data-ttu-id="35e6b-104">F#使用型別推斷來評估函數和運算式的類型。</span><span class="sxs-lookup"><span data-stu-id="35e6b-104">F# uses type inference to evaluate the types of functions and expressions.</span></span> <span data-ttu-id="35e6b-105">本主題描述如何F#自動一般化引數和類型的函式, 以便在可能的情況下使用多個類型。</span><span class="sxs-lookup"><span data-stu-id="35e6b-105">This topic describes how F# automatically generalizes the arguments and types of functions so that they work with multiple types when this is possible.</span></span>

## <a name="automatic-generalization"></a><span data-ttu-id="35e6b-106">自動一般化</span><span class="sxs-lookup"><span data-stu-id="35e6b-106">Automatic Generalization</span></span>

<span data-ttu-id="35e6b-107">當F#編譯器在函式上執行型別推斷時, 會判斷指定的參數是否可以是泛型。</span><span class="sxs-lookup"><span data-stu-id="35e6b-107">The F# compiler, when it performs type inference on a function, determines whether a given parameter can be generic.</span></span> <span data-ttu-id="35e6b-108">編譯器會檢查每個參數, 並判斷函數是否相依于該參數的特定類型。</span><span class="sxs-lookup"><span data-stu-id="35e6b-108">The compiler examines each parameter and determines whether the function has a dependency on the specific type of that parameter.</span></span> <span data-ttu-id="35e6b-109">如果不是, 則會將型別推斷為泛型。</span><span class="sxs-lookup"><span data-stu-id="35e6b-109">If it does not, the type is inferred to be generic.</span></span>

<span data-ttu-id="35e6b-110">下列程式碼範例說明編譯器推斷為泛型的函式。</span><span class="sxs-lookup"><span data-stu-id="35e6b-110">The following code example illustrates a function that the compiler infers to be generic.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

<span data-ttu-id="35e6b-111">類型推斷為`'a -> 'a -> 'a`。</span><span class="sxs-lookup"><span data-stu-id="35e6b-111">The type is inferred to be `'a -> 'a -> 'a`.</span></span>

<span data-ttu-id="35e6b-112">類型指出這是一個函式, 該函式接受相同未知類型的兩個引數, 並傳回該相同類型的值。</span><span class="sxs-lookup"><span data-stu-id="35e6b-112">The type indicates that this is a function that takes two arguments of the same unknown type and returns a value of that same type.</span></span> <span data-ttu-id="35e6b-113">先前的函式可以是泛型的其中一個原因是, 大於運算子 (`>`) 本身就是泛型。</span><span class="sxs-lookup"><span data-stu-id="35e6b-113">One of the reasons that the previous function can be generic is that the greater-than operator (`>`) is itself generic.</span></span> <span data-ttu-id="35e6b-114">大於運算子具有`'a -> 'a -> bool`簽章。</span><span class="sxs-lookup"><span data-stu-id="35e6b-114">The greater-than operator has the signature `'a -> 'a -> bool`.</span></span> <span data-ttu-id="35e6b-115">並非所有運算子都是泛型的, 而且如果函式中的程式碼使用參數類型搭配非泛型函數或運算子, 則該參數類型無法一般化。</span><span class="sxs-lookup"><span data-stu-id="35e6b-115">Not all operators are generic, and if the code in a function uses a parameter type together with a non-generic function or operator, that parameter type cannot be generalized.</span></span>

<span data-ttu-id="35e6b-116">因為`max`是泛型, 所以可以搭配`int`、 `float`等類型使用, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="35e6b-116">Because `max` is generic, it can be used with types such as `int`, `float`, and so on, as shown in the following examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

<span data-ttu-id="35e6b-117">不過, 這兩個引數必須屬於相同的類型。</span><span class="sxs-lookup"><span data-stu-id="35e6b-117">However, the two arguments must be of the same type.</span></span> <span data-ttu-id="35e6b-118">簽章為`'a -> 'a -> 'a`, 而`'a -> 'b -> 'a`非。</span><span class="sxs-lookup"><span data-stu-id="35e6b-118">The signature is `'a -> 'a -> 'a`, not `'a -> 'b -> 'a`.</span></span> <span data-ttu-id="35e6b-119">因此, 下列程式碼會產生錯誤, 因為類型不相符。</span><span class="sxs-lookup"><span data-stu-id="35e6b-119">Therefore, the following code produces an error because the types do not match.</span></span>

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

<span data-ttu-id="35e6b-120">`max`函數也適用于任何支援大於運算子的類型。</span><span class="sxs-lookup"><span data-stu-id="35e6b-120">The `max` function also works with any type that supports the greater-than operator.</span></span> <span data-ttu-id="35e6b-121">因此, 您也可以在字串上使用它, 如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="35e6b-121">Therefore, you could also use it on a string, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet104.fs)]

## <a name="value-restriction"></a><span data-ttu-id="35e6b-122">值限制</span><span class="sxs-lookup"><span data-stu-id="35e6b-122">Value Restriction</span></span>

<span data-ttu-id="35e6b-123">編譯器只會在具有明確引數的完整函式定義和簡單的不可變值上執行自動一般化。</span><span class="sxs-lookup"><span data-stu-id="35e6b-123">The compiler performs automatic generalization only on complete function definitions that have explicit arguments, and on simple immutable values.</span></span>

<span data-ttu-id="35e6b-124">這表示編譯器會在您嘗試編譯的程式碼未充分限制為特定類型, 但也無法歸納時發出錯誤。</span><span class="sxs-lookup"><span data-stu-id="35e6b-124">This means that the compiler issues an error if you try to compile code that is not sufficiently constrained to be a specific type, but is also not generalizable.</span></span> <span data-ttu-id="35e6b-125">此問題的錯誤訊息指的是對值進行自動一般化的限制, 做為*值限制*。</span><span class="sxs-lookup"><span data-stu-id="35e6b-125">The error message for this problem refers to this restriction on automatic generalization for values as the *value restriction*.</span></span>

<span data-ttu-id="35e6b-126">一般而言, 當您想要將結構設為泛型, 但編譯器沒有足夠的資訊來將它一般化, 或當您不小心在非泛型結構中省略足夠的類型資訊時, 就會發生值限制錯誤。</span><span class="sxs-lookup"><span data-stu-id="35e6b-126">Typically, the value restriction error occurs either when you want a construct to be generic but the compiler has insufficient information to generalize it, or when you unintentionally omit sufficient type information in a nongeneric construct.</span></span> <span data-ttu-id="35e6b-127">「值限制」錯誤的解決方案, 是以下列其中一種方式提供更明確的資訊, 以更完整地限制型別推斷問題:</span><span class="sxs-lookup"><span data-stu-id="35e6b-127">The solution to the value restriction error is to provide more explicit information to more fully constrain the type inference problem, in one of the following ways:</span></span>

- <span data-ttu-id="35e6b-128">將明確的類型注釋新增至值或參數, 以將類型限制為非泛型。</span><span class="sxs-lookup"><span data-stu-id="35e6b-128">Constrain a type to be nongeneric by adding an explicit type annotation to a value or parameter.</span></span>

- <span data-ttu-id="35e6b-129">如果問題是使用 nongeneralizable 結構來定義泛型函式, 例如函式組合或未完全套用的擴充函式引數, 請嘗試重寫函數做為一般函式定義。</span><span class="sxs-lookup"><span data-stu-id="35e6b-129">If the problem is using a nongeneralizable construct to define a generic function, such as a function composition or incompletely applied curried function arguments, try to rewrite the function as an ordinary function definition.</span></span>

- <span data-ttu-id="35e6b-130">如果問題是太複雜而無法一般化的運算式, 請新增額外的未使用參數, 使其進入函式。</span><span class="sxs-lookup"><span data-stu-id="35e6b-130">If the problem is an expression that is too complex to be generalized, make it into a function by adding an extra, unused parameter.</span></span>

- <span data-ttu-id="35e6b-131">加入明確的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="35e6b-131">Add explicit generic type parameters.</span></span> <span data-ttu-id="35e6b-132">此選項很少使用。</span><span class="sxs-lookup"><span data-stu-id="35e6b-132">This option is rarely used.</span></span>

- <span data-ttu-id="35e6b-133">下列程式碼範例將說明每個案例。</span><span class="sxs-lookup"><span data-stu-id="35e6b-133">The following code examples illustrate each of these scenarios.</span></span>

<span data-ttu-id="35e6b-134">案例 1:運算式太複雜。</span><span class="sxs-lookup"><span data-stu-id="35e6b-134">Case 1: Too complex an expression.</span></span> <span data-ttu-id="35e6b-135">在此範例中, 清單`counter`的目的`int option ref`是, 但未定義為簡單的不可變值。</span><span class="sxs-lookup"><span data-stu-id="35e6b-135">In this example, the list `counter` is intended to be `int option ref`, but it is not defined as a simple immutable value.</span></span>

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

<span data-ttu-id="35e6b-136">案例 2:使用 nongeneralizable 結構來定義泛型函數。</span><span class="sxs-lookup"><span data-stu-id="35e6b-136">Case 2: Using a nongeneralizable construct to define a generic function.</span></span> <span data-ttu-id="35e6b-137">在此範例中, 結構是 nongeneralizable 的, 因為它牽涉到部分應用函式引數。</span><span class="sxs-lookup"><span data-stu-id="35e6b-137">In this example, the construct is nongeneralizable because it involves partial application of function arguments.</span></span>

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

<span data-ttu-id="35e6b-138">案例 3:加入額外、未使用的參數。</span><span class="sxs-lookup"><span data-stu-id="35e6b-138">Case 3: Adding an extra, unused parameter.</span></span> <span data-ttu-id="35e6b-139">因為此運算式不夠簡單, 無法進行一般化, 所以編譯器會發出值限制錯誤。</span><span class="sxs-lookup"><span data-stu-id="35e6b-139">Because this expression is not simple enough for generalization, the compiler issues the value restriction error.</span></span>

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

<span data-ttu-id="35e6b-140">案例 4:加入型別參數。</span><span class="sxs-lookup"><span data-stu-id="35e6b-140">Case 4: Adding type parameters.</span></span>

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

<span data-ttu-id="35e6b-141">在最後一個案例中, 值會變成類型函式, 可用來建立許多不同類型的值, 例如, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="35e6b-141">In the last case, the value becomes a type function, which may be used to create values of many different types, for example as follows:</span></span>

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a><span data-ttu-id="35e6b-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35e6b-142">See also</span></span>

- [<span data-ttu-id="35e6b-143">類型推斷</span><span class="sxs-lookup"><span data-stu-id="35e6b-143">Type Inference</span></span>](../type-inference.md)
- [<span data-ttu-id="35e6b-144">泛型</span><span class="sxs-lookup"><span data-stu-id="35e6b-144">Generics</span></span>](index.md)
- [<span data-ttu-id="35e6b-145">以統計方式解析的類型參數</span><span class="sxs-lookup"><span data-stu-id="35e6b-145">Statically Resolved Type Parameters</span></span>](statically-resolved-type-parameters.md)
- [<span data-ttu-id="35e6b-146">條件約束</span><span class="sxs-lookup"><span data-stu-id="35e6b-146">Constraints</span></span>](constraints.md)
