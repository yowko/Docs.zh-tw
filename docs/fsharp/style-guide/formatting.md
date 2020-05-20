---
title: F# 程式碼格式方針
description: '瞭解格式化 F # 程式碼的指導方針。'
ms.date: 11/04/2019
ms.openlocfilehash: dde69c573f1ef58d398ae47676b9403f588680b6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617265"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="4f73c-103">F# 程式碼格式方針</span><span class="sxs-lookup"><span data-stu-id="4f73c-103">F# code formatting guidelines</span></span>

<span data-ttu-id="4f73c-104">本文提供如何將程式碼格式化的指導方針，讓您的 F # 程式碼為：</span><span class="sxs-lookup"><span data-stu-id="4f73c-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="4f73c-105">更清晰</span><span class="sxs-lookup"><span data-stu-id="4f73c-105">More legible</span></span>
* <span data-ttu-id="4f73c-106">根據 Visual Studio 和其他編輯器中格式化工具所套用的慣例</span><span class="sxs-lookup"><span data-stu-id="4f73c-106">In accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="4f73c-107">類似于線上的其他程式碼</span><span class="sxs-lookup"><span data-stu-id="4f73c-107">Similar to other code online</span></span>

<span data-ttu-id="4f73c-108">這些指導方針是以[Anh-Ahn-dung Phan](https://github.com/dungpa)的[F # 格式化慣例完整指南](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md)為基礎。</span><span class="sxs-lookup"><span data-stu-id="4f73c-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="4f73c-109">縮排的一般規則</span><span class="sxs-lookup"><span data-stu-id="4f73c-109">General rules for indentation</span></span>

<span data-ttu-id="4f73c-110">F # 預設會使用顯著的空白字元。</span><span class="sxs-lookup"><span data-stu-id="4f73c-110">F# uses significant white space by default.</span></span> <span data-ttu-id="4f73c-111">下列指導方針的目的是要提供如何操控這項挑戰的指引。</span><span class="sxs-lookup"><span data-stu-id="4f73c-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="4f73c-112">使用空格</span><span class="sxs-lookup"><span data-stu-id="4f73c-112">Using spaces</span></span>

<span data-ttu-id="4f73c-113">需要縮排時，您必須使用空格，而不是定位字元。</span><span class="sxs-lookup"><span data-stu-id="4f73c-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="4f73c-114">至少需要一個空格。</span><span class="sxs-lookup"><span data-stu-id="4f73c-114">At least one space is required.</span></span> <span data-ttu-id="4f73c-115">您的組織可以建立編碼標準，以指定要用於縮排的空格數目;在縮排發生的每個層級中，兩個、三個或四個空格的縮排是典型的。</span><span class="sxs-lookup"><span data-stu-id="4f73c-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three, or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="4f73c-116">**我們建議每個縮排有四個空格。**</span><span class="sxs-lookup"><span data-stu-id="4f73c-116">**We recommend four spaces per indentation.**</span></span>

<span data-ttu-id="4f73c-117">話雖如此，程式的縮排就是一項主觀上的問題。</span><span class="sxs-lookup"><span data-stu-id="4f73c-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="4f73c-118">變化良好，但您應該遵循的第一個規則是*縮排的一致性*。</span><span class="sxs-lookup"><span data-stu-id="4f73c-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="4f73c-119">選擇一般接受的縮排樣式，並在整個程式碼基底中有系統地使用它。</span><span class="sxs-lookup"><span data-stu-id="4f73c-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-white-space"></a><span data-ttu-id="4f73c-120">格式化空白字元</span><span class="sxs-lookup"><span data-stu-id="4f73c-120">Formatting white space</span></span>

<span data-ttu-id="4f73c-121">F # 是區分空白字元。</span><span class="sxs-lookup"><span data-stu-id="4f73c-121">F# is white space sensitive.</span></span> <span data-ttu-id="4f73c-122">雖然來自空白字元的大部分語法都是由適當的縮排所涵蓋，但還有一些其他事項需要考慮。</span><span class="sxs-lookup"><span data-stu-id="4f73c-122">Although most semantics from white space are covered by proper indentation, there are some other things to consider.</span></span>

### <a name="formatting-operators-in-arithmetic-expressions"></a><span data-ttu-id="4f73c-123">在算術運算式中格式化運算子</span><span class="sxs-lookup"><span data-stu-id="4f73c-123">Formatting operators in arithmetic expressions</span></span>

<span data-ttu-id="4f73c-124">一律在二元算術運算式前後使用空白字元：</span><span class="sxs-lookup"><span data-stu-id="4f73c-124">Always use white space around binary arithmetic expressions:</span></span>

```fsharp
let subtractThenAdd x = x - 1 + 3
```

<span data-ttu-id="4f73c-125">一元 `-` 運算子應一律緊接在其所否定的值後面：</span><span class="sxs-lookup"><span data-stu-id="4f73c-125">Unary `-` operators should always be immediately followed by the value they are negating:</span></span>

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

<span data-ttu-id="4f73c-126">在運算子之後加入空白字元 `-` 可能會讓其他人混淆。</span><span class="sxs-lookup"><span data-stu-id="4f73c-126">Adding a white-space character after the `-` operator can lead to confusion for others.</span></span>

<span data-ttu-id="4f73c-127">總而言之，一定要：</span><span class="sxs-lookup"><span data-stu-id="4f73c-127">In summary, it's important to always:</span></span>

* <span data-ttu-id="4f73c-128">以空白字元括住二元運算子</span><span class="sxs-lookup"><span data-stu-id="4f73c-128">Surround binary operators with white space</span></span>
* <span data-ttu-id="4f73c-129">一元運算子後面絕對不加尾端空白字元</span><span class="sxs-lookup"><span data-stu-id="4f73c-129">Never have trailing white space after a unary operator</span></span>

<span data-ttu-id="4f73c-130">二元算術運算子指導方針特別重要。</span><span class="sxs-lookup"><span data-stu-id="4f73c-130">The binary arithmetic operator guideline is especially important.</span></span> <span data-ttu-id="4f73c-131">無法將二元運算子括住 `-` ，並結合特定的格式化選項時，可能會導致將它解釋為一元 `-` 。</span><span class="sxs-lookup"><span data-stu-id="4f73c-131">Failing to surround a binary `-` operator, when combined with certain formatting choices, could lead to interpreting it as a unary `-`.</span></span>

### <a name="surround-a-custom-operator-definition-with-white-space"></a><span data-ttu-id="4f73c-132">以空白字元括住自訂運算子定義</span><span class="sxs-lookup"><span data-stu-id="4f73c-132">Surround a custom operator definition with white space</span></span>

<span data-ttu-id="4f73c-133">一律使用空白字元來括住運算子定義：</span><span class="sxs-lookup"><span data-stu-id="4f73c-133">Always use white space to surround an operator definition:</span></span>

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

<span data-ttu-id="4f73c-134">對於開頭為 `*` 且具有多個字元的自訂運算子，您必須在定義的開頭加上空白字元，以避免編譯器不明確。</span><span class="sxs-lookup"><span data-stu-id="4f73c-134">For any custom operator that starts with `*` and that has more than one character, you need to add a white space to the beginning of the definition to avoid a compiler ambiguity.</span></span> <span data-ttu-id="4f73c-135">因此，我們建議您只使用單一空白字元來括住所有運算子的定義。</span><span class="sxs-lookup"><span data-stu-id="4f73c-135">Because of this, we recommend that you simply surround the definitions of all operators with a single white-space character.</span></span>

### <a name="surround-function-parameter-arrows-with-white-space"></a><span data-ttu-id="4f73c-136">以空白字元括住函數參數箭號</span><span class="sxs-lookup"><span data-stu-id="4f73c-136">Surround function parameter arrows with white space</span></span>

<span data-ttu-id="4f73c-137">定義函式的簽章時，請使用空格括住 `->` 符號：</span><span class="sxs-lookup"><span data-stu-id="4f73c-137">When defining the signature of a function, use white space around the `->` symbol:</span></span>

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a><span data-ttu-id="4f73c-138">以空白字元括住函數引數</span><span class="sxs-lookup"><span data-stu-id="4f73c-138">Surround function arguments with white space</span></span>

<span data-ttu-id="4f73c-139">定義函式時，請在每個引數前後使用空白字元。</span><span class="sxs-lookup"><span data-stu-id="4f73c-139">When defining a function, use white space around each argument.</span></span>

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="place-parameters-on-a-new-line-for-long-member-definitions"></a><span data-ttu-id="4f73c-140">將參數放在長成員定義的新行上</span><span class="sxs-lookup"><span data-stu-id="4f73c-140">Place parameters on a new line for long member definitions</span></span>

<span data-ttu-id="4f73c-141">如果您有很長的成員定義，請將參數放在新行上，並將其縮排到一個範圍內。</span><span class="sxs-lookup"><span data-stu-id="4f73c-141">If you have a very long member definition, place the parameters on new lines and indent them one scope.</span></span>

```fsharp
type C() =
    member _.LongMethodWithLotsOfParameters(
        aVeryLongType: AVeryLongTypeThatYouNeedToUse
        aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
        aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
        // ... the body of the method follows
```

<span data-ttu-id="4f73c-142">這也適用于函式：</span><span class="sxs-lookup"><span data-stu-id="4f73c-142">This also applies to constructors:</span></span>

```fsharp
type C(
    aVeryLongType: AVeryLongTypeThatYouNeedToUse
    aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
    aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
    // ... the body of the class follows
```

### <a name="type-annotations"></a><span data-ttu-id="4f73c-143">類型注釋</span><span class="sxs-lookup"><span data-stu-id="4f73c-143">Type annotations</span></span>

#### <a name="right-pad-function-argument-type-annotations"></a><span data-ttu-id="4f73c-144">右面板函數引數類型注釋</span><span class="sxs-lookup"><span data-stu-id="4f73c-144">Right-pad function argument type annotations</span></span>

<span data-ttu-id="4f73c-145">定義具有類型注釋的引數時，請在符號後面使用空白字元 `:` ：</span><span class="sxs-lookup"><span data-stu-id="4f73c-145">When defining arguments with type annotations, use white space after the `:` symbol:</span></span>

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a><span data-ttu-id="4f73c-146">以空白字元括住傳回類型注釋</span><span class="sxs-lookup"><span data-stu-id="4f73c-146">Surround return type annotations with white space</span></span>

<span data-ttu-id="4f73c-147">在 let 系結函式或實值型別注釋中（函數的大小寫），使用符號前後的空白字元 `:` ：</span><span class="sxs-lookup"><span data-stu-id="4f73c-147">In a let-bound function or value type annotation (return type in the case of a function), use white space before and after the `:` symbol:</span></span>

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a><span data-ttu-id="4f73c-148">格式化空白行</span><span class="sxs-lookup"><span data-stu-id="4f73c-148">Formatting blank lines</span></span>

* <span data-ttu-id="4f73c-149">以兩個空白行分隔最上層函式和類別定義。</span><span class="sxs-lookup"><span data-stu-id="4f73c-149">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="4f73c-150">類別內的方法定義會以一行分隔。</span><span class="sxs-lookup"><span data-stu-id="4f73c-150">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="4f73c-151">可能會使用額外的空白行（謹慎）來分隔相關函式的群組。</span><span class="sxs-lookup"><span data-stu-id="4f73c-151">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="4f73c-152">在一堆相關的囉（例如，一組虛擬的執行）之間，可能會省略空白行。</span><span class="sxs-lookup"><span data-stu-id="4f73c-152">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="4f73c-153">請謹慎使用函式中的空白行來表示邏輯區段。</span><span class="sxs-lookup"><span data-stu-id="4f73c-153">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="4f73c-154">格式化批註</span><span class="sxs-lookup"><span data-stu-id="4f73c-154">Formatting comments</span></span>

<span data-ttu-id="4f73c-155">通常偏好透過 ML 樣式的區塊批註使用多個雙斜線批註。</span><span class="sxs-lookup"><span data-stu-id="4f73c-155">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="4f73c-156">內嵌批註應為第一個字母大寫。</span><span class="sxs-lookup"><span data-stu-id="4f73c-156">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="4f73c-157">命名慣例</span><span class="sxs-lookup"><span data-stu-id="4f73c-157">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="4f73c-158">針對類別系結、運算式系結和模式系結值和函式使用 camelCase</span><span class="sxs-lookup"><span data-stu-id="4f73c-158">Use camelCase for class-bound, expression-bound, and pattern-bound values and functions</span></span>

<span data-ttu-id="4f73c-159">這是常見且已接受的 F # 樣式，可針對系結為區域變數的所有名稱，或在模式比對和函式定義中使用 camelCase。</span><span class="sxs-lookup"><span data-stu-id="4f73c-159">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="4f73c-160">類別中的本機系結函數也應該使用 camelCase。</span><span class="sxs-lookup"><span data-stu-id="4f73c-160">Locally bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="4f73c-161">針對模組系結的公用函式使用 camelCase</span><span class="sxs-lookup"><span data-stu-id="4f73c-161">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="4f73c-162">當模組系結函式是公用 API 的一部分時，它應該使用 camelCase：</span><span class="sxs-lookup"><span data-stu-id="4f73c-162">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="4f73c-163">將 camelCase 用於內部和私用模組系結的值和函數</span><span class="sxs-lookup"><span data-stu-id="4f73c-163">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="4f73c-164">將 camelCase 用於私用模組系結的值，包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="4f73c-164">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="4f73c-165">腳本中的特定函式</span><span class="sxs-lookup"><span data-stu-id="4f73c-165">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="4f73c-166">組成模組或類型內部執行的值</span><span class="sxs-lookup"><span data-stu-id="4f73c-166">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="4f73c-167">針對參數使用 camelCase</span><span class="sxs-lookup"><span data-stu-id="4f73c-167">Use camelCase for parameters</span></span>

<span data-ttu-id="4f73c-168">所有參數都應該根據 .NET 命名慣例來使用 camelCase。</span><span class="sxs-lookup"><span data-stu-id="4f73c-168">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="4f73c-169">使用模組的 PascalCase</span><span class="sxs-lookup"><span data-stu-id="4f73c-169">Use PascalCase for modules</span></span>

<span data-ttu-id="4f73c-170">所有模組（最上層、內部、私用、嵌套）都應該使用 PascalCase。</span><span class="sxs-lookup"><span data-stu-id="4f73c-170">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="4f73c-171">針對類型宣告、成員和標籤使用 PascalCase</span><span class="sxs-lookup"><span data-stu-id="4f73c-171">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="4f73c-172">類別、介面、結構、列舉、委派、記錄和區分等位都應該使用 PascalCase 來命名。</span><span class="sxs-lookup"><span data-stu-id="4f73c-172">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="4f73c-173">記錄和區分等位的類型和標籤中的成員也應該使用 PascalCase。</span><span class="sxs-lookup"><span data-stu-id="4f73c-173">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="4f73c-174">將 PascalCase 用於 .NET 的內部結構</span><span class="sxs-lookup"><span data-stu-id="4f73c-174">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="4f73c-175">命名空間、例外狀況、事件和專案/ `.dll` 名稱也應該使用 PascalCase。</span><span class="sxs-lookup"><span data-stu-id="4f73c-175">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="4f73c-176">這不僅讓其他 .NET 語言的耗用量更自然地取用者，也會與您可能會遇到的 .NET 命名慣例保持一致。</span><span class="sxs-lookup"><span data-stu-id="4f73c-176">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="4f73c-177">避免在名稱中有底線</span><span class="sxs-lookup"><span data-stu-id="4f73c-177">Avoid underscores in names</span></span>

<span data-ttu-id="4f73c-178">在過去，某些 F # 程式庫在名稱中使用了底線。</span><span class="sxs-lookup"><span data-stu-id="4f73c-178">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="4f73c-179">不過，這已不再被廣泛接受，部分是因為它與 .NET 命名慣例衝突。</span><span class="sxs-lookup"><span data-stu-id="4f73c-179">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="4f73c-180">話雖如此，有些 F # 程式設計人員會大量使用底線，部分基於歷史原因，而容錯與尊重則很重要。</span><span class="sxs-lookup"><span data-stu-id="4f73c-180">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="4f73c-181">不過，請注意，樣式通常是由其他可選擇是否要使用它的人所不喜歡的。</span><span class="sxs-lookup"><span data-stu-id="4f73c-181">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="4f73c-182">其中一個例外狀況包括與原生元件互通，其中底線是常見的。</span><span class="sxs-lookup"><span data-stu-id="4f73c-182">One exception includes interoperating with native components, where underscores are common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="4f73c-183">使用標準 F # 運算子</span><span class="sxs-lookup"><span data-stu-id="4f73c-183">Use standard F# operators</span></span>

<span data-ttu-id="4f73c-184">下列運算子定義于 F # 標準程式庫中，而且應該使用，而不是定義對等專案。</span><span class="sxs-lookup"><span data-stu-id="4f73c-184">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="4f73c-185">建議使用這些運算子，因為它可能會讓程式碼更容易閱讀和慣用。</span><span class="sxs-lookup"><span data-stu-id="4f73c-185">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="4f73c-186">具有 OCaml 或其他功能性程式設計語言背景的開發人員，可能會習慣不同的慣用語。</span><span class="sxs-lookup"><span data-stu-id="4f73c-186">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="4f73c-187">下列清單摘要說明建議的 F # 運算子。</span><span class="sxs-lookup"><span data-stu-id="4f73c-187">The following list summarizes the recommended F# operators.</span></span>

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="4f73c-188">在喜好設定中使用泛型（）的前置詞語法做為後置 `Foo<T>` 語法（ `T Foo` ）</span><span class="sxs-lookup"><span data-stu-id="4f73c-188">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="4f73c-189">F # 會同時繼承命名泛型型別（例如）的後置 ML 樣式 `int list` ，以及前置詞 .net 樣式（例如 `list<int>` ）。</span><span class="sxs-lookup"><span data-stu-id="4f73c-189">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="4f73c-190">偏好使用 .NET 樣式，但五個特定類型除外：</span><span class="sxs-lookup"><span data-stu-id="4f73c-190">Prefer the .NET style, except for five specific types:</span></span>

1. <span data-ttu-id="4f73c-191">若是 F # 清單，請使用後置形式：， `int list` 而不是 `list<int>` 。</span><span class="sxs-lookup"><span data-stu-id="4f73c-191">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="4f73c-192">若是 F # 選項，請使用後置形式：， `int option` 而不是 `option<int>` 。</span><span class="sxs-lookup"><span data-stu-id="4f73c-192">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="4f73c-193">對於 F # 值選項，請使用後置形式：， `int voption` 而不是 `voption<int>` 。</span><span class="sxs-lookup"><span data-stu-id="4f73c-193">For F# Value Options, use the postfix form: `int voption` rather than `voption<int>`.</span></span>
4. <span data-ttu-id="4f73c-194">若是 F # 陣列，請使用語法名稱， `int[]` 而不是 `int array` 或 `array<int>` 。</span><span class="sxs-lookup"><span data-stu-id="4f73c-194">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
5. <span data-ttu-id="4f73c-195">如需參考資料格，請使用， `int ref` 而不是 `ref<int>` 或 `Ref<int>` 。</span><span class="sxs-lookup"><span data-stu-id="4f73c-195">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="4f73c-196">若為所有其他類型，請使用前置詞形式。</span><span class="sxs-lookup"><span data-stu-id="4f73c-196">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="4f73c-197">格式化元組</span><span class="sxs-lookup"><span data-stu-id="4f73c-197">Formatting tuples</span></span>

<span data-ttu-id="4f73c-198">元組具現化應以括弧括住，而且其中的分隔逗號後面應該接著一個空格，例如： `(1, 2)` 、 `(x, y, z)` 。</span><span class="sxs-lookup"><span data-stu-id="4f73c-198">A tuple instantiation should be parenthesized, and the delimiting commas within it should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="4f73c-199">在元組的模式比對中，通常會接受省略括弧：</span><span class="sxs-lookup"><span data-stu-id="4f73c-199">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

<span data-ttu-id="4f73c-200">如果元組是函式的傳回值，通常也會被接受省略括弧：</span><span class="sxs-lookup"><span data-stu-id="4f73c-200">It is also commonly accepted to omit parentheses if the tuple is the return value of a function:</span></span>

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

<span data-ttu-id="4f73c-201">總而言之，偏好以括弧括住的元組具現化，但當使用元組進行模式比對或傳回值時，會將它視為可避免括弧的問題。</span><span class="sxs-lookup"><span data-stu-id="4f73c-201">In summary, prefer parenthesized tuple instantiations, but when using tuples for pattern matching or a return value, it is considered fine to avoid parentheses.</span></span>

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="4f73c-202">格式化區分聯集宣告</span><span class="sxs-lookup"><span data-stu-id="4f73c-202">Formatting discriminated union declarations</span></span>

<span data-ttu-id="4f73c-203">`|`在類型定義中以四個空格縮排：</span><span class="sxs-lookup"><span data-stu-id="4f73c-203">Indent `|` in type definition by four spaces:</span></span>

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

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="4f73c-204">格式化區分等位</span><span class="sxs-lookup"><span data-stu-id="4f73c-204">Formatting discriminated unions</span></span>

<span data-ttu-id="4f73c-205">分割成多行的具現化區分等位，應為包含的資料提供具有縮排的新範圍：</span><span class="sxs-lookup"><span data-stu-id="4f73c-205">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="4f73c-206">右括弧也可以在新行上：</span><span class="sxs-lookup"><span data-stu-id="4f73c-206">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="4f73c-207">格式化記錄宣告</span><span class="sxs-lookup"><span data-stu-id="4f73c-207">Formatting record declarations</span></span>

<span data-ttu-id="4f73c-208">`{`在類型定義中以四個空格縮排，並在同一行上啟動欄位清單：</span><span class="sxs-lookup"><span data-stu-id="4f73c-208">Indent `{` in type definition by four spaces and start the field list on the same line:</span></span>

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

<span data-ttu-id="4f73c-209">如果您要在記錄上宣告介面執行或成員，最好將開頭標記放在新行上，並在新行上進行結束記號：</span><span class="sxs-lookup"><span data-stu-id="4f73c-209">Placing the opening token on a new line and the closing token on a new line is preferable if you are declaring interface implementations or members on the record:</span></span>

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a><span data-ttu-id="4f73c-210">格式化記錄</span><span class="sxs-lookup"><span data-stu-id="4f73c-210">Formatting records</span></span>

<span data-ttu-id="4f73c-211">短記錄可以用一行撰寫：</span><span class="sxs-lookup"><span data-stu-id="4f73c-211">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="4f73c-212">較長的記錄應該使用新的標籤行：</span><span class="sxs-lookup"><span data-stu-id="4f73c-212">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="4f73c-213">將開啟的 token 放在新行上，將內容索引標籤在一個範圍內，而在新行上的結束記號則比較適合下列情況：</span><span class="sxs-lookup"><span data-stu-id="4f73c-213">Placing the opening token on a new line, the contents tabbed over one scope, and the closing token on a new line is preferable if you are:</span></span>

* <span data-ttu-id="4f73c-214">以不同的縮排範圍在程式碼中移動記錄</span><span class="sxs-lookup"><span data-stu-id="4f73c-214">Moving records around in code with different indentation scopes</span></span>
* <span data-ttu-id="4f73c-215">將它們輸送至函式</span><span class="sxs-lookup"><span data-stu-id="4f73c-215">Piping them into a function</span></span>

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
        SomeField: int
    }
    interface IMyInterface

