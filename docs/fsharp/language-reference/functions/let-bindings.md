---
title: let 繫結 (F#)
description: "了解如何使用 F # 'let' 繫結，其值或函式使用關聯識別項。"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 2abc4e05f9f2977501f01f745062e2e7cd611f68
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="let-bindings"></a><span data-ttu-id="07626-103">let 繫結</span><span class="sxs-lookup"><span data-stu-id="07626-103">let Bindings</span></span>

<span data-ttu-id="07626-104">A*繫結*關聯的值或函式的識別項。</span><span class="sxs-lookup"><span data-stu-id="07626-104">A *binding* associates an identifier with a value or function.</span></span> <span data-ttu-id="07626-105">您使用`let`關鍵字來繫結至值或函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="07626-105">You use the `let` keyword to bind a name to a value or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="07626-106">語法</span><span class="sxs-lookup"><span data-stu-id="07626-106">Syntax</span></span>

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a><span data-ttu-id="07626-107">備註</span><span class="sxs-lookup"><span data-stu-id="07626-107">Remarks</span></span>

<span data-ttu-id="07626-108">`let`關鍵字用於繫結來定義值或一或多個名稱的函式值的運算式。</span><span class="sxs-lookup"><span data-stu-id="07626-108">The `let` keyword is used in binding expressions to define values or function values for one or more names.</span></span> <span data-ttu-id="07626-109">最簡單的形式`let`運算式繫結名稱為簡單的值，如下所示。</span><span class="sxs-lookup"><span data-stu-id="07626-109">The simplest form of the `let` expression binds a name to a simple value, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

<span data-ttu-id="07626-110">如果您使用新的一行分隔識別碼中的運算式，您必須縮排每一行的運算式，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="07626-110">If you separate the expression from the identifier by using a new line, you must indent each line of the expression, as in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

<span data-ttu-id="07626-111">而不是只有名稱，您可以指定包含名稱的模式，例如，一個 tuple，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="07626-111">Instead of just a name, a pattern that contains names can be specified, for example, a tuple, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

<span data-ttu-id="07626-112">*主體運算式*是該名稱使用的運算式。</span><span class="sxs-lookup"><span data-stu-id="07626-112">The *body-expression* is the expression in which the names are used.</span></span> <span data-ttu-id="07626-113">本文顯示此運算式的那一行，並將其與中的第一個字元完全縮排成線條向上`let`關鍵字：</span><span class="sxs-lookup"><span data-stu-id="07626-113">The body expression appears on its own line, indented to line up exactly with the first character in the `let` keyword:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

<span data-ttu-id="07626-114">A`let`繫結可以出現在模組層級定義中的類別類型，或在本機的範圍，例如內嵌函式定義。</span><span class="sxs-lookup"><span data-stu-id="07626-114">A `let` binding can appear at the module level, in the definition of a class type, or in local scopes, such as in a function definition.</span></span> <span data-ttu-id="07626-115">A`let`在最上層的類別類型或模組中的繫結不需要具有主體運算式，但其他範圍層級中，主體必須是運算式。</span><span class="sxs-lookup"><span data-stu-id="07626-115">A `let` binding at the top level in a module or in a class type does not need to have a body expression, but at other scope levels, the body expression is required.</span></span> <span data-ttu-id="07626-116">繫結的名稱會使用點定義，但不是在之前的任何時間點之後`let`出現繫結，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="07626-116">The bound names are usable after the point of definition, but not at any point before the `let` binding appears, as is illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]
    
## <a name="function-bindings"></a><span data-ttu-id="07626-117">函式繫結</span><span class="sxs-lookup"><span data-stu-id="07626-117">Function Bindings</span></span>

<span data-ttu-id="07626-118">函式繫結會遵循值的繫結規則，不同之處在於函式繫結包含函式名稱和參數，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="07626-118">Function bindings follow the rules for value bindings, except that function bindings include the function name and the parameters, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

<span data-ttu-id="07626-119">一般情況下，參數為模式，例如 tuple 模式：</span><span class="sxs-lookup"><span data-stu-id="07626-119">In general, parameters are patterns, such as a tuple pattern:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

<span data-ttu-id="07626-120">A`let`繫結運算式評估為最後一個運算式的值。</span><span class="sxs-lookup"><span data-stu-id="07626-120">A `let` binding expression evaluates to the value of the last expression.</span></span> <span data-ttu-id="07626-121">因此，在下列程式碼範例中，值`result`計算從`100 * function3 (1, 2)`，這會評估為`300`。</span><span class="sxs-lookup"><span data-stu-id="07626-121">Therefore, in the following code example, the value of `result` is computed from `100 * function3 (1, 2)`, which evaluates to `300`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

<span data-ttu-id="07626-122">如需詳細資訊，請參閱[函式](index.md)。</span><span class="sxs-lookup"><span data-stu-id="07626-122">For more information, see [Functions](index.md).</span></span>

