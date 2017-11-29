---
title: "參照儲存格 (F#)"
description: "了解 F # 參考儲存格的儲存位置可讓您參考語意建立可變值的方式。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 09a0b221-ea21-45c4-bae8-5e4a339750c4
ms.openlocfilehash: c7470c9a36cf2cd24dd89ceffcf6e90c6dc4d2dd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="reference-cells"></a><span data-ttu-id="a70e6-104">參考儲存格</span><span class="sxs-lookup"><span data-stu-id="a70e6-104">Reference Cells</span></span>

<span data-ttu-id="a70e6-105">*參考儲存格*是可讓您參考語意建立可變值的儲存位置。</span><span class="sxs-lookup"><span data-stu-id="a70e6-105">*Reference cells* are storage locations that enable you to create mutable values with reference semantics.</span></span>

## <a name="syntax"></a><span data-ttu-id="a70e6-106">語法</span><span class="sxs-lookup"><span data-stu-id="a70e6-106">Syntax</span></span>

```fsharp
ref expression
```

## <a name="remarks"></a><span data-ttu-id="a70e6-107">備註</span><span class="sxs-lookup"><span data-stu-id="a70e6-107">Remarks</span></span>
<span data-ttu-id="a70e6-108">您可以在值的前面使用 `ref` 運算子，建立可封裝值的新參考儲存格。</span><span class="sxs-lookup"><span data-stu-id="a70e6-108">You use the `ref` operator before a value to create a new reference cell that encapsulates the value.</span></span> <span data-ttu-id="a70e6-109">由於基礎值是可變的，因此您接著可以變更這個基礎值。</span><span class="sxs-lookup"><span data-stu-id="a70e6-109">You can then change the underlying value because it is mutable.</span></span>

<span data-ttu-id="a70e6-110">參考儲存格不只是地址，還會保存實際值。</span><span class="sxs-lookup"><span data-stu-id="a70e6-110">A reference cell holds an actual value; it is not just an address.</span></span> <span data-ttu-id="a70e6-111">當您使用 `ref` 運算子建立參考儲存格時，會建立基礎值的複本做為已封裝的可變值。</span><span class="sxs-lookup"><span data-stu-id="a70e6-111">When you create a reference cell by using the `ref` operator, you create a copy of the underlying value as an encapsulated mutable value.</span></span>

<span data-ttu-id="a70e6-112">您可以使用 `!` (驚嘆號) 運算子來取值 (Dereference) 參考儲存格。</span><span class="sxs-lookup"><span data-stu-id="a70e6-112">You can dereference a reference cell by using the `!` (bang) operator.</span></span>

<span data-ttu-id="a70e6-113">下列程式碼範例將示範參考儲存格的宣告和用法。</span><span class="sxs-lookup"><span data-stu-id="a70e6-113">The following code example illustrates the declaration and use of reference cells.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

<span data-ttu-id="a70e6-114">輸出為 `50`。</span><span class="sxs-lookup"><span data-stu-id="a70e6-114">The output is `50`.</span></span>

<span data-ttu-id="a70e6-115">參考儲存格為 `Ref` 泛型記錄型別的執行個體，其宣告如下。</span><span class="sxs-lookup"><span data-stu-id="a70e6-115">Reference cells are instances of the `Ref` generic record type, which is declared as follows.</span></span>

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

<span data-ttu-id="a70e6-116">`'a ref` 型別是 `Ref<'a>` 的同義字。</span><span class="sxs-lookup"><span data-stu-id="a70e6-116">The type `'a ref` is a synonym for `Ref<'a>`.</span></span> <span data-ttu-id="a70e6-117">IDE 中的編譯器和 IntelliSense 會對此型別顯示前者，但基礎定義則為後者。</span><span class="sxs-lookup"><span data-stu-id="a70e6-117">The compiler and IntelliSense in the IDE display the former for this type, but the underlying definition is the latter.</span></span>

<span data-ttu-id="a70e6-118">`ref` 運算子會建立新的參考儲存格。</span><span class="sxs-lookup"><span data-stu-id="a70e6-118">The `ref` operator creates a new reference cell.</span></span> <span data-ttu-id="a70e6-119">下列程式碼為 `ref` 運算子的宣告。</span><span class="sxs-lookup"><span data-stu-id="a70e6-119">The following code is the declaration of the `ref` operator.</span></span>

```fsharp
let ref x = { contents = x }
```

<span data-ttu-id="a70e6-120">下表顯示參考儲存格上的可用功能。</span><span class="sxs-lookup"><span data-stu-id="a70e6-120">The following table shows the features that are available on the reference cell.</span></span>

