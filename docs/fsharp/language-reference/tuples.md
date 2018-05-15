---
title: Tuple (F#)
description: '深入了解 F # tuple 的未命名，但已排序的值，可能是不同類型的群組。'
ms.date: 05/16/2016
ms.openlocfilehash: d017a2ce8a6ad9b3cec8dfa2ee15b47f06d8f67c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="tuples"></a><span data-ttu-id="f9310-103">Tuple</span><span class="sxs-lookup"><span data-stu-id="f9310-103">Tuples</span></span>

<span data-ttu-id="f9310-104">A *tuple*是未命名，但已排序，可能是不同類型的值的群組。</span><span class="sxs-lookup"><span data-stu-id="f9310-104">A *tuple* is a grouping of unnamed but ordered values, possibly of different types.</span></span>  <span data-ttu-id="f9310-105">Tuple 可以是參考型別或結構。</span><span class="sxs-lookup"><span data-stu-id="f9310-105">Tuples can either be reference types or structs.</span></span>

## <a name="syntax"></a><span data-ttu-id="f9310-106">語法</span><span class="sxs-lookup"><span data-stu-id="f9310-106">Syntax</span></span>

```fsharp
(element, ... , element)
struct(element, ... ,element )
```
## <a name="remarks"></a><span data-ttu-id="f9310-107">備註</span><span class="sxs-lookup"><span data-stu-id="f9310-107">Remarks</span></span>
<span data-ttu-id="f9310-108">每個*元素*先前語法中可以是任何有效 F # 運算式。</span><span class="sxs-lookup"><span data-stu-id="f9310-108">Each *element* in the previous syntax can be any valid F# expression.</span></span>

## <a name="examples"></a><span data-ttu-id="f9310-109">範例</span><span class="sxs-lookup"><span data-stu-id="f9310-109">Examples</span></span>
<span data-ttu-id="f9310-110">Tuple 的範例包括組、 三合一，依此類推，相同或不同類型。</span><span class="sxs-lookup"><span data-stu-id="f9310-110">Examples of tuples include pairs, triples, and so on, of the same or different types.</span></span> <span data-ttu-id="f9310-111">部分範例是以下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="f9310-111">Some examples are illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]
    
## <a name="obtaining-individual-values"></a><span data-ttu-id="f9310-112">取得個別的值</span><span class="sxs-lookup"><span data-stu-id="f9310-112">Obtaining Individual Values</span></span>
<span data-ttu-id="f9310-113">您可以使用模式比對來存取和指派名稱 tuple 項目，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="f9310-113">You can use pattern matching to access and assign names for tuple elements, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

<span data-ttu-id="f9310-114">您也可以解構模式比對外部透過 tuple`match`透過運算式`let`繫結：</span><span class="sxs-lookup"><span data-stu-id="f9310-114">You can also deconstruct a tuple via pattern matching outside of a `match` expression via  `let` binding:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

<span data-ttu-id="f9310-115">或是您可以在模式比對的 tuple，做為函式的輸入：</span><span class="sxs-lookup"><span data-stu-id="f9310-115">Or you can pattern match on tuples as inputs to functions:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

<span data-ttu-id="f9310-116">如果您需要只能有一個元素的 tuple，萬用字元 （底線） 可用來避免建立不需要值的新名稱。</span><span class="sxs-lookup"><span data-stu-id="f9310-116">If you need only one element of the tuple, the wildcard character (the underscore) can be used to avoid creating a new name for a value that you do not need.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

<span data-ttu-id="f9310-117">將參考 tuple 中的項目複製到結構 tuple 也很簡單：</span><span class="sxs-lookup"><span data-stu-id="f9310-117">Copying elements from a reference tuple into a struct tuple is also simple:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

<span data-ttu-id="f9310-118">函式`fst`和`snd`（參考 tuple 只） 傳回第一個和第二個 tuple 的項目分別。</span><span class="sxs-lookup"><span data-stu-id="f9310-118">The functions `fst` and `snd` (reference tuples only) return the first and second elements of a tuple, respectively.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

<span data-ttu-id="f9310-119">沒有內建函式，會傳回第三個元素的三倍，但您可以輕鬆地撰寫一個，如下所示。</span><span class="sxs-lookup"><span data-stu-id="f9310-119">There is no built-in function that returns the third element of a triple, but you can easily write one as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

<span data-ttu-id="f9310-120">一般而言，最好使用模式比對以存取個別的 tuple 項目。</span><span class="sxs-lookup"><span data-stu-id="f9310-120">Generally, it is better to use pattern matching to access individual tuple elements.</span></span>

