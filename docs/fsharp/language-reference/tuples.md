---
title: Tuple (F#)
description: '深入了解 F # tuple 的群組不具名但有已排序，可能是不同類型的值。'
ms.date: 05/16/2016
ms.openlocfilehash: e7628e4c4b538c2fe52fca25d2597b10fec28d1c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "43749219"
---
# <a name="tuples"></a><span data-ttu-id="2c15b-103">Tuple</span><span class="sxs-lookup"><span data-stu-id="2c15b-103">Tuples</span></span>

<span data-ttu-id="2c15b-104">A *tuple*是群組不具名但有已排序，可能是不同類型的值。</span><span class="sxs-lookup"><span data-stu-id="2c15b-104">A *tuple* is a grouping of unnamed but ordered values, possibly of different types.</span></span>  <span data-ttu-id="2c15b-105">Tuple 可以是參考型別或結構。</span><span class="sxs-lookup"><span data-stu-id="2c15b-105">Tuples can either be reference types or structs.</span></span>

## <a name="syntax"></a><span data-ttu-id="2c15b-106">語法</span><span class="sxs-lookup"><span data-stu-id="2c15b-106">Syntax</span></span>

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a><span data-ttu-id="2c15b-107">備註</span><span class="sxs-lookup"><span data-stu-id="2c15b-107">Remarks</span></span>

<span data-ttu-id="2c15b-108">每個*項目*在先前的語法可以是任何有效 F # 運算式。</span><span class="sxs-lookup"><span data-stu-id="2c15b-108">Each *element* in the previous syntax can be any valid F# expression.</span></span>

## <a name="examples"></a><span data-ttu-id="2c15b-109">範例</span><span class="sxs-lookup"><span data-stu-id="2c15b-109">Examples</span></span>

<span data-ttu-id="2c15b-110">Tuple 的範例包括組、 三合一、 等等的相同或不同的型別。</span><span class="sxs-lookup"><span data-stu-id="2c15b-110">Examples of tuples include pairs, triples, and so on, of the same or different types.</span></span> <span data-ttu-id="2c15b-111">一些範例是以下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="2c15b-111">Some examples are illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a><span data-ttu-id="2c15b-112">取得個別值</span><span class="sxs-lookup"><span data-stu-id="2c15b-112">Obtaining Individual Values</span></span>

<span data-ttu-id="2c15b-113">您可以使用模式比對來存取和指派名稱的元組元素，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="2c15b-113">You can use pattern matching to access and assign names for tuple elements, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

<span data-ttu-id="2c15b-114">您也可以解構 tuple，以透過模式比對的外部`match`透過運算式`let`繫結：</span><span class="sxs-lookup"><span data-stu-id="2c15b-114">You can also deconstruct a tuple via pattern matching outside of a `match` expression via  `let` binding:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

<span data-ttu-id="2c15b-115">或是您可以在模式比對 tuple 中，做為函式的輸入：</span><span class="sxs-lookup"><span data-stu-id="2c15b-115">Or you can pattern match on tuples as inputs to functions:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

<span data-ttu-id="2c15b-116">如果您需要的只有一個元素的元組，萬用字元 （底線） 可用來避免建立新的名稱，您不需要的值。</span><span class="sxs-lookup"><span data-stu-id="2c15b-116">If you need only one element of the tuple, the wildcard character (the underscore) can be used to avoid creating a new name for a value that you do not need.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

<span data-ttu-id="2c15b-117">將參考 tuple 中的項目複製到的結構元組也很簡單：</span><span class="sxs-lookup"><span data-stu-id="2c15b-117">Copying elements from a reference tuple into a struct tuple is also simple:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

<span data-ttu-id="2c15b-118">函式`fst`和`snd`（參考 tuple 只） 傳回第一個和第二個元素的元組，分別。</span><span class="sxs-lookup"><span data-stu-id="2c15b-118">The functions `fst` and `snd` (reference tuples only) return the first and second elements of a tuple, respectively.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

<span data-ttu-id="2c15b-119">沒有內建函式會傳回三重物件，第三個元素，但您可以輕鬆地撰寫，如下所示。</span><span class="sxs-lookup"><span data-stu-id="2c15b-119">There is no built-in function that returns the third element of a triple, but you can easily write one as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

<span data-ttu-id="2c15b-120">一般而言，最好使用模式比對來存取個別的 tuple 項目。</span><span class="sxs-lookup"><span data-stu-id="2c15b-120">Generally, it is better to use pattern matching to access individual tuple elements.</span></span>

## <a name="using-tuples"></a><span data-ttu-id="2c15b-121">使用 Tuple</span><span class="sxs-lookup"><span data-stu-id="2c15b-121">Using Tuples</span></span>

<span data-ttu-id="2c15b-122">下列範例所示，Tuple 會提供便利的方式，從函式，傳回多個值。</span><span class="sxs-lookup"><span data-stu-id="2c15b-122">Tuples provide a convenient way to return multiple values from a function, as shown in the following example.</span></span> <span data-ttu-id="2c15b-123">此範例會執行整數除法運算，並傳回為元組配對的第一個成員作業，並為第二個配對成員的其餘部分的進位的結果。</span><span class="sxs-lookup"><span data-stu-id="2c15b-123">This example performs integer division and returns the rounded result of the operation as a first member of a tuple pair and the remainder as a second member of the pair.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

<span data-ttu-id="2c15b-124">Tuple 也使用函式引數，當您想要避免隱含對一般函式語法所默許的函式引數。</span><span class="sxs-lookup"><span data-stu-id="2c15b-124">Tuples can also be used as function arguments when you want to avoid the implicit currying of function arguments that is implied by the usual function syntax.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

<span data-ttu-id="2c15b-125">定義函式的一般語法`let sum a b = a + b`可讓您定義部分的應用程式，第一個引數的函式的函式，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="2c15b-125">The usual syntax for defining the function `let sum a b = a + b` enables you to define a function that is the partial application of the first argument of the function, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

<span data-ttu-id="2c15b-126">使用 tuple 的參數會停用對。</span><span class="sxs-lookup"><span data-stu-id="2c15b-126">Using a tuple as the parameter disables currying.</span></span> <span data-ttu-id="2c15b-127">如需詳細資訊，請參閱 「 部分應用程式的引數 」 中[函式](functions/index.md)。</span><span class="sxs-lookup"><span data-stu-id="2c15b-127">For more information, see "Partial Application of Arguments" in [Functions](functions/index.md).</span></span>

## <a name="names-of-tuple-types"></a><span data-ttu-id="2c15b-128">元組類型的名稱</span><span class="sxs-lookup"><span data-stu-id="2c15b-128">Names of Tuple Types</span></span>

<span data-ttu-id="2c15b-129">當您撰寫出的是 tuple 型別名稱時，您會使用`*`符號來分隔元素。</span><span class="sxs-lookup"><span data-stu-id="2c15b-129">When you write out the name of a type that is a tuple, you use the `*` symbol to separate elements.</span></span> <span data-ttu-id="2c15b-130">所組成的 tuple `int`，則`float`，和`string`，例如`(10, 10.0, "ten")`，型別會被寫入，如下所示。</span><span class="sxs-lookup"><span data-stu-id="2c15b-130">For a tuple that consists of an `int`, a `float`, and a `string`, such as `(10, 10.0, "ten")`, the type would be written as follows.</span></span>

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a><span data-ttu-id="2c15b-131">使用 C# Tuple 的互通性</span><span class="sxs-lookup"><span data-stu-id="2c15b-131">Interoperation with C# Tuples</span></span>

<span data-ttu-id="2c15b-132">C# 7.0 引進 tuple 的語言。</span><span class="sxs-lookup"><span data-stu-id="2c15b-132">C# 7.0 introduced tuples to the language.</span></span>  <span data-ttu-id="2c15b-133">Tuple 在 C# 中為結構，並相當於在 F # 中的結構元組。</span><span class="sxs-lookup"><span data-stu-id="2c15b-133">Tuples in C# are structs, and are equivalent to struct tuples in F#.</span></span>  <span data-ttu-id="2c15b-134">如果您需要使用 C# 交互操作，您必須使用結構元組。</span><span class="sxs-lookup"><span data-stu-id="2c15b-134">If you need to interoperate with C#, you must use struct tuples.</span></span>

<span data-ttu-id="2c15b-135">這很簡單。</span><span class="sxs-lookup"><span data-stu-id="2c15b-135">This is easy to do.</span></span>  <span data-ttu-id="2c15b-136">例如，假設您必須將 tuple 傳遞至 C# 類別，然後取用它的結果，這也是 tuple:</span><span class="sxs-lookup"><span data-stu-id="2c15b-136">For example, imagine you have to pass a tuple to a C# class and then consume its result, which is also a tuple:</span></span>

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

<span data-ttu-id="2c15b-137">在 F # 程式碼，您可以再做為參數傳遞的結構元組，並使用結構 tuple 形式的結果。</span><span class="sxs-lookup"><span data-stu-id="2c15b-137">In your F# code, you can then pass a struct tuple as the parameter and consume the result as a struct tuple.</span></span>

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a><span data-ttu-id="2c15b-138">參考 Tuple 及結構元組間的轉換</span><span class="sxs-lookup"><span data-stu-id="2c15b-138">Converting between Reference Tuples and Struct Tuples</span></span>

<span data-ttu-id="2c15b-139">因為參考 Tuple 和結構元組有完全不同的基礎表示法，所以它們不會隱含地轉換。</span><span class="sxs-lookup"><span data-stu-id="2c15b-139">Because Reference Tuples and Struct Tuples have a completely different underlying representation, they are not implicitly convertible.</span></span>  <span data-ttu-id="2c15b-140">也就是說，如下所示的程式碼無法編譯：</span><span class="sxs-lookup"><span data-stu-id="2c15b-140">That is, code such as the following won't compile:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

<span data-ttu-id="2c15b-141">您必須在模式比對一的 tuple，並建構的組成組件與其他。</span><span class="sxs-lookup"><span data-stu-id="2c15b-141">You must pattern match on one tuple and construct the other with the constituent parts.</span></span>  <span data-ttu-id="2c15b-142">例如: </span><span class="sxs-lookup"><span data-stu-id="2c15b-142">For example:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a><span data-ttu-id="2c15b-143">已編譯的形式的參考 Tuple</span><span class="sxs-lookup"><span data-stu-id="2c15b-143">Compiled Form of Reference Tuples</span></span>

<span data-ttu-id="2c15b-144">本章節將說明 tuple 的形式時編譯。</span><span class="sxs-lookup"><span data-stu-id="2c15b-144">This section explains the form of tuples when they're compiled.</span></span>  <span data-ttu-id="2c15b-145">此處提供的資訊不需要讀取，除非您的目標.NET Framework 3.5 或更低。</span><span class="sxs-lookup"><span data-stu-id="2c15b-145">The information here isn't necessary to read unless you are targeting .NET Framework 3.5 or lower.</span></span>

<span data-ttu-id="2c15b-146">Tuple 會編譯成其中一種數個泛型類型，所有具名物件`System.Tuple`的多載上的引數數目或類型參數的數目。</span><span class="sxs-lookup"><span data-stu-id="2c15b-146">Tuples are compiled into objects of one of several generic types, all named `System.Tuple`, that are overloaded on the arity, or number of type parameters.</span></span> <span data-ttu-id="2c15b-147">當您從另一種語言，例如 C# 或 Visual Basic 中，檢視時，或當您使用一種工具，並不知道 F # 建構，元組類型會出現在這種形式。</span><span class="sxs-lookup"><span data-stu-id="2c15b-147">Tuple types appear in this form when you view them from another language, such as C# or Visual Basic, or when you are using a tool that is not aware of F# constructs.</span></span> <span data-ttu-id="2c15b-148">`Tuple` .NET Framework 4 中導入類型。</span><span class="sxs-lookup"><span data-stu-id="2c15b-148">The `Tuple` types were introduced in .NET Framework 4.</span></span> <span data-ttu-id="2c15b-149">如果您的目標是舊版的.NET Framework，編譯器會使用新版[System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3)從 F # 核心程式庫 2.0 版。</span><span class="sxs-lookup"><span data-stu-id="2c15b-149">If you are targeting an earlier version of the .NET Framework, the compiler uses versions of [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) from the 2.0 version of the F# Core Library.</span></span> <span data-ttu-id="2c15b-150">此文件庫中的類型僅用於在 2.0、 3.0 和 3.5 版本的.NET framework 為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2c15b-150">The types in this library are used only for applications that target the 2.0, 3.0, and 3.5 versions of the .NET Framework.</span></span> <span data-ttu-id="2c15b-151">類型轉送用來確保.NET Framework 2.0 和.NET Framework 4 F # 元件之間的二進位相容性。</span><span class="sxs-lookup"><span data-stu-id="2c15b-151">Type forwarding is used to ensure binary compatibility between .NET Framework 2.0 and .NET Framework 4 F# components.</span></span>

### <a name="compiled-form-of-struct-tuples"></a><span data-ttu-id="2c15b-152">已編譯的結構元組的形式</span><span class="sxs-lookup"><span data-stu-id="2c15b-152">Compiled Form of Struct Tuples</span></span>

<span data-ttu-id="2c15b-153">結構元組 (比方說， `struct (x, y)`)，是本質上不同於參考 tuple。</span><span class="sxs-lookup"><span data-stu-id="2c15b-153">Struct tuples (for example, `struct (x, y)`), are fundamentally different from reference tuples.</span></span>  <span data-ttu-id="2c15b-154">還是會編譯至<xref:System.ValueTuple>型別，多載引數數目或類型參數的數目。</span><span class="sxs-lookup"><span data-stu-id="2c15b-154">They are compiled into the <xref:System.ValueTuple> type, overloaded by arity, or the number of type parameters.</span></span>  <span data-ttu-id="2c15b-155">它們是相當於[C# 7.0 Tuple](../../csharp/tuples.md)並[Visual Basic 2017 Tuple](../../visual-basic/programming-guide/language-features/data-types/tuples.md)，以及交互操作雙向。</span><span class="sxs-lookup"><span data-stu-id="2c15b-155">They are equivalent to [C# 7.0 Tuples](../../csharp/tuples.md) and [Visual Basic 2017 Tuples](../../visual-basic/programming-guide/language-features/data-types/tuples.md), and interoperate bidirectionally.</span></span>

## <a name="see-also"></a><span data-ttu-id="2c15b-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c15b-156">See also</span></span>

- [<span data-ttu-id="2c15b-157">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="2c15b-157">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="2c15b-158">F# 類型</span><span class="sxs-lookup"><span data-stu-id="2c15b-158">F# Types</span></span>](fsharp-types.md)