let foo a =
    a
    |> Option.map (fun x ->
        {
            MyField = x
        })
```

<span data-ttu-id="4f73c-216">List 和 array 元素也適用相同的規則。</span><span class="sxs-lookup"><span data-stu-id="4f73c-216">The same rules apply for list and array elements.</span></span>

## <a name="formatting-copy-and-update-record-expressions"></a><span data-ttu-id="4f73c-217">格式化複製和更新記錄運算式</span><span class="sxs-lookup"><span data-stu-id="4f73c-217">Formatting copy-and-update record expressions</span></span>

<span data-ttu-id="4f73c-218">複製和更新記錄運算式仍是一筆記錄，因此適用類似的指導方針。</span><span class="sxs-lookup"><span data-stu-id="4f73c-218">A copy-and-update record expression is still a record, so similar guidelines apply.</span></span>

<span data-ttu-id="4f73c-219">簡短運算式可以放在一行中：</span><span class="sxs-lookup"><span data-stu-id="4f73c-219">Short expressions can fit on one line:</span></span>

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

<span data-ttu-id="4f73c-220">較長的運算式應該使用新的行：</span><span class="sxs-lookup"><span data-stu-id="4f73c-220">Longer expressions should use new lines:</span></span>

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = [ "Zippy"; "George"; "Bungle" ] }
```