## <a name="using-tuples"></a><span data-ttu-id="f9310-121">使用 Tuple</span><span class="sxs-lookup"><span data-stu-id="f9310-121">Using Tuples</span></span>
<span data-ttu-id="f9310-122">Tuple 提供便利的方式從函式，傳回多個值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="f9310-122">Tuples provide a convenient way to return multiple values from a function, as shown in the following example.</span></span> <span data-ttu-id="f9310-123">此範例會執行整數除法運算，並傳回 tuple 配對的第一個成員作業，並為第二個配對成員的其餘部分的進位的結果。</span><span class="sxs-lookup"><span data-stu-id="f9310-123">This example performs integer division and returns the rounded result of the operation as a first member of a tuple pair and the remainder as a second member of the pair.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

<span data-ttu-id="f9310-124">Tuple 也使用做為函式引數，當您想要避免隱含對一般函式語法所隱含的函式引數。</span><span class="sxs-lookup"><span data-stu-id="f9310-124">Tuples can also be used as function arguments when you want to avoid the implicit currying of function arguments that is implied by the usual function syntax.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

<span data-ttu-id="f9310-125">定義函式的一般語法`let sum a b = a + b`可讓您定義部分的應用程式的函式，第一個引數的函式，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="f9310-125">The usual syntax for defining the function `let sum a b = a + b` enables you to define a function that is the partial application of the first argument of the function, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

