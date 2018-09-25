---
title: 'F # 編碼慣例'
description: '撰寫 F # 程式碼時，了解一般的指導方針和慣例。'
ms.date: 05/14/2018
ms.openlocfilehash: b9afd1fbfbd9d8e04d9bfaa07615de045b7e05fe
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47078466"
---
# <a name="f-coding-conventions"></a><span data-ttu-id="7c9b0-103">F # 編碼慣例</span><span class="sxs-lookup"><span data-stu-id="7c9b0-103">F# coding conventions</span></span>

<span data-ttu-id="7c9b0-104">下列慣例會使用大型的 F # 的體驗編寫程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="7c9b0-105">[良好的 F # 程式碼的五個原則](index.md#five-principles-of-good-f-code)是每個建議的基礎。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="7c9b0-106">它們與相關[F # 元件的設計指導方針](component-design-guidelines.md)，但是也適用於任何 F # 程式碼，不只是元件，例如程式庫。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="7c9b0-107">組織程式碼</span><span class="sxs-lookup"><span data-stu-id="7c9b0-107">Organizing code</span></span>

<span data-ttu-id="7c9b0-108">F # 功能來組織程式碼的兩種主要方式： 模組與命名空間。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="7c9b0-109">這些類似，但有下列差異：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="7c9b0-110">命名空間會編譯為.NET 命名空間。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="7c9b0-111">模組會編譯為靜態類別。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="7c9b0-112">命名空間永遠是最上層。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-112">Namespaces are always top level.</span></span> <span data-ttu-id="7c9b0-113">模組可以是最上層和其他模組內的巢狀。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="7c9b0-114">命名空間可以跨多個檔案。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="7c9b0-115">模組不行。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-115">Modules cannot.</span></span>
* <span data-ttu-id="7c9b0-116">模組可以使用裝飾`[<RequireQualifiedAccess>]`和`[<AutoOpen>]`。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="7c9b0-117">下列指導方針將協助您使用這些來組織您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="7c9b0-118">想在最上層的命名空間</span><span class="sxs-lookup"><span data-stu-id="7c9b0-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="7c9b0-119">對於任何可公開使用的程式碼，命名空間是優先高層級的模組。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="7c9b0-120">因為它們會編譯為.NET 命名空間，也就是從 C# 沒有問題可取用。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="7c9b0-121">使用最上層模組可能不會出現不同只從 F # 中，呼叫時，但 C# 取用者，呼叫端可能會感到驚訝需要限定`MyClass`與`MyCode`模組。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="7c9b0-122">請仔細套用 `[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="7c9b0-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="7c9b0-123">`[<AutoOpen>]`建構可以干擾的呼叫端，為範圍和項目來自何處的答案是"magic"。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="7c9b0-124">這通常不是一件好事。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-124">This is generally not a good thing.</span></span> <span data-ttu-id="7c9b0-125">此規則的例外狀況是 F # 核心程式庫本身 （雖然這項事實也是有點備受爭議的）。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="7c9b0-126">不過，它是為了方便起見，如果您希望組織分別從該公用 API 的公用 API 中的協助程式功能。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

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

<span data-ttu-id="7c9b0-127">可以讓您從函式的公用 API 完全不同的實作詳細資料，而不必完整限定的協助程式每次呼叫它。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="7c9b0-128">此外，公開擴充方法和命名空間層級的運算式產生器可以整齊地表示`[<AutoOpen>]`。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="7c9b0-129">使用`[<RequireQualifiedAccess>]`每當名稱可能會發生衝突，或是您認為它有助於提供可讀性</span><span class="sxs-lookup"><span data-stu-id="7c9b0-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="7c9b0-130">新增`[<RequireQualifiedAccess>]`模組的屬性表示模組可能未開啟，而且參考的模組項目需要明確限定存取。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="7c9b0-131">比方說，`Microsoft.FSharp.Collections.List`模組有這個屬性。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="7c9b0-132">當函式和模組中的值有可能會與其他模組中的名稱發生衝突的名稱，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="7c9b0-133">需要完整存取權可能會大幅增加的長期維護性和可演化性程式庫。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="7c9b0-134">排序`open`陳述式拓撲</span><span class="sxs-lookup"><span data-stu-id="7c9b0-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="7c9b0-135">在 F # 中，宣告的順序很重要，包括具有`open`陳述式。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="7c9b0-136">這是不同於 C# 中，其中的效果`using`和`using static`無關的檔案中的這些陳述式的順序。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="7c9b0-137">在 F # 中，開啟進入範圍內的項目可以遮蔽其他已經存在。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="7c9b0-138">這表示重新排列`open`陳述式無法變更程式碼的意義。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="7c9b0-139">如此一來，任何任意排序之所有`open`陳述式 （例如，文數字順序） 通常不建議，以免產生您所預期的不同行為。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is generally not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="7c9b0-140">相反地，我們建議您加以排序[拓撲](https://en.wikipedia.org/wiki/Topological_sorting); 也就是訂單您`open`陳述式中的順序_層_定義您的系統。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="7c9b0-141">英數字元的排序不同的拓撲圖層內也列入考量。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="7c9b0-142">例如，以下是 F # 編譯器服務公用 API 檔案的拓撲排序：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

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

