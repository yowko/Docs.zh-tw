---
title: F# 編碼慣例
description: '瞭解撰寫 F # 程式碼時的一般方針和慣用語。'
ms.date: 01/15/2020
ms.openlocfilehash: 47e9183ce22689a050878cf10d7a9bcf3b929ec6
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2020
ms.locfileid: "84143523"
---
# <a name="f-coding-conventions"></a><span data-ttu-id="ff0a0-103">F# 編碼慣例</span><span class="sxs-lookup"><span data-stu-id="ff0a0-103">F# coding conventions</span></span>

<span data-ttu-id="ff0a0-104">下列慣例是從使用大型 F # 代碼基底的經驗來制定。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="ff0a0-105">[良好 F # 程式碼的五個原則](index.md#five-principles-of-good-f-code)是每個建議的基礎。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="ff0a0-106">它們與[f # 元件設計方針](component-design-guidelines.md)有關，但適用于任何 f # 程式碼，而不只是程式庫之類的元件。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="ff0a0-107">組織程式碼</span><span class="sxs-lookup"><span data-stu-id="ff0a0-107">Organizing code</span></span>

<span data-ttu-id="ff0a0-108">F # 的功能有兩種主要的組織程式碼方式：模組和命名空間。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="ff0a0-109">這些類似，但有下列差異：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="ff0a0-110">命名空間會編譯為 .NET 命名空間。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="ff0a0-111">模組會編譯為靜態類別。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="ff0a0-112">命名空間一律是最上層。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-112">Namespaces are always top level.</span></span> <span data-ttu-id="ff0a0-113">模組可以是最上層，並在其他模組中嵌套。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="ff0a0-114">命名空間可以跨越多個檔案。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="ff0a0-115">模組不能。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-115">Modules cannot.</span></span>
* <span data-ttu-id="ff0a0-116">模組可以使用和裝飾 `[<RequireQualifiedAccess>]` `[<AutoOpen>]` 。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="ff0a0-117">下列指導方針可協助您使用這些指引來組織您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="ff0a0-118">偏好位於最上層的命名空間</span><span class="sxs-lookup"><span data-stu-id="ff0a0-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="ff0a0-119">針對任何可公開取用的程式碼，命名空間會優先于最上層的模組。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="ff0a0-120">因為它們會編譯為 .NET 命名空間，所以可從 c # 取用，而不會有任何問題。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="ff0a0-121">從 F # 呼叫時，使用最上層模組可能不會出現不同的情況，但是對於 c # 取用者，必須使用模組來限定呼叫端可能會驚訝 `MyClass` `MyCode` 。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="ff0a0-122">小心申請`[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="ff0a0-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="ff0a0-123">此 `[<AutoOpen>]` 結構可會污染呼叫端可用的範圍，而發生問題的答案是「魔術」。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="ff0a0-124">這不是件好事。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-124">This is not a good thing.</span></span> <span data-ttu-id="ff0a0-125">此規則的例外狀況是 F # 核心程式庫本身（雖然此事實也有點爭議）。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="ff0a0-126">不過，如果您有想要與公用 API 分開組織之公用 API 的協助程式功能，這是很方便的。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

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

<span data-ttu-id="ff0a0-127">如此一來，您就不需要在每次呼叫時都完整限定協助程式，即可從函式的公用 API 中明確地分隔執行詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="ff0a0-128">此外，在命名空間層級公開擴充方法和運算式產生器，可以使用整齊地表示 `[<AutoOpen>]` 。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="ff0a0-129">`[<RequireQualifiedAccess>]`當名稱可能發生衝突，或您覺得它有助於可讀性時使用</span><span class="sxs-lookup"><span data-stu-id="ff0a0-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="ff0a0-130">將屬性加入模組中， `[<RequireQualifiedAccess>]` 表示模組可能無法開啟，而且對模組元素的參考需要明確限定的存取權。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="ff0a0-131">例如， `Microsoft.FSharp.Collections.List` 模組具有這個屬性。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="ff0a0-132">當模組中的函數和值有可能與其他模組中的名稱衝突的名稱時，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="ff0a0-133">需要限定的存取權可能會大幅增加程式庫的長期維護性和 evolvability。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="ff0a0-134">Sort `open` 語句拓撲</span><span class="sxs-lookup"><span data-stu-id="ff0a0-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="ff0a0-135">在 F # 中，宣告的順序很重要，包括 with `open` 語句。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="ff0a0-136">這與 c # 不同，其中的效果與檔案 `using` `using static` 中這些語句的順序無關。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="ff0a0-137">在 F # 中，在範圍中開啟的專案可能會遮蔽其他已經存在的元素。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="ff0a0-138">這表示重新排列 `open` 語句可能會改變程式碼的意義。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="ff0a0-139">因此，不建議所有語句的任意排序 `open` （例如，排序），以免您會產生可能預期的不同行為。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="ff0a0-140">相反地，我們建議您將它們排序[拓撲](https://en.wikipedia.org/wiki/Topological_sorting);也就是，依照您的系統層級的定義順序來排序您的 `open` 語句。 _layers_</span><span class="sxs-lookup"><span data-stu-id="ff0a0-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="ff0a0-141">您也可以考慮在不同的拓撲層中進行英數位元排序。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="ff0a0-142">例如，以下是 F # 編譯器服務公用 API 檔案的拓撲排序：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

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

