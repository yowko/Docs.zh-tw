---
title: Tuple
description: '深入瞭解 F # 元組，這是一組未命名但已排序的值，可能會有不同的類型。'
ms.date: 05/16/2016
ms.openlocfilehash: 5d26fd5d7ec5b4939a895a6d2a6a0d7fc6c6c733
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173285"
---
# <a name="tuples"></a><span data-ttu-id="84087-103">Tuple</span><span class="sxs-lookup"><span data-stu-id="84087-103">Tuples</span></span>

<span data-ttu-id="84087-104">*元組*是未命名但已排序值的群組，可能會有不同的類型。</span><span class="sxs-lookup"><span data-stu-id="84087-104">A *tuple* is a grouping of unnamed but ordered values, possibly of different types.</span></span>  <span data-ttu-id="84087-105">元組可以是參考型別或結構。</span><span class="sxs-lookup"><span data-stu-id="84087-105">Tuples can either be reference types or structs.</span></span>

## <a name="syntax"></a><span data-ttu-id="84087-106">語法</span><span class="sxs-lookup"><span data-stu-id="84087-106">Syntax</span></span>

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a><span data-ttu-id="84087-107">備註</span><span class="sxs-lookup"><span data-stu-id="84087-107">Remarks</span></span>

<span data-ttu-id="84087-108">上述*語法中的*每個專案可以是任何有效的 F # 運算式。</span><span class="sxs-lookup"><span data-stu-id="84087-108">Each *element* in the previous syntax can be any valid F# expression.</span></span>

## <a name="examples"></a><span data-ttu-id="84087-109">範例</span><span class="sxs-lookup"><span data-stu-id="84087-109">Examples</span></span>

<span data-ttu-id="84087-110">元組範例包括相同或不同類型的配對、三合一等等。</span><span class="sxs-lookup"><span data-stu-id="84087-110">Examples of tuples include pairs, triples, and so on, of the same or different types.</span></span> <span data-ttu-id="84087-111">下列程式碼說明一些範例。</span><span class="sxs-lookup"><span data-stu-id="84087-111">Some examples are illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a><span data-ttu-id="84087-112">取得個別值</span><span class="sxs-lookup"><span data-stu-id="84087-112">Obtaining Individual Values</span></span>

<span data-ttu-id="84087-113">您可以使用模式比對來存取和指派元組元素的名稱，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="84087-113">You can use pattern matching to access and assign names for tuple elements, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

<span data-ttu-id="84087-114">您也可以透過系結，透過運算式外部的模式比對來解構元組 `match` `let` ：</span><span class="sxs-lookup"><span data-stu-id="84087-114">You can also deconstruct a tuple via pattern matching outside of a `match` expression via  `let` binding:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

<span data-ttu-id="84087-115">或者，您可以在元組上進行模式比對，以作為函數的輸入：</span><span class="sxs-lookup"><span data-stu-id="84087-115">Or you can pattern match on tuples as inputs to functions:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