<span data-ttu-id="4f73c-221">如同記錄指導方針，您可能會想要為大括弧專用不同的行，並使用運算式將一個範圍向右縮排。</span><span class="sxs-lookup"><span data-stu-id="4f73c-221">And as with the record guidance, you may want to dedicate separate lines for the braces and indent one scope to the right with the expression.</span></span> <span data-ttu-id="4f73c-222">在某些特殊情況下，例如以不含括弧的選擇性包裝值，您可能需要在一行上保留一個大括弧：</span><span class="sxs-lookup"><span data-stu-id="4f73c-222">In some special cases, such as wrapping a value with an optional without parentheses, you may need to keep a brace on one line:</span></span>

```fsharp
type S = { F1: int; F2: string }
type State = { F:  S option }

let state = { F = Some { F1 = 1; F2 = "Hello" } }
let newState =
    {
        state with
            F = Some {
                    F1 = 0
                    F2 = ""
                }
    }
```

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="4f73c-223">格式化清單和陣列</span><span class="sxs-lookup"><span data-stu-id="4f73c-223">Formatting lists and arrays</span></span>

<span data-ttu-id="4f73c-224">`x :: l`在運算子前後以空格寫入 `::` （ `::` 是中置運算子，因此以空格括住）。</span><span class="sxs-lookup"><span data-stu-id="4f73c-224">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces).</span></span>

