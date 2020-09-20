---
title: Tuple
description: '深入瞭解 F # 元組，這是一個未命名但排序值的群組，可能是不同的類型。'
ms.date: 05/16/2016
ms.openlocfilehash: 6f4adf7e10e22d8b7a8cf697baee15962adf3630
ms.sourcegitcommit: fe8877e564deb68d77fa4b79f55584ac8d7e8997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90720357"
---
# <a name="tuples"></a><span data-ttu-id="b0cc1-103">Tuple</span><span class="sxs-lookup"><span data-stu-id="b0cc1-103">Tuples</span></span>

<span data-ttu-id="b0cc1-104">*元組*是未命名但排序值的群組，可能是不同的類型。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-104">A *tuple* is a grouping of unnamed but ordered values, possibly of different types.</span></span>  <span data-ttu-id="b0cc1-105">元組可以是參考型別或結構。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-105">Tuples can either be reference types or structs.</span></span>

## <a name="syntax"></a><span data-ttu-id="b0cc1-106">語法</span><span class="sxs-lookup"><span data-stu-id="b0cc1-106">Syntax</span></span>

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a><span data-ttu-id="b0cc1-107">備註</span><span class="sxs-lookup"><span data-stu-id="b0cc1-107">Remarks</span></span>

<span data-ttu-id="b0cc1-108">上述語法中的每個 *元素* 都可以是任何有效的 F # 運算式。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-108">Each *element* in the previous syntax can be any valid F# expression.</span></span>

## <a name="examples"></a><span data-ttu-id="b0cc1-109">範例</span><span class="sxs-lookup"><span data-stu-id="b0cc1-109">Examples</span></span>

<span data-ttu-id="b0cc1-110">元組的範例包括相同或不同類型的配對、三合一等等。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-110">Examples of tuples include pairs, triples, and so on, of the same or different types.</span></span> <span data-ttu-id="b0cc1-111">下列程式碼說明一些範例。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-111">Some examples are illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a><span data-ttu-id="b0cc1-112">取得個別值</span><span class="sxs-lookup"><span data-stu-id="b0cc1-112">Obtaining Individual Values</span></span>

<span data-ttu-id="b0cc1-113">您可以使用模式比對來存取和指派元組元素的名稱，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-113">You can use pattern matching to access and assign names for tuple elements, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

<span data-ttu-id="b0cc1-114">您也可以透過系結，透過運算式外部的模式比對來解構元組 `match`  `let` ：</span><span class="sxs-lookup"><span data-stu-id="b0cc1-114">You can also deconstruct a tuple via pattern matching outside of a `match` expression via  `let` binding:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

<span data-ttu-id="b0cc1-115">或者，您可以對元組進行模式比對，作為函式的輸入：</span><span class="sxs-lookup"><span data-stu-id="b0cc1-115">Or you can pattern match on tuples as inputs to functions:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

<span data-ttu-id="b0cc1-116">如果您只需要一個元組的元素，則可以使用 (底線) 的萬用字元，以避免為不需要的值建立新的名稱。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-116">If you need only one element of the tuple, the wildcard character (the underscore) can be used to avoid creating a new name for a value that you do not need.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

<span data-ttu-id="b0cc1-117">從參考元組將元素複製到結構元組也很簡單：</span><span class="sxs-lookup"><span data-stu-id="b0cc1-117">Copying elements from a reference tuple into a struct tuple is also simple:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

