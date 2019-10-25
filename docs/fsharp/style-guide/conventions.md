---
title: F# 編碼慣例
description: 瞭解撰寫F#程式碼時的一般方針和慣用語。
ms.date: 10/22/2019
ms.openlocfilehash: 6700f64aa61308cbfc0b7a38724d69a281a088db
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799110"
---
# <a name="f-coding-conventions"></a><span data-ttu-id="9f904-103">F# 編碼慣例</span><span class="sxs-lookup"><span data-stu-id="9f904-103">F# coding conventions</span></span>

<span data-ttu-id="9f904-104">下列慣例是從使用大型F#代碼基底的經驗來制定。</span><span class="sxs-lookup"><span data-stu-id="9f904-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="9f904-105">[良好F#程式碼的五大原則](index.md#five-principles-of-good-f-code)是每個建議的基礎。</span><span class="sxs-lookup"><span data-stu-id="9f904-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="9f904-106">它們與[ F#元件設計指導方針](component-design-guidelines.md)有關，但適用于任何F#程式碼，而不只是程式庫之類的元件。</span><span class="sxs-lookup"><span data-stu-id="9f904-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="9f904-107">組織程式碼</span><span class="sxs-lookup"><span data-stu-id="9f904-107">Organizing code</span></span>

<span data-ttu-id="9f904-108">F#有兩種主要方式可組織程式碼：模組和命名空間。</span><span class="sxs-lookup"><span data-stu-id="9f904-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="9f904-109">這些類似，但有下列差異：</span><span class="sxs-lookup"><span data-stu-id="9f904-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="9f904-110">命名空間會編譯為 .NET 命名空間。</span><span class="sxs-lookup"><span data-stu-id="9f904-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="9f904-111">模組會編譯為靜態類別。</span><span class="sxs-lookup"><span data-stu-id="9f904-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="9f904-112">命名空間一律是最上層。</span><span class="sxs-lookup"><span data-stu-id="9f904-112">Namespaces are always top level.</span></span> <span data-ttu-id="9f904-113">模組可以是最上層，並在其他模組中嵌套。</span><span class="sxs-lookup"><span data-stu-id="9f904-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="9f904-114">命名空間可以跨越多個檔案。</span><span class="sxs-lookup"><span data-stu-id="9f904-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="9f904-115">模組不能。</span><span class="sxs-lookup"><span data-stu-id="9f904-115">Modules cannot.</span></span>
* <span data-ttu-id="9f904-116">您可以使用 `[<RequireQualifiedAccess>]` 和 `[<AutoOpen>]`裝飾模組。</span><span class="sxs-lookup"><span data-stu-id="9f904-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="9f904-117">下列指導方針可協助您使用這些指引來組織您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9f904-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="9f904-118">偏好位於最上層的命名空間</span><span class="sxs-lookup"><span data-stu-id="9f904-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="9f904-119">針對任何可公開取用的程式碼，命名空間會優先于最上層的模組。</span><span class="sxs-lookup"><span data-stu-id="9f904-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="9f904-120">因為它們會編譯為 .NET 命名空間，所以可以從C#取用，而不會有任何問題。</span><span class="sxs-lookup"><span data-stu-id="9f904-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="9f904-121">當只從F#呼叫時，使用最上層模組可能不會出現不同，但C#對於取用者，必須使用`MyCode`模組限定`MyClass`，可能會讓呼叫端感到驚訝。</span><span class="sxs-lookup"><span data-stu-id="9f904-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="9f904-122">小心套用 `[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="9f904-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="9f904-123">`[<AutoOpen>]` 結構可以會污染可供呼叫端使用的範圍，而有問題的答案則是「魔術」。</span><span class="sxs-lookup"><span data-stu-id="9f904-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="9f904-124">這通常不是件好事。</span><span class="sxs-lookup"><span data-stu-id="9f904-124">This is generally not a good thing.</span></span> <span data-ttu-id="9f904-125">此規則的F#例外狀況是核心程式庫本身（但此事實也是有爭議的）。</span><span class="sxs-lookup"><span data-stu-id="9f904-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="9f904-126">不過，如果您有想要與公用 API 分開組織之公用 API 的協助程式功能，這是很方便的。</span><span class="sxs-lookup"><span data-stu-id="9f904-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

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

<span data-ttu-id="9f904-127">如此一來，您就不需要在每次呼叫時都完整限定協助程式，即可從函式的公用 API 中明確地分隔執行詳細資料。</span><span class="sxs-lookup"><span data-stu-id="9f904-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="9f904-128">此外，在命名空間層級公開擴充方法和運算式產生器，可以使用 `[<AutoOpen>]`進行整齊表示。</span><span class="sxs-lookup"><span data-stu-id="9f904-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="9f904-129">當名稱可能發生衝突，或您覺得它有助於可讀性時，請使用 `[<RequireQualifiedAccess>]`</span><span class="sxs-lookup"><span data-stu-id="9f904-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="9f904-130">將 `[<RequireQualifiedAccess>]` 屬性加入模組中，表示模組可能無法開啟，而且對模組元素的參考需要明確限定的存取權。</span><span class="sxs-lookup"><span data-stu-id="9f904-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="9f904-131">例如，`Microsoft.FSharp.Collections.List` 模組具有這個屬性。</span><span class="sxs-lookup"><span data-stu-id="9f904-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="9f904-132">當模組中的函數和值有可能與其他模組中的名稱衝突的名稱時，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="9f904-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="9f904-133">需要限定的存取權可能會大幅增加程式庫的長期維護性和 evolvability。</span><span class="sxs-lookup"><span data-stu-id="9f904-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="9f904-134">排序 `open` 語句拓撲</span><span class="sxs-lookup"><span data-stu-id="9f904-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="9f904-135">在F#中，宣告的順序很重要，包括 `open`語句。</span><span class="sxs-lookup"><span data-stu-id="9f904-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="9f904-136">這與不同C#之處在于，`using`和`using static`的效果與檔案中這些語句的順序無關。</span><span class="sxs-lookup"><span data-stu-id="9f904-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="9f904-137">在F#中，開啟範圍中的專案可能會遮蔽其他已存在的專案。</span><span class="sxs-lookup"><span data-stu-id="9f904-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="9f904-138">這表示重新排列 `open` 語句可能會改變程式碼的意義。</span><span class="sxs-lookup"><span data-stu-id="9f904-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="9f904-139">因此，通常不建議所有 `open` 語句的任意排序（例如排序），以免您會產生可能預期的不同行為。</span><span class="sxs-lookup"><span data-stu-id="9f904-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is generally not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="9f904-140">相反地，我們建議您將它們排序[拓撲](https://en.wikipedia.org/wiki/Topological_sorting);也就是，依照您的系統_層_級的定義順序來排序您的 `open` 語句。</span><span class="sxs-lookup"><span data-stu-id="9f904-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="9f904-141">您也可以考慮在不同的拓撲層中進行英數位元排序。</span><span class="sxs-lookup"><span data-stu-id="9f904-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="9f904-142">例如，以下是F#編譯器服務公用 API 檔案的拓撲排序：</span><span class="sxs-lookup"><span data-stu-id="9f904-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

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

