---
title: let 繫結
description: '瞭解如何使用 F # 「let」系結，這會將識別碼與值或函式產生關聯。'
ms.date: 05/16/2016
ms.openlocfilehash: 6f2396f480c5e6c631d0022f4732419ee5b07db6
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812220"
---
# <a name="let-bindings"></a><span data-ttu-id="462a3-103">let 繫結</span><span class="sxs-lookup"><span data-stu-id="462a3-103">let Bindings</span></span>

<span data-ttu-id="462a3-104">系結會將識別碼與值或函數*產生關聯。*</span><span class="sxs-lookup"><span data-stu-id="462a3-104">A *binding* associates an identifier with a value or function.</span></span> <span data-ttu-id="462a3-105">您可以使用 `let` 關鍵字將名稱系結至值或函數。</span><span class="sxs-lookup"><span data-stu-id="462a3-105">You use the `let` keyword to bind a name to a value or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="462a3-106">語法</span><span class="sxs-lookup"><span data-stu-id="462a3-106">Syntax</span></span>

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a><span data-ttu-id="462a3-107">備註</span><span class="sxs-lookup"><span data-stu-id="462a3-107">Remarks</span></span>

<span data-ttu-id="462a3-108">`let`關鍵字是在系結運算式中用來定義一個或多個名稱的值或函數值。</span><span class="sxs-lookup"><span data-stu-id="462a3-108">The `let` keyword is used in binding expressions to define values or function values for one or more names.</span></span> <span data-ttu-id="462a3-109">運算式最簡單的形式會將名稱系結 `let` 至簡單的值，如下所示。</span><span class="sxs-lookup"><span data-stu-id="462a3-109">The simplest form of the `let` expression binds a name to a simple value, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

<span data-ttu-id="462a3-110">如果您使用新的行將運算式與識別碼分開，則必須縮排運算式的每一行，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="462a3-110">If you separate the expression from the identifier by using a new line, you must indent each line of the expression, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

<span data-ttu-id="462a3-111">如下列程式碼所示，您可以指定包含名稱的模式，而不只是名稱。</span><span class="sxs-lookup"><span data-stu-id="462a3-111">Instead of just a name, a pattern that contains names can be specified, for example, a tuple, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

<span data-ttu-id="462a3-112">*主體運算式*是使用名稱的運算式。</span><span class="sxs-lookup"><span data-stu-id="462a3-112">The *body-expression* is the expression in which the names are used.</span></span> <span data-ttu-id="462a3-113">本文運算式會出現在自己的行上，並以關鍵字中的第一個字元縮排對齊 `let` ：</span><span class="sxs-lookup"><span data-stu-id="462a3-113">The body expression appears on its own line, indented to line up exactly with the first character in the `let` keyword:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

<span data-ttu-id="462a3-114">系結 `let` 可以出現在模組層級、類別類型的定義或區域範圍中，例如在函式定義中。</span><span class="sxs-lookup"><span data-stu-id="462a3-114">A `let` binding can appear at the module level, in the definition of a class type, or in local scopes, such as in a function definition.</span></span> <span data-ttu-id="462a3-115">`let`模組或類別類型中最上層的系結不需要有內文運算式，但在其他範圍層級，則需要主體運算式。</span><span class="sxs-lookup"><span data-stu-id="462a3-115">A `let` binding at the top level in a module or in a class type does not need to have a body expression, but at other scope levels, the body expression is required.</span></span> <span data-ttu-id="462a3-116">系結名稱可在定義點之後使用，但不能在系結出現之前的任何時間點使用 `let` ，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="462a3-116">The bound names are usable after the point of definition, but not at any point before the `let` binding appears, as is illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a><span data-ttu-id="462a3-117">函數系結</span><span class="sxs-lookup"><span data-stu-id="462a3-117">Function Bindings</span></span>

<span data-ttu-id="462a3-118">函數系結會遵循值系結的規則，但函數系結會包含函數名稱和參數，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="462a3-118">Function bindings follow the rules for value bindings, except that function bindings include the function name and the parameters, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

<span data-ttu-id="462a3-119">一般情況下，參數是模式，例如元組模式：</span><span class="sxs-lookup"><span data-stu-id="462a3-119">In general, parameters are patterns, such as a tuple pattern:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

<span data-ttu-id="462a3-120">系結 `let` 運算式會評估為最後一個運算式的值。</span><span class="sxs-lookup"><span data-stu-id="462a3-120">A `let` binding expression evaluates to the value of the last expression.</span></span> <span data-ttu-id="462a3-121">因此，在下列程式碼範例中，的值 `result` 是從 `100 * function3 (1, 2)` 評估為的計算 `300` 。</span><span class="sxs-lookup"><span data-stu-id="462a3-121">Therefore, in the following code example, the value of `result` is computed from `100 * function3 (1, 2)`, which evaluates to `300`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