<span data-ttu-id="f9310-126">使用 tuple 做為參數會停用對。</span><span class="sxs-lookup"><span data-stu-id="f9310-126">Using a tuple as the parameter disables currying.</span></span> <span data-ttu-id="f9310-127">如需詳細資訊，請參閱 「 部分應用程式的引數 」 中[函式](functions/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f9310-127">For more information, see "Partial Application of Arguments" in [Functions](functions/index.md).</span></span>

## <a name="names-of-tuple-types"></a><span data-ttu-id="f9310-128">Tuple 類型的名稱</span><span class="sxs-lookup"><span data-stu-id="f9310-128">Names of Tuple Types</span></span>
<span data-ttu-id="f9310-129">當您撰寫的是 tuple 的類型名稱時，您會使用`*`符號來分隔項目。</span><span class="sxs-lookup"><span data-stu-id="f9310-129">When you write out the name of a type that is a tuple, you use the `*` symbol to separate elements.</span></span> <span data-ttu-id="f9310-130">包含 tuple `int`、 `float`，和`string`，例如`(10, 10.0, "ten")`，型別會被寫入，如下所示。</span><span class="sxs-lookup"><span data-stu-id="f9310-130">For a tuple that consists of an `int`, a `float`, and a `string`, such as `(10, 10.0, "ten")`, the type would be written as follows.</span></span>

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a><span data-ttu-id="f9310-131">與 C# Tuple 的互通</span><span class="sxs-lookup"><span data-stu-id="f9310-131">Interoperation with C# Tuples</span></span>

<span data-ttu-id="f9310-132">C# 7.0 引進 tuple 的語言。</span><span class="sxs-lookup"><span data-stu-id="f9310-132">C# 7.0 introduced tuples to the language.</span></span>  <span data-ttu-id="f9310-133">在 C# 中的 Tuple 結構，而且相當於在 F # 中的結構 tuple。</span><span class="sxs-lookup"><span data-stu-id="f9310-133">Tuples in C# are structs, and are equivalent to struct tuples in F#.</span></span>  <span data-ttu-id="f9310-134">如果您需要使用 C# 交互操作，您必須使用結構 tuple。</span><span class="sxs-lookup"><span data-stu-id="f9310-134">If you need to interoperate with C#, you must use struct tuples.</span></span>

<span data-ttu-id="f9310-135">這是容易的。</span><span class="sxs-lookup"><span data-stu-id="f9310-135">This is easy to do.</span></span>  <span data-ttu-id="f9310-136">例如，假設您必須將 tuple 傳遞至 C# 類別，並使用它的結果，也是 tuple:</span><span class="sxs-lookup"><span data-stu-id="f9310-136">For example, imagine you have to pass a tuple to a C# class and then consume its result, which is also a tuple:</span></span>

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

<span data-ttu-id="f9310-137">在您 F # 程式碼，您可以再傳遞結構 tuple 做為參數，並使用結構 tuple 形式的結果。</span><span class="sxs-lookup"><span data-stu-id="f9310-137">In your F# code, you can then pass a struct tuple as the parameter and consume the result as a struct tuple.</span></span>

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a><span data-ttu-id="f9310-138">參考的 Tuple 與結構間的轉換</span><span class="sxs-lookup"><span data-stu-id="f9310-138">Converting between Reference Tuples and Struct Tuples</span></span>

<span data-ttu-id="f9310-139">參考的 Tuple 與結構已經完全不同的基礎表示法，因為它們都無法隱含地轉換。</span><span class="sxs-lookup"><span data-stu-id="f9310-139">Because Reference Tuples and Struct Tuples have a completely different underlying representation, they are not implicitly convertible.</span></span>  <span data-ttu-id="f9310-140">亦即，不會編譯程式碼如下所示：</span><span class="sxs-lookup"><span data-stu-id="f9310-140">That is, code such as the following won't compile:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

<span data-ttu-id="f9310-141">您必須在模式比對一個 tuple 和構成組件的其他建構。</span><span class="sxs-lookup"><span data-stu-id="f9310-141">You must pattern match on one tuple and construct the other with the constituent parts.</span></span>  <span data-ttu-id="f9310-142">例如: </span><span class="sxs-lookup"><span data-stu-id="f9310-142">For example:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a><span data-ttu-id="f9310-143">參考 Tuple 的編譯的形式</span><span class="sxs-lookup"><span data-stu-id="f9310-143">Compiled Form of Reference Tuples</span></span>
<span data-ttu-id="f9310-144">本章節將說明它們在編譯時的 tuple 形式。</span><span class="sxs-lookup"><span data-stu-id="f9310-144">This section explains the form of tuples when they're compiled.</span></span>  <span data-ttu-id="f9310-145">這裡的資訊不需要讀取，除非您的目標.NET Framework 3.5 或更低。</span><span class="sxs-lookup"><span data-stu-id="f9310-145">The information here isn't necessary to read unless you are targeting .NET Framework 3.5 or lower.</span></span>

<span data-ttu-id="f9310-146">Tuple 會編譯為物件的其中一種數個泛型類型，所有具名`System.Tuple`，引數數目，則型別參數數目上的多載。</span><span class="sxs-lookup"><span data-stu-id="f9310-146">Tuples are compiled into objects of one of several generic types, all named `System.Tuple`, that are overloaded on the arity, or number of type parameters.</span></span> <span data-ttu-id="f9310-147">當您從另一種語言，例如 C# 或 Visual Basic 中，檢視時，或當您使用一種工具，並不知道 F # 建構 Tuple 類型就會出現在這種形式。</span><span class="sxs-lookup"><span data-stu-id="f9310-147">Tuple types appear in this form when you view them from another language, such as C# or Visual Basic, or when you are using a tool that is not aware of F# constructs.</span></span> <span data-ttu-id="f9310-148">`Tuple` .NET Framework 4 中導入型別。</span><span class="sxs-lookup"><span data-stu-id="f9310-148">The `Tuple` types were introduced in .NET Framework 4.</span></span> <span data-ttu-id="f9310-149">如果您的目標舊版的.NET Framework，編譯器會使用新版[System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3)從 F # 核心程式庫 2.0 版。</span><span class="sxs-lookup"><span data-stu-id="f9310-149">If you are targeting an earlier version of the .NET Framework, the compiler uses versions of [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) from the 2.0 version of the F# Core Library.</span></span> <span data-ttu-id="f9310-150">此文件庫中的類型只能用於以 2.0、 3.0 和 3.5 版本的.NET Framework 為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f9310-150">The types in this library are used only for applications that target the 2.0, 3.0, and 3.5 versions of the .NET Framework.</span></span> <span data-ttu-id="f9310-151">類型轉送用來確保.NET Framework 2.0 和.NET Framework 4 F # 元件之間的二進位碼相容性。</span><span class="sxs-lookup"><span data-stu-id="f9310-151">Type forwarding is used to ensure binary compatibility between .NET Framework 2.0 and .NET Framework 4 F# components.</span></span>

### <a name="compiled-form-of-struct-tuples"></a><span data-ttu-id="f9310-152">編譯的結構 Tuple 形式</span><span class="sxs-lookup"><span data-stu-id="f9310-152">Compiled Form of Struct Tuples</span></span>

<span data-ttu-id="f9310-153">Tuple 結構 (例如， `struct (x, y)`)，基本上不同於參考 tuple。</span><span class="sxs-lookup"><span data-stu-id="f9310-153">Struct tuples (for example, `struct (x, y)`), are fundamentally different from reference tuples.</span></span>  <span data-ttu-id="f9310-154">編譯成<xref:System.ValueTuple>型別引數數目或型別參數數目所多載。</span><span class="sxs-lookup"><span data-stu-id="f9310-154">They are compiled into the <xref:System.ValueTuple> type, overloaded by arity, or the number of type parameters.</span></span>  <span data-ttu-id="f9310-155">它們是相當於[C# 7.0 Tuple](../../csharp/tuples.md)和[Visual Basic 2017 Tuple](../../visual-basic/programming-guide/language-features/data-types/tuples.md)，以及雙向交互操作。</span><span class="sxs-lookup"><span data-stu-id="f9310-155">They are equivalent to [C# 7.0 Tuples](../../csharp/tuples.md) and [Visual Basic 2017 Tuples](../../visual-basic/programming-guide/language-features/data-types/tuples.md), and interoperate bidirectionally.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9310-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9310-156">See Also</span></span>
[<span data-ttu-id="f9310-157">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="f9310-157">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="f9310-158">F# 類型</span><span class="sxs-lookup"><span data-stu-id="f9310-158">F# Types</span></span>](fsharp-types.md)
