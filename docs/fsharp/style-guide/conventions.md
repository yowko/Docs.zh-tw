---
title: F# 編碼慣例
description: 編寫 F# 代碼時，請學習一般準則和習語。
ms.date: 01/15/2020
ms.openlocfilehash: 7266211e501bdb52564220781e2347d1aceaf296
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400306"
---
# <a name="f-coding-conventions"></a><span data-ttu-id="a5629-103">F# 編碼慣例</span><span class="sxs-lookup"><span data-stu-id="a5629-103">F# coding conventions</span></span>

<span data-ttu-id="a5629-104">以下約定是從使用大型 F# 代碼庫的經驗中制定的。</span><span class="sxs-lookup"><span data-stu-id="a5629-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="a5629-105">[好的 F# 代碼的五個原則](index.md#five-principles-of-good-f-code)是每個建議的基礎。</span><span class="sxs-lookup"><span data-stu-id="a5629-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="a5629-106">它們與[F# 元件設計指南](component-design-guidelines.md)相關，但適用于任何 F# 代碼，而不僅僅是庫等元件。</span><span class="sxs-lookup"><span data-stu-id="a5629-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="a5629-107">組織代碼</span><span class="sxs-lookup"><span data-stu-id="a5629-107">Organizing code</span></span>

<span data-ttu-id="a5629-108">F# 具有兩種組織代碼的主要方法：模組和命名空間。</span><span class="sxs-lookup"><span data-stu-id="a5629-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="a5629-109">這些相似，但確實有以下差異：</span><span class="sxs-lookup"><span data-stu-id="a5629-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="a5629-110">命名空間編譯為 .NET 命名空間。</span><span class="sxs-lookup"><span data-stu-id="a5629-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="a5629-111">模組編譯為靜態類。</span><span class="sxs-lookup"><span data-stu-id="a5629-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="a5629-112">命名空間始終是頂層。</span><span class="sxs-lookup"><span data-stu-id="a5629-112">Namespaces are always top level.</span></span> <span data-ttu-id="a5629-113">模組可以是頂級的，可以嵌套在其他模組中。</span><span class="sxs-lookup"><span data-stu-id="a5629-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="a5629-114">命名空間可以跨多個檔。</span><span class="sxs-lookup"><span data-stu-id="a5629-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="a5629-115">模組不能。</span><span class="sxs-lookup"><span data-stu-id="a5629-115">Modules cannot.</span></span>
* <span data-ttu-id="a5629-116">模組可以使用`[<RequireQualifiedAccess>]`和`[<AutoOpen>]`進行修飾。</span><span class="sxs-lookup"><span data-stu-id="a5629-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="a5629-117">以下指南將説明您使用這些準則來組織代碼。</span><span class="sxs-lookup"><span data-stu-id="a5629-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="a5629-118">首選頂層的命名空間</span><span class="sxs-lookup"><span data-stu-id="a5629-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="a5629-119">對於任何公共易用代碼，命名空間優先支援頂層模組。</span><span class="sxs-lookup"><span data-stu-id="a5629-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="a5629-120">因為它們編譯為 .NET 命名空間，因此它們可消耗來自 C#，沒有問題。</span><span class="sxs-lookup"><span data-stu-id="a5629-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="a5629-121">僅從 F# 調用時，使用頂級模組可能看起來不同，但對於 C# 消費者，調用方可能會因為必須符合`MyClass``MyCode`該模組的資格而感到驚訝。</span><span class="sxs-lookup"><span data-stu-id="a5629-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="a5629-122">小心塗抹`[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="a5629-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="a5629-123">構造`[<AutoOpen>]`會污染調用方可用的範圍，而對事物來源的答案是"神奇"。</span><span class="sxs-lookup"><span data-stu-id="a5629-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="a5629-124">這不是一件好事。</span><span class="sxs-lookup"><span data-stu-id="a5629-124">This is not a good thing.</span></span> <span data-ttu-id="a5629-125">此規則的一個例外是 F# 核心庫本身（儘管這一事實也有點爭議）。</span><span class="sxs-lookup"><span data-stu-id="a5629-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="a5629-126">但是，如果您具有公共 API 的説明器功能，您希望獨立于該公共 API 進行組織，則這樣做會很方便。</span><span class="sxs-lookup"><span data-stu-id="a5629-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

```fsharp
module MyAPI =
    [<AutoOpen>]
    module private Helpers =
        let helper1 x y z =
            ...

    let myFunction1 x =
        let y = ...
        let z = ...

        helper1 x y z
```

<span data-ttu-id="a5629-127">這樣，您就可以將實現詳細資訊與函數的公共 API 進行乾淨分離，而無需在每次調用協助程式時完全限定協助程式。</span><span class="sxs-lookup"><span data-stu-id="a5629-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="a5629-128">此外，在命名空間級別公開擴充方法和運算式產生器可以使用 整齊地表示。 `[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="a5629-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="a5629-129">每當`[<RequireQualifiedAccess>]`名稱可能發生衝突或您覺得它有助於可讀性時使用</span><span class="sxs-lookup"><span data-stu-id="a5629-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="a5629-130">將`[<RequireQualifiedAccess>]`屬性添加到模組表示可能無法打開模組，並且對模組元素的引用需要顯式限定訪問。</span><span class="sxs-lookup"><span data-stu-id="a5629-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="a5629-131">例如，`Microsoft.FSharp.Collections.List`模組具有此屬性。</span><span class="sxs-lookup"><span data-stu-id="a5629-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="a5629-132">當模組中的函數和值具有可能與其他模組中的名稱衝突的名稱時，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="a5629-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="a5629-133">要求合格的訪問可以大大提高庫的長期可維護性和可進化性。</span><span class="sxs-lookup"><span data-stu-id="a5629-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="a5629-134">從`open`拓撲上對語句進行排序</span><span class="sxs-lookup"><span data-stu-id="a5629-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="a5629-135">在 F#中，聲明的順序很重要，包括與語句一`open`起。</span><span class="sxs-lookup"><span data-stu-id="a5629-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="a5629-136">這與 C# 不同，C#`using``using static`的影響與檔中這些語句的順序無關。</span><span class="sxs-lookup"><span data-stu-id="a5629-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="a5629-137">在 F# 中，打開到作用域中的元素可能會隱藏其他已經存在的元素。</span><span class="sxs-lookup"><span data-stu-id="a5629-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="a5629-138">這意味著重新排序`open`語句可能會更改代碼的含義。</span><span class="sxs-lookup"><span data-stu-id="a5629-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="a5629-139">因此，不建議對所有`open`語句進行任何任意排序（例如，以 Alpha 數位方式排序），以免生成您可能期望的不同行為。</span><span class="sxs-lookup"><span data-stu-id="a5629-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="a5629-140">相反，我們建議您[按拓撲分類](https://en.wikipedia.org/wiki/Topological_sorting)它們;也就是說，按定義系統`open`_圖層_的順序對語句進行排序。</span><span class="sxs-lookup"><span data-stu-id="a5629-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="a5629-141">也可以考慮在不同的拓撲層內進行字母數位排序。</span><span class="sxs-lookup"><span data-stu-id="a5629-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="a5629-142">例如，下面是 F# 編譯器服務公共 API 檔的拓撲排序：</span><span class="sxs-lookup"><span data-stu-id="a5629-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

