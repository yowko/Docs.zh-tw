---
title: F# 編碼慣例
description: 瞭解撰寫F#程式碼時的一般方針和慣用語。
ms.date: 01/15/2020
ms.openlocfilehash: ca86bcf714d2fb4ee5f173ee54ba12c317f9abe7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737819"
---
# <a name="f-coding-conventions"></a>F# 編碼慣例

下列慣例是從使用大型F#代碼基底的經驗來制定。 [良好F#程式碼的五大原則](index.md#five-principles-of-good-f-code)是每個建議的基礎。 它們與[ F#元件設計指導方針](component-design-guidelines.md)有關，但適用于任何F#程式碼，而不只是程式庫之類的元件。

## <a name="organizing-code"></a>組織程式碼

F#有兩種主要方式可組織程式碼：模組和命名空間。 這些類似，但有下列差異：

* 命名空間會編譯為 .NET 命名空間。 模組會編譯為靜態類別。
* 命名空間一律是最上層。 模組可以是最上層，並在其他模組中嵌套。
* 命名空間可以跨越多個檔案。 模組不能。
* 您可以使用 `[<RequireQualifiedAccess>]` 和 `[<AutoOpen>]`裝飾模組。

下列指導方針可協助您使用這些指引來組織您的程式碼。

### <a name="prefer-namespaces-at-the-top-level"></a>偏好位於最上層的命名空間

針對任何可公開取用的程式碼，命名空間會優先于最上層的模組。 因為它們會編譯為 .NET 命名空間，所以可以從C#取用，而不會有任何問題。

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

當只從F#呼叫時，使用最上層模組可能不會出現不同，但C#對於取用者，必須使用 `MyCode` 模組限定 `MyClass`，可能會讓呼叫端感到驚訝。

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>小心套用 `[<AutoOpen>]`

`[<AutoOpen>]` 結構可以會污染可供呼叫端使用的範圍，而有問題的答案則是「魔術」。 這不是件好事。 此規則的F#例外狀況是核心程式庫本身（但此事實也是有爭議的）。

不過，如果您有想要與公用 API 分開組織之公用 API 的協助程式功能，這是很方便的。

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

如此一來，您就不需要在每次呼叫時都完整限定協助程式，即可從函式的公用 API 中明確地分隔執行詳細資料。

此外，在命名空間層級公開擴充方法和運算式產生器，可以使用 `[<AutoOpen>]`進行整齊表示。

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>當名稱可能發生衝突，或您覺得它有助於可讀性時，請使用 `[<RequireQualifiedAccess>]`

將 `[<RequireQualifiedAccess>]` 屬性加入模組中，表示模組可能無法開啟，而且對模組元素的參考需要明確限定的存取權。 例如，`Microsoft.FSharp.Collections.List` 模組具有這個屬性。

當模組中的函數和值有可能與其他模組中的名稱衝突的名稱時，這會很有用。 需要限定的存取權可能會大幅增加程式庫的長期維護性和 evolvability。

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>排序 `open` 語句拓撲

在F#中，宣告的順序很重要，包括 `open` 語句。 這與不同C#之處在于，`using` 和 `using static` 的效果與檔案中這些語句的順序無關。

在F#中，開啟範圍中的專案可能會遮蔽其他已存在的專案。 這表示重新排列 `open` 語句可能會改變程式碼的意義。 因此，不建議所有 `open` 語句的任意排序（例如排序），以免您會產生可能預期的不同行為。