## <a name="type-annotations"></a><span data-ttu-id="07626-123">型別附註</span><span class="sxs-lookup"><span data-stu-id="07626-123">Type Annotations</span></span>

<span data-ttu-id="07626-124">您可以指定類型的參數包含冒號 （:） 後面接著類型名稱，所有括在括號中。</span><span class="sxs-lookup"><span data-stu-id="07626-124">You can specify types for parameters by including a colon (:) followed by a type name, all enclosed in parentheses.</span></span> <span data-ttu-id="07626-125">您也可以在最後一個參數後附加冒號和型別，以指定傳回值的類型。</span><span class="sxs-lookup"><span data-stu-id="07626-125">You can also specify the type of the return value by appending the colon and type after the last parameter.</span></span> <span data-ttu-id="07626-126">完整的類型註釋`function1`，以做為參數類型的整數，將會如下。</span><span class="sxs-lookup"><span data-stu-id="07626-126">The full type annotations for `function1`, with integers as the parameter types, would be as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

<span data-ttu-id="07626-127">沒有明確的型別參數時，型別推斷會判斷函式的參數型別。</span><span class="sxs-lookup"><span data-stu-id="07626-127">When there are no explicit type parameters, type inference is used to determine the types of parameters of functions.</span></span> <span data-ttu-id="07626-128">這可能包括自動一般化 設為泛型參數的類型。</span><span class="sxs-lookup"><span data-stu-id="07626-128">This can include automatically generalizing the type of a parameter to be generic.</span></span>