```fsharp
namespace Microsoft.FSharp.Compiler.SourceCodeServices

open System
open System.Collections.Generic
open System.Collections.Concurrent
open System.Diagnostics
open System.IO
open System.Reflection
open System.Text

open Microsoft.FSharp.Compiler
open Microsoft.FSharp.Compiler.AbstractIL
open Microsoft.FSharp.Compiler.AbstractIL.Diagnostics
open Microsoft.FSharp.Compiler.AbstractIL.IL
open Microsoft.FSharp.Compiler.AbstractIL.ILBinaryReader
open Microsoft.FSharp.Compiler.AbstractIL.Internal
open Microsoft.FSharp.Compiler.AbstractIL.Internal.Library

open Microsoft.FSharp.Compiler.AccessibilityLogic
open Microsoft.FSharp.Compiler.Ast
open Microsoft.FSharp.Compiler.CompileOps
open Microsoft.FSharp.Compiler.CompileOptions
open Microsoft.FSharp.Compiler.Driver
open Microsoft.FSharp.Compiler.ErrorLogger
open Microsoft.FSharp.Compiler.Infos
open Microsoft.FSharp.Compiler.InfoReader
open Microsoft.FSharp.Compiler.Lexhelp
open Microsoft.FSharp.Compiler.Layout
open Microsoft.FSharp.Compiler.Lib
open Microsoft.FSharp.Compiler.NameResolution
open Microsoft.FSharp.Compiler.PrettyNaming
open Microsoft.FSharp.Compiler.Parser
open Microsoft.FSharp.Compiler.Range
open Microsoft.FSharp.Compiler.Tast
open Microsoft.FSharp.Compiler.Tastops
open Microsoft.FSharp.Compiler.TcGlobals
open Microsoft.FSharp.Compiler.TypeChecker
open Microsoft.FSharp.Compiler.SourceCodeServices.SymbolHelpers

open Internal.Utilities
open Internal.Utilities.Collections
```

<span data-ttu-id="a5629-143">請注意，分行符號將拓撲圖層分開，之後將按字母數位對每一層進行排序。</span><span class="sxs-lookup"><span data-stu-id="a5629-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="a5629-144">這樣可以乾淨地組織代碼，而不會意外地隱藏值。</span><span class="sxs-lookup"><span data-stu-id="a5629-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="a5629-145">使用類包含具有副作用的值</span><span class="sxs-lookup"><span data-stu-id="a5629-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="a5629-146">初始化值很多時候會產生副作用，例如將上下文具現化到資料庫或其他遠端資源。</span><span class="sxs-lookup"><span data-stu-id="a5629-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="a5629-147">在模組中初始化此類內容並將其用於後續函數是很有誘惑力的：</span><span class="sxs-lookup"><span data-stu-id="a5629-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

```fsharp
// This is bad!
module MyApi =
    let dep1 = File.ReadAllText "/Users/{your name}/connectionstring.txt"
    let dep2 = Environment.GetEnvironmentVariable "DEP_2"

    let private r = Random()
    let dep3() = r.Next() // Problematic if multiple threads use this

    let function1 arg = doStuffWith dep1 dep2 dep3 arg
    let function2 arg = doSutffWith dep1 dep2 dep3 arg
```

<span data-ttu-id="a5629-148">由於幾個原因，這通常是一個壞主意：</span><span class="sxs-lookup"><span data-stu-id="a5629-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="a5629-149">首先，應用程式佈建被推送到 代碼庫中`dep1`， `dep2`</span><span class="sxs-lookup"><span data-stu-id="a5629-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="a5629-150">這在較大的代碼庫中很難維護。</span><span class="sxs-lookup"><span data-stu-id="a5629-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="a5629-151">其次，靜態初始化資料不應包括不安全的執行緒值（如果元件本身將使用多個執行緒）。</span><span class="sxs-lookup"><span data-stu-id="a5629-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="a5629-152">這顯然被`dep3`違反。</span><span class="sxs-lookup"><span data-stu-id="a5629-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="a5629-153">最後，模組初始化編譯為整個編譯單元的靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="a5629-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="a5629-154">如果該模組中的允許綁定值初始化中出現任何錯誤，則該初始化將表現為`TypeInitializationException`然後緩存整個應用程式的存留期。</span><span class="sxs-lookup"><span data-stu-id="a5629-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="a5629-155">這可能很難診斷。</span><span class="sxs-lookup"><span data-stu-id="a5629-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="a5629-156">通常有一個內部異常，你可以嘗試推理，但如果沒有，那麼沒有告訴根本原因是什麼。</span><span class="sxs-lookup"><span data-stu-id="a5629-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="a5629-157">相反，只需使用簡單類來保存依賴項：</span><span class="sxs-lookup"><span data-stu-id="a5629-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member _.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member _.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="a5629-158">這支援以下功能：</span><span class="sxs-lookup"><span data-stu-id="a5629-158">This enables the following:</span></span>

1. <span data-ttu-id="a5629-159">將任何從屬狀態推送到 API 本身之外。</span><span class="sxs-lookup"><span data-stu-id="a5629-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="a5629-160">配置現在可以在 API 之外完成。</span><span class="sxs-lookup"><span data-stu-id="a5629-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="a5629-161">從屬值的初始化錯誤不太可能表現為`TypeInitializationException`。</span><span class="sxs-lookup"><span data-stu-id="a5629-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="a5629-162">API 現在更易於測試。</span><span class="sxs-lookup"><span data-stu-id="a5629-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="a5629-163">錯誤管理</span><span class="sxs-lookup"><span data-stu-id="a5629-163">Error management</span></span>

<span data-ttu-id="a5629-164">大型系統中的錯誤管理是一項複雜而細緻的工作，在確保系統具有容錯性和良好行為方面沒有銀彈。</span><span class="sxs-lookup"><span data-stu-id="a5629-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="a5629-165">以下指南應為導航此困難空間提供指導。</span><span class="sxs-lookup"><span data-stu-id="a5629-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="a5629-166">在域固有的類型中表示錯誤案例和非法狀態</span><span class="sxs-lookup"><span data-stu-id="a5629-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="a5629-167">使用["歧視聯合"，F#](../language-reference/discriminated-unions.md)使您能夠在類型系統中表示錯誤的程式狀態。</span><span class="sxs-lookup"><span data-stu-id="a5629-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="a5629-168">例如：</span><span class="sxs-lookup"><span data-stu-id="a5629-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="a5629-169">在這種情況下，有三種已知方式從銀行帳戶提取資金可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="a5629-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="a5629-170">每個錯誤案例都以類型表示，因此可以在整個程式中安全地處理。</span><span class="sxs-lookup"><span data-stu-id="a5629-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="a5629-171">通常，如果可以對域中某些內容可能**失敗**的不同方式進行建模，則錯誤處理代碼不再被視為除常規程式流之外必須處理的內容。</span><span class="sxs-lookup"><span data-stu-id="a5629-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="a5629-172">它只是正常程式流的一部分，不被認為是**例外**。</span><span class="sxs-lookup"><span data-stu-id="a5629-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="a5629-173">這有兩個主要好處：</span><span class="sxs-lookup"><span data-stu-id="a5629-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="a5629-174">隨著域隨時間的變化而更易於維護。</span><span class="sxs-lookup"><span data-stu-id="a5629-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="a5629-175">錯誤案例更易於單元測試。</span><span class="sxs-lookup"><span data-stu-id="a5629-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="a5629-176">當無法用類型表示錯誤時，請使用異常</span><span class="sxs-lookup"><span data-stu-id="a5629-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="a5629-177">並非所有錯誤都可以在問題域中表示。</span><span class="sxs-lookup"><span data-stu-id="a5629-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="a5629-178">這些類型的故障在性質上*是例外*的，因此能夠提高和捕獲 F# 中的異常。</span><span class="sxs-lookup"><span data-stu-id="a5629-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="a5629-179">首先，建議您閱讀[例外設計指南](../../standard/design-guidelines/exceptions.md)。</span><span class="sxs-lookup"><span data-stu-id="a5629-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="a5629-180">這些也適用于 F#。</span><span class="sxs-lookup"><span data-stu-id="a5629-180">These are also applicable to F#.</span></span>

