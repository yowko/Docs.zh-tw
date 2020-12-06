---
title: F# 編碼慣例
description: '瞭解撰寫 F # 程式碼時的一般指導方針和慣用語。'
ms.date: 01/15/2020
ms.openlocfilehash: 87955c379f0abba929b0ced75d62d2601f37dc5a
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739898"
---
# <a name="f-coding-conventions"></a><span data-ttu-id="7f009-103">F# 編碼慣例</span><span class="sxs-lookup"><span data-stu-id="7f009-103">F# coding conventions</span></span>

<span data-ttu-id="7f009-104">下列慣例是從使用大型 F # 基底的經驗來制定的。</span><span class="sxs-lookup"><span data-stu-id="7f009-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="7f009-105">[良好 F # 程式碼的五個準則](index.md#five-principles-of-good-f-code)是每個建議的基礎。</span><span class="sxs-lookup"><span data-stu-id="7f009-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="7f009-106">它們與 [f # 元件設計指導方針](component-design-guidelines.md)相關，但適用于任何 f # 程式碼，而不只是程式庫之類的元件。</span><span class="sxs-lookup"><span data-stu-id="7f009-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="7f009-107">組織程式碼</span><span class="sxs-lookup"><span data-stu-id="7f009-107">Organizing code</span></span>

<span data-ttu-id="7f009-108">F # 提供兩種主要的方式來組織程式碼：模組和命名空間。</span><span class="sxs-lookup"><span data-stu-id="7f009-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="7f009-109">這些都很類似，但有下列差異：</span><span class="sxs-lookup"><span data-stu-id="7f009-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="7f009-110">命名空間會編譯為 .NET 命名空間。</span><span class="sxs-lookup"><span data-stu-id="7f009-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="7f009-111">模組會編譯為靜態類別。</span><span class="sxs-lookup"><span data-stu-id="7f009-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="7f009-112">命名空間一律為最上層。</span><span class="sxs-lookup"><span data-stu-id="7f009-112">Namespaces are always top level.</span></span> <span data-ttu-id="7f009-113">模組可以是最上層的，也可以嵌套在其他模組內。</span><span class="sxs-lookup"><span data-stu-id="7f009-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="7f009-114">命名空間可以橫跨多個檔案。</span><span class="sxs-lookup"><span data-stu-id="7f009-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="7f009-115">模組無法。</span><span class="sxs-lookup"><span data-stu-id="7f009-115">Modules cannot.</span></span>
* <span data-ttu-id="7f009-116">模組可以使用和裝飾 `[<RequireQualifiedAccess>]` `[<AutoOpen>]` 。</span><span class="sxs-lookup"><span data-stu-id="7f009-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="7f009-117">下列指導方針可協助您使用這些程式碼來組織程式碼。</span><span class="sxs-lookup"><span data-stu-id="7f009-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="7f009-118">偏好最上層的命名空間</span><span class="sxs-lookup"><span data-stu-id="7f009-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="7f009-119">對於任何公開取用的程式碼，命名空間都優先于最上層的模組。</span><span class="sxs-lookup"><span data-stu-id="7f009-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="7f009-120">因為它們會編譯為 .NET 命名空間，所以可以從 c # 取用，而不會有任何問題。</span><span class="sxs-lookup"><span data-stu-id="7f009-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="7f009-121">使用最上層模組可能不會在從 F # 呼叫時出現不同的情況，但針對 c # 取用者，呼叫者可能會因為必須符合此模組而感到驚訝 `MyClass` `MyCode` 。</span><span class="sxs-lookup"><span data-stu-id="7f009-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="7f009-122">謹慎申請 `[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="7f009-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="7f009-123">此 `[<AutoOpen>]` 結構可會污染可供呼叫端使用的範圍，而發生問題的答案是「魔術」。</span><span class="sxs-lookup"><span data-stu-id="7f009-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="7f009-124">這不是件好事。</span><span class="sxs-lookup"><span data-stu-id="7f009-124">This is not a good thing.</span></span> <span data-ttu-id="7f009-125">這項規則的例外狀況是 F # 核心程式庫本身 (但這項事實也有點有爭議的) 。</span><span class="sxs-lookup"><span data-stu-id="7f009-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="7f009-126">但是，如果您有想要與公用 API 分開組織的公用 API 的協助程式功能，這是一個便利的方式。</span><span class="sxs-lookup"><span data-stu-id="7f009-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

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

<span data-ttu-id="7f009-127">這可讓您將函式公用 API 中的實作詳細資料完全分開，而不需要在每次呼叫時都完整限定協助程式。</span><span class="sxs-lookup"><span data-stu-id="7f009-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="7f009-128">此外，您可以在命名空間層級公開擴充方法和運算式產生器，以整齊地表示 `[<AutoOpen>]` 。</span><span class="sxs-lookup"><span data-stu-id="7f009-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="7f009-129">`[<RequireQualifiedAccess>]`在名稱可能發生衝突時使用，或者您覺得它有助於提高可讀性</span><span class="sxs-lookup"><span data-stu-id="7f009-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="7f009-130">將 `[<RequireQualifiedAccess>]` 屬性新增至模組，表示模組可能無法開啟，而且模組的元素參考需要明確的存取權。</span><span class="sxs-lookup"><span data-stu-id="7f009-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="7f009-131">例如， `Microsoft.FSharp.Collections.List` 模組有這個屬性。</span><span class="sxs-lookup"><span data-stu-id="7f009-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="7f009-132">當模組中的函式和值有可能與其他模組中的名稱衝突的名稱時，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="7f009-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="7f009-133">需要限定存取權可能會大幅增加資源庫的長期維護和 evolvability。</span><span class="sxs-lookup"><span data-stu-id="7f009-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="7f009-134">排序 `open` 語句拓撲</span><span class="sxs-lookup"><span data-stu-id="7f009-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="7f009-135">在 F # 中，宣告的順序很重要，包括 `open` 語句。</span><span class="sxs-lookup"><span data-stu-id="7f009-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="7f009-136">這與 c # 不同，它的效果與檔案 `using` `using static` 中這些語句的順序無關。</span><span class="sxs-lookup"><span data-stu-id="7f009-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="7f009-137">在 F # 中，開啟至範圍的專案可以遮蔽其他已經存在的專案。</span><span class="sxs-lookup"><span data-stu-id="7f009-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="7f009-138">這表示重新排列 `open` 語句可以改變程式碼的意義。</span><span class="sxs-lookup"><span data-stu-id="7f009-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="7f009-139">因此，所有語句的任意排序 (例如 `open` ，不建議使用順序) ，以免您產生可能預期的不同行為。</span><span class="sxs-lookup"><span data-stu-id="7f009-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="7f009-140">相反地，我們建議您將它們排序 [拓撲](https://en.wikipedia.org/wiki/Topological_sorting);也就是說，依照您的系統層級定義順序來排序您的 `open` 語句。 _layers_</span><span class="sxs-lookup"><span data-stu-id="7f009-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="7f009-141">也可以考慮在不同拓撲層級內進行英數位元排序。</span><span class="sxs-lookup"><span data-stu-id="7f009-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="7f009-142">例如，以下是 F # 編譯器服務公用 API 檔案的拓撲排序：</span><span class="sxs-lookup"><span data-stu-id="7f009-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