<span data-ttu-id="ff0a0-143">請注意，分行符號會分隔拓撲層，之後的每個圖層都會排序排序。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="ff0a0-144">這會完全組織程式碼，而不會不小心遮蔽值。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="ff0a0-145">使用類別來包含有副作用的值</span><span class="sxs-lookup"><span data-stu-id="ff0a0-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="ff0a0-146">將值初始化時，有很多時候會有副作用，例如將內容具現化至資料庫或其他遠端資源。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="ff0a0-147">在模組中初始化這類專案，並在後續的函式中使用它是很吸引人的：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

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

<span data-ttu-id="ff0a0-148">這通常是不好的想法，原因如下：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="ff0a0-149">首先，應用程式設定會使用和推送至程式碼基底 `dep1` `dep2` 。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="ff0a0-150">這在較大的基本代碼基底中很容易維護。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="ff0a0-151">第二，如果您的元件本身會使用多個執行緒，則靜態初始化的資料應該不會包含不具備執行緒安全的值。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="ff0a0-152">這很明顯地違反了 `dep3` 。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="ff0a0-153">最後，模組初始化會編譯成整個編譯單位的靜態函式。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="ff0a0-154">如果在該模組的 let 系結值初始化中發生任何錯誤，則會將它視為， `TypeInitializationException` 然後針對應用程式的整個存留期進行快取。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="ff0a0-155">這可能很容易診斷。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="ff0a0-156">通常，您可以嘗試進行的內部例外狀況，但如果沒有，則不會告知根本原因。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="ff0a0-157">相反地，只要使用簡單的類別來保存相依性：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member _.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member _.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="ff0a0-158">這會啟用下列功能：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-158">This enables the following:</span></span>

1. <span data-ttu-id="ff0a0-159">將任何相依的狀態推送至 API 本身以外的地方。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="ff0a0-160">設定現在可以在 API 外部完成。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="ff0a0-161">相依值的初始化錯誤不太可能會資訊清單 `TypeInitializationException` 。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="ff0a0-162">API 現在更容易測試。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="ff0a0-163">錯誤管理</span><span class="sxs-lookup"><span data-stu-id="ff0a0-163">Error management</span></span>

<span data-ttu-id="ff0a0-164">大型系統中的錯誤管理是一項複雜且差別細微的工作，而且沒有任何銀級的專案，以確保您的系統具有容錯能力，而且行為良好。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="ff0a0-165">下列指導方針應該提供流覽這個艱難空間的指引。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="ff0a0-166">表示在您的網域內建類型中的錯誤案例和不合法的狀態</span><span class="sxs-lookup"><span data-stu-id="ff0a0-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="ff0a0-167">使用[區分](../language-reference/discriminated-unions.md)聯集時，F # 可讓您在類型系統中代表錯誤的程式狀態。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="ff0a0-168">例如：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="ff0a0-169">在此情況下，有三種已知的方式可讓銀行帳戶的提款 money 失敗。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="ff0a0-170">每個錯誤案例都會以類型表示，因此可在整個程式中安全地處理。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="ff0a0-171">一般來說，如果您可以建立在網域中可能會**失敗**之不同方式的模型，則不會再將錯誤處理常式代碼視為您必須處理的某些專案，而不是一般程式流程。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="ff0a0-172">這只是一般程式流程的一部分，並不會視為**例外**狀況。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="ff0a0-173">這有兩個主要優點：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="ff0a0-174">隨著您的網域在一段時間內的變更，更容易維護。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="ff0a0-175">錯誤案例較容易進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="ff0a0-176">當錯誤無法以類型表示時，使用例外狀況</span><span class="sxs-lookup"><span data-stu-id="ff0a0-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="ff0a0-177">並非所有的錯誤都可以在問題網域中表示。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="ff0a0-178">這類錯誤本質上是*例外*，因此能夠在 F # 中引發和攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="ff0a0-179">首先，建議您閱讀[例外狀況設計指導方針](../../standard/design-guidelines/exceptions.md)。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="ff0a0-180">這些也適用于 F #。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-180">These are also applicable to F#.</span></span>

<span data-ttu-id="ff0a0-181">F # 中可用來引發例外狀況的主要結構，應依照下列喜好設定順序來考慮：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="ff0a0-182">函式</span><span class="sxs-lookup"><span data-stu-id="ff0a0-182">Function</span></span> | <span data-ttu-id="ff0a0-183">語法</span><span class="sxs-lookup"><span data-stu-id="ff0a0-183">Syntax</span></span> | <span data-ttu-id="ff0a0-184">目的</span><span class="sxs-lookup"><span data-stu-id="ff0a0-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="ff0a0-185">`System.ArgumentNullException`使用指定的引數名稱引發。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="ff0a0-186">`System.ArgumentException`使用指定的引數名稱和訊息引發。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="ff0a0-187">`System.InvalidOperationException`使用指定的訊息引發。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="ff0a0-188">用來擲回例外狀況的一般用途機制。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="ff0a0-189">`System.Exception`使用指定的訊息引發。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="ff0a0-190">`System.Exception`以格式字串及其輸入所決定的訊息引發。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="ff0a0-191">使用 `nullArg` 、 `invalidArg` 和 `invalidOp` 做為要擲回的機制 `ArgumentNullException` `ArgumentException` 和適當的時機 `InvalidOperationException` 。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="ff0a0-192">`failwith` `failwithf` 通常應該避免使用和函數，因為它們會引發基底 `Exception` 類型，而不是特定的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="ff0a0-193">根據例外狀況[設計指導方針](../../standard/design-guidelines/exceptions.md)，您會想要在可以時引發更具體的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="using-exception-handling-syntax"></a><span data-ttu-id="ff0a0-194">使用例外狀況處理語法</span><span class="sxs-lookup"><span data-stu-id="ff0a0-194">Using exception-handling syntax</span></span>