<span data-ttu-id="84087-116">如果您只需要元組的一個元素，則可以使用底線)  (萬用字元來避免為不需要的值建立新名稱。</span><span class="sxs-lookup"><span data-stu-id="84087-116">If you need only one element of the tuple, the wildcard character (the underscore) can be used to avoid creating a new name for a value that you do not need.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

<span data-ttu-id="84087-117">將元素從參考元組複製到結構元組也很簡單：</span><span class="sxs-lookup"><span data-stu-id="84087-117">Copying elements from a reference tuple into a struct tuple is also simple:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

<span data-ttu-id="84087-118">函數 `fst` 和 `snd` (參考元組僅) 會分別傳回元組的第一個和第二個元素。</span><span class="sxs-lookup"><span data-stu-id="84087-118">The functions `fst` and `snd` (reference tuples only) return the first and second elements of a tuple, respectively.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

<span data-ttu-id="84087-119">沒有任何內建函數會傳回第三個元素，但您可以輕鬆地撰寫一個，如下所示。</span><span class="sxs-lookup"><span data-stu-id="84087-119">There is no built-in function that returns the third element of a triple, but you can easily write one as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

<span data-ttu-id="84087-120">一般來說，最好是使用模式比對來存取個別的元組元素。</span><span class="sxs-lookup"><span data-stu-id="84087-120">Generally, it is better to use pattern matching to access individual tuple elements.</span></span>

## <a name="using-tuples"></a><span data-ttu-id="84087-121">使用元組</span><span class="sxs-lookup"><span data-stu-id="84087-121">Using Tuples</span></span>

<span data-ttu-id="84087-122">元組提供一個便利的方式，可從函式傳回多個值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="84087-122">Tuples provide a convenient way to return multiple values from a function, as shown in the following example.</span></span> <span data-ttu-id="84087-123">這個範例會執行整數除法，並將運算的四捨五入結果當做元組配對的第一個成員，並將餘數當做配對的第二個成員。</span><span class="sxs-lookup"><span data-stu-id="84087-123">This example performs integer division and returns the rounded result of the operation as a first member of a tuple pair and the remainder as a second member of the pair.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

<span data-ttu-id="84087-124">當您想要避免使用一般函式語法所隱含之函式引數的隱含 currying 時，元組也可以做為函數引數。</span><span class="sxs-lookup"><span data-stu-id="84087-124">Tuples can also be used as function arguments when you want to avoid the implicit currying of function arguments that is implied by the usual function syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

<span data-ttu-id="84087-125">定義函式的一般語法可 `let sum a b = a + b` 讓您定義函式，該函式是函式第一個引數的部分應用，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="84087-125">The usual syntax for defining the function `let sum a b = a + b` enables you to define a function that is the partial application of the first argument of the function, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

<span data-ttu-id="84087-126">使用元組作為參數時，會停用 currying。</span><span class="sxs-lookup"><span data-stu-id="84087-126">Using a tuple as the parameter disables currying.</span></span> <span data-ttu-id="84087-127">如需詳細資訊，請參閱[函數](./functions/index.md)中的「部分引數應用程式」。</span><span class="sxs-lookup"><span data-stu-id="84087-127">For more information, see "Partial Application of Arguments" in [Functions](./functions/index.md).</span></span>

## <a name="names-of-tuple-types"></a><span data-ttu-id="84087-128">元組類型的名稱</span><span class="sxs-lookup"><span data-stu-id="84087-128">Names of Tuple Types</span></span>

<span data-ttu-id="84087-129">當您寫出屬於元組的型別名稱時，您可以使用 `*` 符號來分隔元素。</span><span class="sxs-lookup"><span data-stu-id="84087-129">When you write out the name of a type that is a tuple, you use the `*` symbol to separate elements.</span></span> <span data-ttu-id="84087-130">若為包含、和的元組（例如）， `int` `float` 則會 `string` `(10, 10.0, "ten")` 以下列方式寫入類型。</span><span class="sxs-lookup"><span data-stu-id="84087-130">For a tuple that consists of an `int`, a `float`, and a `string`, such as `(10, 10.0, "ten")`, the type would be written as follows.</span></span>

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a><span data-ttu-id="84087-131">與 c # 元組的交互操作</span><span class="sxs-lookup"><span data-stu-id="84087-131">Interoperation with C# Tuples</span></span>

<span data-ttu-id="84087-132">C # 7.0 引進了語言的元組。</span><span class="sxs-lookup"><span data-stu-id="84087-132">C# 7.0 introduced tuples to the language.</span></span>  <span data-ttu-id="84087-133">C # 中的元組是結構，而且相當於 F # 中的結構元組。</span><span class="sxs-lookup"><span data-stu-id="84087-133">Tuples in C# are structs, and are equivalent to struct tuples in F#.</span></span>  <span data-ttu-id="84087-134">如果您需要與 c # 交互操作，您必須使用結構元組。</span><span class="sxs-lookup"><span data-stu-id="84087-134">If you need to interoperate with C#, you must use struct tuples.</span></span>

<span data-ttu-id="84087-135">這很容易執行。</span><span class="sxs-lookup"><span data-stu-id="84087-135">This is easy to do.</span></span>  <span data-ttu-id="84087-136">例如，假設您必須將元組傳遞至 c # 類別，然後使用其結果，這也是一個元組：</span><span class="sxs-lookup"><span data-stu-id="84087-136">For example, imagine you have to pass a tuple to a C# class and then consume its result, which is also a tuple:</span></span>

```csharp
namespace CSharpTupleInterop
{
    public static class Example
    {
        public static (int, int) AddOneToXAndY((int x, int y) a) =>
            (a.x + 1, a.y + 1);
    }
}
```

<span data-ttu-id="84087-137">在您的 F # 程式碼中，您可以接著傳遞結構元組做為參數，並將結果當做結構元組來使用。</span><span class="sxs-lookup"><span data-stu-id="84087-137">In your F# code, you can then pass a struct tuple as the parameter and consume the result as a struct tuple.</span></span>

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a><span data-ttu-id="84087-138">在參考元組和結構元組之間轉換</span><span class="sxs-lookup"><span data-stu-id="84087-138">Converting between Reference Tuples and Struct Tuples</span></span>

<span data-ttu-id="84087-139">因為參考元組和結構元組具有完全不同的基礎標記法，所以它們無法隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="84087-139">Because Reference Tuples and Struct Tuples have a completely different underlying representation, they are not implicitly convertible.</span></span>  <span data-ttu-id="84087-140">也就是說，下面這類程式碼不會進行編譯：</span><span class="sxs-lookup"><span data-stu-id="84087-140">That is, code such as the following won't compile:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

<span data-ttu-id="84087-141">您必須在一個元組上進行比對，並使用組成的部分來建立另一個。</span><span class="sxs-lookup"><span data-stu-id="84087-141">You must pattern match on one tuple and construct the other with the constituent parts.</span></span>  <span data-ttu-id="84087-142">例如︰</span><span class="sxs-lookup"><span data-stu-id="84087-142">For example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a><span data-ttu-id="84087-143">參考元組的已編譯形式</span><span class="sxs-lookup"><span data-stu-id="84087-143">Compiled Form of Reference Tuples</span></span>

<span data-ttu-id="84087-144">本節說明元組在編譯時的形式。</span><span class="sxs-lookup"><span data-stu-id="84087-144">This section explains the form of tuples when they're compiled.</span></span>  <span data-ttu-id="84087-145">除非您的目標是 .NET Framework 3.5 或更低版本，否則不需要閱讀這裡的資訊。</span><span class="sxs-lookup"><span data-stu-id="84087-145">The information here isn't necessary to read unless you are targeting .NET Framework 3.5 or lower.</span></span>

<span data-ttu-id="84087-146">元組會編譯成數個泛型型別之一的物件， `System.Tuple` 這些型別會在 arity 上多載，或型別參數的數目。</span><span class="sxs-lookup"><span data-stu-id="84087-146">Tuples are compiled into objects of one of several generic types, all named `System.Tuple`, that are overloaded on the arity, or number of type parameters.</span></span> <span data-ttu-id="84087-147">當您從另一種語言（例如 c # 或 Visual Basic）或使用不知道 F # 結構的工具時，元組類型會以此形式出現。</span><span class="sxs-lookup"><span data-stu-id="84087-147">Tuple types appear in this form when you view them from another language, such as C# or Visual Basic, or when you are using a tool that is not aware of F# constructs.</span></span> <span data-ttu-id="84087-148">`Tuple`類型是在 .NET Framework 4 中引進。</span><span class="sxs-lookup"><span data-stu-id="84087-148">The `Tuple` types were introduced in .NET Framework 4.</span></span> <span data-ttu-id="84087-149">如果您的目標是舊版的 .NET Framework，編譯器會使用2.0 版本的 F # 核心程式庫中的[system.object](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3)版本。</span><span class="sxs-lookup"><span data-stu-id="84087-149">If you are targeting an earlier version of the .NET Framework, the compiler uses versions of [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) from the 2.0 version of the F# Core Library.</span></span> <span data-ttu-id="84087-150">此程式庫中的類型僅適用于以 .NET Framework 2.0、3.0 和3.5 版本為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="84087-150">The types in this library are used only for applications that target the 2.0, 3.0, and 3.5 versions of the .NET Framework.</span></span> <span data-ttu-id="84087-151">類型轉送是用來確保 .NET Framework 2.0 和 .NET Framework 4 F # 元件之間的二進位相容性。</span><span class="sxs-lookup"><span data-stu-id="84087-151">Type forwarding is used to ensure binary compatibility between .NET Framework 2.0 and .NET Framework 4 F# components.</span></span>

### <a name="compiled-form-of-struct-tuples"></a><span data-ttu-id="84087-152">結構元組的已編譯形式</span><span class="sxs-lookup"><span data-stu-id="84087-152">Compiled Form of Struct Tuples</span></span>

<span data-ttu-id="84087-153">結構元組 (例如， `struct (x, y)`) ，基本上與參考元組不同。</span><span class="sxs-lookup"><span data-stu-id="84087-153">Struct tuples (for example, `struct (x, y)`), are fundamentally different from reference tuples.</span></span>  <span data-ttu-id="84087-154">它們會編譯成 <xref:System.ValueTuple> 型別、以 arity 進行多載，或型別參數的數目。</span><span class="sxs-lookup"><span data-stu-id="84087-154">They are compiled into the <xref:System.ValueTuple> type, overloaded by arity, or the number of type parameters.</span></span>  <span data-ttu-id="84087-155">它們相當於[c # 7.0 元組](../../csharp/language-reference/builtin-types/value-tuples.md)和[Visual Basic 2017 元組](../../visual-basic/programming-guide/language-features/data-types/tuples.md)，並可交互操作雙向。</span><span class="sxs-lookup"><span data-stu-id="84087-155">They are equivalent to [C# 7.0 Tuples](../../csharp/language-reference/builtin-types/value-tuples.md) and [Visual Basic 2017 Tuples](../../visual-basic/programming-guide/language-features/data-types/tuples.md), and interoperate bidirectionally.</span></span>

## <a name="see-also"></a><span data-ttu-id="84087-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84087-156">See also</span></span>

- [<span data-ttu-id="84087-157">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="84087-157">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="84087-158">F# 類型</span><span class="sxs-lookup"><span data-stu-id="84087-158">F# Types</span></span>](fsharp-types.md)
