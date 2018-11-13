---
title: 泛型 (F#)
description: 了解如何使用 F# 泛型函式和類型，可讓您撰寫程式碼，而不需要重複程式碼適用於各種不同的類型。
ms.date: 05/16/2016
ms.openlocfilehash: fc061f19c6c7fa737f7ca05aae83fd42c0010b37
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "44084958"
---
# <a name="generics"></a><span data-ttu-id="8554b-103">泛型</span><span class="sxs-lookup"><span data-stu-id="8554b-103">Generics</span></span>

<span data-ttu-id="8554b-104">F# 函式值、方法、屬性和彙總類型 (例如類別、記錄和差別聯集) 都可以是「泛型」。</span><span class="sxs-lookup"><span data-stu-id="8554b-104">F# function values, methods, properties, and aggregate types such as classes, records, and discriminated unions can be *generic*.</span></span> <span data-ttu-id="8554b-105">泛型建構至少包含一個類型參數，此參數通常是由泛型建構的使用者所提供。</span><span class="sxs-lookup"><span data-stu-id="8554b-105">Generic constructs contain at least one type parameter, which is usually supplied by the user of the generic construct.</span></span> <span data-ttu-id="8554b-106">泛型函式和類型可讓您撰寫適用於各種類型的程式碼，而不需對每一種類型重複輸入程式碼。</span><span class="sxs-lookup"><span data-stu-id="8554b-106">Generic functions and types enable you to write code that works with a variety of types without repeating the code for each type.</span></span> <span data-ttu-id="8554b-107">由於編譯器的型別推斷和自動一般化機制通常會將程式碼隱含推斷為泛型，所以要讓程式碼在 F# 中成為泛型很簡單。</span><span class="sxs-lookup"><span data-stu-id="8554b-107">Making your code generic can be simple in F#, because often your code is implicitly inferred to be generic by the compiler's type inference and automatic generalization mechanisms.</span></span>

## <a name="syntax"></a><span data-ttu-id="8554b-108">語法</span><span class="sxs-lookup"><span data-stu-id="8554b-108">Syntax</span></span>

```fsharp
// Explicitly generic function.
let function-name<type-parameters> parameter-list =
function-body

// Explicitly generic method.
[ static ] member object-identifer.method-name<type-parameters> parameter-list [ return-type ] =
method-body

// Explicitly generic class, record, interface, structure,
// or discriminated union.
type type-name<type-parameters> type-definition
```

## <a name="remarks"></a><span data-ttu-id="8554b-109">備註</span><span class="sxs-lookup"><span data-stu-id="8554b-109">Remarks</span></span>

<span data-ttu-id="8554b-110">在函式或類型名稱之後的角括弧中，明確泛型函式或類型的宣告非常類似於非泛型函式或類型的宣告，但類型參數的規格 (和使用方式) 除外。</span><span class="sxs-lookup"><span data-stu-id="8554b-110">The declaration of an explicitly generic function or type is much like that of a non-generic function or type, except for the specification (and use) of the type parameters, in angle brackets after the function or type name.</span></span>

<span data-ttu-id="8554b-111">宣告通常為隱含泛型。</span><span class="sxs-lookup"><span data-stu-id="8554b-111">Declarations are often implicitly generic.</span></span> <span data-ttu-id="8554b-112">若您並未完全指定每一個用於組成函式或類型之參數的類型，則編譯器會嘗試根據您撰寫的程式碼來推斷每一個參數、值和變數的類型。</span><span class="sxs-lookup"><span data-stu-id="8554b-112">If you do not fully specify the type of every parameter that is used to compose a function or type, the compiler attempts to infer the type of each parameter, value, and variable from the code you write.</span></span> <span data-ttu-id="8554b-113">如需詳細資訊，請參閱[型別推斷](../type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="8554b-113">For more information, see [Type Inference](../type-inference.md).</span></span> <span data-ttu-id="8554b-114">若類型或函式的程式碼並未限制參數的類型，則函式或類型即為隱含泛型。</span><span class="sxs-lookup"><span data-stu-id="8554b-114">If the code for your type or function does not otherwise constrain the types of parameters, the function or type is implicitly generic.</span></span> <span data-ttu-id="8554b-115">此程序稱為「自動一般化」。</span><span class="sxs-lookup"><span data-stu-id="8554b-115">This process is named *automatic generalization*.</span></span> <span data-ttu-id="8554b-116">自動一般化有一些限制。</span><span class="sxs-lookup"><span data-stu-id="8554b-116">There are some limits on automatic generalization.</span></span> <span data-ttu-id="8554b-117">例如，若 F# 編譯器無法推斷泛型建構的類型，則該編譯器所回報的錯誤會參考一種稱為「值限制」的限制。</span><span class="sxs-lookup"><span data-stu-id="8554b-117">For example, if the F# compiler is unable to infer the types for a generic construct, the compiler reports an error that refers to a restriction called the *value restriction*.</span></span> <span data-ttu-id="8554b-118">在此情況下，您可能必須新增一些類型註解。</span><span class="sxs-lookup"><span data-stu-id="8554b-118">In that case, you may have to add some type annotations.</span></span> <span data-ttu-id="8554b-119">如需自動一般化和值限制的詳細資訊，以及如何變更程式碼來解決問題的詳細資訊，請參閱[自動產生](automatic-generalization.md)。</span><span class="sxs-lookup"><span data-stu-id="8554b-119">For more information about automatic generalization and the value restriction, and how to change your code to address the problem, see [Automatic Generalization](automatic-generalization.md).</span></span>

<span data-ttu-id="8554b-120">在先前的語法中，*type-parameters* 是一份代表未知類型的參數清單 (以逗號分隔)，而每一個參數都是以單引號開頭，並選擇性加入條件約束子句，以進一步限制哪些類型可用於該類型參數。</span><span class="sxs-lookup"><span data-stu-id="8554b-120">In the previous syntax, *type-parameters* is a comma-separated list of parameters that represent unknown types, each of which starts with a single quotation mark, optionally with a constraint clause that further limits what types may be used for that type parameter.</span></span> <span data-ttu-id="8554b-121">如需各種條件約束子句的語法以及條件約束的其他資訊，請參閱[條件約束](constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="8554b-121">For the syntax for constraint clauses of various kinds and other information about constraints, see [Constraints](constraints.md).</span></span>

<span data-ttu-id="8554b-122">語法中的 *type-definition* 與非泛型型別的類型定義相同。</span><span class="sxs-lookup"><span data-stu-id="8554b-122">The *type-definition* in the syntax is the same as the type definition for a non-generic type.</span></span> <span data-ttu-id="8554b-123">這包含類別類型的建構函式參數、選擇性 `as` 子句、等號、記錄欄位、`inherit` 子句、差別聯集的選項、`let` 和 `do` 繫結、成員定義，以及非泛型型別定義中允許的任何其他項目。</span><span class="sxs-lookup"><span data-stu-id="8554b-123">It includes the constructor parameters for a class type, an optional `as` clause, the equal symbol, the record fields, the `inherit` clause, the choices for a discriminated union, `let` and `do` bindings, member definitions, and anything else permitted in a non-generic type definition.</span></span>

<span data-ttu-id="8554b-124">其他語法項目與非泛型函式和類型的語法項目相同。</span><span class="sxs-lookup"><span data-stu-id="8554b-124">The other syntax elements are the same as those for non-generic functions and types.</span></span> <span data-ttu-id="8554b-125">例如，*object-identifier* 是一個代表包含物件本身的識別項。</span><span class="sxs-lookup"><span data-stu-id="8554b-125">For example, *object-identifier* is an identifier that represents the containing object itself.</span></span>

<span data-ttu-id="8554b-126">屬性、欄位和建構函式不能比封入類型更加泛型。</span><span class="sxs-lookup"><span data-stu-id="8554b-126">Properties, fields, and constructors cannot be more generic than the enclosing type.</span></span> <span data-ttu-id="8554b-127">此外，模組中的值不可以為泛型。</span><span class="sxs-lookup"><span data-stu-id="8554b-127">Also, values in a module cannot be generic.</span></span>

## <a name="implicitly-generic-constructs"></a><span data-ttu-id="8554b-128">隱含泛型建構</span><span class="sxs-lookup"><span data-stu-id="8554b-128">Implicitly Generic Constructs</span></span>

<span data-ttu-id="8554b-129">當 F# 編譯器推斷程式碼中的類型時，它會自動將任何可以成為泛型的函式自動視為泛型。</span><span class="sxs-lookup"><span data-stu-id="8554b-129">When the F# compiler infers the types in your code, it automatically treats any function that can be generic as generic.</span></span> <span data-ttu-id="8554b-130">若您明確指定類型 (例如參數類型)，則會防止自動一般化。</span><span class="sxs-lookup"><span data-stu-id="8554b-130">If you specify a type explicitly, such as a parameter type, you prevent automatic generalization.</span></span>

<span data-ttu-id="8554b-131">在下列程式碼範例中，`makeList` 是泛型的，即使它或它的參數皆未明確地宣告為泛型。</span><span class="sxs-lookup"><span data-stu-id="8554b-131">In the following code example, `makeList` is generic, even though neither it nor its parameters are explicitly declared as generic.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1700.fs)]

<span data-ttu-id="8554b-132">此函式的簽章被推斷為 `'a -> 'a -> 'a list`。</span><span class="sxs-lookup"><span data-stu-id="8554b-132">The signature of the function is inferred to be `'a -> 'a -> 'a list`.</span></span> <span data-ttu-id="8554b-133">請注意，這個範例中的 `a` 和 `b` 被推斷為具有相同的類型。</span><span class="sxs-lookup"><span data-stu-id="8554b-133">Note that `a` and `b` in this example are inferred to have the same type.</span></span> <span data-ttu-id="8554b-134">這是因為它們一起包含在清單中，而且清單的所有項目都必須是相同的類型。</span><span class="sxs-lookup"><span data-stu-id="8554b-134">This is because they are included in a list together, and all elements of a list must be of the same type.</span></span>

<span data-ttu-id="8554b-135">您也可以在類型註解中使用單引號語法，表示參數類型是泛型型別參數，而讓函式成為泛型。</span><span class="sxs-lookup"><span data-stu-id="8554b-135">You can also make a function generic by using the single quotation mark syntax in a type annotation to indicate that a parameter type is a generic type parameter.</span></span> <span data-ttu-id="8554b-136">在下列程式碼中，`function1` 為泛型，因為它的參數已用這種方式宣告為類型參數。</span><span class="sxs-lookup"><span data-stu-id="8554b-136">In the following code, `function1` is generic because its parameters are declared in this manner, as type parameters.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1701.fs)]

