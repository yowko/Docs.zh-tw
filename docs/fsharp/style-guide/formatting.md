---
title: F# 程式碼格式方針
description: 瞭解 F# 程式碼的格式設定指南。
ms.date: 11/04/2019
ms.openlocfilehash: b8be70dd29a04e71614308164e541b99a1724305
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739549"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="b4db3-103">F# 程式碼格式方針</span><span class="sxs-lookup"><span data-stu-id="b4db3-103">F# code formatting guidelines</span></span>

<span data-ttu-id="b4db3-104">本文提供了如何設定代碼格式的指南,以便 F# 代碼具有:</span><span class="sxs-lookup"><span data-stu-id="b4db3-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="b4db3-105">更清晰</span><span class="sxs-lookup"><span data-stu-id="b4db3-105">More legible</span></span>
* <span data-ttu-id="b4db3-106">依視覺化工作室和其他編輯器中格式工具應用程式的約定</span><span class="sxs-lookup"><span data-stu-id="b4db3-106">In accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="b4db3-107">類似於其他線上碼</span><span class="sxs-lookup"><span data-stu-id="b4db3-107">Similar to other code online</span></span>

<span data-ttu-id="b4db3-108">這些準則基於[由安-鄧潘](https://github.com/dungpa)[對 F# 格式約定的全面指南](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md)。</span><span class="sxs-lookup"><span data-stu-id="b4db3-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="b4db3-109">縮排的一般規則</span><span class="sxs-lookup"><span data-stu-id="b4db3-109">General rules for indentation</span></span>

<span data-ttu-id="b4db3-110">默認情況下,F# 使用大量空白。</span><span class="sxs-lookup"><span data-stu-id="b4db3-110">F# uses significant white space by default.</span></span> <span data-ttu-id="b4db3-111">以下準則旨在就如何應對可能帶來的一些挑戰提供指導。</span><span class="sxs-lookup"><span data-stu-id="b4db3-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="b4db3-112">使用空白</span><span class="sxs-lookup"><span data-stu-id="b4db3-112">Using spaces</span></span>

<span data-ttu-id="b4db3-113">當需要縮進時,必須使用空格,而不是選項卡。</span><span class="sxs-lookup"><span data-stu-id="b4db3-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="b4db3-114">至少需要一個空格。</span><span class="sxs-lookup"><span data-stu-id="b4db3-114">At least one space is required.</span></span> <span data-ttu-id="b4db3-115">您的組織可以創建編碼標準來指定用於縮進的空間數;在發生縮進的每個級別,2 個、3 個或 4 個縮進空間是典型的。</span><span class="sxs-lookup"><span data-stu-id="b4db3-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three, or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="b4db3-116">**我們建議每個縮進四個空格。**</span><span class="sxs-lookup"><span data-stu-id="b4db3-116">**We recommend four spaces per indentation.**</span></span>

<span data-ttu-id="b4db3-117">這就是說,程式縮進是一個主觀問題。</span><span class="sxs-lookup"><span data-stu-id="b4db3-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="b4db3-118">變異是可以的,但您應該遵循的第一條規則是*縮進的一致性*。</span><span class="sxs-lookup"><span data-stu-id="b4db3-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="b4db3-119">選擇一種普遍接受的縮進樣式,並在代碼庫中系統地使用它。</span><span class="sxs-lookup"><span data-stu-id="b4db3-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-white-space"></a><span data-ttu-id="b4db3-120">設定空白格式</span><span class="sxs-lookup"><span data-stu-id="b4db3-120">Formatting white space</span></span>

<span data-ttu-id="b4db3-121">F# 對空白敏感。</span><span class="sxs-lookup"><span data-stu-id="b4db3-121">F# is white space sensitive.</span></span> <span data-ttu-id="b4db3-122">儘管空白的大多數語義都由適當的縮進覆蓋,但還有其他一些需要考慮。</span><span class="sxs-lookup"><span data-stu-id="b4db3-122">Although most semantics from white space are covered by proper indentation, there are some other things to consider.</span></span>

### <a name="formatting-operators-in-arithmetic-expressions"></a><span data-ttu-id="b4db3-123">算術表示式的運算子格式</span><span class="sxs-lookup"><span data-stu-id="b4db3-123">Formatting operators in arithmetic expressions</span></span>

<span data-ttu-id="b4db3-124">始終在二進位算術表達式周圍使用空白:</span><span class="sxs-lookup"><span data-stu-id="b4db3-124">Always use white space around binary arithmetic expressions:</span></span>

```fsharp
let subtractThenAdd x = x - 1 + 3
```

<span data-ttu-id="b4db3-125">一元`-`運算子應始終立即跟隨他們否定的值:</span><span class="sxs-lookup"><span data-stu-id="b4db3-125">Unary `-` operators should always be immediately followed by the value they are negating:</span></span>

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

<span data-ttu-id="b4db3-126">在`-`運算符之後添加空格字元可能會導致其他人混淆。</span><span class="sxs-lookup"><span data-stu-id="b4db3-126">Adding a white-space character after the `-` operator can lead to confusion for others.</span></span>

<span data-ttu-id="b4db3-127">總之,始終:</span><span class="sxs-lookup"><span data-stu-id="b4db3-127">In summary, it's important to always:</span></span>

* <span data-ttu-id="b4db3-128">環繞具有空白的二進位運算子</span><span class="sxs-lookup"><span data-stu-id="b4db3-128">Surround binary operators with white space</span></span>
* <span data-ttu-id="b4db3-129">一個一元運算符後,永遠不會有尾隨空格</span><span class="sxs-lookup"><span data-stu-id="b4db3-129">Never have trailing white space after a unary operator</span></span>

<span data-ttu-id="b4db3-130">二進位算術運算符準則尤為重要。</span><span class="sxs-lookup"><span data-stu-id="b4db3-130">The binary arithmetic operator guideline is especially important.</span></span> <span data-ttu-id="b4db3-131">如果無法包圍二進位`-`運算符,當與某些格式選項結合使用時,可能會導致將其解釋為一元`-`。</span><span class="sxs-lookup"><span data-stu-id="b4db3-131">Failing to surround a binary `-` operator, when combined with certain formatting choices, could lead to interpreting it as a unary `-`.</span></span>

### <a name="surround-a-custom-operator-definition-with-white-space"></a><span data-ttu-id="b4db3-132">以空白方繞自訂運算符定義</span><span class="sxs-lookup"><span data-stu-id="b4db3-132">Surround a custom operator definition with white space</span></span>

<span data-ttu-id="b4db3-133">始終使用空白環繞運算符定義:</span><span class="sxs-lookup"><span data-stu-id="b4db3-133">Always use white space to surround an operator definition:</span></span>

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

<span data-ttu-id="b4db3-134">對於任何以開頭`*`且具有多個字元的自定義運算符,都需要向定義開頭添加一個空格以避免編譯器歧義。</span><span class="sxs-lookup"><span data-stu-id="b4db3-134">For any custom operator that starts with `*` and that has more than one character, you need to add a white space to the beginning of the definition to avoid a compiler ambiguity.</span></span> <span data-ttu-id="b4db3-135">因此,我們建議您只需使用單個空格字元括括所有運算元的定義。</span><span class="sxs-lookup"><span data-stu-id="b4db3-135">Because of this, we recommend that you simply surround the definitions of all operators with a single white-space character.</span></span>

### <a name="surround-function-parameter-arrows-with-white-space"></a><span data-ttu-id="b4db3-136">帶空格的環繞函數參數箭頭</span><span class="sxs-lookup"><span data-stu-id="b4db3-136">Surround function parameter arrows with white space</span></span>

<span data-ttu-id="b4db3-137">定義函數的簽名時,請使用`->`符號周圍的空白:</span><span class="sxs-lookup"><span data-stu-id="b4db3-137">When defining the signature of a function, use white space around the `->` symbol:</span></span>

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a><span data-ttu-id="b4db3-138">帶空格的環繞函數參數</span><span class="sxs-lookup"><span data-stu-id="b4db3-138">Surround function arguments with white space</span></span>

<span data-ttu-id="b4db3-139">定義函數時,在每個參數周圍使用空白。</span><span class="sxs-lookup"><span data-stu-id="b4db3-139">When defining a function, use white space around each argument.</span></span>

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="place-parameters-on-a-new-line-for-long-member-definitions"></a><span data-ttu-id="b4db3-140">將參數放在長成員定義的新行上</span><span class="sxs-lookup"><span data-stu-id="b4db3-140">Place parameters on a new line for long member definitions</span></span>

<span data-ttu-id="b4db3-141">如果您有很長的成員定義,則將參數放在新行上,並縮進它們一個作用域。</span><span class="sxs-lookup"><span data-stu-id="b4db3-141">If you have a very long member definition, place the parameters on new lines and indent them one scope.</span></span>

```fsharp
type C() =
    member _.LongMethodWithLotsOfParameters(
        aVeryLongType: AVeryLongTypeThatYouNeedToUse
        aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
        aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
        // ... the body of the method follows
```

<span data-ttu-id="b4db3-142">這也適用於建構函數:</span><span class="sxs-lookup"><span data-stu-id="b4db3-142">This also applies to constructors:</span></span>

```fsharp
type C(
    aVeryLongType: AVeryLongTypeThatYouNeedToUse
    aSecondVeryLongType: AVeryLongTypeThatYouNeedToUse
    aThirdVeryLongType: AVeryLongTypeThatYouNeedToUse) =
    // ... the body of the class follows
```

### <a name="type-annotations"></a><span data-ttu-id="b4db3-143">類型註解</span><span class="sxs-lookup"><span data-stu-id="b4db3-143">Type annotations</span></span>

#### <a name="right-pad-function-argument-type-annotations"></a><span data-ttu-id="b4db3-144">右墊函數參數類型註解</span><span class="sxs-lookup"><span data-stu-id="b4db3-144">Right-pad function argument type annotations</span></span>

<span data-ttu-id="b4db3-145">使用類型註釋定義參數時,在`:`符號之後使用空格:</span><span class="sxs-lookup"><span data-stu-id="b4db3-145">When defining arguments with type annotations, use white space after the `:` symbol:</span></span>

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a><span data-ttu-id="b4db3-146">帶空格的環繞傳回類型註解</span><span class="sxs-lookup"><span data-stu-id="b4db3-146">Surround return type annotations with white space</span></span>

<span data-ttu-id="b4db3-147">在允許結合函數或值型態註解(在函數的情況下傳回類型)中,`:`在符號之前和之後使用空格:</span><span class="sxs-lookup"><span data-stu-id="b4db3-147">In a let-bound function or value type annotation (return type in the case of a function), use white space before and after the `:` symbol:</span></span>

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a><span data-ttu-id="b4db3-148">設定空白列格式</span><span class="sxs-lookup"><span data-stu-id="b4db3-148">Formatting blank lines</span></span>

* <span data-ttu-id="b4db3-149">使用兩條空白行分隔頂級函數和類定義。</span><span class="sxs-lookup"><span data-stu-id="b4db3-149">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="b4db3-150">類中的方法定義由單個空白行分隔。</span><span class="sxs-lookup"><span data-stu-id="b4db3-150">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="b4db3-151">額外的空白行可用於(謹慎)分隔相關函陣列。</span><span class="sxs-lookup"><span data-stu-id="b4db3-151">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="b4db3-152">在一堆相關的單行(例如,一組虛擬實現)之間可以省略空白行。</span><span class="sxs-lookup"><span data-stu-id="b4db3-152">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="b4db3-153">請謹慎在函數中使用空白行來指示邏輯部分。</span><span class="sxs-lookup"><span data-stu-id="b4db3-153">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="b4db3-154">設定註解的格式</span><span class="sxs-lookup"><span data-stu-id="b4db3-154">Formatting comments</span></span>

<span data-ttu-id="b4db3-155">通常更喜歡多個雙斜杠註釋,而不是 ML 樣式塊註釋。</span><span class="sxs-lookup"><span data-stu-id="b4db3-155">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="b4db3-156">內聯註釋應將第一個字母大寫。</span><span class="sxs-lookup"><span data-stu-id="b4db3-156">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="b4db3-157">命名慣例</span><span class="sxs-lookup"><span data-stu-id="b4db3-157">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="b4db3-158">對類綁定、運算式綁定和模式綁定值和函數使用 camelCase</span><span class="sxs-lookup"><span data-stu-id="b4db3-158">Use camelCase for class-bound, expression-bound, and pattern-bound values and functions</span></span>

<span data-ttu-id="b4db3-159">對於綁定為局部變數的所有名稱或在模式匹配和函數定義中,使用 camelCase 是常見且公認的 F# 樣式。</span><span class="sxs-lookup"><span data-stu-id="b4db3-159">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="b4db3-160">類中的本地綁定函數還應使用 camelCase。</span><span class="sxs-lookup"><span data-stu-id="b4db3-160">Locally bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="b4db3-161">將 CamelCase 用於模組的公共函數</span><span class="sxs-lookup"><span data-stu-id="b4db3-161">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="b4db3-162">當模組綁定函數是公共 API 的一部分時,它應使用 camelCase:</span><span class="sxs-lookup"><span data-stu-id="b4db3-162">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="b4db3-163">將 camelCase 用於內部和私有模組綁定值和函數</span><span class="sxs-lookup"><span data-stu-id="b4db3-163">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="b4db3-164">對專用模組綁定值使用 camelCase,包括:</span><span class="sxs-lookup"><span data-stu-id="b4db3-164">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="b4db3-165">文稿中的暫存函數</span><span class="sxs-lookup"><span data-stu-id="b4db3-165">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="b4db3-166">組成模組或類型的內部實現的值</span><span class="sxs-lookup"><span data-stu-id="b4db3-166">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="b4db3-167">使用 camelCase 進行參數</span><span class="sxs-lookup"><span data-stu-id="b4db3-167">Use camelCase for parameters</span></span>

<span data-ttu-id="b4db3-168">所有參數都應根據 .NET 命名約定使用 camelCase。</span><span class="sxs-lookup"><span data-stu-id="b4db3-168">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="b4db3-169">將帕斯卡套件用於模組</span><span class="sxs-lookup"><span data-stu-id="b4db3-169">Use PascalCase for modules</span></span>

<span data-ttu-id="b4db3-170">所有模組(頂級、內部、私有、嵌套)都應使用 PascalCase。</span><span class="sxs-lookup"><span data-stu-id="b4db3-170">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="b4db3-171">將 PascalCase 用於類型聲明、成員和標籤</span><span class="sxs-lookup"><span data-stu-id="b4db3-171">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="b4db3-172">類、介面、結構、枚舉、委託、記錄和受歧視的聯合都應使用 PascalCase 命名。</span><span class="sxs-lookup"><span data-stu-id="b4db3-172">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="b4db3-173">記錄和受歧視結合的類型和標籤中的成員也應使用 PascalCase。</span><span class="sxs-lookup"><span data-stu-id="b4db3-173">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="b4db3-174">使用 PascalCase 進行 .NET 固有的建構</span><span class="sxs-lookup"><span data-stu-id="b4db3-174">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="b4db3-175">命名空間、異常、事件和專案/`.dll`名稱也應使用 PascalCase。</span><span class="sxs-lookup"><span data-stu-id="b4db3-175">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="b4db3-176">這不僅使來自其他 .NET 語言的消費者感覺更自然,而且與您可能遇到的 .NET 命名約定一致。</span><span class="sxs-lookup"><span data-stu-id="b4db3-176">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="b4db3-177">避免在名稱中下劃線</span><span class="sxs-lookup"><span data-stu-id="b4db3-177">Avoid underscores in names</span></span>

<span data-ttu-id="b4db3-178">從歷史上看,某些 F# 庫在名稱中使用了下劃線。</span><span class="sxs-lookup"><span data-stu-id="b4db3-178">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="b4db3-179">但是,這不再被廣泛接受,部分原因是它與 .NET 命名約定衝突。</span><span class="sxs-lookup"><span data-stu-id="b4db3-179">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="b4db3-180">也就是說,一些 F# 程式師使用強調很大,部分原因是歷史原因,寬容和尊重很重要。</span><span class="sxs-lookup"><span data-stu-id="b4db3-180">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="b4db3-181">但是,請注意,對於是否使用該樣式,其他人通常不喜歡這種風格。</span><span class="sxs-lookup"><span data-stu-id="b4db3-181">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="b4db3-182">一個例外包括與本機組件進行互操作,其中下劃線很常見。</span><span class="sxs-lookup"><span data-stu-id="b4db3-182">One exception includes interoperating with native components, where underscores are common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="b4db3-183">使用標準 F# 運算子</span><span class="sxs-lookup"><span data-stu-id="b4db3-183">Use standard F# operators</span></span>

<span data-ttu-id="b4db3-184">以下運算符在 F# 標準庫中定義,應使用而不是定義等效項。</span><span class="sxs-lookup"><span data-stu-id="b4db3-184">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="b4db3-185">建議使用這些運算符,因為它會使代碼更具可讀性和慣用性。</span><span class="sxs-lookup"><span data-stu-id="b4db3-185">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="b4db3-186">具有 OCaml 或其他函數程式設計語言背景的開發人員可能習慣於不同的習語。</span><span class="sxs-lookup"><span data-stu-id="b4db3-186">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="b4db3-187">下面的清單總結了推薦的 F# 運算符。</span><span class="sxs-lookup"><span data-stu-id="b4db3-187">The following list summarizes the recommended F# operators.</span></span>

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="b4db3-188">使用泛型的前置字語法`Foo<T>`( ) 優先於後`T Foo`綴語法 ( )</span><span class="sxs-lookup"><span data-stu-id="b4db3-188">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="b4db3-189">F# 既繼承命名泛型類型的後綴 ML 樣`int list`式(例如 ),也繼承前綴 .NET`list<int>`樣式(例如)。</span><span class="sxs-lookup"><span data-stu-id="b4db3-189">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="b4db3-190">首選 .NET 樣式,但五種特定類型除外:</span><span class="sxs-lookup"><span data-stu-id="b4db3-190">Prefer the .NET style, except for five specific types:</span></span>

1. <span data-ttu-id="b4db3-191">對於 F# 清單,請使用後修復`int list`窗型`list<int>`:而不是 。</span><span class="sxs-lookup"><span data-stu-id="b4db3-191">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="b4db3-192">對 F# 選項,請使用後修復`int option`窗型`option<int>`:而不是 。</span><span class="sxs-lookup"><span data-stu-id="b4db3-192">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="b4db3-193">對 F# 值選項,請使用後修復`int voption`窗型`voption<int>`:而不是 。</span><span class="sxs-lookup"><span data-stu-id="b4db3-193">For F# Value Options, use the postfix form: `int voption` rather than `voption<int>`.</span></span>
4. <span data-ttu-id="b4db3-194">對於 F# 陣列,請使用句`int[]`法`int array`名稱`array<int>`而不是或 。</span><span class="sxs-lookup"><span data-stu-id="b4db3-194">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
5. <span data-ttu-id="b4db3-195">對參考儲存格,使用`int ref`而不是`ref<int>``Ref<int>`或 。</span><span class="sxs-lookup"><span data-stu-id="b4db3-195">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="b4db3-196">對於所有其他類型,請使用首碼窗體。</span><span class="sxs-lookup"><span data-stu-id="b4db3-196">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="b4db3-197">格式化中陣數</span><span class="sxs-lookup"><span data-stu-id="b4db3-197">Formatting tuples</span></span>

<span data-ttu-id="b4db3-198">中繼實體資訊資訊設定為括弧,其中的分隔逗號應後跟單個空白,例如: `(1, 2)`。 `(x, y, z)`</span><span class="sxs-lookup"><span data-stu-id="b4db3-198">A tuple instantiation should be parenthesized, and the delimiting commas within it should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="b4db3-199">在組合的圖案比對中省略括弧是通常接受的:</span><span class="sxs-lookup"><span data-stu-id="b4db3-199">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

<span data-ttu-id="b4db3-200">如果元組是函數的返回值,則通常也接受省略括弧:</span><span class="sxs-lookup"><span data-stu-id="b4db3-200">It is also commonly accepted to omit parentheses if the tuple is the return value of a function:</span></span>

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

<span data-ttu-id="b4db3-201">總之,首選括弧組實例化,但當使用組合體進行模式匹配或返回值時,避免括弧被認為是好的。</span><span class="sxs-lookup"><span data-stu-id="b4db3-201">In summary, prefer parenthesized tuple instantiations, but when using tuples for pattern matching or a return value, it is considered fine to avoid parentheses.</span></span>

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="b4db3-202">格式化受歧視的工會聲明</span><span class="sxs-lookup"><span data-stu-id="b4db3-202">Formatting discriminated union declarations</span></span>

<span data-ttu-id="b4db3-203">類型定義`|`中按四個空白縮排:</span><span class="sxs-lookup"><span data-stu-id="b4db3-203">Indent `|` in type definition by four spaces:</span></span>

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

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="b4db3-204">格式化受歧視的工會</span><span class="sxs-lookup"><span data-stu-id="b4db3-204">Formatting discriminated unions</span></span>

<span data-ttu-id="b4db3-205">跨多行拆分的實例化歧視聯合應為包含的數據提供具有縮進的新作用域:</span><span class="sxs-lookup"><span data-stu-id="b4db3-205">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="b4db3-206">閉合括弧也可以位於新行上:</span><span class="sxs-lookup"><span data-stu-id="b4db3-206">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="b4db3-207">格式化記錄聲明</span><span class="sxs-lookup"><span data-stu-id="b4db3-207">Formatting record declarations</span></span>

<span data-ttu-id="b4db3-208">按四`{`個空白在類型定義中縮進,並在同一行上啟動欄位清單:</span><span class="sxs-lookup"><span data-stu-id="b4db3-208">Indent `{` in type definition by four spaces and start the field list on the same line:</span></span>

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

<span data-ttu-id="b4db3-209">如果要聲明介面實現或記錄上的成員,最好在新行上放置首開令牌,在新行上放置結束令牌:</span><span class="sxs-lookup"><span data-stu-id="b4db3-209">Placing the opening token on a new line and the closing token on a new line is preferable if you are declaring interface implementations or members on the record:</span></span>

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

## <a name="formatting-records"></a><span data-ttu-id="b4db3-210">設定記錄格式</span><span class="sxs-lookup"><span data-stu-id="b4db3-210">Formatting records</span></span>

<span data-ttu-id="b4db3-211">短記錄可以寫在一行:</span><span class="sxs-lookup"><span data-stu-id="b4db3-211">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="b4db3-212">較長的紀錄應使用新行用於標籤:</span><span class="sxs-lookup"><span data-stu-id="b4db3-212">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="b4db3-213">將首開權杖放在新行上,內容在一個作用網域上選項卡,如果是:</span><span class="sxs-lookup"><span data-stu-id="b4db3-213">Placing the opening token on a new line, the contents tabbed over one scope, and the closing token on a new line is preferable if you are:</span></span>

* <span data-ttu-id="b4db3-214">在具有不同縮進作用網域的代碼中移動記錄</span><span class="sxs-lookup"><span data-stu-id="b4db3-214">Moving records around in code with different indentation scopes</span></span>
* <span data-ttu-id="b4db3-215">將它們放入函數中</span><span class="sxs-lookup"><span data-stu-id="b4db3-215">Piping them into a function</span></span>

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

<span data-ttu-id="b4db3-216">相同的規則適用於清單和陣列元素。</span><span class="sxs-lookup"><span data-stu-id="b4db3-216">The same rules apply for list and array elements.</span></span>

## <a name="formatting-copy-and-update-record-expressions"></a><span data-ttu-id="b4db3-217">格式化複製及更新記錄表示式</span><span class="sxs-lookup"><span data-stu-id="b4db3-217">Formatting copy-and-update record expressions</span></span>

<span data-ttu-id="b4db3-218">複製和更新記錄表達式仍然是記錄,因此適用類似的準則。</span><span class="sxs-lookup"><span data-stu-id="b4db3-218">A copy-and-update record expression is still a record, so similar guidelines apply.</span></span>

<span data-ttu-id="b4db3-219">短運算式可以適合在一行上:</span><span class="sxs-lookup"><span data-stu-id="b4db3-219">Short expressions can fit on one line:</span></span>

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

<span data-ttu-id="b4db3-220">較長的運算式應使用新行:</span><span class="sxs-lookup"><span data-stu-id="b4db3-220">Longer expressions should use new lines:</span></span>

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="b4db3-221">與記錄指南一樣,您可能希望為大括弧專用單獨的行,並將一個範圍縮進到右側。</span><span class="sxs-lookup"><span data-stu-id="b4db3-221">And as with the record guidance, you may want to dedicate separate lines for the braces and indent one scope to the right with the expression.</span></span> <span data-ttu-id="b4db3-222">在某些特殊情況下,例如使用可選的無括弧包裝值,您可能需要在一行上保留大括弧:</span><span class="sxs-lookup"><span data-stu-id="b4db3-222">In some special cases, such as wrapping a value with an optional without parentheses, you may need to keep a brace on one line:</span></span>

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

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="b4db3-223">設定清單與陣列格式</span><span class="sxs-lookup"><span data-stu-id="b4db3-223">Formatting lists and arrays</span></span>

<span data-ttu-id="b4db3-224">使用`x :: l``::`運算子周圍的空白寫入(`::`是一個內碼運算符,因此被空格包圍)。</span><span class="sxs-lookup"><span data-stu-id="b4db3-224">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces).</span></span>

