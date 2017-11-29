---
title: "類別中的 do 繫結 (F#)"
description: "了解如何使用 F # 'do' 繫結，在類別定義中，這會執行動作，當物件的建構或第一次使用的型別。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 78987cb8-bdba-46e2-b5b2-994c83fe42c4
ms.openlocfilehash: f9582338306d87c3dd799425083037cc95b31b1e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="do-bindings-in-classes"></a><span data-ttu-id="9428e-104">類別中的 do 繫結</span><span class="sxs-lookup"><span data-stu-id="9428e-104">do Bindings in Classes</span></span>

<span data-ttu-id="9428e-105">A`do`繫結的類別定義中執行的動作，當物件的建構或時，靜態`do`繫結，當第一次使用類型。</span><span class="sxs-lookup"><span data-stu-id="9428e-105">A `do` binding in a class definition performs actions when the object is constructed or, for a static `do` binding, when the type is first used.</span></span>


## <a name="syntax"></a><span data-ttu-id="9428e-106">語法</span><span class="sxs-lookup"><span data-stu-id="9428e-106">Syntax</span></span>

```fsharp
[static] do expression
```

## <a name="remarks"></a><span data-ttu-id="9428e-107">備註</span><span class="sxs-lookup"><span data-stu-id="9428e-107">Remarks</span></span>
<span data-ttu-id="9428e-108">A`do`搭配或之後，會顯示繫結`let`繫結的類別定義中的成員定義之前。</span><span class="sxs-lookup"><span data-stu-id="9428e-108">A `do` binding appears together with or after `let` bindings but before member definitions in a class definition.</span></span> <span data-ttu-id="9428e-109">雖然`do`關鍵字是選擇性的`do`繫結在模組層級，它不是選擇性的`do`類別定義中的繫結。</span><span class="sxs-lookup"><span data-stu-id="9428e-109">Although the `do` keyword is optional for `do` bindings at the module level, it is not optional for `do` bindings in a class definition.</span></span>

<span data-ttu-id="9428e-110">針對每個物件的任何建構指定的型別，而非靜態`do`繫結和非靜態`let`繫結以它們出現在類別定義中的順序執行。</span><span class="sxs-lookup"><span data-stu-id="9428e-110">For the construction of every object of any given type, non-static `do` bindings and non-static `let` bindings are executed in the order in which they appear in the class definition.</span></span> <span data-ttu-id="9428e-111">多個`do`繫結可能會發生一個類型中。</span><span class="sxs-lookup"><span data-stu-id="9428e-111">Multiple `do` bindings can occur in one type.</span></span> <span data-ttu-id="9428e-112">非靜態`let`繫結和非靜態`do`繫結會變成主要建構函式的主體。</span><span class="sxs-lookup"><span data-stu-id="9428e-112">The non-static `let` bindings and the non-static `do` bindings become the body of the primary constructor.</span></span> <span data-ttu-id="9428e-113">在非靜態程式碼`do`主要建構函式參數和值或定義中的函式，可以參考繫結區段`let`繫結區段。</span><span class="sxs-lookup"><span data-stu-id="9428e-113">The code in the non-static `do` bindings section can reference the primary constructor parameters and any values or functions that are defined in the `let` bindings section.</span></span>

<span data-ttu-id="9428e-114">非靜態`do`繫結可存取類別的成員，只要類別有本身的識別項所定義`as`行標頭，，只要所有使用這些成員以類別自我識別項都限定的類別中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="9428e-114">Non-static `do` bindings can access members of the class as long as the class has a self identifier that is defined by an `as` keyword in the class heading, and as long as all uses of those members are qualified with the self identifier for the class.</span></span>

<span data-ttu-id="9428e-115">因為`let`繫結初始化私用欄位的類別，這個方法通常需要保證成員會如預期運作，`do`繫結通常會放在之後`let`繫結中的程式碼讓`do`繫結可以執行與完整初始化的物件。</span><span class="sxs-lookup"><span data-stu-id="9428e-115">Because `let` bindings initialize the private fields of a class, which is often necessary to guarantee that members behave as expected, `do` bindings are usually put after `let` bindings so that code in the `do` binding can execute with a fully initialized object.</span></span> <span data-ttu-id="9428e-116">如果您的程式碼嘗試使用成員初始設定完成之前，會引發 InvalidOperationException。</span><span class="sxs-lookup"><span data-stu-id="9428e-116">If your code attempts to use a member before the initialization is complete, an InvalidOperationException is raised.</span></span>

<span data-ttu-id="9428e-117">靜態`do`繫結可以參考靜態成員或欄位封入類別，但不是執行個體成員或欄位。</span><span class="sxs-lookup"><span data-stu-id="9428e-117">Static `do` bindings can reference static members or fields of the enclosing class but not instance members or fields.</span></span> <span data-ttu-id="9428e-118">靜態`do`繫結會成為類別，可保證執行之前先使用的類別的靜態初始設定式的一部分。</span><span class="sxs-lookup"><span data-stu-id="9428e-118">Static `do` bindings become part of the static initializer for the class, which is guaranteed to execute before the class is first used.</span></span>

<span data-ttu-id="9428e-119">屬性會被忽略`do`類型中的繫結。</span><span class="sxs-lookup"><span data-stu-id="9428e-119">Attributes are ignored for `do` bindings in types.</span></span> <span data-ttu-id="9428e-120">屬性是否需要執行的程式碼`do`繫結時，它必須套用至主要建構函式。</span><span class="sxs-lookup"><span data-stu-id="9428e-120">If an attribute is required for code that executes in a `do` binding, it must be applied to the primary constructor.</span></span>

<span data-ttu-id="9428e-121">下列程式碼中，類別還具有靜態`do`繫結和非靜態`do`繫結。</span><span class="sxs-lookup"><span data-stu-id="9428e-121">In the following code, a class has a static `do` binding and a non-static `do` binding.</span></span> <span data-ttu-id="9428e-122">物件具有兩個參數的建構函式`a`和`b`，且兩個私用欄位定義於`let`繫結的類別。</span><span class="sxs-lookup"><span data-stu-id="9428e-122">The object has a constructor that has two parameters, `a` and `b`, and two private fields are defined in the `let` bindings for the class.</span></span> <span data-ttu-id="9428e-123">也會定義兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="9428e-123">Two properties are also defined.</span></span> <span data-ttu-id="9428e-124">所有這些都是在非靜態範圍中`do`繫結區段中，會列印所有這些值的行中所示。</span><span class="sxs-lookup"><span data-stu-id="9428e-124">All of these are in scope in the non-static `do` bindings section, as is illustrated by the line that prints all those values.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

<span data-ttu-id="9428e-125">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="9428e-125">The output is as follows.</span></span>

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a><span data-ttu-id="9428e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9428e-126">See Also</span></span>
[<span data-ttu-id="9428e-127">成員</span><span class="sxs-lookup"><span data-stu-id="9428e-127">Members</span></span>](index.md)

[<span data-ttu-id="9428e-128">類別</span><span class="sxs-lookup"><span data-stu-id="9428e-128">Classes</span></span>](../classes.md)

[<span data-ttu-id="9428e-129">建構函式</span><span class="sxs-lookup"><span data-stu-id="9428e-129">Constructors</span></span>](constructors.md)

[<span data-ttu-id="9428e-130">類別中的 `let` 繫結</span><span class="sxs-lookup"><span data-stu-id="9428e-130">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)

[<span data-ttu-id="9428e-131">`do`繫結</span><span class="sxs-lookup"><span data-stu-id="9428e-131">`do` Bindings</span></span>](../functions/do-Bindings.md)