<span data-ttu-id="a5629-181">F# 中用於引發異常的主要構造應考慮以下首選項順序：</span><span class="sxs-lookup"><span data-stu-id="a5629-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="a5629-182">函式</span><span class="sxs-lookup"><span data-stu-id="a5629-182">Function</span></span> | <span data-ttu-id="a5629-183">語法</span><span class="sxs-lookup"><span data-stu-id="a5629-183">Syntax</span></span> | <span data-ttu-id="a5629-184">目的</span><span class="sxs-lookup"><span data-stu-id="a5629-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="a5629-185">使用指定的`System.ArgumentNullException`參數名稱引發 a。</span><span class="sxs-lookup"><span data-stu-id="a5629-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="a5629-186">使用指定的`System.ArgumentException`參數名稱和消息引發 。</span><span class="sxs-lookup"><span data-stu-id="a5629-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="a5629-187">使用指定`System.InvalidOperationException`的消息引發 a。</span><span class="sxs-lookup"><span data-stu-id="a5629-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="a5629-188">用於引發異常的通用機制。</span><span class="sxs-lookup"><span data-stu-id="a5629-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="a5629-189">使用指定`System.Exception`的消息引發 a。</span><span class="sxs-lookup"><span data-stu-id="a5629-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="a5629-190">使用格式`System.Exception`字串及其輸入確定的消息引發 。</span><span class="sxs-lookup"><span data-stu-id="a5629-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="a5629-191">使用`nullArg` `invalidArg` ，`invalidOp`並作為投擲`ArgumentNullException`的機制，`ArgumentException`並在`InvalidOperationException`適當時使用 。</span><span class="sxs-lookup"><span data-stu-id="a5629-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="a5629-192">通常`failwith`應避免`failwithf`和 函數，因為它們會引發基`Exception`類型，而不是特定的異常。</span><span class="sxs-lookup"><span data-stu-id="a5629-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="a5629-193">根據[例外設計指南](../../standard/design-guidelines/exceptions.md)，您希望在可以時提出更具體的異常。</span><span class="sxs-lookup"><span data-stu-id="a5629-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="using-exception-handling-syntax"></a><span data-ttu-id="a5629-194">使用異常處理語法</span><span class="sxs-lookup"><span data-stu-id="a5629-194">Using exception-handling syntax</span></span>

<span data-ttu-id="a5629-195">F# 通過`try...with`語法支援異常模式：</span><span class="sxs-lookup"><span data-stu-id="a5629-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="a5629-196">如果要保持代碼整潔，在面對模式匹配的異常時要執行的功能可能會有點棘手。</span><span class="sxs-lookup"><span data-stu-id="a5629-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="a5629-197">處理這種情況的一種方法是使用[活動模式](../language-reference/active-patterns.md)作為將圍繞錯誤案例的功能分組具有異常本身的方法。</span><span class="sxs-lookup"><span data-stu-id="a5629-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="a5629-198">例如，您可能正在使用 API，當它引發異常時，該 API 會將有價值的資訊包含在異常中繼資料中。</span><span class="sxs-lookup"><span data-stu-id="a5629-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="a5629-199">在某些情況下，在活動模式內展開捕獲的異常正文中的有用值並返回該值可能會有所説明。</span><span class="sxs-lookup"><span data-stu-id="a5629-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="a5629-200">請勿使用單體錯誤處理來替換異常</span><span class="sxs-lookup"><span data-stu-id="a5629-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="a5629-201">異常在函數式程式設計中被視為一些禁忌。</span><span class="sxs-lookup"><span data-stu-id="a5629-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="a5629-202">事實上，異常會侵犯純度，因此可以放心地考慮它們不太有效。</span><span class="sxs-lookup"><span data-stu-id="a5629-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="a5629-203">但是，這忽略了代碼必須運行的位置，並且可能發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="a5629-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="a5629-204">通常，編寫代碼時假定大多數事物既不是純的也不是完全的，以儘量減少令人不快的意外。</span><span class="sxs-lookup"><span data-stu-id="a5629-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="a5629-205">在 .NET 運行時和整個跨語言生態系統中的相關性和適當性方面，必須考慮異常的以下核心優勢/方面：</span><span class="sxs-lookup"><span data-stu-id="a5629-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="a5629-206">它們包含詳細的診斷資訊，這在調試問題時非常有用。</span><span class="sxs-lookup"><span data-stu-id="a5629-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="a5629-207">運行時和其他 .NET 語言都很好地理解它們。</span><span class="sxs-lookup"><span data-stu-id="a5629-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="a5629-208">與通過臨時實現語義的某些子集來*避免*異常的代碼相比，它們可以減少重要的樣板。</span><span class="sxs-lookup"><span data-stu-id="a5629-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="a5629-209">第三點至關重要。</span><span class="sxs-lookup"><span data-stu-id="a5629-209">This third point is critical.</span></span> <span data-ttu-id="a5629-210">對於不處理非大型複雜操作，不使用異常可能會導致處理這樣的結構：</span><span class="sxs-lookup"><span data-stu-id="a5629-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="a5629-211">這很容易導致脆弱的代碼，如模式匹配的"字串類型"錯誤：</span><span class="sxs-lookup"><span data-stu-id="a5629-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="a5629-212">此外，對於返回"更好"類型的"簡單"函數的渴望，可以接受任何異常是很有誘惑力的：</span><span class="sxs-lookup"><span data-stu-id="a5629-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="a5629-213">遺憾的是，`tryReadAllText`可以基於檔案系統上可能發生的無數事情引發大量異常，並且此代碼會丟棄有關環境中實際出錯的任何資訊。</span><span class="sxs-lookup"><span data-stu-id="a5629-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="a5629-214">如果使用此代碼類型替換此代碼，則返回"字串鍵入"錯誤訊息分析：</span><span class="sxs-lookup"><span data-stu-id="a5629-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Ok
    with e -> Error e.Message

let r = tryReadAllText "path-to-file"
match r with
| Ok text -> ...
| Error e ->
    if e.Contains "uh oh, here we go again..." then ...
    else ...
