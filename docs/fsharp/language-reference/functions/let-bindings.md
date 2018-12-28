---
title: let 繫結
description: 了解如何使用F#'let' 繫結，其中關聯識別項的值或函式。
ms.date: 05/16/2016
ms.openlocfilehash: 45de82acf6f4423698cd8037266968e023f40dcb
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612669"
---
# <a name="let-bindings"></a><span data-ttu-id="82266-103">let 繫結</span><span class="sxs-lookup"><span data-stu-id="82266-103">let Bindings</span></span>

<span data-ttu-id="82266-104">A*繫結*關聯的值或函式的識別項。</span><span class="sxs-lookup"><span data-stu-id="82266-104">A *binding* associates an identifier with a value or function.</span></span> <span data-ttu-id="82266-105">您使用`let`關鍵字來將名稱繫結至值或函式。</span><span class="sxs-lookup"><span data-stu-id="82266-105">You use the `let` keyword to bind a name to a value or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="82266-106">語法</span><span class="sxs-lookup"><span data-stu-id="82266-106">Syntax</span></span>

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a><span data-ttu-id="82266-107">備註</span><span class="sxs-lookup"><span data-stu-id="82266-107">Remarks</span></span>

<span data-ttu-id="82266-108">`let`關鍵字可用於繫結來定義值或一或多個名稱的函式值的運算式。</span><span class="sxs-lookup"><span data-stu-id="82266-108">The `let` keyword is used in binding expressions to define values or function values for one or more names.</span></span> <span data-ttu-id="82266-109">最簡單的形式`let`運算式繫結名稱為簡單的值，如下所示。</span><span class="sxs-lookup"><span data-stu-id="82266-109">The simplest form of the `let` expression binds a name to a simple value, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

<span data-ttu-id="82266-110">如果您使用新的一行分隔識別碼中的運算式，您必須縮排每一行的運算式，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="82266-110">If you separate the expression from the identifier by using a new line, you must indent each line of the expression, as in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

<span data-ttu-id="82266-111">而非只是名稱，可以指定包含名稱的模式，例如，一個 tuple，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="82266-111">Instead of just a name, a pattern that contains names can be specified, for example, a tuple, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

<span data-ttu-id="82266-112">*主體運算式*是所用的名稱的運算式。</span><span class="sxs-lookup"><span data-stu-id="82266-112">The *body-expression* is the expression in which the names are used.</span></span> <span data-ttu-id="82266-113">主體運算式會出現在它自己的一行，將其完全與中的第一個字元縮排到行向上`let`關鍵字：</span><span class="sxs-lookup"><span data-stu-id="82266-113">The body expression appears on its own line, indented to line up exactly with the first character in the `let` keyword:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

<span data-ttu-id="82266-114">A`let`繫結可以出現在模組層級，定義中的類別類型，或在區域範圍，例如內嵌函式定義。</span><span class="sxs-lookup"><span data-stu-id="82266-114">A `let` binding can appear at the module level, in the definition of a class type, or in local scopes, such as in a function definition.</span></span> <span data-ttu-id="82266-115">A`let`最上層的類別類型或模組中的繫結不需要具有主體運算式，但在其他領域層級中，主體必須是運算式。</span><span class="sxs-lookup"><span data-stu-id="82266-115">A `let` binding at the top level in a module or in a class type does not need to have a body expression, but at other scope levels, the body expression is required.</span></span> <span data-ttu-id="82266-116">繫結的名稱可定義，但不是在任何時間點之前時間點之後`let`繫結隨即出現，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="82266-116">The bound names are usable after the point of definition, but not at any point before the `let` binding appears, as is illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a><span data-ttu-id="82266-117">函式繫結</span><span class="sxs-lookup"><span data-stu-id="82266-117">Function Bindings</span></span>

<span data-ttu-id="82266-118">函式繫結會遵循值繫結的規則，不同之處在於函式繫結包含函式名稱和參數，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="82266-118">Function bindings follow the rules for value bindings, except that function bindings include the function name and the parameters, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

<span data-ttu-id="82266-119">一般情況下，參數為模式，例如 tuple 模式：</span><span class="sxs-lookup"><span data-stu-id="82266-119">In general, parameters are patterns, such as a tuple pattern:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

<span data-ttu-id="82266-120">A`let`繫結運算式評估為最後一個運算式的值。</span><span class="sxs-lookup"><span data-stu-id="82266-120">A `let` binding expression evaluates to the value of the last expression.</span></span> <span data-ttu-id="82266-121">因此，在下列程式碼範例中，值`result`從計算`100 * function3 (1, 2)`，它會評估為`300`。</span><span class="sxs-lookup"><span data-stu-id="82266-121">Therefore, in the following code example, the value of `result` is computed from `100 * function3 (1, 2)`, which evaluates to `300`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