<span data-ttu-id="9f904-143">請注意，分行符號會分隔拓撲層，之後的每個圖層都會排序排序。</span><span class="sxs-lookup"><span data-stu-id="9f904-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="9f904-144">這會完全組織程式碼，而不會不小心遮蔽值。</span><span class="sxs-lookup"><span data-stu-id="9f904-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="9f904-145">使用類別來包含有副作用的值</span><span class="sxs-lookup"><span data-stu-id="9f904-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="9f904-146">將值初始化時，有很多時候會有副作用，例如將內容具現化至資料庫或其他遠端資源。</span><span class="sxs-lookup"><span data-stu-id="9f904-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="9f904-147">在模組中初始化這類專案，並在後續的函式中使用它是很吸引人的：</span><span class="sxs-lookup"><span data-stu-id="9f904-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

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

<span data-ttu-id="9f904-148">這通常是不好的想法，原因如下：</span><span class="sxs-lookup"><span data-stu-id="9f904-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="9f904-149">首先，應用程式設定會使用 `dep1` 和 `dep2`推送至程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="9f904-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="9f904-150">這在較大的基本代碼基底中很容易維護。</span><span class="sxs-lookup"><span data-stu-id="9f904-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="9f904-151">第二，如果您的元件本身會使用多個執行緒，則靜態初始化的資料應該不會包含不具備執行緒安全的值。</span><span class="sxs-lookup"><span data-stu-id="9f904-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="9f904-152">`dep3`會明顯地違反此情況。</span><span class="sxs-lookup"><span data-stu-id="9f904-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="9f904-153">最後，模組初始化會編譯成整個編譯單位的靜態函式。</span><span class="sxs-lookup"><span data-stu-id="9f904-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="9f904-154">如果在該模組的 let 系結值初始化中發生任何錯誤，則會將它視為 `TypeInitializationException`，然後針對應用程式的整個存留期進行快取。</span><span class="sxs-lookup"><span data-stu-id="9f904-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="9f904-155">這可能很容易診斷。</span><span class="sxs-lookup"><span data-stu-id="9f904-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="9f904-156">通常，您可以嘗試進行的內部例外狀況，但如果沒有，則不會告知根本原因。</span><span class="sxs-lookup"><span data-stu-id="9f904-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="9f904-157">相反地，只要使用簡單的類別來保存相依性：</span><span class="sxs-lookup"><span data-stu-id="9f904-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="9f904-158">這會啟用下列功能：</span><span class="sxs-lookup"><span data-stu-id="9f904-158">This enables the following:</span></span>

1. <span data-ttu-id="9f904-159">將任何相依的狀態推送至 API 本身以外的地方。</span><span class="sxs-lookup"><span data-stu-id="9f904-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="9f904-160">設定現在可以在 API 外部完成。</span><span class="sxs-lookup"><span data-stu-id="9f904-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="9f904-161">相依值的初始化錯誤不太可能會 `TypeInitializationException`資訊清單。</span><span class="sxs-lookup"><span data-stu-id="9f904-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="9f904-162">API 現在更容易測試。</span><span class="sxs-lookup"><span data-stu-id="9f904-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="9f904-163">錯誤管理</span><span class="sxs-lookup"><span data-stu-id="9f904-163">Error management</span></span>

<span data-ttu-id="9f904-164">大型系統中的錯誤管理是一項複雜且差別細微的工作，而且沒有任何銀級的專案，以確保您的系統具有容錯能力，而且行為良好。</span><span class="sxs-lookup"><span data-stu-id="9f904-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="9f904-165">下列指導方針應該提供流覽這個艱難空間的指引。</span><span class="sxs-lookup"><span data-stu-id="9f904-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="9f904-166">表示在您的網域內建類型中的錯誤案例和不合法的狀態</span><span class="sxs-lookup"><span data-stu-id="9f904-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="9f904-167">使用[區分](../language-reference/discriminated-unions.md)聯集F# ，可讓您在類型系統中代表有問題的程式狀態。</span><span class="sxs-lookup"><span data-stu-id="9f904-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="9f904-168">例如:</span><span class="sxs-lookup"><span data-stu-id="9f904-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="9f904-169">在此情況下，有三種已知的方式可讓銀行帳戶的提款 money 失敗。</span><span class="sxs-lookup"><span data-stu-id="9f904-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="9f904-170">每個錯誤案例都會以類型表示，因此可在整個程式中安全地處理。</span><span class="sxs-lookup"><span data-stu-id="9f904-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="9f904-171">一般來說，如果您可以建立在網域中可能會**失敗**之不同方式的模型，則不會再將錯誤處理常式代碼視為您必須處理的某些專案，而不是一般程式流程。</span><span class="sxs-lookup"><span data-stu-id="9f904-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="9f904-172">這只是一般程式流程的一部分，並不會視為**例外**狀況。</span><span class="sxs-lookup"><span data-stu-id="9f904-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="9f904-173">這有兩個主要優點：</span><span class="sxs-lookup"><span data-stu-id="9f904-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="9f904-174">隨著您的網域在一段時間內的變更，更容易維護。</span><span class="sxs-lookup"><span data-stu-id="9f904-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="9f904-175">錯誤案例較容易進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="9f904-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="9f904-176">當錯誤無法以類型表示時，使用例外狀況</span><span class="sxs-lookup"><span data-stu-id="9f904-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="9f904-177">並非所有的錯誤都可以在問題網域中表示。</span><span class="sxs-lookup"><span data-stu-id="9f904-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="9f904-178">這類錯誤本質上是*例外*狀況，因此能夠引發和攔截中F#的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9f904-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="9f904-179">首先，建議您閱讀[例外狀況設計指導方針](../../standard/design-guidelines/exceptions.md)。</span><span class="sxs-lookup"><span data-stu-id="9f904-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="9f904-180">這些也適用于F#。</span><span class="sxs-lookup"><span data-stu-id="9f904-180">These are also applicable to F#.</span></span>