<span data-ttu-id="4f73c-225">在單一行上宣告的清單和陣列，在左括弧後面和右括弧前面應該有一個空格：</span><span class="sxs-lookup"><span data-stu-id="4f73c-225">List and arrays declared on a single line should have a space after the opening bracket and before the closing bracket:</span></span>

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

<span data-ttu-id="4f73c-226">在兩個不同的大括弧運算子之間一律使用至少一個空格。</span><span class="sxs-lookup"><span data-stu-id="4f73c-226">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="4f73c-227">例如，在和之間保留一個空格 `[` `{` 。</span><span class="sxs-lookup"><span data-stu-id="4f73c-227">For example, leave a space between a `[` and a `{`.</span></span>

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

<span data-ttu-id="4f73c-228">相同的指導方針適用于元組的清單或陣列。</span><span class="sxs-lookup"><span data-stu-id="4f73c-228">The same guideline applies for lists or arrays of tuples.</span></span>

<span data-ttu-id="4f73c-229">分割成多行的清單和陣列會遵循類似記錄的規則：</span><span class="sxs-lookup"><span data-stu-id="4f73c-229">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

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

<span data-ttu-id="4f73c-230">就像記錄一樣，在自己的行上宣告開頭和結尾括弧，會讓移動程式碼變得更容易。</span><span class="sxs-lookup"><span data-stu-id="4f73c-230">And as with records, declaring the opening and closing brackets on their own line will make moving code around and piping into functions easier.</span></span>

