---
title: 結構 (F#)
description: '深入了解 F # 結構，壓縮物件型別通常比具有少量資料且行為簡單類型的類別更有效率。'
ms.date: 05/16/2016
ms.openlocfilehash: 08af88132dda28883e246b94585ff4ed8bd2f16a
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46321058"
---
# <a name="structures"></a><span data-ttu-id="2fa95-103">結構</span><span class="sxs-lookup"><span data-stu-id="2fa95-103">Structures</span></span>

<span data-ttu-id="2fa95-104">A*結構*是一種精簡的物件類型，可能會比具有少量資料且行為簡單類型的類別更有效率。</span><span class="sxs-lookup"><span data-stu-id="2fa95-104">A *structure* is a compact object type that can be more efficient than a class for types that have a small amount of data and simple behavior.</span></span>

## <a name="syntax"></a><span data-ttu-id="2fa95-105">語法</span><span class="sxs-lookup"><span data-stu-id="2fa95-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="2fa95-106">備註</span><span class="sxs-lookup"><span data-stu-id="2fa95-106">Remarks</span></span>

<span data-ttu-id="2fa95-107">結構*實值型別*、 它們儲存在堆疊上的直接或，作為，所以這表示欄位或類型陣列的元素，內嵌在父代。</span><span class="sxs-lookup"><span data-stu-id="2fa95-107">Structures are *value types*, which means that they are stored directly on the stack or, when they are used as fields or array elements, inline in the parent type.</span></span> <span data-ttu-id="2fa95-108">有別於類別與記錄，結構具有以值傳遞的語意。</span><span class="sxs-lookup"><span data-stu-id="2fa95-108">Unlike classes and records, structures have pass-by-value semantics.</span></span> <span data-ttu-id="2fa95-109">這表示它們主要對於經常存取及複製的小型資料彙總相當實用。</span><span class="sxs-lookup"><span data-stu-id="2fa95-109">This means that they are useful primarily for small aggregates of data that are accessed and copied frequently.</span></span>

<span data-ttu-id="2fa95-110">在先前的語法中，顯示了兩個表單。</span><span class="sxs-lookup"><span data-stu-id="2fa95-110">In the previous syntax, two forms are shown.</span></span> <span data-ttu-id="2fa95-111">第一個表單的語法略為複雜，但使用卻很頻繁，因為當您使用 `struct` 和 `end` 關鍵字時，可以省略出現在第二個表單中的 `StructAttribute` 屬性。</span><span class="sxs-lookup"><span data-stu-id="2fa95-111">The first is not the lightweight syntax, but it is nevertheless frequently used because, when you use the `struct` and `end` keywords, you can omit the `StructAttribute` attribute, which appears in the second form.</span></span> <span data-ttu-id="2fa95-112">您可以將 `StructAttribute` 縮寫為只有 `Struct`。</span><span class="sxs-lookup"><span data-stu-id="2fa95-112">You can abbreviate `StructAttribute` to just `Struct`.</span></span>

<span data-ttu-id="2fa95-113">*型別-定義-項目-和-成員*在先前的語法表示的成員宣告和定義。</span><span class="sxs-lookup"><span data-stu-id="2fa95-113">The *type-definition-elements-and-members* in the previous syntax represents member declarations and definitions.</span></span> <span data-ttu-id="2fa95-114">結構可以具有建構函式及可變動和不可變的欄位，同時它們可以宣告成員及介面實作。</span><span class="sxs-lookup"><span data-stu-id="2fa95-114">Structures can have constructors and mutable and immutable fields, and they can declare members and interface implementations.</span></span> <span data-ttu-id="2fa95-115">如需詳細資訊，請參閱 <<c0> [ 成員](members/index.md)。</span><span class="sxs-lookup"><span data-stu-id="2fa95-115">For more information, see [Members](members/index.md).</span></span>

<span data-ttu-id="2fa95-116">結構無法參與繼承、不能包含 `let` 或 `do` 繫結，且不得以遞迴方式包含其本身類型的欄位 (不過它們可以包含參考其本身類型的參考儲存格)。</span><span class="sxs-lookup"><span data-stu-id="2fa95-116">Structures cannot participate in inheritance, cannot contain `let` or `do` bindings, and cannot recursively contain fields of their own type (although they can contain reference cells that reference their own type).</span></span>

<span data-ttu-id="2fa95-117">因為結構不允許 `let` 繫結，因此您必須使用 `val` 關鍵字來宣告結構中的欄位。</span><span class="sxs-lookup"><span data-stu-id="2fa95-117">Because structures do not allow `let` bindings, you must declare fields in structures by using the `val` keyword.</span></span> <span data-ttu-id="2fa95-118">`val` 關鍵字會定義欄位及其類型，但不允許進行初始化。</span><span class="sxs-lookup"><span data-stu-id="2fa95-118">The `val` keyword defines a field and its type but does not allow initialization.</span></span> <span data-ttu-id="2fa95-119">相反地，`val` 宣告會初始化為零或 null。</span><span class="sxs-lookup"><span data-stu-id="2fa95-119">Instead, `val` declarations are initialized to zero or null.</span></span> <span data-ttu-id="2fa95-120">基於這個理由，具有隱含建構函式 (也就是緊接在宣告中結構名稱後的指定參數) 的結構，需要 `val` 宣告加上 `DefaultValue` 屬性的附註。</span><span class="sxs-lookup"><span data-stu-id="2fa95-120">For this reason, structures that have an implicit constructor (that is, parameters that are given immediately after the structure name in the declaration) require that `val` declarations be annotated with the `DefaultValue` attribute.</span></span> <span data-ttu-id="2fa95-121">具有已定義的建構函式之結構，仍然支援零初始化。</span><span class="sxs-lookup"><span data-stu-id="2fa95-121">Structures that have a defined constructor still support zero-initialization.</span></span> <span data-ttu-id="2fa95-122">因此，`DefaultValue` 屬性是一種零值對於欄位有效的宣告。</span><span class="sxs-lookup"><span data-stu-id="2fa95-122">Therefore, the `DefaultValue` attribute is a declaration that such a zero value is valid for the field.</span></span> <span data-ttu-id="2fa95-123">結構的隱含建構函式不會執行任何動作，因為類型上不允許 `let` 和 `do` 繫結，但傳入的隱含建構函式參數值均可用作為私用欄位。</span><span class="sxs-lookup"><span data-stu-id="2fa95-123">Implicit constructors for structures do not perform any actions because `let` and `do` bindings aren’t allowed on the type, but the implicit constructor parameter values passed in are available as private fields.</span></span>

<span data-ttu-id="2fa95-124">明確建構函式可能會牽涉到欄位值的初始化。</span><span class="sxs-lookup"><span data-stu-id="2fa95-124">Explicit constructors might involve initialization of field values.</span></span> <span data-ttu-id="2fa95-125">當您的結構有明確的建構函式時，它仍然可以支援零初始化。不過，請勿在 `DefaultValue` 宣告上使用 `val` 屬性，因為它與明確建構函式相衝突。</span><span class="sxs-lookup"><span data-stu-id="2fa95-125">When you have a structure that has an explicit constructor, it still supports zero-initialization; however, you do not use the `DefaultValue` attribute on the `val` declarations because it conflicts with the explicit constructor.</span></span> <span data-ttu-id="2fa95-126">如需詳細資訊`val`宣告，請參閱[明確欄位：`val`關鍵字](members/explicit-fields-the-val-keyword.md)。</span><span class="sxs-lookup"><span data-stu-id="2fa95-126">For more information about `val` declarations, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="2fa95-127">結構上允許屬性和存取範圍修飾詞，並遵循與其他類型相同的規則。</span><span class="sxs-lookup"><span data-stu-id="2fa95-127">Attributes and accessibility modifiers are allowed on structures, and follow the same rules as those for other types.</span></span> <span data-ttu-id="2fa95-128">如需詳細資訊，請參閱 <<c0> [ 屬性](attributes.md)並[存取控制](access-control.md)。</span><span class="sxs-lookup"><span data-stu-id="2fa95-128">For more information, see [Attributes](attributes.md) and [Access Control](access-control.md).</span></span>

<span data-ttu-id="2fa95-129">下列程式碼範例說明結構定義。</span><span class="sxs-lookup"><span data-stu-id="2fa95-129">The following code examples illustrate structure definitions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="byreflike-structs"></a><span data-ttu-id="2fa95-130">ByRefLike 結構</span><span class="sxs-lookup"><span data-stu-id="2fa95-130">ByRefLike structs</span></span>

<span data-ttu-id="2fa95-131">您可以定義您自己的結構可以符合`byref`-例如語意： 請參閱 < [Byref](byrefs.md)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2fa95-131">You can define your own structs that can adhere to `byref`-like semantics: see [Byrefs](byrefs.md) for more information.</span></span> <span data-ttu-id="2fa95-132">做法是使用<xref:System.Runtime.CompilerServices.IsByRefLikeAttribute>屬性：</span><span class="sxs-lookup"><span data-stu-id="2fa95-132">This is done with the <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribute:</span></span>

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="2fa95-133">`IsByRefLike` 並不表示`Struct`。</span><span class="sxs-lookup"><span data-stu-id="2fa95-133">`IsByRefLike` does not imply `Struct`.</span></span> <span data-ttu-id="2fa95-134">兩者都必須要有型別。</span><span class="sxs-lookup"><span data-stu-id="2fa95-134">Both must be present on the type.</span></span>

<span data-ttu-id="2fa95-135">「`byref`-例如"F # 中的結構是堆疊繫結值型別。</span><span class="sxs-lookup"><span data-stu-id="2fa95-135">A "`byref`-like" struct in F# is a stack-bound value type.</span></span> <span data-ttu-id="2fa95-136">永遠不會在 managed 堆積上配置。</span><span class="sxs-lookup"><span data-stu-id="2fa95-136">It is never allocated on the managed heap.</span></span> <span data-ttu-id="2fa95-137">A `byref`-就像結構適用於高效能的程式設計，因為它會強制執行設定的強式存留期和非擷取相關的檢查。</span><span class="sxs-lookup"><span data-stu-id="2fa95-137">A `byref`-like struct is useful for high-performance programming, as it is enforced with set of strong checks about lifetime and non-capture.</span></span> <span data-ttu-id="2fa95-138">規則包括：</span><span class="sxs-lookup"><span data-stu-id="2fa95-138">The rules are:</span></span>

* <span data-ttu-id="2fa95-139">它們可用來當做函式參數、 方法參數、 區域變數、 方法會傳回。</span><span class="sxs-lookup"><span data-stu-id="2fa95-139">They can be used as function parameters, method parameters, local variables, method returns.</span></span>
* <span data-ttu-id="2fa95-140">它們不能是靜態或執行個體的類別或一般結構的成員。</span><span class="sxs-lookup"><span data-stu-id="2fa95-140">They cannot be static or instance members of a class or normal struct.</span></span>
* <span data-ttu-id="2fa95-141">它們無法擷取任何關閉的建構 (`async`方法或 lambda 運算式)。</span><span class="sxs-lookup"><span data-stu-id="2fa95-141">They cannot be captured by any closure construct (`async` methods or lambda expressions).</span></span>
* <span data-ttu-id="2fa95-142">它們不能當做泛型參數。</span><span class="sxs-lookup"><span data-stu-id="2fa95-142">They cannot be used as a generic parameter.</span></span>

<span data-ttu-id="2fa95-143">雖然很希望這些規則會限制使用方式，如此一來滿足承諾的高效能運算以安全的方式。</span><span class="sxs-lookup"><span data-stu-id="2fa95-143">Although these rules very strongly restrict usage, they do so to fulfill the promise of high-performance computing in a safe manner.</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="2fa95-144">唯讀結構</span><span class="sxs-lookup"><span data-stu-id="2fa95-144">ReadOnly structs</span></span>

<span data-ttu-id="2fa95-145">您可以標註結構與<xref:System.Runtime.CompilerServices.IsReadOnlyAttribute>屬性。</span><span class="sxs-lookup"><span data-stu-id="2fa95-145">You can annotate structs with the <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> attribute.</span></span> <span data-ttu-id="2fa95-146">例如: </span><span class="sxs-lookup"><span data-stu-id="2fa95-146">For example:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="2fa95-147">`IsReadOnly` 並不表示`Struct`。</span><span class="sxs-lookup"><span data-stu-id="2fa95-147">`IsReadOnly` does not imply `Struct`.</span></span> <span data-ttu-id="2fa95-148">您必須新增具有`IsReadOnly`結構。</span><span class="sxs-lookup"><span data-stu-id="2fa95-148">You must add both to have an `IsReadOnly` struct.</span></span>

<span data-ttu-id="2fa95-149">使用這個屬性會發出中繼資料，讓 F # 和 C# 以將其視為知道`inref<'T>`和`in ref`分別。</span><span class="sxs-lookup"><span data-stu-id="2fa95-149">Use of this attribute emits metadata letting F# and C# know to treat it as `inref<'T>` and `in ref`, respectively.</span></span>

<span data-ttu-id="2fa95-150">定義 readonly 結構內可變動的值會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="2fa95-150">Defining a mutable value inside of a readonly struct produces an error.</span></span>

## <a name="struct-records-and-discriminated-unions"></a><span data-ttu-id="2fa95-151">結構的記錄和差別聯的集</span><span class="sxs-lookup"><span data-stu-id="2fa95-151">Struct Records and Discriminated Unions</span></span>

<span data-ttu-id="2fa95-152">可代表[記錄](records.md)並[差別聯集](discriminated-unions.md)使用的結構為`[<Struct>]`屬性。</span><span class="sxs-lookup"><span data-stu-id="2fa95-152">You can represent [Records](records.md) and [Discriminated Unions](discriminated-unions.md) as structs with the `[<Struct>]` attribute.</span></span>  <span data-ttu-id="2fa95-153">請參閱 < 若要深入了每個發行項。</span><span class="sxs-lookup"><span data-stu-id="2fa95-153">See each article to learn more.</span></span>

## <a name="see-also"></a><span data-ttu-id="2fa95-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2fa95-154">See also</span></span>

- [<span data-ttu-id="2fa95-155">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="2fa95-155">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="2fa95-156">類別</span><span class="sxs-lookup"><span data-stu-id="2fa95-156">Classes</span></span>](classes.md)
- [<span data-ttu-id="2fa95-157">記錄</span><span class="sxs-lookup"><span data-stu-id="2fa95-157">Records</span></span>](records.md)
- [<span data-ttu-id="2fa95-158">成員</span><span class="sxs-lookup"><span data-stu-id="2fa95-158">Members</span></span>](members/index.md)