<span data-ttu-id="b4db3-225">在單行上聲明的清單和陣列應在開口括弧後和右括弧之前具有空格:</span><span class="sxs-lookup"><span data-stu-id="b4db3-225">List and arrays declared on a single line should have a space after the opening bracket and before the closing bracket:</span></span>

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

<span data-ttu-id="b4db3-226">始終在兩個不同的大括弧運算元之間至少使用一個空格。</span><span class="sxs-lookup"><span data-stu-id="b4db3-226">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="b4db3-227">例如,在和`[`之間留一個`{`空格。</span><span class="sxs-lookup"><span data-stu-id="b4db3-227">For example, leave a space between a `[` and a `{`.</span></span>

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

<span data-ttu-id="b4db3-228">同樣的準則也適用於元組的清單或陣列。</span><span class="sxs-lookup"><span data-stu-id="b4db3-228">The same guideline applies for lists or arrays of tuples.</span></span>

<span data-ttu-id="b4db3-229">跨行拆分的清單和陣列遵循與紀錄類似的規則:</span><span class="sxs-lookup"><span data-stu-id="b4db3-229">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

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

<span data-ttu-id="b4db3-230">與記錄一樣,在自己的行上聲明首括弧和關閉括弧將使行動碼和管道進入功能變得更加容易。</span><span class="sxs-lookup"><span data-stu-id="b4db3-230">And as with records, declaring the opening and closing brackets on their own line will make moving code around and piping into functions easier.</span></span>