<span data-ttu-id="ff0a0-195">F # 支援透過語法的例外狀況模式 `try...with` ：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="ff0a0-196">如果您想要讓程式碼保持整潔，請將功能與模式比對的例外狀況協調，以降低執行的情況。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="ff0a0-197">處理這種情況的方法之一，就是使用作用中的[模式](../language-reference/active-patterns.md)來分組發生錯誤案例的功能，以及例外狀況本身。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="ff0a0-198">例如，您可能會使用 API，當它擲回例外狀況時，會在例外狀況中繼資料中括住重要資訊。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="ff0a0-199">在使用中模式的已捕捉例外狀況內解除包裝有用的值，並在某些情況下傳回該值會很有説明。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="ff0a0-200">請勿使用 monadic 錯誤處理來取代例外狀況</span><span class="sxs-lookup"><span data-stu-id="ff0a0-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="ff0a0-201">在功能程式設計中，例外狀況會被視為有點 taboo。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="ff0a0-202">事實上，例外狀況違反了純度，因此可以放心地將它們視為不太實用。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="ff0a0-203">不過，這會忽略程式碼必須執行的實際情況，而且可能會發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="ff0a0-204">一般來說，請撰寫程式碼，假設大部分專案都不是純粹的，也不是總計，以儘量減少不愉快的意外。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="ff0a0-205">對於 .NET 執行時間和跨語言生態系統中的相關性和」適當性，請務必考慮下列各項核心的優缺點：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="ff0a0-206">其中包含詳細的診斷資訊，在發生問題時很有説明。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="ff0a0-207">這是執行時間和其他 .NET 語言的良好理解。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="ff0a0-208">相較于無法以臨機操作方式來執行某些部分的語義，它們可以減少重複使用的程式碼，以*避免*例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="ff0a0-209">第三個點很重要。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-209">This third point is critical.</span></span> <span data-ttu-id="ff0a0-210">針對重要複雜的作業，無法使用例外狀況可能會導致處理如下的結構：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="ff0a0-211">這可以輕鬆地導致像是「stringly 類型」錯誤的模式比對等脆弱的程式碼：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="ff0a0-212">此外，若要對傳回 "更好" 類型的「簡單」函式，忍受任何例外狀況，可能會很吸引人：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="ff0a0-213">可惜的是， `tryReadAllText` 可能會根據檔案系統上的各種專案來擲回許多例外狀況，而此程式碼會捨棄您的環境中可能發生錯誤的任何相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="ff0a0-214">如果您將此程式碼取代為結果類型，則會回到「stringly 類型」錯誤訊息剖析：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

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

<span data-ttu-id="ff0a0-215">而將例外狀況物件本身放在函式中， `Error` 只會強制您在呼叫位置（而不是在函式）中正確處理例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="ff0a0-216">這麼做可以有效地建立已檢查的例外狀況，這是以 API 的呼叫者身分處理的 unfun。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="ff0a0-217">在上述範例中，有一個很好的替代方式，就是攔截*特定*的例外狀況，並在該例外狀況的內容中傳回有意義的值。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="ff0a0-218">如果您修改函式，如下所示 `tryReadAllText` ，會 `None` 有更多意義：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="ff0a0-219">此函式會立即適當地處理找不到檔案的情況，並將該意義指派給傳回，而不是當做全部攔截。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="ff0a0-220">這個傳回值可以對應至該錯誤案例，而不會捨棄任何內容資訊或強制呼叫端處理常式代碼中可能不相關的案例。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="ff0a0-221">之類的型別 `Result<'Success, 'Error>` 適用于不是嵌套的基本作業，而 F # 選擇性型別則非常適合用來表示何時可以傳回*東西*或*任何*內容。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="ff0a0-222">不過，它們不是例外狀況的取代，而且不應該用於嘗試取代例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="ff0a0-223">相反地，應該謹慎套用，以以目標方式處理例外狀況和錯誤管理原則的特定層面。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="ff0a0-224">部分應用程式和無點程式設計</span><span class="sxs-lookup"><span data-stu-id="ff0a0-224">Partial application and point-free programming</span></span>

