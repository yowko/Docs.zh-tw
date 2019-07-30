---
title: 類別中的 do 繫結
description: 瞭解如何在類別定義F#中使用「do」系結, 此系結會在物件建立時或第一次使用型別時, 執行動作。
ms.date: 05/16/2016
ms.openlocfilehash: ced4f1bb17d9e23bf51cc79b5a275cc334cca013
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627584"
---
# <a name="do-bindings-in-classes"></a><span data-ttu-id="172db-103">類別中的 do 繫結</span><span class="sxs-lookup"><span data-stu-id="172db-103">do Bindings in Classes</span></span>

<span data-ttu-id="172db-104">類別定義中的系結會在物件建立時執行動作, 或在第一`do`次使用該類型時, 針對靜態系結。 `do`</span><span class="sxs-lookup"><span data-stu-id="172db-104">A `do` binding in a class definition performs actions when the object is constructed or, for a static `do` binding, when the type is first used.</span></span>

## <a name="syntax"></a><span data-ttu-id="172db-105">語法</span><span class="sxs-lookup"><span data-stu-id="172db-105">Syntax</span></span>

```fsharp
[static] do expression
```

## <a name="remarks"></a><span data-ttu-id="172db-106">備註</span><span class="sxs-lookup"><span data-stu-id="172db-106">Remarks</span></span>

<span data-ttu-id="172db-107">系結會與系結一起`let`出現, 但在類別定義中的成員定義之前。 `do`</span><span class="sxs-lookup"><span data-stu-id="172db-107">A `do` binding appears together with or after `let` bindings but before member definitions in a class definition.</span></span> <span data-ttu-id="172db-108">雖然關鍵字對於`do`模組層級的系結是選擇性的, 但對於`do`類別定義中的系結而言, 並不是選擇性的。 `do`</span><span class="sxs-lookup"><span data-stu-id="172db-108">Although the `do` keyword is optional for `do` bindings at the module level, it is not optional for `do` bindings in a class definition.</span></span>

<span data-ttu-id="172db-109">針對任何給定類型的每個物件的結構, 非靜態`do`系結和非靜態`let`系結會依照它們出現在類別定義中的順序來執行。</span><span class="sxs-lookup"><span data-stu-id="172db-109">For the construction of every object of any given type, non-static `do` bindings and non-static `let` bindings are executed in the order in which they appear in the class definition.</span></span> <span data-ttu-id="172db-110">一個`do`類型中可能會發生多個系結。</span><span class="sxs-lookup"><span data-stu-id="172db-110">Multiple `do` bindings can occur in one type.</span></span> <span data-ttu-id="172db-111">非靜態`let`系結和非靜態`do`系結會成為主要函式的主體。</span><span class="sxs-lookup"><span data-stu-id="172db-111">The non-static `let` bindings and the non-static `do` bindings become the body of the primary constructor.</span></span> <span data-ttu-id="172db-112">[非靜態`do`系結] 區段中的程式碼可以參考主要的函式參數, 以及系結區段`let`中所定義的任何值或函數。</span><span class="sxs-lookup"><span data-stu-id="172db-112">The code in the non-static `do` bindings section can reference the primary constructor parameters and any values or functions that are defined in the `let` bindings section.</span></span>

<span data-ttu-id="172db-113">只要類別具有`do`類別標題中`as`關鍵字所定義的自我識別碼, 而且這些成員的所有用法都是以類別的自我識別碼限定, 非靜態系結就可以存取類別的成員。</span><span class="sxs-lookup"><span data-stu-id="172db-113">Non-static `do` bindings can access members of the class as long as the class has a self identifier that is defined by an `as` keyword in the class heading, and as long as all uses of those members are qualified with the self identifier for the class.</span></span>

