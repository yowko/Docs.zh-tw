---
title: "結構 (F#)"
description: "深入了解 F # 結構，壓縮物件型別通常更有效率的類別，只需要編寫小量的資料和簡單行為的類型。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 50819506-3210-418f-9602-0ee1c9a52177
ms.openlocfilehash: 542b69a5aacb8fcfb0e8f6d6c943fe1954c4c59c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="structures"></a><span data-ttu-id="e9127-104">結構</span><span class="sxs-lookup"><span data-stu-id="e9127-104">Structures</span></span>

<span data-ttu-id="e9127-105">A*結構*可以更有效率的類別具有少量資料和簡單行為的類型是精簡的物件類型。</span><span class="sxs-lookup"><span data-stu-id="e9127-105">A *structure* is a compact object type that can be more efficient than a class for types that have a small amount of data and simple behavior.</span></span>

## <a name="syntax"></a><span data-ttu-id="e9127-106">語法</span><span class="sxs-lookup"><span data-stu-id="e9127-106">Syntax</span></span>

```fsharp
[ attributes ]
type [accessibility-modifier] type-name =
    struct
        type-definition-elements
    end
// or
[ attributes ]
[<StructAttribute>]
type [accessibility-modifier] type-name =
    type-definition-elements
```

## <a name="remarks"></a><span data-ttu-id="e9127-107">備註</span><span class="sxs-lookup"><span data-stu-id="e9127-107">Remarks</span></span>
<span data-ttu-id="e9127-108">兩個結構*實值型別的*，也就是說，它們會儲存在堆疊上直接或，做為使用中時的欄位或陣列元素的父系中的內嵌輸入。</span><span class="sxs-lookup"><span data-stu-id="e9127-108">Structures are *value types*, which means that they are stored directly on the stack or, when they are used as fields or array elements, inline in the parent type.</span></span> <span data-ttu-id="e9127-109">有別於類別與記錄，結構具有以值傳遞的語意。</span><span class="sxs-lookup"><span data-stu-id="e9127-109">Unlike classes and records, structures have pass-by-value semantics.</span></span> <span data-ttu-id="e9127-110">這表示它們主要對於經常存取及複製的小型資料彙總相當實用。</span><span class="sxs-lookup"><span data-stu-id="e9127-110">This means that they are useful primarily for small aggregates of data that are accessed and copied frequently.</span></span>

<span data-ttu-id="e9127-111">在先前的語法中，顯示了兩個表單。</span><span class="sxs-lookup"><span data-stu-id="e9127-111">In the previous syntax, two forms are shown.</span></span> <span data-ttu-id="e9127-112">第一個表單的語法略為複雜，但使用卻很頻繁，因為當您使用 `struct` 和 `end` 關鍵字時，可以省略出現在第二個表單中的 `StructAttribute` 屬性。</span><span class="sxs-lookup"><span data-stu-id="e9127-112">The first is not the lightweight syntax, but it is nevertheless frequently used because, when you use the `struct` and `end` keywords, you can omit the `StructAttribute` attribute, which appears in the second form.</span></span> <span data-ttu-id="e9127-113">您可以將 `StructAttribute` 縮寫為只有 `Struct`。</span><span class="sxs-lookup"><span data-stu-id="e9127-113">You can abbreviate `StructAttribute` to just `Struct`.</span></span>