<span data-ttu-id="462a3-122">如需詳細資訊，請參閱[函式](index.md)。</span><span class="sxs-lookup"><span data-stu-id="462a3-122">For more information, see [Functions](index.md).</span></span>

## <a name="type-annotations"></a><span data-ttu-id="462a3-123">類型注釋</span><span class="sxs-lookup"><span data-stu-id="462a3-123">Type Annotations</span></span>

<span data-ttu-id="462a3-124">您可以指定參數的類型，方法是包含冒號 (： ) 後面接著類型名稱，全都以括弧括住。</span><span class="sxs-lookup"><span data-stu-id="462a3-124">You can specify types for parameters by including a colon (:) followed by a type name, all enclosed in parentheses.</span></span> <span data-ttu-id="462a3-125">您也可以在最後一個參數之後附加冒號和類型，以指定傳回值的類型。</span><span class="sxs-lookup"><span data-stu-id="462a3-125">You can also specify the type of the return value by appending the colon and type after the last parameter.</span></span> <span data-ttu-id="462a3-126">的完整類型注釋 `function1` （使用整數做為參數類型）如下所示。</span><span class="sxs-lookup"><span data-stu-id="462a3-126">The full type annotations for `function1`, with integers as the parameter types, would be as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

<span data-ttu-id="462a3-127">如果沒有明確的型別參數，則會使用型別推斷來判斷函式的參數類型。</span><span class="sxs-lookup"><span data-stu-id="462a3-127">When there are no explicit type parameters, type inference is used to determine the types of parameters of functions.</span></span> <span data-ttu-id="462a3-128">這可能包括自動將參數的類型一般化為泛型。</span><span class="sxs-lookup"><span data-stu-id="462a3-128">This can include automatically generalizing the type of a parameter to be generic.</span></span>