<span data-ttu-id="82266-122">如需詳細資訊，請參閱[函式](index.md)。</span><span class="sxs-lookup"><span data-stu-id="82266-122">For more information, see [Functions](index.md).</span></span>

## <a name="type-annotations"></a><span data-ttu-id="82266-123">型別註釋</span><span class="sxs-lookup"><span data-stu-id="82266-123">Type Annotations</span></span>

<span data-ttu-id="82266-124">包含冒號 （:） 後面接著類型的名稱，為所有以括號顯示，您可以指定參數的類型。</span><span class="sxs-lookup"><span data-stu-id="82266-124">You can specify types for parameters by including a colon (:) followed by a type name, all enclosed in parentheses.</span></span> <span data-ttu-id="82266-125">您也可以在最後一個參數後附加冒號和型別，以指定傳回值的型別。</span><span class="sxs-lookup"><span data-stu-id="82266-125">You can also specify the type of the return value by appending the colon and type after the last parameter.</span></span> <span data-ttu-id="82266-126">完整型別註釋`function1`，做為參數類型的整數，是，如下所示。</span><span class="sxs-lookup"><span data-stu-id="82266-126">The full type annotations for `function1`, with integers as the parameter types, would be as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

<span data-ttu-id="82266-127">沒有明確的類型參數時，型別推斷來判斷函式參數的類型。</span><span class="sxs-lookup"><span data-stu-id="82266-127">When there are no explicit type parameters, type inference is used to determine the types of parameters of functions.</span></span> <span data-ttu-id="82266-128">這可能包括自動一般化成為泛型參數的型別。</span><span class="sxs-lookup"><span data-stu-id="82266-128">This can include automatically generalizing the type of a parameter to be generic.</span></span>