<span data-ttu-id="b0cc1-118">`fst` `snd` 只有) 傳回元組的第一個和第二個元素時，才會有函數和 (參考元組。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-118">The functions `fst` and `snd` (reference tuples only) return the first and second elements of a tuple, respectively.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

<span data-ttu-id="b0cc1-119">沒有可傳回三個三個元素的內建函數，但您可以輕鬆地撰寫一個，如下所示。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-119">There is no built-in function that returns the third element of a triple, but you can easily write one as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

<span data-ttu-id="b0cc1-120">一般而言，最好使用模式比對來存取個別的元組元素。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-120">Generally, it is better to use pattern matching to access individual tuple elements.</span></span>

## <a name="using-tuples"></a><span data-ttu-id="b0cc1-121">使用元組</span><span class="sxs-lookup"><span data-stu-id="b0cc1-121">Using Tuples</span></span>

<span data-ttu-id="b0cc1-122">元組提供一個便利的方式，從函式傳回多個值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-122">Tuples provide a convenient way to return multiple values from a function, as shown in the following example.</span></span> <span data-ttu-id="b0cc1-123">此範例會執行整數除法運算，並將作業的舍入結果傳回為元組配對的第一個成員，並傳回餘數做為配對的第二個成員。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-123">This example performs integer division and returns the rounded result of the operation as a first member of a tuple pair and the remainder as a second member of the pair.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

<span data-ttu-id="b0cc1-124">當您想要避免一般函數語法所隱含的函式引數隱含 currying 時，元組也可以當做函式引數使用。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-124">Tuples can also be used as function arguments when you want to avoid the implicit currying of function arguments that is implied by the usual function syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

<span data-ttu-id="b0cc1-125">定義函式的一般語法可 `let sum a b = a + b` 讓您定義函式，該函式是函式之第一個引數的部分應用，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-125">The usual syntax for defining the function `let sum a b = a + b` enables you to define a function that is the partial application of the first argument of the function, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

<span data-ttu-id="b0cc1-126">使用元組作為參數會停用 currying。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-126">Using a tuple as the parameter disables currying.</span></span> <span data-ttu-id="b0cc1-127">如需詳細資訊，請參閱函 [式中的](./functions/index.md)「部分引數應用程式」。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-127">For more information, see "Partial Application of Arguments" in [Functions](./functions/index.md).</span></span>

## <a name="names-of-tuple-types"></a><span data-ttu-id="b0cc1-128">元組類型的名稱</span><span class="sxs-lookup"><span data-stu-id="b0cc1-128">Names of Tuple Types</span></span>

<span data-ttu-id="b0cc1-129">當您寫出屬於元組的型別名稱時，會使用 `*` 符號來分隔專案。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-129">When you write out the name of a type that is a tuple, you use the `*` symbol to separate elements.</span></span> <span data-ttu-id="b0cc1-130">若為包含 `int` 、和的元組（ `float` `string` 例如 `(10, 10.0, "ten")` ），則會以下列方式寫入類型。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-130">For a tuple that consists of an `int`, a `float`, and a `string`, such as `(10, 10.0, "ten")`, the type would be written as follows.</span></span>

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a><span data-ttu-id="b0cc1-131">與 c # 元組交互操作</span><span class="sxs-lookup"><span data-stu-id="b0cc1-131">Interoperation with C# Tuples</span></span>

<span data-ttu-id="b0cc1-132">C # 7.0 引進了元組至語言。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-132">C# 7.0 introduced tuples to the language.</span></span>  <span data-ttu-id="b0cc1-133">C # 中的元組是結構，相當於 F # 中的結構元組。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-133">Tuples in C# are structs, and are equivalent to struct tuples in F#.</span></span>  <span data-ttu-id="b0cc1-134">如果您需要與 c # 交互操作，您必須使用結構元組。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-134">If you need to interoperate with C#, you must use struct tuples.</span></span>

<span data-ttu-id="b0cc1-135">這麼做很簡單。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-135">This is easy to do.</span></span>  <span data-ttu-id="b0cc1-136">例如，假設您必須將元組傳遞給 c # 類別，然後使用它的結果，也就是元組：</span><span class="sxs-lookup"><span data-stu-id="b0cc1-136">For example, imagine you have to pass a tuple to a C# class and then consume its result, which is also a tuple:</span></span>

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

<span data-ttu-id="b0cc1-137">在您的 F # 程式碼中，您可以傳遞結構元組作為參數，並將結果作為結構元組使用。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-137">In your F# code, you can then pass a struct tuple as the parameter and consume the result as a struct tuple.</span></span>

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a><span data-ttu-id="b0cc1-138">在參考元組和結構元組之間轉換</span><span class="sxs-lookup"><span data-stu-id="b0cc1-138">Converting between Reference Tuples and Struct Tuples</span></span>

<span data-ttu-id="b0cc1-139">由於參考元組和結構元組具有完全不同的基礎標記法，因此它們無法隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-139">Because Reference Tuples and Struct Tuples have a completely different underlying representation, they are not implicitly convertible.</span></span>  <span data-ttu-id="b0cc1-140">也就是說，如下所示的程式碼將不會編譯：</span><span class="sxs-lookup"><span data-stu-id="b0cc1-140">That is, code such as the following won't compile:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

<span data-ttu-id="b0cc1-141">您必須在一個元組上進行模式比對，並使用組成零件來建立另一個。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-141">You must pattern match on one tuple and construct the other with the constituent parts.</span></span>  <span data-ttu-id="b0cc1-142">例如：</span><span class="sxs-lookup"><span data-stu-id="b0cc1-142">For example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a><span data-ttu-id="b0cc1-143">參考元組的編譯形式</span><span class="sxs-lookup"><span data-stu-id="b0cc1-143">Compiled Form of Reference Tuples</span></span>

<span data-ttu-id="b0cc1-144">本節說明編譯元組的形式。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-144">This section explains the form of tuples when they're compiled.</span></span>  <span data-ttu-id="b0cc1-145">除非您的目標是 .NET Framework 3.5 或更低版本，否則不需要讀取此處的資訊。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-145">The information here isn't necessary to read unless you are targeting .NET Framework 3.5 or lower.</span></span>

<span data-ttu-id="b0cc1-146">元組會編譯成數個泛型型別之一的物件，這些泛型型別全都命名為 arity 上的多載， `System.Tuple` 或類型參數的數目。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-146">Tuples are compiled into objects of one of several generic types, all named `System.Tuple`, that are overloaded on the arity, or number of type parameters.</span></span> <span data-ttu-id="b0cc1-147">當您從另一種語言（例如 c # 或 Visual Basic，或使用不知道 F # 結構的工具）來查看元組類型時，元組類型會以此形式出現。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-147">Tuple types appear in this form when you view them from another language, such as C# or Visual Basic, or when you are using a tool that is not aware of F# constructs.</span></span> <span data-ttu-id="b0cc1-148">這些 `Tuple` 類型是在 .NET Framework 4 中引進。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-148">The `Tuple` types were introduced in .NET Framework 4.</span></span> <span data-ttu-id="b0cc1-149">如果您的目標是舊版 .NET Framework，編譯器會使用 `System.Tuple` 來自2.0 版 F # 核心程式庫的版本。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-149">If you are targeting an earlier version of .NET Framework, the compiler uses versions of `System.Tuple` from the 2.0 version of the F# Core Library.</span></span> <span data-ttu-id="b0cc1-150">此程式庫中的類型僅適用于以 .NET Framework 2.0、3.0 和3.5 版本為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-150">The types in this library are used only for applications that target the 2.0, 3.0, and 3.5 versions of .NET Framework.</span></span> <span data-ttu-id="b0cc1-151">類型轉送是用來確保 .NET Framework 2.0 和 .NET Framework 4 F # 元件之間的二進位相容性。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-151">Type forwarding is used to ensure binary compatibility between .NET Framework 2.0 and .NET Framework 4 F# components.</span></span>

### <a name="compiled-form-of-struct-tuples"></a><span data-ttu-id="b0cc1-152">結構元組的編譯形式</span><span class="sxs-lookup"><span data-stu-id="b0cc1-152">Compiled Form of Struct Tuples</span></span>

<span data-ttu-id="b0cc1-153">結構元組 (例如 `struct (x, y)`) ，基本上與參考元組不同。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-153">Struct tuples (for example, `struct (x, y)`), are fundamentally different from reference tuples.</span></span>  <span data-ttu-id="b0cc1-154">它們會編譯成 <xref:System.ValueTuple> 類型、以 arity 來多載，或是類型參數的數目。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-154">They are compiled into the <xref:System.ValueTuple> type, overloaded by arity, or the number of type parameters.</span></span>  <span data-ttu-id="b0cc1-155">它們相當於 [c # 7.0 元組](../../csharp/language-reference/builtin-types/value-tuples.md) 和 [Visual Basic 2017 元組](../../visual-basic/programming-guide/language-features/data-types/tuples.md)，而且可交互操作雙向。</span><span class="sxs-lookup"><span data-stu-id="b0cc1-155">They are equivalent to [C# 7.0 Tuples](../../csharp/language-reference/builtin-types/value-tuples.md) and [Visual Basic 2017 Tuples](../../visual-basic/programming-guide/language-features/data-types/tuples.md), and interoperate bidirectionally.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0cc1-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0cc1-156">See also</span></span>

- [<span data-ttu-id="b0cc1-157">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="b0cc1-157">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="b0cc1-158">F# 類型</span><span class="sxs-lookup"><span data-stu-id="b0cc1-158">F# Types</span></span>](fsharp-types.md)