<span data-ttu-id="462a3-129">如需詳細資訊，請參閱 [自動一般化](../generics/automatic-generalization.md) 和 [型別推斷](../type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="462a3-129">For more information, see [Automatic Generalization](../generics/automatic-generalization.md) and [Type Inference](../type-inference.md).</span></span>

## <a name="let-bindings-in-classes"></a><span data-ttu-id="462a3-130">類別中的 let 繫結</span><span class="sxs-lookup"><span data-stu-id="462a3-130">let Bindings in Classes</span></span>

<span data-ttu-id="462a3-131">系結 `let` 可以出現在類別型別中，但不能出現在結構或記錄型別中。</span><span class="sxs-lookup"><span data-stu-id="462a3-131">A `let` binding can appear in a class type but not in a structure or record type.</span></span> <span data-ttu-id="462a3-132">若要在類別型別中使用 let 系結，類別必須有主要的函式。</span><span class="sxs-lookup"><span data-stu-id="462a3-132">To use a let binding in a class type, the class must have a primary constructor.</span></span> <span data-ttu-id="462a3-133">函式參數必須出現在類別定義中的類型名稱之後。</span><span class="sxs-lookup"><span data-stu-id="462a3-133">Constructor parameters must appear after the type name in the class definition.</span></span> <span data-ttu-id="462a3-134">類別型別中的系結 `let` 會定義該類別型別的私用欄位和成員，並且與型別中的系結形成型別的系結程式 `do` 代碼。</span><span class="sxs-lookup"><span data-stu-id="462a3-134">A `let` binding in a class type defines private fields and members for that class type and, together with `do` bindings in the type, forms the code for the primary constructor for the type.</span></span> <span data-ttu-id="462a3-135">下列程式碼範例會顯示 `MyClass` 具有私用欄位 `field1` 和的類別 `field2` 。</span><span class="sxs-lookup"><span data-stu-id="462a3-135">The following code examples show a class `MyClass` with private fields `field1` and `field2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

<span data-ttu-id="462a3-136">和的範圍 `field1` `field2` 僅限於宣告它們的型別。</span><span class="sxs-lookup"><span data-stu-id="462a3-136">The scopes of `field1` and `field2` are limited to the type in which they are declared.</span></span> <span data-ttu-id="462a3-137">如需詳細資訊，請參閱類別和[類別](../classes.md) [ `let` 中](../members/let-bindings-in-classes.md)的系結。</span><span class="sxs-lookup"><span data-stu-id="462a3-137">For more information, see [`let` Bindings in Classes](../members/let-bindings-in-classes.md) and [Classes](../classes.md).</span></span>

## <a name="type-parameters-in-let-bindings"></a><span data-ttu-id="462a3-138">Let 系結中的型別參數</span><span class="sxs-lookup"><span data-stu-id="462a3-138">Type Parameters in let Bindings</span></span>

<span data-ttu-id="462a3-139">在 `let` 模組層級、型別或計算運算式中的系結可以有明確的型別參數。</span><span class="sxs-lookup"><span data-stu-id="462a3-139">A `let` binding at the module level, in a type, or in a computation expression can have explicit type parameters.</span></span> <span data-ttu-id="462a3-140">運算式中的 let 系結（例如在函式定義內）不能有型別參數。</span><span class="sxs-lookup"><span data-stu-id="462a3-140">A let binding in an expression, such as within a function definition, cannot have type parameters.</span></span> <span data-ttu-id="462a3-141">如需詳細資訊，請參閱[泛型](../generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="462a3-141">For more information, see [Generics](../generics/index.md).</span></span>

## <a name="attributes-on-let-bindings"></a><span data-ttu-id="462a3-142">Let 系結上的屬性</span><span class="sxs-lookup"><span data-stu-id="462a3-142">Attributes on let Bindings</span></span>

<span data-ttu-id="462a3-143">屬性可以套用至模組中的最上層系結 `let` ，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="462a3-143">Attributes can be applied to top-level `let` bindings in a module, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a><span data-ttu-id="462a3-144">Let 系結的範圍和協助工具</span><span class="sxs-lookup"><span data-stu-id="462a3-144">Scope and Accessibility of Let Bindings</span></span>

<span data-ttu-id="462a3-145">以 let 系結宣告的實體範圍僅限於包含範圍 (的部分，例如函式、模組、檔案或類別在系結出現之後) 。</span><span class="sxs-lookup"><span data-stu-id="462a3-145">The scope of an entity declared with a let binding is limited to the portion of the containing scope (such as a function, module, file or class) after the binding appears.</span></span> <span data-ttu-id="462a3-146">因此，您可以說 let 系結將名稱引入範圍中。</span><span class="sxs-lookup"><span data-stu-id="462a3-146">Therefore, it can be said that a let binding introduces a name into a scope.</span></span> <span data-ttu-id="462a3-147">在模組中，只要模組可供存取，模組的用戶端就可以存取 let 系結值或函數，因為模組中的 let 系結會編譯成模組的公用函式。</span><span class="sxs-lookup"><span data-stu-id="462a3-147">In a module, a let-bound value or function is accessible to clients of a module as long as the module is accessible, since the let bindings in a module are compiled into public functions of the module.</span></span> <span data-ttu-id="462a3-148">相較之下，「讓類別中的系結」是類別的私用。</span><span class="sxs-lookup"><span data-stu-id="462a3-148">By contrast, let bindings in a class are private to the class.</span></span>

<span data-ttu-id="462a3-149">一般來說，當用戶端程式代碼使用模組時，模組中的函式必須以模組的名稱來限定。</span><span class="sxs-lookup"><span data-stu-id="462a3-149">Normally, functions in modules must be qualified by the name of the module when used by client code.</span></span> <span data-ttu-id="462a3-150">例如，如果模組 `Module1` 有一個函式 `function1` ，則使用者會指定 `Module1.function1` 參考該函數。</span><span class="sxs-lookup"><span data-stu-id="462a3-150">For example, if a module `Module1` has a function `function1`, users would specify `Module1.function1` to refer to the function.</span></span>

<span data-ttu-id="462a3-151">模組的使用者可能會使用匯入宣告，讓該模組內的函式可供使用，而不會受到模組名稱的限定。</span><span class="sxs-lookup"><span data-stu-id="462a3-151">Users of a module may use an import declaration to make the functions within that module available for use without being qualified by the module name.</span></span> <span data-ttu-id="462a3-152">在剛才提及的範例中，模組的使用者可以在該案例中使用匯入宣告開啟模組， `Module1` 之後再參考 `function1` 直接。</span><span class="sxs-lookup"><span data-stu-id="462a3-152">In the example just mentioned, users of the module can in that case open the module by using the import declaration open `Module1` and thereafter refer to `function1` directly.</span></span>

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

<span data-ttu-id="462a3-153">某些模組具有 [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html)屬性，這表示它們所公開的函式必須以模組的名稱來限定。</span><span class="sxs-lookup"><span data-stu-id="462a3-153">Some modules have the attribute [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html), which means that the functions that they expose must be qualified with the name of the module.</span></span> <span data-ttu-id="462a3-154">例如，F # 清單模組有這個屬性。</span><span class="sxs-lookup"><span data-stu-id="462a3-154">For example, the F# List module has this attribute.</span></span>

<span data-ttu-id="462a3-155">如需模組和存取控制的詳細資訊，請參閱 [模組](../modules.md) 和 [存取控制](../access-control.md)。</span><span class="sxs-lookup"><span data-stu-id="462a3-155">For more information on modules and access control, see [Modules](../modules.md) and [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="462a3-156">請參閱</span><span class="sxs-lookup"><span data-stu-id="462a3-156">See also</span></span>

- [<span data-ttu-id="462a3-157">函式</span><span class="sxs-lookup"><span data-stu-id="462a3-157">Functions</span></span>](index.md)
- [<span data-ttu-id="462a3-158">`let` 類別中的系結</span><span class="sxs-lookup"><span data-stu-id="462a3-158">`let` Bindings in Classes</span></span>](../members/let-bindings-in-classes.md)