```

<span data-ttu-id="a5629-215">將異常物件本身放在建構函式中`Error`只會強制您在調用網站而不是函數中正確處理異常類型。</span><span class="sxs-lookup"><span data-stu-id="a5629-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="a5629-216">這樣做可以有效地創建已檢查的異常，這些異常作為 API 的調用方處理起來非常不有趣。</span><span class="sxs-lookup"><span data-stu-id="a5629-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="a5629-217">上述示例的一個很好的替代方法是在該異常上下文中捕獲*特定*異常並返回有意義的值。</span><span class="sxs-lookup"><span data-stu-id="a5629-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="a5629-218">如果修改函數`tryReadAllText`如下所示，`None`則具有更多含義：</span><span class="sxs-lookup"><span data-stu-id="a5629-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="a5629-219">現在，當找不到檔並將該含義分配給返回時，此函數將正確處理案例，而不是充當"全部捕獲"功能。</span><span class="sxs-lookup"><span data-stu-id="a5629-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="a5629-220">此傳回值可以映射到該錯誤情況，同時不會放棄任何上下文資訊或強制調用方處理代碼中此時可能不相關的案例。</span><span class="sxs-lookup"><span data-stu-id="a5629-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="a5629-221">類型（如`Result<'Success, 'Error>`適用于未嵌套的基本操作）和 F# 可選類型非常適合表示某些內容可以返回*或\*\*什麼都不*返回時。</span><span class="sxs-lookup"><span data-stu-id="a5629-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="a5629-222">但是，它們不是異常的替換，不應用於嘗試替換異常。</span><span class="sxs-lookup"><span data-stu-id="a5629-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="a5629-223">相反，應明智地應用它們，以有針對性的方式處理異常和錯誤管理政策的具體方面。</span><span class="sxs-lookup"><span data-stu-id="a5629-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="a5629-224">部分應用和無點程式設計</span><span class="sxs-lookup"><span data-stu-id="a5629-224">Partial application and point-free programming</span></span>

<span data-ttu-id="a5629-225">F# 支援部分應用程式，因此，以各種方式以無點樣式進行程式設計。</span><span class="sxs-lookup"><span data-stu-id="a5629-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="a5629-226">這有利於模組內的代碼重用或某些內容的實現，但這不是公開的內容。</span><span class="sxs-lookup"><span data-stu-id="a5629-226">This can be beneficial for code reuse within a module or the implementation of something, but it is not something to expose publicly.</span></span> <span data-ttu-id="a5629-227">一般來說，無點程式設計本身並不是一種美德，它可以為不沉浸于這種風格的人增加一個重大的認知障礙。</span><span class="sxs-lookup"><span data-stu-id="a5629-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="a5629-228">請勿在公共 API 中使用部分應用程式和咖喱</span><span class="sxs-lookup"><span data-stu-id="a5629-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="a5629-229">除了很少的情況外，在公共 API 中使用部分應用程式可能會令消費者感到困惑。</span><span class="sxs-lookup"><span data-stu-id="a5629-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="a5629-230">通常，F#`let`代碼中的綁定值是**值**，而不是**函數值**。</span><span class="sxs-lookup"><span data-stu-id="a5629-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="a5629-231">將值和函數值混合在一起可以節省少量程式碼，以換取相當多的認知開銷，特別是如果與組合函數等`>>`運算子結合使用時。</span><span class="sxs-lookup"><span data-stu-id="a5629-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="a5629-232">考慮無點程式設計的工具含義</span><span class="sxs-lookup"><span data-stu-id="a5629-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="a5629-233">庫瑞德函數不標記其參數。</span><span class="sxs-lookup"><span data-stu-id="a5629-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="a5629-234">這具有工具含義。</span><span class="sxs-lookup"><span data-stu-id="a5629-234">This has tooling implications.</span></span> <span data-ttu-id="a5629-235">請考慮以下兩個函數：</span><span class="sxs-lookup"><span data-stu-id="a5629-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="a5629-236">兩者都是有效的函數，`funcWithApplication`但都是一個咖喱函數。</span><span class="sxs-lookup"><span data-stu-id="a5629-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="a5629-237">當您在編輯器中懸停在它們的類型上時，您將看到：</span><span class="sxs-lookup"><span data-stu-id="a5629-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="a5629-238">在呼叫網站，Visual Studio 等工具工具提示不會為您提供有關`string`和`int`輸入類型實際表示的內容的有意義的資訊。</span><span class="sxs-lookup"><span data-stu-id="a5629-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="a5629-239">如果您遇到這樣的`funcWithApplication`無點代碼是公共易用的，建議執行完全 +擴展，以便工具可以獲取有意義的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="a5629-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="a5629-240">此外，調試無點代碼可能具有挑戰性，如果不是不可能的話。</span><span class="sxs-lookup"><span data-stu-id="a5629-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="a5629-241">調試工具依賴于綁定到名稱的值（例如綁定`let`），以便在執行中途檢查中間值。</span><span class="sxs-lookup"><span data-stu-id="a5629-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="a5629-242">當代碼沒有要檢查的值時，將沒有任何要調試的值。</span><span class="sxs-lookup"><span data-stu-id="a5629-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="a5629-243">將來，調試工具可能會根據以前執行的路徑來合成這些值，但最好對*潛在的*調試功能進行對沖。</span><span class="sxs-lookup"><span data-stu-id="a5629-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="a5629-244">將部分應用視為減少內部樣板的技術</span><span class="sxs-lookup"><span data-stu-id="a5629-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="a5629-245">與前一點不同，部分應用程式是減少應用程式內部的樣板或 API 的深層內部的絕妙工具。</span><span class="sxs-lookup"><span data-stu-id="a5629-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="a5629-246">對於單元測試更複雜的 API 的實現很有説明，其中樣板通常需要處理。</span><span class="sxs-lookup"><span data-stu-id="a5629-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="a5629-247">例如，以下代碼演示如何完成大多數類比框架所賦予您的內容，而無需對此類框架進行外部依賴，並且必須學習相關的定制 API。</span><span class="sxs-lookup"><span data-stu-id="a5629-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="a5629-248">例如，請考慮以下解決方案地形：</span><span class="sxs-lookup"><span data-stu-id="a5629-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

<span data-ttu-id="a5629-249">`ImplementationLogic.fsproj`可能會公開代碼，例如：</span><span class="sxs-lookup"><span data-stu-id="a5629-249">`ImplementationLogic.fsproj` might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member _.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="a5629-250">單元`ImplementationLogic.Tests.fsproj`測試`Transactions.doTransaction`非常簡單：</span><span class="sxs-lookup"><span data-stu-id="a5629-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fsproj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="a5629-251">使用類比`doTransaction`上下文物件進行部分應用允許您在所有單元測試中調用函數，而無需每次都構造類比上下文：</span><span class="sxs-lookup"><span data-stu-id="a5629-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

```fsharp
namespace TransactionTests

open Xunit
open TransactionTypes
open TransactionsTestingUtil
open TransactionsTestingUtil.TransactionsTestable

let testableContext =
    { new ITransactionContext with
        member _.TheFirstMember() = ...
        member _.TheSecondMember() = ... }

let transactionRoutine = getTestableTransactionRoutine testableContext

[<Fact>]
let ``Test withdrawal transaction with 0.0 for balance``() =
    let expected = ...
    let actual = transactionRoutine TransactionType.Withdraw 0.0
    Assert.Equal(expected, actual)
