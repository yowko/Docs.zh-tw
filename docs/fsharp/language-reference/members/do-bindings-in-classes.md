---
title: 類別中的 do 繫結
description: 了解如何使用F#'do' 在類別定義中，這會執行動作，或第一次使用的型別時，物件建構的繫結。
ms.date: 05/16/2016
ms.openlocfilehash: 0ddf2b5ca458d0950c2e07bf2c37c205877e2173
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613111"
---
# <a name="do-bindings-in-classes"></a><span data-ttu-id="58f70-103">類別中的 do 繫結</span><span class="sxs-lookup"><span data-stu-id="58f70-103">do Bindings in Classes</span></span>

<span data-ttu-id="58f70-104">A`do`在類別定義的繫結會執行動作的物件建構時或者，若為靜態`do`繫結，當第一次使用類型。</span><span class="sxs-lookup"><span data-stu-id="58f70-104">A `do` binding in a class definition performs actions when the object is constructed or, for a static `do` binding, when the type is first used.</span></span>

## <a name="syntax"></a><span data-ttu-id="58f70-105">語法</span><span class="sxs-lookup"><span data-stu-id="58f70-105">Syntax</span></span>

```fsharp
[static] do expression
```

## <a name="remarks"></a><span data-ttu-id="58f70-106">備註</span><span class="sxs-lookup"><span data-stu-id="58f70-106">Remarks</span></span>

<span data-ttu-id="58f70-107">A`do`搭配使用，或是之後，就會出現繫結`let`繫結類別定義中的成員定義之前。</span><span class="sxs-lookup"><span data-stu-id="58f70-107">A `do` binding appears together with or after `let` bindings but before member definitions in a class definition.</span></span> <span data-ttu-id="58f70-108">雖然`do`是選擇性的關鍵字`do`繫結在模組層級中，它不是選擇性的`do`類別定義中的繫結。</span><span class="sxs-lookup"><span data-stu-id="58f70-108">Although the `do` keyword is optional for `do` bindings at the module level, it is not optional for `do` bindings in a class definition.</span></span>

<span data-ttu-id="58f70-109">針對每個物件的任何建構指定的型別，而非靜態`do`繫結和非靜態`let`繫結以其出現在類別定義的順序執行。</span><span class="sxs-lookup"><span data-stu-id="58f70-109">For the construction of every object of any given type, non-static `do` bindings and non-static `let` bindings are executed in the order in which they appear in the class definition.</span></span> <span data-ttu-id="58f70-110">多個`do`繫結可能會發生在一種類型。</span><span class="sxs-lookup"><span data-stu-id="58f70-110">Multiple `do` bindings can occur in one type.</span></span> <span data-ttu-id="58f70-111">非靜態`let`繫結和非靜態`do`繫結會變成主要建構函式的主體。</span><span class="sxs-lookup"><span data-stu-id="58f70-111">The non-static `let` bindings and the non-static `do` bindings become the body of the primary constructor.</span></span> <span data-ttu-id="58f70-112">在非靜態程式碼`do`主要建構函式參數的任何值或函式中所定義的可以參考繫結區段`let`繫結區段。</span><span class="sxs-lookup"><span data-stu-id="58f70-112">The code in the non-static `do` bindings section can reference the primary constructor parameters and any values or functions that are defined in the `let` bindings section.</span></span>

<span data-ttu-id="58f70-113">非靜態`do`繫結可以存取類別的成員，只要類別具有本身的識別項所定義`as`標題，並只要所有使用這些成員的類別的自我識別項都限定的類別中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="58f70-113">Non-static `do` bindings can access members of the class as long as the class has a self identifier that is defined by an `as` keyword in the class heading, and as long as all uses of those members are qualified with the self identifier for the class.</span></span>

<span data-ttu-id="58f70-114">因為`let`繫結初始化的類別，也就是通常需要保證成員會在如預期般運作，私用欄位`do`繫結通常會放在後`let`繫結中的程式碼以便`do`繫結可以執行與完整初始化的物件。</span><span class="sxs-lookup"><span data-stu-id="58f70-114">Because `let` bindings initialize the private fields of a class, which is often necessary to guarantee that members behave as expected, `do` bindings are usually put after `let` bindings so that code in the `do` binding can execute with a fully initialized object.</span></span> <span data-ttu-id="58f70-115">如果您的程式碼嘗試使用成員初始設定完成之前，會引發 InvalidOperationException。</span><span class="sxs-lookup"><span data-stu-id="58f70-115">If your code attempts to use a member before the initialization is complete, an InvalidOperationException is raised.</span></span>

<span data-ttu-id="58f70-116">靜態`do`繫結可以參考靜態成員或欄位的封入類別，但不是執行個體成員或欄位。</span><span class="sxs-lookup"><span data-stu-id="58f70-116">Static `do` bindings can reference static members or fields of the enclosing class but not instance members or fields.</span></span> <span data-ttu-id="58f70-117">靜態`do`繫結會成為類別，會執行之前先使用此類別的靜態初始設定式的一部分。</span><span class="sxs-lookup"><span data-stu-id="58f70-117">Static `do` bindings become part of the static initializer for the class, which is guaranteed to execute before the class is first used.</span></span>

<span data-ttu-id="58f70-118">屬性會忽略`do`類型中的繫結。</span><span class="sxs-lookup"><span data-stu-id="58f70-118">Attributes are ignored for `do` bindings in types.</span></span> <span data-ttu-id="58f70-119">如果屬性是的執行中的程式碼需要`do`繫結，它必須套用至主要建構函式。</span><span class="sxs-lookup"><span data-stu-id="58f70-119">If an attribute is required for code that executes in a `do` binding, it must be applied to the primary constructor.</span></span>

<span data-ttu-id="58f70-120">下列程式碼中，類別所擁有的靜態`do`繫結和非靜態`do`繫結。</span><span class="sxs-lookup"><span data-stu-id="58f70-120">In the following code, a class has a static `do` binding and a non-static `do` binding.</span></span> <span data-ttu-id="58f70-121">物件具有兩個參數的建構函式`a`並`b`，且兩個私用欄位已定義在`let`類別的繫結。</span><span class="sxs-lookup"><span data-stu-id="58f70-121">The object has a constructor that has two parameters, `a` and `b`, and two private fields are defined in the `let` bindings for the class.</span></span> <span data-ttu-id="58f70-122">此外，也會定義兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="58f70-122">Two properties are also defined.</span></span> <span data-ttu-id="58f70-123">這些都在範圍內非靜態`do`繫結區段，如線條會列印所有這些值的說明。</span><span class="sxs-lookup"><span data-stu-id="58f70-123">All of these are in scope in the non-static `do` bindings section, as is illustrated by the line that prints all those values.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

<span data-ttu-id="58f70-124">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="58f70-124">The output is as follows.</span></span>

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a><span data-ttu-id="58f70-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58f70-125">See also</span></span>

- [<span data-ttu-id="58f70-126">成員</span><span class="sxs-lookup"><span data-stu-id="58f70-126">Members</span></span>](index.md)
- [<span data-ttu-id="58f70-127">類別</span><span class="sxs-lookup"><span data-stu-id="58f70-127">Classes</span></span>](../classes.md)
- [<span data-ttu-id="58f70-128">建構函式</span><span class="sxs-lookup"><span data-stu-id="58f70-128">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="58f70-129">類別中的 `let` 繫結</span><span class="sxs-lookup"><span data-stu-id="58f70-129">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
- [<span data-ttu-id="58f70-130">`do` 繫結</span><span class="sxs-lookup"><span data-stu-id="58f70-130">`do` Bindings</span></span>](../functions/do-Bindings.md)