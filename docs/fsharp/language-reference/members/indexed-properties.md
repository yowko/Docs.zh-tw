---
title: 索引屬性
description: 深入瞭解中F#的索引屬性, 可讓您以類似陣列的方式存取已排序的資料。
ms.date: 10/17/2018
ms.openlocfilehash: 379417e31b8e178d8c939e5b23dc144bfb17e562
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627565"
---
# <a name="indexed-properties"></a><span data-ttu-id="8576a-103">索引屬性</span><span class="sxs-lookup"><span data-stu-id="8576a-103">Indexed Properties</span></span>

<span data-ttu-id="8576a-104">在定義可抽象化已排序資料的類別時, 有時會很有説明, 提供該資料的索引存取權, 而不會公開基礎的執行。</span><span class="sxs-lookup"><span data-stu-id="8576a-104">When defining a class that abstracts over ordered data, it can sometimes be helpful to provide indexed access to that data without exposing the underlying implementation.</span></span> <span data-ttu-id="8576a-105">這是使用`Item`成員完成的。</span><span class="sxs-lookup"><span data-stu-id="8576a-105">This is done with the `Item` member.</span></span>

## <a name="syntax"></a><span data-ttu-id="8576a-106">語法</span><span class="sxs-lookup"><span data-stu-id="8576a-106">Syntax</span></span>

```fsharp
// Indexed property that can be read and written to
member self-identifier.Item
    with get(index-values) =
        get-member-body
    and set index-values values-to-set =
        set-member-body

// Indexed property can only be read
member self-identifier.Item
    with get(index-values) =
        get-member-body

// Indexed property that can only be set
member self-identifier.Item
    with set index-values values-to-set =
        set-member-body
```

## <a name="remarks"></a><span data-ttu-id="8576a-107">備註</span><span class="sxs-lookup"><span data-stu-id="8576a-107">Remarks</span></span>

<span data-ttu-id="8576a-108">上述語法的形式`get`顯示如何定義具有`set`和方法的索引屬性、僅具有`get`方法, 或僅具有`set`方法。</span><span class="sxs-lookup"><span data-stu-id="8576a-108">The forms of the previous syntax show how to define indexed properties that have both a `get` and a `set` method, have a `get` method only, or have a `set` method only.</span></span> <span data-ttu-id="8576a-109">您也可以結合僅供 get 使用的語法和針對 set 所顯示的語法, 並產生同時具有 get 和 set 的屬性。</span><span class="sxs-lookup"><span data-stu-id="8576a-109">You can also combine both the syntax shown for get only and the syntax shown for set only, and produce a property that has both get and set.</span></span> <span data-ttu-id="8576a-110">第二個表單可讓您將不同的存取範圍修飾詞和屬性放在 get 和 set 方法上。</span><span class="sxs-lookup"><span data-stu-id="8576a-110">This latter form allows you to put different accessibility modifiers and attributes on the get and set methods.</span></span>

<span data-ttu-id="8576a-111">藉由使用名稱`Item`, 編譯器會將屬性視為預設的索引屬性。</span><span class="sxs-lookup"><span data-stu-id="8576a-111">By using the name `Item`, the compiler treats the property as a default indexed property.</span></span> <span data-ttu-id="8576a-112">*預設的索引屬性*是您可以在物件實例上使用類似陣列的語法來存取的屬性。</span><span class="sxs-lookup"><span data-stu-id="8576a-112">A *default indexed property* is a property that you can access by using array-like syntax on the object instance.</span></span> <span data-ttu-id="8576a-113">例如, 如果`o`是定義此屬性之類型的物件, 則會使用語法`o.[index]`來存取屬性。</span><span class="sxs-lookup"><span data-stu-id="8576a-113">For example, if `o` is an object of the type that defines this property, the syntax `o.[index]` is used to access the property.</span></span>

<span data-ttu-id="8576a-114">存取非預設索引屬性的語法是在括弧中提供屬性名稱和索引, 就像一般成員一樣。</span><span class="sxs-lookup"><span data-stu-id="8576a-114">The syntax for accessing a non-default indexed property is to provide the name of the property and the index in parentheses, just like a regular member.</span></span> <span data-ttu-id="8576a-115">例如, 如果呼叫`o` `Ordinal`上的屬性, 您可以寫入`o.Ordinal(index)`來存取它。</span><span class="sxs-lookup"><span data-stu-id="8576a-115">For example, if the property on `o` is called `Ordinal`, you write `o.Ordinal(index)` to access it.</span></span>

<span data-ttu-id="8576a-116">無論您使用哪一種形式, 都應該一律在索引屬性上使用 set 方法的擴充形式。</span><span class="sxs-lookup"><span data-stu-id="8576a-116">Regardless of which form you use, you should always use the curried form for the set method on an indexed property.</span></span> <span data-ttu-id="8576a-117">如需擴充函數的詳細資訊, 請參閱[函式](../functions/index.md)。</span><span class="sxs-lookup"><span data-stu-id="8576a-117">For information about curried functions, see [Functions](../functions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="8576a-118">範例</span><span class="sxs-lookup"><span data-stu-id="8576a-118">Example</span></span>

<span data-ttu-id="8576a-119">下列程式碼範例說明如何定義和使用具有 get 和 set 方法的預設和非預設索引屬性。</span><span class="sxs-lookup"><span data-stu-id="8576a-119">The following code example illustrates the definition and use of default and non-default indexed properties that have get and set methods.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a><span data-ttu-id="8576a-120">Output</span><span class="sxs-lookup"><span data-stu-id="8576a-120">Output</span></span>

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-values"></a><span data-ttu-id="8576a-121">具有多個索引值的索引屬性</span><span class="sxs-lookup"><span data-stu-id="8576a-121">Indexed Properties with multiple index values</span></span>

<span data-ttu-id="8576a-122">已編制索引的屬性可以有一個以上的索引值。</span><span class="sxs-lookup"><span data-stu-id="8576a-122">Indexed properties can have more than one index value.</span></span> <span data-ttu-id="8576a-123">在此情況下, 使用屬性時, 值會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="8576a-123">In that case, the values are separated by commas when the property is used.</span></span> <span data-ttu-id="8576a-124">這類屬性中的 set 方法必須有兩個擴充引數, 第一個是包含索引鍵的元組, 而第二個是要設定的值。</span><span class="sxs-lookup"><span data-stu-id="8576a-124">The set method in such a property must have two curried arguments, the first of which is a tuple containing the keys, and the second of which is the value to set.</span></span>

<span data-ttu-id="8576a-125">下列程式碼示範如何使用具有多個索引值的索引屬性。</span><span class="sxs-lookup"><span data-stu-id="8576a-125">The following code demonstrates the use of an indexed property with multiple index values.</span></span>

```fsharp
open System.Collections.Generic

/// Basic implementation of a sparse matrix based on a dictionary
type SparseMatrix() =
    let table = new Dictionary<(int * int), float>()
    member __.Item
        // Because the key is comprised of two values, 'get' has two index values
        with get(key1, key2) = table.[(key1, key2)]

        // 'set' has two index values and a new value to place in the key's position
        and set (key1, key2) value = table.[(key1, key2)] <- value

let sm = new SparseMatrix()
for i in 1..1000 do
    sm.[i, i] <- float i * float i
```

## <a name="see-also"></a><span data-ttu-id="8576a-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8576a-126">See also</span></span>

- [<span data-ttu-id="8576a-127">成員</span><span class="sxs-lookup"><span data-stu-id="8576a-127">Members</span></span>](index.md)
