---
title: 建構函式
description: '瞭解如何在 F # 中定義和使用函數，以建立和初始化類別和結構物件。'
ms.date: 05/16/2016
ms.openlocfilehash: be8fc3f1d82a9a7c778a6d094139f14150a28813
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303435"
---
# <a name="constructors"></a><span data-ttu-id="7370c-103">建構函式</span><span class="sxs-lookup"><span data-stu-id="7370c-103">Constructors</span></span>

<span data-ttu-id="7370c-104">本文說明如何定義和使用函式來建立和初始化類別和結構物件。</span><span class="sxs-lookup"><span data-stu-id="7370c-104">This article describes how to define and use constructors to create and initialize class and structure objects.</span></span>

## <a name="construction-of-class-objects"></a><span data-ttu-id="7370c-105">類別物件的結構</span><span class="sxs-lookup"><span data-stu-id="7370c-105">Construction of class objects</span></span>

<span data-ttu-id="7370c-106">類別類型的物件具有函數。</span><span class="sxs-lookup"><span data-stu-id="7370c-106">Objects of class types have constructors.</span></span> <span data-ttu-id="7370c-107">有兩種類型的函數。</span><span class="sxs-lookup"><span data-stu-id="7370c-107">There are two kinds of constructors.</span></span> <span data-ttu-id="7370c-108">其中一個是主要的函式，其參數會出現在型別名稱後面的括弧中。</span><span class="sxs-lookup"><span data-stu-id="7370c-108">One is the primary constructor, whose parameters appear in parentheses just after the type name.</span></span> <span data-ttu-id="7370c-109">您可以使用關鍵字來指定其他選擇性的其他函式 `new` 。</span><span class="sxs-lookup"><span data-stu-id="7370c-109">You specify other, optional additional constructors by using the `new` keyword.</span></span> <span data-ttu-id="7370c-110">任何這類額外的函式都必須呼叫主要的函式。</span><span class="sxs-lookup"><span data-stu-id="7370c-110">Any such additional constructors must call the primary constructor.</span></span>