```fsharp
namespace Microsoft.FSharp.Compiler.SourceCodeServices

open System
open System.Collections.Generic
open System.Collections.Concurrent
open System.Diagnostics
open System.IO
open System.Reflection
open System.Text

open FSharp.Compiler
open FSharp.Compiler.AbstractIL
open FSharp.Compiler.AbstractIL.Diagnostics
open FSharp.Compiler.AbstractIL.IL
open FSharp.Compiler.AbstractIL.ILBinaryReader
open FSharp.Compiler.AbstractIL.Internal
open FSharp.Compiler.AbstractIL.Internal.Library

open FSharp.Compiler.AccessibilityLogic
open FSharp.Compiler.Ast
open FSharp.Compiler.CompileOps
open FSharp.Compiler.CompileOptions
open FSharp.Compiler.Driver

open Internal.Utilities
open Internal.Utilities.Collections
```

<span data-ttu-id="7f009-143">請注意，分行符號會分隔拓撲層，之後每個圖層會以順序的方式排序。</span><span class="sxs-lookup"><span data-stu-id="7f009-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="7f009-144">這會完全組織程式碼，而不會不小心地遮蔽值。</span><span class="sxs-lookup"><span data-stu-id="7f009-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="7f009-145">使用類別包含具有副作用的值</span><span class="sxs-lookup"><span data-stu-id="7f009-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="7f009-146">初始化某個值時，有許多次可能會有副作用，例如將內容具現化至資料庫或其他遠端資源。</span><span class="sxs-lookup"><span data-stu-id="7f009-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="7f009-147">將模組中的這類專案初始化是很吸引人，並在後續的函式中使用：</span><span class="sxs-lookup"><span data-stu-id="7f009-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

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

<span data-ttu-id="7f009-148">這通常不是個好主意，原因如下：</span><span class="sxs-lookup"><span data-stu-id="7f009-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="7f009-149">首先，應用程式設定會使用和推送至程式碼基底 `dep1` `dep2` 。</span><span class="sxs-lookup"><span data-stu-id="7f009-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="7f009-150">這在較大的程式碼基底中很難維護。</span><span class="sxs-lookup"><span data-stu-id="7f009-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="7f009-151">第二，如果您的元件本身會使用多個執行緒，則靜態初始化的資料不應該包含不安全線程的值。</span><span class="sxs-lookup"><span data-stu-id="7f009-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="7f009-152">這顯然是違反的 `dep3` 。</span><span class="sxs-lookup"><span data-stu-id="7f009-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="7f009-153">最後，模組初始化會編譯成整個編譯單位的靜態函式。</span><span class="sxs-lookup"><span data-stu-id="7f009-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="7f009-154">如果該模組中的 let 系結值初始化發生任何錯誤，則會將它列為， `TypeInitializationException` 然後針對應用程式的整個存留期進行快取。</span><span class="sxs-lookup"><span data-stu-id="7f009-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="7f009-155">這可能很難診斷。</span><span class="sxs-lookup"><span data-stu-id="7f009-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="7f009-156">通常您可以嘗試的內部例外狀況，但如果沒有，則不會告訴根本原因為何。</span><span class="sxs-lookup"><span data-stu-id="7f009-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="7f009-157">相反地，只要使用簡單的類別來保存相依性即可：</span><span class="sxs-lookup"><span data-stu-id="7f009-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member _.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member _.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="7f009-158">這會啟用下列功能：</span><span class="sxs-lookup"><span data-stu-id="7f009-158">This enables the following:</span></span>

1. <span data-ttu-id="7f009-159">將任何相依狀態推送至 API 本身之外。</span><span class="sxs-lookup"><span data-stu-id="7f009-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="7f009-160">您現在可以在 API 外部進行設定。</span><span class="sxs-lookup"><span data-stu-id="7f009-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="7f009-161">相依值的初始化錯誤不太可能會被資訊清單為 `TypeInitializationException` 。</span><span class="sxs-lookup"><span data-stu-id="7f009-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="7f009-162">API 現在更容易測試。</span><span class="sxs-lookup"><span data-stu-id="7f009-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="7f009-163">錯誤管理</span><span class="sxs-lookup"><span data-stu-id="7f009-163">Error management</span></span>

<span data-ttu-id="7f009-164">大型系統中的錯誤管理是一項複雜且差別細微的工作，而且沒有任何銀級的專案可確保您的系統具有容錯能力且運作正常。</span><span class="sxs-lookup"><span data-stu-id="7f009-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="7f009-165">下列指導方針應提供導覽此困難空間的指引。</span><span class="sxs-lookup"><span data-stu-id="7f009-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="7f009-166">代表您的網域內建類型中的錯誤案例和不合法的狀態</span><span class="sxs-lookup"><span data-stu-id="7f009-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="7f009-167">使用 [差異](../language-reference/discriminated-unions.md)聯集時，F # 讓您能夠在類型系統中代表錯誤的程式狀態。</span><span class="sxs-lookup"><span data-stu-id="7f009-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="7f009-168">例如：</span><span class="sxs-lookup"><span data-stu-id="7f009-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="7f009-169">在此情況下，有三種已知方式可從銀行帳戶提款 money。</span><span class="sxs-lookup"><span data-stu-id="7f009-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="7f009-170">每個錯誤案例都是以類型表示，因此可在整個程式中安全地處理。</span><span class="sxs-lookup"><span data-stu-id="7f009-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f{am}"
    | InsufficientFunds balance -> printfn "Failed: balance is %f{balance}"
    | CardExpired expiredDate -> printfn "Failed: card expired on %O{expiredDate}"
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="7f009-171">一般情況下，如果您可以針對在網域中可能會 **失敗** 的不同方式建立模型，則錯誤處理常式代碼不會再被視為您必須在一般程式流程中處理的某些專案。</span><span class="sxs-lookup"><span data-stu-id="7f009-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="7f009-172">它只是一般程式流程的一部分，不是 **例外** 狀況。</span><span class="sxs-lookup"><span data-stu-id="7f009-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="7f009-173">這有兩個主要優點：</span><span class="sxs-lookup"><span data-stu-id="7f009-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="7f009-174">當您的網域隨著時間變更時，更容易維護。</span><span class="sxs-lookup"><span data-stu-id="7f009-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="7f009-175">錯誤案例更容易進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="7f009-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="7f009-176">當錯誤無法以類型表示時，請使用例外狀況</span><span class="sxs-lookup"><span data-stu-id="7f009-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="7f009-177">並非所有錯誤都可以在問題網域中表示。</span><span class="sxs-lookup"><span data-stu-id="7f009-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="7f009-178">這類錯誤本質上很 *例外* ，因此能夠在 F # 中引發和攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7f009-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="7f009-179">首先，建議您閱讀 [例外狀況設計指導方針](../../standard/design-guidelines/exceptions.md)。</span><span class="sxs-lookup"><span data-stu-id="7f009-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="7f009-180">這些也適用于 F #。</span><span class="sxs-lookup"><span data-stu-id="7f009-180">These are also applicable to F#.</span></span>

