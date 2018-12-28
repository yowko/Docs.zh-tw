---
title: F#程式碼格式化方針
description: 了解格式的指導方針F#程式碼。
ms.date: 11/26/2018
ms.openlocfilehash: e8e0af2ebffd0e2f3720896bf710961afa11e7bd
ms.sourcegitcommit: 49af435bfdd41faf26d38c20c5b0cc07e87bea60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53396821"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="bbe89-103">F#程式碼格式化方針</span><span class="sxs-lookup"><span data-stu-id="bbe89-103">F# code formatting guidelines</span></span>

<span data-ttu-id="bbe89-104">這篇文章提供如何格式化您的程式碼的指導方針，讓您F#的程式碼：</span><span class="sxs-lookup"><span data-stu-id="bbe89-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="bbe89-105">通常視為更易於閱讀</span><span class="sxs-lookup"><span data-stu-id="bbe89-105">Generally viewed as more legible</span></span>
* <span data-ttu-id="bbe89-106">會根據套用在 Visual Studio 中的工具和其他的編輯器格式設定慣例</span><span class="sxs-lookup"><span data-stu-id="bbe89-106">Is in accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="bbe89-107">類似於線上的其他程式碼</span><span class="sxs-lookup"><span data-stu-id="bbe89-107">Similar to other code online</span></span>