相反地，我們建議您將它們排序[拓撲](https://en.wikipedia.org/wiki/Topological_sorting);也就是，依照您的系統_層_級的定義順序來排序您的 `open` 語句。 您也可以考慮在不同的拓撲層中進行英數位元排序。

例如，以下是F#編譯器服務公用 API 檔案的拓撲排序：

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

請注意，分行符號會分隔拓撲層，之後的每個圖層都會排序排序。 這會完全組織程式碼，而不會不小心遮蔽值。

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>使用類別來包含有副作用的值

將值初始化時，有很多時候會有副作用，例如將內容具現化至資料庫或其他遠端資源。 在模組中初始化這類專案，並在後續的函式中使用它是很吸引人的：

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

這通常是不好的想法，原因如下：

首先，應用程式設定會使用 `dep1` 和 `dep2`推送至程式碼基底。 這在較大的基本代碼基底中很容易維護。

第二，如果您的元件本身會使用多個執行緒，則靜態初始化的資料應該不會包含不具備執行緒安全的值。 `dep3`會明顯地違反此情況。

最後，模組初始化會編譯成整個編譯單位的靜態函式。 如果在該模組的 let 系結值初始化中發生任何錯誤，則會將它視為 `TypeInitializationException`，然後針對應用程式的整個存留期進行快取。 這可能很容易診斷。 通常，您可以嘗試進行的內部例外狀況，但如果沒有，則不會告知根本原因。

相反地，只要使用簡單的類別來保存相依性：

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member _.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member _.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

這會啟用下列功能：

1. 將任何相依的狀態推送至 API 本身以外的地方。
2. 設定現在可以在 API 外部完成。
3. 相依值的初始化錯誤不太可能會 `TypeInitializationException`資訊清單。
4. API 現在更容易測試。

## <a name="error-management"></a>錯誤管理

大型系統中的錯誤管理是一項複雜且差別細微的工作，而且沒有任何銀級的專案，以確保您的系統具有容錯能力，而且行為良好。 下列指導方針應該提供流覽這個艱難空間的指引。

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>表示在您的網域內建類型中的錯誤案例和不合法的狀態

使用[區分](../language-reference/discriminated-unions.md)聯集F# ，可讓您在類型系統中代表有問題的程式狀態。 例如：

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

在此情況下，有三種已知的方式可讓銀行帳戶的提款 money 失敗。 每個錯誤案例都會以類型表示，因此可在整個程式中安全地處理。

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

一般來說，如果您可以建立在網域中可能會**失敗**之不同方式的模型，則不會再將錯誤處理常式代碼視為您必須處理的某些專案，而不是一般程式流程。 這只是一般程式流程的一部分，並不會視為**例外**狀況。 這有兩個主要優點：

1. 隨著您的網域在一段時間內的變更，更容易維護。
2. 錯誤案例較容易進行單元測試。

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>當錯誤無法以類型表示時，使用例外狀況

並非所有的錯誤都可以在問題網域中表示。 這類錯誤本質上是*例外*狀況，因此能夠引發和攔截中F#的例外狀況。

首先，建議您閱讀[例外狀況設計指導方針](../../standard/design-guidelines/exceptions.md)。 這些也適用于F#。

中F#可用來引發例外狀況的主要結構，應依照下列喜好設定順序來考慮：

| 函數 | 語法 | 用途 |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | 使用指定的引數名稱引發 `System.ArgumentNullException`。 |
| `invalidArg` | `invalidArg "argumentName" "message"` | 使用指定的引數名稱和訊息，引發 `System.ArgumentException`。 |
| `invalidOp` | `invalidOp "message"` | 使用指定的訊息引發 `System.InvalidOperationException`。 |
|`raise`| `raise (ExceptionType("message"))` | 用來擲回例外狀況的一般用途機制。 |
| `failwith` | `failwith "message"` | 使用指定的訊息引發 `System.Exception`。 |
| `failwithf` | `failwithf "format string" argForFormatString` | 使用格式字串及其輸入所決定的訊息，引發 `System.Exception`。 |

在適當的情況下，請使用 `nullArg`、`invalidArg` 和 `invalidOp` 作為用來擲回 `ArgumentNullException`、`ArgumentException` 和 `InvalidOperationException` 的機制。

通常應該避免使用 `failwith` 和 `failwithf` 函數，因為它們會引發基底 `Exception` 類型，而不是特定的例外狀況。 根據例外狀況[設計指導方針](../../standard/design-guidelines/exceptions.md)，您會想要在可以時引發更具體的例外狀況。

### <a name="using-exception-handling-syntax"></a>使用例外狀況處理語法

F#支援透過 `try...with` 語法的例外狀況模式：

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

如果您想要讓程式碼保持整潔，請將功能與模式比對的例外狀況協調，以降低執行的情況。 處理這種情況的方法之一，就是使用作用中的[模式](../language-reference/active-patterns.md)來分組發生錯誤案例的功能，以及例外狀況本身。 例如，您可能會使用 API，當它擲回例外狀況時，會在例外狀況中繼資料中括住重要資訊。 在使用中模式的已捕捉例外狀況內解除包裝有用的值，並在某些情況下傳回該值會很有説明。

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>請勿使用 monadic 錯誤處理來取代例外狀況

在功能程式設計中，例外狀況會被視為有點 taboo。 事實上，例外狀況違反了純度，因此可以放心地將它們視為不太實用。 不過，這會忽略程式碼必須執行的實際情況，而且可能會發生執行階段錯誤。 一般來說，請撰寫程式碼，假設大部分專案都不是純粹的，也不是總計，以儘量減少不愉快的意外。

對於 .NET 執行時間和跨語言生態系統中的相關性和」適當性，請務必考慮下列各項核心的優缺點：

1. 其中包含詳細的診斷資訊，在發生問題時很有説明。
2. 這是執行時間和其他 .NET 語言的良好理解。
3. 相較于無法以臨機操作方式來執行某些部分的語義，它們可以減少重複使用的程式碼，以*避免*例外狀況。

第三個點很重要。 針對重要複雜的作業，無法使用例外狀況可能會導致處理如下的結構：

```fsharp
Result<Result<MyType, string>, string list>
```

這可以輕鬆地導致像是「stringly 類型」錯誤的模式比對等脆弱的程式碼：

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

此外，若要對傳回 "更好" 類型的「簡單」函式，忍受任何例外狀況，可能會很吸引人：

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

可惜的是，`tryReadAllText` 可能會根據檔案系統上的各種專案來擲回許多例外狀況，而此程式碼會捨棄您的環境中可能發生錯誤的任何相關資訊。 如果您將此程式碼取代為結果類型，則會回到「stringly 類型」錯誤訊息剖析：

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

而將例外狀況物件本身放在 `Error` 的函式中，只會強制您在呼叫位置（而不是在函式）中正確處理例外狀況類型。 這麼做可以有效地建立已檢查的例外狀況，這是以 API 的呼叫者身分處理的 unfun。

在上述範例中，有一個很好的替代方式，就是攔截*特定*的例外狀況，並在該例外狀況的內容中傳回有意義的值。 如果您修改 `tryReadAllText` 函式，如下所示，`None` 會有更多意義：

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

此函式會立即適當地處理找不到檔案的情況，並將該意義指派給傳回，而不是當做全部攔截。 這個傳回值可以對應至該錯誤案例，而不會捨棄任何內容資訊或強制呼叫端處理常式代碼中可能不相關的案例。

如 `Result<'Success, 'Error>` 之類的類型適用于不是嵌套的基本作業，而F#選擇性類型則非常適合用來表示何時可以傳回任何*內容*或*任何*內容。 不過，它們不是例外狀況的取代，而且不應該用於嘗試取代例外狀況。 相反地，應該謹慎套用，以以目標方式處理例外狀況和錯誤管理原則的特定層面。

## <a name="partial-application-and-point-free-programming"></a>部分應用程式和無點程式設計

F#支援部分應用程式，因此可以用各種不同的方式，以無點的風格進行程式設計。 這對於在模組內重複使用程式碼或執行某個專案很有説明，但並不是要公開公開的東西。 一般來說，無點程式設計並不是本身的本身，而且可以為未可以沉浸樣式的人員加入重要的認知屏障。

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>請勿在公用 Api 中使用部分應用程式和 currying

除了例外狀況外，在公用 Api 中使用部分應用程式可能會對取用者造成混淆。 通常，程式碼中F#的 `let`系結值為**值**，而不是**函數值**。 將值和函數值混在一起，可讓您在 exchange 中儲存少量的程式碼，以產生相當多的認知額外負荷，尤其是如果與 `>>` 的運算子結合以撰寫函式。

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>考慮無點程式設計的工具含意

擴充函數不會標示其引數。 這會影響工具。 請考慮下列兩個功能：

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

兩者都是有效的函式，但 `funcWithApplication` 是一個擴充函數。 當您將滑鼠停留在編輯器中的類型時，您會看到：

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

在呼叫位置，工具（例如 Visual Studio）中的工具提示不會提供有意義的資訊，讓您瞭解 `string` 和 `int` 輸入類型實際上所代表的內容。

如果您遇到無點程式碼，例如可公開使用的 `funcWithApplication`，建議您執行完整的η擴充，讓工具可以針對引數取得有意義的名稱。

此外，如果不可能，則偵錯工具不會有困難的程式碼。 偵錯工具會依賴系結至名稱的值（例如，`let` 系結），以便您可以在執行期間檢查中間值。 當您的程式碼沒有任何要檢查的值時，不會有任何可進行的偵錯工具。 在未來，偵錯工具可能會演變為根據先前執行的路徑來合成這些值，但不建議您在*可能*的偵測功能上建立您的理由。

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>將部分應用程式視為減少內部重複使用的技術

相較于先前的點，部分應用程式是一項很棒的工具，可減少應用程式內的重複使用或更深入的 API 內部。 這對於執行更複雜 Api 的單元測試很有説明，其中的重複使用通常是一項很難處理的難題。 例如，下列程式碼會示範如何完成大部分的模擬架構，讓您不需要對這類架構進行外部相依性，也必須瞭解相關的定制 API。

例如，請考慮下列解決方案的拓撲：

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj` 可能會公開程式碼，例如：

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member _.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

`ImplementationLogic.Tests.fsproj` 中的單元測試 `Transactions.doTransaction` 很簡單：

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

部分套用 `doTransaction` 搭配模擬內容物件，可讓您在所有單元測試中呼叫函式，而不需要每次都要建立模擬內容：

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

這項技術不應通用地套用到整個程式碼基底，但這是減少複雜內部和單元測試這些內部專案的好方法。

## <a name="access-control"></a>存取控制

F#有多個[存取控制](../language-reference/access-control.md)選項，繼承自 .net 執行時間中可用的內容。 這些不只適用于類型，您也可以將它們用於函數。

* 偏好非`public` 的類型和成員，直到您需要它們可公開取用為止。 這也可以減少取用者的需求。
* 努力保持所有 helper 功能 `private`。
* 請考慮在 helper 函式的私用模組上使用 `[<AutoOpen>]` （如果它們變得很多）。

## <a name="type-inference-and-generics"></a>型別推斷和泛型

型別推斷可為您節省許多樣板的輸入。 而編譯器中的F#自動一般化可以協助您撰寫更通用的程式碼，幾乎不需要額外的工作。 不過，這些功能並不是很普遍。

* 請考慮在公用 Api 中使用明確類型標記引數名稱，而且不依賴此的類型推斷。

    這是因為**您**應該控制 API 的形式，而不是編譯器。 雖然編譯器可以在推斷型別時執行精細的作業，但如果它依賴的內部專案有變更的型別，則您的 API 可能會有變更的圖形。 這可能是您想要的，但幾乎肯定會導致下游取用者必須處理的中斷性 API 變更。 相反地，如果您明確控制公用 API 的形式，則可以控制這些重大變更。 在 DDD 詞彙中，這可以視為反損毀層。

* 請考慮為您的泛型引數提供有意義的名稱。

    除非您撰寫的是真正的一般程式碼，而不是特定的網域，否則有意義的名稱可以協助其他程式設計人員瞭解他們正在處理的網域。 例如，在與檔資料庫互動的內容中，名為 `'Document` 的型別參數，讓您使用的函式或成員可接受一般檔案類型。

* 請考慮使用 PascalCase 來命名泛型型別參數。

    這是在 .NET 中執行工作的一般方式，因此建議您使用 PascalCase，而不要使用 snake_case 或 camelCase。

最後，對於不熟悉F#或大型程式碼基底的人員而言，自動一般化不一定是 boon 的。 使用泛型元件時，會發生認知額外負荷。 此外，如果自動一般化的函式不會與不同的輸入型別搭配使用（如果要用來做為這種類型，請單獨使用），在該時間點就不會有真正的優勢。 請務必考慮您撰寫的程式碼實際上是否受益于一般。

## <a name="performance"></a>效能

### <a name="prefer-structs-for-small-data-types"></a>針對小型資料類型偏好結構

使用結構（也稱為實數值型別）通常會導致某些程式碼的效能更高，因為它通常會避免設定物件。 不過，結構不一定是「更快速」的按鈕：如果結構中的資料大小超過16個位元組，複製資料通常會導致比使用參考型別更多的 CPU 時間。

若要判斷您是否應該使用結構，請考慮下列條件：

- 如果您的資料大小是16個位元組或更小。
- 如果您可能在執行中的程式中有許多這些資料類型是常駐在記憶體中。

如果第一個條件適用，您通常應該使用結構。 如果兩者都適用，您應該幾乎一律使用結構。 在某些情況下，可能會套用先前的條件，但使用結構不會比使用參考型別更好或更糟，但可能很罕見。 不過，一定要測量進行這類變更的時機，而不是在假設或直覺上操作。

#### <a name="prefer-struct-tuples-when-grouping-small-value-types"></a>群組小型數值型別時偏好使用結構元組

請考慮下列兩個功能：

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

當您使用[BenchmarkDotNet](https://benchmarkdotnet.org/)之類的統計效能評定工具來評估這些函式時，您會發現使用結構元組的 `runWithStructTuple` 函式會以更快的速度執行40%，且不會配置記憶體。

不過，在您自己的程式碼中，這些結果不一定會是這種情況。 如果您將函式標示為 `inline`，使用參考元組的程式碼可能會取得一些額外的優化，或配置的程式碼只會優化掉。 當效能考慮時，您應該一律測量結果，而且永遠不會根據假設或直覺來操作。

#### <a name="prefer-struct-records-when-the-data-type-is-small"></a>當資料類型很少時，偏好使用結構記錄

稍早所述的經驗法則也適用于[ F#記錄類型](../language-reference/records.md)。 請考慮下列處理它們的資料類型和函數：

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

這類似先前的元組程式碼，但這次範例會使用記錄和內嵌的內建函式。

當您使用[BenchmarkDotNet](https://benchmarkdotnet.org/)之類的統計效能評定工具來評估這些函式時，會發現 `processStructPoint` 的執行速度幾乎60%，而且不會在受控堆積上配置任何內容。

#### <a name="prefer-struct-discriminated-unions-when-the-data-type-is-small"></a>當資料類型很小時，偏好使用結構區分等位

先前的關於結構元組和記錄的效能，也適用于[ F#區分](../language-reference/discriminated-unions.md)等位。 請考慮下列程式碼：

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

定義單一案例的區分等位通常是為了進行領域模型化。 當您使用[BenchmarkDotNet](https://benchmarkdotnet.org/)之類的統計效能評定工具來評估這些函式時，您會發現 `structReverseName` 的執行速度比小型字串 `reverseName` 快25%。 對於大型字串，兩者都有相同的執行。 因此，在此情況下，最好是使用結構。 如先前所述，一律測量並不會在假設或直覺上運作。

雖然先前的範例顯示結構區分聯集產生較佳的效能，但在模型化定義域時，通常會有更大的區分等位。 較大的資料類型（例如，如果它們是結構而定）可能也不會執行，因為可能會涉及更多的複製作業。

### <a name="functional-programming-and-mutation"></a>功能性程式設計和變化

F#值預設為不可變，可讓您避免特定類別的錯誤（特別是涉及並行處理和平行處理原則的問題）。 不過，在某些情況下，為了達到執行時間或記憶體配置的最佳（或甚至合理）效率，可以使用就地的狀態變動來執行工作範圍。 您可以使用F#搭配 `mutable` 關鍵字的選擇來進行這項工作。

使用中F#的 `mutable` 可能會有功能純度的機率。 這是可理解的，但功能純度可能會有效能目標的機率。 入侵是要封裝變動，讓呼叫端不必在意呼叫函式時所發生的情況。 這可讓您針對效能關鍵程式碼，透過以變化為基礎的執行來撰寫功能介面。

#### <a name="wrap-mutable-code-in-immutable-interfaces"></a>在不可變的介面中包裝可變的程式碼

透過參考透明度作為目標，撰寫程式碼不會公開效能關鍵函式的可變動 underbelly，是很重要的。 例如，下列程式碼會實作用於F#核心程式庫中的 `Array.contains` 函式：

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

多次呼叫此函式並不會變更基礎陣列，也不需要維護任何使用它的可變狀態。 它參考上透明，即使其中幾乎每一行程式碼都使用變化。

#### <a name="consider-encapsulating-mutable-data-in-classes"></a>考慮在類別中封裝可變數據

先前的範例使用單一函式來封裝使用可變動資料的作業。 對於更複雜的資料集，這不一定是足夠的。 請考慮下列函數集：

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

這段程式碼的效能良好，但它會公開由呼叫端負責維護的以變化為基礎的資料結構。 這可以包裝在類別內，而且沒有可變更的基礎成員：

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

`Closure1Table` 封裝基礎的變動式資料結構，因此不會強制呼叫端維護基礎資料結構。 類別是一種強大的方式，可封裝以變化為基礎的資料和常式，而不會向呼叫端公開細節。

#### <a name="prefer-let-mutable-to-reference-cells"></a>偏好 `let mutable` 參考資料格

參考儲存格是一種方式，代表值的參考，而不是值本身。 雖然它們可以用於效能關鍵程式碼，但不建議您這麼做。 參考下列範例：

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

使用參考儲存格現在「干擾」所有後續的程式碼，都必須對基礎資料進行取值和重新參考。 相反地，請考慮 `let mutable`：

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

除了 lambda 運算式中間的單一變化點外，其他所有觸及 `acc` 的程式碼，都可以用與一般 `let`系結不可變值的用法不同的方式來執行這項操作。 這可讓您更輕鬆地隨著時間變更。

## <a name="object-programming"></a>物件程式設計

F#具有物件和麵向物件（OO）概念的完整支援。 雖然許多 OO 概念都非常強大且實用，但並非全部都適合使用。 下列清單提供有關在高階的 OO 功能類別的指引。

**在許多情況下，請考慮使用這些功能：**

* 點標記法（`x.Length`）
* 實例成員
* 隱含的函式
* 靜態成員
* 索引子標記法（`arr.[x]`）
* 命名和選擇性引數
* 介面和介面的實現

**請先不要觸達這些功能，但當它們很方便解決問題時，請謹慎套用：**

* 方法多載
* 封裝的可變數據
* 類型的運算子
* 自動屬性
* 執行 `IDisposable` 和 `IEnumerable`
* 類型延伸模組
* 「事件」
* 結構
* 委派
* 列舉

**除非您必須使用這些功能，否則通常會予以避免：**

* 繼承型型別階層和實作為繼承
* Null 和 `Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>偏好透過繼承撰寫

透過[繼承進行撰寫](https://en.wikipedia.org/wiki/Composition_over_inheritance)，是良好F#程式碼可以遵守的長期用法。 基本原則是，您不應該公開基類，並強制呼叫端從該基類繼承來取得功能。

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>如果您不需要類別，請使用物件運算式來執行介面

[物件運算式](../language-reference/object-expressions.md)可讓您即時執行介面，將實的介面系結至值，而不需要在類別內執行此動作。 這很方便，特別是當您_只_需要執行介面，而不需要完整類別時。

例如，下列程式碼會在[Ionide](http://ionide.io/)中執行，以提供程式碼修正動作（若您已新增不具有 `open` 語句的符號）：

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

因為與 Visual Studio Code API 互動時不需要類別，所以物件運算式是適用于此的理想工具。 當您想要以臨機操作方式將具有測試常式的介面 stub 時，它們也非常適合進行單元測試。

## <a name="consider-type-abbreviations-to-shorten-signatures"></a>請考慮輸入縮寫來縮短簽章

[類型縮寫](../language-reference/type-abbreviations.md)是將標籤指派給另一種類型（例如，函式簽章或更複雜的類型）的便利方式。 例如，下列別名會將標籤指派給使用[CNTK](https://docs.microsoft.com/cognitive-toolkit/)（深度學習程式庫）定義計算所需的內容：

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

`Computation` 名稱是一個方便的方式，可表示任何符合它所別名之簽章的函式。 使用這類的類型縮寫十分方便，並允許更簡潔的程式碼。

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>避免使用類型縮寫來代表您的網域

雖然類型縮寫對於提供名稱給函式簽章很方便，但在縮寫其他類型時可能會造成混淆。 請考慮下列縮寫：

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

這可能會讓您以多種方式混淆：

* `BufferSize` 不是抽象概念;它只是一個整數的另一個名稱。
* 如果 `BufferSize` 在公用 API 中公開，很容易被誤解為表示不只是 `int`。 一般來說，網欄位型別有多個屬性，而且不是基本型別，例如 `int`。 此縮寫違反該假設。
* `BufferSize` 的大小寫（PascalCase）表示此類型包含更多資料。
* 相較于將具名引數提供給函式，此別名並不提供更清楚的清晰度。
* 縮寫不會在編譯的 IL 中進行資訊清單;這只是一個整數，而此別名是編譯時間結構。

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

總而言之，類型縮寫的缺陷是它們**不**是縮寫的類型的抽象概念。 在上一個範例中，`BufferSize` 只是在幕後的 `int`，沒有額外的資料，也沒有任何來自型別系統的好處，除了 `int` 已經有的功能以外。

使用類型縮寫來表示網域的替代方法是使用單一案例的區分等位。 先前的範例可以模型化，如下所示：

```fsharp
type BufferSize = BufferSize of int
```

如果您撰寫的程式碼是以 `BufferSize` 及其基礎值來運作，您需要建立一個，而不是傳入任何任意整數：

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

這可減少錯誤地將任意整數傳遞至 `send` 函式的可能性，因為呼叫端必須先建立 `BufferSize` 型別來包裝值，然後再呼叫函式。