<span data-ttu-id="7c9b0-143">請注意分行符號分隔拓撲的層級，與正在排序文數字順序之後每個圖層。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="7c9b0-144">這完全沒有不小心遮蔽值組織程式碼。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="7c9b0-145">使用類別來包含有副作用的值</span><span class="sxs-lookup"><span data-stu-id="7c9b0-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="7c9b0-146">很多時候初始化值，當有副作用，例如具現化的資料庫或其他遠端資源的內容。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="7c9b0-147">相當吸引人，初始化模組中的這類項目，並將它用於後續的函式：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

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

<span data-ttu-id="7c9b0-148">通常是個好主意的幾個原因：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="7c9b0-149">首先，應用程式設定都會被推送至程式碼基底`dep1`和`dep2`。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="7c9b0-150">這很難維護較大程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="7c9b0-151">第二個，以靜態方式初始化的資料不應該包含不具備執行緒安全，如果您的元件將本身使用多個執行緒的值。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="7c9b0-152">這顯然違反`dep3`。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="7c9b0-153">最後，模組的初始化會編譯成靜態的建構函式的整個編譯單元。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="7c9b0-154">如果在該模組中的 let 繫結值初始化，就會發生任何錯誤，它記錄成資訊清單`TypeInitializationException`，則快取的應用程式的整個存留期間。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="7c9b0-155">這很難診斷。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="7c9b0-156">通常是內部例外狀況，您可以嘗試理解，但如果沒有，則沒有的根本原因的任何告知。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="7c9b0-157">相反地，只要使用簡單的類別來保存相依性：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="7c9b0-158">這可啟用下列功能：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-158">This enables the following:</span></span>

1. <span data-ttu-id="7c9b0-159">將推送 API 本身以外任何相依的狀態。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="7c9b0-160">外部 API 時，可以立即進行設定。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="7c9b0-161">初始化相依的值中的錯誤不是可能會顯示為`TypeInitializationException`。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="7c9b0-162">現在您更輕鬆地測試 API。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="7c9b0-163">錯誤管理</span><span class="sxs-lookup"><span data-stu-id="7c9b0-163">Error management</span></span>

<span data-ttu-id="7c9b0-164">大型系統中的錯誤管理是一項複雜且細微精密的工作，而且有項目符號，確保您的系統在容錯和行為也沒有 silver。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="7c9b0-165">下列指導方針也應該提供指導方針中瀏覽此困難的空間。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="7c9b0-166">代表錯誤案例和您的網域內建函式的型別中不合法的狀態</span><span class="sxs-lookup"><span data-stu-id="7c9b0-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="7c9b0-167">具有[差別聯集](../language-reference/discriminated-unions.md)，F # 可讓您能夠代表您的型別系統中的錯誤的程式狀態。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="7c9b0-168">例如: </span><span class="sxs-lookup"><span data-stu-id="7c9b0-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="7c9b0-169">在此情況下，有三種已知的方式，從銀行帳戶提款金額可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="7c9b0-170">每個錯誤案例中會表示成的型別，並可以因此處理安全地在整個程式。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="7c9b0-171">一般情況下，如果您可以建立模型的不同方式有可以**失敗**在您的網域，然後錯誤處理程式碼不會再視為您除了一般程式流程必須處理的項目。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="7c9b0-172">它是只是一般程式流程的一部分，而且不被視為**卓越**。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="7c9b0-173">有這兩項主要優點：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="7c9b0-174">很容易維護一段時間，變更您的網域。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="7c9b0-175">錯誤的情況下會更容易進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="7c9b0-176">使用例外狀況，當類型不可以有錯誤</span><span class="sxs-lookup"><span data-stu-id="7c9b0-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="7c9b0-177">問題領域中，就可以表示並非所有的錯誤。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="7c9b0-178">這類錯誤會*卓越*性質，因此能夠提高，並在 F # 中攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="7c9b0-179">首先，建議您先閱讀[例外狀況的設計方針](../../standard/design-guidelines/exceptions.md)。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="7c9b0-180">這些也是適用於 F #。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-180">These are also applicable to F#.</span></span>