<span data-ttu-id="ff0a0-225">F # 支援部分應用程式，因此有各種不同的方式可使用無點的樣式進行程式設計。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="ff0a0-226">這對於在模組內重複使用程式碼或執行某個專案很有説明，但並不是要公開公開的東西。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-226">This can be beneficial for code reuse within a module or the implementation of something, but it is not something to expose publicly.</span></span> <span data-ttu-id="ff0a0-227">一般來說，無點程式設計並不是本身的本身，而且可以為未可以沉浸樣式的人員加入重要的認知屏障。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="ff0a0-228">請勿在公用 Api 中使用部分應用程式和 currying</span><span class="sxs-lookup"><span data-stu-id="ff0a0-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="ff0a0-229">除了例外狀況外，在公用 Api 中使用部分應用程式可能會對取用者造成混淆。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="ff0a0-230">`let`F # 程式碼中的通常系結值為**值**，而不是**函數值**。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="ff0a0-231">將值和函數值混在一起，可讓您在 exchange 中儲存少量的程式碼，以產生相當多的認知額外負荷，尤其是在結合運算子（例如）來撰寫函式時 `>>` 。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="ff0a0-232">考慮無點程式設計的工具含意</span><span class="sxs-lookup"><span data-stu-id="ff0a0-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="ff0a0-233">擴充函數不會標示其引數。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="ff0a0-234">這會影響工具。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-234">This has tooling implications.</span></span> <span data-ttu-id="ff0a0-235">請考慮下列兩個功能：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="ff0a0-236">兩者都是有效的函式，但卻 `funcWithApplication` 是一個擴充函數。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="ff0a0-237">當您將滑鼠停留在編輯器中的類型時，您會看到：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="ff0a0-238">在呼叫位置，工具（例如 Visual Studio）中的工具提示不會提供您有意義的資訊，做為 `string` 和 `int` 輸入類型實際代表的內容。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="ff0a0-239">如果您遇到類似于可公開使用的無點程式碼 `funcWithApplication` ，建議您執行完整的η擴充，讓工具可以針對引數取得有意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="ff0a0-240">此外，如果不可能，則偵錯工具不會有困難的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="ff0a0-241">偵錯工具會依賴系結至名稱的值（例如，系結 `let` ），以便您可以在執行期間檢查中間值。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="ff0a0-242">當您的程式碼沒有任何要檢查的值時，不會有任何可進行的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="ff0a0-243">在未來，偵錯工具可能會演變為根據先前執行的路徑來合成這些值，但不建議您在*可能*的偵測功能上建立您的理由。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="ff0a0-244">將部分應用程式視為減少內部重複使用的技術</span><span class="sxs-lookup"><span data-stu-id="ff0a0-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="ff0a0-245">相較于先前的點，部分應用程式是一項很棒的工具，可減少應用程式內的重複使用或更深入的 API 內部。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="ff0a0-246">這對於執行更複雜 Api 的單元測試很有説明，其中的重複使用通常是一項很難處理的難題。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="ff0a0-247">例如，下列程式碼會示範如何完成大部分的模擬架構，讓您不需要對這類架構進行外部相依性，也必須瞭解相關的定制 API。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="ff0a0-248">例如，請考慮下列解決方案的拓撲：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

<span data-ttu-id="ff0a0-249">`ImplementationLogic.fsproj`可能會公開程式碼，例如：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-249">`ImplementationLogic.fsproj` might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member _.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="ff0a0-250">中的單元測試 `Transactions.doTransaction` `ImplementationLogic.Tests.fsproj` 很容易：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fsproj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="ff0a0-251">部分套用 `doTransaction` 模擬內容物件可讓您在所有單元測試中呼叫函式，而不需要每次都要建立模擬內容：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

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

<span data-ttu-id="ff0a0-252">這項技術不應通用地套用到整個程式碼基底，但這是減少複雜內部和單元測試這些內部專案的好方法。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="ff0a0-253">存取控制</span><span class="sxs-lookup"><span data-stu-id="ff0a0-253">Access control</span></span>

<span data-ttu-id="ff0a0-254">F # 有多個[存取控制](../language-reference/access-control.md)選項，繼承自 .net 執行時間中可用的內容。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="ff0a0-255">這些不只適用于類型，您也可以將它們用於函數。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="ff0a0-256">偏好使用非 `public` 類型和成員，直到您需要它們可公開取用為止。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="ff0a0-257">這也可以減少取用者的需求。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-257">This also minimizes what consumers couple to.</span></span>
* <span data-ttu-id="ff0a0-258">努力保留所有 helper 功能 `private` 。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="ff0a0-259">請考慮在 helper 函式的 `[<AutoOpen>]` 私用模組上使用（如果它們變得很多）。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="ff0a0-260">型別推斷和泛型</span><span class="sxs-lookup"><span data-stu-id="ff0a0-260">Type inference and generics</span></span>

<span data-ttu-id="ff0a0-261">型別推斷可為您節省許多樣板的輸入。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="ff0a0-262">而 F # 編譯器中的自動一般化可以協助您撰寫更通用的程式碼，幾乎不需要額外的精力。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="ff0a0-263">不過，這些功能並不是很普遍。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="ff0a0-264">請考慮在公用 Api 中使用明確類型標記引數名稱，而且不依賴此的類型推斷。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="ff0a0-265">這是因為**您**應該控制 API 的形式，而不是編譯器。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="ff0a0-266">雖然編譯器可以在推斷型別時執行精細的作業，但如果它依賴的內部專案有變更的型別，則您的 API 可能會有變更的圖形。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="ff0a0-267">這可能是您想要的，但幾乎肯定會導致下游取用者必須處理的中斷性 API 變更。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="ff0a0-268">相反地，如果您明確控制公用 API 的形式，則可以控制這些重大變更。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="ff0a0-269">在 DDD 詞彙中，這可以視為反損毀層。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="ff0a0-270">請考慮為您的泛型引數提供有意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="ff0a0-271">除非您撰寫的是真正的一般程式碼，而不是特定的網域，否則有意義的名稱可以協助其他程式設計人員瞭解他們正在處理的網域。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="ff0a0-272">例如，在與檔資料庫互動的內容中名為的型別參數，可 `'Document` 讓您更清楚的是，您正在使用的函式或成員可以接受一般檔案類型。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="ff0a0-273">請考慮使用 PascalCase 來命名泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="ff0a0-274">這是在 .NET 中執行工作的一般方式，因此建議您使用 PascalCase，而不要使用 snake_case 或 camelCase。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="ff0a0-275">最後，對於 F # 的新手或大型程式碼基底的人而言，自動一般化不一定是 boon 的。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="ff0a0-276">使用泛型元件時，會發生認知額外負荷。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="ff0a0-277">此外，如果自動一般化的函式不會與不同的輸入型別搭配使用（如果要用來做為這種類型，請單獨使用），在該時間點就不會有真正的優勢。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="ff0a0-278">請務必考慮您撰寫的程式碼實際上是否受益于一般。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="ff0a0-279">效能</span><span class="sxs-lookup"><span data-stu-id="ff0a0-279">Performance</span></span>