<span data-ttu-id="9f904-181">中F#可用來引發例外狀況的主要結構，應依照下列喜好設定順序來考慮：</span><span class="sxs-lookup"><span data-stu-id="9f904-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="9f904-182">功能</span><span class="sxs-lookup"><span data-stu-id="9f904-182">Function</span></span> | <span data-ttu-id="9f904-183">語法</span><span class="sxs-lookup"><span data-stu-id="9f904-183">Syntax</span></span> | <span data-ttu-id="9f904-184">用途</span><span class="sxs-lookup"><span data-stu-id="9f904-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="9f904-185">使用指定的引數名稱引發 `System.ArgumentNullException`。</span><span class="sxs-lookup"><span data-stu-id="9f904-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="9f904-186">使用指定的引數名稱和訊息，引發 `System.ArgumentException`。</span><span class="sxs-lookup"><span data-stu-id="9f904-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="9f904-187">使用指定的訊息引發 `System.InvalidOperationException`。</span><span class="sxs-lookup"><span data-stu-id="9f904-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="9f904-188">用來擲回例外狀況的一般用途機制。</span><span class="sxs-lookup"><span data-stu-id="9f904-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="9f904-189">使用指定的訊息引發 `System.Exception`。</span><span class="sxs-lookup"><span data-stu-id="9f904-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="9f904-190">使用格式字串及其輸入所決定的訊息，引發 `System.Exception`。</span><span class="sxs-lookup"><span data-stu-id="9f904-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="9f904-191">在適當的情況下，請使用 `nullArg`、`invalidArg` 和 `invalidOp` 作為用來擲回 `ArgumentNullException`、`ArgumentException` 和 `InvalidOperationException` 的機制。</span><span class="sxs-lookup"><span data-stu-id="9f904-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="9f904-192">通常應該避免使用 `failwith` 和 `failwithf` 函數，因為它們會引發基底 `Exception` 類型，而不是特定的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9f904-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="9f904-193">根據例外狀況[設計指導方針](../../standard/design-guidelines/exceptions.md)，您會想要在可以時引發更具體的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9f904-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="using-exception-handling-syntax"></a><span data-ttu-id="9f904-194">使用例外狀況處理語法</span><span class="sxs-lookup"><span data-stu-id="9f904-194">Using exception-handling syntax</span></span>

<span data-ttu-id="9f904-195">F#支援透過`try...with`語法的例外狀況模式：</span><span class="sxs-lookup"><span data-stu-id="9f904-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="9f904-196">如果您想要讓程式碼保持整潔，請將功能與模式比對的例外狀況協調，以降低執行的情況。</span><span class="sxs-lookup"><span data-stu-id="9f904-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="9f904-197">處理這種情況的方法之一，就是使用作用中的[模式](../language-reference/active-patterns.md)來分組發生錯誤案例的功能，以及例外狀況本身。</span><span class="sxs-lookup"><span data-stu-id="9f904-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="9f904-198">例如，您可能會使用 API，當它擲回例外狀況時，會在例外狀況中繼資料中括住重要資訊。</span><span class="sxs-lookup"><span data-stu-id="9f904-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="9f904-199">在使用中模式的已捕捉例外狀況內解除包裝有用的值，並在某些情況下傳回該值會很有説明。</span><span class="sxs-lookup"><span data-stu-id="9f904-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="9f904-200">請勿使用 monadic 錯誤處理來取代例外狀況</span><span class="sxs-lookup"><span data-stu-id="9f904-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="9f904-201">在功能程式設計中，例外狀況會被視為有點 taboo。</span><span class="sxs-lookup"><span data-stu-id="9f904-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="9f904-202">事實上，例外狀況違反了純度，因此可以放心地將它們視為不太實用。</span><span class="sxs-lookup"><span data-stu-id="9f904-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="9f904-203">不過，這會忽略程式碼必須執行的實際情況，而且可能會發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="9f904-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="9f904-204">一般來說，請撰寫程式碼，假設大部分專案都不是純粹的，也不是總計，以儘量減少不愉快的意外。</span><span class="sxs-lookup"><span data-stu-id="9f904-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="9f904-205">對於 .NET 執行時間和跨語言生態系統中的相關性和」適當性，請務必考慮下列各項核心的優缺點：</span><span class="sxs-lookup"><span data-stu-id="9f904-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="9f904-206">其中包含詳細的診斷資訊，在發生問題時很有説明。</span><span class="sxs-lookup"><span data-stu-id="9f904-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="9f904-207">這是執行時間和其他 .NET 語言的良好理解。</span><span class="sxs-lookup"><span data-stu-id="9f904-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="9f904-208">相較于無法以臨機操作方式來執行某些部分的語義，它們可以減少重複使用的程式碼，以*避免*例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9f904-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="9f904-209">第三個點很重要。</span><span class="sxs-lookup"><span data-stu-id="9f904-209">This third point is critical.</span></span> <span data-ttu-id="9f904-210">針對重要複雜的作業，無法使用例外狀況可能會導致處理如下的結構：</span><span class="sxs-lookup"><span data-stu-id="9f904-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="9f904-211">這可以輕鬆地導致像是「stringly 類型」錯誤的模式比對等脆弱的程式碼：</span><span class="sxs-lookup"><span data-stu-id="9f904-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="9f904-212">此外，若要對傳回 "更好" 類型的「簡單」函式，忍受任何例外狀況，可能會很吸引人：</span><span class="sxs-lookup"><span data-stu-id="9f904-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="9f904-213">可惜的是，`tryReadAllText` 可能會根據檔案系統上的各種專案來擲回許多例外狀況，而此程式碼會捨棄您的環境中可能發生錯誤的任何相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9f904-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="9f904-214">如果您將此程式碼取代為結果類型，則會回到「stringly 類型」錯誤訊息剖析：</span><span class="sxs-lookup"><span data-stu-id="9f904-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

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