<span data-ttu-id="4f73c-231">以程式設計方式產生陣列和清單時，偏好 `->` `do ... yield` 一律產生值時：</span><span class="sxs-lookup"><span data-stu-id="4f73c-231">When generating arrays and lists programmatically, prefer `->` over `do ... yield` when a value is always generated:</span></span>

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x * x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x * x ]
```

<span data-ttu-id="4f73c-232">較舊版本的 F # 語言需要 `yield` 在可能有條件地產生資料的情況下指定，或者可能會有連續的運算式進行評估。</span><span class="sxs-lookup"><span data-stu-id="4f73c-232">Older versions of the F# language required specifying `yield` in situations where data may be generated conditionally, or there may be consecutive expressions to be evaluated.</span></span> <span data-ttu-id="4f73c-233">`yield`除非您必須使用較舊的 F # 語言版本進行編譯，否則偏好省略這些關鍵字：</span><span class="sxs-lookup"><span data-stu-id="4f73c-233">Prefer omitting these `yield` keywords unless you must compile with an older F# language version:</span></span>

```fsharp
// Preferred
let daysOfWeek includeWeekend =
    [
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    ]

// Not preferred
let daysOfWeek' includeWeekend =
    [
        yield "Monday"
        yield "Tuesday"
        yield "Wednesday"
        yield "Thursday"
        yield "Friday"
        if includeWeekend then
            yield "Saturday"
            yield "Sunday"
    ]