## <a name="explicitly-generic-constructs"></a><span data-ttu-id="8554b-137">明確泛型建構</span><span class="sxs-lookup"><span data-stu-id="8554b-137">Explicitly Generic Constructs</span></span>

<span data-ttu-id="8554b-138">以角括弧 (`<type-parameter>`) 明確宣告函式的類型參數，也可以讓函式變成泛型函式。</span><span class="sxs-lookup"><span data-stu-id="8554b-138">You can also make a function generic by explicitly declaring its type parameters in angle brackets (`<type-parameter>`).</span></span> <span data-ttu-id="8554b-139">以下的程式碼可說明這點。</span><span class="sxs-lookup"><span data-stu-id="8554b-139">The following code illustrates this.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1703.fs)]

## <a name="using-generic-constructs"></a><span data-ttu-id="8554b-140">使用泛型建構</span><span class="sxs-lookup"><span data-stu-id="8554b-140">Using Generic Constructs</span></span>

<span data-ttu-id="8554b-141">當您使用泛型函式或方法時，您不一定要指定類型引數。</span><span class="sxs-lookup"><span data-stu-id="8554b-141">When you use generic functions or methods, you might not have to specify the type arguments.</span></span> <span data-ttu-id="8554b-142">編譯器會使用型別推斷來推斷適當的類型引數。</span><span class="sxs-lookup"><span data-stu-id="8554b-142">The compiler uses type inference to infer the appropriate type arguments.</span></span> <span data-ttu-id="8554b-143">若仍然模稜兩可，您可以在角括弧中提供類型引數，並以逗號分隔多個類型引數。</span><span class="sxs-lookup"><span data-stu-id="8554b-143">If there is still an ambiguity, you can supply type arguments in angle brackets, separating multiple type arguments with commas.</span></span>