<span data-ttu-id="7c9b0-181">基於引發例外狀況的 F # 中可用的主要建構應該考慮以下列順序的喜好設定：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="7c9b0-182">功能</span><span class="sxs-lookup"><span data-stu-id="7c9b0-182">Function</span></span> | <span data-ttu-id="7c9b0-183">語法</span><span class="sxs-lookup"><span data-stu-id="7c9b0-183">Syntax</span></span> | <span data-ttu-id="7c9b0-184">用途</span><span class="sxs-lookup"><span data-stu-id="7c9b0-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="7c9b0-185">引發`System.ArgumentNullException`具有指定的引數名稱。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="7c9b0-186">引發`System.ArgumentException`使用指定的引數名稱和訊息。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="7c9b0-187">引發`System.InvalidOperationException`使用指定的訊息。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="7c9b0-188">擲回例外狀況的一般用途機制。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="7c9b0-189">引發`System.Exception`使用指定的訊息。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="7c9b0-190">引發`System.Exception`取決於在格式字串和其輸入的訊息。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="7c9b0-191">使用`nullArg`，`invalidArg`並`invalidOp`做為擲回機制`ArgumentNullException`，`ArgumentException`和`InvalidOperationException`適當的時候。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="7c9b0-192">`failwith`並`failwithf`函式通常應該避免因為它們會引發基底`Exception`輸入時，沒有特定的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="7c9b0-193">依照[例外狀況的設計方針](../../standard/design-guidelines/exceptions.md)，您想要時您可以引發其他特定的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="using-exception-handling-syntax"></a><span data-ttu-id="7c9b0-194">使用例外狀況處理語法</span><span class="sxs-lookup"><span data-stu-id="7c9b0-194">Using exception-handling syntax</span></span>

<span data-ttu-id="7c9b0-195">F # 支援例外狀況模式，透過`try...with`語法：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="7c9b0-196">重新調整功能，以執行例外狀況的模式比對時可能有點困難，如果您想要的程式碼保持乾淨。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="7c9b0-197">若要處理這其中一種方法是使用[作用中的模式](../language-reference/active-patterns.md)做為相關的例外狀況本身發生錯誤狀況的群組功能的方法。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="7c9b0-198">例如，您可能會使用的 API，當它擲回例外狀況，則是寶貴的資訊放在例外狀況中繼資料。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="7c9b0-199">解除包裝成為現用模式內擷取的例外狀況的主體中有用的值，並傳回值可以在某些情況下很有幫助。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="7c9b0-200">請勿使用單邊錯誤取代例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="7c9b0-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="7c9b0-201">例外狀況都被視為有點函式程式設計的 taboo。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="7c9b0-202">事實上，例外狀況會違反單純性，以便安全地將它們視為不相當的功能。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="7c9b0-203">不過，這會略過在實際程式碼必須執行位置，和該執行階段可能會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="7c9b0-204">一般情況下，撰寫程式碼大多是純和總計，以減少發生意外狀況都不假設。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="7c9b0-205">請務必考慮下列核心優勢/層面的例外狀況相對於其相關性和.NET 執行階段和跨語言生態系統中整體的適當性：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="7c9b0-206">它們包含詳細的診斷資訊，也就是很有幫助，當偵錯問題。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="7c9b0-207">也就是大家熟悉的執行階段和其他.NET 語言。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="7c9b0-208">他們可以縮減目前相較於超出其方法的程式碼重大的未定案*避免*藉由實作其語意的一些臨機操作為基礎的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="7c9b0-209">此第三個點很重要。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-209">This third point is critical.</span></span> <span data-ttu-id="7c9b0-210">重要的複雜作業，無法使用例外狀況可能會導致處理結構如下：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="7c9b0-211">這很容易導致易損壞的程式碼，例如模式比對"stringly 型別 」 的錯誤：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="7c9b0-212">此外，它很吸引人，適當地抑制在 「 簡單 」 的函式會傳回 「 好了 」 的型別所需的任何例外狀況：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="7c9b0-213">不幸的是，`tryReadAllText`無數個檔案在系統，可以發生的情況為基礎的多個例外狀況，以及這段程式碼會立即捨棄任何項目可能實際上出錯您環境中的資訊。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="7c9b0-214">如果您將此程式碼取代結果型別時，您會回到 「 stringly 型別 」 的錯誤訊息剖析：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

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