<span data-ttu-id="82266-129">如需詳細資訊，請參閱 <<c0> [ 自動一般化](../generics/automatic-generalization.md)並[型別推斷](../type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="82266-129">For more information, see [Automatic Generalization](../generics/automatic-generalization.md) and [Type Inference](../type-inference.md).</span></span>

## <a name="let-bindings-in-classes"></a><span data-ttu-id="82266-130">類別中的 let 繫結</span><span class="sxs-lookup"><span data-stu-id="82266-130">let Bindings in Classes</span></span>

<span data-ttu-id="82266-131">A`let`繫結可以出現在類別類型，但不是在結構或記錄類型。</span><span class="sxs-lookup"><span data-stu-id="82266-131">A `let` binding can appear in a class type but not in a structure or record type.</span></span> <span data-ttu-id="82266-132">若要使用 let 繫結中的類別類型，類別必須具有主要建構函式。</span><span class="sxs-lookup"><span data-stu-id="82266-132">To use a let binding in a class type, the class must have a primary constructor.</span></span> <span data-ttu-id="82266-133">建構函式參數必須出現在類別定義的型別名稱之後。</span><span class="sxs-lookup"><span data-stu-id="82266-133">Constructor parameters must appear after the type name in the class definition.</span></span> <span data-ttu-id="82266-134">A`let`中的類別類型的繫結定義私用欄位和成員，該類別類型，並搭配`do`類型中的繫結表單類型的主要建構函式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="82266-134">A `let` binding in a class type defines private fields and members for that class type and, together with `do` bindings in the type, forms the code for the primary constructor for the type.</span></span> <span data-ttu-id="82266-135">下列程式碼範例顯示類別`MyClass`私用欄位`field1`和`field2`。</span><span class="sxs-lookup"><span data-stu-id="82266-135">The following code examples show a class `MyClass` with private fields `field1` and `field2`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

<span data-ttu-id="82266-136">範圍`field1`和`field2`僅限於其宣告的型別。</span><span class="sxs-lookup"><span data-stu-id="82266-136">The scopes of `field1` and `field2` are limited to the type in which they are declared.</span></span> <span data-ttu-id="82266-137">如需詳細資訊，請參閱 < [ `let`類別中的繫結](../members/let-bindings-in-classes.md)並[類別](../classes.md)。</span><span class="sxs-lookup"><span data-stu-id="82266-137">For more information, see [`let` Bindings in Classes](../members/let-bindings-in-classes.md) and [Classes](../classes.md).</span></span>

## <a name="type-parameters-in-let-bindings"></a><span data-ttu-id="82266-138">型別參數中的 let 繫結</span><span class="sxs-lookup"><span data-stu-id="82266-138">Type Parameters in let Bindings</span></span>

<span data-ttu-id="82266-139">A`let`繫結，在模組層級，在類型中，或在 計算運算式中可以有明確的型別參數。</span><span class="sxs-lookup"><span data-stu-id="82266-139">A `let` binding at the module level, in a type, or in a computation expression can have explicit type parameters.</span></span> <span data-ttu-id="82266-140">Let 繫結中的運算式，例如函式定義內不得有類型參數。</span><span class="sxs-lookup"><span data-stu-id="82266-140">A let binding in an expression, such as within a function definition, cannot have type parameters.</span></span> <span data-ttu-id="82266-141">如需詳細資訊，請參閱[泛型](../generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="82266-141">For more information, see [Generics](../generics/index.md).</span></span>

## <a name="attributes-on-let-bindings"></a><span data-ttu-id="82266-142">屬性的 let 繫結</span><span class="sxs-lookup"><span data-stu-id="82266-142">Attributes on let Bindings</span></span>

<span data-ttu-id="82266-143">屬性可以套用至最上層`let`繫結，在模組中，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="82266-143">Attributes can be applied to top-level `let` bindings in a module, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a><span data-ttu-id="82266-144">範圍和協助工具的 Let 繫結</span><span class="sxs-lookup"><span data-stu-id="82266-144">Scope and Accessibility of Let Bindings</span></span>

<span data-ttu-id="82266-145">使用 let 繫結所宣告的實體的範圍僅限於包含的部分繫結出現之後，範圍 （例如函式、 模組、 檔案或類別）。</span><span class="sxs-lookup"><span data-stu-id="82266-145">The scope of an entity declared with a let binding is limited to the portion of the containing scope (such as a function, module, file or class) after the binding appears.</span></span> <span data-ttu-id="82266-146">因此，它可說是 let 繫結引入的名稱，進入範圍內。</span><span class="sxs-lookup"><span data-stu-id="82266-146">Therefore, it can be said that a let binding introduces a name into a scope.</span></span> <span data-ttu-id="82266-147">在模組中，讓繫結值或函式是模組的用戶端可以存取為模組可供存取，因為在模組中的 let 繫結會編譯成模組的公用函式。</span><span class="sxs-lookup"><span data-stu-id="82266-147">In a module, a let-bound value or function is accessible to clients of a module as long as the module is accessible, since the let bindings in a module are compiled into public functions of the module.</span></span> <span data-ttu-id="82266-148">相反地，類別中的 let 繫結是私用類別。</span><span class="sxs-lookup"><span data-stu-id="82266-148">By contrast, let bindings in a class are private to the class.</span></span>

<span data-ttu-id="82266-149">一般來說，模組中的函式必須使用用戶端程式碼時的模組名稱所限定。</span><span class="sxs-lookup"><span data-stu-id="82266-149">Normally, functions in modules must be qualified by the name of the module when used by client code.</span></span> <span data-ttu-id="82266-150">例如，如果模組`Module1`函式`function1`，使用者會指定`Module1.function1`參考函式。</span><span class="sxs-lookup"><span data-stu-id="82266-150">For example, if a module `Module1` has a function `function1`, users would specify `Module1.function1` to refer to the function.</span></span>

<span data-ttu-id="82266-151">模組的使用者可以使用匯入宣告，而不限定的模組名稱，使該模組內的函式可供使用。</span><span class="sxs-lookup"><span data-stu-id="82266-151">Users of a module may use an import declaration to make the functions within that module available for use without being qualified by the module name.</span></span> <span data-ttu-id="82266-152">在上述範例中，模組的使用者可以在此情況下開啟模組使用匯入宣告開放`Module1`，而且之後參考`function1`直接。</span><span class="sxs-lookup"><span data-stu-id="82266-152">In the example just mentioned, users of the module can in that case open the module by using the import declaration open `Module1` and thereafter refer to `function1` directly.</span></span>

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

<span data-ttu-id="82266-153">某些模組具有屬性[RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15)，這表示它們所公開的函式必須以模組名稱加以限定。</span><span class="sxs-lookup"><span data-stu-id="82266-153">Some modules have the attribute [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), which means that the functions that they expose must be qualified with the name of the module.</span></span> <span data-ttu-id="82266-154">例如， F# List 模組具有這個屬性。</span><span class="sxs-lookup"><span data-stu-id="82266-154">For example, the F# List module has this attribute.</span></span>

<span data-ttu-id="82266-155">如需有關模組和存取控制的詳細資訊，請參閱 <<c0> [ 模組](../modules.md)並[存取控制](../access-control.md)。</span><span class="sxs-lookup"><span data-stu-id="82266-155">For more information on modules and access control, see [Modules](../modules.md) and [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="82266-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82266-156">See also</span></span>

- [<span data-ttu-id="82266-157">函式</span><span class="sxs-lookup"><span data-stu-id="82266-157">Functions</span></span>](index.md)
- [<span data-ttu-id="82266-158">類別中的 `let` 繫結</span><span class="sxs-lookup"><span data-stu-id="82266-158">`let` Bindings in Classes</span></span>](../members/let-bindings-in-classes.md)