<span data-ttu-id="8554b-144">下列程式碼顯示如何使用先前章節中定義的函式。</span><span class="sxs-lookup"><span data-stu-id="8554b-144">The following code shows the use of the functions that are defined in the previous sections.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1702.fs)]

>[!NOTE]
<span data-ttu-id="8554b-145">依照名稱參考泛型型別的方法有兩種。</span><span class="sxs-lookup"><span data-stu-id="8554b-145">There are two ways to refer to a generic type by name.</span></span> <span data-ttu-id="8554b-146">例如，`list<int>` 和 `int list` 就是兩種用於參考具有單一類型引數 `int` 之泛型型別 `list` 的方法。</span><span class="sxs-lookup"><span data-stu-id="8554b-146">For example, `list<int>` and `int list` are two ways to refer to a generic type `list` that has a single type argument `int`.</span></span> <span data-ttu-id="8554b-147">後面的形式照慣例僅適用於內建的 F# 類型，例如 `list` 和 `option`。</span><span class="sxs-lookup"><span data-stu-id="8554b-147">The latter form is conventionally used only with built-in F# types such as `list` and `option`.</span></span> <span data-ttu-id="8554b-148">若有多個類型引數，您通常會使用語法 `Dictionary<int, string>`，但是也可以使用語法 `(int, string) Dictionary`。</span><span class="sxs-lookup"><span data-stu-id="8554b-148">If there are multiple type arguments, you normally use the syntax `Dictionary<int, string>` but you can also use the syntax `(int, string) Dictionary`.</span></span>

