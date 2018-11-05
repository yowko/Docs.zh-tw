---
title: 'F # 程式碼格式設定指導方針'
description: '了解 F # 程式碼格式化的指導方針。'
ms.date: 05/14/2018
ms.openlocfilehash: 0d7d2d1771710db55bf990f3a06079b2aec48fd7
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "43858001"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="9d7f8-103">F # 程式碼格式設定指導方針</span><span class="sxs-lookup"><span data-stu-id="9d7f8-103">F# code formatting guidelines</span></span>

<span data-ttu-id="9d7f8-104">這篇文章提供如何格式化您的程式碼，使 F # 程式碼的指導方針：</span><span class="sxs-lookup"><span data-stu-id="9d7f8-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="9d7f8-105">通常視為更易於閱讀</span><span class="sxs-lookup"><span data-stu-id="9d7f8-105">Generally viewed as more legible</span></span>
* <span data-ttu-id="9d7f8-106">會根據套用在 Visual Studio 中的工具和其他的編輯器格式設定慣例</span><span class="sxs-lookup"><span data-stu-id="9d7f8-106">Is in accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="9d7f8-107">類似於線上的其他程式碼</span><span class="sxs-lookup"><span data-stu-id="9d7f8-107">Similar to other code online</span></span>

<span data-ttu-id="9d7f8-108">這些指導方針根據[F # 格式設定慣例的完整指南](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md)依[Anh phan （英文)](https://github.com/dungpa)。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="9d7f8-109">縮排的一般規則</span><span class="sxs-lookup"><span data-stu-id="9d7f8-109">General rules for indentation</span></span>

<span data-ttu-id="9d7f8-110">F # 會使用預設的顯著泛空白字元。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-110">F# uses significant white space by default.</span></span> <span data-ttu-id="9d7f8-111">下列指導方針的用意在於提供指引來選擇要掌握這造成一些挑戰。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="9d7f8-112">使用空間</span><span class="sxs-lookup"><span data-stu-id="9d7f8-112">Using spaces</span></span>

<span data-ttu-id="9d7f8-113">需要縮排時，您必須使用空格，而不是索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="9d7f8-114">需要至少一個空白字元。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-114">At least one space is required.</span></span> <span data-ttu-id="9d7f8-115">您的組織可以建立以指定要用來縮排; 的空格數目的程式碼撰寫標準通常會發生縮排每個層級的縮排的兩個、 三個或四個空格。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="9d7f8-116">**我們建議每個縮排的 4 個空格。**</span><span class="sxs-lookup"><span data-stu-id="9d7f8-116">**We recommend 4 spaces per indentation.**</span></span>

<span data-ttu-id="9d7f8-117">話雖如此，程式的縮排是主觀的問題而已。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="9d7f8-118">變化都沒問題，但您應該遵循的第一個規則*縮排的一致性*。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="9d7f8-119">選擇通常可接受的縮排樣式，並在整個程式碼基底有系統地使用它。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-blank-lines"></a><span data-ttu-id="9d7f8-120">格式化的空白行</span><span class="sxs-lookup"><span data-stu-id="9d7f8-120">Formatting blank lines</span></span>

* <span data-ttu-id="9d7f8-121">另一個最上層函式和類別定義兩個空白的行。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-121">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="9d7f8-122">在類別內的方法定義是以單一的空白行分隔。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-122">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="9d7f8-123">額外的空白的行可能會用來分隔組相關的函式的 （謹慎使用）。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-123">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="9d7f8-124">一大堆相關單行 （比方說，一組虛擬實作） 之間，可能會省略空白的行。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-124">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="9d7f8-125">使用空白列在函式，盡量節制，來指出邏輯區段。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-125">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="9d7f8-126">格式化註解</span><span class="sxs-lookup"><span data-stu-id="9d7f8-126">Formatting comments</span></span>

<span data-ttu-id="9d7f8-127">通常不用 ML 樣式區塊註解的多個雙斜線註解。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-127">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="9d7f8-128">第一個字母時，應大寫內嵌註解。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-128">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="9d7f8-129">命名規範</span><span class="sxs-lookup"><span data-stu-id="9d7f8-129">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="9d7f8-130">使用 camelCase 類別繫結、 繫結運算式和模式繫結的值和函式</span><span class="sxs-lookup"><span data-stu-id="9d7f8-130">Use camelCase for class-bound, expression-bound and pattern-bound values and functions</span></span>

<span data-ttu-id="9d7f8-131">是很常見，並接受的 F # 使用樣式 camelCase 的所有名稱繫結做為本機變數，或在模式比對和函式定義中。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-131">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="9d7f8-132">本機繫結類別中的函式也應該使用 camelCase。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-132">Locally-bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="9d7f8-133">針對模組繫結的公用函式使用 camelCase</span><span class="sxs-lookup"><span data-stu-id="9d7f8-133">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="9d7f8-134">當模組繫結函式是公用 API 的一部分時，它應該使用 camelCase:</span><span class="sxs-lookup"><span data-stu-id="9d7f8-134">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="9d7f8-135">使用 camelCase 的內部與私用模組繫結值和函式</span><span class="sxs-lookup"><span data-stu-id="9d7f8-135">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="9d7f8-136">使用 camelCase 的私用模組繫結值，包括下列：</span><span class="sxs-lookup"><span data-stu-id="9d7f8-136">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="9d7f8-137">在指令碼中的特定函式</span><span class="sxs-lookup"><span data-stu-id="9d7f8-137">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="9d7f8-138">組成模組或類型的內部實作的值</span><span class="sxs-lookup"><span data-stu-id="9d7f8-138">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="9d7f8-139">針對參數使用 camelCase</span><span class="sxs-lookup"><span data-stu-id="9d7f8-139">Use camelCase for parameters</span></span>

<span data-ttu-id="9d7f8-140">所有參數都應該都使用 camelCase 根據.NET 命名慣例。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-140">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="9d7f8-141">使用 PascalCase 的模組</span><span class="sxs-lookup"><span data-stu-id="9d7f8-141">Use PascalCase for modules</span></span>

<span data-ttu-id="9d7f8-142">（最上層、 內部、 私用、 巢狀） 的所有模組都應該都使用 PascalCase。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-142">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="9d7f8-143">使用 PascalCase 的型別宣告、 成員和標籤</span><span class="sxs-lookup"><span data-stu-id="9d7f8-143">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="9d7f8-144">類別、 介面、 結構、 列舉、 委派、 記錄和差別聯的集全部命名為使用 PascalCase。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-144">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="9d7f8-145">型別和用於記錄和差別聯的集的標籤內的成員也應該使用 PascalCase。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-145">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

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

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="9d7f8-146">適用於.NET 內建函式建構的使用 PascalCase</span><span class="sxs-lookup"><span data-stu-id="9d7f8-146">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="9d7f8-147">命名空間、 例外狀況、 事件和專案 /`.dll`名稱也應該使用 PascalCase。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-147">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="9d7f8-148">不只這樣清楚感受更自然的取用者從其他.NET 語言使用，也是配合您可能會遇到的.NET 命名慣例。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-148">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="9d7f8-149">避免在名稱中的底線</span><span class="sxs-lookup"><span data-stu-id="9d7f8-149">Avoid underscores in names</span></span>

<span data-ttu-id="9d7f8-150">在過去，某些 F # 程式庫名稱中使用底線。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-150">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="9d7f8-151">不過，這是不會再被廣泛接受，這是因為它與.NET 命名慣例衝突。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-151">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="9d7f8-152">話雖如此，某些 F # 程式設計人員使用底線大量、 部分基於歷史原因，並容錯] 和 [方面很重要。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-152">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="9d7f8-153">不過，請注意樣式通常會不喜歡的人可以選擇要使用它。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-153">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="9d7f8-154">某些例外狀況包含間的互通性與原生元件，其中底線很常見。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-154">Some exceptions includes interoperating with native components, where underscores are very common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="9d7f8-155">使用標準的 F # 運算子</span><span class="sxs-lookup"><span data-stu-id="9d7f8-155">Use standard F# operators</span></span>

<span data-ttu-id="9d7f8-156">下列運算子 F # 標準程式庫中已定義，而且應該使用而不是定義對等項目。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-156">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="9d7f8-157">因為它會使程式碼，更容易理解且慣用語，建議使用這些運算子。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-157">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="9d7f8-158">具有背景的 OCaml 或其他功能的程式設計語言的開發人員可能習慣將不同的習慣用語。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-158">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="9d7f8-159">下列清單摘要說明建議的 F # 運算子。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-159">The following list summarizes the recommended F# operators.</span></span>

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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="9d7f8-160">使用泛型的前置詞的語法 (`Foo<T>`) 而非後置語法 (`T Foo`)</span><span class="sxs-lookup"><span data-stu-id="9d7f8-160">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="9d7f8-161">F # 會繼承這兩個後置 ML 的樣式命名泛型型別 (例如`int list`) 以及.NET 樣式的前置詞 (例如`list<int>`)。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-161">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="9d7f8-162">偏好的.NET 樣式，除了特定的四種類型：</span><span class="sxs-lookup"><span data-stu-id="9d7f8-162">Prefer the .NET style, except for four specific types:</span></span>

1. <span data-ttu-id="9d7f8-163">F # 清單中，使用後置格式：`int list`而非`list<int>`。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-163">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="9d7f8-164">使用 F # 選項，請使用後置格式：`int option`而非`option<int>`。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-164">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="9d7f8-165">F # 陣列，使用的語法名稱`int[]`而非`int array`或`array<int>`。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-165">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
4. <span data-ttu-id="9d7f8-166">參考儲存格，使用`int ref`而非`ref<int>`或`Ref<int>`。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-166">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="9d7f8-167">對於所有其他類型，使用前置詞的表單。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-167">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="9d7f8-168">格式化的 tuple</span><span class="sxs-lookup"><span data-stu-id="9d7f8-168">Formatting tuples</span></span>

<span data-ttu-id="9d7f8-169">Tuple 的具現化應該是括號括住，而且中分隔的逗號後面必須接著一個空格，例如： `(1, 2)`， `(x, y, z)`。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-169">A tuple instantiation should be parenthesized, and the delimiting commas within should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="9d7f8-170">通常可接受省略括號中的 tuple 模式比對：</span><span class="sxs-lookup"><span data-stu-id="9d7f8-170">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="9d7f8-171">設定格式化的差別等位宣告</span><span class="sxs-lookup"><span data-stu-id="9d7f8-171">Formatting discriminated union declarations</span></span>

<span data-ttu-id="9d7f8-172">縮排`|`由 4 個空格的型別定義中：</span><span class="sxs-lookup"><span data-stu-id="9d7f8-172">Indent `|` in type definition by 4 spaces:</span></span>

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

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="9d7f8-173">格式化差別聯集</span><span class="sxs-lookup"><span data-stu-id="9d7f8-173">Formatting discriminated unions</span></span>

<span data-ttu-id="9d7f8-174">具現化差別聯集分割成多行，應該會產生包含的資料附縮排新的範圍：</span><span class="sxs-lookup"><span data-stu-id="9d7f8-174">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="9d7f8-175">右括號也可以在新的一行：</span><span class="sxs-lookup"><span data-stu-id="9d7f8-175">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="9d7f8-176">格式設定記錄的宣告</span><span class="sxs-lookup"><span data-stu-id="9d7f8-176">Formatting record declarations</span></span>

<span data-ttu-id="9d7f8-177">縮排`{`在類型定義由 4 空間，開始在同一行上的 [欄位] 清單：</span><span class="sxs-lookup"><span data-stu-id="9d7f8-177">Indent `{` in type definition by 4 spaces and start the field list on the same line:</span></span>

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

<span data-ttu-id="9d7f8-178">將左語彙基元放在同一行和結尾語彙基元，在新的一行上也是沒問題，但請注意，您必須使用[詳細語法](../language-reference/verbose-syntax.md)來定義成員 (`with`關鍵字):</span><span class="sxs-lookup"><span data-stu-id="9d7f8-178">Placing the opening token on the same line and the closing token on a new line is also fine, but be aware that you need to use the [verbose syntax](../language-reference/verbose-syntax.md) to define members (the `with` keyword):</span></span>

```fsharp
//  OK, but verbose syntax required
type PostalAddress = { 
    Address: string
    City: string
    Zip: string
} with
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City
```

## <a name="formatting-records"></a><span data-ttu-id="9d7f8-179">格式化的記錄</span><span class="sxs-lookup"><span data-stu-id="9d7f8-179">Formatting records</span></span>

<span data-ttu-id="9d7f8-180">可以在同一行撰寫簡短的記錄：</span><span class="sxs-lookup"><span data-stu-id="9d7f8-180">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="9d7f8-181">較長的記錄應該使用新行標籤：</span><span class="sxs-lookup"><span data-stu-id="9d7f8-181">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="9d7f8-182">將左語彙基元放在同一行和結尾語彙基元，在新的一行上，也沒問題：</span><span class="sxs-lookup"><span data-stu-id="9d7f8-182">Placing the opening token on the same line and the closing token on a new line is also fine:</span></span>

```fsharp
let rainbow = {
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
```

<span data-ttu-id="9d7f8-183">相同的規則適用於清單和陣列的項目。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-183">The same rules apply for list and array elements.</span></span>

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="9d7f8-184">格式化的清單和陣列</span><span class="sxs-lookup"><span data-stu-id="9d7f8-184">Formatting lists and arrays</span></span>

<span data-ttu-id="9d7f8-185">撰寫`x :: l`與前後的空格`::`運算子 (`::`是中置運算子，因此括住空格) 和`[1; 2; 3]`(`;`是分隔符號，因此後面接著空格)。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-185">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces) and `[1; 2; 3]` (`;` is a delimiter, hence followed by a space).</span></span>

<span data-ttu-id="9d7f8-186">一律使用兩個不同的大括號類似運算子之間的至少一個空白字元。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-186">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="9d7f8-187">例如，將保留之間保留一個空格`[`和`{`。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-187">For example, leave a space between a `[` and a `{`.</span></span>

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

<span data-ttu-id="9d7f8-188">清單和陣列分成多行，請遵循類似的規則記錄也一樣：</span><span class="sxs-lookup"><span data-stu-id="9d7f8-188">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

```fsharp
let pascalsTriangle = [|
    [|1|]
    [|1; 1|]
    [|1; 2; 1|]
    [|1; 3; 3; 1|]
    [|1; 4; 6; 4; 1|]
    [|1; 5; 10; 10; 5; 1|]
    [|1; 6; 15; 20; 15; 6; 1|]
    [|1; 7; 21; 35; 35; 21; 7; 1|]
    [|1; 8; 28; 56; 70; 56; 28; 8; 1|]
|]
```

## <a name="formatting-if-expressions"></a><span data-ttu-id="9d7f8-189">如果格式運算式</span><span class="sxs-lookup"><span data-stu-id="9d7f8-189">Formatting if expressions</span></span>

<span data-ttu-id="9d7f8-190">縮排的條件取決於它們構成的運算式的大小。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-190">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="9d7f8-191">如果`cond`，`e1`和`e2`簡短，只要將它們寫入在同一行：</span><span class="sxs-lookup"><span data-stu-id="9d7f8-191">If `cond`, `e1` and `e2` are short, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="9d7f8-192">如果有任一`cond`，`e1`或`e2`更久，但不多行：</span><span class="sxs-lookup"><span data-stu-id="9d7f8-192">If either `cond`, `e1` or `e2` are longer, but not multi-line:</span></span>

```fsharp
if cond
then e1
else e2
```

<span data-ttu-id="9d7f8-193">如果任何運算式是多行：</span><span class="sxs-lookup"><span data-stu-id="9d7f8-193">If any of the expressions are multi-line:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="9d7f8-194">使用多個條件`elif`並`else`縮排在相同範圍`if`:</span><span class="sxs-lookup"><span data-stu-id="9d7f8-194">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="9d7f8-195">模式比對建構</span><span class="sxs-lookup"><span data-stu-id="9d7f8-195">Pattern matching constructs</span></span>

<span data-ttu-id="9d7f8-196">使用`|`不縮排每個子句的相符項目。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-196">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="9d7f8-197">如果運算式很短，您可以考慮使用單一行，如果每一個子運算式也很簡單。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-197">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> _
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> _
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

<span data-ttu-id="9d7f8-198">如果在模式比對的箭號右側的運算式太大，將它移至下列這一行，縮排的一個步驟，從`match` / `|`。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-198">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="9d7f8-199">模式比對的匿名函式，來啟動`function`，應該通常不縮排牽扯太廣。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-199">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="9d7f8-200">例如，縮排一個範圍，如下所示沒關係：</span><span class="sxs-lookup"><span data-stu-id="9d7f8-200">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="9d7f8-201">模式比對中所定義的函式`let`或是`let rec`之後開始進行縮排的 4 個空格`let`，即使`function`關鍵字可用於：</span><span class="sxs-lookup"><span data-stu-id="9d7f8-201">Pattern matching in functions defined by `let` or `let rec` should be indented 4 spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="9d7f8-202">我們不建議對齊箭號。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-202">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="9d7f8-203">格式化的 try / with 運算式</span><span class="sxs-lookup"><span data-stu-id="9d7f8-203">Formatting try/with expressions</span></span>

<span data-ttu-id="9d7f8-204">模式比對的例外狀況類型應位於相同層級會縮排`with`。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-204">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

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

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="9d7f8-205">格式函式參數的應用程式</span><span class="sxs-lookup"><span data-stu-id="9d7f8-205">Formatting function parameter application</span></span>

<span data-ttu-id="9d7f8-206">一般而言，大部分函式參數的應用程式是在同一行。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-206">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="9d7f8-207">如果您想要套用至新的一行中的函式的參數，則由一個範圍縮排。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-207">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

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

<span data-ttu-id="9d7f8-208">函式引數的 lambda 運算式套用相同的指導方針。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-208">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="9d7f8-209">如果 lambda 運算式主體的主體可以有另一條，縮排一個範圍</span><span class="sxs-lookup"><span data-stu-id="9d7f8-209">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

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

<span data-ttu-id="9d7f8-210">不過，如果多行 lambda 運算式的主體，請考慮一下重構到個別函式而非已做為單一引數套用至函式的多行建構。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-210">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="9d7f8-211">格式化 中置運算子</span><span class="sxs-lookup"><span data-stu-id="9d7f8-211">Formatting infix operators</span></span>

<span data-ttu-id="9d7f8-212">以空格分開的運算子。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-212">Separate operators by spaces.</span></span> <span data-ttu-id="9d7f8-213">明顯的例外狀況，此規則會`!`和`.`運算子。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-213">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="9d7f8-214">中置運算式會為同一個資料行的組合中的 [確定]:</span><span class="sxs-lookup"><span data-stu-id="9d7f8-214">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="9d7f8-215">格式設定管線運算子</span><span class="sxs-lookup"><span data-stu-id="9d7f8-215">Formatting pipeline operators</span></span>

<span data-ttu-id="9d7f8-216">管線`|>`運算子都應下它們對的運算式。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-216">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

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

### <a name="formatting-modules"></a><span data-ttu-id="9d7f8-217">格式化的模組</span><span class="sxs-lookup"><span data-stu-id="9d7f8-217">Formatting modules</span></span>

<span data-ttu-id="9d7f8-218">在本機的模組中的程式碼必須相對於模組，縮排，但應該不會縮排在最上層模組中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-218">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="9d7f8-219">縮排沒有命名空間項目。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-219">Namespace elements do not have to be indented.</span></span>

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

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="9d7f8-220">格式化的物件運算式和介面</span><span class="sxs-lookup"><span data-stu-id="9d7f8-220">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="9d7f8-221">物件運算式和介面應該使用相同的方式對齊`member`正在後 4 個空格縮排。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-221">Object expressions and interfaces should be aligned in the same way with `member` being indented after 4 spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s : String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="9d7f8-222">設定格式化的運算式中的泛空白字元</span><span class="sxs-lookup"><span data-stu-id="9d7f8-222">Formatting white space in expressions</span></span>

<span data-ttu-id="9d7f8-223">避免多餘的空白字元在 F # 運算式。</span><span class="sxs-lookup"><span data-stu-id="9d7f8-223">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="9d7f8-224">具名引數也不應該周圍的空間`=`:</span><span class="sxs-lookup"><span data-stu-id="9d7f8-224">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```