|<span data-ttu-id="a70e6-121">運算子、成員或欄位</span><span class="sxs-lookup"><span data-stu-id="a70e6-121">Operator, member, or field</span></span>|<span data-ttu-id="a70e6-122">描述</span><span class="sxs-lookup"><span data-stu-id="a70e6-122">Description</span></span>|<span data-ttu-id="a70e6-123">類型</span><span class="sxs-lookup"><span data-stu-id="a70e6-123">Type</span></span>|<span data-ttu-id="a70e6-124">定義</span><span class="sxs-lookup"><span data-stu-id="a70e6-124">Definition</span></span>|
|--------------------------|-----------|----|----------|
|<span data-ttu-id="a70e6-125">`!` (取值運算子)</span><span class="sxs-lookup"><span data-stu-id="a70e6-125">`!` (dereference operator)</span></span>|<span data-ttu-id="a70e6-126">傳回基礎值。</span><span class="sxs-lookup"><span data-stu-id="a70e6-126">Returns the underlying value.</span></span>|`'a ref -> 'a`|`let (!) r = r.contents`|
|<span data-ttu-id="a70e6-127">`:=` (指派運算子)</span><span class="sxs-lookup"><span data-stu-id="a70e6-127">`:=` (assignment operator)</span></span>|<span data-ttu-id="a70e6-128">變更基礎值。</span><span class="sxs-lookup"><span data-stu-id="a70e6-128">Changes the underlying value.</span></span>|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|<span data-ttu-id="a70e6-129">`ref` (運算子)</span><span class="sxs-lookup"><span data-stu-id="a70e6-129">`ref` (operator)</span></span>|<span data-ttu-id="a70e6-130">將值封裝至新的參考儲存格。</span><span class="sxs-lookup"><span data-stu-id="a70e6-130">Encapsulates a value into a new reference cell.</span></span>|`'a -> 'a ref`|`let ref x = { contents = x }`|
|<span data-ttu-id="a70e6-131">`Value` (屬性)</span><span class="sxs-lookup"><span data-stu-id="a70e6-131">`Value` (property)</span></span>|<span data-ttu-id="a70e6-132">取得或設定基礎值。</span><span class="sxs-lookup"><span data-stu-id="a70e6-132">Gets or sets the underlying value.</span></span>|`unit -> 'a`|`member x.Value = x.contents`|
|<span data-ttu-id="a70e6-133">`contents` (記錄欄位)</span><span class="sxs-lookup"><span data-stu-id="a70e6-133">`contents` (record field)</span></span>|<span data-ttu-id="a70e6-134">取得或設定基礎值。</span><span class="sxs-lookup"><span data-stu-id="a70e6-134">Gets or sets the underlying value.</span></span>|`'a`|`let ref x = { contents = x }`|
<span data-ttu-id="a70e6-135">有數個方式可以存取基礎值。</span><span class="sxs-lookup"><span data-stu-id="a70e6-135">There are several ways to access the underlying value.</span></span> <span data-ttu-id="a70e6-136">取值運算子 (`!`) 傳回的值不是可指派的值。</span><span class="sxs-lookup"><span data-stu-id="a70e6-136">The value returned by the dereference operator (`!`) is not an assignable value.</span></span> <span data-ttu-id="a70e6-137">因此如果您要修改基礎值，則必須改用指派運算子 (`:=`)。</span><span class="sxs-lookup"><span data-stu-id="a70e6-137">Therefore, if you are modifying the underlying value, you must use the assignment operator (`:=`) instead.</span></span>

<span data-ttu-id="a70e6-138">`Value` 屬性和 `contents` 欄位都是可指派的值。</span><span class="sxs-lookup"><span data-stu-id="a70e6-138">Both the `Value` property and the `contents` field are assignable values.</span></span> <span data-ttu-id="a70e6-139">因此，您可以使用它們來存取或變更基礎值，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="a70e6-139">Therefore, you can use these to either access or change the underlying value, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

<span data-ttu-id="a70e6-140">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="a70e6-140">The output is as follows.</span></span>

```
10
10
11
12
```

<span data-ttu-id="a70e6-141">`contents` 欄位是針對與其他 ML 版本相容而提供，而且會在編譯期間產生警告。</span><span class="sxs-lookup"><span data-stu-id="a70e6-141">The field `contents` is provided for compatibility with other versions of ML and will produce a warning during compilation.</span></span> <span data-ttu-id="a70e6-142">若要停用這個警告，請使用 `--mlcompatibility` 編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="a70e6-142">To disable the warning, use the `--mlcompatibility` compiler option.</span></span> <span data-ttu-id="a70e6-143">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="a70e6-143">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="a70e6-144">下列程式碼將示範如何將參考儲存格用於參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="a70e6-144">The following code illustrates the use of reference cells in parameter passing.</span></span> <span data-ttu-id="a70e6-145">增量器類型具有方法採用參數，其中包含 byref 參數類型中的遞增值。</span><span class="sxs-lookup"><span data-stu-id="a70e6-145">The Incrementor type has a method Increment that takes a parameter that includes byref in the parameter type.</span></span> <span data-ttu-id="a70e6-146">Byref 參數類型中的表示呼叫端，必須傳遞參考儲存格或指定型別的一般變數位址，在此案例的 int。其餘的程式碼示範如何呼叫這兩種類型的引數，與遞增值，並建立參考儲存格 (ref myDelta1) 的變數上將示範如何使用 ref 運算子。</span><span class="sxs-lookup"><span data-stu-id="a70e6-146">The byref in the parameter type indicates that callers must pass a reference cell or the address of a typical variable of the specified type, in this case int. The remaining code illustrates how to call Increment with both of these types of arguments, and shows the use of the ref operator on a variable to create a reference cell (ref myDelta1).</span></span> <span data-ttu-id="a70e6-147">接著，程式碼會示範如何使用傳址運算子 (&amp;) 來產生適當引數。</span><span class="sxs-lookup"><span data-stu-id="a70e6-147">It then shows the use of the address-of operator (&amp;) to generate an appropriate argument.</span></span> <span data-ttu-id="a70e6-148">最後，使用宣告可透過 let 繫結的參考儲存格時再次呼叫 Increment 方法。</span><span class="sxs-lookup"><span data-stu-id="a70e6-148">Finally, the Increment method is called again by using a reference cell that is declared by using a let binding.</span></span> <span data-ttu-id="a70e6-149">最後一行程式碼會示範如何使用 ！</span><span class="sxs-lookup"><span data-stu-id="a70e6-149">The final line of code demonstrates the use of the !</span></span> <span data-ttu-id="a70e6-150">運算子來取值參考儲存格供列印。</span><span class="sxs-lookup"><span data-stu-id="a70e6-150">operator to dereference the reference cell for printing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2204.fs)]