```

<span data-ttu-id="4f73c-234">在某些情況下， `do...yield` 可能有助於提高可讀性。</span><span class="sxs-lookup"><span data-stu-id="4f73c-234">In some cases, `do...yield` may aid in readability.</span></span> <span data-ttu-id="4f73c-235">不過，您應該將這些案例納入主觀。</span><span class="sxs-lookup"><span data-stu-id="4f73c-235">These cases, though subjective, should be taken into consideration.</span></span>

## <a name="formatting-if-expressions"></a><span data-ttu-id="4f73c-236">設定運算式時的格式</span><span class="sxs-lookup"><span data-stu-id="4f73c-236">Formatting if expressions</span></span>

<span data-ttu-id="4f73c-237">條件的縮排取決於組成它們的運算式大小。</span><span class="sxs-lookup"><span data-stu-id="4f73c-237">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="4f73c-238">如果 `cond` 、 `e1` 和 `e2` 很短，只要將它們寫在一行就行了：</span><span class="sxs-lookup"><span data-stu-id="4f73c-238">If `cond`, `e1` and `e2` are short, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="4f73c-239">如果其中一個 `cond` 、 `e1` 或較 `e2` 長，但不是多行：</span><span class="sxs-lookup"><span data-stu-id="4f73c-239">If either `cond`, `e1` or `e2` are longer, but not multi-line:</span></span>

```fsharp
if cond
then e1
else e2
```

<span data-ttu-id="4f73c-240">如果有任何運算式是多行：</span><span class="sxs-lookup"><span data-stu-id="4f73c-240">If any of the expressions are multi-line:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="4f73c-241">具有和的多個條件 `elif` `else` 會在與相同的範圍內縮排 `if` ：</span><span class="sxs-lookup"><span data-stu-id="4f73c-241">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="4f73c-242">模式比對結構</span><span class="sxs-lookup"><span data-stu-id="4f73c-242">Pattern matching constructs</span></span>

<span data-ttu-id="4f73c-243">`|`針對相符的每個子句使用，而不是縮排。</span><span class="sxs-lookup"><span data-stu-id="4f73c-243">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="4f73c-244">如果運算式是 short，則如果每個子運算式也很簡單，您可以考慮使用單一行。</span><span class="sxs-lookup"><span data-stu-id="4f73c-244">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

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

<span data-ttu-id="4f73c-245">如果模式比對箭頭右邊的運算式太大，請將它移至下一行，從縮排一個步驟 `match` / `|` 。</span><span class="sxs-lookup"><span data-stu-id="4f73c-245">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="4f73c-246">匿名函式的模式比對，從開始 `function` ，通常不會太過太多縮排。</span><span class="sxs-lookup"><span data-stu-id="4f73c-246">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="4f73c-247">例如，縮排一個範圍，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4f73c-247">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="4f73c-248">或所定義之函式中的模式比 `let` `let rec` 對，應該在開始之後縮排四個空格 `let` ，即使 `function` 使用關鍵字也一樣：</span><span class="sxs-lookup"><span data-stu-id="4f73c-248">Pattern matching in functions defined by `let` or `let rec` should be indented four spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="4f73c-249">我們不建議對齊箭號。</span><span class="sxs-lookup"><span data-stu-id="4f73c-249">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="4f73c-250">格式化 try/with 運算式</span><span class="sxs-lookup"><span data-stu-id="4f73c-250">Formatting try/with expressions</span></span>

<span data-ttu-id="4f73c-251">例外狀況類型的模式比對應該在與相同的層級上縮排 `with` 。</span><span class="sxs-lookup"><span data-stu-id="4f73c-251">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

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

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="4f73c-252">格式化函數參數應用程式</span><span class="sxs-lookup"><span data-stu-id="4f73c-252">Formatting function parameter application</span></span>

<span data-ttu-id="4f73c-253">一般而言，大部分的函式參數應用程式都是在同一行上完成。</span><span class="sxs-lookup"><span data-stu-id="4f73c-253">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="4f73c-254">如果您想要將參數套用至新行上的函式，請依一個範圍來縮排它們。</span><span class="sxs-lookup"><span data-stu-id="4f73c-254">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

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

<span data-ttu-id="4f73c-255">相同的指導方針適用于 lambda 運算式做為函式引數。</span><span class="sxs-lookup"><span data-stu-id="4f73c-255">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="4f73c-256">如果 lambda 運算式的主體，主體可以有另一行，並以一個範圍縮排</span><span class="sxs-lookup"><span data-stu-id="4f73c-256">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

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

<span data-ttu-id="4f73c-257">不過，如果 lambda 運算式的主體超過一行，請考慮將它分解成不同的函式，而不是將多行結構套用為函式的單一引數。</span><span class="sxs-lookup"><span data-stu-id="4f73c-257">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="4f73c-258">格式化中綴運算子</span><span class="sxs-lookup"><span data-stu-id="4f73c-258">Formatting infix operators</span></span>

<span data-ttu-id="4f73c-259">以空格分隔運算子。</span><span class="sxs-lookup"><span data-stu-id="4f73c-259">Separate operators by spaces.</span></span> <span data-ttu-id="4f73c-260">此規則的例外狀況是 `!` 和 `.` 運算子。</span><span class="sxs-lookup"><span data-stu-id="4f73c-260">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="4f73c-261">中綴運算式可以在相同的資料行上進行組合：</span><span class="sxs-lookup"><span data-stu-id="4f73c-261">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="4f73c-262">格式化管線運算子</span><span class="sxs-lookup"><span data-stu-id="4f73c-262">Formatting pipeline operators</span></span>

<span data-ttu-id="4f73c-263">管線 `|>` 運算子應該放在其操作所在的運算式之下。</span><span class="sxs-lookup"><span data-stu-id="4f73c-263">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

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

### <a name="formatting-modules"></a><span data-ttu-id="4f73c-264">格式化模組</span><span class="sxs-lookup"><span data-stu-id="4f73c-264">Formatting modules</span></span>

<span data-ttu-id="4f73c-265">本機模組中的程式碼必須相對於模組進行縮排，但最上層模組中的程式碼不應該縮排。</span><span class="sxs-lookup"><span data-stu-id="4f73c-265">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="4f73c-266">命名空間元素不必縮排。</span><span class="sxs-lookup"><span data-stu-id="4f73c-266">Namespace elements do not have to be indented.</span></span>

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a * a + b * b

module A2 =
    let function2 a b = a * a - b * b
```

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="4f73c-267">格式化物件運算式和介面</span><span class="sxs-lookup"><span data-stu-id="4f73c-267">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="4f73c-268">物件運算式和介面應該以相同的方式對齊，並在 `member` 四個空格之後縮排。</span><span class="sxs-lookup"><span data-stu-id="4f73c-268">Object expressions and interfaces should be aligned in the same way with `member` being indented after four spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="4f73c-269">格式化運算式中的空白字元</span><span class="sxs-lookup"><span data-stu-id="4f73c-269">Formatting white space in expressions</span></span>