<span data-ttu-id="bbe89-108">這些指導方針根據[的完整指南F#格式設定慣例](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md)所[Anh phan （英文)](https://github.com/dungpa)。</span><span class="sxs-lookup"><span data-stu-id="bbe89-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="bbe89-109">縮排的一般規則</span><span class="sxs-lookup"><span data-stu-id="bbe89-109">General rules for indentation</span></span>

<span data-ttu-id="bbe89-110">F#預設會使用顯著泛空白字元。</span><span class="sxs-lookup"><span data-stu-id="bbe89-110">F# uses significant white space by default.</span></span> <span data-ttu-id="bbe89-111">下列指導方針的用意在於提供指引來選擇要掌握這造成一些挑戰。</span><span class="sxs-lookup"><span data-stu-id="bbe89-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="bbe89-112">使用空間</span><span class="sxs-lookup"><span data-stu-id="bbe89-112">Using spaces</span></span>

<span data-ttu-id="bbe89-113">需要縮排時，您必須使用空格，而不是索引標籤。</span><span class="sxs-lookup"><span data-stu-id="bbe89-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="bbe89-114">需要至少一個空白字元。</span><span class="sxs-lookup"><span data-stu-id="bbe89-114">At least one space is required.</span></span> <span data-ttu-id="bbe89-115">您的組織可以建立以指定要用來縮排; 的空格數目的程式碼撰寫標準通常會發生縮排每個層級的縮排的兩個、 三個或四個空格。</span><span class="sxs-lookup"><span data-stu-id="bbe89-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="bbe89-116">**我們建議每個縮排的 4 個空格。**</span><span class="sxs-lookup"><span data-stu-id="bbe89-116">**We recommend 4 spaces per indentation.**</span></span>

<span data-ttu-id="bbe89-117">話雖如此，程式的縮排是主觀的問題而已。</span><span class="sxs-lookup"><span data-stu-id="bbe89-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="bbe89-118">變化都沒問題，但您應該遵循的第一個規則*縮排的一致性*。</span><span class="sxs-lookup"><span data-stu-id="bbe89-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="bbe89-119">選擇通常可接受的縮排樣式，並在整個程式碼基底有系統地使用它。</span><span class="sxs-lookup"><span data-stu-id="bbe89-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-white-space"></a><span data-ttu-id="bbe89-120">格式化的泛空白字元</span><span class="sxs-lookup"><span data-stu-id="bbe89-120">Formatting white space</span></span>

<span data-ttu-id="bbe89-121">F#是機密的泛空白字元。</span><span class="sxs-lookup"><span data-stu-id="bbe89-121">F# is white space sensitive.</span></span> <span data-ttu-id="bbe89-122">雖然大部分的語意，空白字元係由其適當縮排，有一些其他考量事項。</span><span class="sxs-lookup"><span data-stu-id="bbe89-122">Although most semantics from white space are covered by proper indentation, there are some other things to consider.</span></span>

### <a name="formatting-operators-in-arithmetic-expressions"></a><span data-ttu-id="bbe89-123">設定格式化的算術運算式中的運算子</span><span class="sxs-lookup"><span data-stu-id="bbe89-123">Formatting operators in arithmetic expressions</span></span>

<span data-ttu-id="bbe89-124">一律使用二進位算術運算式周圍的空白字元：</span><span class="sxs-lookup"><span data-stu-id="bbe89-124">Always use white space around binary arithmetic expressions:</span></span>

```fsharp
let subtractThenAdd x = x - 1 + 3
```

<span data-ttu-id="bbe89-125">一元`-`運算子應一律具有的值，它們會否定緊接：</span><span class="sxs-lookup"><span data-stu-id="bbe89-125">Unary `-` operators should always have the value they are negating immediately follow:</span></span>

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

<span data-ttu-id="bbe89-126">新增之後的空格字元`-`運算子可能會導致其他人的混淆。</span><span class="sxs-lookup"><span data-stu-id="bbe89-126">Adding a white-space character after the `-` operator can lead to confusion for others.</span></span>

<span data-ttu-id="bbe89-127">總而言之，務必一律：</span><span class="sxs-lookup"><span data-stu-id="bbe89-127">In summary, it's important to always:</span></span>

* <span data-ttu-id="bbe89-128">範圍陳述式以空白字元的二元運算子</span><span class="sxs-lookup"><span data-stu-id="bbe89-128">Surround binary operators with white space</span></span>
* <span data-ttu-id="bbe89-129">永遠不會將尾端空白之後的一元運算子</span><span class="sxs-lookup"><span data-stu-id="bbe89-129">Never have trailing white space after a unary operator</span></span>

<span data-ttu-id="bbe89-130">二進位的算術運算子的指導方針是特別重要。</span><span class="sxs-lookup"><span data-stu-id="bbe89-130">The binary arithmetic operator guideline is especially important.</span></span> <span data-ttu-id="bbe89-131">失敗來括住二進位`-`運算子，以特定格式設定的選項組合時可能會導致解譯為一元`-`。</span><span class="sxs-lookup"><span data-stu-id="bbe89-131">Failing to surround a binary `-` operator, when combined with certain formatting choices, could lead to interpreting it as a unary `-`.</span></span>

### <a name="surround-a-custom-operator-definition-with-white-space"></a><span data-ttu-id="bbe89-132">括住空白字元的自訂運算子定義</span><span class="sxs-lookup"><span data-stu-id="bbe89-132">Surround a custom operator definition with white space</span></span>

<span data-ttu-id="bbe89-133">一律使用泛空白字元來括住運算子定義：</span><span class="sxs-lookup"><span data-stu-id="bbe89-133">Always use white space to surround an operator definition:</span></span>

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

<span data-ttu-id="bbe89-134">開始任何自訂運算子`*`，您必須定義，以避免編譯器模稜兩可的開頭加入泛空白字元。</span><span class="sxs-lookup"><span data-stu-id="bbe89-134">For any custom operator that starts with `*`, you'll need to add a white space to the beginning of the definition to avoid a compiler ambiguity.</span></span> <span data-ttu-id="bbe89-135">因為這個緣故，建議您只需括住的所有運算子以單一空格字元定義。</span><span class="sxs-lookup"><span data-stu-id="bbe89-135">Because of this, it's recommended that you simply surround the definitions of all operators with a single white-space character.</span></span>

### <a name="surround-function-parameter-arrows-with-white-space"></a><span data-ttu-id="bbe89-136">括住函式參數的箭號以空白字元</span><span class="sxs-lookup"><span data-stu-id="bbe89-136">Surround function parameter arrows with white space</span></span>

<span data-ttu-id="bbe89-137">在定義的函式簽章時，使用周圍的空白`->`符號：</span><span class="sxs-lookup"><span data-stu-id="bbe89-137">When defining the signature of a function, use white space around the `->` symbol:</span></span>

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

## <a name="formatting-blank-lines"></a><span data-ttu-id="bbe89-138">格式化的空白行</span><span class="sxs-lookup"><span data-stu-id="bbe89-138">Formatting blank lines</span></span>

* <span data-ttu-id="bbe89-139">另一個最上層函式和類別定義兩個空白的行。</span><span class="sxs-lookup"><span data-stu-id="bbe89-139">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="bbe89-140">在類別內的方法定義是以單一的空白行分隔。</span><span class="sxs-lookup"><span data-stu-id="bbe89-140">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="bbe89-141">額外的空白的行可能會用來分隔組相關的函式的 （謹慎使用）。</span><span class="sxs-lookup"><span data-stu-id="bbe89-141">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="bbe89-142">一大堆相關單行 （比方說，一組虛擬實作） 之間，可能會省略空白的行。</span><span class="sxs-lookup"><span data-stu-id="bbe89-142">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="bbe89-143">使用空白列在函式，盡量節制，來指出邏輯區段。</span><span class="sxs-lookup"><span data-stu-id="bbe89-143">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="bbe89-144">格式化註解</span><span class="sxs-lookup"><span data-stu-id="bbe89-144">Formatting comments</span></span>

<span data-ttu-id="bbe89-145">通常不用 ML 樣式區塊註解的多個雙斜線註解。</span><span class="sxs-lookup"><span data-stu-id="bbe89-145">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="bbe89-146">第一個字母時，應大寫內嵌註解。</span><span class="sxs-lookup"><span data-stu-id="bbe89-146">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="bbe89-147">命名規範</span><span class="sxs-lookup"><span data-stu-id="bbe89-147">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="bbe89-148">使用 camelCase 類別繫結、 繫結運算式和模式繫結的值和函式</span><span class="sxs-lookup"><span data-stu-id="bbe89-148">Use camelCase for class-bound, expression-bound and pattern-bound values and functions</span></span>

<span data-ttu-id="bbe89-149">它很常見而且可接受F#使用 camelCase 的所有名稱繫結為本機變數，或在模式比對，而函式定義的樣式。</span><span class="sxs-lookup"><span data-stu-id="bbe89-149">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="bbe89-150">本機繫結類別中的函式也應該使用 camelCase。</span><span class="sxs-lookup"><span data-stu-id="bbe89-150">Locally-bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="bbe89-151">針對模組繫結的公用函式使用 camelCase</span><span class="sxs-lookup"><span data-stu-id="bbe89-151">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="bbe89-152">當模組繫結函式是公用 API 的一部分時，它應該使用 camelCase:</span><span class="sxs-lookup"><span data-stu-id="bbe89-152">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="bbe89-153">使用 camelCase 的內部與私用模組繫結值和函式</span><span class="sxs-lookup"><span data-stu-id="bbe89-153">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="bbe89-154">使用 camelCase 的私用模組繫結值，包括下列：</span><span class="sxs-lookup"><span data-stu-id="bbe89-154">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="bbe89-155">在指令碼中的特定函式</span><span class="sxs-lookup"><span data-stu-id="bbe89-155">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="bbe89-156">組成模組或類型的內部實作的值</span><span class="sxs-lookup"><span data-stu-id="bbe89-156">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="bbe89-157">針對參數使用 camelCase</span><span class="sxs-lookup"><span data-stu-id="bbe89-157">Use camelCase for parameters</span></span>

<span data-ttu-id="bbe89-158">所有參數都應該都使用 camelCase 根據.NET 命名慣例。</span><span class="sxs-lookup"><span data-stu-id="bbe89-158">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="bbe89-159">使用 PascalCase 的模組</span><span class="sxs-lookup"><span data-stu-id="bbe89-159">Use PascalCase for modules</span></span>

<span data-ttu-id="bbe89-160">（最上層、 內部、 私用、 巢狀） 的所有模組都應該都使用 PascalCase。</span><span class="sxs-lookup"><span data-stu-id="bbe89-160">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="bbe89-161">使用 PascalCase 的型別宣告、 成員和標籤</span><span class="sxs-lookup"><span data-stu-id="bbe89-161">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="bbe89-162">類別、 介面、 結構、 列舉、 委派、 記錄和差別聯的集全部命名為使用 PascalCase。</span><span class="sxs-lookup"><span data-stu-id="bbe89-162">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="bbe89-163">型別和用於記錄和差別聯的集的標籤內的成員也應該使用 PascalCase。</span><span class="sxs-lookup"><span data-stu-id="bbe89-163">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

```fsharp
type IMyInterface =
    abstract Something: int

type MyClass() =
    member this.MyMethod(x, y) = x + y

type MyRecord = { IntVal: int; StringVal: string }

type SchoolPerson =
    | Professor
    | Student
    | Advisor
    | Administrator
```

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="bbe89-164">適用於.NET 內建函式建構的使用 PascalCase</span><span class="sxs-lookup"><span data-stu-id="bbe89-164">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="bbe89-165">命名空間、 例外狀況、 事件和專案 /`.dll`名稱也應該使用 PascalCase。</span><span class="sxs-lookup"><span data-stu-id="bbe89-165">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="bbe89-166">不只這樣清楚感受更自然的取用者從其他.NET 語言使用，也是配合您可能會遇到的.NET 命名慣例。</span><span class="sxs-lookup"><span data-stu-id="bbe89-166">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="bbe89-167">避免在名稱中的底線</span><span class="sxs-lookup"><span data-stu-id="bbe89-167">Avoid underscores in names</span></span>

<span data-ttu-id="bbe89-168">在過去，某些F#程式庫名稱中使用底線。</span><span class="sxs-lookup"><span data-stu-id="bbe89-168">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="bbe89-169">不過，這是不會再被廣泛接受，這是因為它與.NET 命名慣例衝突。</span><span class="sxs-lookup"><span data-stu-id="bbe89-169">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="bbe89-170">話雖如此，一些F#程式設計人員使用底線大量、 部分基於歷史原因，並容錯] 和 [方面很重要。</span><span class="sxs-lookup"><span data-stu-id="bbe89-170">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="bbe89-171">不過，請注意樣式通常會不喜歡的人可以選擇要使用它。</span><span class="sxs-lookup"><span data-stu-id="bbe89-171">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="bbe89-172">某些例外狀況包含間的互通性與原生元件，其中底線很常見。</span><span class="sxs-lookup"><span data-stu-id="bbe89-172">Some exceptions includes interoperating with native components, where underscores are very common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="bbe89-173">使用標準F#運算子</span><span class="sxs-lookup"><span data-stu-id="bbe89-173">Use standard F# operators</span></span>

<span data-ttu-id="bbe89-174">在定義了下列運算子F#標準程式庫，應使用而不是定義對等項目。</span><span class="sxs-lookup"><span data-stu-id="bbe89-174">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="bbe89-175">因為它會使程式碼，更容易理解且慣用語，建議使用這些運算子。</span><span class="sxs-lookup"><span data-stu-id="bbe89-175">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="bbe89-176">具有背景的 OCaml 或其他功能的程式設計語言的開發人員可能習慣將不同的習慣用語。</span><span class="sxs-lookup"><span data-stu-id="bbe89-176">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="bbe89-177">下列清單摘要說明建議F#運算子。</span><span class="sxs-lookup"><span data-stu-id="bbe89-177">The following list summarizes the recommended F# operators.</span></span>

```fsharp
x |> f // Forward pipeline
f >> g // Forward composition
x |> ignore // Discard away a value
x + y // Overloaded addition (including string concatenation)
x - y // Overloaded subtraction
x * y // Overloaded multiplication
x / y // Overloaded division
x % y // Overloaded modulus
x && y // Lazy/short-cut "and"
x || y // Lazy/short-cut "or"
x <<< y // Bitwise left shift
x >>> y // Bitwise right shift
x ||| y // Bitwise or, also for working with “flags” enumeration
x &&& y // Bitwise and, also for working with “flags” enumeration
x ^^^ y // Bitwise xor, also for working with “flags” enumeration
```

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="bbe89-178">使用泛型的前置詞的語法 (`Foo<T>`) 而非後置語法 (`T Foo`)</span><span class="sxs-lookup"><span data-stu-id="bbe89-178">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="bbe89-179">F#繼承這兩個後置 ML 的樣式命名泛型型別 (例如`int list`) 以及.NET 樣式的前置詞 (例如`list<int>`)。</span><span class="sxs-lookup"><span data-stu-id="bbe89-179">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="bbe89-180">偏好的.NET 樣式，除了特定的四種類型：</span><span class="sxs-lookup"><span data-stu-id="bbe89-180">Prefer the .NET style, except for four specific types:</span></span>

1. <span data-ttu-id="bbe89-181">針對F#清單中，使用後置格式：`int list`而非`list<int>`。</span><span class="sxs-lookup"><span data-stu-id="bbe89-181">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="bbe89-182">針對F#選項，請使用後置格式：`int option`而非`option<int>`。</span><span class="sxs-lookup"><span data-stu-id="bbe89-182">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="bbe89-183">針對F#陣列，請使用語法的名稱`int[]`而非`int array`或是`array<int>`。</span><span class="sxs-lookup"><span data-stu-id="bbe89-183">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
4. <span data-ttu-id="bbe89-184">參考儲存格，使用`int ref`而非`ref<int>`或`Ref<int>`。</span><span class="sxs-lookup"><span data-stu-id="bbe89-184">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="bbe89-185">對於所有其他類型，使用前置詞的表單。</span><span class="sxs-lookup"><span data-stu-id="bbe89-185">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="bbe89-186">格式化的 tuple</span><span class="sxs-lookup"><span data-stu-id="bbe89-186">Formatting tuples</span></span>

<span data-ttu-id="bbe89-187">Tuple 的具現化應該是括號括住，而且中分隔的逗號後面必須接著一個空格，例如： `(1, 2)`， `(x, y, z)`。</span><span class="sxs-lookup"><span data-stu-id="bbe89-187">A tuple instantiation should be parenthesized, and the delimiting commas within should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="bbe89-188">通常可接受省略括號中的 tuple 模式比對：</span><span class="sxs-lookup"><span data-stu-id="bbe89-188">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="bbe89-189">設定格式化的差別等位宣告</span><span class="sxs-lookup"><span data-stu-id="bbe89-189">Formatting discriminated union declarations</span></span>

<span data-ttu-id="bbe89-190">縮排`|`由 4 個空格的型別定義中：</span><span class="sxs-lookup"><span data-stu-id="bbe89-190">Indent `|` in type definition by 4 spaces:</span></span>

```fsharp
// OK
type Volume =
    | Liter of float
    | FluidOunce of float
    | ImperialPint of float

// Not OK
type Volume =
| Liter of float
| USPint of float
| ImperialPint of float
```

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="bbe89-191">格式化差別聯集</span><span class="sxs-lookup"><span data-stu-id="bbe89-191">Formatting discriminated unions</span></span>

<span data-ttu-id="bbe89-192">具現化差別聯集分割成多行，應該會產生包含的資料附縮排新的範圍：</span><span class="sxs-lookup"><span data-stu-id="bbe89-192">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="bbe89-193">右括號也可以在新的一行：</span><span class="sxs-lookup"><span data-stu-id="bbe89-193">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="bbe89-194">格式設定記錄的宣告</span><span class="sxs-lookup"><span data-stu-id="bbe89-194">Formatting record declarations</span></span>

<span data-ttu-id="bbe89-195">縮排`{`在類型定義由 4 空間，開始在同一行上的 [欄位] 清單：</span><span class="sxs-lookup"><span data-stu-id="bbe89-195">Indent `{` in type definition by 4 spaces and start the field list on the same line:</span></span>

```fsharp
// OK
type PostalAddress =
    { Address: string
      City: string
      Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

// Not OK
type PostalAddress =
  { Address: string
    City: string
    Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City
    
// Unusual in F#
type PostalAddress =
    { 
        Address: string
        City: string
        Zip: string
    }
```

<span data-ttu-id="bbe89-196">在新行和結尾語彙基元，在新行上的放置的左語彙基元是下班時間，如果您在記錄上宣告的介面實作或成員：</span><span class="sxs-lookup"><span data-stu-id="bbe89-196">Placing the opening token on a new line and the closing token on a new line is preferrable if you are declaring interface implementations or members on the record:</span></span>

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    { 
        Address: string
        City: string
        Zip: string
    } with
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City
    
type MyRecord =
    {
        SomeField : int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a><span data-ttu-id="bbe89-197">格式化的記錄</span><span class="sxs-lookup"><span data-stu-id="bbe89-197">Formatting records</span></span>

<span data-ttu-id="bbe89-198">可以在同一行撰寫簡短的記錄：</span><span class="sxs-lookup"><span data-stu-id="bbe89-198">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="bbe89-199">較長的記錄應該使用新行標籤：</span><span class="sxs-lookup"><span data-stu-id="bbe89-199">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="bbe89-200">放置開頭索引標籤式的語彙基元的新行上，內容一段範圍內，，並在新的一行的結尾語彙基元是下班時間，如果您是：</span><span class="sxs-lookup"><span data-stu-id="bbe89-200">Placing the opening token on a new line, the contents tabbed over one scope, and the closing token on a new line is preferrable if you are:</span></span>

* <span data-ttu-id="bbe89-201">在不同的縮排的領域的程式碼中四處移動記錄</span><span class="sxs-lookup"><span data-stu-id="bbe89-201">Moving records around in code with different indentation scopes</span></span>
* <span data-ttu-id="bbe89-202">將它們傳送到函式</span><span class="sxs-lookup"><span data-stu-id="bbe89-202">Piping them into a function</span></span>

```fsharp
let rainbow =
    {
        Boss1 = "Jeffrey"
        Boss2 = "Jeffrey"
        Boss3 = "Jeffrey"
        Boss4 = "Jeffrey"
        Boss5 = "Jeffrey"
        Boss6 = "Jeffrey"
        Boss7 = "Jeffrey"
        Boss8 = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"]
    }
    
type MyRecord =
    {
        SomeField : int
    }
    interface IMyInterface

let foo a =
    a
    |> Option.map (fun x ->
        {
            MyField = x
        })
```

<span data-ttu-id="bbe89-203">相同的規則適用於清單和陣列的項目。</span><span class="sxs-lookup"><span data-stu-id="bbe89-203">The same rules apply for list and array elements.</span></span>

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="bbe89-204">格式化的清單和陣列</span><span class="sxs-lookup"><span data-stu-id="bbe89-204">Formatting lists and arrays</span></span>

<span data-ttu-id="bbe89-205">撰寫`x :: l`與前後的空格`::`運算子 (`::`是中置運算子，因此括住空格)。</span><span class="sxs-lookup"><span data-stu-id="bbe89-205">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces).</span></span>

<span data-ttu-id="bbe89-206">清單和陣列宣告在單行上應該有空格之後的左括弧和右括弧之前：</span><span class="sxs-lookup"><span data-stu-id="bbe89-206">List and arrays declared on a single line should have a space after the opening bracket and before the closing bracket:</span></span>

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

<span data-ttu-id="bbe89-207">一律使用兩個不同的大括號類似運算子之間的至少一個空白字元。</span><span class="sxs-lookup"><span data-stu-id="bbe89-207">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="bbe89-208">例如，將保留之間保留一個空格`[`和`{`。</span><span class="sxs-lookup"><span data-stu-id="bbe89-208">For example, leave a space between a `[` and a `{`.</span></span>

```fsharp
// OK
[ { IngredientName = "Green beans"; Quantity = 250 }
  { IngredientName = "Pine nuts"; Quantity = 250 }
  { IngredientName = "Feta cheese"; Quantity = 250 }
  { IngredientName = "Olive oil"; Quantity = 10 }
  { IngredientName = "Lemon"; Quantity = 1 } ]

// Not OK
[{ IngredientName = "Green beans"; Quantity = 250 }
 { IngredientName = "Pine nuts"; Quantity = 250 }
 { IngredientName = "Feta cheese"; Quantity = 250 }
 { IngredientName = "Olive oil"; Quantity = 10 }
 { IngredientName = "Lemon"; Quantity = 1 }]
```

<span data-ttu-id="bbe89-209">相同的指導方針適用於清單或陣列的 tuple。</span><span class="sxs-lookup"><span data-stu-id="bbe89-209">The same guideline applies for lists or arrays of tuples.</span></span>

<span data-ttu-id="bbe89-210">清單和陣列分成多行，請遵循類似的規則記錄也一樣：</span><span class="sxs-lookup"><span data-stu-id="bbe89-210">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

```fsharp
let pascalsTriangle =
    [|
        [| 1 |]
        [| 1; 1 |]
        [| 1; 2; 1 |]
        [| 1; 3; 3; 1 |]
        [| 1; 4; 6; 4; 1 |]
        [| 1; 5; 10; 10; 5; 1 |]
        [| 1; 6; 15; 20; 15; 6; 1 |]
        [| 1; 7; 21; 35; 35; 21; 7; 1 |]
        [| 1; 8; 28; 56; 70; 56; 28; 8; 1 |]
    |]
```

<span data-ttu-id="bbe89-211">如同記錄，在各自的行上宣告的開頭和結尾括號會簡化移動程式碼的位置和管線執行函式。</span><span class="sxs-lookup"><span data-stu-id="bbe89-211">And as with records, declaring the opening and closing brackets on their own line will make moving code around and piping into functions easier.</span></span>

## <a name="formatting-if-expressions"></a><span data-ttu-id="bbe89-212">如果格式運算式</span><span class="sxs-lookup"><span data-stu-id="bbe89-212">Formatting if expressions</span></span>

<span data-ttu-id="bbe89-213">縮排的條件取決於它們構成的運算式的大小。</span><span class="sxs-lookup"><span data-stu-id="bbe89-213">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="bbe89-214">如果`cond`，`e1`和`e2`簡短，只要將它們寫入在同一行：</span><span class="sxs-lookup"><span data-stu-id="bbe89-214">If `cond`, `e1` and `e2` are short, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="bbe89-215">如果有任一`cond`，`e1`或`e2`更久，但不多行：</span><span class="sxs-lookup"><span data-stu-id="bbe89-215">If either `cond`, `e1` or `e2` are longer, but not multi-line:</span></span>

```fsharp
if cond
then e1
else e2
```

<span data-ttu-id="bbe89-216">如果任何運算式是多行：</span><span class="sxs-lookup"><span data-stu-id="bbe89-216">If any of the expressions are multi-line:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="bbe89-217">使用多個條件`elif`並`else`縮排在相同範圍`if`:</span><span class="sxs-lookup"><span data-stu-id="bbe89-217">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="bbe89-218">模式比對建構</span><span class="sxs-lookup"><span data-stu-id="bbe89-218">Pattern matching constructs</span></span>

<span data-ttu-id="bbe89-219">使用`|`不縮排每個子句的相符項目。</span><span class="sxs-lookup"><span data-stu-id="bbe89-219">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="bbe89-220">如果運算式很短，您可以考慮使用單一行，如果每一個子運算式也很簡單。</span><span class="sxs-lookup"><span data-stu-id="bbe89-220">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> x
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> x
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

<span data-ttu-id="bbe89-221">如果在模式比對的箭號右側的運算式太大，將它移至下列這一行，縮排的一個步驟，從`match` / `|`。</span><span class="sxs-lookup"><span data-stu-id="bbe89-221">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="bbe89-222">模式比對的匿名函式，來啟動`function`，應該通常不縮排牽扯太廣。</span><span class="sxs-lookup"><span data-stu-id="bbe89-222">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="bbe89-223">例如，縮排一個範圍，如下所示沒關係：</span><span class="sxs-lookup"><span data-stu-id="bbe89-223">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="bbe89-224">模式比對中所定義的函式`let`或是`let rec`之後開始進行縮排的 4 個空格`let`，即使`function`關鍵字可用於：</span><span class="sxs-lookup"><span data-stu-id="bbe89-224">Pattern matching in functions defined by `let` or `let rec` should be indented 4 spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="bbe89-225">我們不建議對齊箭號。</span><span class="sxs-lookup"><span data-stu-id="bbe89-225">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="bbe89-226">格式化的 try / with 運算式</span><span class="sxs-lookup"><span data-stu-id="bbe89-226">Formatting try/with expressions</span></span>

<span data-ttu-id="bbe89-227">模式比對的例外狀況類型應位於相同層級會縮排`with`。</span><span class="sxs-lookup"><span data-stu-id="bbe89-227">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

```fsharp
try
    if System.DateTime.Now.Second % 3 = 0 then
        raise (new System.Exception())
    else
        raise (new System.ApplicationException())
with
| :? System.ApplicationException ->
    printfn "A second that was not a multiple of 3"
| _ ->
    printfn "A second that was a multiple of 3"
```

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="bbe89-228">格式函式參數的應用程式</span><span class="sxs-lookup"><span data-stu-id="bbe89-228">Formatting function parameter application</span></span>

<span data-ttu-id="bbe89-229">一般而言，大部分函式參數的應用程式是在同一行。</span><span class="sxs-lookup"><span data-stu-id="bbe89-229">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="bbe89-230">如果您想要套用至新的一行中的函式的參數，則由一個範圍縮排。</span><span class="sxs-lookup"><span data-stu-id="bbe89-230">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

```fsharp
// OK
sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
sprintf
     "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
let printVolumes x =
    printf "Volume in liters = %f, in us pints = %f, in imperial = %f"
        (convertVolumeToLiter x)
        (convertVolumeUSPint x)
        (convertVolumeImperialPint x)
```

<span data-ttu-id="bbe89-231">函式引數的 lambda 運算式套用相同的指導方針。</span><span class="sxs-lookup"><span data-stu-id="bbe89-231">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="bbe89-232">如果 lambda 運算式主體的主體可以有另一條，縮排一個範圍</span><span class="sxs-lookup"><span data-stu-id="bbe89-232">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

```fsharp
let printListWithOffset a list1 =
    List.iter
        (fun elem -> printfn "%d" (a + elem))
        list1

// OK if lambda body is long enough
let printListWithOffset a list1 =
    List.iter
        (fun elem ->
            printfn "%d" (a + elem))
        list1
```

<span data-ttu-id="bbe89-233">不過，如果多行 lambda 運算式的主體，請考慮一下重構到個別函式而非已做為單一引數套用至函式的多行建構。</span><span class="sxs-lookup"><span data-stu-id="bbe89-233">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="bbe89-234">格式化 中置運算子</span><span class="sxs-lookup"><span data-stu-id="bbe89-234">Formatting infix operators</span></span>

<span data-ttu-id="bbe89-235">以空格分開的運算子。</span><span class="sxs-lookup"><span data-stu-id="bbe89-235">Separate operators by spaces.</span></span> <span data-ttu-id="bbe89-236">明顯的例外狀況，此規則會`!`和`.`運算子。</span><span class="sxs-lookup"><span data-stu-id="bbe89-236">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="bbe89-237">中置運算式會為同一個資料行的組合中的 [確定]:</span><span class="sxs-lookup"><span data-stu-id="bbe89-237">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="bbe89-238">格式設定管線運算子</span><span class="sxs-lookup"><span data-stu-id="bbe89-238">Formatting pipeline operators</span></span>

<span data-ttu-id="bbe89-239">管線`|>`運算子都應下它們對的運算式。</span><span class="sxs-lookup"><span data-stu-id="bbe89-239">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

```fsharp
// Preferred approach
let methods2 =
    System.AppDomain.CurrentDomain.GetAssemblies()
    |> List.ofArray
    |> List.map (fun assm -> assm.GetTypes())
    |> Array.concat
    |> List.ofArray
    |> List.map (fun t -> t.GetMethods())
    |> Array.concat

// Not OK
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
            |> List.ofArray
            |> List.map (fun assm -> assm.GetTypes())
            |> Array.concat
            |> List.ofArray
            |> List.map (fun t -> t.GetMethods())
            |> Array.concat
```

### <a name="formatting-modules"></a><span data-ttu-id="bbe89-240">格式化的模組</span><span class="sxs-lookup"><span data-stu-id="bbe89-240">Formatting modules</span></span>

<span data-ttu-id="bbe89-241">在本機的模組中的程式碼必須相對於模組，縮排，但應該不會縮排在最上層模組中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="bbe89-241">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="bbe89-242">縮排沒有命名空間項目。</span><span class="sxs-lookup"><span data-stu-id="bbe89-242">Namespace elements do not have to be indented.</span></span>

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a*a + b*b

module A2 =
    let function2 a b = a*a - b*b
```

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="bbe89-243">格式化的物件運算式和介面</span><span class="sxs-lookup"><span data-stu-id="bbe89-243">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="bbe89-244">物件運算式和介面應該使用相同的方式對齊`member`正在後 4 個空格縮排。</span><span class="sxs-lookup"><span data-stu-id="bbe89-244">Object expressions and interfaces should be aligned in the same way with `member` being indented after 4 spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s : String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="bbe89-245">設定格式化的運算式中的泛空白字元</span><span class="sxs-lookup"><span data-stu-id="bbe89-245">Formatting white space in expressions</span></span>

<span data-ttu-id="bbe89-246">避免多餘的泛空白字元，在F#運算式。</span><span class="sxs-lookup"><span data-stu-id="bbe89-246">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="bbe89-247">具名引數也不應該周圍的空間`=`:</span><span class="sxs-lookup"><span data-stu-id="bbe89-247">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a><span data-ttu-id="bbe89-248">格式化屬性</span><span class="sxs-lookup"><span data-stu-id="bbe89-248">Formatting attributes</span></span>

<span data-ttu-id="bbe89-249">[屬性](../language-reference/attributes.md)位於上述建構：</span><span class="sxs-lookup"><span data-stu-id="bbe89-249">[Attributes](../language-reference/attributes.md) are placed above a construct:</span></span>

```fsharp
[<SomeAttribute>]
type MyClass() = ...

[<RequireQualifiedAccess>]
module M =
    let f x = x

[<Struct>]
type MyRecord =
    { Label1: int
      Label2: string }
```

### <a name="formatting-attributes-on-parameters"></a><span data-ttu-id="bbe89-250">參數的格式化屬性</span><span class="sxs-lookup"><span data-stu-id="bbe89-250">Formatting attributes on parameters</span></span>

<span data-ttu-id="bbe89-251">屬性也可以在參數上的位置。</span><span class="sxs-lookup"><span data-stu-id="bbe89-251">Attributes can also be places on parameters.</span></span> <span data-ttu-id="bbe89-252">在此情況下，將再置於相同的行做為參數，並在名稱前面：</span><span class="sxs-lookup"><span data-stu-id="bbe89-252">In this case, place then on the same line as the parameter and before the name:</span></span>

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member __.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a><span data-ttu-id="bbe89-253">格式化多個屬性</span><span class="sxs-lookup"><span data-stu-id="bbe89-253">Formatting multiple attributes</span></span>

<span data-ttu-id="bbe89-254">當多個屬性會套用至不是參數的建構時，它們應該放使得每行一個屬性：</span><span class="sxs-lookup"><span data-stu-id="bbe89-254">When multiple attributes are applied to a construct that is not a parameter, they should be placed such that there is one attribute per line:</span></span>

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

<span data-ttu-id="bbe89-255">套用至參數時，則它們必須在同一行中，以分隔`;`分隔符號。</span><span class="sxs-lookup"><span data-stu-id="bbe89-255">When applied to a parameter, they must be on the same line and separated by a `;` separator.</span></span>

## <a name="formatting-literals"></a><span data-ttu-id="bbe89-256">格式化常值</span><span class="sxs-lookup"><span data-stu-id="bbe89-256">Formatting literals</span></span>

<span data-ttu-id="bbe89-257">[F#常值](../language-reference/literals.md)使用`Literal`應該將屬性放在它自己的行並使用 camelCase 的命名屬性：</span><span class="sxs-lookup"><span data-stu-id="bbe89-257">[F# literals](../language-reference/literals.md) using the `Literal` attribute should should place the attribute on its own line and use camelCase naming:</span></span>

```fsharp
[<Literal>]
let path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let myUrl = "www.mywebsitethatiamworkingwith.com"
```

<span data-ttu-id="bbe89-258">避免將屬性放在同一行的值。</span><span class="sxs-lookup"><span data-stu-id="bbe89-258">Avoid placing the attribute on the same line as the value.</span></span>