<span data-ttu-id="7c9b0-215">並將例外狀況物件本身放置在`Error`建構函式只會強制您正確地處理在呼叫站台，而不是函式中的例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="7c9b0-216">有效地執行此動作會建立檢查例外狀況，也就是都是聲名狼藉 unfun 作為 API 的呼叫者處理。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="7c9b0-217">理想的替代方法，上述範例是以攔截*特定*例外狀況，並傳回有意義的值，該例外狀況的內容中。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="7c9b0-218">如果您修改`tryReadAllText`函式，如下所示，`None`有更多的意義：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="7c9b0-219">而不是做為全部擷取，此函式會立即正確處理的情況時找不到檔案，並將該意義指派給傳回。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="7c9b0-220">不捨棄任何內容的資訊，或強制呼叫者處理可能不在該點在程式碼相關的案例時，此傳回值可以對應到此錯誤的情況下。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="7c9b0-221">類型，例如`Result<'Success, 'Error>`適用於基本作業不巢狀的方式，而 F # 選擇性型別非常適合做為項目無法傳回時，代表*東西*或*nothing*.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="7c9b0-222">它們不能取代例外狀況，不過，和不應嘗試將例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="7c9b0-223">相反地，它們應套用明智地址的例外狀況和錯誤管理原則的特定層面目標的方式。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="7c9b0-224">部分應用程式和無點的程式設計</span><span class="sxs-lookup"><span data-stu-id="7c9b0-224">Partial application and point-free programming</span></span>

<span data-ttu-id="7c9b0-225">F # 支援部分的應用程式，因此，程式的各種方式無端點的樣式。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="7c9b0-226">這可以是有幫助模組內的項目，實作的程式碼重複使用，但它通常不是要公開可公開 （expose） 的項目。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-226">This can be beneficial for code reuse within a module or the implementation of something, but it is generally not something to expose publicly.</span></span> <span data-ttu-id="7c9b0-227">一般情況下，無點的程式設計不本身，作為，而且可以加入重大的認知障礙不沉浸在樣式中的人員。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="7c9b0-228">請勿使用部分的應用程式及對公用 Api 中</span><span class="sxs-lookup"><span data-stu-id="7c9b0-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="7c9b0-229">有一些例外狀況，使用公用 Api 中的部分應用程式會造成混淆的取用者。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="7c9b0-230">通常`let`-F # 程式碼中的繫結的值是**值**，而非**函式值**。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="7c9b0-231">混合在一起，值和函式值可能會導致儲存少數幾行程式碼，但是也會處理一堆認知的額外負荷，尤其是這類結合運算子`>>`撰寫函式。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="7c9b0-232">考慮工具產生的影響無點的程式設計</span><span class="sxs-lookup"><span data-stu-id="7c9b0-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="7c9b0-233">局部調用函式不會標示其引數。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="7c9b0-234">這會有影響的工具。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-234">This has tooling implications.</span></span> <span data-ttu-id="7c9b0-235">請考慮下列兩個函式：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="7c9b0-236">兩者都是有效的函式，但`funcWithApplication`是局部調用的函式。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="7c9b0-237">當您停留在編輯器中其型別時，您會看到這個：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="7c9b0-238">在呼叫位置，Visual Studio 這類的工具中的工具提示不會讓您有意義的資訊，內幕消息`string`和`int`實際代表輸入的類型。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="7c9b0-239">如果您遇到像點免程式碼`funcWithApplication`可公開使用，建議您執行完整的 η 擴充，以便工具可以挑選上有意義的名稱，引數。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="7c9b0-240">此外，偵錯點免程式碼可能相當困難，不可能。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="7c9b0-241">偵錯工具需要依賴繫結至名稱的值 (例如`let`繫結)，因此您可以檢查執行的中間值中途。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="7c9b0-242">當您的程式碼不有任何值，以檢查時，任何偵錯。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="7c9b0-243">在未來，偵錯工具可能會有所演進合成根據先前執行的路徑，這些值，但不是個不錯的主意 hedge 了上*潛在*偵錯功能。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="7c9b0-244">請考慮減少內部重複使用在這項技術的部分應用程式</span><span class="sxs-lookup"><span data-stu-id="7c9b0-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="7c9b0-245">相較於上一點，部分應用程式會是絕佳的工具，以降低應用程式或 API 的更深入的內部資訊內的重複使用。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="7c9b0-246">它可以是單元測試更複雜的 Api，其中未定案通常是太痛苦了處理的實作很有幫助。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="7c9b0-247">例如，下列的程式碼示範如何完成哪些最模擬架構讓您無須在這類架構的外部相依性，而不必了解相關 bespoke API。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="7c9b0-248">例如，請考慮下列解決方案拓撲：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

