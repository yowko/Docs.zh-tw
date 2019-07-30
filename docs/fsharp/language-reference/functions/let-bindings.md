---
title: let 繫結
description: 瞭解如何使用F# 「let」系結, 以將識別碼與值或函式產生關聯。
ms.date: 05/16/2016
ms.openlocfilehash: 654631c7d1c48d8737e6098c98efee54cfdd91be
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630634"
---
# <a name="let-bindings"></a><span data-ttu-id="ab148-103">let 繫結</span><span class="sxs-lookup"><span data-stu-id="ab148-103">let Bindings</span></span>

<span data-ttu-id="ab148-104">系  結會將識別碼與值或函數產生關聯。</span><span class="sxs-lookup"><span data-stu-id="ab148-104">A *binding* associates an identifier with a value or function.</span></span> <span data-ttu-id="ab148-105">您可以使用`let`關鍵字, 將名稱系結至值或函數。</span><span class="sxs-lookup"><span data-stu-id="ab148-105">You use the `let` keyword to bind a name to a value or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="ab148-106">語法</span><span class="sxs-lookup"><span data-stu-id="ab148-106">Syntax</span></span>

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a><span data-ttu-id="ab148-107">備註</span><span class="sxs-lookup"><span data-stu-id="ab148-107">Remarks</span></span>

<span data-ttu-id="ab148-108">`let`關鍵字是在系結運算式中用來定義一或多個名稱的值或函數值。</span><span class="sxs-lookup"><span data-stu-id="ab148-108">The `let` keyword is used in binding expressions to define values or function values for one or more names.</span></span> <span data-ttu-id="ab148-109">`let`運算式的最簡單形式會將名稱系結至簡單的值, 如下所示。</span><span class="sxs-lookup"><span data-stu-id="ab148-109">The simplest form of the `let` expression binds a name to a simple value, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

<span data-ttu-id="ab148-110">如果您使用新的行來分隔運算式與識別碼, 則必須縮排運算式的每一行, 如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="ab148-110">If you separate the expression from the identifier by using a new line, you must indent each line of the expression, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

<span data-ttu-id="ab148-111">如下列程式碼所示, 您可以指定包含名稱的模式, 而不只是名稱。</span><span class="sxs-lookup"><span data-stu-id="ab148-111">Instead of just a name, a pattern that contains names can be specified, for example, a tuple, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

<span data-ttu-id="ab148-112">*主體運算式*是使用名稱的運算式。</span><span class="sxs-lookup"><span data-stu-id="ab148-112">The *body-expression* is the expression in which the names are used.</span></span> <span data-ttu-id="ab148-113">本文運算式會顯示在它自己的行上, 並與`let`關鍵字中的第一個字元完全對齊:</span><span class="sxs-lookup"><span data-stu-id="ab148-113">The body expression appears on its own line, indented to line up exactly with the first character in the `let` keyword:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

<span data-ttu-id="ab148-114">`let`系結可能會出現在模組層級、類別類型的定義中, 或在本機範圍 (如函式定義中)。</span><span class="sxs-lookup"><span data-stu-id="ab148-114">A `let` binding can appear at the module level, in the definition of a class type, or in local scopes, such as in a function definition.</span></span> <span data-ttu-id="ab148-115">`let`在模組或類別類型中, 位於最上層的系結不需要具有主體運算式, 但在其他範圍層級, 則需要主體運算式。</span><span class="sxs-lookup"><span data-stu-id="ab148-115">A `let` binding at the top level in a module or in a class type does not need to have a body expression, but at other scope levels, the body expression is required.</span></span> <span data-ttu-id="ab148-116">系結名稱可在定義點之後使用, 但不會出現在系結之前`let`的任何時間點, 如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="ab148-116">The bound names are usable after the point of definition, but not at any point before the `let` binding appears, as is illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a><span data-ttu-id="ab148-117">函數系結</span><span class="sxs-lookup"><span data-stu-id="ab148-117">Function Bindings</span></span>

<span data-ttu-id="ab148-118">函數系結會遵循值系結的規則, 不同之處在于函式系結包含函式名稱和參數, 如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="ab148-118">Function bindings follow the rules for value bindings, except that function bindings include the function name and the parameters, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

<span data-ttu-id="ab148-119">一般而言, 參數是模式, 例如元組模式:</span><span class="sxs-lookup"><span data-stu-id="ab148-119">In general, parameters are patterns, such as a tuple pattern:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

<span data-ttu-id="ab148-120">`let`系結運算式會評估為最後一個運算式的值。</span><span class="sxs-lookup"><span data-stu-id="ab148-120">A `let` binding expression evaluates to the value of the last expression.</span></span> <span data-ttu-id="ab148-121">因此, 在下列`result`程式碼範例中, 的值是從`100 * function3 (1, 2)` `300`計算得出的。</span><span class="sxs-lookup"><span data-stu-id="ab148-121">Therefore, in the following code example, the value of `result` is computed from `100 * function3 (1, 2)`, which evaluates to `300`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