### <a name="prefer-structs-for-small-data-types"></a><span data-ttu-id="ff0a0-280">針對小型資料類型偏好結構</span><span class="sxs-lookup"><span data-stu-id="ff0a0-280">Prefer structs for small data types</span></span>

<span data-ttu-id="ff0a0-281">使用結構（也稱為實數值型別）通常會導致某些程式碼的效能更高，因為它通常會避免設定物件。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-281">Using structs (also called Value Types) can often result in higher performance for some code because it typically avoids allocating objects.</span></span> <span data-ttu-id="ff0a0-282">不過，結構不一定是「更快速」的按鈕：如果結構中的資料大小超過16個位元組，複製資料通常會導致比使用參考型別更多的 CPU 時間。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-282">However, structs are not always a "go faster" button: if the size of the data in a struct exceeds 16 bytes, copying the data can often result in more CPU time spend than using a reference type.</span></span>

<span data-ttu-id="ff0a0-283">若要判斷您是否應該使用結構，請考慮下列條件：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-283">To determine if you should use a struct, consider the following conditions:</span></span>

- <span data-ttu-id="ff0a0-284">如果您的資料大小是16個位元組或更小。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-284">If the size of your data is 16 bytes or smaller.</span></span>
- <span data-ttu-id="ff0a0-285">如果您可能在執行中的程式中有許多這些資料類型是常駐在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-285">If you're likely to have many of these data types resident in memory in a running program.</span></span>

<span data-ttu-id="ff0a0-286">如果第一個條件適用，您通常應該使用結構。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-286">If the first condition applies, you should generally use a struct.</span></span> <span data-ttu-id="ff0a0-287">如果兩者都適用，您應該幾乎一律使用結構。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-287">If both apply, you should almost always use a struct.</span></span> <span data-ttu-id="ff0a0-288">在某些情況下，可能會套用先前的條件，但使用結構不會比使用參考型別更好或更糟，但可能很罕見。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-288">There may be some cases where the previous conditions apply, but using a struct is no better or worse than using a reference type, but they are likely to be rare.</span></span> <span data-ttu-id="ff0a0-289">不過，一定要測量進行這類變更的時機，而不是在假設或直覺上操作。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-289">It's important to always measure when making changes like this, though, and not operate on assumption or intuition.</span></span>

#### <a name="prefer-struct-tuples-when-grouping-small-value-types"></a><span data-ttu-id="ff0a0-290">群組小型數值型別時偏好使用結構元組</span><span class="sxs-lookup"><span data-stu-id="ff0a0-290">Prefer struct tuples when grouping small value types</span></span>

<span data-ttu-id="ff0a0-291">請考慮下列兩個功能：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-291">Consider the following two functions:</span></span>

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