<span data-ttu-id="172db-114">由於`let`系結會初始化類別的私用欄位, 因此通常必須確保成員如預期般運作, 而且`do`系結通常會在`let`系結之後放置, 讓`do`系結中的程式碼可以使用完全初始化的物件來執行。</span><span class="sxs-lookup"><span data-stu-id="172db-114">Because `let` bindings initialize the private fields of a class, which is often necessary to guarantee that members behave as expected, `do` bindings are usually put after `let` bindings so that code in the `do` binding can execute with a fully initialized object.</span></span> <span data-ttu-id="172db-115">如果您的程式碼在初始化完成之前嘗試使用成員, 則會引發 InvalidOperationException。</span><span class="sxs-lookup"><span data-stu-id="172db-115">If your code attempts to use a member before the initialization is complete, an InvalidOperationException is raised.</span></span>

<span data-ttu-id="172db-116">靜態`do`系結可以參考封閉式類別的靜態成員或欄位, 但不能參考實例成員或欄位。</span><span class="sxs-lookup"><span data-stu-id="172db-116">Static `do` bindings can reference static members or fields of the enclosing class but not instance members or fields.</span></span> <span data-ttu-id="172db-117">靜態`do`系結會成為類別靜態初始化運算式的一部分, 保證會在第一次使用類別之前執行。</span><span class="sxs-lookup"><span data-stu-id="172db-117">Static `do` bindings become part of the static initializer for the class, which is guaranteed to execute before the class is first used.</span></span>

<span data-ttu-id="172db-118">類型中的`do`系結會忽略屬性。</span><span class="sxs-lookup"><span data-stu-id="172db-118">Attributes are ignored for `do` bindings in types.</span></span> <span data-ttu-id="172db-119">如果在系結中`do`執行的程式碼需要屬性, 則必須將它套用至主要的函式。</span><span class="sxs-lookup"><span data-stu-id="172db-119">If an attribute is required for code that executes in a `do` binding, it must be applied to the primary constructor.</span></span>

<span data-ttu-id="172db-120">在下列程式碼中, 類別具有靜態`do`系結和非靜態`do`系結。</span><span class="sxs-lookup"><span data-stu-id="172db-120">In the following code, a class has a static `do` binding and a non-static `do` binding.</span></span> <span data-ttu-id="172db-121">物件有一個具有兩個參數 ( `a`和`b`) 的函式, 以及兩個私用欄位`let`定義于類別的系結中。</span><span class="sxs-lookup"><span data-stu-id="172db-121">The object has a constructor that has two parameters, `a` and `b`, and two private fields are defined in the `let` bindings for the class.</span></span> <span data-ttu-id="172db-122">也會定義兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="172db-122">Two properties are also defined.</span></span> <span data-ttu-id="172db-123">這些全都位於 [非靜態`do`系結] 區段的 [範圍] 中, 如列印所有這些值的程式程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="172db-123">All of these are in scope in the non-static `do` bindings section, as is illustrated by the line that prints all those values.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3101.fs)]

<span data-ttu-id="172db-124">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="172db-124">The output is as follows.</span></span>

```console
Initializing MyType.
Initializing object 1 2 2 4 8 16
```

## <a name="see-also"></a><span data-ttu-id="172db-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="172db-125">See also</span></span>

- [<span data-ttu-id="172db-126">成員</span><span class="sxs-lookup"><span data-stu-id="172db-126">Members</span></span>](index.md)
- [<span data-ttu-id="172db-127">類別</span><span class="sxs-lookup"><span data-stu-id="172db-127">Classes</span></span>](../classes.md)
- [<span data-ttu-id="172db-128">建構函式</span><span class="sxs-lookup"><span data-stu-id="172db-128">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="172db-129">類別中的 `let` 繫結</span><span class="sxs-lookup"><span data-stu-id="172db-129">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
- [<span data-ttu-id="172db-130">`do`關係</span><span class="sxs-lookup"><span data-stu-id="172db-130">`do` Bindings</span></span>](../functions/do-Bindings.md)