<span data-ttu-id="4f73c-270">避免在 F # 運算式中有多餘的空白字元。</span><span class="sxs-lookup"><span data-stu-id="4f73c-270">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="4f73c-271">具名引數的周圍也不應該有空格 `=` ：</span><span class="sxs-lookup"><span data-stu-id="4f73c-271">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a><span data-ttu-id="4f73c-272">格式化屬性</span><span class="sxs-lookup"><span data-stu-id="4f73c-272">Formatting attributes</span></span>

<span data-ttu-id="4f73c-273">[屬性](../language-reference/attributes.md)會放在結構的上方：</span><span class="sxs-lookup"><span data-stu-id="4f73c-273">[Attributes](../language-reference/attributes.md) are placed above a construct:</span></span>

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

### <a name="formatting-attributes-on-parameters"></a><span data-ttu-id="4f73c-274">格式化參數上的屬性</span><span class="sxs-lookup"><span data-stu-id="4f73c-274">Formatting attributes on parameters</span></span>

<span data-ttu-id="4f73c-275">屬性也可以放在參數上。</span><span class="sxs-lookup"><span data-stu-id="4f73c-275">Attributes can also be placed on parameters.</span></span> <span data-ttu-id="4f73c-276">在此情況下，請將它放在與參數相同的行上，並在名稱之前：</span><span class="sxs-lookup"><span data-stu-id="4f73c-276">In this case, place then on the same line as the parameter and before the name:</span></span>

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a><span data-ttu-id="4f73c-277">格式化多個屬性</span><span class="sxs-lookup"><span data-stu-id="4f73c-277">Formatting multiple attributes</span></span>

