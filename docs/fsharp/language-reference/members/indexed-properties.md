---
title: 索引屬性 (F#)
description: 深入了解索引的屬性，在F#，可讓已排序的資料類似陣列存取。
ms.date: 10/17/2018
ms.openlocfilehash: 3dac60eba3d9e7a9c3e76ad7ee051e6b30b88636
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452244"
---
# <a name="indexed-properties"></a><span data-ttu-id="34198-103">索引屬性</span><span class="sxs-lookup"><span data-stu-id="34198-103">Indexed Properties</span></span>

<span data-ttu-id="34198-104">在定義類別，用來對已排序的資料擷取時，有時候很有幫助，而不會公開基礎實作中提供索引的存取該資料。</span><span class="sxs-lookup"><span data-stu-id="34198-104">When defining a class that abstracts over ordered data, it can sometimes be helpful to provide indexed access to that data without exposing the underlying implementation.</span></span> <span data-ttu-id="34198-105">做法是使用`Index`成員。</span><span class="sxs-lookup"><span data-stu-id="34198-105">This is done with the `Index` member.</span></span>

## <a name="syntax"></a><span data-ttu-id="34198-106">語法</span><span class="sxs-lookup"><span data-stu-id="34198-106">Syntax</span></span>

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.Index
    with get(index-values) =
        get-member-body
    and set index-values values-to-set =
        set-member-body

// Indexed property with get only
member self-identifier.Index
    with get(index-values) =
        get-member-body

// Indexed property that has set only.
member self-identifier.Index
    with set index-values values-to-set =
        set-member-body
```

## <a name="remarks"></a><span data-ttu-id="34198-107">備註</span><span class="sxs-lookup"><span data-stu-id="34198-107">Remarks</span></span>

<span data-ttu-id="34198-108">先前的語法中的表單會顯示如何定義索引的屬性都有`get`和`set`方法中，有`get`方法，或有`set`僅方法。</span><span class="sxs-lookup"><span data-stu-id="34198-108">The forms of the previous syntax show how to define indexed properties that have both a `get` and a `set` method, have a `get` method only, or have a `set` method only.</span></span> <span data-ttu-id="34198-109">您也可以結合這兩僅 get 和集合，顯示的語法所示的語法，並產生具有 get 和 set 的屬性。</span><span class="sxs-lookup"><span data-stu-id="34198-109">You can also combine both the syntax shown for get only and the syntax shown for set only, and produce a property that has both get and set.</span></span> <span data-ttu-id="34198-110">此第二個表單可讓您將不同的存取範圍修飾詞和屬性放在 get 和 set 方法。</span><span class="sxs-lookup"><span data-stu-id="34198-110">This latter form allows you to put different accessibility modifiers and attributes on the get and set methods.</span></span>

<span data-ttu-id="34198-111">使用名稱`Item`，編譯器會將屬性視為預設索引屬性。</span><span class="sxs-lookup"><span data-stu-id="34198-111">By using the name `Item`, the compiler treats the property as a default indexed property.</span></span> <span data-ttu-id="34198-112">A*預設索引屬性*是屬性，您可以存取的物件執行個體上使用類似陣列的語法。</span><span class="sxs-lookup"><span data-stu-id="34198-112">A *default indexed property* is a property that you can access by using array-like syntax on the object instance.</span></span> <span data-ttu-id="34198-113">例如，如果`o`會定義此屬性，語法類型的物件`o.[index]`用來存取屬性。</span><span class="sxs-lookup"><span data-stu-id="34198-113">For example, if `o` is an object of the type that defines this property, the syntax `o.[index]` is used to access the property.</span></span>

<span data-ttu-id="34198-114">存取非預設的索引的屬性的語法是要提供屬性的索引，就像一般成員一樣括號括住的名稱。</span><span class="sxs-lookup"><span data-stu-id="34198-114">The syntax for accessing a non-default indexed property is to provide the name of the property and the index in parentheses, just like a regular member.</span></span> <span data-ttu-id="34198-115">例如，如果上的屬性`o`稱為`Ordinal`，您撰寫`o.Ordinal(index)`存取它。</span><span class="sxs-lookup"><span data-stu-id="34198-115">For example, if the property on `o` is called `Ordinal`, you write `o.Ordinal(index)` to access it.</span></span>

<span data-ttu-id="34198-116">不論您使用哪一個表單，您應該一律使用局部調用的形式的索引屬性上的 set 方法。</span><span class="sxs-lookup"><span data-stu-id="34198-116">Regardless of which form you use, you should always use the curried form for the set method on an indexed property.</span></span> <span data-ttu-id="34198-117">如需局部調用的函式的詳細資訊，請參閱[函式](../functions/index.md)。</span><span class="sxs-lookup"><span data-stu-id="34198-117">For information about curried functions, see [Functions](../functions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="34198-118">範例</span><span class="sxs-lookup"><span data-stu-id="34198-118">Example</span></span>

<span data-ttu-id="34198-119">下列程式碼範例說明如何定義和使用預設值和非預設索引的屬性，有 get 和 set 方法。</span><span class="sxs-lookup"><span data-stu-id="34198-119">The following code example illustrates the definition and use of default and non-default indexed properties that have get and set methods.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a><span data-ttu-id="34198-120">輸出</span><span class="sxs-lookup"><span data-stu-id="34198-120">Output</span></span>

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a><span data-ttu-id="34198-121">具有多個索引變數的索引的屬性</span><span class="sxs-lookup"><span data-stu-id="34198-121">Indexed Properties with Multiple Index Variables</span></span>

<span data-ttu-id="34198-122">索引的屬性可以有一個以上的索引變數。</span><span class="sxs-lookup"><span data-stu-id="34198-122">Indexed properties can have more than one index variable.</span></span> <span data-ttu-id="34198-123">在此情況下，變數會以逗號分隔的屬性使用時。</span><span class="sxs-lookup"><span data-stu-id="34198-123">In that case, the variables are separated by commas when the property is used.</span></span> <span data-ttu-id="34198-124">在這類屬性的 set 方法必須有兩個局部調用的引數，其中第一個 tuple，其中包含索引鍵，而第二個所設定的值。</span><span class="sxs-lookup"><span data-stu-id="34198-124">The set method in such a property must have two curried arguments, the first of which is a tuple containing the keys, and the second of which is the value being set.</span></span>

<span data-ttu-id="34198-125">下列程式碼示範如何使用多個索引變數的索引屬性。</span><span class="sxs-lookup"><span data-stu-id="34198-125">The following code demonstrates the use of an indexed property with multiple index variables.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]

## <a name="see-also"></a><span data-ttu-id="34198-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34198-126">See also</span></span>

- [<span data-ttu-id="34198-127">成員</span><span class="sxs-lookup"><span data-stu-id="34198-127">Members</span></span>](index.md)