```

<span data-ttu-id="a5629-252">此技術不應普遍應用於整個代碼庫，但它是減少複雜內部和單元測試這些內部的樣板的好方法。</span><span class="sxs-lookup"><span data-stu-id="a5629-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="a5629-253">存取控制</span><span class="sxs-lookup"><span data-stu-id="a5629-253">Access control</span></span>

<span data-ttu-id="a5629-254">F# 具有多個[存取控制](../language-reference/access-control.md)選項，從 .NET 運行時中可用的選項繼承。</span><span class="sxs-lookup"><span data-stu-id="a5629-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="a5629-255">這些不僅可用於類型 - 您也可以將它們用於函數。</span><span class="sxs-lookup"><span data-stu-id="a5629-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="a5629-256">首選非`public`類型和成員，直到您需要它們是公共消耗品。</span><span class="sxs-lookup"><span data-stu-id="a5629-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="a5629-257">這也最大限度地減少了消費者對之的耦合。</span><span class="sxs-lookup"><span data-stu-id="a5629-257">This also minimizes what consumers couple to.</span></span>
* <span data-ttu-id="a5629-258">努力保持所有説明器的功能`private`。</span><span class="sxs-lookup"><span data-stu-id="a5629-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="a5629-259">請考慮在説明器`[<AutoOpen>]`函數的專用模組上使用這些函數（如果它們變為大量）。</span><span class="sxs-lookup"><span data-stu-id="a5629-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="a5629-260">型別推斷和泛型</span><span class="sxs-lookup"><span data-stu-id="a5629-260">Type inference and generics</span></span>

<span data-ttu-id="a5629-261">型別推斷可以節省您輸入大量樣板。</span><span class="sxs-lookup"><span data-stu-id="a5629-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="a5629-262">F# 編譯器中的自動泛化可以説明您編寫更通用的代碼，而您幾乎不需要額外的工作。</span><span class="sxs-lookup"><span data-stu-id="a5629-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="a5629-263">但是，這些功能並非普遍良好。</span><span class="sxs-lookup"><span data-stu-id="a5629-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="a5629-264">請考慮在公共 API 中標記具有顯式類型的參數名稱，並且不要為此依賴類型推斷。</span><span class="sxs-lookup"><span data-stu-id="a5629-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="a5629-265">原因是**您應該**控制 API 的形狀，而不是編譯器。</span><span class="sxs-lookup"><span data-stu-id="a5629-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="a5629-266">儘管編譯器可以出色地推斷類型，但如果它所依賴的內部類型已更改，則 API 的形狀可能會發生變化。</span><span class="sxs-lookup"><span data-stu-id="a5629-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="a5629-267">這可能是你想要的，但它幾乎肯定會導致一個突破的API更改，然後下游消費者將不得不處理。</span><span class="sxs-lookup"><span data-stu-id="a5629-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="a5629-268">相反，如果您顯式控制公共 API 的形狀，則可以控制這些重大更改。</span><span class="sxs-lookup"><span data-stu-id="a5629-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="a5629-269">用 DDD 術語來說，這可以被視為反腐敗層。</span><span class="sxs-lookup"><span data-stu-id="a5629-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="a5629-270">請考慮為泛型參數指定一個有意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="a5629-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="a5629-271">除非您正在編寫不特定于特定域的真正通用代碼，否則有意義的名稱可以説明其他程式師瞭解他們正在處理的域。</span><span class="sxs-lookup"><span data-stu-id="a5629-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="a5629-272">例如，在與文檔資料庫交互的`'Document`上下文中命名的類型參數使正在使用的函數或成員可以接受通用文件類型更加清晰。</span><span class="sxs-lookup"><span data-stu-id="a5629-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="a5629-273">請考慮使用 PascalCase 命名泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="a5629-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="a5629-274">這是在 .NET 中執行操作的一般方法，因此建議您使用 PascalCase 而不是snake_case或駱駝Case。</span><span class="sxs-lookup"><span data-stu-id="a5629-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="a5629-275">最後，對於 F# 或大型代碼庫的新增人員而言，自動泛化並不總是一個福音。</span><span class="sxs-lookup"><span data-stu-id="a5629-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="a5629-276">使用萬用群組件存在認知開銷。</span><span class="sxs-lookup"><span data-stu-id="a5629-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="a5629-277">此外，如果自動通用化函數不用於不同的輸入類型（更不用說它們打算用作此類函數），那麼在那個時間點，它們是泛型函數沒有實際的好處。</span><span class="sxs-lookup"><span data-stu-id="a5629-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="a5629-278">始終考慮您編寫的代碼是否實際上將受益于泛型。</span><span class="sxs-lookup"><span data-stu-id="a5629-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="a5629-279">效能</span><span class="sxs-lookup"><span data-stu-id="a5629-279">Performance</span></span>

### <a name="prefer-structs-for-small-data-types"></a><span data-ttu-id="a5629-280">首選小型資料類型的結構</span><span class="sxs-lookup"><span data-stu-id="a5629-280">Prefer structs for small data types</span></span>

<span data-ttu-id="a5629-281">使用結構（也稱為數值型別）通常會導致某些代碼的性能更高，因為它通常避免分配物件。</span><span class="sxs-lookup"><span data-stu-id="a5629-281">Using structs (also called Value Types) can often result in higher performance for some code because it typically avoids allocating objects.</span></span> <span data-ttu-id="a5629-282">但是，結構並不總是一個"更快"按鈕：如果結構中的資料大小超過 16 個位元組，則複製資料通常會導致比使用參考型別花費更多的 CPU 時間。</span><span class="sxs-lookup"><span data-stu-id="a5629-282">However, structs are not always a "go faster" button: if the size of the data in a struct exceeds 16 bytes, copying the data can often result in more CPU time spend than using a reference type.</span></span>

<span data-ttu-id="a5629-283">要確定是否應使用結構，請考慮以下條件：</span><span class="sxs-lookup"><span data-stu-id="a5629-283">To determine if you should use a struct, consider the following conditions:</span></span>

- <span data-ttu-id="a5629-284">如果資料的大小為 16 位元組或更小。</span><span class="sxs-lookup"><span data-stu-id="a5629-284">If the size of your data is 16 bytes or smaller.</span></span>
- <span data-ttu-id="a5629-285">如果運行程式中的記憶體中可能有許多此類資料類型駐留在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="a5629-285">If you're likely to have many of these data types resident in memory in a running program.</span></span>

<span data-ttu-id="a5629-286">如果應用第一個條件，通常應使用結構。</span><span class="sxs-lookup"><span data-stu-id="a5629-286">If the first condition applies, you should generally use a struct.</span></span> <span data-ttu-id="a5629-287">如果兩者都適用，您幾乎總是應該使用結構。</span><span class="sxs-lookup"><span data-stu-id="a5629-287">If both apply, you should almost always use a struct.</span></span> <span data-ttu-id="a5629-288">可能在某些情況下，應用前面的條件，但使用結構並不比使用參考型別更好或更差，但它們可能很少見。</span><span class="sxs-lookup"><span data-stu-id="a5629-288">There may be some cases where the previous conditions apply, but using a struct is no better or worse than using a reference type, but they are likely to be rare.</span></span> <span data-ttu-id="a5629-289">但是，在進行這樣的更改時，始終要衡量，而不是根據假設或直覺行事，這一點很重要。</span><span class="sxs-lookup"><span data-stu-id="a5629-289">It's important to always measure when making changes like this, though, and not operate on assumption or intuition.</span></span>

#### <a name="prefer-struct-tuples-when-grouping-small-value-types"></a><span data-ttu-id="a5629-290">在分組小數值型別時，首選結構組合</span><span class="sxs-lookup"><span data-stu-id="a5629-290">Prefer struct tuples when grouping small value types</span></span>

<span data-ttu-id="a5629-291">請考慮以下兩個函數：</span><span class="sxs-lookup"><span data-stu-id="a5629-291">Consider the following two functions:</span></span>

```fsharp
let rec runWithTuple t offset times =
    let offsetValues x y z offset =
        (x + offset, y + offset, z + offset)

    if times <= 0 then
        t
    else
        let (x, y, z) = t
        let r = offsetValues x y z offset
        runWithTuple r offset (times - 1)

let rec runWithStructTuple t offset times =
    let offsetValues x y z offset =
        struct(x + offset, y + offset, z + offset)

    if times <= 0 then
        t
    else
        let struct(x, y, z) = t
        let r = offsetValues x y z offset
        runWithStructTuple r offset (times - 1)
```