<span data-ttu-id="7c9b0-249">`ImplementationLogic.fsproj` 可能會公開程式碼，像是所示：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-249">`ImplementationLogic.fsproj` might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="7c9b0-250">單元測試`Transactions.doTransaction`在`ImplementationLogic.Tests.fspoj`很簡單：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fspoj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="7c9b0-251">部分套用`doTransaction`使用模擬的內容物件可讓您所有的單元測試中呼叫函式，而不必每次建構的模擬 （mock） 的內容：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

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

<span data-ttu-id="7c9b0-252">這項技術應該不通用於您整個程式碼基底，但是它是一個好的方法，以減少重複使用複雜的內部項目和單元測試這些內部項目。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="7c9b0-253">存取控制</span><span class="sxs-lookup"><span data-stu-id="7c9b0-253">Access control</span></span>

<span data-ttu-id="7c9b0-254">F # 提供多個選項[存取控制](../language-reference/access-control.md)、 繼承自.NET 執行階段中可用。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="7c9b0-255">這些不是只用於類型-您也可以使用它們的函式。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="7c9b0-256">偏好非`public`類型和成員，直到您需要它們來公開取用。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="7c9b0-257">這樣也可以降低至哪些取用者幾</span><span class="sxs-lookup"><span data-stu-id="7c9b0-257">This also minimizes what consumers couple to</span></span>
* <span data-ttu-id="7c9b0-258">致力於讓您將所有的協助程式功能`private`。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="7c9b0-259">請考慮使用`[<AutoOpen>]`helper 函式，如果它們變成許多私用模組上。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="7c9b0-260">型別推斷和泛型</span><span class="sxs-lookup"><span data-stu-id="7c9b0-260">Type inference and generics</span></span>

<span data-ttu-id="7c9b0-261">型別推斷可讓您輸入的未定案很多。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="7c9b0-262">在 F # 編譯器自動產生可協助您撰寫更一般的程式碼幾乎不必額外費心與您的組件上。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="7c9b0-263">不過，這些功能不普遍良好。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="7c9b0-264">請考慮使用明確的類型，在公用 Api 標記引數名稱，並不依賴類型推斷此。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="7c9b0-265">原因在於**您**應該控制您的 API，不是編譯器的形狀。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="7c9b0-266">雖然編譯器能夠推斷類型，為您在正常作業，就可以有您的 API 變更的形狀，如果它會依賴內部項目已變更類型。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="7c9b0-267">這可能是您要的結果，但它幾乎肯定會導致下游取用者再也不必處理重大 API 變更。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="7c9b0-268">相反地，如果您明確地控制您的公用 API 的形狀，您可以控制這些重大變更。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="7c9b0-269">以 DDD 術語來說，這可以視為防損毀層。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="7c9b0-270">請考慮您的泛型引數來提供有意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="7c9b0-271">除非您要撰寫真正泛型程式碼，並非專屬於特定的網域，有意義的名稱可以幫助其他程式設計人員了解他們正在處理中的網域。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="7c9b0-272">例如，名為的型別參數`'Document`互動與文件的內容中資料庫讓您更清楚，一般文件類型可接受函式或您正在使用的成員。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="7c9b0-273">請考慮使用 PascalCase 的泛型型別參數命名。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="7c9b0-274">這是一般的方法做事在.NET 中，所以建議您使用 PascalCase 而不是為 snake_case 加上或 camelCase。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="7c9b0-275">最後，自動一般化並不一定對象是剛接觸 F # 或大型的程式碼基底的人是一大福音。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="7c9b0-276">在中使用的一般元件沒有額外的認知。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="7c9b0-277">此外，如果自動一般化的函式不適用於採用不同輸入類型 (let 單獨如果它們要這麼做)，則沒有任何實質就是在該時間點的泛用的好處。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="7c9b0-278">請務必考慮您要撰寫的程式碼會實際從泛型中獲益。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="7c9b0-279">效能</span><span class="sxs-lookup"><span data-stu-id="7c9b0-279">Performance</span></span>