<span data-ttu-id="7370c-111">主要的函式包含和系結 `let` `do` ，它會出現在類別定義的開頭。</span><span class="sxs-lookup"><span data-stu-id="7370c-111">The primary constructor contains `let` and `do` bindings that appear at the start of the class definition.</span></span> <span data-ttu-id="7370c-112">系結會宣告 `let` 類別的私用欄位和方法，系結會 `do` 執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="7370c-112">A `let` binding declares private fields and methods of the class; a `do` binding executes code.</span></span> <span data-ttu-id="7370c-113">如需類別函式中系結的詳細資訊 `let` ，請參閱[ `let` 類別中的](let-bindings-in-classes.md)系結。</span><span class="sxs-lookup"><span data-stu-id="7370c-113">For more information about `let` bindings in class constructors, see [`let` Bindings in Classes](let-bindings-in-classes.md).</span></span> <span data-ttu-id="7370c-114">如需有關在函式中系結的詳細資訊 `do` ，請參閱[ `do` 類別中的](do-bindings-in-classes.md)系結。</span><span class="sxs-lookup"><span data-stu-id="7370c-114">For more information about `do` bindings in constructors, see [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

<span data-ttu-id="7370c-115">不論您想要呼叫的是主要的函式或其他的函數，您都可以使用運算式來建立物件 `new` ，並搭配或不搭配選擇性 `new` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="7370c-115">Regardless of whether the constructor you want to call is a primary constructor or an additional constructor, you can create objects by using a `new` expression, with or without the optional `new` keyword.</span></span> <span data-ttu-id="7370c-116">您可以使用函式引數來初始化您的物件，方法是依序列出引數，並以逗號分隔並括在括弧中，或使用括弧中的具名引數和值。</span><span class="sxs-lookup"><span data-stu-id="7370c-116">You initialize your objects together with constructor arguments, either by listing the arguments in order and separated by commas and enclosed in parentheses, or by using named arguments and values in parentheses.</span></span> <span data-ttu-id="7370c-117">您也可以在物件的結構中，使用屬性名稱和指派值來設定物件的屬性，就如同使用命名的函式引數一樣。</span><span class="sxs-lookup"><span data-stu-id="7370c-117">You can also set properties on an object during the construction of the object by using the property names and assigning values just as you use named constructor arguments.</span></span>

<span data-ttu-id="7370c-118">下列程式碼說明具有函式和各種建立物件方法的類別：</span><span class="sxs-lookup"><span data-stu-id="7370c-118">The following code illustrates a class that has a constructor and various ways of creating objects:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

<span data-ttu-id="7370c-119">輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="7370c-119">The output is as follows:</span></span>

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a><span data-ttu-id="7370c-120">結構結構</span><span class="sxs-lookup"><span data-stu-id="7370c-120">Construction of structures</span></span>

<span data-ttu-id="7370c-121">結構會遵循類別的所有規則。</span><span class="sxs-lookup"><span data-stu-id="7370c-121">Structures follow all the rules of classes.</span></span> <span data-ttu-id="7370c-122">因此，您可以擁有主要的函式，也可以使用來提供其他的函式 `new` 。</span><span class="sxs-lookup"><span data-stu-id="7370c-122">Therefore, you can have a primary constructor, and you can provide additional constructors by using `new`.</span></span> <span data-ttu-id="7370c-123">不過，結構和類別之間有一個重要的差異：結構可以有無參數的函式（也就是沒有引數的函式），即使未定義主要的函式。</span><span class="sxs-lookup"><span data-stu-id="7370c-123">However, there is one important difference between structures and classes: structures can have a parameterless constructor (that is, one with no arguments) even if no primary constructor is defined.</span></span> <span data-ttu-id="7370c-124">無參數的函式會將所有欄位初始化為該類型的預設值，通常為零或其相等。</span><span class="sxs-lookup"><span data-stu-id="7370c-124">The parameterless constructor initializes all the fields to the default value for that type, usually zero or its equivalent.</span></span> <span data-ttu-id="7370c-125">您為結構定義的任何函式都必須至少有一個引數，才不會與無參數的處理常式衝突。</span><span class="sxs-lookup"><span data-stu-id="7370c-125">Any constructors that you define for structures must have at least one argument so that they do not conflict with the parameterless constructor.</span></span>

<span data-ttu-id="7370c-126">此外，結構通常會有使用關鍵字建立的欄位 `val` ; 類別也可以有這些欄位。</span><span class="sxs-lookup"><span data-stu-id="7370c-126">Also, structures often have fields that are created by using the `val` keyword; classes can also have these fields.</span></span> <span data-ttu-id="7370c-127">具有使用關鍵字定義之欄位的結構和類別 `val` ，也可以使用記錄運算式在其他的函式中進行初始化，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="7370c-127">Structures and classes that have fields defined by using the `val` keyword can also be initialized in additional constructors by using record expressions, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

<span data-ttu-id="7370c-128">如需詳細資訊，請參閱[明確欄位： `val` 關鍵字](explicit-fields-the-val-keyword.md)。</span><span class="sxs-lookup"><span data-stu-id="7370c-128">For more information, see [Explicit Fields: The `val` Keyword](explicit-fields-the-val-keyword.md).</span></span>

## <a name="executing-side-effects-in-constructors"></a><span data-ttu-id="7370c-129">在函式中執行副作用</span><span class="sxs-lookup"><span data-stu-id="7370c-129">Executing side effects in constructors</span></span>

<span data-ttu-id="7370c-130">類別中的主要函式可以在系結中執行程式碼 `do` 。</span><span class="sxs-lookup"><span data-stu-id="7370c-130">A primary constructor in a class can execute code in a `do` binding.</span></span> <span data-ttu-id="7370c-131">不過，如果您必須在不使用系結的其他函式中執行程式碼，該怎麼辦 `do` ？</span><span class="sxs-lookup"><span data-stu-id="7370c-131">However, what if you have to execute code in an additional constructor, without a `do` binding?</span></span> <span data-ttu-id="7370c-132">若要這麼做，請使用 `then` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="7370c-132">To do this, you use the `then` keyword.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

<span data-ttu-id="7370c-133">主要的函式的副作用仍會執行。</span><span class="sxs-lookup"><span data-stu-id="7370c-133">The side effects of the primary constructor still execute.</span></span> <span data-ttu-id="7370c-134">因此，輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="7370c-134">Therefore, the output is as follows:</span></span>

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

<span data-ttu-id="7370c-135">為什麼 `then` 需要而不是另一個的原因 `do` 是， `do` 當關鍵字存在於其他的函式 `unit` 主體中時，關鍵字會有其標準意義來分隔傳回的運算式。</span><span class="sxs-lookup"><span data-stu-id="7370c-135">The reason why `then` is required instead of another `do` is that the `do` keyword has its standard meaning of delimiting a `unit`-returning expression when present in the body of an additional constructor.</span></span> <span data-ttu-id="7370c-136">它在主要的函式內容中只具有特殊意義。</span><span class="sxs-lookup"><span data-stu-id="7370c-136">It only has special meaning in the context of primary constructors.</span></span>

## <a name="self-identifiers-in-constructors"></a><span data-ttu-id="7370c-137">函式中的自我識別碼</span><span class="sxs-lookup"><span data-stu-id="7370c-137">Self identifiers in constructors</span></span>

<span data-ttu-id="7370c-138">在其他成員中，您會在每個成員的定義中提供目前物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="7370c-138">In other members, you provide a name for the current object in the definition of each member.</span></span> <span data-ttu-id="7370c-139">您也可以使用緊接在函式參數後面的關鍵字，將自我識別碼放在類別定義的第一行 `as` 。</span><span class="sxs-lookup"><span data-stu-id="7370c-139">You can also put the self identifier on the first line of the class definition by using the `as` keyword immediately following the constructor parameters.</span></span> <span data-ttu-id="7370c-140">下列範例說明此語法。</span><span class="sxs-lookup"><span data-stu-id="7370c-140">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

<span data-ttu-id="7370c-141">在其他的函式中，您也可以將子句放在函式參數後面，以定義自我識別碼 `as` 。</span><span class="sxs-lookup"><span data-stu-id="7370c-141">In additional constructors, you can also define a self identifier by putting the `as` clause right after the constructor parameters.</span></span> <span data-ttu-id="7370c-142">下列範例說明這個語法：</span><span class="sxs-lookup"><span data-stu-id="7370c-142">The following example illustrates this syntax:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

<span data-ttu-id="7370c-143">當您嘗試在完全定義物件之前使用它，可能會發生問題。</span><span class="sxs-lookup"><span data-stu-id="7370c-143">Problems can occur when you try to use an object before it is fully defined.</span></span> <span data-ttu-id="7370c-144">因此，使用自我識別碼可能會導致編譯器發出警告，並插入額外的檢查，以確保物件的成員在初始化之前不會被存取。</span><span class="sxs-lookup"><span data-stu-id="7370c-144">Therefore, uses of the self identifier can cause the compiler to emit a warning and insert additional checks to ensure the members of an object are not accessed before the object is initialized.</span></span> <span data-ttu-id="7370c-145">您應該只在主要函式的系結中 `do` ，或在其他函式中的關鍵字之後，使用自我識別碼 `then` 。</span><span class="sxs-lookup"><span data-stu-id="7370c-145">You should only use the self identifier in the `do` bindings of the primary constructor, or after the `then` keyword in additional constructors.</span></span>

<span data-ttu-id="7370c-146">本身識別碼的名稱不一定要是 `this` 。</span><span class="sxs-lookup"><span data-stu-id="7370c-146">The name of the self identifier does not have to be `this`.</span></span> <span data-ttu-id="7370c-147">它可以是任何有效的識別碼。</span><span class="sxs-lookup"><span data-stu-id="7370c-147">It can be any valid identifier.</span></span>

## <a name="assigning-values-to-properties-at-initialization"></a><span data-ttu-id="7370c-148">在初始化時將值指派給屬性</span><span class="sxs-lookup"><span data-stu-id="7370c-148">Assigning values to properties at initialization</span></span>

<span data-ttu-id="7370c-149">您可以將表單指派清單附加至函式 `property = value` 的引數清單，以將值指派給初始化程式碼中的類別物件屬性。</span><span class="sxs-lookup"><span data-stu-id="7370c-149">You can assign values to the properties of a class object in the initialization code by appending a list of assignments of the form `property = value` to the argument list for a constructor.</span></span> <span data-ttu-id="7370c-150">作法如下列的程式碼範例所示：</span><span class="sxs-lookup"><span data-stu-id="7370c-150">This is shown in the following code example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="7370c-151">下列版本的舊版程式碼說明了一般引數、選擇性引數和屬性設定在一個函式呼叫中的組合：</span><span class="sxs-lookup"><span data-stu-id="7370c-151">The following version of the previous code illustrates the combination of ordinary arguments, optional arguments, and property settings in one constructor call:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a><span data-ttu-id="7370c-152">繼承類別中的函式</span><span class="sxs-lookup"><span data-stu-id="7370c-152">Constructors in inherited class</span></span>

<span data-ttu-id="7370c-153">從具有函數的基類繼承時，您必須在繼承子句中指定其引數。</span><span class="sxs-lookup"><span data-stu-id="7370c-153">When inheriting from a base class that has a constructor, you must specify its arguments in the inherit clause.</span></span> <span data-ttu-id="7370c-154">如需詳細資訊，請參閱[函數和繼承](../inheritance.md#constructors-and-inheritance)。</span><span class="sxs-lookup"><span data-stu-id="7370c-154">For more information, see [Constructors and inheritance](../inheritance.md#constructors-and-inheritance).</span></span>

## <a name="static-constructors-or-type-constructors"></a><span data-ttu-id="7370c-155">靜態的函式或類型的構造函式</span><span class="sxs-lookup"><span data-stu-id="7370c-155">Static constructors or type constructors</span></span>

<span data-ttu-id="7370c-156">除了指定建立物件的程式碼之外， `let` `do` 也可以在第一次使用類型來執行類型層級的初始化之前，在執行的類別類型中撰寫靜態和系結。</span><span class="sxs-lookup"><span data-stu-id="7370c-156">In addition to specifying code for creating objects, static `let` and `do` bindings can be authored in class types that execute before the type is first used to perform initialization at the type level.</span></span> <span data-ttu-id="7370c-157">如需詳細資訊，請參閱類別中[ `let` 類別](let-bindings-in-classes.md)和系結[ `do` 中](do-bindings-in-classes.md)的系結。</span><span class="sxs-lookup"><span data-stu-id="7370c-157">For more information, see [`let` Bindings in Classes](let-bindings-in-classes.md) and [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7370c-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7370c-158">See also</span></span>

- [<span data-ttu-id="7370c-159">成員</span><span class="sxs-lookup"><span data-stu-id="7370c-159">Members</span></span>](index.md)