<span data-ttu-id="7f009-181">F # 中可用來引發例外狀況的主要結構，應該依照下列喜好設定順序來考慮：</span><span class="sxs-lookup"><span data-stu-id="7f009-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="7f009-182">函數</span><span class="sxs-lookup"><span data-stu-id="7f009-182">Function</span></span> | <span data-ttu-id="7f009-183">語法</span><span class="sxs-lookup"><span data-stu-id="7f009-183">Syntax</span></span> | <span data-ttu-id="7f009-184">目的</span><span class="sxs-lookup"><span data-stu-id="7f009-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="7f009-185">`System.ArgumentNullException`使用指定的引數名稱引發。</span><span class="sxs-lookup"><span data-stu-id="7f009-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="7f009-186">`System.ArgumentException`使用指定的引數名稱和訊息來引發。</span><span class="sxs-lookup"><span data-stu-id="7f009-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="7f009-187">`System.InvalidOperationException`使用指定的訊息引發。</span><span class="sxs-lookup"><span data-stu-id="7f009-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="7f009-188">擲回例外狀況的一般用途機制。</span><span class="sxs-lookup"><span data-stu-id="7f009-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="7f009-189">`System.Exception`使用指定的訊息引發。</span><span class="sxs-lookup"><span data-stu-id="7f009-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="7f009-190">`System.Exception`使用格式字串及其輸入所決定的訊息來引發。</span><span class="sxs-lookup"><span data-stu-id="7f009-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="7f009-191">使用 `nullArg` 、 `invalidArg` 和 `invalidOp` 做為要擲回的機制 `ArgumentNullException` `ArgumentException` 和 `InvalidOperationException` 適當時機。</span><span class="sxs-lookup"><span data-stu-id="7f009-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="7f009-192">和函式 `failwith` `failwithf` 通常應該避免，因為它們會引發基底 `Exception` 類型，而不是特定的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7f009-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="7f009-193">根據例外狀況 [設計指導方針](../../standard/design-guidelines/exceptions.md)，您會想要在可以的情況下引發更明確的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7f009-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="use-exception-handling-syntax"></a><span data-ttu-id="7f009-194">使用例外狀況處理語法</span><span class="sxs-lookup"><span data-stu-id="7f009-194">Use exception-handling syntax</span></span>

<span data-ttu-id="7f009-195">F # 透過語法支援例外狀況模式 `try...with` ：</span><span class="sxs-lookup"><span data-stu-id="7f009-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="7f009-196">如果您想要讓程式碼保持乾淨，請在發生例外狀況的情況時，協調要執行的功能。</span><span class="sxs-lookup"><span data-stu-id="7f009-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="7f009-197">處理這種情況的其中一種方法，就是使用 [主動模式](../language-reference/active-patterns.md) ，將發生例外狀況本身的功能分組。</span><span class="sxs-lookup"><span data-stu-id="7f009-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="7f009-198">例如，您可能會使用 API，當它擲回例外狀況時，會將寶貴的資訊包含在例外狀況中繼資料中。</span><span class="sxs-lookup"><span data-stu-id="7f009-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="7f009-199">在主動模式內的已攔截例外狀況內，解除包裝有用的值，並傳回該值，在某些情況下可能會很有説明。</span><span class="sxs-lookup"><span data-stu-id="7f009-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="7f009-200">請勿使用 monadic 錯誤處理來取代例外狀況</span><span class="sxs-lookup"><span data-stu-id="7f009-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="7f009-201">例外狀況會在功能程式設計中被視為有點 taboo。</span><span class="sxs-lookup"><span data-stu-id="7f009-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="7f009-202">事實上，例外狀況違反了純度，因此可以放心地將它們視為無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="7f009-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="7f009-203">不過，這會忽略程式碼必須執行的實際情況，而且可能發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="7f009-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="7f009-204">一般來說，撰寫程式碼時假設大部分的專案都不是單純也不是總計，以將不愉快的意外情況降到最低。</span><span class="sxs-lookup"><span data-stu-id="7f009-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="7f009-205">請務必考慮下列與 .NET 執行時間和跨語言生態系統中的相關性和」適當性相關的例外狀況核心優勢/層面：</span><span class="sxs-lookup"><span data-stu-id="7f009-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="7f009-206">它們包含詳細的診斷資訊，在對問題進行偵錯工具時很有説明。</span><span class="sxs-lookup"><span data-stu-id="7f009-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="7f009-207">執行時間和其他 .NET 語言都能充分瞭解它們。</span><span class="sxs-lookup"><span data-stu-id="7f009-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="7f009-208">相 *較于在* 特定的程式碼中執行部分部分的部分，它們可以減少重複使用的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7f009-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="7f009-209">第三個點很重要。</span><span class="sxs-lookup"><span data-stu-id="7f009-209">This third point is critical.</span></span> <span data-ttu-id="7f009-210">針對重要複雜的作業，無法使用例外狀況可能會導致處理如下的結構：</span><span class="sxs-lookup"><span data-stu-id="7f009-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="7f009-211">這可能會導致「stringly 型別」錯誤的模式比對等脆弱的程式碼：</span><span class="sxs-lookup"><span data-stu-id="7f009-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="7f009-212">此外，對於會傳回 "更好" 類型的 "simple" 函式，忍受任何例外狀況可能很吸引人：</span><span class="sxs-lookup"><span data-stu-id="7f009-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="7f009-213">可惜的是， `tryReadAllText` 可能會擲回許多例外狀況，而這些例外狀況可能會發生在檔案系統上，而此程式碼會捨棄您的環境中可能發生錯誤的任何資訊。</span><span class="sxs-lookup"><span data-stu-id="7f009-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="7f009-214">如果您以結果型別取代此程式碼，則會回到「stringly 型別」的錯誤訊息剖析：</span><span class="sxs-lookup"><span data-stu-id="7f009-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

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

<span data-ttu-id="7f009-215">然後，將例外狀況物件本身放在函式中， `Error` 就會強制您在呼叫位置（而不是在函式中）適當處理例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="7f009-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="7f009-216">這麼做可有效地建立已檢查的例外狀況，這些例外狀況是 unfun 來處理成為 API 的呼叫者。</span><span class="sxs-lookup"><span data-stu-id="7f009-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="7f009-217">上述範例的一個好方法是攔截 *特定* 的例外狀況，並在該例外狀況的內容中傳回有意義的值。</span><span class="sxs-lookup"><span data-stu-id="7f009-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="7f009-218">如果您依照下列方式修改函式 `tryReadAllText` ， `None` 有更多意義：</span><span class="sxs-lookup"><span data-stu-id="7f009-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="7f009-219">這個函式現在會在找不到檔案時適當地處理案例，並將該意義指派給傳回，而不是全部運作。</span><span class="sxs-lookup"><span data-stu-id="7f009-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="7f009-220">這個傳回值可以對應至該錯誤案例，而不會捨棄任何內容相關資訊，或強制呼叫端處理在程式碼中該點可能不相關的案例。</span><span class="sxs-lookup"><span data-stu-id="7f009-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="7f009-221">等型別 `Result<'Success, 'Error>` 適用于不會進行嵌套的基本作業，而且 F # 選用型別最適合用來表示何時有可能傳回 *某事物* 或 *任何* 東西。</span><span class="sxs-lookup"><span data-stu-id="7f009-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="7f009-222">不過，它們不是例外狀況的取代，而且不應該用於嘗試取代例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7f009-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="7f009-223">相反地，應謹慎套用，以依目標的方式處理例外狀況和錯誤管理原則的特定層面。</span><span class="sxs-lookup"><span data-stu-id="7f009-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="7f009-224">部分應用程式和無點程式設計</span><span class="sxs-lookup"><span data-stu-id="7f009-224">Partial application and point-free programming</span></span>