<span data-ttu-id="7c9b0-280">F # 值是根據預設，可讓您避免某些 bug （特別是那些包含並行和平行處理原則） 的類別不可變的。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-280">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="7c9b0-281">不過，在某些情況下，為了達到最佳的 （或甚至是合理的） 的執行時間或記憶體配置的高效率工作的範圍可能最適合實作使用狀態的就地變化。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-281">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="7c9b0-282">這可自由選擇是否搭配 F # 中`mutable`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-282">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="7c9b0-283">不過，使用`mutable`F # 中可能會覺得相悖功能的單純性。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-283">However, use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="7c9b0-284">這是正常的如果您調整至單純性的期望[參考透明度](https://en.wikipedia.org/wiki/Referential_transparency)。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-284">This is fine, if you adjust expectations from purity to [referential transparency](https://en.wikipedia.org/wiki/Referential_transparency).</span></span> <span data-ttu-id="7c9b0-285">參考透明度-不純正性-撰寫 F # 函式時的最終目的。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-285">Referential transparency - not purity - is the end goal when writing F# functions.</span></span> <span data-ttu-id="7c9b0-286">這可讓您在效能關鍵的程式碼的變化型實作覆寫功能的介面。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-286">This allows you to write a functional interface over a mutation-based implementation for performance critical code.</span></span>

### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="7c9b0-287">將可變動的程式碼包裝在不可變的介面</span><span class="sxs-lookup"><span data-stu-id="7c9b0-287">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="7c9b0-288">為目標的參考透明度，請務必撰寫程式碼不會公開可變動的 underbelly 效能關鍵的函式。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-288">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="7c9b0-289">例如，下列程式碼會實作`Array.contains`F # 核心程式庫中的函式：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-289">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

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

<span data-ttu-id="7c9b0-290">多次呼叫此函式不會變更基礎的陣列，也不會要求您維護中使用它的任何可變動狀態。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-290">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="7c9b0-291">即使幾乎每一行程式碼，在其中使用變動時，它是參考透明。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-291">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="7c9b0-292">請考慮將封裝在類別中可變動的資料</span><span class="sxs-lookup"><span data-stu-id="7c9b0-292">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="7c9b0-293">前面的範例會使用單一函式，來封裝使用可變動的資料作業。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-293">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="7c9b0-294">這不一定能夠以更複雜的資料集。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-294">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="7c9b0-295">請考慮下列會設定函式：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-295">Consider the following sets of functions:</span></span>

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

<span data-ttu-id="7c9b0-296">此程式碼是高效能，但它會公開的呼叫端會負責維護的變動為基礎的資料結構。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-296">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="7c9b0-297">這可以包裝在不含基礎的成員可以變更的類別內：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-297">This can be wrapped inside of a class with no underlying members that can change:</span></span>

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

<span data-ttu-id="7c9b0-298">`Closure1Table` 封裝基礎的變動為基礎的資料結構，因此未強制執行以維護基礎資料結構的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-298">`Closure1Table` encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="7c9b0-299">類別是強大的方式來封裝資料和而不會公開給呼叫者的詳細資料是以變動為基礎的常式。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-299">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="7c9b0-300">偏好`let mutable`來參考儲存格</span><span class="sxs-lookup"><span data-stu-id="7c9b0-300">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="7c9b0-301">參考儲存格可代表值，而不是值本身的參考。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-301">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="7c9b0-302">雖然它們可以用於效能關鍵的程式碼，但是它們通常不建議。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-302">Although they can be used for performance-critical code, they are generally not recommended.</span></span> <span data-ttu-id="7c9b0-303">參考下列範例：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-303">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="7c9b0-304">使用參考儲存格現在 「 污染 」 具有來取值 （dereference），並重新參考基礎資料所有後續的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-304">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="7c9b0-305">請改為考慮`let mutable`:</span><span class="sxs-lookup"><span data-stu-id="7c9b0-305">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="7c9b0-306">Lambda 運算式的中間的變動的單一點，除了所有其他程式碼，接觸`acc`可以這樣做並無一般需要使用不同的方式`let`-繫結不可變的值。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-306">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="7c9b0-307">這會讓您更輕鬆地隨著時間而變更。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-307">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="7c9b0-308">物件的程式設計</span><span class="sxs-lookup"><span data-stu-id="7c9b0-308">Object programming</span></span>

