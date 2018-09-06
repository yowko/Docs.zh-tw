---
title: 結構 (F#)
description: '深入了解 F # 結構，壓縮物件型別通常比具有少量資料且行為簡單類型的類別更有效率。'
ms.date: 05/16/2016
ms.openlocfilehash: 889d493af3c9c388bdc7969c02bc7b021b82517d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43799667"
---
# <a name="structures"></a><span data-ttu-id="c3307-103">結構</span><span class="sxs-lookup"><span data-stu-id="c3307-103">Structures</span></span>

<span data-ttu-id="c3307-104">A*結構*是一種精簡的物件類型，可能會比具有少量資料且行為簡單類型的類別更有效率。</span><span class="sxs-lookup"><span data-stu-id="c3307-104">A *structure* is a compact object type that can be more efficient than a class for types that have a small amount of data and simple behavior.</span></span>

## <a name="syntax"></a><span data-ttu-id="c3307-105">語法</span><span class="sxs-lookup"><span data-stu-id="c3307-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="c3307-106">備註</span><span class="sxs-lookup"><span data-stu-id="c3307-106">Remarks</span></span>

<span data-ttu-id="c3307-107">結構*實值型別*、 它們儲存在堆疊上的直接或，作為，所以這表示欄位或類型陣列的元素，內嵌在父代。</span><span class="sxs-lookup"><span data-stu-id="c3307-107">Structures are *value types*, which means that they are stored directly on the stack or, when they are used as fields or array elements, inline in the parent type.</span></span> <span data-ttu-id="c3307-108">有別於類別與記錄，結構具有以值傳遞的語意。</span><span class="sxs-lookup"><span data-stu-id="c3307-108">Unlike classes and records, structures have pass-by-value semantics.</span></span> <span data-ttu-id="c3307-109">這表示它們主要對於經常存取及複製的小型資料彙總相當實用。</span><span class="sxs-lookup"><span data-stu-id="c3307-109">This means that they are useful primarily for small aggregates of data that are accessed and copied frequently.</span></span>

<span data-ttu-id="c3307-110">在先前的語法中，顯示了兩個表單。</span><span class="sxs-lookup"><span data-stu-id="c3307-110">In the previous syntax, two forms are shown.</span></span> <span data-ttu-id="c3307-111">第一個表單的語法略為複雜，但使用卻很頻繁，因為當您使用 `struct` 和 `end` 關鍵字時，可以省略出現在第二個表單中的 `StructAttribute` 屬性。</span><span class="sxs-lookup"><span data-stu-id="c3307-111">The first is not the lightweight syntax, but it is nevertheless frequently used because, when you use the `struct` and `end` keywords, you can omit the `StructAttribute` attribute, which appears in the second form.</span></span> <span data-ttu-id="c3307-112">您可以將 `StructAttribute` 縮寫為只有 `Struct`。</span><span class="sxs-lookup"><span data-stu-id="c3307-112">You can abbreviate `StructAttribute` to just `Struct`.</span></span>

<span data-ttu-id="c3307-113">*型別-定義-項目-和-成員*在先前的語法表示的成員宣告和定義。</span><span class="sxs-lookup"><span data-stu-id="c3307-113">The *type-definition-elements-and-members* in the previous syntax represents member declarations and definitions.</span></span> <span data-ttu-id="c3307-114">結構可以具有建構函式及可變動和不可變的欄位，同時它們可以宣告成員及介面實作。</span><span class="sxs-lookup"><span data-stu-id="c3307-114">Structures can have constructors and mutable and immutable fields, and they can declare members and interface implementations.</span></span> <span data-ttu-id="c3307-115">如需詳細資訊，請參閱 <<c0> [ 成員](members/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c3307-115">For more information, see [Members](members/index.md).</span></span>

<span data-ttu-id="c3307-116">結構無法參與繼承、不能包含 `let` 或 `do` 繫結，且不得以遞迴方式包含其本身類型的欄位 (不過它們可以包含參考其本身類型的參考儲存格)。</span><span class="sxs-lookup"><span data-stu-id="c3307-116">Structures cannot participate in inheritance, cannot contain `let` or `do` bindings, and cannot recursively contain fields of their own type (although they can contain reference cells that reference their own type).</span></span>

<span data-ttu-id="c3307-117">因為結構不允許 `let` 繫結，因此您必須使用 `val` 關鍵字來宣告結構中的欄位。</span><span class="sxs-lookup"><span data-stu-id="c3307-117">Because structures do not allow `let` bindings, you must declare fields in structures by using the `val` keyword.</span></span> <span data-ttu-id="c3307-118">`val` 關鍵字會定義欄位及其類型，但不允許進行初始化。</span><span class="sxs-lookup"><span data-stu-id="c3307-118">The `val` keyword defines a field and its type but does not allow initialization.</span></span> <span data-ttu-id="c3307-119">相反地，`val` 宣告會初始化為零或 null。</span><span class="sxs-lookup"><span data-stu-id="c3307-119">Instead, `val` declarations are initialized to zero or null.</span></span> <span data-ttu-id="c3307-120">基於這個理由，具有隱含建構函式 (也就是緊接在宣告中結構名稱後的指定參數) 的結構，需要 `val` 宣告加上 `DefaultValue` 屬性的附註。</span><span class="sxs-lookup"><span data-stu-id="c3307-120">For this reason, structures that have an implicit constructor (that is, parameters that are given immediately after the structure name in the declaration) require that `val` declarations be annotated with the `DefaultValue` attribute.</span></span> <span data-ttu-id="c3307-121">具有已定義的建構函式之結構，仍然支援零初始化。</span><span class="sxs-lookup"><span data-stu-id="c3307-121">Structures that have a defined constructor still support zero-initialization.</span></span> <span data-ttu-id="c3307-122">因此，`DefaultValue` 屬性是一種零值對於欄位有效的宣告。</span><span class="sxs-lookup"><span data-stu-id="c3307-122">Therefore, the `DefaultValue` attribute is a declaration that such a zero value is valid for the field.</span></span> <span data-ttu-id="c3307-123">結構的隱含建構函式不會執行任何動作，因為類型上不允許 `let` 和 `do` 繫結，但傳入的隱含建構函式參數值均可用作為私用欄位。</span><span class="sxs-lookup"><span data-stu-id="c3307-123">Implicit constructors for structures do not perform any actions because `let` and `do` bindings aren’t allowed on the type, but the implicit constructor parameter values passed in are available as private fields.</span></span>

<span data-ttu-id="c3307-124">明確建構函式可能會牽涉到欄位值的初始化。</span><span class="sxs-lookup"><span data-stu-id="c3307-124">Explicit constructors might involve initialization of field values.</span></span> <span data-ttu-id="c3307-125">當您的結構有明確的建構函式時，它仍然可以支援零初始化。不過，請勿在 `DefaultValue` 宣告上使用 `val` 屬性，因為它與明確建構函式相衝突。</span><span class="sxs-lookup"><span data-stu-id="c3307-125">When you have a structure that has an explicit constructor, it still supports zero-initialization; however, you do not use the `DefaultValue` attribute on the `val` declarations because it conflicts with the explicit constructor.</span></span> <span data-ttu-id="c3307-126">如需詳細資訊`val`宣告，請參閱[明確欄位：`val`關鍵字](members/explicit-fields-the-val-keyword.md)。</span><span class="sxs-lookup"><span data-stu-id="c3307-126">For more information about `val` declarations, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="c3307-127">結構上允許屬性和存取範圍修飾詞，並遵循與其他類型相同的規則。</span><span class="sxs-lookup"><span data-stu-id="c3307-127">Attributes and accessibility modifiers are allowed on structures, and follow the same rules as those for other types.</span></span> <span data-ttu-id="c3307-128">如需詳細資訊，請參閱 <<c0> [ 屬性](attributes.md)並[存取控制](access-control.md)。</span><span class="sxs-lookup"><span data-stu-id="c3307-128">For more information, see [Attributes](attributes.md) and [Access Control](access-control.md).</span></span>

<span data-ttu-id="c3307-129">下列程式碼範例說明結構定義。</span><span class="sxs-lookup"><span data-stu-id="c3307-129">The following code examples illustrate structure definitions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="struct-records-and-discriminated-unions"></a><span data-ttu-id="c3307-130">結構的記錄和差別聯的集</span><span class="sxs-lookup"><span data-stu-id="c3307-130">Struct Records and Discriminated Unions</span></span>

<span data-ttu-id="c3307-131">從 F # 4.1 開始，您可以代表[記錄](records.md)並[差別聯集](discriminated-unions.md)使用的結構為`[<Struct>]`屬性。</span><span class="sxs-lookup"><span data-stu-id="c3307-131">Starting with F# 4.1, you can represent [Records](records.md) and [Discriminated Unions](discriminated-unions.md) as structs with the `[<Struct>]` attribute.</span></span>  <span data-ttu-id="c3307-132">請參閱 < 若要深入了每個發行項。</span><span class="sxs-lookup"><span data-stu-id="c3307-132">See each article to learn more.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3307-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3307-133">See also</span></span>

- [<span data-ttu-id="c3307-134">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="c3307-134">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="c3307-135">類別</span><span class="sxs-lookup"><span data-stu-id="c3307-135">Classes</span></span>](classes.md)
- [<span data-ttu-id="c3307-136">記錄</span><span class="sxs-lookup"><span data-stu-id="c3307-136">Records</span></span>](records.md)
- [<span data-ttu-id="c3307-137">成員</span><span class="sxs-lookup"><span data-stu-id="c3307-137">Members</span></span>](members/index.md)