<span data-ttu-id="b4db3-231">以程式設計方式產生陣列和清單時,請`->`首`do ... yield`選 始終產生值時:</span><span class="sxs-lookup"><span data-stu-id="b4db3-231">When generating arrays and lists programmatically, prefer `->` over `do ... yield` when a value is always generated:</span></span>

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x*x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x*x ]
```

<span data-ttu-id="b4db3-232">在可能有條件地生成數據或可能需要`yield`計算連續運算式的情況下,需要指定較舊版本的 F# 語言。</span><span class="sxs-lookup"><span data-stu-id="b4db3-232">Older versions of the F# language required specifying `yield` in situations where data may be generated conditionally, or there may be consecutive expressions to be evaluated.</span></span> <span data-ttu-id="b4db3-233">預設的一般略`yield`這些 關鍵字,除非您必須使用較舊的 F# 語言版本進行編譯:</span><span class="sxs-lookup"><span data-stu-id="b4db3-233">Prefer omitting these `yield` keywords unless you must compile with an older F# language version:</span></span>

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

<span data-ttu-id="b4db3-234">在某些情況下,`do...yield`可能有助於可讀性。</span><span class="sxs-lookup"><span data-stu-id="b4db3-234">In some cases, `do...yield` may aid in readability.</span></span> <span data-ttu-id="b4db3-235">這些案件雖然是主觀的,但應當加以考慮。</span><span class="sxs-lookup"><span data-stu-id="b4db3-235">These cases, though subjective, should be taken into consideration.</span></span>

## <a name="formatting-if-expressions"></a><span data-ttu-id="b4db3-236">格式化運算式</span><span class="sxs-lookup"><span data-stu-id="b4db3-236">Formatting if expressions</span></span>

<span data-ttu-id="b4db3-237">條件縮進取決於構成條件的表達式的大小。</span><span class="sxs-lookup"><span data-stu-id="b4db3-237">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="b4db3-238">如果`cond``e1``e2`和短,只需將它們寫在一行上:</span><span class="sxs-lookup"><span data-stu-id="b4db3-238">If `cond`, `e1` and `e2` are short, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="b4db3-239">如果`cond``e1``e2`或較長,但不是多行:</span><span class="sxs-lookup"><span data-stu-id="b4db3-239">If either `cond`, `e1` or `e2` are longer, but not multi-line:</span></span>

```fsharp
if cond
then e1
else e2
```

<span data-ttu-id="b4db3-240">如果任何表示式是多行的:</span><span class="sxs-lookup"><span data-stu-id="b4db3-240">If any of the expressions are multi-line:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="b4db3-241">具有`elif`與`else``if`的多個條件與</span><span class="sxs-lookup"><span data-stu-id="b4db3-241">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="b4db3-242">模式符合建構</span><span class="sxs-lookup"><span data-stu-id="b4db3-242">Pattern matching constructs</span></span>

<span data-ttu-id="b4db3-243">`|`對匹配的每個子句使用,沒有縮進。</span><span class="sxs-lookup"><span data-stu-id="b4db3-243">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="b4db3-244">如果表達式較短,則可以考慮使用單行,如果每個子表達式也很簡單。</span><span class="sxs-lookup"><span data-stu-id="b4db3-244">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

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

<span data-ttu-id="b4db3-245">如果模式匹配箭頭右側的表達式太大,將其移動到下一行,從 縮進`match`/`|`一步。</span><span class="sxs-lookup"><span data-stu-id="b4db3-245">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="b4db3-246">以 開`function`頭的匿名函數的模式匹配通常不應縮進太遠。</span><span class="sxs-lookup"><span data-stu-id="b4db3-246">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="b4db3-247">例如,按照如下方式縮進一個作用域可以:</span><span class="sxs-lookup"><span data-stu-id="b4db3-247">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="b4db3-248">在`let`函數中定義`let rec`的 或應在 啟動後縮進四個`let`空白中的 模式`function`符合,即使使用關鍵字:</span><span class="sxs-lookup"><span data-stu-id="b4db3-248">Pattern matching in functions defined by `let` or `let rec` should be indented four spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="b4db3-249">我們不建議對齊箭頭。</span><span class="sxs-lookup"><span data-stu-id="b4db3-249">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="b4db3-250">設定設定/包含表示式的格式</span><span class="sxs-lookup"><span data-stu-id="b4db3-250">Formatting try/with expressions</span></span>

<span data-ttu-id="b4db3-251">異常類型的模式匹配應縮進與的級別`with`相同。</span><span class="sxs-lookup"><span data-stu-id="b4db3-251">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

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

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="b4db3-252">格式化功能參數應用程式</span><span class="sxs-lookup"><span data-stu-id="b4db3-252">Formatting function parameter application</span></span>

<span data-ttu-id="b4db3-253">通常,大多數函數參數應用都在同一行上完成。</span><span class="sxs-lookup"><span data-stu-id="b4db3-253">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="b4db3-254">如果要將參數應用於新行上的函數,請按一個作用域縮進參數。</span><span class="sxs-lookup"><span data-stu-id="b4db3-254">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

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

<span data-ttu-id="b4db3-255">相同的準則適用於 lambda 運算式和函數參數。</span><span class="sxs-lookup"><span data-stu-id="b4db3-255">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="b4db3-256">如果 lambda 表示式的正文,正文可以有另一條線,由一個作用域縮進</span><span class="sxs-lookup"><span data-stu-id="b4db3-256">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

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

<span data-ttu-id="b4db3-257">但是,如果 lambda 表達式的正文是多行,請考慮將其分解為單獨的函數,而不是將多行構造作為單個參數應用於函數。</span><span class="sxs-lookup"><span data-stu-id="b4db3-257">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="b4db3-258">格式化固定運算子</span><span class="sxs-lookup"><span data-stu-id="b4db3-258">Formatting infix operators</span></span>

<span data-ttu-id="b4db3-259">按空格分隔運算符。</span><span class="sxs-lookup"><span data-stu-id="b4db3-259">Separate operators by spaces.</span></span> <span data-ttu-id="b4db3-260">此規則的明顯例外是`!`和`.`運算符。</span><span class="sxs-lookup"><span data-stu-id="b4db3-260">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="b4db3-261">infix 表示式可以在同一列上提供陣容:</span><span class="sxs-lookup"><span data-stu-id="b4db3-261">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="b4db3-262">格式化導管運算子</span><span class="sxs-lookup"><span data-stu-id="b4db3-262">Formatting pipeline operators</span></span>

<span data-ttu-id="b4db3-263">管道`|>`操作員應位於其操作的表達式下方。</span><span class="sxs-lookup"><span data-stu-id="b4db3-263">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

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

### <a name="formatting-modules"></a><span data-ttu-id="b4db3-264">格式化模組</span><span class="sxs-lookup"><span data-stu-id="b4db3-264">Formatting modules</span></span>

<span data-ttu-id="b4db3-265">本地模組中的代碼必須相對於模組縮進,但頂層模組中的代碼不應縮進。</span><span class="sxs-lookup"><span data-stu-id="b4db3-265">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="b4db3-266">命名空間元素不必縮進。</span><span class="sxs-lookup"><span data-stu-id="b4db3-266">Namespace elements do not have to be indented.</span></span>

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

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="b4db3-267">設定物件運算式與介面的格式</span><span class="sxs-lookup"><span data-stu-id="b4db3-267">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="b4db3-268">對象運算式和介面應與在四個空格後縮`member`進 的方式對齊。</span><span class="sxs-lookup"><span data-stu-id="b4db3-268">Object expressions and interfaces should be aligned in the same way with `member` being indented after four spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="b4db3-269">設定式式空白格式</span><span class="sxs-lookup"><span data-stu-id="b4db3-269">Formatting white space in expressions</span></span>

<span data-ttu-id="b4db3-270">避免 F# 運算式中的無關空白。</span><span class="sxs-lookup"><span data-stu-id="b4db3-270">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="b4db3-271">命名參數也不應圍繞`=`:</span><span class="sxs-lookup"><span data-stu-id="b4db3-271">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-attributes"></a><span data-ttu-id="b4db3-272">設定屬性的格式</span><span class="sxs-lookup"><span data-stu-id="b4db3-272">Formatting attributes</span></span>

<span data-ttu-id="b4db3-273">[屬性](../language-reference/attributes.md)放置在建構上方:</span><span class="sxs-lookup"><span data-stu-id="b4db3-273">[Attributes](../language-reference/attributes.md) are placed above a construct:</span></span>

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

### <a name="formatting-attributes-on-parameters"></a><span data-ttu-id="b4db3-274">參數上的格式設定屬性</span><span class="sxs-lookup"><span data-stu-id="b4db3-274">Formatting attributes on parameters</span></span>

<span data-ttu-id="b4db3-275">屬性也可以是參數上的放置。</span><span class="sxs-lookup"><span data-stu-id="b4db3-275">Attributes can also be places on parameters.</span></span> <span data-ttu-id="b4db3-276">在這種情況下,將放在與參數相同的行上,並在名稱之前:</span><span class="sxs-lookup"><span data-stu-id="b4db3-276">In this case, place then on the same line as the parameter and before the name:</span></span>

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a><span data-ttu-id="b4db3-277">設定多個屬性的格式</span><span class="sxs-lookup"><span data-stu-id="b4db3-277">Formatting multiple attributes</span></span>

<span data-ttu-id="b4db3-278">當多個屬性應用於不是參數的建構時,應放置這些屬性,以便每行有一個屬性:</span><span class="sxs-lookup"><span data-stu-id="b4db3-278">When multiple attributes are applied to a construct that is not a parameter, they should be placed such that there is one attribute per line:</span></span>

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

<span data-ttu-id="b4db3-279">應用於參數時,它們必須位於同一`;`行上,並由分隔符分隔。</span><span class="sxs-lookup"><span data-stu-id="b4db3-279">When applied to a parameter, they must be on the same line and separated by a `;` separator.</span></span>

## <a name="formatting-literals"></a><span data-ttu-id="b4db3-280">格式化文字</span><span class="sxs-lookup"><span data-stu-id="b4db3-280">Formatting literals</span></span>

<span data-ttu-id="b4db3-281">使用`Literal`屬性的[F# 文字](../language-reference/literals.md)應將屬性放在自己的行上,並使用 PascalCase 命名:</span><span class="sxs-lookup"><span data-stu-id="b4db3-281">[F# literals](../language-reference/literals.md) using the `Literal` attribute should place the attribute on its own line and use PascalCase naming:</span></span>

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

<span data-ttu-id="b4db3-282">避免將屬性放在與值相同的行上。</span><span class="sxs-lookup"><span data-stu-id="b4db3-282">Avoid placing the attribute on the same line as the value.</span></span>
