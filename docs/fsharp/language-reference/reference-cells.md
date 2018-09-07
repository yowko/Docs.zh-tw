---
title: 參照儲存格 (F#)
description: '了解 F # 參考儲存格的儲存體位置，可讓您以參考語意建立可變值的方式。'
ms.date: 05/16/2016
ms.openlocfilehash: e2e1a91c62fd76e4992bc5ae11bb672766850718
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079292"
---
# <a name="reference-cells"></a><span data-ttu-id="e516a-103">參考儲存格</span><span class="sxs-lookup"><span data-stu-id="e516a-103">Reference Cells</span></span>

<span data-ttu-id="e516a-104">*參考儲存格*是可讓您以參考語意建立可變值的儲存體位置。</span><span class="sxs-lookup"><span data-stu-id="e516a-104">*Reference cells* are storage locations that enable you to create mutable values with reference semantics.</span></span>

## <a name="syntax"></a><span data-ttu-id="e516a-105">語法</span><span class="sxs-lookup"><span data-stu-id="e516a-105">Syntax</span></span>

```fsharp
ref expression
```

## <a name="remarks"></a><span data-ttu-id="e516a-106">備註</span><span class="sxs-lookup"><span data-stu-id="e516a-106">Remarks</span></span>

<span data-ttu-id="e516a-107">您可以在值的前面使用 `ref` 運算子，建立可封裝值的新參考儲存格。</span><span class="sxs-lookup"><span data-stu-id="e516a-107">You use the `ref` operator before a value to create a new reference cell that encapsulates the value.</span></span> <span data-ttu-id="e516a-108">由於基礎值是可變的，因此您接著可以變更這個基礎值。</span><span class="sxs-lookup"><span data-stu-id="e516a-108">You can then change the underlying value because it is mutable.</span></span>

<span data-ttu-id="e516a-109">參考儲存格不只是地址，還會保存實際值。</span><span class="sxs-lookup"><span data-stu-id="e516a-109">A reference cell holds an actual value; it is not just an address.</span></span> <span data-ttu-id="e516a-110">當您使用 `ref` 運算子建立參考儲存格時，會建立基礎值的複本做為已封裝的可變值。</span><span class="sxs-lookup"><span data-stu-id="e516a-110">When you create a reference cell by using the `ref` operator, you create a copy of the underlying value as an encapsulated mutable value.</span></span>

<span data-ttu-id="e516a-111">您可以使用 `!` (驚嘆號) 運算子來取值 (Dereference) 參考儲存格。</span><span class="sxs-lookup"><span data-stu-id="e516a-111">You can dereference a reference cell by using the `!` (bang) operator.</span></span>

<span data-ttu-id="e516a-112">下列程式碼範例將示範參考儲存格的宣告和用法。</span><span class="sxs-lookup"><span data-stu-id="e516a-112">The following code example illustrates the declaration and use of reference cells.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

<span data-ttu-id="e516a-113">輸出為 `50`。</span><span class="sxs-lookup"><span data-stu-id="e516a-113">The output is `50`.</span></span>

<span data-ttu-id="e516a-114">參考儲存格為 `Ref` 泛型記錄型別的執行個體，其宣告如下。</span><span class="sxs-lookup"><span data-stu-id="e516a-114">Reference cells are instances of the `Ref` generic record type, which is declared as follows.</span></span>

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

<span data-ttu-id="e516a-115">`'a ref` 型別是 `Ref<'a>` 的同義字。</span><span class="sxs-lookup"><span data-stu-id="e516a-115">The type `'a ref` is a synonym for `Ref<'a>`.</span></span> <span data-ttu-id="e516a-116">IDE 中的編譯器和 IntelliSense 會對此型別顯示前者，但基礎定義則為後者。</span><span class="sxs-lookup"><span data-stu-id="e516a-116">The compiler and IntelliSense in the IDE display the former for this type, but the underlying definition is the latter.</span></span>

<span data-ttu-id="e516a-117">`ref` 運算子會建立新的參考儲存格。</span><span class="sxs-lookup"><span data-stu-id="e516a-117">The `ref` operator creates a new reference cell.</span></span> <span data-ttu-id="e516a-118">下列程式碼為 `ref` 運算子的宣告。</span><span class="sxs-lookup"><span data-stu-id="e516a-118">The following code is the declaration of the `ref` operator.</span></span>

```fsharp
let ref x = { contents = x }
```

<span data-ttu-id="e516a-119">下表顯示參考儲存格上的可用功能。</span><span class="sxs-lookup"><span data-stu-id="e516a-119">The following table shows the features that are available on the reference cell.</span></span>

|<span data-ttu-id="e516a-120">運算子、成員或欄位</span><span class="sxs-lookup"><span data-stu-id="e516a-120">Operator, member, or field</span></span>|<span data-ttu-id="e516a-121">描述</span><span class="sxs-lookup"><span data-stu-id="e516a-121">Description</span></span>|<span data-ttu-id="e516a-122">類型</span><span class="sxs-lookup"><span data-stu-id="e516a-122">Type</span></span>|<span data-ttu-id="e516a-123">定義</span><span class="sxs-lookup"><span data-stu-id="e516a-123">Definition</span></span>|
|--------------------------|-----------|----|----------|
|<span data-ttu-id="e516a-124">`!` (取值運算子)</span><span class="sxs-lookup"><span data-stu-id="e516a-124">`!` (dereference operator)</span></span>|<span data-ttu-id="e516a-125">傳回基礎值。</span><span class="sxs-lookup"><span data-stu-id="e516a-125">Returns the underlying value.</span></span>|`'a ref -> 'a`|`let (!) r = r.contents`|
|<span data-ttu-id="e516a-126">`:=` (指派運算子)</span><span class="sxs-lookup"><span data-stu-id="e516a-126">`:=` (assignment operator)</span></span>|<span data-ttu-id="e516a-127">變更基礎值。</span><span class="sxs-lookup"><span data-stu-id="e516a-127">Changes the underlying value.</span></span>|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|<span data-ttu-id="e516a-128">`ref` (運算子)</span><span class="sxs-lookup"><span data-stu-id="e516a-128">`ref` (operator)</span></span>|<span data-ttu-id="e516a-129">將值封裝至新的參考儲存格。</span><span class="sxs-lookup"><span data-stu-id="e516a-129">Encapsulates a value into a new reference cell.</span></span>|`'a -> 'a ref`|`let ref x = { contents = x }`|
|<span data-ttu-id="e516a-130">`Value` (屬性)</span><span class="sxs-lookup"><span data-stu-id="e516a-130">`Value` (property)</span></span>|<span data-ttu-id="e516a-131">取得或設定基礎值。</span><span class="sxs-lookup"><span data-stu-id="e516a-131">Gets or sets the underlying value.</span></span>|`unit -> 'a`|`member x.Value = x.contents`|
|<span data-ttu-id="e516a-132">`contents` (記錄欄位)</span><span class="sxs-lookup"><span data-stu-id="e516a-132">`contents` (record field)</span></span>|<span data-ttu-id="e516a-133">取得或設定基礎值。</span><span class="sxs-lookup"><span data-stu-id="e516a-133">Gets or sets the underlying value.</span></span>|`'a`|`let ref x = { contents = x }`|
<span data-ttu-id="e516a-134">有數個方式可以存取基礎值。</span><span class="sxs-lookup"><span data-stu-id="e516a-134">There are several ways to access the underlying value.</span></span> <span data-ttu-id="e516a-135">取值運算子 (`!`) 傳回的值不是可指派的值。</span><span class="sxs-lookup"><span data-stu-id="e516a-135">The value returned by the dereference operator (`!`) is not an assignable value.</span></span> <span data-ttu-id="e516a-136">因此如果您要修改基礎值，則必須改用指派運算子 (`:=`)。</span><span class="sxs-lookup"><span data-stu-id="e516a-136">Therefore, if you are modifying the underlying value, you must use the assignment operator (`:=`) instead.</span></span>

<span data-ttu-id="e516a-137">`Value` 屬性和 `contents` 欄位都是可指派的值。</span><span class="sxs-lookup"><span data-stu-id="e516a-137">Both the `Value` property and the `contents` field are assignable values.</span></span> <span data-ttu-id="e516a-138">因此，您可以使用它們來存取或變更基礎值，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="e516a-138">Therefore, you can use these to either access or change the underlying value, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

<span data-ttu-id="e516a-139">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="e516a-139">The output is as follows.</span></span>

```
10
10
11
12
```

<span data-ttu-id="e516a-140">`contents` 欄位是針對與其他 ML 版本相容而提供，而且會在編譯期間產生警告。</span><span class="sxs-lookup"><span data-stu-id="e516a-140">The field `contents` is provided for compatibility with other versions of ML and will produce a warning during compilation.</span></span> <span data-ttu-id="e516a-141">若要停用這個警告，請使用 `--mlcompatibility` 編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="e516a-141">To disable the warning, use the `--mlcompatibility` compiler option.</span></span> <span data-ttu-id="e516a-142">如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。</span><span class="sxs-lookup"><span data-stu-id="e516a-142">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="e516a-143">C# 程式設計人員應該要知道`ref`C# 中不是一樣`ref`F # 中。</span><span class="sxs-lookup"><span data-stu-id="e516a-143">C# programmers should know that `ref` in C# is not the same thing as `ref` in F#.</span></span> <span data-ttu-id="e516a-144">F # 中對等的建構[byref](byrefs.md)，這是不同的概念，從參考儲存格。</span><span class="sxs-lookup"><span data-stu-id="e516a-144">The equivalent constructs in F# are [byrefs](byrefs.md), which are a different concept from reference cells.</span></span>

<span data-ttu-id="e516a-145">值將會標示`mutable`可能會自動升級為`'a ref`如果擷取的 closure; 請參閱[值](values/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e516a-145">Values marked as `mutable`may be automatically promoted to `'a ref` if captured by a closure; see [Values](values/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e516a-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e516a-146">See also</span></span>

- [<span data-ttu-id="e516a-147">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="e516a-147">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="e516a-148">參數和引數</span><span class="sxs-lookup"><span data-stu-id="e516a-148">Parameters and Arguments</span></span>](parameters-and-arguments.md)
- [<span data-ttu-id="e516a-149">符號和運算子參考</span><span class="sxs-lookup"><span data-stu-id="e516a-149">Symbol and Operator Reference</span></span>](symbol-and-operator-reference/index.md)
- [<span data-ttu-id="e516a-150">值</span><span class="sxs-lookup"><span data-stu-id="e516a-150">Values</span></span>](values/index.md)