<span data-ttu-id="ab148-122">如需詳細資訊，請參閱[函式](index.md)。</span><span class="sxs-lookup"><span data-stu-id="ab148-122">For more information, see [Functions](index.md).</span></span>

## <a name="type-annotations"></a><span data-ttu-id="ab148-123">類型注釋</span><span class="sxs-lookup"><span data-stu-id="ab148-123">Type Annotations</span></span>

<span data-ttu-id="ab148-124">您可以指定參數的類型, 方法是包含冒號 (:)後面接著一個型別名稱, 並以括弧括住。</span><span class="sxs-lookup"><span data-stu-id="ab148-124">You can specify types for parameters by including a colon (:) followed by a type name, all enclosed in parentheses.</span></span> <span data-ttu-id="ab148-125">您也可以在最後一個參數之後附加冒號和類型, 藉以指定傳回值的類型。</span><span class="sxs-lookup"><span data-stu-id="ab148-125">You can also specify the type of the return value by appending the colon and type after the last parameter.</span></span> <span data-ttu-id="ab148-126">具有整數做為參數`function1`類型的完整類型注釋, 將如下所示。</span><span class="sxs-lookup"><span data-stu-id="ab148-126">The full type annotations for `function1`, with integers as the parameter types, would be as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

<span data-ttu-id="ab148-127">當沒有明確型別參數時, 會使用型別推斷來判斷函數的參數類型。</span><span class="sxs-lookup"><span data-stu-id="ab148-127">When there are no explicit type parameters, type inference is used to determine the types of parameters of functions.</span></span> <span data-ttu-id="ab148-128">這可能包括自動將參數的類型一般化為泛型。</span><span class="sxs-lookup"><span data-stu-id="ab148-128">This can include automatically generalizing the type of a parameter to be generic.</span></span>