<span data-ttu-id="9f904-215">而將例外狀況物件本身放在 `Error` 的函式中，只會強制您在呼叫位置（而不是在函式）中正確處理例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="9f904-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="9f904-216">這麼做可以有效地建立已檢查的例外狀況，這是以 API 的呼叫者身分處理的 unfun。</span><span class="sxs-lookup"><span data-stu-id="9f904-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="9f904-217">在上述範例中，有一個很好的替代方式，就是攔截*特定*的例外狀況，並在該例外狀況的內容中傳回有意義的值。</span><span class="sxs-lookup"><span data-stu-id="9f904-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="9f904-218">如果您修改 `tryReadAllText` 函式，如下所示，`None` 會有更多意義：</span><span class="sxs-lookup"><span data-stu-id="9f904-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="9f904-219">此函式會立即適當地處理找不到檔案的情況，並將該意義指派給傳回，而不是當做全部攔截。</span><span class="sxs-lookup"><span data-stu-id="9f904-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="9f904-220">這個傳回值可以對應至該錯誤案例，而不會捨棄任何內容資訊或強制呼叫端處理常式代碼中可能不相關的案例。</span><span class="sxs-lookup"><span data-stu-id="9f904-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="9f904-221">如 `Result<'Success, 'Error>` 之類的類型適用于不是嵌套的基本作業，而F#選擇性類型則非常適合用來表示何時可以傳回任何*內容*或*任何*內容。</span><span class="sxs-lookup"><span data-stu-id="9f904-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="9f904-222">不過，它們不是例外狀況的取代，而且不應該用於嘗試取代例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9f904-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="9f904-223">相反地，應該謹慎套用，以以目標方式處理例外狀況和錯誤管理原則的特定層面。</span><span class="sxs-lookup"><span data-stu-id="9f904-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="9f904-224">部分應用程式和無點程式設計</span><span class="sxs-lookup"><span data-stu-id="9f904-224">Partial application and point-free programming</span></span>

<span data-ttu-id="9f904-225">F#支援部分應用程式，因此可以用各種不同的方式，以無點的風格進行程式設計。</span><span class="sxs-lookup"><span data-stu-id="9f904-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="9f904-226">這對於在模組內重複使用程式碼或執行某個專案很有説明，但通常並不是公開公開的東西。</span><span class="sxs-lookup"><span data-stu-id="9f904-226">This can be beneficial for code reuse within a module or the implementation of something, but it is generally not something to expose publicly.</span></span> <span data-ttu-id="9f904-227">一般來說，無點程式設計並不是本身的本身，而且可以為未可以沉浸樣式的人員加入重要的認知屏障。</span><span class="sxs-lookup"><span data-stu-id="9f904-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="9f904-228">請勿在公用 Api 中使用部分應用程式和 currying</span><span class="sxs-lookup"><span data-stu-id="9f904-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="9f904-229">除了例外狀況外，在公用 Api 中使用部分應用程式可能會對取用者造成混淆。</span><span class="sxs-lookup"><span data-stu-id="9f904-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="9f904-230">通常，程式碼中F#的 `let`系結值為**值**，而不是**函數值**。</span><span class="sxs-lookup"><span data-stu-id="9f904-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="9f904-231">將值和函數值混在一起，可讓您在 exchange 中儲存少量的程式碼，以產生相當多的認知額外負荷，尤其是如果與 `>>` 的運算子結合以撰寫函式。</span><span class="sxs-lookup"><span data-stu-id="9f904-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="9f904-232">考慮無點程式設計的工具含意</span><span class="sxs-lookup"><span data-stu-id="9f904-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="9f904-233">擴充函數不會標示其引數。</span><span class="sxs-lookup"><span data-stu-id="9f904-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="9f904-234">這會影響工具。</span><span class="sxs-lookup"><span data-stu-id="9f904-234">This has tooling implications.</span></span> <span data-ttu-id="9f904-235">請考慮下列兩個功能：</span><span class="sxs-lookup"><span data-stu-id="9f904-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="9f904-236">兩者都是有效的函式，但 `funcWithApplication` 是一個擴充函數。</span><span class="sxs-lookup"><span data-stu-id="9f904-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="9f904-237">當您將滑鼠停留在編輯器中的類型時，您會看到：</span><span class="sxs-lookup"><span data-stu-id="9f904-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="9f904-238">在呼叫位置，工具（例如 Visual Studio）中的工具提示不會提供有意義的資訊，讓您瞭解 `string` 和 `int` 輸入類型實際上所代表的內容。</span><span class="sxs-lookup"><span data-stu-id="9f904-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="9f904-239">如果您遇到無點程式碼，例如可公開使用的 `funcWithApplication`，建議您執行完整的η擴充，讓工具可以針對引數取得有意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="9f904-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="9f904-240">此外，如果不可能，則偵錯工具不會有困難的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9f904-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="9f904-241">偵錯工具會依賴系結至名稱的值（例如，`let` 系結），以便您可以在執行期間檢查中間值。</span><span class="sxs-lookup"><span data-stu-id="9f904-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="9f904-242">當您的程式碼沒有任何要檢查的值時，不會有任何可進行的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="9f904-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="9f904-243">在未來，偵錯工具可能會演變為根據先前執行的路徑來合成這些值，但不建議您在*可能*的偵測功能上建立您的理由。</span><span class="sxs-lookup"><span data-stu-id="9f904-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="9f904-244">將部分應用程式視為減少內部重複使用的技術</span><span class="sxs-lookup"><span data-stu-id="9f904-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="9f904-245">相較于先前的點，部分應用程式是一項很棒的工具，可減少應用程式內的重複使用或更深入的 API 內部。</span><span class="sxs-lookup"><span data-stu-id="9f904-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="9f904-246">這對於執行更複雜 Api 的單元測試很有説明，其中的重複使用通常是一項很難處理的難題。</span><span class="sxs-lookup"><span data-stu-id="9f904-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="9f904-247">例如，下列程式碼會示範如何完成大部分的模擬架構，讓您不需要對這類架構進行外部相依性，也必須瞭解相關的定制 API。</span><span class="sxs-lookup"><span data-stu-id="9f904-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="9f904-248">例如，請考慮下列解決方案的拓撲：</span><span class="sxs-lookup"><span data-stu-id="9f904-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