<span data-ttu-id="07626-129">如需詳細資訊，請參閱[自動一般化](../generics/automatic-generalization.md)和[型別推斷](../type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="07626-129">For more information, see [Automatic Generalization](../generics/automatic-generalization.md) and [Type Inference](../type-inference.md).</span></span>

## <a name="let-bindings-in-classes"></a><span data-ttu-id="07626-130">類別中的 let 繫結</span><span class="sxs-lookup"><span data-stu-id="07626-130">let Bindings in Classes</span></span>

<span data-ttu-id="07626-131">A`let`繫結可以出現在類別類型，但不是在結構或記錄類型。</span><span class="sxs-lookup"><span data-stu-id="07626-131">A `let` binding can appear in a class type but not in a structure or record type.</span></span> <span data-ttu-id="07626-132">若要使用的類別類型中的繫結可讓，類別必須具有主要建構函式。</span><span class="sxs-lookup"><span data-stu-id="07626-132">To use a let binding in a class type, the class must have a primary constructor.</span></span> <span data-ttu-id="07626-133">建構函式參數必須出現在類別定義中的類型名稱之後。</span><span class="sxs-lookup"><span data-stu-id="07626-133">Constructor parameters must appear after the type name in the class definition.</span></span> <span data-ttu-id="07626-134">A`let`類別型別中的繫結定義私用欄位和成員，該類別類型，並搭配`do`類型中的繫結表單類型的主要建構函式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="07626-134">A `let` binding in a class type defines private fields and members for that class type and, together with `do` bindings in the type, forms the code for the primary constructor for the type.</span></span> <span data-ttu-id="07626-135">下列程式碼範例顯示類別`MyClass`與私用欄位`field1`和`field2`。</span><span class="sxs-lookup"><span data-stu-id="07626-135">The following code examples show a class `MyClass` with private fields `field1` and `field2`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

<span data-ttu-id="07626-136">範圍`field1`和`field2`僅限於在宣告的型別。</span><span class="sxs-lookup"><span data-stu-id="07626-136">The scopes of `field1` and `field2` are limited to the type in which they are declared.</span></span> <span data-ttu-id="07626-137">如需詳細資訊，請參閱[`let`類別中的繫結](../members/let-bindings-in-classes.md)和[類別](../classes.md)。</span><span class="sxs-lookup"><span data-stu-id="07626-137">For more information, see [`let` Bindings in Classes](../members/let-bindings-in-classes.md) and [Classes](../classes.md).</span></span>

## <a name="type-parameters-in-let-bindings"></a><span data-ttu-id="07626-138">型別參數中的 let 繫結</span><span class="sxs-lookup"><span data-stu-id="07626-138">Type Parameters in let Bindings</span></span>

<span data-ttu-id="07626-139">A`let`繫結，在模組層級，在類型中，或計算運算式中可以有明確的型別參數。</span><span class="sxs-lookup"><span data-stu-id="07626-139">A `let` binding at the module level, in a type, or in a computation expression can have explicit type parameters.</span></span> <span data-ttu-id="07626-140">中的繫結運算式，例如函式定義內可讓不能有型別參數。</span><span class="sxs-lookup"><span data-stu-id="07626-140">A let binding in an expression, such as within a function definition, cannot have type parameters.</span></span> <span data-ttu-id="07626-141">如需詳細資訊，請參閱[泛型](../generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="07626-141">For more information, see [Generics](../generics/index.md).</span></span>

## <a name="attributes-on-let-bindings"></a><span data-ttu-id="07626-142">上的屬性 let 繫結</span><span class="sxs-lookup"><span data-stu-id="07626-142">Attributes on let Bindings</span></span>

<span data-ttu-id="07626-143">屬性可以套用至最上層`let`繫結，在模組中，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="07626-143">Attributes can be applied to top-level `let` bindings in a module, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]
    
## <a name="scope-and-accessibility-of-let-bindings"></a><span data-ttu-id="07626-144">領域和存取範圍 Let 繫結</span><span class="sxs-lookup"><span data-stu-id="07626-144">Scope and Accessibility of Let Bindings</span></span>

<span data-ttu-id="07626-145">Let 繫結所宣告的實體的範圍僅限於包含的部分繫結出現後 （例如函式、 模組、 檔案或類別） 的範圍。</span><span class="sxs-lookup"><span data-stu-id="07626-145">The scope of an entity declared with a let binding is limited to the portion of the containing scope (such as a function, module, file or class) after the binding appears.</span></span> <span data-ttu-id="07626-146">因此，它可說是 let 繫結引進一個名稱，進入範圍內。</span><span class="sxs-lookup"><span data-stu-id="07626-146">Therefore, it can be said that a let binding introduces a name into a scope.</span></span> <span data-ttu-id="07626-147">在模組中，讓繫結值或函式是模組的用戶端可以存取，只要模組可供存取，因為模組中的 let 繫結會編譯成模組的公用函式。</span><span class="sxs-lookup"><span data-stu-id="07626-147">In a module, a let-bound value or function is accessible to clients of a module as long as the module is accessible, since the let bindings in a module are compiled into public functions of the module.</span></span> <span data-ttu-id="07626-148">相反地，類別中的 let 繫結是私用類別。</span><span class="sxs-lookup"><span data-stu-id="07626-148">By contrast, let bindings in a class are private to the class.</span></span>

<span data-ttu-id="07626-149">一般來說，模組中的函式必須使用用戶端程式碼時的模組名稱所限定。</span><span class="sxs-lookup"><span data-stu-id="07626-149">Normally, functions in modules must be qualified by the name of the module when used by client code.</span></span> <span data-ttu-id="07626-150">例如，如果模組`Module1`有函式`function1`，使用者就必須指定`Module1.function1`到參考的函式。</span><span class="sxs-lookup"><span data-stu-id="07626-150">For example, if a module `Module1` has a function `function1`, users would specify `Module1.function1` to refer to the function.</span></span>

<span data-ttu-id="07626-151">模組的使用者可以使用匯入宣告而不以模組名稱所限定，使該模組內的函式可供使用。</span><span class="sxs-lookup"><span data-stu-id="07626-151">Users of a module may use an import declaration to make the functions within that module available for use without being qualified by the module name.</span></span> <span data-ttu-id="07626-152">在上述範例中，模組的使用者可以在此情況下開啟模組使用匯入宣告開啟`Module1`，而且此後參考`function1`直接。</span><span class="sxs-lookup"><span data-stu-id="07626-152">In the example just mentioned, users of the module can in that case open the module by using the import declaration open `Module1` and thereafter refer to `function1` directly.</span></span>

```fsharp
module Module1 =
    let function1 x = x + 1.0

module Module2 =
    let function2 x =
        Module1.function1 x

open Module1

let function3 x =
    function1 x
```

<span data-ttu-id="07626-153">某些模組具有屬性[RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15)，這表示它們公開的函式必須以模組名稱加以限定。</span><span class="sxs-lookup"><span data-stu-id="07626-153">Some modules have the attribute [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), which means that the functions that they expose must be qualified with the name of the module.</span></span> <span data-ttu-id="07626-154">例如，F # 清單模組有這個屬性。</span><span class="sxs-lookup"><span data-stu-id="07626-154">For example, the F# List module has this attribute.</span></span>

<span data-ttu-id="07626-155">如需有關模組和存取控制的詳細資訊，請參閱[模組](../modules.md)和[存取控制](../access-control.md)。</span><span class="sxs-lookup"><span data-stu-id="07626-155">For more information on modules and access control, see [Modules](../modules.md) and [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="07626-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07626-156">See Also</span></span>

[<span data-ttu-id="07626-157">函式</span><span class="sxs-lookup"><span data-stu-id="07626-157">Functions</span></span>](index.md)

[<span data-ttu-id="07626-158">類別中的 `let` 繫結</span><span class="sxs-lookup"><span data-stu-id="07626-158">`let` Bindings in Classes</span></span>](../members/let-bindings-in-classes.md)