<span data-ttu-id="7f009-225">F # 支援部分的應用程式，因此，您可以使用不同的方式來以無點的樣式進行程式設計。</span><span class="sxs-lookup"><span data-stu-id="7f009-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="7f009-226">這對於在模組內重複使用程式碼或執行某些工作很有説明，但它並不是公開的內容。</span><span class="sxs-lookup"><span data-stu-id="7f009-226">This can be beneficial for code reuse within a module or the implementation of something, but it is not something to expose publicly.</span></span> <span data-ttu-id="7f009-227">一般來說，無點程式設計並不是本身的作用，而且可以為不是可以沉浸在樣式中的人員新增重要的認知屏障。</span><span class="sxs-lookup"><span data-stu-id="7f009-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="7f009-228">請勿在公用 Api 中使用部分應用程式和 currying</span><span class="sxs-lookup"><span data-stu-id="7f009-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="7f009-229">只要稍微例外，在公用 Api 中使用部分應用程式可能會對取用者造成混淆。</span><span class="sxs-lookup"><span data-stu-id="7f009-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="7f009-230">`let`F # 程式碼中的系結值通常是 **值**，而不是 **函數值**。</span><span class="sxs-lookup"><span data-stu-id="7f009-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="7f009-231">將值與函式值混合在一起可能會導致在 exchange 中儲存少量的程式碼，以達相當多的認知負擔，特別是當結合運算子（例如） `>>` 來撰寫函數時。</span><span class="sxs-lookup"><span data-stu-id="7f009-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="7f009-232">考慮無點程式設計的工具含意</span><span class="sxs-lookup"><span data-stu-id="7f009-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="7f009-233">擴充函式不會標記其引數。</span><span class="sxs-lookup"><span data-stu-id="7f009-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="7f009-234">這會影響工具。</span><span class="sxs-lookup"><span data-stu-id="7f009-234">This has tooling implications.</span></span> <span data-ttu-id="7f009-235">請考慮下列兩個功能：</span><span class="sxs-lookup"><span data-stu-id="7f009-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is {name} and I am %d{age} years old!"

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="7f009-236">兩者都是有效的函式，但 `funcWithApplication` 是一個局部函數。</span><span class="sxs-lookup"><span data-stu-id="7f009-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="7f009-237">當您將滑鼠停留在編輯器中的類型上時，就會看到：</span><span class="sxs-lookup"><span data-stu-id="7f009-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="7f009-238">在呼叫位置，工具中的工具提示（例如 Visual Studio）將不會提供有意義的資訊，讓您知道 `string` 和 `int` 輸入類型實際上代表什麼。</span><span class="sxs-lookup"><span data-stu-id="7f009-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="7f009-239">如果您遇到可公開取用的無點程式碼 `funcWithApplication` ，則建議進行完整η展開，讓工具可以針對引數使用有意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="7f009-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="7f009-240">此外，如果不可能，則偵錯工具的程式碼可能會很困難。</span><span class="sxs-lookup"><span data-stu-id="7f009-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="7f009-241">偵錯工具依賴系結至名稱的值 (例如，系結 `let`) ，以便您可以在執行時檢查中繼值。</span><span class="sxs-lookup"><span data-stu-id="7f009-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="7f009-242">當您的程式碼沒有要檢查的值時，就不會有任何要進行的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="7f009-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="7f009-243">未來，偵錯工具可能會發展，以根據先前執行的路徑來合成這些值，但不建議您在 *可能* 的偵錯工具上建立您的理由。</span><span class="sxs-lookup"><span data-stu-id="7f009-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="7f009-244">將部分應用程式視為減少內部重複使用的技術</span><span class="sxs-lookup"><span data-stu-id="7f009-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="7f009-245">相較于上一個重點，部分應用程式是一項絕佳的工具，可減少應用程式內的重複使用或更深入的 API 內部。</span><span class="sxs-lookup"><span data-stu-id="7f009-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="7f009-246">對於執行更複雜 Api 的單元測試而言很有説明，因為未定案通常是很棘手的問題。</span><span class="sxs-lookup"><span data-stu-id="7f009-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="7f009-247">例如，下列程式碼會示範如何完成大部分的模擬架構，而不需要對這類架構進行外部相依性，以及瞭解相關的定制 API。</span><span class="sxs-lookup"><span data-stu-id="7f009-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="7f009-248">例如，請考慮下列解決方案拓撲：</span><span class="sxs-lookup"><span data-stu-id="7f009-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

<span data-ttu-id="7f009-249">`ImplementationLogic.fsproj` 可能會公開程式碼，例如：</span><span class="sxs-lookup"><span data-stu-id="7f009-249">`ImplementationLogic.fsproj` might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member _.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="7f009-250">中的單元測試 `Transactions.doTransaction` `ImplementationLogic.Tests.fsproj` 很簡單：</span><span class="sxs-lookup"><span data-stu-id="7f009-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fsproj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="7f009-251">部分套用 `doTransaction` 模擬內容物件可讓您在所有單元測試中呼叫函式，而不需要每次都要建立模擬內容：</span><span class="sxs-lookup"><span data-stu-id="7f009-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

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

<span data-ttu-id="7f009-252">這項技術不應該通用地套用至整個程式碼基底，但這是減少複雜內部和單元測試這些內部的好方法。</span><span class="sxs-lookup"><span data-stu-id="7f009-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="7f009-253">存取控制</span><span class="sxs-lookup"><span data-stu-id="7f009-253">Access control</span></span>

<span data-ttu-id="7f009-254">F # 有多個 [存取控制](../language-reference/access-control.md)選項，可從 .net 執行時間中的可用內容繼承。</span><span class="sxs-lookup"><span data-stu-id="7f009-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="7f009-255">這些都不只適用于型別，您也可以將它們用於函數。</span><span class="sxs-lookup"><span data-stu-id="7f009-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="7f009-256">偏好非 `public` 類型和成員，直到您需要它們可供公開取用為止。</span><span class="sxs-lookup"><span data-stu-id="7f009-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="7f009-257">這也可減少取用者的需求。</span><span class="sxs-lookup"><span data-stu-id="7f009-257">This also minimizes what consumers couple to.</span></span>
* <span data-ttu-id="7f009-258">努力保留所有協助程式功能 `private` 。</span><span class="sxs-lookup"><span data-stu-id="7f009-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="7f009-259">請考慮在 helper 函式的 `[<AutoOpen>]` 私用模組上使用，如果它們變成很多。</span><span class="sxs-lookup"><span data-stu-id="7f009-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="7f009-260">型別推斷和泛型</span><span class="sxs-lookup"><span data-stu-id="7f009-260">Type inference and generics</span></span>