<span data-ttu-id="a5629-292">當您使用基準資料測試控管（如[基準點網](https://benchmarkdotnet.org/)）對這些函數進行基準測試時，您會發現使用`runWithStructTuple`結構元數的函數運行速度要快 40%，並且不分配記憶體。</span><span class="sxs-lookup"><span data-stu-id="a5629-292">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that the `runWithStructTuple` function that uses struct tuples runs 40% faster and allocates no memory.</span></span>

<span data-ttu-id="a5629-293">但是，這些結果並不總是在您自己的代碼中如此。</span><span class="sxs-lookup"><span data-stu-id="a5629-293">However, these results won't always be the case in your own code.</span></span> <span data-ttu-id="a5629-294">如果將函數標記為`inline`，使用參考元數的代碼可能會獲得一些額外的優化，或者分配的代碼可以簡單地進行優化。</span><span class="sxs-lookup"><span data-stu-id="a5629-294">If you mark a function as `inline`, code that uses reference tuples may get some additional optimizations, or code that would allocate could simply be optimized away.</span></span> <span data-ttu-id="a5629-295">您應該始終在績效方面衡量結果，並且絕不基於假設或直覺操作。</span><span class="sxs-lookup"><span data-stu-id="a5629-295">You should always measure results whenever performance is concerned, and never operate based on assumption or intuition.</span></span>

#### <a name="prefer-struct-records-when-the-data-type-is-small"></a><span data-ttu-id="a5629-296">資料類型較小時更喜歡結構記錄</span><span class="sxs-lookup"><span data-stu-id="a5629-296">Prefer struct records when the data type is small</span></span>

<span data-ttu-id="a5629-297">前面描述的經驗法則也適用于[F# 記錄類型](../language-reference/records.md)。</span><span class="sxs-lookup"><span data-stu-id="a5629-297">The rule of thumb described earlier also holds for [F# record types](../language-reference/records.md).</span></span> <span data-ttu-id="a5629-298">請考慮處理它們的以下資料類型和函數：</span><span class="sxs-lookup"><span data-stu-id="a5629-298">Consider the following data types and functions that process them:</span></span>

```fsharp
type Point = { X: float; Y: float; Z: float }

[<Struct>]
type SPoint = { X: float; Y: float; Z: float }

let rec processPoint (p: Point) offset times =
    let inline offsetValues (p: Point) offset =
        { p with X = p.X + offset; Y = p.Y + offset; Z = p.Z + offset }

    if times <= 0 then
        p
    else
        let r = offsetValues p offset
        processPoint r offset (times - 1)

let rec processStructPoint (p: SPoint) offset times =
    let inline offsetValues (p: SPoint) offset =
        { p with X = p.X + offset; Y = p.Y + offset; Z = p.Z + offset }

    if times <= 0 then
        p
    else
        let r = offsetValues p offset
        processStructPoint r offset (times - 1)
```

<span data-ttu-id="a5629-299">這與前面的元組代碼類似，但這次示例使用記錄和內聯內建函式。</span><span class="sxs-lookup"><span data-stu-id="a5629-299">This is similar to the previous tuple code, but this time the example uses records and an inlined inner function.</span></span>

<span data-ttu-id="a5629-300">當您使用基準資料測試控管（如[基準點網](https://benchmarkdotnet.org/)）對這些函數進行基準測試時，您會發現`processStructPoint`運行速度接近 60%，並且在託管堆上不分配任何內容。</span><span class="sxs-lookup"><span data-stu-id="a5629-300">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that `processStructPoint` runs nearly 60% faster and allocates nothing on the managed heap.</span></span>

#### <a name="prefer-struct-discriminated-unions-when-the-data-type-is-small"></a><span data-ttu-id="a5629-301">在資料類型較小時，首選結構區分結合</span><span class="sxs-lookup"><span data-stu-id="a5629-301">Prefer struct discriminated unions when the data type is small</span></span>

<span data-ttu-id="a5629-302">以前關於具有結構元數和記錄的表現的觀察也適用于[F_ 歧視聯盟](../language-reference/discriminated-unions.md)。</span><span class="sxs-lookup"><span data-stu-id="a5629-302">The previous observations about performance with struct tuples and records also holds for [F# Discriminated Unions](../language-reference/discriminated-unions.md).</span></span> <span data-ttu-id="a5629-303">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="a5629-303">Consider the following code:</span></span>

```fsharp
    type Name = Name of string

    [<Struct>]
    type SName = SName of string

    let reverseName (Name s) =
        s.ToCharArray()
        |> Array.rev
        |> string
        |> Name

    let structReverseName (SName s) =
        s.ToCharArray()
        |> Array.rev
        |> string
        |> SName
```

<span data-ttu-id="a5629-304">為域建模定義像這樣的單一案例"歧視聯合"很常見。</span><span class="sxs-lookup"><span data-stu-id="a5629-304">It's common to define single-case Discriminated Unions like this for domain modeling.</span></span> <span data-ttu-id="a5629-305">當您使用基準資料測試控管（如[基準點網](https://benchmarkdotnet.org/)）對這些函數進行基準測試時，您會發現`structReverseName`運行速度比`reverseName`小字串快 25%。</span><span class="sxs-lookup"><span data-stu-id="a5629-305">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that `structReverseName` runs about 25% faster than `reverseName` for small strings.</span></span> <span data-ttu-id="a5629-306">對於大字串，兩者執行大致相同。</span><span class="sxs-lookup"><span data-stu-id="a5629-306">For large strings, both perform about the same.</span></span> <span data-ttu-id="a5629-307">因此，在這種情況下，最好使用結構。</span><span class="sxs-lookup"><span data-stu-id="a5629-307">So, in this case, it's always preferable to use a struct.</span></span> <span data-ttu-id="a5629-308">如前所述，始終根據假設或直覺進行測量和操作。</span><span class="sxs-lookup"><span data-stu-id="a5629-308">As previously mentioned, always measure and do not operate on assumptions or intuition.</span></span>

<span data-ttu-id="a5629-309">儘管前面的示例顯示結構歧視聯合產生了更好的性能，但建模域時通常具有較大的"歧視聯合"。</span><span class="sxs-lookup"><span data-stu-id="a5629-309">Although the previous example showed that a struct Discriminated Union yielded better performance, it is common to have larger Discriminated Unions when modeling a domain.</span></span> <span data-ttu-id="a5629-310">如果較大的資料類型根據它們的操作進行結構，則它們可能無法很好地執行，因為可能涉及更多的複製。</span><span class="sxs-lookup"><span data-stu-id="a5629-310">Larger data types like that may not perform as well if they are structs depending on the operations on them, since more copying could be involved.</span></span>

### <a name="functional-programming-and-mutation"></a><span data-ttu-id="a5629-311">函數程式設計和突變</span><span class="sxs-lookup"><span data-stu-id="a5629-311">Functional programming and mutation</span></span>

<span data-ttu-id="a5629-312">預設情況下，F# 值是不可變的，這允許您避免某些類 bug（尤其是涉及併發和並行性的錯誤類）。</span><span class="sxs-lookup"><span data-stu-id="a5629-312">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="a5629-313">但是，在某些情況下，為了實現執行時間或記憶體分配的最佳（甚至合理）效率，最好使用就地狀態突變來實現工作跨度。</span><span class="sxs-lookup"><span data-stu-id="a5629-313">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="a5629-314">這在加入宣告的基礎上是可能的，F# 與`mutable`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a5629-314">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="a5629-315">`mutable`在 F# 中使用可能會感覺與功能純度不一致。</span><span class="sxs-lookup"><span data-stu-id="a5629-315">Use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="a5629-316">這是可以理解的，但無處不在的功能純度可能與性能目標相悖。</span><span class="sxs-lookup"><span data-stu-id="a5629-316">This is understandable, but functional purity everywhere can be at odds with performance goals.</span></span> <span data-ttu-id="a5629-317">一種妥協是封裝突變，這樣調用方就不必關心調用函數時會發生什麼。</span><span class="sxs-lookup"><span data-stu-id="a5629-317">A compromise is to encapsulate mutation such that callers need not care about what happens when they call a function.</span></span> <span data-ttu-id="a5629-318">這允許您通過基於突變的實現為性能關鍵代碼編寫功能介面。</span><span class="sxs-lookup"><span data-stu-id="a5629-318">This allows you to write a functional interface over a mutation-based implementation for performance-critical code.</span></span>

#### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="a5629-319">在不可變介面中包裝可變代碼</span><span class="sxs-lookup"><span data-stu-id="a5629-319">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="a5629-320">以參考透明度為目標，編寫不公開性能關鍵函數可變下層代碼至關重要。</span><span class="sxs-lookup"><span data-stu-id="a5629-320">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="a5629-321">例如，以下代碼在`Array.contains`F# 核心庫中實現函數：</span><span class="sxs-lookup"><span data-stu-id="a5629-321">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

```fsharp
[<CompiledName("Contains")>]
let inline contains value (array:'T[]) =
    checkNonNull "array" array
    let mutable state = false
    let mutable i = 0
    while not state && i < array.Length do
        state <- value = array.[i]
        i <- i + 1
    state
```

<span data-ttu-id="a5629-322">多次調用此函數不會更改基礎陣列，也不要求您在使用該函數時保持任何可變狀態。</span><span class="sxs-lookup"><span data-stu-id="a5629-322">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="a5629-323">它具有參考性透明，即使其中幾乎每行代碼都使用突變。</span><span class="sxs-lookup"><span data-stu-id="a5629-323">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

#### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="a5629-324">考慮在類中封裝可變數據</span><span class="sxs-lookup"><span data-stu-id="a5629-324">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="a5629-325">前面的示例使用單個函數來使用可變數據封裝操作。</span><span class="sxs-lookup"><span data-stu-id="a5629-325">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="a5629-326">對於更複雜的資料集，這並不總是足夠。</span><span class="sxs-lookup"><span data-stu-id="a5629-326">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="a5629-327">請考慮以下函數集：</span><span class="sxs-lookup"><span data-stu-id="a5629-327">Consider the following sets of functions:</span></span>

```fsharp
open System.Collections.Generic

let addToClosureTable (key, value) (t: Dictionary<_,_>) =
    if not (t.ContainsKey(key)) then
        t.Add(key, value)
    else
        t.[key] <- value

let closureTableCount (t: Dictionary<_,_>) = t.Count

let closureTableContains (key, value) (t: Dictionary<_, HashSet<_>>) =
    match t.TryGetValue(key) with
    | (true, v) -> v.Equals(value)
    | (false, _) -> false
```

<span data-ttu-id="a5629-328">此代碼是執行的，但它公開調用方負責維護的基於突變的資料結構。</span><span class="sxs-lookup"><span data-stu-id="a5629-328">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="a5629-329">這可以包裝在類中，而沒有可以更改的基礎成員：</span><span class="sxs-lookup"><span data-stu-id="a5629-329">This can be wrapped inside of a class with no underlying members that can change:</span></span>

```fsharp
open System.Collections.Generic

/// The results of computing the LALR(1) closure of an LR(0) kernel
type Closure1Table() =
    let t = Dictionary<Item0, HashSet<TerminalIndex>>()

    member _.Add(key, value) =
        if not (t.ContainsKey(key)) then
            t.Add(key, value)
        else
            t.[key] <- value

    member _.Count = t.Count

    member _.Contains(key, value) =
        match t.TryGetValue(key) with
        | (true, v) -> v.Equals(value)
        | (false, _) -> false
```

<span data-ttu-id="a5629-330">`Closure1Table`封裝基於突變的基礎資料結構，從而不強制調用方維護基礎資料結構。</span><span class="sxs-lookup"><span data-stu-id="a5629-330">`Closure1Table` encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="a5629-331">類是封裝基於突變的資料和常式而不向調用方公開詳細資訊的強大方法。</span><span class="sxs-lookup"><span data-stu-id="a5629-331">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

#### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="a5629-332">更喜歡`let mutable`引用儲存格</span><span class="sxs-lookup"><span data-stu-id="a5629-332">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="a5629-333">引用儲存格是表示對值的引用而不是值本身的一種方式。</span><span class="sxs-lookup"><span data-stu-id="a5629-333">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="a5629-334">儘管它們可用於性能關鍵型代碼，但不建議它們。</span><span class="sxs-lookup"><span data-stu-id="a5629-334">Although they can be used for performance-critical code, they are not recommended.</span></span> <span data-ttu-id="a5629-335">請考慮下列範例：</span><span class="sxs-lookup"><span data-stu-id="a5629-335">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="a5629-336">使用引用儲存格現在"污染"所有後續代碼，必須取消引用和重新引用基礎資料。</span><span class="sxs-lookup"><span data-stu-id="a5629-336">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="a5629-337">相反，請考慮`let mutable`：</span><span class="sxs-lookup"><span data-stu-id="a5629-337">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="a5629-338">除了 lambda 運算式中間的單點突變之外，所有其他涉及`acc`的代碼都可以以與正常`let`綁定不可變值的使用沒有什麼不同的方式執行此操作。</span><span class="sxs-lookup"><span data-stu-id="a5629-338">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="a5629-339">這將使隨著時間的推移更容易改變。</span><span class="sxs-lookup"><span data-stu-id="a5629-339">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="a5629-340">物件程式設計</span><span class="sxs-lookup"><span data-stu-id="a5629-340">Object programming</span></span>

<span data-ttu-id="a5629-341">F# 完全支持對象和麵向物件 （OO） 概念。</span><span class="sxs-lookup"><span data-stu-id="a5629-341">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="a5629-342">儘管許多 OO 概念功能強大且有用，但並非所有概念都是理想的使用。</span><span class="sxs-lookup"><span data-stu-id="a5629-342">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="a5629-343">以下清單提供了有關高級別 OO 功能類別的指導。</span><span class="sxs-lookup"><span data-stu-id="a5629-343">The following lists offer guidance on categories of OO features at a high level.</span></span>

<span data-ttu-id="a5629-344">**考慮在許多情況下使用這些功能：**</span><span class="sxs-lookup"><span data-stu-id="a5629-344">**Consider using these features in many situations:**</span></span>

* <span data-ttu-id="a5629-345">點標記法`x.Length`（ ）</span><span class="sxs-lookup"><span data-stu-id="a5629-345">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="a5629-346">實例成員</span><span class="sxs-lookup"><span data-stu-id="a5629-346">Instance members</span></span>
* <span data-ttu-id="a5629-347">隱式建構函式</span><span class="sxs-lookup"><span data-stu-id="a5629-347">Implicit constructors</span></span>
* <span data-ttu-id="a5629-348">靜態成員</span><span class="sxs-lookup"><span data-stu-id="a5629-348">Static members</span></span>
* <span data-ttu-id="a5629-349">索引子標記法`arr.[x]`（ ）</span><span class="sxs-lookup"><span data-stu-id="a5629-349">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="a5629-350">命名和可選參數</span><span class="sxs-lookup"><span data-stu-id="a5629-350">Named and Optional arguments</span></span>
* <span data-ttu-id="a5629-351">介面和介面實現</span><span class="sxs-lookup"><span data-stu-id="a5629-351">Interfaces and interface implementations</span></span>

<span data-ttu-id="a5629-352">**不要首先訪問這些功能，但在它們方便解決問題時，請明智地應用它們：**</span><span class="sxs-lookup"><span data-stu-id="a5629-352">**Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:**</span></span>

* <span data-ttu-id="a5629-353">方法多載</span><span class="sxs-lookup"><span data-stu-id="a5629-353">Method overloading</span></span>
* <span data-ttu-id="a5629-354">封裝的可變數據</span><span class="sxs-lookup"><span data-stu-id="a5629-354">Encapsulated mutable data</span></span>
* <span data-ttu-id="a5629-355">類型上的運算子</span><span class="sxs-lookup"><span data-stu-id="a5629-355">Operators on types</span></span>
* <span data-ttu-id="a5629-356">自動屬性</span><span class="sxs-lookup"><span data-stu-id="a5629-356">Auto properties</span></span>
* <span data-ttu-id="a5629-357">實施`IDisposable`和`IEnumerable`</span><span class="sxs-lookup"><span data-stu-id="a5629-357">Implementing `IDisposable` and `IEnumerable`</span></span>
* <span data-ttu-id="a5629-358">類型擴展</span><span class="sxs-lookup"><span data-stu-id="a5629-358">Type extensions</span></span>
* <span data-ttu-id="a5629-359">事件</span><span class="sxs-lookup"><span data-stu-id="a5629-359">Events</span></span>
* <span data-ttu-id="a5629-360">結構</span><span class="sxs-lookup"><span data-stu-id="a5629-360">Structs</span></span>
* <span data-ttu-id="a5629-361">委派</span><span class="sxs-lookup"><span data-stu-id="a5629-361">Delegates</span></span>
* <span data-ttu-id="a5629-362">列舉</span><span class="sxs-lookup"><span data-stu-id="a5629-362">Enums</span></span>

<span data-ttu-id="a5629-363">**通常避免這些功能，除非您必須使用它們：**</span><span class="sxs-lookup"><span data-stu-id="a5629-363">**Generally avoid these features unless you must use them:**</span></span>

* <span data-ttu-id="a5629-364">基於繼承的類型層次結構和實現繼承</span><span class="sxs-lookup"><span data-stu-id="a5629-364">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="a5629-365">空和`Unchecked.defaultof<_>`</span><span class="sxs-lookup"><span data-stu-id="a5629-365">Nulls and `Unchecked.defaultof<_>`</span></span>

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="a5629-366">首選組合而不是繼承</span><span class="sxs-lookup"><span data-stu-id="a5629-366">Prefer composition over inheritance</span></span>

<span data-ttu-id="a5629-367">[繼承的組成](https://en.wikipedia.org/wiki/Composition_over_inheritance)是一個長期存在的習慣用法，好的 F# 代碼可以遵循。</span><span class="sxs-lookup"><span data-stu-id="a5629-367">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="a5629-368">基本原則是，不應公開基類，並強制調用方從該基類繼承以獲取功能。</span><span class="sxs-lookup"><span data-stu-id="a5629-368">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="a5629-369">如果不需要類，請使用物件運算式實現介面</span><span class="sxs-lookup"><span data-stu-id="a5629-369">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="a5629-370">[物件運算式](../language-reference/object-expressions.md)允許您動態實現介面，將實現的介面綁定到值，而無需在類內部執行此操作。</span><span class="sxs-lookup"><span data-stu-id="a5629-370">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="a5629-371">這很方便，特別是當您_只需要_實現介面，並且不需要完整類時。</span><span class="sxs-lookup"><span data-stu-id="a5629-371">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="a5629-372">例如，如果您添加了沒有用於以下語句的`open`符號，則下面是在[Ionide](http://ionide.io/)中運行的代碼，以提供代碼修復操作：</span><span class="sxs-lookup"><span data-stu-id="a5629-372">For example, here is the code that is run in [Ionide](http://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

```fsharp
    let private createProvider () =
        { new CodeActionProvider with
            member this.provideCodeActions(doc, range, context, ct) =
                let diagnostics = context.diagnostics
                let diagnostic = diagnostics |> Seq.tryFind (fun d -> d.message.Contains "Unused open statement")
                let res =
                    match diagnostic with
                    | None -> [||]
                    | Some d ->
                        let line = doc.lineAt d.range.start.line
                        let cmd = createEmpty<Command>
                        cmd.title <- "Remove unused open"
                        cmd.command <- "fsharp.unusedOpenFix"
                        cmd.arguments <- Some ([| doc |> unbox; line.range |> unbox; |] |> ResizeArray)
                        [|cmd |]
                res
                |> ResizeArray
                |> U2.Case1
        }
```

<span data-ttu-id="a5629-373">由於與 Visual Studio 代碼 API 交互時不需要類，因此物件運算式是理想的工具。</span><span class="sxs-lookup"><span data-stu-id="a5629-373">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="a5629-374">當您想要以臨時方式與測試常式建立介面時，它們對於單元測試也很有價值。</span><span class="sxs-lookup"><span data-stu-id="a5629-374">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="consider-type-abbreviations-to-shorten-signatures"></a><span data-ttu-id="a5629-375">考慮類型縮寫以縮短簽名</span><span class="sxs-lookup"><span data-stu-id="a5629-375">Consider Type Abbreviations to shorten signatures</span></span>

<span data-ttu-id="a5629-376">[類型縮寫](../language-reference/type-abbreviations.md)是將標籤分配給另一種類型（如函數簽名或更複雜的類型）的便捷方法。</span><span class="sxs-lookup"><span data-stu-id="a5629-376">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="a5629-377">例如，以下別名將標籤分配給使用[CNTK（](https://docs.microsoft.com/cognitive-toolkit/)深度學習庫）定義計算所需的內容：</span><span class="sxs-lookup"><span data-stu-id="a5629-377">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](https://docs.microsoft.com/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="a5629-378">該`Computation`名稱是表示與它所混疊的簽名匹配的任何函數的便捷方式。</span><span class="sxs-lookup"><span data-stu-id="a5629-378">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="a5629-379">使用像這樣的類型縮寫很方便，並允許更簡潔的代碼。</span><span class="sxs-lookup"><span data-stu-id="a5629-379">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="a5629-380">避免使用類型縮寫來表示您的域</span><span class="sxs-lookup"><span data-stu-id="a5629-380">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="a5629-381">儘管類型縮寫對於為函數簽名指定名稱很方便，但當縮寫其他類型時，它們可能會令人困惑。</span><span class="sxs-lookup"><span data-stu-id="a5629-381">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="a5629-382">請考慮此縮寫：</span><span class="sxs-lookup"><span data-stu-id="a5629-382">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="a5629-383">這可以通過多種方式令人困惑：</span><span class="sxs-lookup"><span data-stu-id="a5629-383">This can be confusing in multiple ways:</span></span>

* <span data-ttu-id="a5629-384">`BufferSize`不是抽象的;不是抽象的。它只是整數的另一個名稱。</span><span class="sxs-lookup"><span data-stu-id="a5629-384">`BufferSize` is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="a5629-385">如果在`BufferSize`公共 API 中公開，很容易被誤解為不僅僅是`int`。</span><span class="sxs-lookup"><span data-stu-id="a5629-385">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="a5629-386">通常，欄位型別具有多個屬性，並且不是基元類型，如`int`。</span><span class="sxs-lookup"><span data-stu-id="a5629-386">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="a5629-387">此縮寫違反了這一假設。</span><span class="sxs-lookup"><span data-stu-id="a5629-387">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="a5629-388">（PascalCase） 的`BufferSize`套管意味著此類型包含更多資料。</span><span class="sxs-lookup"><span data-stu-id="a5629-388">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="a5629-389">與向函數提供具名引數相比，此別名的清晰度不會提高。</span><span class="sxs-lookup"><span data-stu-id="a5629-389">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="a5629-390">縮寫不會在編譯的 IL 中體現;因此，縮寫不會以 IL 表示。它只是一個整數，這個別名是一個編譯時構造。</span><span class="sxs-lookup"><span data-stu-id="a5629-390">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

<span data-ttu-id="a5629-391">總之，類型縮寫的陷阱是，**它們不是**對縮寫類型的抽象。</span><span class="sxs-lookup"><span data-stu-id="a5629-391">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="a5629-392">在前面的示例中，`BufferSize`只是一個`int`封面，沒有額外的資料，也沒有從類型系統的任何好處，除了`int`已經擁有。</span><span class="sxs-lookup"><span data-stu-id="a5629-392">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>

<span data-ttu-id="a5629-393">使用類型縮寫來表示域的另一種方法是使用單一案例區分結合。</span><span class="sxs-lookup"><span data-stu-id="a5629-393">An alternative approach to using type abbreviations to represent a domain is to use single-case discriminated unions.</span></span> <span data-ttu-id="a5629-394">前面的示例可以建模如下：</span><span class="sxs-lookup"><span data-stu-id="a5629-394">The previous sample can be modeled as follows:</span></span>

```fsharp
type BufferSize = BufferSize of int
```

<span data-ttu-id="a5629-395">如果編寫的代碼按`BufferSize`及其基礎值運行，則需要構造一個代碼，而不是傳遞任何任意整數：</span><span class="sxs-lookup"><span data-stu-id="a5629-395">If you write code that operates in terms of `BufferSize` and its underlying value, you need to construct one rather than pass in any arbitrary integer:</span></span>

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

<span data-ttu-id="a5629-396">這降低了錯誤地將任意整數傳遞到`send`函數的可能性，因為調用方必須在調用函數之前構造一個`BufferSize`類型來包裝值。</span><span class="sxs-lookup"><span data-stu-id="a5629-396">This reduces the likelihood of mistakenly passing an arbitrary integer into the `send` function, because the caller must construct a `BufferSize` type to wrap a value before calling the function.</span></span>