<span data-ttu-id="7c9b0-309">F # 提供物件和物件導向 (OO) 概念的完整支援。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-309">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="7c9b0-310">雖然許多 OO 概念是功能強大且實用，但並非全部都適合使用。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-310">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="7c9b0-311">下列清單提供高層級的 OO 功能的類別上的指導方針。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-311">The following lists offer guidance on categories of OO features at a high level.</span></span>

<span data-ttu-id="7c9b0-312">**請考慮在許多情況下使用這些功能：**</span><span class="sxs-lookup"><span data-stu-id="7c9b0-312">**Consider using these features in many situations:**</span></span>

* <span data-ttu-id="7c9b0-313">點標記法 (`x.Length`)</span><span class="sxs-lookup"><span data-stu-id="7c9b0-313">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="7c9b0-314">執行個體成員</span><span class="sxs-lookup"><span data-stu-id="7c9b0-314">Instance members</span></span>
* <span data-ttu-id="7c9b0-315">隱含的建構函式</span><span class="sxs-lookup"><span data-stu-id="7c9b0-315">Implicit constructors</span></span>
* <span data-ttu-id="7c9b0-316">靜態成員</span><span class="sxs-lookup"><span data-stu-id="7c9b0-316">Static members</span></span>
* <span data-ttu-id="7c9b0-317">索引子標記法 (`arr.[x]`)</span><span class="sxs-lookup"><span data-stu-id="7c9b0-317">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="7c9b0-318">具名和選擇性引數</span><span class="sxs-lookup"><span data-stu-id="7c9b0-318">Named and Optional arguments</span></span>
* <span data-ttu-id="7c9b0-319">介面和介面實作</span><span class="sxs-lookup"><span data-stu-id="7c9b0-319">Interfaces and interface implementations</span></span>

<span data-ttu-id="7c9b0-320">**不會送達這些功能的第一次，但請謹慎套用它們何時可方便地解決問題：**</span><span class="sxs-lookup"><span data-stu-id="7c9b0-320">**Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:**</span></span>

* <span data-ttu-id="7c9b0-321">方法多載</span><span class="sxs-lookup"><span data-stu-id="7c9b0-321">Method overloading</span></span>
* <span data-ttu-id="7c9b0-322">封裝可變動的資料</span><span class="sxs-lookup"><span data-stu-id="7c9b0-322">Encapsulated mutable data</span></span>
* <span data-ttu-id="7c9b0-323">類型的運算子</span><span class="sxs-lookup"><span data-stu-id="7c9b0-323">Operators on types</span></span>
* <span data-ttu-id="7c9b0-324">Auto 屬性</span><span class="sxs-lookup"><span data-stu-id="7c9b0-324">Auto properties</span></span>
* <span data-ttu-id="7c9b0-325">實作`IDisposable`和 `IEnumerable`</span><span class="sxs-lookup"><span data-stu-id="7c9b0-325">Implementing `IDisposable` and `IEnumerable`</span></span>
* <span data-ttu-id="7c9b0-326">類型擴充功能</span><span class="sxs-lookup"><span data-stu-id="7c9b0-326">Type extensions</span></span>
* <span data-ttu-id="7c9b0-327">事件</span><span class="sxs-lookup"><span data-stu-id="7c9b0-327">Events</span></span>
* <span data-ttu-id="7c9b0-328">結構</span><span class="sxs-lookup"><span data-stu-id="7c9b0-328">Structs</span></span>
* <span data-ttu-id="7c9b0-329">委派</span><span class="sxs-lookup"><span data-stu-id="7c9b0-329">Delegates</span></span>
* <span data-ttu-id="7c9b0-330">列舉</span><span class="sxs-lookup"><span data-stu-id="7c9b0-330">Enums</span></span>

<span data-ttu-id="7c9b0-331">**除非您必須使用它們，通常可以避免這些功能：**</span><span class="sxs-lookup"><span data-stu-id="7c9b0-331">**Generally avoid these features unless you must use them:**</span></span>