<span data-ttu-id="7f009-261">型別推斷可以節省您輸入許多未定案的內容。</span><span class="sxs-lookup"><span data-stu-id="7f009-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="7f009-262">F # 編譯器中的自動一般化可協助您撰寫更多的一般程式碼，幾乎不需要額外投入您的部分。</span><span class="sxs-lookup"><span data-stu-id="7f009-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="7f009-263">不過，這些功能並不普遍。</span><span class="sxs-lookup"><span data-stu-id="7f009-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="7f009-264">請考慮在公用 Api 中以明確類型標記引數名稱，而不依賴此的型別推斷。</span><span class="sxs-lookup"><span data-stu-id="7f009-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="7f009-265">這是因為 **您** 應該控制 API 的圖形，而不是編譯器的形式。</span><span class="sxs-lookup"><span data-stu-id="7f009-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="7f009-266">雖然編譯器可以在推斷類型時進行精確的工作，但如果它所依賴的本質具有變更類型，則您的 API 圖形可能會變更。</span><span class="sxs-lookup"><span data-stu-id="7f009-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="7f009-267">這可能是您想要的結果，但它幾乎會產生突破性的 API 變更，下游取用者就必須處理這些變更。</span><span class="sxs-lookup"><span data-stu-id="7f009-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="7f009-268">相反地，如果您明確控制公用 API 的形狀，就可以控制這些重大變更。</span><span class="sxs-lookup"><span data-stu-id="7f009-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="7f009-269">在 DDD 方面，可以將這視為反損毀層。</span><span class="sxs-lookup"><span data-stu-id="7f009-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="7f009-270">請考慮為您的泛型引數提供有意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="7f009-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="7f009-271">除非您要撰寫非特定網域專屬的真正泛型程式碼，否則有意義的名稱可協助其他程式設計人員瞭解他們所使用的網域。</span><span class="sxs-lookup"><span data-stu-id="7f009-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="7f009-272">例如，在與檔資料庫互動的內容中命名的型別參數，可讓您所使用的函式 `'Document` 或成員接受一般檔案類型更加清楚。</span><span class="sxs-lookup"><span data-stu-id="7f009-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="7f009-273">請考慮使用 PascalCase 來命名泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="7f009-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="7f009-274">這是在 .NET 中執行作業的一般方式，因此建議您使用 PascalCase，而不是 snake_case 或 camelCase。</span><span class="sxs-lookup"><span data-stu-id="7f009-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="7f009-275">最後，對於 F # 或大型程式碼基底的人員而言，自動一般化不一定是 boon。</span><span class="sxs-lookup"><span data-stu-id="7f009-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="7f009-276">使用一般的元件時，有認知負擔。</span><span class="sxs-lookup"><span data-stu-id="7f009-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="7f009-277">此外，如果自動一般化的函式不會搭配不同的輸入類型使用 (請單獨使用這些函式，以作為這類) ，如此一來，這些函式就不會在該時間點成為泛型。</span><span class="sxs-lookup"><span data-stu-id="7f009-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="7f009-278">請一律考慮您所撰寫的程式碼是否會真正受益于泛型。</span><span class="sxs-lookup"><span data-stu-id="7f009-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="7f009-279">效能</span><span class="sxs-lookup"><span data-stu-id="7f009-279">Performance</span></span>

### <a name="consider-structs-for-small-types-with-high-allocation-rates"></a><span data-ttu-id="7f009-280">針對具有高配置速率的小型類型考慮結構</span><span class="sxs-lookup"><span data-stu-id="7f009-280">Consider structs for small types with high allocation rates</span></span>

<span data-ttu-id="7f009-281">使用結構 (也稱為實值型別) 通常可以針對某些程式碼產生更高的效能，因為它通常可避免設定物件。</span><span class="sxs-lookup"><span data-stu-id="7f009-281">Using structs (also called Value Types) can often result in higher performance for some code because it typically avoids allocating objects.</span></span> <span data-ttu-id="7f009-282">不過，結構不一定是「更快速」的按鈕：如果結構中的資料大小超過16個位元組，複製資料通常可能會比使用參考型別更多的 CPU 時間。</span><span class="sxs-lookup"><span data-stu-id="7f009-282">However, structs are not always a "go faster" button: if the size of the data in a struct exceeds 16 bytes, copying the data can often result in more CPU time spend than using a reference type.</span></span>

<span data-ttu-id="7f009-283">若要判斷是否應該使用結構，請考慮下列條件：</span><span class="sxs-lookup"><span data-stu-id="7f009-283">To determine if you should use a struct, consider the following conditions:</span></span>

- <span data-ttu-id="7f009-284">如果您的資料大小是16個位元組或更小。</span><span class="sxs-lookup"><span data-stu-id="7f009-284">If the size of your data is 16 bytes or smaller.</span></span>
- <span data-ttu-id="7f009-285">如果您可能有許多這些類型的實例在執行中程式的記憶體中。</span><span class="sxs-lookup"><span data-stu-id="7f009-285">If you're likely to have many instances of these types resident in memory in a running program.</span></span>

<span data-ttu-id="7f009-286">如果第一個條件適用，您通常應該使用結構。</span><span class="sxs-lookup"><span data-stu-id="7f009-286">If the first condition applies, you should generally use a struct.</span></span> <span data-ttu-id="7f009-287">如果兩者都適用，您幾乎都應該使用結構。</span><span class="sxs-lookup"><span data-stu-id="7f009-287">If both apply, you should almost always use a struct.</span></span> <span data-ttu-id="7f009-288">在某些情況下，您可能會在某些情況下套用先前的條件，但使用結構不會比使用參考型別更好或更糟，但很可能很罕見。</span><span class="sxs-lookup"><span data-stu-id="7f009-288">There may be some cases where the previous conditions apply, but using a struct is no better or worse than using a reference type, but they are likely to be rare.</span></span> <span data-ttu-id="7f009-289">不過，一定要在進行這類變更時進行測量，而不是在假設或直覺上運作。</span><span class="sxs-lookup"><span data-stu-id="7f009-289">It's important to always measure when making changes like this, though, and not operate on assumption or intuition.</span></span>

#### <a name="consider-struct-tuples-when-grouping-small-value-types-with-high-allocation-rates"></a><span data-ttu-id="7f009-290">以高配置速率分組較小數值型別時，請考慮結構元組</span><span class="sxs-lookup"><span data-stu-id="7f009-290">Consider struct tuples when grouping small value types with high allocation rates</span></span>

<span data-ttu-id="7f009-291">請考慮下列兩個功能：</span><span class="sxs-lookup"><span data-stu-id="7f009-291">Consider the following two functions:</span></span>

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