<span data-ttu-id="9f904-249">`ImplementationLogic.fsproj` 可能會公開程式碼，例如：</span><span class="sxs-lookup"><span data-stu-id="9f904-249">`ImplementationLogic.fsproj` might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="9f904-250">`ImplementationLogic.Tests.fsproj` 中的單元測試 `Transactions.doTransaction` 很簡單：</span><span class="sxs-lookup"><span data-stu-id="9f904-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fsproj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="9f904-251">部分套用 `doTransaction` 搭配模擬內容物件，可讓您在所有單元測試中呼叫函式，而不需要每次都要建立模擬內容：</span><span class="sxs-lookup"><span data-stu-id="9f904-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

```fsharp
namespace TransactionTests

open Xunit
open TransactionTypes
open TransactionsTestingUtil
open TransactionsTestingUtil.TransactionsTestable

let testableContext =
    { new ITransactionContext with
        member __.TheFirstMember() = ...
        member __.TheSecondMember() = ... }

let transactionRoutine = getTestableTransactionRoutine testableContext

[<Fact>]
let ``Test withdrawal transaction with 0.0 for balance``() =
    let expected = ...
    let actual = transactionRoutine TransactionType.Withdraw 0.0
    Assert.Equal(expected, actual)
```

<span data-ttu-id="9f904-252">這項技術不應通用地套用到整個程式碼基底，但這是減少複雜內部和單元測試這些內部專案的好方法。</span><span class="sxs-lookup"><span data-stu-id="9f904-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="9f904-253">存取控制</span><span class="sxs-lookup"><span data-stu-id="9f904-253">Access control</span></span>

<span data-ttu-id="9f904-254">F#有多個[存取控制](../language-reference/access-control.md)選項，繼承自 .net 執行時間中可用的內容。</span><span class="sxs-lookup"><span data-stu-id="9f904-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="9f904-255">這些不只適用于類型，您也可以將它們用於函數。</span><span class="sxs-lookup"><span data-stu-id="9f904-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="9f904-256">偏好非`public` 的類型和成員，直到您需要它們可公開取用為止。</span><span class="sxs-lookup"><span data-stu-id="9f904-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="9f904-257">這也可以減少取用者的需求。</span><span class="sxs-lookup"><span data-stu-id="9f904-257">This also minimizes what consumers couple to.</span></span>
* <span data-ttu-id="9f904-258">努力保持所有 helper 功能 `private`。</span><span class="sxs-lookup"><span data-stu-id="9f904-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="9f904-259">請考慮在 helper 函式的私用模組上使用 `[<AutoOpen>]` （如果它們變得很多）。</span><span class="sxs-lookup"><span data-stu-id="9f904-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="9f904-260">型別推斷和泛型</span><span class="sxs-lookup"><span data-stu-id="9f904-260">Type inference and generics</span></span>

<span data-ttu-id="9f904-261">型別推斷可為您節省許多樣板的輸入。</span><span class="sxs-lookup"><span data-stu-id="9f904-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="9f904-262">而編譯器中的F#自動一般化可以協助您撰寫更通用的程式碼，幾乎不需要額外的工作。</span><span class="sxs-lookup"><span data-stu-id="9f904-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="9f904-263">不過，這些功能並不是很普遍。</span><span class="sxs-lookup"><span data-stu-id="9f904-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="9f904-264">請考慮在公用 Api 中使用明確類型標記引數名稱，而且不依賴此的類型推斷。</span><span class="sxs-lookup"><span data-stu-id="9f904-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="9f904-265">這是因為**您**應該控制 API 的形式，而不是編譯器。</span><span class="sxs-lookup"><span data-stu-id="9f904-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="9f904-266">雖然編譯器可以在推斷型別時執行精細的作業，但如果它依賴的內部專案有變更的型別，則您的 API 可能會有變更的圖形。</span><span class="sxs-lookup"><span data-stu-id="9f904-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="9f904-267">這可能是您想要的，但幾乎肯定會導致下游取用者必須處理的中斷性 API 變更。</span><span class="sxs-lookup"><span data-stu-id="9f904-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="9f904-268">相反地，如果您明確控制公用 API 的形式，則可以控制這些重大變更。</span><span class="sxs-lookup"><span data-stu-id="9f904-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="9f904-269">在 DDD 詞彙中，這可以視為反損毀層。</span><span class="sxs-lookup"><span data-stu-id="9f904-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="9f904-270">請考慮為您的泛型引數提供有意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="9f904-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="9f904-271">除非您撰寫的是真正的一般程式碼，而不是特定的網域，否則有意義的名稱可以協助其他程式設計人員瞭解他們正在處理的網域。</span><span class="sxs-lookup"><span data-stu-id="9f904-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="9f904-272">例如，在與檔資料庫互動的內容中，名為 `'Document` 的型別參數，讓您使用的函式或成員可接受一般檔案類型。</span><span class="sxs-lookup"><span data-stu-id="9f904-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="9f904-273">請考慮使用 PascalCase 來命名泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="9f904-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="9f904-274">這是在 .NET 中執行工作的一般方式，因此建議您使用 PascalCase，而不要使用 snake_case 或 camelCase。</span><span class="sxs-lookup"><span data-stu-id="9f904-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="9f904-275">最後，對於不熟悉F#或大型程式碼基底的人員而言，自動一般化不一定是 boon 的。</span><span class="sxs-lookup"><span data-stu-id="9f904-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="9f904-276">使用泛型元件時，會發生認知額外負荷。</span><span class="sxs-lookup"><span data-stu-id="9f904-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="9f904-277">此外，如果自動一般化的函式不會與不同的輸入型別搭配使用（如果要用來做為這種類型，請單獨使用），在該時間點就不會有真正的優勢。</span><span class="sxs-lookup"><span data-stu-id="9f904-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="9f904-278">請務必考慮您撰寫的程式碼實際上是否受益于一般。</span><span class="sxs-lookup"><span data-stu-id="9f904-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="9f904-279">效能</span><span class="sxs-lookup"><span data-stu-id="9f904-279">Performance</span></span>

