---
title: 'F # 編碼慣例'
description: '撰寫 F # 程式碼時，了解一般方針和慣例。'
ms.date: 05/14/2018
ms.openlocfilehash: f3d16f735ddc1901aeaa5ebb39e2fa2b70a3d836
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457978"
---
# <a name="f-coding-conventions"></a>F # 編碼慣例

下列慣例會構成從經驗使用大型的 F # 程式碼基底。 [良好的 F # 程式碼的五個原則](index.md#five-principles-of-good-f-code)每個建議的基礎。 它們與相關[F # 元件的設計指導方針](component-design-guidelines.md)，但也適用於任何 F # 程式碼，不只是元件，例如文件庫。

## <a name="organizing-code"></a>組織程式碼

F # 的功能來組織程式碼的兩個主要方式： 模組和命名空間。 這些非常類似，但是沒有下列差異：

* 命名空間會編譯為.NET 命名空間。 模組會編譯成靜態類別。
* 命名空間永遠是最上層。 模組可以是最上層和其他模組內的巢狀。
* 命名空間可以跨越多個檔案。 模組無法。
* 模組可以使用裝飾`[<RequireQualifiedAccess>]`和`[<AutoOpen>]`。

下列指導方針將協助您使用這些來組織您的程式碼。

### <a name="prefer-namespaces-at-the-top-level"></a>偏好的最上層命名空間

任何公開您可以使用程式碼中，命名空間都優先最上層的模組。 是，因為它們會編譯為.NET 命名空間，您可以從使用 C# 與任何問題。

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

使用最上層模組可能不會出現不同時只會從 F # 中，呼叫，但 C# 取用者，呼叫端可能而感到驚訝需限定`MyClass`與`MyCode`模組。

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>請仔細套用 `[<AutoOpen>]`

`[<AutoOpen>]`建構可以會干擾範圍可用的呼叫端，並回答的項目來自何處是"magic"。 這通常不是個好方法。 此規則的例外狀況是 F # 核心程式庫本身 （雖然這項事實也是一個位元爭議）。

不過，它是方便起見，如果想要組織分別從該公用 API 的公用 API 中的協助專家的功能。

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

這可讓您完全不同的實作詳細資料，從函式的公用 API 而不必完整限定每次呼叫時的協助程式。

此外，公開的擴充方法和命名空間層級的運算式產生器可以清楚表示與`[<AutoOpen>]`。

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>使用`[<RequireQualifiedAccess>]`每當名稱可能會發生衝突，或是您認為它有助於可讀性

加入`[<RequireQualifiedAccess>]`模組的屬性表示模組可能未開啟，而且參考的模組項目需要明確限定存取。 例如，`Microsoft.FSharp.Collections.List`模組有這個屬性。

當函式和模組中的值有可能會與其他模組中的名稱發生衝突的名稱，這非常有用。 需要完整存取權可以大幅增加長期的可維護性和 evolvability 的文件庫。

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>排序`open`陳述式拓撲

F # 中宣告的順序很重要，包括具有`open`陳述式。 這是不同於 C# 中，其中的效果`using`和`using static`無關的檔案中的這些陳述式的順序。

在 F # 中，開啟進入範圍內的項目可以遮蔽其他人已經存在。 這表示該重新排列`open`陳述式無法變更程式碼的意義。 如此一來，所有排序任何任意`open`陳述式 （例如，文數字順序） 通常不建議，能產生您所預期的不同行為。