<span data-ttu-id="ff0a0-292">當您使用[BenchmarkDotNet](https://benchmarkdotnet.org/)之類的統計效能評定工具來評估這些函式時，您會發現 `runWithStructTuple` 使用結構元組的函式執行速度40% 並不會配置任何記憶體。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-292">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that the `runWithStructTuple` function that uses struct tuples runs 40% faster and allocates no memory.</span></span>

<span data-ttu-id="ff0a0-293">不過，在您自己的程式碼中，這些結果不一定會是這種情況。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-293">However, these results won't always be the case in your own code.</span></span> <span data-ttu-id="ff0a0-294">如果您將函式標示為 `inline` ，使用參考元組的程式碼可能會取得一些額外的優化，或配置的程式碼可以直接優化。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-294">If you mark a function as `inline`, code that uses reference tuples may get some additional optimizations, or code that would allocate could simply be optimized away.</span></span> <span data-ttu-id="ff0a0-295">當效能考慮時，您應該一律測量結果，而且永遠不會根據假設或直覺來操作。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-295">You should always measure results whenever performance is concerned, and never operate based on assumption or intuition.</span></span>

#### <a name="prefer-struct-records-when-the-data-type-is-small"></a><span data-ttu-id="ff0a0-296">當資料類型很少時，偏好使用結構記錄</span><span class="sxs-lookup"><span data-stu-id="ff0a0-296">Prefer struct records when the data type is small</span></span>

<span data-ttu-id="ff0a0-297">稍早所述的經驗法則也適用于[F # 記錄類型](../language-reference/records.md)。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-297">The rule of thumb described earlier also holds for [F# record types](../language-reference/records.md).</span></span> <span data-ttu-id="ff0a0-298">請考慮下列處理它們的資料類型和函數：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-298">Consider the following data types and functions that process them:</span></span>

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

<span data-ttu-id="ff0a0-299">這類似先前的元組程式碼，但這次範例會使用記錄和內嵌的內建函式。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-299">This is similar to the previous tuple code, but this time the example uses records and an inlined inner function.</span></span>

<span data-ttu-id="ff0a0-300">當您使用[BenchmarkDotNet](https://benchmarkdotnet.org/)之類的統計效能評定工具來評估這些函式時，會發現 `processStructPoint` 執行速度幾乎60%，而且不會在受控堆積上配置任何內容。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-300">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that `processStructPoint` runs nearly 60% faster and allocates nothing on the managed heap.</span></span>

#### <a name="prefer-struct-discriminated-unions-when-the-data-type-is-small"></a><span data-ttu-id="ff0a0-301">當資料類型很小時，偏好使用結構區分等位</span><span class="sxs-lookup"><span data-stu-id="ff0a0-301">Prefer struct discriminated unions when the data type is small</span></span>

<span data-ttu-id="ff0a0-302">先前的關於結構元組和記錄的效能，也適用于[F # 區分](../language-reference/discriminated-unions.md)等位。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-302">The previous observations about performance with struct tuples and records also holds for [F# Discriminated Unions](../language-reference/discriminated-unions.md).</span></span> <span data-ttu-id="ff0a0-303">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-303">Consider the following code:</span></span>

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

<span data-ttu-id="ff0a0-304">定義單一案例的區分等位通常是為了進行領域模型化。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-304">It's common to define single-case Discriminated Unions like this for domain modeling.</span></span> <span data-ttu-id="ff0a0-305">當您使用[BenchmarkDotNet](https://benchmarkdotnet.org/)之類的統計效能評定工具來評估這些函式時，會發現 `structReverseName` 執行速度比小型字串快 25% `reverseName` 。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-305">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that `structReverseName` runs about 25% faster than `reverseName` for small strings.</span></span> <span data-ttu-id="ff0a0-306">對於大型字串，兩者都有相同的執行。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-306">For large strings, both perform about the same.</span></span> <span data-ttu-id="ff0a0-307">因此，在此情況下，最好是使用結構。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-307">So, in this case, it's always preferable to use a struct.</span></span> <span data-ttu-id="ff0a0-308">如先前所述，一律測量並不會在假設或直覺上運作。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-308">As previously mentioned, always measure and do not operate on assumptions or intuition.</span></span>

<span data-ttu-id="ff0a0-309">雖然先前的範例顯示結構區分聯集產生較佳的效能，但在模型化定義域時，通常會有更大的區分等位。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-309">Although the previous example showed that a struct Discriminated Union yielded better performance, it is common to have larger Discriminated Unions when modeling a domain.</span></span> <span data-ttu-id="ff0a0-310">較大的資料類型（例如，如果它們是結構而定）可能也不會執行，因為可能會涉及更多的複製作業。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-310">Larger data types like that may not perform as well if they are structs depending on the operations on them, since more copying could be involved.</span></span>

### <a name="functional-programming-and-mutation"></a><span data-ttu-id="ff0a0-311">功能性程式設計和變化</span><span class="sxs-lookup"><span data-stu-id="ff0a0-311">Functional programming and mutation</span></span>

<span data-ttu-id="ff0a0-312">F # 值預設是不可變的，這可讓您避免特定類別的錯誤（特別是涉及並行處理和平行處理原則的問題）。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-312">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="ff0a0-313">不過，在某些情況下，為了達到執行時間或記憶體配置的最佳（或甚至合理）效率，可以使用就地的狀態變動來執行工作範圍。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-313">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="ff0a0-314">這可以透過使用關鍵字的 F # 來選擇 `mutable` 。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-314">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="ff0a0-315">`mutable`在 F # 中使用，可能會覺得功能純度的機率。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-315">Use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="ff0a0-316">這是可理解的，但功能純度可能會有效能目標的機率。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-316">This is understandable, but functional purity everywhere can be at odds with performance goals.</span></span> <span data-ttu-id="ff0a0-317">入侵是要封裝變動，讓呼叫端不必在意呼叫函式時所發生的情況。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-317">A compromise is to encapsulate mutation such that callers need not care about what happens when they call a function.</span></span> <span data-ttu-id="ff0a0-318">這可讓您針對效能關鍵程式碼，透過以變化為基礎的執行來撰寫功能介面。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-318">This allows you to write a functional interface over a mutation-based implementation for performance-critical code.</span></span>

#### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="ff0a0-319">在不可變的介面中包裝可變的程式碼</span><span class="sxs-lookup"><span data-stu-id="ff0a0-319">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="ff0a0-320">透過參考透明度作為目標，撰寫程式碼不會公開效能關鍵函式的可變動 underbelly，是很重要的。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-320">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="ff0a0-321">例如，下列程式碼會實 `Array.contains` 作用於 F # 核心程式庫中的函式：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-321">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

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

<span data-ttu-id="ff0a0-322">多次呼叫此函式並不會變更基礎陣列，也不需要維護任何使用它的可變狀態。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-322">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="ff0a0-323">它參考上透明，即使其中幾乎每一行程式碼都使用變化。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-323">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

#### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="ff0a0-324">考慮在類別中封裝可變數據</span><span class="sxs-lookup"><span data-stu-id="ff0a0-324">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="ff0a0-325">先前的範例使用單一函式來封裝使用可變動資料的作業。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-325">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="ff0a0-326">對於更複雜的資料集，這不一定是足夠的。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-326">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="ff0a0-327">請考慮下列函數集：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-327">Consider the following sets of functions:</span></span>

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

<span data-ttu-id="ff0a0-328">這段程式碼的效能良好，但它會公開由呼叫端負責維護的以變化為基礎的資料結構。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-328">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="ff0a0-329">這可以包裝在類別內，而且沒有可變更的基礎成員：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-329">This can be wrapped inside of a class with no underlying members that can change:</span></span>

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

<span data-ttu-id="ff0a0-330">`Closure1Table`封裝基礎的變動式資料結構，因此不會強制呼叫端維護基礎資料結構。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-330">`Closure1Table` encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="ff0a0-331">類別是一種強大的方式，可封裝以變化為基礎的資料和常式，而不會向呼叫端公開細節。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-331">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

#### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="ff0a0-332">偏好 `let mutable` 參考資料格</span><span class="sxs-lookup"><span data-stu-id="ff0a0-332">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="ff0a0-333">參考儲存格是一種方式，代表值的參考，而不是值本身。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-333">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="ff0a0-334">雖然它們可以用於效能關鍵程式碼，但不建議您這麼做。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-334">Although they can be used for performance-critical code, they are not recommended.</span></span> <span data-ttu-id="ff0a0-335">請考慮下列範例：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-335">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="ff0a0-336">使用參考儲存格現在「干擾」所有後續的程式碼，都必須對基礎資料進行取值和重新參考。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-336">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="ff0a0-337">相反地，請考慮 `let mutable` ：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-337">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="ff0a0-338">除了 lambda 運算式中間的單一變化點之外，所有其他接觸的程式碼都 `acc` 可以使用與一般系結不可變值相同的方式來執行這項操作 `let` 。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-338">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="ff0a0-339">這可讓您更輕鬆地隨著時間變更。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-339">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="ff0a0-340">物件程式設計</span><span class="sxs-lookup"><span data-stu-id="ff0a0-340">Object programming</span></span>

<span data-ttu-id="ff0a0-341">F # 具有物件和麵向物件（OO）概念的完整支援。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-341">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="ff0a0-342">雖然許多 OO 概念都非常強大且實用，但並非全部都適合使用。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-342">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="ff0a0-343">下列清單提供有關在高階的 OO 功能類別的指引。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-343">The following lists offer guidance on categories of OO features at a high level.</span></span>

<span data-ttu-id="ff0a0-344">**在許多情況下，請考慮使用這些功能：**</span><span class="sxs-lookup"><span data-stu-id="ff0a0-344">**Consider using these features in many situations:**</span></span>

* <span data-ttu-id="ff0a0-345">點標記法（ `x.Length` ）</span><span class="sxs-lookup"><span data-stu-id="ff0a0-345">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="ff0a0-346">實例成員</span><span class="sxs-lookup"><span data-stu-id="ff0a0-346">Instance members</span></span>
* <span data-ttu-id="ff0a0-347">隱含的函式</span><span class="sxs-lookup"><span data-stu-id="ff0a0-347">Implicit constructors</span></span>
* <span data-ttu-id="ff0a0-348">靜態成員</span><span class="sxs-lookup"><span data-stu-id="ff0a0-348">Static members</span></span>
* <span data-ttu-id="ff0a0-349">索引子標記法（ `arr.[x]` ）</span><span class="sxs-lookup"><span data-stu-id="ff0a0-349">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="ff0a0-350">命名和選擇性引數</span><span class="sxs-lookup"><span data-stu-id="ff0a0-350">Named and Optional arguments</span></span>
* <span data-ttu-id="ff0a0-351">介面和介面的實現</span><span class="sxs-lookup"><span data-stu-id="ff0a0-351">Interfaces and interface implementations</span></span>

<span data-ttu-id="ff0a0-352">**請先不要觸達這些功能，但當它們很方便解決問題時，請謹慎套用：**</span><span class="sxs-lookup"><span data-stu-id="ff0a0-352">**Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:**</span></span>

* <span data-ttu-id="ff0a0-353">方法多載</span><span class="sxs-lookup"><span data-stu-id="ff0a0-353">Method overloading</span></span>
* <span data-ttu-id="ff0a0-354">封裝的可變數據</span><span class="sxs-lookup"><span data-stu-id="ff0a0-354">Encapsulated mutable data</span></span>
* <span data-ttu-id="ff0a0-355">類型的運算子</span><span class="sxs-lookup"><span data-stu-id="ff0a0-355">Operators on types</span></span>
* <span data-ttu-id="ff0a0-356">自動屬性</span><span class="sxs-lookup"><span data-stu-id="ff0a0-356">Auto properties</span></span>
* <span data-ttu-id="ff0a0-357">執行 `IDisposable` 和`IEnumerable`</span><span class="sxs-lookup"><span data-stu-id="ff0a0-357">Implementing `IDisposable` and `IEnumerable`</span></span>
* <span data-ttu-id="ff0a0-358">類型延伸模組</span><span class="sxs-lookup"><span data-stu-id="ff0a0-358">Type extensions</span></span>
* <span data-ttu-id="ff0a0-359">事件</span><span class="sxs-lookup"><span data-stu-id="ff0a0-359">Events</span></span>
* <span data-ttu-id="ff0a0-360">結構</span><span class="sxs-lookup"><span data-stu-id="ff0a0-360">Structs</span></span>
* <span data-ttu-id="ff0a0-361">委派</span><span class="sxs-lookup"><span data-stu-id="ff0a0-361">Delegates</span></span>
* <span data-ttu-id="ff0a0-362">列舉</span><span class="sxs-lookup"><span data-stu-id="ff0a0-362">Enums</span></span>

<span data-ttu-id="ff0a0-363">**除非您必須使用這些功能，否則通常會予以避免：**</span><span class="sxs-lookup"><span data-stu-id="ff0a0-363">**Generally avoid these features unless you must use them:**</span></span>

* <span data-ttu-id="ff0a0-364">繼承型型別階層和實作為繼承</span><span class="sxs-lookup"><span data-stu-id="ff0a0-364">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="ff0a0-365">Null 和`Unchecked.defaultof<_>`</span><span class="sxs-lookup"><span data-stu-id="ff0a0-365">Nulls and `Unchecked.defaultof<_>`</span></span>

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="ff0a0-366">偏好透過繼承撰寫</span><span class="sxs-lookup"><span data-stu-id="ff0a0-366">Prefer composition over inheritance</span></span>

<span data-ttu-id="ff0a0-367">透過[繼承撰寫](https://en.wikipedia.org/wiki/Composition_over_inheritance)是一種長期的用法，可以讓 F # 程式碼符合。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-367">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="ff0a0-368">基本原則是，您不應該公開基類，並強制呼叫端從該基類繼承來取得功能。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-368">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="ff0a0-369">如果您不需要類別，請使用物件運算式來執行介面</span><span class="sxs-lookup"><span data-stu-id="ff0a0-369">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="ff0a0-370">[物件運算式](../language-reference/object-expressions.md)可讓您即時執行介面，將實的介面系結至值，而不需要在類別內執行此動作。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-370">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="ff0a0-371">這很方便，特別是當您_只_需要執行介面，而不需要完整類別時。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-371">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="ff0a0-372">例如，下列程式碼會在[Ionide](https://ionide.io/)中執行，以提供程式碼修正動作（如果您已新增不具有 `open` 語句的符號）：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-372">For example, here is the code that is run in [Ionide](https://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

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

<span data-ttu-id="ff0a0-373">因為與 Visual Studio Code API 互動時不需要類別，所以物件運算式是適用于此的理想工具。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-373">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="ff0a0-374">當您想要以臨機操作方式將具有測試常式的介面 stub 時，它們也非常適合進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-374">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="consider-type-abbreviations-to-shorten-signatures"></a><span data-ttu-id="ff0a0-375">請考慮輸入縮寫來縮短簽章</span><span class="sxs-lookup"><span data-stu-id="ff0a0-375">Consider Type Abbreviations to shorten signatures</span></span>

<span data-ttu-id="ff0a0-376">[類型縮寫](../language-reference/type-abbreviations.md)是將標籤指派給另一種類型（例如，函式簽章或更複雜的類型）的便利方式。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-376">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="ff0a0-377">例如，下列別名會將標籤指派給使用[CNTK](https://docs.microsoft.com/cognitive-toolkit/)（深度學習程式庫）定義計算所需的內容：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-377">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](https://docs.microsoft.com/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="ff0a0-378">`Computation`名稱是一種方便的方式，表示符合其別名的任何功能。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-378">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="ff0a0-379">使用這類的類型縮寫十分方便，並允許更簡潔的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-379">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="ff0a0-380">避免使用類型縮寫來代表您的網域</span><span class="sxs-lookup"><span data-stu-id="ff0a0-380">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="ff0a0-381">雖然類型縮寫對於提供名稱給函式簽章很方便，但在縮寫其他類型時可能會造成混淆。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-381">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="ff0a0-382">請考慮下列縮寫：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-382">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="ff0a0-383">這可能會讓您以多種方式混淆：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-383">This can be confusing in multiple ways:</span></span>

* <span data-ttu-id="ff0a0-384">`BufferSize`不是抽象概念;它只是一個整數的另一個名稱。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-384">`BufferSize` is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="ff0a0-385">如果 `BufferSize` 公開在公用 API 中，您可以輕易地誤解，而不只是表示 `int` 。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-385">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="ff0a0-386">一般來說，網域型別有多個屬性，而且不是像這樣的基本類型 `int` 。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-386">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="ff0a0-387">此縮寫違反該假設。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-387">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="ff0a0-388">的大小寫 `BufferSize` （PascalCase）表示此類型包含更多資料。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-388">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="ff0a0-389">相較于將具名引數提供給函式，此別名並不提供更清楚的清晰度。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-389">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="ff0a0-390">縮寫不會在編譯的 IL 中進行資訊清單;這只是一個整數，而此別名是編譯時間結構。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-390">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

<span data-ttu-id="ff0a0-391">總而言之，類型縮寫的缺陷是它們**不**是縮寫的類型的抽象概念。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-391">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="ff0a0-392">在上述範例中， `BufferSize` 只是 `int` 在幕後，沒有其他資料，也是來自類型系統的任何優點（除了已經有的內容之外） `int` 。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-392">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>

<span data-ttu-id="ff0a0-393">使用類型縮寫來表示網域的替代方法是使用單一案例的區分等位。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-393">An alternative approach to using type abbreviations to represent a domain is to use single-case discriminated unions.</span></span> <span data-ttu-id="ff0a0-394">先前的範例可以模型化，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-394">The previous sample can be modeled as follows:</span></span>

```fsharp
type BufferSize = BufferSize of int
```

<span data-ttu-id="ff0a0-395">如果您撰寫的程式碼是以 `BufferSize` 及其基礎值來運作，您需要建立一個，而不是傳入任何任意整數：</span><span class="sxs-lookup"><span data-stu-id="ff0a0-395">If you write code that operates in terms of `BufferSize` and its underlying value, you need to construct one rather than pass in any arbitrary integer:</span></span>

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

<span data-ttu-id="ff0a0-396">這可減少錯誤地將任意整數傳遞至函式的可能性 `send` ，因為呼叫端必須 `BufferSize` 先建立類型來包裝值，再呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="ff0a0-396">This reduces the likelihood of mistakenly passing an arbitrary integer into the `send` function, because the caller must construct a `BufferSize` type to wrap a value before calling the function.</span></span>