<span data-ttu-id="9f904-280">F#值預設為不可變，可讓您避免特定類別的錯誤（特別是涉及並行處理和平行處理原則的問題）。</span><span class="sxs-lookup"><span data-stu-id="9f904-280">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="9f904-281">不過，在某些情況下，為了達到執行時間或記憶體配置的最佳（或甚至合理）效率，可以使用就地的狀態變動來執行工作範圍。</span><span class="sxs-lookup"><span data-stu-id="9f904-281">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="9f904-282">您可以使用F#搭配`mutable`關鍵字的選擇來進行這項工作。</span><span class="sxs-lookup"><span data-stu-id="9f904-282">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="9f904-283">不過，在中F#使用 `mutable` 可能會有功能純度的機率。</span><span class="sxs-lookup"><span data-stu-id="9f904-283">However, use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="9f904-284">如果您調整從純度到[引用透明度](https://en.wikipedia.org/wiki/Referential_transparency)的期望，這就沒問題。</span><span class="sxs-lookup"><span data-stu-id="9f904-284">This is fine, if you adjust expectations from purity to [referential transparency](https://en.wikipedia.org/wiki/Referential_transparency).</span></span> <span data-ttu-id="9f904-285">參考透明度-不是純度-這是撰寫F#函式時的最終目標。</span><span class="sxs-lookup"><span data-stu-id="9f904-285">Referential transparency - not purity - is the end goal when writing F# functions.</span></span> <span data-ttu-id="9f904-286">這可讓您針對效能關鍵程式碼，透過以變化為基礎的執行來撰寫功能介面。</span><span class="sxs-lookup"><span data-stu-id="9f904-286">This allows you to write a functional interface over a mutation-based implementation for performance critical code.</span></span>

### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="9f904-287">在不可變的介面中包裝可變的程式碼</span><span class="sxs-lookup"><span data-stu-id="9f904-287">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="9f904-288">透過參考透明度作為目標，撰寫程式碼不會公開效能關鍵函式的可變動 underbelly，是很重要的。</span><span class="sxs-lookup"><span data-stu-id="9f904-288">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="9f904-289">例如，下列程式碼會實作用於F#核心程式庫中的 `Array.contains` 函式：</span><span class="sxs-lookup"><span data-stu-id="9f904-289">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

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

<span data-ttu-id="9f904-290">多次呼叫此函式並不會變更基礎陣列，也不需要維護任何使用它的可變狀態。</span><span class="sxs-lookup"><span data-stu-id="9f904-290">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="9f904-291">它參考上透明，即使其中幾乎每一行程式碼都使用變化。</span><span class="sxs-lookup"><span data-stu-id="9f904-291">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="9f904-292">考慮在類別中封裝可變數據</span><span class="sxs-lookup"><span data-stu-id="9f904-292">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="9f904-293">先前的範例使用單一函式來封裝使用可變動資料的作業。</span><span class="sxs-lookup"><span data-stu-id="9f904-293">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="9f904-294">對於更複雜的資料集，這不一定是足夠的。</span><span class="sxs-lookup"><span data-stu-id="9f904-294">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="9f904-295">請考慮下列函數集：</span><span class="sxs-lookup"><span data-stu-id="9f904-295">Consider the following sets of functions:</span></span>

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

<span data-ttu-id="9f904-296">這段程式碼的效能良好，但它會公開由呼叫端負責維護的以變化為基礎的資料結構。</span><span class="sxs-lookup"><span data-stu-id="9f904-296">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="9f904-297">這可以包裝在類別內，而且沒有可變更的基礎成員：</span><span class="sxs-lookup"><span data-stu-id="9f904-297">This can be wrapped inside of a class with no underlying members that can change:</span></span>

```fsharp
open System.Collections.Generic

/// The results of computing the LALR(1) closure of an LR(0) kernel
type Closure1Table() =
    let t = Dictionary<Item0, HashSet<TerminalIndex>>()

    member __.Add(key, value) =
        if not (t.ContainsKey(key)) then
            t.Add(key, value)
        else
            t.[key] <- value

    member __.Count = t.Count

    member __.Contains(key, value) =
        match t.TryGetValue(key) with
        | (true, v) -> v.Equals(value)
        | (false, _) -> false
```