<span data-ttu-id="ab148-129">如需詳細資訊, 請參閱[自動一般化](../generics/automatic-generalization.md)和[型別推斷](../type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="ab148-129">For more information, see [Automatic Generalization](../generics/automatic-generalization.md) and [Type Inference](../type-inference.md).</span></span>

## <a name="let-bindings-in-classes"></a><span data-ttu-id="ab148-130">類別中的 let 繫結</span><span class="sxs-lookup"><span data-stu-id="ab148-130">let Bindings in Classes</span></span>

<span data-ttu-id="ab148-131">`let`系結可以出現在類別類型中, 而不是在結構或記錄類型中。</span><span class="sxs-lookup"><span data-stu-id="ab148-131">A `let` binding can appear in a class type but not in a structure or record type.</span></span> <span data-ttu-id="ab148-132">若要在類別類型中使用 let 系結, 類別必須具有主要的函式。</span><span class="sxs-lookup"><span data-stu-id="ab148-132">To use a let binding in a class type, the class must have a primary constructor.</span></span> <span data-ttu-id="ab148-133">函式參數必須出現在類別定義中的型別名稱之後。</span><span class="sxs-lookup"><span data-stu-id="ab148-133">Constructor parameters must appear after the type name in the class definition.</span></span> <span data-ttu-id="ab148-134">類別`let`類型中的系結會定義該類別類型的私用欄位和成員, `do`連同類型中的系結, 會形成該類型主要的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ab148-134">A `let` binding in a class type defines private fields and members for that class type and, together with `do` bindings in the type, forms the code for the primary constructor for the type.</span></span> <span data-ttu-id="ab148-135">下列程式碼範例顯示具有私`MyClass`用欄位`field1`和`field2`的類別。</span><span class="sxs-lookup"><span data-stu-id="ab148-135">The following code examples show a class `MyClass` with private fields `field1` and `field2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

<span data-ttu-id="ab148-136">`field1` 和`field2`的範圍僅限於宣告它們的類型。</span><span class="sxs-lookup"><span data-stu-id="ab148-136">The scopes of `field1` and `field2` are limited to the type in which they are declared.</span></span> <span data-ttu-id="ab148-137">如需詳細資訊, 請參閱[ `let`類別](../members/let-bindings-in-classes.md)和[類別](../classes.md)中的系結。</span><span class="sxs-lookup"><span data-stu-id="ab148-137">For more information, see [`let` Bindings in Classes](../members/let-bindings-in-classes.md) and [Classes](../classes.md).</span></span>

## <a name="type-parameters-in-let-bindings"></a><span data-ttu-id="ab148-138">Let 系結中的型別參數</span><span class="sxs-lookup"><span data-stu-id="ab148-138">Type Parameters in let Bindings</span></span>

<span data-ttu-id="ab148-139">`let`模組層級、類型或計算運算式中的系結可以有明確類型參數。</span><span class="sxs-lookup"><span data-stu-id="ab148-139">A `let` binding at the module level, in a type, or in a computation expression can have explicit type parameters.</span></span> <span data-ttu-id="ab148-140">運算式中的 let 系結 (例如函式定義內) 不能有型別參數。</span><span class="sxs-lookup"><span data-stu-id="ab148-140">A let binding in an expression, such as within a function definition, cannot have type parameters.</span></span> <span data-ttu-id="ab148-141">如需詳細資訊，請參閱[泛型](../generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ab148-141">For more information, see [Generics](../generics/index.md).</span></span>

## <a name="attributes-on-let-bindings"></a><span data-ttu-id="ab148-142">Let 系結上的屬性</span><span class="sxs-lookup"><span data-stu-id="ab148-142">Attributes on let Bindings</span></span>

<span data-ttu-id="ab148-143">屬性可以套用至模組中的最`let`上層系結, 如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="ab148-143">Attributes can be applied to top-level `let` bindings in a module, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a><span data-ttu-id="ab148-144">Let 系結的範圍和可存取性</span><span class="sxs-lookup"><span data-stu-id="ab148-144">Scope and Accessibility of Let Bindings</span></span>

<span data-ttu-id="ab148-145">使用 let 系結所宣告之實體的範圍, 會在系結出現之後, 限制為包含範圍的部分 (例如函式、模組、檔案或類別)。</span><span class="sxs-lookup"><span data-stu-id="ab148-145">The scope of an entity declared with a let binding is limited to the portion of the containing scope (such as a function, module, file or class) after the binding appears.</span></span> <span data-ttu-id="ab148-146">因此, 您可以將「let 系結」引進範圍中的名稱。</span><span class="sxs-lookup"><span data-stu-id="ab148-146">Therefore, it can be said that a let binding introduces a name into a scope.</span></span> <span data-ttu-id="ab148-147">在模組中, 只要模組可供存取, 模組的用戶端就可以存取「let 系結」值或函數, 因為「let 系結」會編譯成模組的公用函式。</span><span class="sxs-lookup"><span data-stu-id="ab148-147">In a module, a let-bound value or function is accessible to clients of a module as long as the module is accessible, since the let bindings in a module are compiled into public functions of the module.</span></span> <span data-ttu-id="ab148-148">相反地, 類別中的 let 系結是私用的。</span><span class="sxs-lookup"><span data-stu-id="ab148-148">By contrast, let bindings in a class are private to the class.</span></span>

<span data-ttu-id="ab148-149">一般來說, 當用戶端程式代碼使用模組的名稱時, 模組中的函式必須以該模組的名稱來限定。</span><span class="sxs-lookup"><span data-stu-id="ab148-149">Normally, functions in modules must be qualified by the name of the module when used by client code.</span></span> <span data-ttu-id="ab148-150">例如, 如果模組`Module1`具有`function1`函式, 則使用者會指定`Module1.function1`來參考該函式。</span><span class="sxs-lookup"><span data-stu-id="ab148-150">For example, if a module `Module1` has a function `function1`, users would specify `Module1.function1` to refer to the function.</span></span>

<span data-ttu-id="ab148-151">模組的使用者可以使用匯入宣告, 讓該模組內的函式可供使用, 而不需要由模組名稱限定。</span><span class="sxs-lookup"><span data-stu-id="ab148-151">Users of a module may use an import declaration to make the functions within that module available for use without being qualified by the module name.</span></span> <span data-ttu-id="ab148-152">在剛才所述的範例中, 模組的使用者可以在此情況下, 使用匯入`Module1`宣告開啟模組, 並在之後`function1`直接參考。</span><span class="sxs-lookup"><span data-stu-id="ab148-152">In the example just mentioned, users of the module can in that case open the module by using the import declaration open `Module1` and thereafter refer to `function1` directly.</span></span>

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

<span data-ttu-id="ab148-153">有些模組具有屬性[RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), 這表示它們所公開的函式必須以模組的名稱來限定。</span><span class="sxs-lookup"><span data-stu-id="ab148-153">Some modules have the attribute [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), which means that the functions that they expose must be qualified with the name of the module.</span></span> <span data-ttu-id="ab148-154">例如, F# List 模組具有這個屬性。</span><span class="sxs-lookup"><span data-stu-id="ab148-154">For example, the F# List module has this attribute.</span></span>

<span data-ttu-id="ab148-155">如需模組和存取控制的詳細資訊, 請參閱[模組](../modules.md)和[存取控制](../access-control.md)。</span><span class="sxs-lookup"><span data-stu-id="ab148-155">For more information on modules and access control, see [Modules](../modules.md) and [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ab148-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab148-156">See also</span></span>

- [<span data-ttu-id="ab148-157">函式</span><span class="sxs-lookup"><span data-stu-id="ab148-157">Functions</span></span>](index.md)
- [<span data-ttu-id="ab148-158">類別中的 `let` 繫結</span><span class="sxs-lookup"><span data-stu-id="ab148-158">`let` Bindings in Classes</span></span>](../members/let-bindings-in-classes.md)
