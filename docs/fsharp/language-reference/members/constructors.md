---
title: 建構函式
description: 了解如何定義和使用的建構函式F#建立和初始化類別和結構的物件。
ms.date: 05/16/2016
ms.openlocfilehash: 34989e2877b29f6f9fe1f6cc05e3fd7c90a1306a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903964"
---
# <a name="constructors"></a><span data-ttu-id="457ad-103">建構函式</span><span class="sxs-lookup"><span data-stu-id="457ad-103">Constructors</span></span>

<span data-ttu-id="457ad-104">本主題描述如何定義和使用建構函式來建立和初始化類別和結構的物件。</span><span class="sxs-lookup"><span data-stu-id="457ad-104">This topic describes how to define and use constructors to create and initialize class and structure objects.</span></span>

## <a name="construction-of-class-objects"></a><span data-ttu-id="457ad-105">類別物件的建構</span><span class="sxs-lookup"><span data-stu-id="457ad-105">Construction of Class Objects</span></span>

<span data-ttu-id="457ad-106">類別類型的物件具有建構函式。</span><span class="sxs-lookup"><span data-stu-id="457ad-106">Objects of class types have constructors.</span></span> <span data-ttu-id="457ad-107">有兩種類型的建構函式。</span><span class="sxs-lookup"><span data-stu-id="457ad-107">There are two kinds of constructors.</span></span> <span data-ttu-id="457ad-108">其中一個是主要的建構函式，其參數的型別名稱之後括號括住。</span><span class="sxs-lookup"><span data-stu-id="457ad-108">One is the primary constructor, whose parameters appear in parentheses just after the type name.</span></span> <span data-ttu-id="457ad-109">您可以指定其他的選擇性額外的建構函式使用`new`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="457ad-109">You specify other, optional additional constructors by using the `new` keyword.</span></span> <span data-ttu-id="457ad-110">任何這類其他建構函式必須呼叫主要建構函式。</span><span class="sxs-lookup"><span data-stu-id="457ad-110">Any such additional constructors must call the primary constructor.</span></span>