<span data-ttu-id="a70e6-151">如需如何以傳址方式傳遞的詳細資訊，請參閱[參數和引數](parameters-and-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="a70e6-151">For more information about how to pass by reference, see [Parameters and Arguments](parameters-and-arguments.md).</span></span>

>[!NOTE]
<span data-ttu-id="a70e6-152">C# 程式設計人員應該知道運作方式，該 ref F # 中不同於 C#。</span><span class="sxs-lookup"><span data-stu-id="a70e6-152">C# programmers should know that ref works differently in F# than it does in C#.</span></span> <span data-ttu-id="a70e6-153">比方說，使用 ref 時傳遞引數並沒有相同的效果在 F # 與 C# 中。</span><span class="sxs-lookup"><span data-stu-id="a70e6-153">For example, the use of ref when you pass an argument does not have the same effect in F# as it does in C#.</span></span>

## <a name="consuming-c-ref-returns"></a><span data-ttu-id="a70e6-154">使用 C#`ref`傳回</span><span class="sxs-lookup"><span data-stu-id="a70e6-154">Consuming C# `ref` returns</span></span>

<span data-ttu-id="a70e6-155">從 F # 4.1 開始，您可以使用`ref`傳回 C# 中產生。</span><span class="sxs-lookup"><span data-stu-id="a70e6-155">Starting with F# 4.1, you can consume `ref` returns generated in C#.</span></span>  <span data-ttu-id="a70e6-156">這類呼叫的結果是`byref<_>`指標。</span><span class="sxs-lookup"><span data-stu-id="a70e6-156">The result of such a call is a `byref<_>` pointer.</span></span>

<span data-ttu-id="a70e6-157">下列 C# 方法：</span><span class="sxs-lookup"><span data-stu-id="a70e6-157">The following C# method:</span></span>

```csharp
namespace RefReturns
{
    public static class RefClass
    {
        public static ref int Find(int val, int[] vals)
        {
            for (int i = 0; i < vals.Length; i++)
            {
                if (vals[i] == val)
                {
                    return ref numbers[i]; // Returns the location, not the value
                }
            }

            throw new IndexOutOfRangeException($"{nameof(number)} not found");
        }
    }
}
```

<span data-ttu-id="a70e6-158">可以被明確地呼叫 F # 與沒有特殊的語法：</span><span class="sxs-lookup"><span data-stu-id="a70e6-158">Can be transparently called by F# with no special syntax:</span></span>

```fsharp
open RefReturns

let consumeRefReturn() =
    let result = RefClass.Find(3, [| 1; 2; 3; 4; 5 |]) // 'result' is of type 'byref<int>'.
    ()
```

<span data-ttu-id="a70e6-159">您也可以宣告的函式也可能需要`ref`傳回做為輸入，例如：</span><span class="sxs-lookup"><span data-stu-id="a70e6-159">You can also declare functions which could take a `ref` return as input, for example:</span></span>

```fsharp
let f (x: byref<int>) = &x
```

<span data-ttu-id="a70e6-160">目前沒有任何方法來產生`ref`在 F # 中無法使用 C# 中傳回。</span><span class="sxs-lookup"><span data-stu-id="a70e6-160">There is currently no way to generate a `ref` return in F# which could be consumed in C#.</span></span>

## <a name="see-also"></a><span data-ttu-id="a70e6-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a70e6-161">See Also</span></span>
[<span data-ttu-id="a70e6-162">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="a70e6-162">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="a70e6-163">參數和引數</span><span class="sxs-lookup"><span data-stu-id="a70e6-163">Parameters and Arguments</span></span>](parameters-and-arguments.md)

[<span data-ttu-id="a70e6-164">符號和運算子參考</span><span class="sxs-lookup"><span data-stu-id="a70e6-164">Symbol and Operator Reference</span></span>](symbol-and-operator-reference/index.md)