<span data-ttu-id="4f73c-278">當多個屬性套用至不是參數的結構時，應該將它們放置在每一行有一個屬性：</span><span class="sxs-lookup"><span data-stu-id="4f73c-278">When multiple attributes are applied to a construct that is not a parameter, they should be placed such that there is one attribute per line:</span></span>

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

<span data-ttu-id="4f73c-279">套用至參數時，它們必須位於同一行，並以 `;` 分隔符號分隔。</span><span class="sxs-lookup"><span data-stu-id="4f73c-279">When applied to a parameter, they must be on the same line and separated by a `;` separator.</span></span>

## <a name="formatting-literals"></a><span data-ttu-id="4f73c-280">格式化常值</span><span class="sxs-lookup"><span data-stu-id="4f73c-280">Formatting literals</span></span>

<span data-ttu-id="4f73c-281">使用屬性的[F # 常](../language-reference/literals.md)值 `Literal` 應該將屬性放在它自己的行上，並使用 PascalCase 命名：</span><span class="sxs-lookup"><span data-stu-id="4f73c-281">[F# literals](../language-reference/literals.md) using the `Literal` attribute should place the attribute on its own line and use PascalCase naming:</span></span>

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

<span data-ttu-id="4f73c-282">避免將屬性放在與值相同的行上。</span><span class="sxs-lookup"><span data-stu-id="4f73c-282">Avoid placing the attribute on the same line as the value.</span></span>