<span data-ttu-id="457ad-111">主要的建構函式包含`let`和`do`繫結，都會出現在類別定義的開頭。</span><span class="sxs-lookup"><span data-stu-id="457ad-111">The primary constructor contains `let` and `do` bindings that appear at the start of the class definition.</span></span> <span data-ttu-id="457ad-112">A`let`繫結會宣告私用欄位和方法的類別;`do`繫結會執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="457ad-112">A `let` binding declares private fields and methods of the class; a `do` binding executes code.</span></span> <span data-ttu-id="457ad-113">如需詳細資訊`let`繫結的類別建構函式，請參閱[`let`類別中的繫結](let-bindings-in-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="457ad-113">For more information about `let` bindings in class constructors, see [`let` Bindings in Classes](let-bindings-in-classes.md).</span></span> <span data-ttu-id="457ad-114">如需詳細資訊`do`繫結的建構函式，請參閱[`do`類別中的繫結](do-bindings-in-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="457ad-114">For more information about `do` bindings in constructors, see [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

<span data-ttu-id="457ad-115">不論您想要呼叫的建構函式是主要的建構函式或其他建構函式，您可以建立物件，使用`new`運算式包含或不含選擇性`new`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="457ad-115">Regardless of whether the constructor you want to call is a primary constructor or an additional constructor, you can create objects by using a `new` expression, with or without the optional `new` keyword.</span></span> <span data-ttu-id="457ad-116">初始化您的物件，以及建構函式引數，藉由列出的順序中的引數，和以逗號分隔並括在括號內，或使用括號括住的具名引數和值。</span><span class="sxs-lookup"><span data-stu-id="457ad-116">You initialize your objects together with constructor arguments, either by listing the arguments in order and separated by commas and enclosed in parentheses, or by using named arguments and values in parentheses.</span></span> <span data-ttu-id="457ad-117">您也可以設定屬性的物件上之物件的建構期間所使用的屬性名稱，並指派值，就如同您使用名為建構函式引數。</span><span class="sxs-lookup"><span data-stu-id="457ad-117">You can also set properties on an object during the construction of the object by using the property names and assigning values just as you use named constructor arguments.</span></span>

<span data-ttu-id="457ad-118">下列程式碼說明具有建構函式和建立物件的各種方法的類別。</span><span class="sxs-lookup"><span data-stu-id="457ad-118">The following code illustrates a class that has a constructor and various ways of creating objects.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

<span data-ttu-id="457ad-119">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="457ad-119">The output is as follows.</span></span>

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a><span data-ttu-id="457ad-120">建構的結構</span><span class="sxs-lookup"><span data-stu-id="457ad-120">Construction of Structures</span></span>

<span data-ttu-id="457ad-121">結構遵循所有規則的類別。</span><span class="sxs-lookup"><span data-stu-id="457ad-121">Structures follow all the rules of classes.</span></span> <span data-ttu-id="457ad-122">因此，您可以擁有的主要建構函式，而且您可以使用，以提供額外的建構函式`new`。</span><span class="sxs-lookup"><span data-stu-id="457ad-122">Therefore, you can have a primary constructor, and you can provide additional constructors by using `new`.</span></span> <span data-ttu-id="457ad-123">不過，還有結構和類別之間的一個重要差異： 結構可以具有預設建構函式 （也就是一個不含引數），即使沒有主要建構函式定義。</span><span class="sxs-lookup"><span data-stu-id="457ad-123">However, there is one important difference between structures and classes: structures can have a default constructor (that is, one with no arguments) even if no primary constructor is defined.</span></span> <span data-ttu-id="457ad-124">預設建構函式會初始化該類型，通常是零或其相等的預設值的所有欄位。</span><span class="sxs-lookup"><span data-stu-id="457ad-124">The default constructor initializes all the fields to the default value for that type, usually zero or its equivalent.</span></span> <span data-ttu-id="457ad-125">您為結構定義任何建構函式必須具有至少一個引數，如此他們不會衝突的預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="457ad-125">Any constructors that you define for structures must have at least one argument so that they do not conflict with the default constructor.</span></span>

<span data-ttu-id="457ad-126">此外，結構通常會有使用所建立的欄位`val`關鍵字; 類別也可以有這些欄位。</span><span class="sxs-lookup"><span data-stu-id="457ad-126">Also, structures often have fields that are created by using the `val` keyword; classes can also have these fields.</span></span> <span data-ttu-id="457ad-127">結構和類別具有定義所使用的欄位`val`關鍵字也可以初始化其他建構函式中使用記錄的運算式，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="457ad-127">Structures and classes that have fields defined by using the `val` keyword can also be initialized in additional constructors by using record expressions, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

<span data-ttu-id="457ad-128">如需詳細資訊，請參閱[明確欄位：`val`關鍵字](explicit-fields-the-val-keyword.md)。</span><span class="sxs-lookup"><span data-stu-id="457ad-128">For more information, see [Explicit Fields: The `val` Keyword](explicit-fields-the-val-keyword.md).</span></span>

## <a name="executing-side-effects-in-constructors"></a><span data-ttu-id="457ad-129">建構函式中執行的副作用</span><span class="sxs-lookup"><span data-stu-id="457ad-129">Executing Side Effects in Constructors</span></span>

<span data-ttu-id="457ad-130">在類別中的主要建構函式可以執行中的程式碼`do`繫結。</span><span class="sxs-lookup"><span data-stu-id="457ad-130">A primary constructor in a class can execute code in a `do` binding.</span></span> <span data-ttu-id="457ad-131">不過，如果您有什麼不執行程式碼中的其他建構函式，`do`繫結嗎？</span><span class="sxs-lookup"><span data-stu-id="457ad-131">However, what if you have to execute code in an additional constructor, without a `do` binding?</span></span> <span data-ttu-id="457ad-132">若要這樣做，您使用`then`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="457ad-132">To do this, you use the `then` keyword.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

<span data-ttu-id="457ad-133">仍然執行主要建構函式的副作用。</span><span class="sxs-lookup"><span data-stu-id="457ad-133">The side effects of the primary constructor still execute.</span></span> <span data-ttu-id="457ad-134">因此，輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="457ad-134">Therefore, the output is as follows.</span></span>

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a><span data-ttu-id="457ad-135">建構函式中的自我識別項</span><span class="sxs-lookup"><span data-stu-id="457ad-135">Self Identifiers in Constructors</span></span>

<span data-ttu-id="457ad-136">在其他成員，您可以提供中的每個成員定義的目前物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="457ad-136">In other members, you provide a name for the current object in the definition of each member.</span></span> <span data-ttu-id="457ad-137">您也可以使類別定義的第一行上自我識別項，利用`as`緊接的建構函式參數的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="457ad-137">You can also put the self identifier on the first line of the class definition by using the `as` keyword immediately following the constructor parameters.</span></span> <span data-ttu-id="457ad-138">下列範例說明這種語法。</span><span class="sxs-lookup"><span data-stu-id="457ad-138">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

<span data-ttu-id="457ad-139">在其他建構函式，您也可以定義本身的識別項放`as`子句後面的建構函式參數。</span><span class="sxs-lookup"><span data-stu-id="457ad-139">In additional constructors, you can also define a self identifier by putting the `as` clause right after the constructor parameters.</span></span> <span data-ttu-id="457ad-140">下列範例說明這種語法。</span><span class="sxs-lookup"><span data-stu-id="457ad-140">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

<span data-ttu-id="457ad-141">當您嘗試使用物件，才能完整定義時，可能會發生問題。</span><span class="sxs-lookup"><span data-stu-id="457ad-141">Problems can occur when you try to use an object before it is fully defined.</span></span> <span data-ttu-id="457ad-142">因此，自我識別項的用法可能會導致編譯器發出警告，並插入額外的檢查，以確保該物件初始化之前，不會存取物件的成員。</span><span class="sxs-lookup"><span data-stu-id="457ad-142">Therefore, uses of the self identifier can cause the compiler to emit a warning and insert additional checks to ensure the members of an object are not accessed before the object is initialized.</span></span> <span data-ttu-id="457ad-143">您應該只使用中的自我識別項`do`繫結的主要建構函式，或之後`then`其他建構函式中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="457ad-143">You should only use the self identifier in the `do` bindings of the primary constructor, or after the `then` keyword in additional constructors.</span></span>

<span data-ttu-id="457ad-144">自我識別項名稱不一定要`this`。</span><span class="sxs-lookup"><span data-stu-id="457ad-144">The name of the self identifier does not have to be `this`.</span></span> <span data-ttu-id="457ad-145">它可以是任何有效的識別項。</span><span class="sxs-lookup"><span data-stu-id="457ad-145">It can be any valid identifier.</span></span>

## <a name="assigning-values-to-properties-at-initialization"></a><span data-ttu-id="457ad-146">將值指派給在初始化屬性</span><span class="sxs-lookup"><span data-stu-id="457ad-146">Assigning Values to Properties at Initialization</span></span>

<span data-ttu-id="457ad-147">您也可以附加一份格式的指派至類別物件初始化程式碼中的屬性指派值`property = value`建構函式的引數清單。</span><span class="sxs-lookup"><span data-stu-id="457ad-147">You can assign values to the properties of a class object in the initialization code by appending a list of assignments of the form `property = value` to the argument list for a constructor.</span></span> <span data-ttu-id="457ad-148">這會顯示在以下程式碼範例中。</span><span class="sxs-lookup"><span data-stu-id="457ad-148">This is shown in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="457ad-149">下列版本的先前的程式碼說明一般引數、 選擇性引數和一個建構函式呼叫中的屬性設定的組合。</span><span class="sxs-lookup"><span data-stu-id="457ad-149">The following version of the previous code illustrates the combination of ordinary arguments, optional arguments, and property settings in one constructor call.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a><span data-ttu-id="457ad-150">繼承的類別的建構函式</span><span class="sxs-lookup"><span data-stu-id="457ad-150">Constructors in inherited class</span></span>

<span data-ttu-id="457ad-151">繼承自基底類別具有建構函式時，您必須在繼承子句中指定其引數。</span><span class="sxs-lookup"><span data-stu-id="457ad-151">When inheriting from a base class that has a constructor, you must specify its arguments in the inherit clause.</span></span> <span data-ttu-id="457ad-152">如需詳細資訊，請參閱 <<c0> [ 建構函式和繼承](../inheritance.md#constructors-and-inheritance)。</span><span class="sxs-lookup"><span data-stu-id="457ad-152">For more information, see [Constructors and inheritance](../inheritance.md#constructors-and-inheritance).</span></span>

## <a name="static-constructors-or-type-constructors"></a><span data-ttu-id="457ad-153">靜態建構函式或類型建構函式</span><span class="sxs-lookup"><span data-stu-id="457ad-153">Static Constructors or Type Constructors</span></span>

<span data-ttu-id="457ad-154">除了指定用於建立物件，靜態程式碼`let`和`do`繫結可以撰寫在型別第一次用來執行類型層級的初始設定之前，先執行的類別類型。</span><span class="sxs-lookup"><span data-stu-id="457ad-154">In addition to specifying code for creating objects, static `let` and `do` bindings can be authored in class types that execute before the type is first used to perform initialization at the type level.</span></span> <span data-ttu-id="457ad-155">如需詳細資訊，請參閱 < [ `let`類別中的繫結](let-bindings-in-classes.md)並[`do`類別中的繫結](do-bindings-in-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="457ad-155">For more information, see [`let` Bindings in Classes](let-bindings-in-classes.md) and [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="457ad-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="457ad-156">See also</span></span>

- [<span data-ttu-id="457ad-157">成員</span><span class="sxs-lookup"><span data-stu-id="457ad-157">Members</span></span>](index.md)