<span data-ttu-id="7f009-292">當您使用 [BenchmarkDotNet](https://benchmarkdotnet.org/)之類的統計效能評定工具來評定這些函式時，您會發現 `runWithStructTuple` 使用結構元組的函式會以更快的速度執行40%，並且不會配置任何記憶體。</span><span class="sxs-lookup"><span data-stu-id="7f009-292">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that the `runWithStructTuple` function that uses struct tuples runs 40% faster and allocates no memory.</span></span>

<span data-ttu-id="7f009-293">不過，在您自己的程式碼中，這些結果不一定是如此。</span><span class="sxs-lookup"><span data-stu-id="7f009-293">However, these results won't always be the case in your own code.</span></span> <span data-ttu-id="7f009-294">如果您將函式標示為 `inline` ，則使用參考元組的程式碼可能會取得一些額外的優化，或可配置的程式碼可能只會經過優化。</span><span class="sxs-lookup"><span data-stu-id="7f009-294">If you mark a function as `inline`, code that uses reference tuples may get some additional optimizations, or code that would allocate could simply be optimized away.</span></span> <span data-ttu-id="7f009-295">當效能考慮時，您應該一律測量結果，而且永遠不會根據假設或直覺來操作。</span><span class="sxs-lookup"><span data-stu-id="7f009-295">You should always measure results whenever performance is concerned, and never operate based on assumption or intuition.</span></span>

#### <a name="consider-struct-records-when-the-type-is-small-and-has-high-allocation-rates"></a><span data-ttu-id="7f009-296">當類型很小且配置速率很高時，請考慮結構記錄</span><span class="sxs-lookup"><span data-stu-id="7f009-296">Consider struct records when the type is small and has high allocation rates</span></span>

<span data-ttu-id="7f009-297">稍早所述的經驗法則也保留 [F # 記錄類型](../language-reference/records.md)。</span><span class="sxs-lookup"><span data-stu-id="7f009-297">The rule of thumb described earlier also holds for [F# record types](../language-reference/records.md).</span></span> <span data-ttu-id="7f009-298">請考慮下列用來處理這些資料類型的資料類型和函數：</span><span class="sxs-lookup"><span data-stu-id="7f009-298">Consider the following data types and functions that process them:</span></span>

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

<span data-ttu-id="7f009-299">這類似于先前的元組程式碼，但這次範例會使用記錄和內嵌的內建函式。</span><span class="sxs-lookup"><span data-stu-id="7f009-299">This is similar to the previous tuple code, but this time the example uses records and an inlined inner function.</span></span>

<span data-ttu-id="7f009-300">當您使用 [BenchmarkDotNet](https://benchmarkdotnet.org/)之類的統計效能評定工具來對這些函式進行基準測試時，您會發現 `processStructPoint` 執行速度快到60%，而且在 managed 堆積上未配置任何內容。</span><span class="sxs-lookup"><span data-stu-id="7f009-300">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that `processStructPoint` runs nearly 60% faster and allocates nothing on the managed heap.</span></span>

#### <a name="consider-struct-discriminated-unions-when-the-data-type-is-small-with-high-allocation-rates"></a><span data-ttu-id="7f009-301">當資料類型很小且具有高配置速率時，請考慮結構區分等位</span><span class="sxs-lookup"><span data-stu-id="7f009-301">Consider struct discriminated unions when the data type is small with high allocation rates</span></span>

<span data-ttu-id="7f009-302">先前有關結構元組和記錄效能的觀察也保留給 [F #](../language-reference/discriminated-unions.md)差異聯集。</span><span class="sxs-lookup"><span data-stu-id="7f009-302">The previous observations about performance with struct tuples and records also holds for [F# Discriminated Unions](../language-reference/discriminated-unions.md).</span></span> <span data-ttu-id="7f009-303">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="7f009-303">Consider the following code:</span></span>

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

<span data-ttu-id="7f009-304">通常會針對網域模型定義像這樣的單一案例差異聯集。</span><span class="sxs-lookup"><span data-stu-id="7f009-304">It's common to define single-case Discriminated Unions like this for domain modeling.</span></span> <span data-ttu-id="7f009-305">當您使用 [BenchmarkDotNet](https://benchmarkdotnet.org/)之類的統計效能評定工具來對這些函式進行基準測試時，您會發現其 `structReverseName` 執行速度比小型字串快 25% `reverseName` 。</span><span class="sxs-lookup"><span data-stu-id="7f009-305">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that `structReverseName` runs about 25% faster than `reverseName` for small strings.</span></span> <span data-ttu-id="7f009-306">針對大型字串，兩者都會執行相同的。</span><span class="sxs-lookup"><span data-stu-id="7f009-306">For large strings, both perform about the same.</span></span> <span data-ttu-id="7f009-307">因此，在此情況下，最好是使用結構。</span><span class="sxs-lookup"><span data-stu-id="7f009-307">So, in this case, it's always preferable to use a struct.</span></span> <span data-ttu-id="7f009-308">如先前所述，一律測量並不會在假設或直覺上運作。</span><span class="sxs-lookup"><span data-stu-id="7f009-308">As previously mentioned, always measure and do not operate on assumptions or intuition.</span></span>

<span data-ttu-id="7f009-309">雖然先前的範例顯示結構差異聯集產生較佳的效能，但在建立定義域模型時，通常會有較大的區分等位。</span><span class="sxs-lookup"><span data-stu-id="7f009-309">Although the previous example showed that a struct Discriminated Union yielded better performance, it is common to have larger Discriminated Unions when modeling a domain.</span></span> <span data-ttu-id="7f009-310">較大的資料類型（例如，如果它們是結構，視其上的作業而定）可能不會同時執行，因為可能會涉及更多的複製。</span><span class="sxs-lookup"><span data-stu-id="7f009-310">Larger data types like that may not perform as well if they are structs depending on the operations on them, since more copying could be involved.</span></span>

### <a name="functional-programming-and-mutation"></a><span data-ttu-id="7f009-311">功能性程式設計和變化</span><span class="sxs-lookup"><span data-stu-id="7f009-311">Functional programming and mutation</span></span>

<span data-ttu-id="7f009-312">F # 值預設為固定值，可讓您避免特定類別的 bug (特別是) 平行存取和平行處理原則的類別。</span><span class="sxs-lookup"><span data-stu-id="7f009-312">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="7f009-313">不過，在某些情況下，若要達到最佳 (，或甚至合理) 執行時間或記憶體配置的效率，最好是使用狀態的就地變化來實行工作範圍。</span><span class="sxs-lookup"><span data-stu-id="7f009-313">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="7f009-314">您可以使用關鍵字搭配 F # 來加入宣告。 `mutable`</span><span class="sxs-lookup"><span data-stu-id="7f009-314">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="7f009-315">`mutable`在 F # 中使用可能會覺得功能純度很可能。</span><span class="sxs-lookup"><span data-stu-id="7f009-315">Use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="7f009-316">這是可理解的，但功能的純度可能會有效能目標。</span><span class="sxs-lookup"><span data-stu-id="7f009-316">This is understandable, but functional purity everywhere can be at odds with performance goals.</span></span> <span data-ttu-id="7f009-317">折衷的是封裝變化，讓呼叫端不需要在意呼叫函式時會發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="7f009-317">A compromise is to encapsulate mutation such that callers need not care about what happens when they call a function.</span></span> <span data-ttu-id="7f009-318">這可讓您針對效能關鍵程式碼，透過以變化為基礎的執行來撰寫功能介面。</span><span class="sxs-lookup"><span data-stu-id="7f009-318">This allows you to write a functional interface over a mutation-based implementation for performance-critical code.</span></span>

#### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="7f009-319">將可變的程式碼包裝在不可變的介面中</span><span class="sxs-lookup"><span data-stu-id="7f009-319">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="7f009-320">使用參考透明度做為目標時，請務必撰寫不會公開效能關鍵函式之可變 underbelly 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7f009-320">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="7f009-321">例如，下列程式碼會 `Array.contains` 在 F # 核心程式庫中實作為函式：</span><span class="sxs-lookup"><span data-stu-id="7f009-321">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

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

<span data-ttu-id="7f009-322">多次呼叫此函式並不會變更基礎陣列，也不會要求您維持任何使用中的可變狀態。</span><span class="sxs-lookup"><span data-stu-id="7f009-322">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="7f009-323">它是參考上透明的，雖然幾乎每一行程式碼都會使用變化。</span><span class="sxs-lookup"><span data-stu-id="7f009-323">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

#### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="7f009-324">考慮將可變數據封裝在類別中</span><span class="sxs-lookup"><span data-stu-id="7f009-324">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="7f009-325">先前的範例使用單一函式來封裝使用可變動資料的作業。</span><span class="sxs-lookup"><span data-stu-id="7f009-325">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="7f009-326">對於更複雜的資料集而言，這不一定足夠。</span><span class="sxs-lookup"><span data-stu-id="7f009-326">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="7f009-327">請考慮下列函數集：</span><span class="sxs-lookup"><span data-stu-id="7f009-327">Consider the following sets of functions:</span></span>

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

<span data-ttu-id="7f009-328">這段程式碼的效能很高，但它會公開呼叫端負責維護的變化式資料結構。</span><span class="sxs-lookup"><span data-stu-id="7f009-328">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="7f009-329">這可以包裝在類別內，但不能變更任何基礎成員：</span><span class="sxs-lookup"><span data-stu-id="7f009-329">This can be wrapped inside of a class with no underlying members that can change:</span></span>

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

<span data-ttu-id="7f009-330">`Closure1Table` 封裝基礎以變化為基礎的資料結構，因此不會強制呼叫者維護基礎資料結構。</span><span class="sxs-lookup"><span data-stu-id="7f009-330">`Closure1Table` encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="7f009-331">類別是一種功能強大的方法，可封裝以變化為基礎的資料和常式，而不會向呼叫端公開詳細資料。</span><span class="sxs-lookup"><span data-stu-id="7f009-331">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

#### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="7f009-332">偏好 `let mutable` 參考資料格</span><span class="sxs-lookup"><span data-stu-id="7f009-332">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="7f009-333">參考資料格是一種表示值參考的方法，而不是值本身。</span><span class="sxs-lookup"><span data-stu-id="7f009-333">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="7f009-334">雖然它們可用於效能關鍵的程式碼，但不建議使用。</span><span class="sxs-lookup"><span data-stu-id="7f009-334">Although they can be used for performance-critical code, they are not recommended.</span></span> <span data-ttu-id="7f009-335">請考慮下列範例：</span><span class="sxs-lookup"><span data-stu-id="7f009-335">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="7f009-336">使用參考儲存格現在會「干擾」所有後續的程式碼，而且必須對基礎資料進行取值和重新參考。</span><span class="sxs-lookup"><span data-stu-id="7f009-336">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="7f009-337">請改 `let mutable` 為考慮：</span><span class="sxs-lookup"><span data-stu-id="7f009-337">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="7f009-338">除了 lambda 運算式中間的單一變化點之外，其他所有接觸的程式碼都 `acc` 可以使用與一般系結不可變的值不同的方式來達成 `let` 。</span><span class="sxs-lookup"><span data-stu-id="7f009-338">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="7f009-339">這可讓您更輕鬆地隨著時間變更。</span><span class="sxs-lookup"><span data-stu-id="7f009-339">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="7f009-340">物件程式設計</span><span class="sxs-lookup"><span data-stu-id="7f009-340">Object programming</span></span>

<span data-ttu-id="7f009-341">F # 對於物件和麵向物件的 (OO) 概念具有完整的支援。</span><span class="sxs-lookup"><span data-stu-id="7f009-341">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="7f009-342">雖然許多 OO 概念都很強大且很有用，但並非全部都適合使用。</span><span class="sxs-lookup"><span data-stu-id="7f009-342">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="7f009-343">下列清單提供高階各類 OO 功能的指引。</span><span class="sxs-lookup"><span data-stu-id="7f009-343">The following lists offer guidance on categories of OO features at a high level.</span></span>

<span data-ttu-id="7f009-344">**在許多情況下，請考慮使用這些功能：**</span><span class="sxs-lookup"><span data-stu-id="7f009-344">**Consider using these features in many situations:**</span></span>

* <span data-ttu-id="7f009-345">點標記法 (`x.Length`) </span><span class="sxs-lookup"><span data-stu-id="7f009-345">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="7f009-346">執行個體成員</span><span class="sxs-lookup"><span data-stu-id="7f009-346">Instance members</span></span>
* <span data-ttu-id="7f009-347">隱含的函式</span><span class="sxs-lookup"><span data-stu-id="7f009-347">Implicit constructors</span></span>
* <span data-ttu-id="7f009-348">靜態成員</span><span class="sxs-lookup"><span data-stu-id="7f009-348">Static members</span></span>
* <span data-ttu-id="7f009-349">索引子標記法 (`arr.[x]`) </span><span class="sxs-lookup"><span data-stu-id="7f009-349">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="7f009-350">指名的和選擇性引數</span><span class="sxs-lookup"><span data-stu-id="7f009-350">Named and Optional arguments</span></span>
* <span data-ttu-id="7f009-351">介面和介面的實現</span><span class="sxs-lookup"><span data-stu-id="7f009-351">Interfaces and interface implementations</span></span>

<span data-ttu-id="7f009-352">**請先找不到這些功能，但在方便解決問題時，請謹慎套用這些功能：**</span><span class="sxs-lookup"><span data-stu-id="7f009-352">**Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:**</span></span>

* <span data-ttu-id="7f009-353">方法多載</span><span class="sxs-lookup"><span data-stu-id="7f009-353">Method overloading</span></span>
* <span data-ttu-id="7f009-354">封裝的可變數據</span><span class="sxs-lookup"><span data-stu-id="7f009-354">Encapsulated mutable data</span></span>
* <span data-ttu-id="7f009-355">類型上的運算子</span><span class="sxs-lookup"><span data-stu-id="7f009-355">Operators on types</span></span>
* <span data-ttu-id="7f009-356">Auto 屬性</span><span class="sxs-lookup"><span data-stu-id="7f009-356">Auto properties</span></span>
* <span data-ttu-id="7f009-357">執行 `IDisposable` 和 `IEnumerable`</span><span class="sxs-lookup"><span data-stu-id="7f009-357">Implementing `IDisposable` and `IEnumerable`</span></span>
* <span data-ttu-id="7f009-358">類型延伸模組</span><span class="sxs-lookup"><span data-stu-id="7f009-358">Type extensions</span></span>
* <span data-ttu-id="7f009-359">事件</span><span class="sxs-lookup"><span data-stu-id="7f009-359">Events</span></span>
* <span data-ttu-id="7f009-360">結構</span><span class="sxs-lookup"><span data-stu-id="7f009-360">Structs</span></span>
* <span data-ttu-id="7f009-361">委派</span><span class="sxs-lookup"><span data-stu-id="7f009-361">Delegates</span></span>
* <span data-ttu-id="7f009-362">列舉</span><span class="sxs-lookup"><span data-stu-id="7f009-362">Enums</span></span>

<span data-ttu-id="7f009-363">**一般來說，除非您必須使用這些功能，否則請避免這些功能：**</span><span class="sxs-lookup"><span data-stu-id="7f009-363">**Generally avoid these features unless you must use them:**</span></span>

* <span data-ttu-id="7f009-364">繼承型型別階層和執行繼承</span><span class="sxs-lookup"><span data-stu-id="7f009-364">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="7f009-365">Null 和 `Unchecked.defaultof<_>`</span><span class="sxs-lookup"><span data-stu-id="7f009-365">Nulls and `Unchecked.defaultof<_>`</span></span>

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="7f009-366">偏好透過繼承撰寫</span><span class="sxs-lookup"><span data-stu-id="7f009-366">Prefer composition over inheritance</span></span>

<span data-ttu-id="7f009-367">[超越繼承的組合](https://en.wikipedia.org/wiki/Composition_over_inheritance) 是良好的 F # 程式碼可以遵守的長期用法。</span><span class="sxs-lookup"><span data-stu-id="7f009-367">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="7f009-368">基本原則是，您不應該公開基類，並強制呼叫端繼承自該基類以取得功能。</span><span class="sxs-lookup"><span data-stu-id="7f009-368">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="7f009-369">如果您不需要類別，請使用物件運算式來執行介面</span><span class="sxs-lookup"><span data-stu-id="7f009-369">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="7f009-370">[物件運算式](../language-reference/object-expressions.md) 可讓您即時執行介面，將實介面系結至值，而不需要在類別內部執行此動作。</span><span class="sxs-lookup"><span data-stu-id="7f009-370">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="7f009-371">這很方便，尤其是當您 _只_ 需要執行介面，且不需要完整類別時更是如此。</span><span class="sxs-lookup"><span data-stu-id="7f009-371">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="7f009-372">例如，以下是在 [Ionide](https://ionide.io/) 中執行的程式碼，如果您已新增沒有語句的符號，則會提供程式碼修正動作 `open` ：</span><span class="sxs-lookup"><span data-stu-id="7f009-372">For example, here is the code that is run in [Ionide](https://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

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

<span data-ttu-id="7f009-373">由於與 Visual Studio Code API 互動時，不需要類別，因此物件運算式是理想的工具。</span><span class="sxs-lookup"><span data-stu-id="7f009-373">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="7f009-374">當您想要以臨機操作的方式，以測試常式來取代介面時，它們也非常適合單元測試。</span><span class="sxs-lookup"><span data-stu-id="7f009-374">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="consider-type-abbreviations-to-shorten-signatures"></a><span data-ttu-id="7f009-375">請考慮輸入縮寫以縮短簽章</span><span class="sxs-lookup"><span data-stu-id="7f009-375">Consider Type Abbreviations to shorten signatures</span></span>

<span data-ttu-id="7f009-376">[類型縮寫](../language-reference/type-abbreviations.md) 是將標籤指派給另一種類型的便利方法，例如函式簽章或更複雜的型別。</span><span class="sxs-lookup"><span data-stu-id="7f009-376">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="7f009-377">例如，下列別名會將標籤指派給使用 [CNTK](/cognitive-toolkit/)（深度學習程式庫）定義計算所需的內容：</span><span class="sxs-lookup"><span data-stu-id="7f009-377">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="7f009-378">`Computation`名稱是一種便利的方式，用來表示任何符合其別名的簽章的函式。</span><span class="sxs-lookup"><span data-stu-id="7f009-378">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="7f009-379">使用這類的類型縮寫很方便，而且可讓程式碼更簡潔。</span><span class="sxs-lookup"><span data-stu-id="7f009-379">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="7f009-380">避免使用類型縮寫來表示您的網域</span><span class="sxs-lookup"><span data-stu-id="7f009-380">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="7f009-381">雖然型別縮寫對於為函式簽章提供名稱很方便，但在縮寫其他類型時可能會造成混淆。</span><span class="sxs-lookup"><span data-stu-id="7f009-381">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="7f009-382">請考慮以下縮寫：</span><span class="sxs-lookup"><span data-stu-id="7f009-382">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="7f009-383">這可能會讓您以多種方式造成混淆：</span><span class="sxs-lookup"><span data-stu-id="7f009-383">This can be confusing in multiple ways:</span></span>

* <span data-ttu-id="7f009-384">`BufferSize` 不是抽象概念;這只是整數的另一個名稱。</span><span class="sxs-lookup"><span data-stu-id="7f009-384">`BufferSize` is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="7f009-385">如果 `BufferSize` 在公用 API 中公開，就可以輕易地將它誤解為非單純的表示 `int` 。</span><span class="sxs-lookup"><span data-stu-id="7f009-385">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="7f009-386">一般而言，網欄位型別具有多個屬性，而且不是基本類型，例如 `int` 。</span><span class="sxs-lookup"><span data-stu-id="7f009-386">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="7f009-387">此縮寫違反該假設。</span><span class="sxs-lookup"><span data-stu-id="7f009-387">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="7f009-388"> (的大小寫 `BufferSize`) 表示此型別會保存更多資料。</span><span class="sxs-lookup"><span data-stu-id="7f009-388">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="7f009-389">相較于將具名引數提供給函式，此別名不會提供更高的清晰度。</span><span class="sxs-lookup"><span data-stu-id="7f009-389">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="7f009-390">縮寫不會在編譯的 IL 中資訊清單;它只是一個整數，而此別名是編譯時期的結構。</span><span class="sxs-lookup"><span data-stu-id="7f009-390">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

<span data-ttu-id="7f009-391">總而言之，類型縮寫的缺點是它們在縮寫的類型上 **不** 是抽象概念。</span><span class="sxs-lookup"><span data-stu-id="7f009-391">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="7f009-392">在上述範例中， `BufferSize` 只是 `int` 在幕後，沒有額外的資料，也不會有任何來自型別系統的優點，除了已有的內容之外 `int` 。</span><span class="sxs-lookup"><span data-stu-id="7f009-392">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>

<span data-ttu-id="7f009-393">使用類型縮寫來表示網域的替代方法是使用單一案例差異聯集。</span><span class="sxs-lookup"><span data-stu-id="7f009-393">An alternative approach to using type abbreviations to represent a domain is to use single-case discriminated unions.</span></span> <span data-ttu-id="7f009-394">先前的範例可以模型化，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7f009-394">The previous sample can be modeled as follows:</span></span>

```fsharp
type BufferSize = BufferSize of int
```

<span data-ttu-id="7f009-395">如果您撰寫的程式碼會以 `BufferSize` 和其基礎值運作，您必須建立一個，而不是傳入任何任意整數：</span><span class="sxs-lookup"><span data-stu-id="7f009-395">If you write code that operates in terms of `BufferSize` and its underlying value, you need to construct one rather than pass in any arbitrary integer:</span></span>

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

<span data-ttu-id="7f009-396">這樣可以減少錯誤地將任意整數傳遞給函式的可能性 `send` ，因為呼叫端必須在 `BufferSize` 呼叫函式之前，先建立型別來包裝值。</span><span class="sxs-lookup"><span data-stu-id="7f009-396">This reduces the likelihood of mistakenly passing an arbitrary integer into the `send` function, because the caller must construct a `BufferSize` type to wrap a value before calling the function.</span></span>