## <a name="wildcards-as-type-arguments"></a><span data-ttu-id="8554b-149">使用萬用字元作為類型引數</span><span class="sxs-lookup"><span data-stu-id="8554b-149">Wildcards as Type Arguments</span></span>

<span data-ttu-id="8554b-150">若要指定應該由編譯器推斷的類型引數，您可以使用底線或萬用字元符號 (`_`)，而非使用具名的類型引數。</span><span class="sxs-lookup"><span data-stu-id="8554b-150">To specify that a type argument should be inferred by the compiler, you can use the underscore, or wildcard symbol (`_`), instead of a named type argument.</span></span> <span data-ttu-id="8554b-151">如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="8554b-151">This is shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1704.fs)]

## <a name="constraints-in-generic-types-and-functions"></a><span data-ttu-id="8554b-152">泛型型別和函式的條件約束</span><span class="sxs-lookup"><span data-stu-id="8554b-152">Constraints in Generic Types and Functions</span></span>

<span data-ttu-id="8554b-153">在泛型型別或函式定義中，您只能使用已知可用於泛型型別參數的建構。</span><span class="sxs-lookup"><span data-stu-id="8554b-153">In a generic type or function definition, you can use only those constructs that are known to be available on the generic type parameter.</span></span> <span data-ttu-id="8554b-154">如此一來，才能在編譯階段啟用函式和方法呼叫的驗證。</span><span class="sxs-lookup"><span data-stu-id="8554b-154">This is required to enable the verification of function and method calls at compile time.</span></span> <span data-ttu-id="8554b-155">若您明確宣告類型參數，則可以將明確條件約束套用至泛型型別參數，以通知編譯器可以使用某些方法和函式。</span><span class="sxs-lookup"><span data-stu-id="8554b-155">If you declare your type parameters explicitly, you can apply an explicit constraint to a generic type parameter to notify the compiler that certain methods and functions are available.</span></span> <span data-ttu-id="8554b-156">不過，若您允許 F# 編譯器推斷您的泛型參數類型，則它會為您判斷適當的條件約束。</span><span class="sxs-lookup"><span data-stu-id="8554b-156">However, if you allow the F# compiler to infer your generic parameter types, it will determine the appropriate constraints for you.</span></span> <span data-ttu-id="8554b-157">如需詳細資訊，請參閱[條件約束](constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="8554b-157">For more information, see [Constraints](constraints.md).</span></span>