<span data-ttu-id="9f904-298">`Closure1Table` 封裝基礎的變動式資料結構，因此不會強制呼叫端維護基礎資料結構。</span><span class="sxs-lookup"><span data-stu-id="9f904-298">`Closure1Table` encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="9f904-299">類別是一種強大的方式，可封裝以變化為基礎的資料和常式，而不會向呼叫端公開細節。</span><span class="sxs-lookup"><span data-stu-id="9f904-299">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="9f904-300">偏好 `let mutable` 參考資料格</span><span class="sxs-lookup"><span data-stu-id="9f904-300">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="9f904-301">參考儲存格是一種方式，代表值的參考，而不是值本身。</span><span class="sxs-lookup"><span data-stu-id="9f904-301">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="9f904-302">雖然它們可以用於效能關鍵程式碼，但通常不建議使用。</span><span class="sxs-lookup"><span data-stu-id="9f904-302">Although they can be used for performance-critical code, they are generally not recommended.</span></span> <span data-ttu-id="9f904-303">參考下列範例：</span><span class="sxs-lookup"><span data-stu-id="9f904-303">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="9f904-304">使用參考儲存格現在「干擾」所有後續的程式碼，都必須對基礎資料進行取值和重新參考。</span><span class="sxs-lookup"><span data-stu-id="9f904-304">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="9f904-305">相反地，請考慮 `let mutable`：</span><span class="sxs-lookup"><span data-stu-id="9f904-305">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="9f904-306">除了 lambda 運算式中間的單一變化點外，其他所有觸及 `acc` 的程式碼，都可以用與一般 `let`系結不可變值的用法不同的方式來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="9f904-306">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="9f904-307">這可讓您更輕鬆地隨著時間變更。</span><span class="sxs-lookup"><span data-stu-id="9f904-307">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="9f904-308">物件程式設計</span><span class="sxs-lookup"><span data-stu-id="9f904-308">Object programming</span></span>

<span data-ttu-id="9f904-309">F#具有物件和麵向物件（OO）概念的完整支援。</span><span class="sxs-lookup"><span data-stu-id="9f904-309">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="9f904-310">雖然許多 OO 概念都非常強大且實用，但並非全部都適合使用。</span><span class="sxs-lookup"><span data-stu-id="9f904-310">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="9f904-311">下列清單提供有關在高階的 OO 功能類別的指引。</span><span class="sxs-lookup"><span data-stu-id="9f904-311">The following lists offer guidance on categories of OO features at a high level.</span></span>

<span data-ttu-id="9f904-312">**在許多情況下，請考慮使用這些功能：**</span><span class="sxs-lookup"><span data-stu-id="9f904-312">**Consider using these features in many situations:**</span></span>

* <span data-ttu-id="9f904-313">點標記法（`x.Length`）</span><span class="sxs-lookup"><span data-stu-id="9f904-313">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="9f904-314">實例成員</span><span class="sxs-lookup"><span data-stu-id="9f904-314">Instance members</span></span>
* <span data-ttu-id="9f904-315">隱含的函式</span><span class="sxs-lookup"><span data-stu-id="9f904-315">Implicit constructors</span></span>
* <span data-ttu-id="9f904-316">靜態成員</span><span class="sxs-lookup"><span data-stu-id="9f904-316">Static members</span></span>
* <span data-ttu-id="9f904-317">索引子標記法（`arr.[x]`）</span><span class="sxs-lookup"><span data-stu-id="9f904-317">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="9f904-318">命名和選擇性引數</span><span class="sxs-lookup"><span data-stu-id="9f904-318">Named and Optional arguments</span></span>
* <span data-ttu-id="9f904-319">介面和介面的實現</span><span class="sxs-lookup"><span data-stu-id="9f904-319">Interfaces and interface implementations</span></span>

<span data-ttu-id="9f904-320">**請先不要觸達這些功能，但當它們很方便解決問題時，請謹慎套用：**</span><span class="sxs-lookup"><span data-stu-id="9f904-320">**Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:**</span></span>

* <span data-ttu-id="9f904-321">方法多載</span><span class="sxs-lookup"><span data-stu-id="9f904-321">Method overloading</span></span>
* <span data-ttu-id="9f904-322">封裝的可變數據</span><span class="sxs-lookup"><span data-stu-id="9f904-322">Encapsulated mutable data</span></span>
* <span data-ttu-id="9f904-323">類型的運算子</span><span class="sxs-lookup"><span data-stu-id="9f904-323">Operators on types</span></span>
* <span data-ttu-id="9f904-324">自動屬性</span><span class="sxs-lookup"><span data-stu-id="9f904-324">Auto properties</span></span>
* <span data-ttu-id="9f904-325">執行 `IDisposable` 和 `IEnumerable`</span><span class="sxs-lookup"><span data-stu-id="9f904-325">Implementing `IDisposable` and `IEnumerable`</span></span>
* <span data-ttu-id="9f904-326">類型延伸模組</span><span class="sxs-lookup"><span data-stu-id="9f904-326">Type extensions</span></span>
* <span data-ttu-id="9f904-327">「事件」</span><span class="sxs-lookup"><span data-stu-id="9f904-327">Events</span></span>
* <span data-ttu-id="9f904-328">結構</span><span class="sxs-lookup"><span data-stu-id="9f904-328">Structs</span></span>
* <span data-ttu-id="9f904-329">委派</span><span class="sxs-lookup"><span data-stu-id="9f904-329">Delegates</span></span>
* <span data-ttu-id="9f904-330">列舉</span><span class="sxs-lookup"><span data-stu-id="9f904-330">Enums</span></span>

<span data-ttu-id="9f904-331">**除非您必須使用這些功能，否則通常會予以避免：**</span><span class="sxs-lookup"><span data-stu-id="9f904-331">**Generally avoid these features unless you must use them:**</span></span>

* <span data-ttu-id="9f904-332">繼承型型別階層和實作為繼承</span><span class="sxs-lookup"><span data-stu-id="9f904-332">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="9f904-333">Null 和 `Unchecked.defaultof<_>`</span><span class="sxs-lookup"><span data-stu-id="9f904-333">Nulls and `Unchecked.defaultof<_>`</span></span>

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="9f904-334">偏好透過繼承撰寫</span><span class="sxs-lookup"><span data-stu-id="9f904-334">Prefer composition over inheritance</span></span>

