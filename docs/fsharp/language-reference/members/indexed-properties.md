---
title: 索引屬性 (F#)
description: '深入了解 F # 編製索引的屬性，可提供陣列存取權限已排序的資料屬性。'
ms.date: 05/16/2016
ms.openlocfilehash: b3945c7fc22977373b601856036178e890abc13e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="indexed-properties"></a><span data-ttu-id="913d1-103">索引屬性</span><span class="sxs-lookup"><span data-stu-id="913d1-103">Indexed Properties</span></span>

<span data-ttu-id="913d1-104">*索引屬性*提供陣列存取權限的屬性來排序資料。</span><span class="sxs-lookup"><span data-stu-id="913d1-104">*Indexed properties* are properties that provide array-like access to ordered data.</span></span>


## <a name="syntax"></a><span data-ttu-id="913d1-105">語法</span><span class="sxs-lookup"><span data-stu-id="913d1-105">Syntax</span></span>

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.PropertyName
    with get(index-variable) =
        get-function-body
    and set index-variablesvalue-variables =
        set-function-body

// Indexed property that has get only.
member self-identifier.PropertyName(index-variable) =
    get-function-body

// Alternative syntax for indexed property with get only
member self-identifier.PropertyName
    with get(index-variables) =
        get-function-body

// Indexed property that has set only.
member self-identifier.PropertyName
    with set index-variablesvalue-variables = 
        set-function-body
```

## <a name="remarks"></a><span data-ttu-id="913d1-106">備註</span><span class="sxs-lookup"><span data-stu-id="913d1-106">Remarks</span></span>
<span data-ttu-id="913d1-107">先前的語法中的三種形式顯示定義索引的屬性都有`get`和`set`方法，有`get`方法，或具有`set`只方法。</span><span class="sxs-lookup"><span data-stu-id="913d1-107">The three forms of the previous syntax show how to define indexed properties that have both a `get` and a `set` method, have a `get` method only, or have a `set` method only.</span></span> <span data-ttu-id="913d1-108">您也可以合併兩者，僅 get 與集，顯示的語法中所顯示的語法，並產生具有 get 和 set 屬性的屬性。</span><span class="sxs-lookup"><span data-stu-id="913d1-108">You can also combine both the syntax shown for get only and the syntax shown for set only, and produce a property that has both get and set.</span></span> <span data-ttu-id="913d1-109">此第二個表單可讓您將不同的存取範圍修飾詞和屬性放在 get 和 set 方法。</span><span class="sxs-lookup"><span data-stu-id="913d1-109">This latter form allows you to put different accessibility modifiers and attributes on the get and set methods.</span></span>

<span data-ttu-id="913d1-110">當*PropertyName*是`Item`，編譯器會將屬性視為預設索引屬性。</span><span class="sxs-lookup"><span data-stu-id="913d1-110">When the *PropertyName* is `Item`, the compiler treats the property as a default indexed property.</span></span> <span data-ttu-id="913d1-111">A*預設索引的屬性*是屬性，您可以存取的物件執行個體上使用類似陣列的語法。</span><span class="sxs-lookup"><span data-stu-id="913d1-111">A *default indexed property* is a property that you can access by using array-like syntax on the object instance.</span></span> <span data-ttu-id="913d1-112">例如，如果`obj`是定義這個屬性，語法的型別物件`obj.[index]`用來存取屬性。</span><span class="sxs-lookup"><span data-stu-id="913d1-112">For example, if `obj` is an object of the type that defines this property, the syntax `obj.[index]` is used to access the property.</span></span>

<span data-ttu-id="913d1-113">提供屬性的名稱和括號中的索引為存取編製索引的非預設屬性的語法。</span><span class="sxs-lookup"><span data-stu-id="913d1-113">The syntax for accessing a nondefault indexed property is to provide the name of the property and the index in parentheses.</span></span> <span data-ttu-id="913d1-114">例如，如果屬性是`Ordinal`，您撰寫`obj.Ordinal(index)`存取它。</span><span class="sxs-lookup"><span data-stu-id="913d1-114">For example, if the property is `Ordinal`, you write `obj.Ordinal(index)` to access it.</span></span>

<span data-ttu-id="913d1-115">不論您使用的表單，您應該一律使用的局部調用的表單`set`索引屬性的方法。</span><span class="sxs-lookup"><span data-stu-id="913d1-115">Regardless of which form you use, you should always use the curried form for the `set` method on an indexed property.</span></span> <span data-ttu-id="913d1-116">局部調用函式的相關資訊，請參閱[函式](../functions/index.md)。</span><span class="sxs-lookup"><span data-stu-id="913d1-116">For information about curried functions, see [Functions](../functions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="913d1-117">範例</span><span class="sxs-lookup"><span data-stu-id="913d1-117">Example</span></span>

<span data-ttu-id="913d1-118">下列程式碼範例說明如何定義和使用的預設值和非預設索引的屬性有 get 和 set 方法。</span><span class="sxs-lookup"><span data-stu-id="913d1-118">The following code example illustrates the definition and use of default and non-default indexed properties that have get and set methods.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a><span data-ttu-id="913d1-119">輸出</span><span class="sxs-lookup"><span data-stu-id="913d1-119">Output</span></span>

```
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a><span data-ttu-id="913d1-120">多個索引變數的索引的屬性</span><span class="sxs-lookup"><span data-stu-id="913d1-120">Indexed Properties with Multiple Index Variables</span></span>
<span data-ttu-id="913d1-121">索引的屬性可以有一個以上的索引變數。</span><span class="sxs-lookup"><span data-stu-id="913d1-121">Indexed properties can have more than one index variable.</span></span> <span data-ttu-id="913d1-122">在此情況下，變數會以逗號分隔的屬性使用時。</span><span class="sxs-lookup"><span data-stu-id="913d1-122">In that case, the variables are separated by commas when the property is used.</span></span> <span data-ttu-id="913d1-123">在這類屬性的 set 方法必須有兩個局部調用的引數，其中第一個 tuple 包含索引鍵，而第二個所設定的值。</span><span class="sxs-lookup"><span data-stu-id="913d1-123">The set method in such a property must have two curried arguments, the first of which is a tuple containing the keys, and the second of which is the value being set.</span></span>

<span data-ttu-id="913d1-124">下列程式碼示範如何使用多個索引變數的索引屬性。</span><span class="sxs-lookup"><span data-stu-id="913d1-124">The following code demonstrates the use of an indexed property with multiple index variables.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]
    
## <a name="see-also"></a><span data-ttu-id="913d1-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="913d1-125">See Also</span></span>
[<span data-ttu-id="913d1-126">成員</span><span class="sxs-lookup"><span data-stu-id="913d1-126">Members</span></span>](index.md)