<span data-ttu-id="e9127-114">*類型定義項目*先前語法中代表成員宣告和定義。</span><span class="sxs-lookup"><span data-stu-id="e9127-114">The *type-definition-elements* in the previous syntax represents member declarations and definitions.</span></span> <span data-ttu-id="e9127-115">結構可以具有建構函式及可變動和不可變的欄位，同時它們可以宣告成員及介面實作。</span><span class="sxs-lookup"><span data-stu-id="e9127-115">Structures can have constructors and mutable and immutable fields, and they can declare members and interface implementations.</span></span> <span data-ttu-id="e9127-116">如需詳細資訊，請參閱[成員](members/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e9127-116">For more information, see [Members](members/index.md).</span></span>

<span data-ttu-id="e9127-117">結構無法參與繼承、不能包含 `let` 或 `do` 繫結，且不得以遞迴方式包含其本身類型的欄位 (不過它們可以包含參考其本身類型的參考儲存格)。</span><span class="sxs-lookup"><span data-stu-id="e9127-117">Structures cannot participate in inheritance, cannot contain `let` or `do` bindings, and cannot recursively contain fields of their own type (although they can contain reference cells that reference their own type).</span></span>

<span data-ttu-id="e9127-118">因為結構不允許 `let` 繫結，因此您必須使用 `val` 關鍵字來宣告結構中的欄位。</span><span class="sxs-lookup"><span data-stu-id="e9127-118">Because structures do not allow `let` bindings, you must declare fields in structures by using the `val` keyword.</span></span> <span data-ttu-id="e9127-119">`val` 關鍵字會定義欄位及其類型，但不允許進行初始化。</span><span class="sxs-lookup"><span data-stu-id="e9127-119">The `val` keyword defines a field and its type but does not allow initialization.</span></span> <span data-ttu-id="e9127-120">相反地，`val` 宣告會初始化為零或 null。</span><span class="sxs-lookup"><span data-stu-id="e9127-120">Instead, `val` declarations are initialized to zero or null.</span></span> <span data-ttu-id="e9127-121">基於這個理由，具有隱含建構函式 (也就是緊接在宣告中結構名稱後的指定參數) 的結構，需要 `val` 宣告加上 `DefaultValue` 屬性的附註。</span><span class="sxs-lookup"><span data-stu-id="e9127-121">For this reason, structures that have an implicit constructor (that is, parameters that are given immediately after the structure name in the declaration) require that `val` declarations be annotated with the `DefaultValue` attribute.</span></span> <span data-ttu-id="e9127-122">具有已定義的建構函式之結構，仍然支援零初始化。</span><span class="sxs-lookup"><span data-stu-id="e9127-122">Structures that have a defined constructor still support zero-initialization.</span></span> <span data-ttu-id="e9127-123">因此，`DefaultValue` 屬性是一種零值對於欄位有效的宣告。</span><span class="sxs-lookup"><span data-stu-id="e9127-123">Therefore, the `DefaultValue` attribute is a declaration that such a zero value is valid for the field.</span></span> <span data-ttu-id="e9127-124">結構的隱含建構函式不會執行任何動作，因為類型上不允許 `let` 和 `do` 繫結，但傳入的隱含建構函式參數值均可用作為私用欄位。</span><span class="sxs-lookup"><span data-stu-id="e9127-124">Implicit constructors for structures do not perform any actions because `let` and `do` bindings aren’t allowed on the type, but the implicit constructor parameter values passed in are available as private fields.</span></span>

<span data-ttu-id="e9127-125">明確建構函式可能會牽涉到欄位值的初始化。</span><span class="sxs-lookup"><span data-stu-id="e9127-125">Explicit constructors might involve initialization of field values.</span></span> <span data-ttu-id="e9127-126">當您的結構有明確的建構函式時，它仍然可以支援零初始化。不過，請勿在 `DefaultValue` 宣告上使用 `val` 屬性，因為它與明確建構函式相衝突。</span><span class="sxs-lookup"><span data-stu-id="e9127-126">When you have a structure that has an explicit constructor, it still supports zero-initialization; however, you do not use the `DefaultValue` attribute on the `val` declarations because it conflicts with the explicit constructor.</span></span> <span data-ttu-id="e9127-127">如需有關`val`宣告，請參閱[明確欄位：`val`關鍵字](members/explicit-fields-the-val-keyword.md)。</span><span class="sxs-lookup"><span data-stu-id="e9127-127">For more information about `val` declarations, see [Explicit Fields: The `val` Keyword](members/explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="e9127-128">結構上允許屬性和存取範圍修飾詞，並遵循與其他類型相同的規則。</span><span class="sxs-lookup"><span data-stu-id="e9127-128">Attributes and accessibility modifiers are allowed on structures, and follow the same rules as those for other types.</span></span> <span data-ttu-id="e9127-129">如需詳細資訊，請參閱[屬性](attributes.md)和[存取控制](access-control.md)。</span><span class="sxs-lookup"><span data-stu-id="e9127-129">For more information, see [Attributes](attributes.md) and [Access Control](access-control.md).</span></span>

<span data-ttu-id="e9127-130">下列程式碼範例說明結構定義。</span><span class="sxs-lookup"><span data-stu-id="e9127-130">The following code examples illustrate structure definitions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2501.fs)]

## <a name="struct-records-and-discriminated-unions"></a><span data-ttu-id="e9127-131">結構的記錄和差別聯的集</span><span class="sxs-lookup"><span data-stu-id="e9127-131">Struct Records and Discriminated Unions</span></span>

<span data-ttu-id="e9127-132">從 F # 4.1 開始，您可以表示[記錄](records.md)和[差別等位](discriminated-unions.md)為結構與`[<Struct>]`屬性。</span><span class="sxs-lookup"><span data-stu-id="e9127-132">Starting with F# 4.1, you can represent [Records](records.md) and [Discriminated Unions](discriminated-unions.md) as structs with the `[<Struct>]` attribute.</span></span>  <span data-ttu-id="e9127-133">請參閱 < 若要進一步了解每個發行項。</span><span class="sxs-lookup"><span data-stu-id="e9127-133">See each article to learn more.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="e9127-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9127-134">See Also</span></span>
[<span data-ttu-id="e9127-135">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="e9127-135">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="e9127-136">類別</span><span class="sxs-lookup"><span data-stu-id="e9127-136">Classes</span></span>](classes.md)

[<span data-ttu-id="e9127-137">記錄</span><span class="sxs-lookup"><span data-stu-id="e9127-137">Records</span></span>](records.md)

[<span data-ttu-id="e9127-138">成員</span><span class="sxs-lookup"><span data-stu-id="e9127-138">Members</span></span>](members/index.md)