<span data-ttu-id="9f904-335">透過[繼承進行撰寫](https://en.wikipedia.org/wiki/Composition_over_inheritance)，是良好F#程式碼可以遵守的長期用法。</span><span class="sxs-lookup"><span data-stu-id="9f904-335">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="9f904-336">基本原則是，您不應該公開基類，並強制呼叫端從該基類繼承來取得功能。</span><span class="sxs-lookup"><span data-stu-id="9f904-336">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="9f904-337">如果您不需要類別，請使用物件運算式來執行介面</span><span class="sxs-lookup"><span data-stu-id="9f904-337">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="9f904-338">[物件運算式](../language-reference/object-expressions.md)可讓您即時執行介面，將實的介面系結至值，而不需要在類別內執行此動作。</span><span class="sxs-lookup"><span data-stu-id="9f904-338">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="9f904-339">這很方便，特別是當您_只_需要執行介面，而不需要完整類別時。</span><span class="sxs-lookup"><span data-stu-id="9f904-339">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="9f904-340">例如，下列程式碼會在[Ionide](http://ionide.io/)中執行，以提供程式碼修正動作（若您已新增不具有 `open` 語句的符號）：</span><span class="sxs-lookup"><span data-stu-id="9f904-340">For example, here is the code that is run in [Ionide](http://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

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

<span data-ttu-id="9f904-341">因為與 Visual Studio Code API 互動時不需要類別，所以物件運算式是適用于此的理想工具。</span><span class="sxs-lookup"><span data-stu-id="9f904-341">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="9f904-342">當您想要以臨機操作方式將具有測試常式的介面 stub 時，它們也非常適合進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="9f904-342">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="consider-type-abbreviations-to-shorten-signatures"></a><span data-ttu-id="9f904-343">請考慮輸入縮寫來縮短簽章</span><span class="sxs-lookup"><span data-stu-id="9f904-343">Consider Type Abbreviations to shorten signatures</span></span>

<span data-ttu-id="9f904-344">[類型縮寫](../language-reference/type-abbreviations.md)是將標籤指派給另一種類型（例如，函式簽章或更複雜的類型）的便利方式。</span><span class="sxs-lookup"><span data-stu-id="9f904-344">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="9f904-345">例如，下列別名會將標籤指派給使用[CNTK](https://docs.microsoft.com/cognitive-toolkit/)（深度學習程式庫）定義計算所需的內容：</span><span class="sxs-lookup"><span data-stu-id="9f904-345">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](https://docs.microsoft.com/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="9f904-346">`Computation` 名稱是一個方便的方式，可表示任何符合它所別名之簽章的函式。</span><span class="sxs-lookup"><span data-stu-id="9f904-346">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="9f904-347">使用這類的類型縮寫十分方便，並允許更簡潔的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9f904-347">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="9f904-348">避免使用類型縮寫來代表您的網域</span><span class="sxs-lookup"><span data-stu-id="9f904-348">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="9f904-349">雖然類型縮寫對於提供名稱給函式簽章很方便，但在縮寫其他類型時可能會造成混淆。</span><span class="sxs-lookup"><span data-stu-id="9f904-349">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="9f904-350">請考慮下列縮寫：</span><span class="sxs-lookup"><span data-stu-id="9f904-350">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="9f904-351">這可能會讓您以多種方式混淆：</span><span class="sxs-lookup"><span data-stu-id="9f904-351">This can be confusing in multiple ways:</span></span>

* <span data-ttu-id="9f904-352">`BufferSize` 不是抽象概念;它只是一個整數的另一個名稱。</span><span class="sxs-lookup"><span data-stu-id="9f904-352">`BufferSize` is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="9f904-353">如果 `BufferSize` 在公用 API 中公開，很容易被誤解為表示不只是 `int`。</span><span class="sxs-lookup"><span data-stu-id="9f904-353">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="9f904-354">一般來說，網欄位型別有多個屬性，而且不是基本型別，例如 `int`。</span><span class="sxs-lookup"><span data-stu-id="9f904-354">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="9f904-355">此縮寫違反該假設。</span><span class="sxs-lookup"><span data-stu-id="9f904-355">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="9f904-356">`BufferSize` 的大小寫（PascalCase）表示此類型包含更多資料。</span><span class="sxs-lookup"><span data-stu-id="9f904-356">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="9f904-357">相較于將具名引數提供給函式，此別名並不提供更清楚的清晰度。</span><span class="sxs-lookup"><span data-stu-id="9f904-357">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="9f904-358">縮寫不會在編譯的 IL 中進行資訊清單;這只是一個整數，而此別名是編譯時間結構。</span><span class="sxs-lookup"><span data-stu-id="9f904-358">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

<span data-ttu-id="9f904-359">總而言之，類型縮寫的缺陷是它們**不**是縮寫的類型的抽象概念。</span><span class="sxs-lookup"><span data-stu-id="9f904-359">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="9f904-360">在上一個範例中，`BufferSize` 只是在幕後的 `int`，沒有額外的資料，也沒有任何來自型別系統的好處，除了 `int` 已經有的功能以外。</span><span class="sxs-lookup"><span data-stu-id="9f904-360">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>

<span data-ttu-id="9f904-361">使用類型縮寫來表示網域的替代方法是使用單一案例的區分等位。</span><span class="sxs-lookup"><span data-stu-id="9f904-361">An alternative approach to using type abbreviations to represent a domain is to use single-case discriminated unions.</span></span> <span data-ttu-id="9f904-362">先前的範例可以模型化，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9f904-362">The previous sample can be modeled as follows:</span></span>

```fsharp
type BufferSize = BufferSize of int
```

<span data-ttu-id="9f904-363">如果您撰寫的程式碼是以 `BufferSize` 及其基礎值來運作，您需要建立一個，而不是傳入任何任意整數：</span><span class="sxs-lookup"><span data-stu-id="9f904-363">If you write code that operates in terms of `BufferSize` and its underlying value, you need to construct one rather than pass in any arbitrary integer:</span></span>

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

<span data-ttu-id="9f904-364">這可減少錯誤地將任意整數傳遞至 `send` 函式的可能性，因為呼叫端必須先建立 `BufferSize` 型別來包裝值，然後再呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="9f904-364">This reduces the likelihood of mistakenly passing an arbitrary integer into the `send` function, because the caller must construct a `BufferSize` type to wrap a value before calling the function.</span></span>