* <span data-ttu-id="7c9b0-332">繼承為基礎的型別階層架構和實作繼承</span><span class="sxs-lookup"><span data-stu-id="7c9b0-332">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="7c9b0-333">Null 和 `Unchecked.defaultof<_>`</span><span class="sxs-lookup"><span data-stu-id="7c9b0-333">Nulls and `Unchecked.defaultof<_>`</span></span>

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="7c9b0-334">偏好撰寫比繼承</span><span class="sxs-lookup"><span data-stu-id="7c9b0-334">Prefer composition over inheritance</span></span>

<span data-ttu-id="7c9b0-335">[撰寫比繼承](https://en.wikipedia.org/wiki/Composition_over_inheritance)是長久以來的慣用句，良好的 F # 程式碼可以符合。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-335">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="7c9b0-336">基本原則是，您不應該公開 （expose） 的基底類別並強制繼承自該基底類別，以取得功能的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-336">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="7c9b0-337">使用物件運算式實作介面，如果您不需要類別</span><span class="sxs-lookup"><span data-stu-id="7c9b0-337">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="7c9b0-338">[物件運算式](../language-reference/object-expressions.md)可讓您實作介面即時，繫結實作的介面值，而不需要這麼做在類別內。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-338">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="7c9b0-339">這是很方便，尤其是如果您_只_需要實作介面並不需要完整的類別。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-339">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="7c9b0-340">例如，以下是執行中的程式碼[Ionide](http://ionide.io/)提供的程式碼修正動作，如果您已新增一個符號，您還沒有`open`陳述式：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-340">For example, here is the code that is run in [Ionide](http://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

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

<span data-ttu-id="7c9b0-341">因為類別不需要與 Visual Studio 程式碼 API 互動時，物件運算式都是這樣的理想工具。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-341">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="7c9b0-342">它們也是單元測試，當您想要去除測試常式的介面，以臨機操作方式的重要依據。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-342">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="type-abbreviations"></a><span data-ttu-id="7c9b0-343">類型縮寫</span><span class="sxs-lookup"><span data-stu-id="7c9b0-343">Type Abbreviations</span></span>

<span data-ttu-id="7c9b0-344">[類型縮寫](../language-reference/type-abbreviations.md)是便利的方式來將標籤指派給另一個類型，例如函式簽章或更複雜的類型。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-344">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="7c9b0-345">例如，下列別名會將標籤指派給需要哪些技能來定義與計算[CNTK](https://www.microsoft.com/en-us/cognitive-toolkit/)、 深入學習程式庫：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-345">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](https://www.microsoft.com/en-us/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="7c9b0-346">`Computation`名稱是便利的方式來表示任何符合函式，它是別名的簽章。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-346">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="7c9b0-347">就像這樣使用類型縮寫很方便，而且允許更簡潔的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-347">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="7c9b0-348">請避免使用類型縮寫來代表您的網域</span><span class="sxs-lookup"><span data-stu-id="7c9b0-348">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="7c9b0-349">雖然類型縮寫是方便命名函式簽章，但它們可能會造成混淆的情況，當縮寫其他類型。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-349">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="7c9b0-350">請考慮這個縮寫：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-350">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="7c9b0-351">這可能是令人困惑，以多種方式：</span><span class="sxs-lookup"><span data-stu-id="7c9b0-351">This can be confusing in multiple ways:</span></span>

* <span data-ttu-id="7c9b0-352">`BufferSize` 不是抽象概念;這是整數的只是另一個名稱。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-352">`BufferSize` is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="7c9b0-353">如果`BufferSize`公開在公用 API 中，它可以輕鬆地被錯誤解譯不只是表示`int`。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-353">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="7c9b0-354">一般而言，網域類型有多個屬性，而不是基本型別，例如`int`。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-354">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="7c9b0-355">這個縮寫違反的假設。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-355">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="7c9b0-356">大小寫的`BufferSize`(PascalCase) 表示這個型別含有更多資料。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-356">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="7c9b0-357">此別名並未提供相較於提供具名引數的函式的更的清楚。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-357">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="7c9b0-358">已編譯的 IL; 的縮寫將沒有資訊清單它只是一個整數，與此別名是編譯時期建構。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-358">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) =
        ...
```

<span data-ttu-id="7c9b0-359">在 [摘要] 類型縮寫就是它們均**不**它們縮寫類型的抽象概念。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-359">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="7c9b0-360">在上述範例中，`BufferSize`就`int`實際上與任何其他的資料或從項目以外的型別系統的任何權益`int`已經有。</span><span class="sxs-lookup"><span data-stu-id="7c9b0-360">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>