相反地，我們建議您排序它們[拓撲](https://en.wikipedia.org/wiki/Topological_sorting); 也就是排序您`open`陳述式中的順序_層_定義您的系統。 英數字元的排序不同拓撲的圖層內也列入考量。

例如，以下是 F # 編譯器服務公開 API 檔案的拓樸排序：

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

請注意分行符號分隔拓樸的圖層，與正在排序文數字順序之後的每個圖層。 這完全沒有不小心遮蔽值組織程式碼。

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>使用的類別包含具有副作用的值

有許多次初始化值，當有副作用，例如具現化的資料庫或其他遠端資源的內容。 很容易初始化模組中的這類事件，並將它用於後續的函式：

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

通常是個好主意有幾個原因：

首先，應用程式設定都會被推送至與程式碼基底`dep1`和`dep2`。 這是不易維護中較大程式碼基底。

第二個，以靜態方式初始化的資料不應該包含不具備執行緒安全，如果您的元件將本身使用多個執行緒的值。 這清楚地違反`dep3`。

最後，模組初始化會編譯成靜態建構函式的整個編譯單元。 如果該模組中的 let 繫結值初始化發生任何錯誤時，它都會顯示`TypeInitializationException`，然後快取的應用程式的整個存留期間。 這很難進行診斷。 通常是內部例外狀況，您可以嘗試理解，但如果沒有，就沒有通知的根本原因為何。

相反地，只使用一個簡單的類別來保存相依性：

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

這可啟用下列功能：

1. 推入 API 本身以外的任何相依狀態。
2. 現在，先完成組態外部應用程式開發介面。
3. 相依值的初始設定中的錯誤不太可能為`TypeInitializationException`。
4. 現在您更輕鬆地測試應用程式開發介面。

## <a name="error-management"></a>錯誤管理

大型系統中的錯誤管理是複雜且 nuanced 的工作，而且沒有任何銀級項目符號，確保您的系統容錯，而且也行為。 下列指導方針應該提供瀏覽此困難空間的指引。

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>表示錯誤的情況下，類型內建到您的網域中有不合法的狀態

與[差別等位](../language-reference/discriminated-unions.md)，F # 可讓您以型別系統中表示錯誤的程式狀態。 例如: 

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

在此情況下，有三個提款從銀行帳戶的金錢可以失敗的已知的方式。 每個錯誤案例中呈現的型別，，和可以因此局部性安全地在整個程式。

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

一般情況下，如果您可以建立模型的不同方式的事情可以**失敗**在您的網域，然後錯誤處理程式碼不再視為您除了一般程式流程必須處理的項目。 它是只是一般程式流程的一部分，而且不會被視為**例外**。 有這兩項主要優點：

1. 很容易維護您的網域變更後經過一段時間。
2. 錯誤的情況下是單元測試更容易。

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>當錯誤不可以有型別時，使用例外狀況

可以表示並非所有錯誤，問題網域中。 這些類型的錯誤則*例外*的本質，因此能夠提高和 F # 中攔截例外狀況。

首先，建議您先閱讀[例外狀況的設計指導方針](../../standard/design-guidelines/exceptions.md)。 這些是也適用於 F #。

基於引發例外狀況的可用在 F # 中的主要構造應該考慮下列喜好設定順序：

| 功能 | 語法 | 用途 |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | 引發`System.ArgumentNullException`具有指定的引數名稱。 |
| `invalidArg` | `invalidArg "argumentName" "message"` | 引發`System.ArgumentException`具有指定的引數名稱和訊息。 |
| `invalidOp` | `invalidOp "message"` | 引發`System.InvalidOperationException`使用指定的訊息。 |
|`raise`| `raise (ExceptionType("message"))` | 擲回例外狀況的一般用途機制。 |
| `failwith` | `failwith "message"` | 引發`System.Exception`使用指定的訊息。 |
| `failwithf` | `failwithf "format string" argForFormatString` | 引發`System.Exception`由格式字串和其輸入的訊息。 |

使用`nullArg`，`invalidArg`和`invalidOp`做為擲回的機制`ArgumentNullException`，`ArgumentException`和`InvalidOperationException`適當的時候。

`failwith`和`failwithf`函式通常應該避免因為在引發基底`Exception`輸入時，不特定的例外狀況。 根據[例外狀況的設計指導方針](../../standard/design-guidelines/exceptions.md)，您想要時您可以引發其他特定的例外狀況。

### <a name="using-exception-handling-syntax"></a>使用例外狀況處理語法

F # 支援透過例外狀況模式`try...with`語法：

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

協調遇到例外狀況的模式比對時所執行的功能可能有點困難，如果您想要讓程式碼清除。 若要處理這一個這類方法是使用[現用模式](../language-reference/active-patterns.md)做為群組周圍本身發生例外狀況的錯誤案例的功能。 比方說，您可能會耗用的 API，就會擲回例外狀況，當是有用的資訊放在例外狀況的中繼資料。 解除包裝成為現用模式內擷取例外狀況的主體中有用的值和傳回值可以在某些情況下很有幫助。

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>請勿使用 monadic 錯誤取代例外狀況處理

例外狀況會視為稍微 taboo 功能性程式設計。 事實上，例外狀況會違反純度，因此可以放心將它們未竟全功功能。 不過，這會忽略實際的程式碼必須執行位置，和該執行階段可能會發生錯誤。 一般而言，撰寫程式碼大部分都是純都總計，以減少不愉快的意外假設。

請務必考慮下列核心優勢/層面的例外狀況相對於其相關性及整個.NET 執行階段和跨語言生態系統中的:

1. 它們包含詳細的診斷資訊，這問題進行偵錯時非常有用。
2. 它們是由執行階段和其他.NET 語言非常清楚。
3. 可降低未定案相較於超出其方法的程式碼的重大*避免*藉由實作其語意某些子集臨機操作為基礎的例外狀況。

此第三個點很重要。 重要複雜的作業，無法使用例外狀況可能會導致處理結構如下：

```fsharp
Result<Result<MyType, string>, string list>
```

這很容易導致易損壞的模式比對"stringly 型別 」 的錯誤程式碼：

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

此外，可能很容易讓人忍受希望 「 簡單 」 函式會傳回"沒用"的型別中的任何例外狀況：

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

不幸的是，`tryReadAllText`根據在檔案系統上，可以發生的事項的相關的許多例外狀況，以及這段程式碼會立即捨棄可能實際上什麼錯誤您的環境中的任何資訊。 如果您取代這段程式碼的結果型別時，您可以回到 「 stringly 型別 」 的錯誤訊息剖析：

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

然後將放入本身的例外狀況物件中`Error`建構函式只會強制您正確處理位於呼叫位置，而不是函式中的例外狀況類型。 如此一來有效地建立選取的例外狀況，也就是為應用程式開發介面的呼叫端處理簡單 unfun。

上述範例的理想替代方法是以攔截*特定*例外狀況，並傳回該例外狀況的內容中有意義的值。 如果您修改`tryReadAllText`函式，如下所示，`None`有更多的意義：

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

而不是做為 catch all，此函式將現在正確處理的情況時找不到檔案，而且將該意義指派給傳回。 不捨棄任何內容的資訊，或強制處理情況下可能不相關的程式碼中該時間點呼叫時，這個傳回值可以對應到此錯誤的情況下。

這類類型`Result<'Success, 'Error>`適用於基本作業，它們不巢狀的而 F # 選擇性類型非常適合用以表示當項目無法回到*東西*或*nothing*. 它們並非取代例外狀況，不過，不應嘗試取代例外狀況。 而是應該將它們套用明智地址的例外狀況和錯誤的管理原則的特定層面目標的方式。

## <a name="partial-application-and-point-free-programming"></a>部分應用程式和無點的程式設計

F # 支援部分的應用程式，因此程式的各種方式點可用樣式。 這可能會很有用的模組或某樣東西，實作內重複使用程式碼，但它通常不是可公開公開。 一般情況下，無點的程式設計 virtue 本身，並不可以加入認知一道重大障礙人士不 immersed 樣式。

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>請勿使用部分的應用程式和對在公用 Api

有一些例外狀況，使用公用 Api 中的部分應用程式可以是取用者會造成混淆。 通常， `let`-F # 程式碼中的繫結值**值**，而非**函式值**。 混合在一起的值和函式值可能會導致儲存少數的幾行程式碼出具相當多的認知的額外負荷，特別是當這類結合運算子`>>`撰寫函式。

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>請考慮點可用程式設計工具含意

局部調用函式不會標示其引數。 這會有影響的工具。 請考慮下列兩個函式：

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

兩者都是有效的函式，但`funcWithApplication`是局部調用函式。 當您將滑鼠停留在它們的型別，在編輯器中時，您會看到：

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

位於呼叫位置，例如 Visual Studio 工具中的工具提示將不提供有意義的資訊項目`string`和`int`實際代表輸入的類型。

如果您遇到點釋出類似的程式碼`funcWithApplication`公開您可以使用，建議您執行完整的 η 擴充，以工具可以挑選上引數的有意義的名稱。

此外，偵錯無點的程式碼會有點困難，不可能。 偵錯工具需要依賴繫結至名稱的值 (例如，`let`繫結)，使您可以檢查執行透過中繼值入該值。 當您的程式碼沒有要檢查的值時，要偵錯項目。 未來，偵錯工具可能發展合成根據先前執行的路徑，這些值，但不是個不錯的主意 hedge 您首選上*潛在*偵錯功能。

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>請考慮減少內部未定案做為一個技巧部分應用程式

相較於先前的點，部分應用程式是用來減少應用程式或應用程式開發介面的更深入的內部資訊內的未定案的完美工具。 它可以很有幫助的單元測試更複雜應用程式開發介面，其中未定案通常是處理很麻煩的實作。 例如，下列的程式碼示範如何完成哪些最模擬架構可讓您不需使這類架構上的外部相依性，需要了解相關 bespoke 應用程式開發介面。

例如，請考慮下列解決方案拓撲：

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj` 例如，可能會公開程式碼：

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

單元測試`Transactions.doTransaction`中`ImplementationLogic.Tests.fspoj`很簡單：

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

部分套用`doTransaction`與模擬的內容物件可讓您在單元測試的所有呼叫函式，而不需要每次建構模擬的內容：

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

這項技術應該不會全域套用至您整個程式碼基底，但是它是一個好的方法，以減少重複使用的複雜的內部和執行單元測試這些內部項目。

## <a name="access-control"></a>存取控制

F # 擁有多個選項[存取控制](../language-reference/access-control.md)、 繼承自所提供的.NET 執行階段功能。 這些不是只可供類型-您也可以使用它們的函式。

* 偏好非`public`型別和成員，直到您需要的時候才可供公開使用。 這也會盡可能降低到哪些取用者幾
* 努力將所有的協助程式功能`private`。
* 請考慮使用`[<AutoOpen>]`helper 函式如果它們變成許多私用模組上。

## <a name="type-inference-and-generics"></a>類型推斷泛型

類型推斷可讓您輸入大量重複使用。 而自動產生 F # 編譯器中的可協助您在您的組件上撰寫更泛型的程式碼，使用幾乎任何額外的工作。 不過，這些功能不通用良好。

* 請考慮使用明確的類型，在公用 Api 標記引數名稱，請勿依賴類型推斷的。

    這麼做的原因在於**您**應該在您的 API，編譯器不圖形的控制項。 儘管編譯器推斷類型，讓您在正常作業，很可能有的應用程式開發介面變更形狀，如果它依賴內部項目已變更的類型。 這可能是您要的結果，但它將會幾乎導致下游取用者必須處理的重大應用程式開發介面變更。 相反地，如果您明確地控制您的公用 API 的形狀，您可以控制這些重大變更。 DDD 來說，這可以視為反損毀圖層。

* 請考慮您的泛型引數，提供有意義的名稱。

    除非您正在撰寫並非專門針對特定網域的真正泛型程式碼，有意義的名稱可協助其他程式設計人員了解他們正在處理中的網域。 例如，名為型別參數`'Document`互動與文件的內容中資料庫讓您更清楚，可接受泛型文件類型的函式或您正在使用的成員。

* 請考慮命名 PascalCase 與泛型型別參數。

    這是一般的方式來作業，在.NET 中，所以建議您在 PascalCase 而不是 snake_case 或 camelCase 時使用。

最後，自動一般化不一定是 F # 或大型的程式碼基底的新手人員 boon。 中使用的一般元件沒有認知的額外負荷。 此外，如果自動一般化函式不適用於採用不同輸入類型 （讓單獨如果它們要這麼做），則沒有任何實際它們正在泛型時間中該時間點的好處。 務必考慮您要撰寫的程式碼將會實際從正在泛型中獲益。

## <a name="performance"></a>效能

F # 的值為依預設，可讓您避免某些錯誤 （特別是那些涉及並行處理和平行處理原則） 的類別不可變的。 不過，在某些情況下，為了達到最佳 （或甚至合理） 的執行時間或記憶體配置的效率工作的範圍可能最好使用來實作就地變動的狀態。 這是可行的選擇加入個別與 F # 與`mutable`關鍵字。

不過，使用`mutable`F # 中可能會覺得與功能的單純性。 這是正常的如果您調整純度，若要從期望[參考透明度](https://en.wikipedia.org/wiki/Referential_transparency)。 參考透明度-不純度-撰寫 F # 函式時最終目標。 這可讓您以變動為基礎實作的效能關鍵的程式碼覆寫功能的介面。

### <a name="wrap-mutable-code-in-immutable-interfaces"></a>可變動的程式碼包裝在不可變的介面

具有參考目標的透明度，務必撰寫程式碼，不會公開可變動的 underbelly 的效能關鍵的函式。 例如，下列程式碼會實作`Array.contains`F # 核心程式庫中的函式：

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

多次呼叫這個函式不會變更基礎的陣列，也不會要求您維護任何可變動的狀態中使用它。 它是參考透明，，即使幾乎每一行程式碼內使用變動。

### <a name="consider-encapsulating-mutable-data-in-classes"></a>請考慮將封裝中的類別可變動的資料

前一個範例會用來封裝使用可變動的資料作業的單一函式。 這不一定足夠用於更複雜的資料集。 請考慮下列各組函式：

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

此程式碼是高效能，但是它會公開的呼叫端必須負責維護的變化型資料結構。 這可以在不含基礎成員可以變更類別包裝：

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

`Closure1Table` 封裝基礎變動為基礎的資料結構，因此未強制執行以維護基礎資料結構的呼叫端。 類別是強大的方式，來封裝資料，而不會暴露給呼叫者的詳細資料是以變動為基礎的常式。

### <a name="prefer-let-mutable-to-reference-cells"></a>偏好`let mutable`參考儲存格

參考儲存格可將代表值，而不是值本身的參考。 雖然它們可用於效能關鍵的程式碼，並通常不建議。 參考下列範例：

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

使用參考儲存格現在"污染"與需要取值 （dereference），並重新參考的基礎資料的所有後續程式碼。 相反地，請考慮`let mutable`:

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

Lambda 運算式的中間變動的單一點，除了所有其他程式碼，且碰觸`acc`可以在一般使用方式沒有不同的方式進行`let`-繫結不可變的值。 這會讓您更輕鬆地隨著時間而變更。

## <a name="object-programming"></a>物件的程式設計

F # 提供物件和物件導向 (OO) 概念的完整支援。 雖然許多 OO 概念是功能強大且很有用，但並非所有都適合用來使用。 下列清單提供指引以高層級 OO 功能的類別。

**請考慮在許多情況下使用這些功能：**

* 點標記法 (`x.Length`)
* 執行個體成員
* 隱含建構函式
* 靜態成員
* 索引子標記法 (`arr.[x]`)
* 具名和選擇性引數
* 介面與介面實作

**不連線到這些功能的第一次，但不要明智時加以套用它們會很方便解決問題：**

* 方法多載
* 封裝可變動的資料
* 類型的運算子
* Auto 屬性
* 實作`IDisposable`和 `IEnumerable`
* 類型擴充功能
* 事件
* 結構
* 委派
* 列舉

**除非您必須使用它們，通常可以避免這些功能：**

* 繼承型別階層和實作繼承
* Null 和 `Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>組合，而不用繼承

[組合透過繼承](https://en.wikipedia.org/wiki/Composition_over_inheritance)是很好的 F # 程式碼遵守 lock 慣用句。 基本原則是您應該不公開基底類別，並強制繼承自該基底類別，以取得功能的呼叫端。

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>如果您不需要在類別實作介面中使用物件運算式

[物件運算式](../language-reference/object-expressions.md)可讓您即時實作介面，繫結實作的介面值而不需要這麼做在類別內。 這非常方便，尤其是如果您_只_需要實作介面並不需要完整的類別。

例如，以下是執行中的程式碼[Ionide](http://ionide.io/)提供程式碼修正動作，如果您已新增您不需要的符號`open`陳述式：

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

因為類別不需要與 Visual Studio 程式碼 API 互動時，物件運算式都是這個的理想工具。 它們也是有價值的單元測試，當您想要清除以臨機操作方式與測試常式的介面。

## <a name="type-abbreviations"></a>類型縮寫

[類型縮寫](../language-reference/type-abbreviations.md)是方便的方法，若要將標籤指派至另一個類型，例如函式簽章或複雜類型。 例如，下列別名會將標籤指派給需要什麼來定義的計算與[CNTK](https://www.microsoft.com/cognitive-toolkit/)、 深層學習程式庫：

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

`Computation`名稱是一個便利的方式來表示它是別名的簽章相符的任何函式。 使用像這樣的類型縮寫相當方便，而且允許更簡潔的程式碼。

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>請避免使用以代表您的網域類型縮寫

雖然類型縮寫方便函式簽章來為指定的名稱，但是它們可能會造成混淆的情況，當縮寫其他類型。 請考慮這個縮寫：

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

這可能會造成混淆的多種方式項目：

* `BufferSize` 不是抽象概念。這是整數的只是另一個名稱。
* 如果`BufferSize`公開在公用 API 中，它可以輕鬆地被錯譯不只是表示`int`。 一般而言，有多個屬性，這些網域類型，而不是基本型別，例如`int`。 這個縮寫違反假設。
* 大小寫`BufferSize`(PascalCase) 表示這個類型保留更多資料。
* 此別名並未提供相較於提供給函式的具名引數的增加的清晰度。
* 縮寫不將資訊清單中已編譯的 IL。它只是整數，這個別名是編譯時期建構。

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) =
        ...
```

在 [摘要] 使用類型縮寫陷阱一點是它**不**它們縮寫的類型的抽象概念。 在上述範例中，`BufferSize`只是`int`實際上與其他資料或從型別系統，除了功能所帶來的優點`int`已使用。