## <a name="statically-resolved-type-parameters"></a><span data-ttu-id="8554b-158">以統計方式解析的型別參數</span><span class="sxs-lookup"><span data-stu-id="8554b-158">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="8554b-159">F# 程式中可以使用的類型參數有兩種。</span><span class="sxs-lookup"><span data-stu-id="8554b-159">There are two kinds of type parameters that can be used in F# programs.</span></span> <span data-ttu-id="8554b-160">第一種是前幾節中所描述的該類泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="8554b-160">The first are generic type parameters of the kind described in the previous sections.</span></span> <span data-ttu-id="8554b-161">這一種類型參數等同於在 Visual Basic 和 C# 等語言中使用的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="8554b-161">This first kind of type parameter is equivalent to the generic type parameters that are used in languages such as Visual Basic and C#.</span></span> <span data-ttu-id="8554b-162">另一種類型參數則專屬於 F#，稱為「以統計方式解析的類型參數」。</span><span class="sxs-lookup"><span data-stu-id="8554b-162">Another kind of type parameter is specific to F# and is referred to as a *statically resolved type parameter*.</span></span> <span data-ttu-id="8554b-163">如需這類建構的資訊，請參閱[以統計方式解析的類型參數](statically-resolved-type-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="8554b-163">For information about these constructs, see [Statically Resolved Type Parameters](statically-resolved-type-parameters.md).</span></span>

## <a name="examples"></a><span data-ttu-id="8554b-164">範例</span><span class="sxs-lookup"><span data-stu-id="8554b-164">Examples</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1705.fs)]

## <a name="see-also"></a><span data-ttu-id="8554b-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8554b-165">See also</span></span>

- [<span data-ttu-id="8554b-166">語言參考</span><span class="sxs-lookup"><span data-stu-id="8554b-166">Language Reference</span></span>](../index.md)
- [<span data-ttu-id="8554b-167">型別</span><span class="sxs-lookup"><span data-stu-id="8554b-167">Types</span></span>](../fsharp-types.md)
- [<span data-ttu-id="8554b-168">以統計方式解析的類型參數</span><span class="sxs-lookup"><span data-stu-id="8554b-168">Statically Resolved Type Parameters</span></span>](statically-resolved-type-parameters.md)
- [<span data-ttu-id="8554b-169">.NET Framework 中的泛型</span><span class="sxs-lookup"><span data-stu-id="8554b-169">Generics in the .NET Framework</span></span>](~/docs/standard/generics/index.md)
- [<span data-ttu-id="8554b-170">自動一般化</span><span class="sxs-lookup"><span data-stu-id="8554b-170">Automatic Generalization</span></span>](automatic-generalization.md)
- [<span data-ttu-id="8554b-171">條件約束</span><span class="sxs-lookup"><span data-stu-id="8554b-171">Constraints</span></span>](constraints.md)
