---
title: 結構
description: 瞭解F#結構, 精簡的物件類型通常比具有少量資料和簡單行為之類型的類別更有效率。
ms.date: 05/16/2016
ms.openlocfilehash: 1e9652cc4776e4d1d52eb20e41b6dd87a6c5ba05
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106818"
---
# <a name="structures"></a><span data-ttu-id="77a8a-103">結構</span><span class="sxs-lookup"><span data-stu-id="77a8a-103">Structures</span></span>

<span data-ttu-id="77a8a-104">*結構*是精簡的物件類型, 相較于具有少量資料和簡單行為之類型的類別, 其效率會更有效率。</span><span class="sxs-lookup"><span data-stu-id="77a8a-104">A *structure* is a compact object type that can be more efficient than a class for types that have a small amount of data and simple behavior.</span></span>

## <a name="syntax"></a><span data-ttu-id="77a8a-105">語法</span><span class="sxs-lookup"><span data-stu-id="77a8a-105">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    struct
        type-definition-elements-and-members
    end
// or
[ attributes ]
[<StructAttribute>]
type [accessibility-modifier] type-name =
    type-definition-elements-and-members
```

## <a name="remarks"></a><span data-ttu-id="77a8a-106">備註</span><span class="sxs-lookup"><span data-stu-id="77a8a-106">Remarks</span></span>

<span data-ttu-id="77a8a-107">結構是實*值*型別, 這表示它們是直接儲存在堆疊上, 或是當做欄位或陣列元素使用 (在父類型中內嵌)。</span><span class="sxs-lookup"><span data-stu-id="77a8a-107">Structures are *value types*, which means that they are stored directly on the stack or, when they are used as fields or array elements, inline in the parent type.</span></span> <span data-ttu-id="77a8a-108">有別於類別與記錄，結構具有以值傳遞的語意。</span><span class="sxs-lookup"><span data-stu-id="77a8a-108">Unlike classes and records, structures have pass-by-value semantics.</span></span> <span data-ttu-id="77a8a-109">這表示它們主要對於經常存取及複製的小型資料彙總相當實用。</span><span class="sxs-lookup"><span data-stu-id="77a8a-109">This means that they are useful primarily for small aggregates of data that are accessed and copied frequently.</span></span>

<span data-ttu-id="77a8a-110">在先前的語法中，顯示了兩個表單。</span><span class="sxs-lookup"><span data-stu-id="77a8a-110">In the previous syntax, two forms are shown.</span></span> <span data-ttu-id="77a8a-111">第一個表單的語法略為複雜，但使用卻很頻繁，因為當您使用 `struct` 和 `end` 關鍵字時，可以省略出現在第二個表單中的 `StructAttribute` 屬性。</span><span class="sxs-lookup"><span data-stu-id="77a8a-111">The first is not the lightweight syntax, but it is nevertheless frequently used because, when you use the `struct` and `end` keywords, you can omit the `StructAttribute` attribute, which appears in the second form.</span></span> <span data-ttu-id="77a8a-112">您可以將 `StructAttribute` 縮寫為只有 `Struct`。</span><span class="sxs-lookup"><span data-stu-id="77a8a-112">You can abbreviate `StructAttribute` to just `Struct`.</span></span>

<span data-ttu-id="77a8a-113">上一個語法中的*類型定義-elements 和成員*代表成員宣告和定義。</span><span class="sxs-lookup"><span data-stu-id="77a8a-113">The *type-definition-elements-and-members* in the previous syntax represents member declarations and definitions.</span></span> <span data-ttu-id="77a8a-114">結構可以具有建構函式及可變動和不可變的欄位，同時它們可以宣告成員及介面實作。</span><span class="sxs-lookup"><span data-stu-id="77a8a-114">Structures can have constructors and mutable and immutable fields, and they can declare members and interface implementations.</span></span> <span data-ttu-id="77a8a-115">如需詳細資訊, 請參閱[成員](./members/index.md)。</span><span class="sxs-lookup"><span data-stu-id="77a8a-115">For more information, see [Members](./members/index.md).</span></span>

<span data-ttu-id="77a8a-116">結構無法參與繼承、不能包含 `let` 或 `do` 繫結，且不得以遞迴方式包含其本身類型的欄位 (不過它們可以包含參考其本身類型的參考儲存格)。</span><span class="sxs-lookup"><span data-stu-id="77a8a-116">Structures cannot participate in inheritance, cannot contain `let` or `do` bindings, and cannot recursively contain fields of their own type (although they can contain reference cells that reference their own type).</span></span>

<span data-ttu-id="77a8a-117">因為結構不允許 `let` 繫結，因此您必須使用 `val` 關鍵字來宣告結構中的欄位。</span><span class="sxs-lookup"><span data-stu-id="77a8a-117">Because structures do not allow `let` bindings, you must declare fields in structures by using the `val` keyword.</span></span> <span data-ttu-id="77a8a-118">`val` 關鍵字會定義欄位及其類型，但不允許進行初始化。</span><span class="sxs-lookup"><span data-stu-id="77a8a-118">The `val` keyword defines a field and its type but does not allow initialization.</span></span> <span data-ttu-id="77a8a-119">相反地，`val` 宣告會初始化為零或 null。</span><span class="sxs-lookup"><span data-stu-id="77a8a-119">Instead, `val` declarations are initialized to zero or null.</span></span> <span data-ttu-id="77a8a-120">基於這個理由，具有隱含建構函式 (也就是緊接在宣告中結構名稱後的指定參數) 的結構，需要 `val` 宣告標註 `DefaultValue` 屬性。</span><span class="sxs-lookup"><span data-stu-id="77a8a-120">For this reason, structures that have an implicit constructor (that is, parameters that are given immediately after the structure name in the declaration) require that `val` declarations be annotated with the `DefaultValue` attribute.</span></span> <span data-ttu-id="77a8a-121">具有已定義的建構函式之結構，仍然支援零初始化。</span><span class="sxs-lookup"><span data-stu-id="77a8a-121">Structures that have a defined constructor still support zero-initialization.</span></span> <span data-ttu-id="77a8a-122">因此，`DefaultValue` 屬性是一種零值對於欄位有效的宣告。</span><span class="sxs-lookup"><span data-stu-id="77a8a-122">Therefore, the `DefaultValue` attribute is a declaration that such a zero value is valid for the field.</span></span> <span data-ttu-id="77a8a-123">結構的隱含建構函式不會執行任何動作，因為類型上不允許 `let` 和 `do` 繫結，但傳入的隱含建構函式參數值均可用作為私用欄位。</span><span class="sxs-lookup"><span data-stu-id="77a8a-123">Implicit constructors for structures do not perform any actions because `let` and `do` bindings aren’t allowed on the type, but the implicit constructor parameter values passed in are available as private fields.</span></span>

<span data-ttu-id="77a8a-124">明確建構函式可能會牽涉到欄位值的初始化。</span><span class="sxs-lookup"><span data-stu-id="77a8a-124">Explicit constructors might involve initialization of field values.</span></span> <span data-ttu-id="77a8a-125">當您的結構有明確的建構函式時，它仍然可以支援零初始化。不過，請勿在 `DefaultValue` 宣告上使用 `val` 屬性，因為它與明確建構函式相衝突。</span><span class="sxs-lookup"><span data-stu-id="77a8a-125">When you have a structure that has an explicit constructor, it still supports zero-initialization; however, you do not use the `DefaultValue` attribute on the `val` declarations because it conflicts with the explicit constructor.</span></span> <span data-ttu-id="77a8a-126">如需宣告的`val`詳細資訊, [請參閱明確欄位:`val`關鍵字。](./members/explicit-fields-the-val-keyword.md)</span><span class="sxs-lookup"><span data-stu-id="77a8a-126">For more information about `val` declarations, see [Explicit Fields: The `val` Keyword](./members/explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="77a8a-127">結構上允許屬性和存取範圍修飾詞，並遵循與其他類型相同的規則。</span><span class="sxs-lookup"><span data-stu-id="77a8a-127">Attributes and accessibility modifiers are allowed on structures, and follow the same rules as those for other types.</span></span> <span data-ttu-id="77a8a-128">如需詳細資訊, 請參閱[屬性](attributes.md)和[存取控制](access-control.md)。</span><span class="sxs-lookup"><span data-stu-id="77a8a-128">For more information, see [Attributes](attributes.md) and [Access Control](access-control.md).</span></span>

<span data-ttu-id="77a8a-129">下列程式碼範例說明結構定義。</span><span class="sxs-lookup"><span data-stu-id="77a8a-129">The following code examples illustrate structure definitions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="byreflike-structs"></a><span data-ttu-id="77a8a-130">ByRefLike 結構</span><span class="sxs-lookup"><span data-stu-id="77a8a-130">ByRefLike structs</span></span>

<span data-ttu-id="77a8a-131">您可以定義自己的結構, 以`byref`遵循類似的語義: 如需詳細資訊, 請參閱[byref](byrefs.md) 。</span><span class="sxs-lookup"><span data-stu-id="77a8a-131">You can define your own structs that can adhere to `byref`-like semantics: see [Byrefs](byrefs.md) for more information.</span></span> <span data-ttu-id="77a8a-132">這會透過<xref:System.Runtime.CompilerServices.IsByRefLikeAttribute>屬性來完成:</span><span class="sxs-lookup"><span data-stu-id="77a8a-132">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="77a8a-133">`IsByRefLike`不表示`Struct`。</span><span class="sxs-lookup"><span data-stu-id="77a8a-133">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="77a8a-134">這兩者都必須存在於類型上。</span><span class="sxs-lookup"><span data-stu-id="77a8a-134">Both must be present on the type.</span></span>

<span data-ttu-id="77a8a-135">`byref`中F#的「類似」結構是堆疊系結的實值型別。</span><span class="sxs-lookup"><span data-stu-id="77a8a-135">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="77a8a-136">它永遠不會在受控堆積上配置。</span><span class="sxs-lookup"><span data-stu-id="77a8a-136">It is never allocated on the managed heap.</span></span> <span data-ttu-id="77a8a-137">類似`byref`的結構適用于高效能程式設計, 因為它會強制執行一組有關存留期和非捕捉的強式檢查。</span><span class="sxs-lookup"><span data-stu-id="77a8a-137">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="77a8a-138">規則包括:</span><span class="sxs-lookup"><span data-stu-id="77a8a-138">The rules are:</span></span>

- <span data-ttu-id="77a8a-139">它們可用來做為函式參數、方法參數、區域變數、方法傳回。</span><span class="sxs-lookup"><span data-stu-id="77a8a-139">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
- <span data-ttu-id="77a8a-140">它們不能是類別或一般結構的靜態或實例成員。</span><span class="sxs-lookup"><span data-stu-id="77a8a-140">They cannot be static or instance members of a class or normal struct.</span></span>
- <span data-ttu-id="77a8a-141">它們不能由任何結束結構 (`async`方法或 lambda 運算式) 來捕捉。</span><span class="sxs-lookup"><span data-stu-id="77a8a-141">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
- <span data-ttu-id="77a8a-142">它們不能用來做為泛型參數。</span><span class="sxs-lookup"><span data-stu-id="77a8a-142">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="77a8a-143">雖然這些規則非常嚴格地限制使用方式, 但它們會以安全的方式滿足高效能運算的承諾。</span><span class="sxs-lookup"><span data-stu-id="77a8a-143">Although these rules very strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="77a8a-144">ReadOnly 結構</span><span class="sxs-lookup"><span data-stu-id="77a8a-144">ReadOnly structs</span></span>

<span data-ttu-id="77a8a-145">您可以使用<xref:System.Runtime.CompilerServices.IsReadOnlyAttribute>屬性來標注結構。</span><span class="sxs-lookup"><span data-stu-id="77a8a-145">You can annotate structs with the <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> attribute.</span></span> <span data-ttu-id="77a8a-146">例如：</span><span class="sxs-lookup"><span data-stu-id="77a8a-146">For example:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="77a8a-147">`IsReadOnly`不表示`Struct`。</span><span class="sxs-lookup"><span data-stu-id="77a8a-147">`IsReadOnly` does not imply `Struct`.</span></span> <span data-ttu-id="77a8a-148">您必須加入這兩個才能`IsReadOnly`具有結構。</span><span class="sxs-lookup"><span data-stu-id="77a8a-148">You must add both to have an `IsReadOnly` struct.</span></span>

<span data-ttu-id="77a8a-149">使用此屬性會發出中繼資料F# , C#並知道要分別將`inref<'T>`它`in ref`視為和。</span><span class="sxs-lookup"><span data-stu-id="77a8a-149">Use of this attribute emits metadata letting F# and C# know to treat it as `inref<'T>` and `in ref`, respectively.</span></span>

<span data-ttu-id="77a8a-150">在 readonly 結構內定義可變值會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="77a8a-150">Defining a mutable value inside of a readonly struct produces an error.</span></span>

## <a name="struct-records-and-discriminated-unions"></a><span data-ttu-id="77a8a-151">結構記錄和區分等位</span><span class="sxs-lookup"><span data-stu-id="77a8a-151">Struct Records and Discriminated Unions</span></span>

<span data-ttu-id="77a8a-152">您可以使用`[<Struct>]`屬性來表示[記錄](records.md)和[區分](discriminated-unions.md)等位做為結構。</span><span class="sxs-lookup"><span data-stu-id="77a8a-152">You can represent [Records](records.md) and [Discriminated Unions](discriminated-unions.md) as structs with the `[<Struct>]` attribute.</span></span>  <span data-ttu-id="77a8a-153">若要深入瞭解, 請參閱每篇文章。</span><span class="sxs-lookup"><span data-stu-id="77a8a-153">See each article to learn more.</span></span>

## <a name="see-also"></a><span data-ttu-id="77a8a-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77a8a-154">See also</span></span>

- [<span data-ttu-id="77a8a-155">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="77a8a-155">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="77a8a-156">類別</span><span class="sxs-lookup"><span data-stu-id="77a8a-156">Classes</span></span>](classes.md)
- [<span data-ttu-id="77a8a-157">記錄</span><span class="sxs-lookup"><span data-stu-id="77a8a-157">Records</span></span>](records.md)
- [<span data-ttu-id="77a8a-158">成員</span><span class="sxs-lookup"><span data-stu-id="77a8a-158">Members</span></span>](./members/index.md)
