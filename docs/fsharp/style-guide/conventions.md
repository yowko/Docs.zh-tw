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
# <a name="f-coding-conventions"></a>F # 編碼慣例

下列慣例會使用大型的 F # 的體驗編寫程式碼基底。 [良好的 F # 程式碼的五個原則](index.md#five-principles-of-good-f-code)是每個建議的基礎。 它們與相關[F # 元件的設計指導方針](component-design-guidelines.md)，但是也適用於任何 F # 程式碼，不只是元件，例如程式庫。

## <a name="organizing-code"></a>組織程式碼

F # 功能來組織程式碼的兩種主要方式： 模組與命名空間。 這些類似，但有下列差異：

* 命名空間會編譯為.NET 命名空間。 模組會編譯為靜態類別。
* 命名空間永遠是最上層。 模組可以是最上層和其他模組內的巢狀。
* 命名空間可以跨多個檔案。 模組不行。
* 模組可以使用裝飾`[<RequireQualifiedAccess>]`和`[<AutoOpen>]`。

下列指導方針將協助您使用這些來組織您的程式碼。

### <a name="prefer-namespaces-at-the-top-level"></a>想在最上層的命名空間

對於任何可公開使用的程式碼，命名空間是優先高層級的模組。 因為它們會編譯為.NET 命名空間，也就是從 C# 沒有問題可取用。

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

使用最上層模組可能不會出現不同只從 F # 中，呼叫時，但 C# 取用者，呼叫端可能會感到驚訝需要限定`MyClass`與`MyCode`模組。

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>請仔細套用 `[<AutoOpen>]`

`[<AutoOpen>]`建構可以干擾的呼叫端，為範圍和項目來自何處的答案是"magic"。 這通常不是一件好事。 此規則的例外狀況是 F # 核心程式庫本身 （雖然這項事實也是有點備受爭議的）。

不過，它是為了方便起見，如果您希望組織分別從該公用 API 的公用 API 中的協助程式功能。

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

可以讓您從函式的公用 API 完全不同的實作詳細資料，而不必完整限定的協助程式每次呼叫它。

此外，公開擴充方法和命名空間層級的運算式產生器可以整齊地表示`[<AutoOpen>]`。

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>使用`[<RequireQualifiedAccess>]`每當名稱可能會發生衝突，或是您認為它有助於提供可讀性

新增`[<RequireQualifiedAccess>]`模組的屬性表示模組可能未開啟，而且參考的模組項目需要明確限定存取。 比方說，`Microsoft.FSharp.Collections.List`模組有這個屬性。

當函式和模組中的值有可能會與其他模組中的名稱發生衝突的名稱，這非常有用。 需要完整存取權可能會大幅增加的長期維護性和可演化性程式庫。

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>排序`open`陳述式拓撲

在 F # 中，宣告的順序很重要，包括具有`open`陳述式。 這是不同於 C# 中，其中的效果`using`和`using static`無關的檔案中的這些陳述式的順序。

在 F # 中，開啟進入範圍內的項目可以遮蔽其他已經存在。 這表示重新排列`open`陳述式無法變更程式碼的意義。 如此一來，任何任意排序之所有`open`陳述式 （例如，文數字順序） 通常不建議，以免產生您所預期的不同行為。

相反地，我們建議您加以排序[拓撲](https://en.wikipedia.org/wiki/Topological_sorting); 也就是訂單您`open`陳述式中的順序_層_定義您的系統。 英數字元的排序不同的拓撲圖層內也列入考量。

例如，以下是 F # 編譯器服務公用 API 檔案的拓撲排序：

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

請注意分行符號分隔拓撲的層級，與正在排序文數字順序之後每個圖層。 這完全沒有不小心遮蔽值組織程式碼。

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>使用類別來包含有副作用的值

很多時候初始化值，當有副作用，例如具現化的資料庫或其他遠端資源的內容。 相當吸引人，初始化模組中的這類項目，並將它用於後續的函式：

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

通常是個好主意的幾個原因：

首先，應用程式設定都會被推送至程式碼基底`dep1`和`dep2`。 這很難維護較大程式碼基底。

第二個，以靜態方式初始化的資料不應該包含不具備執行緒安全，如果您的元件將本身使用多個執行緒的值。 這顯然違反`dep3`。

最後，模組的初始化會編譯成靜態的建構函式的整個編譯單元。 如果在該模組中的 let 繫結值初始化，就會發生任何錯誤，它記錄成資訊清單`TypeInitializationException`，則快取的應用程式的整個存留期間。 這很難診斷。 通常是內部例外狀況，您可以嘗試理解，但如果沒有，則沒有的根本原因的任何告知。

相反地，只要使用簡單的類別來保存相依性：

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

這可啟用下列功能：

1. 將推送 API 本身以外任何相依的狀態。
2. 外部 API 時，可以立即進行設定。
3. 初始化相依的值中的錯誤不是可能會顯示為`TypeInitializationException`。
4. 現在您更輕鬆地測試 API。

## <a name="error-management"></a>錯誤管理

大型系統中的錯誤管理是一項複雜且細微精密的工作，而且有項目符號，確保您的系統在容錯和行為也沒有 silver。 下列指導方針也應該提供指導方針中瀏覽此困難的空間。

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>代表錯誤案例和您的網域內建函式的型別中不合法的狀態

具有[差別聯集](../language-reference/discriminated-unions.md)，F # 可讓您能夠代表您的型別系統中的錯誤的程式狀態。 例如: 

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

在此情況下，有三種已知的方式，從銀行帳戶提款金額可能會失敗。 每個錯誤案例中會表示成的型別，並可以因此處理安全地在整個程式。

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

一般情況下，如果您可以建立模型的不同方式有可以**失敗**在您的網域，然後錯誤處理程式碼不會再視為您除了一般程式流程必須處理的項目。 它是只是一般程式流程的一部分，而且不被視為**卓越**。 有這兩項主要優點：

1. 很容易維護一段時間，變更您的網域。
2. 錯誤的情況下會更容易進行單元測試。

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>使用例外狀況，當類型不可以有錯誤

問題領域中，就可以表示並非所有的錯誤。 這類錯誤會*卓越*性質，因此能夠提高，並在 F # 中攔截例外狀況。

首先，建議您先閱讀[例外狀況的設計方針](../../standard/design-guidelines/exceptions.md)。 這些也是適用於 F #。

基於引發例外狀況的 F # 中可用的主要建構應該考慮以下列順序的喜好設定：

| 功能 | 語法 | 用途 |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | 引發`System.ArgumentNullException`具有指定的引數名稱。 |
| `invalidArg` | `invalidArg "argumentName" "message"` | 引發`System.ArgumentException`使用指定的引數名稱和訊息。 |
| `invalidOp` | `invalidOp "message"` | 引發`System.InvalidOperationException`使用指定的訊息。 |
|`raise`| `raise (ExceptionType("message"))` | 擲回例外狀況的一般用途機制。 |
| `failwith` | `failwith "message"` | 引發`System.Exception`使用指定的訊息。 |
| `failwithf` | `failwithf "format string" argForFormatString` | 引發`System.Exception`取決於在格式字串和其輸入的訊息。 |

使用`nullArg`，`invalidArg`並`invalidOp`做為擲回機制`ArgumentNullException`，`ArgumentException`和`InvalidOperationException`適當的時候。

`failwith`並`failwithf`函式通常應該避免因為它們會引發基底`Exception`輸入時，沒有特定的例外狀況。 依照[例外狀況的設計方針](../../standard/design-guidelines/exceptions.md)，您想要時您可以引發其他特定的例外狀況。

### <a name="using-exception-handling-syntax"></a>使用例外狀況處理語法

F # 支援例外狀況模式，透過`try...with`語法：

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

重新調整功能，以執行例外狀況的模式比對時可能有點困難，如果您想要的程式碼保持乾淨。 若要處理這其中一種方法是使用[作用中的模式](../language-reference/active-patterns.md)做為相關的例外狀況本身發生錯誤狀況的群組功能的方法。 例如，您可能會使用的 API，當它擲回例外狀況，則是寶貴的資訊放在例外狀況中繼資料。 解除包裝成為現用模式內擷取的例外狀況的主體中有用的值，並傳回值可以在某些情況下很有幫助。

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>請勿使用單邊錯誤取代例外狀況處理

例外狀況都被視為有點函式程式設計的 taboo。 事實上，例外狀況會違反單純性，以便安全地將它們視為不相當的功能。 不過，這會略過在實際程式碼必須執行位置，和該執行階段可能會發生錯誤。 一般情況下，撰寫程式碼大多是純和總計，以減少發生意外狀況都不假設。

請務必考慮下列核心優勢/層面的例外狀況相對於其相關性和.NET 執行階段和跨語言生態系統中整體的適當性：

1. 它們包含詳細的診斷資訊，也就是很有幫助，當偵錯問題。
2. 也就是大家熟悉的執行階段和其他.NET 語言。
3. 他們可以縮減目前相較於超出其方法的程式碼重大的未定案*避免*藉由實作其語意的一些臨機操作為基礎的例外狀況。

此第三個點很重要。 重要的複雜作業，無法使用例外狀況可能會導致處理結構如下：

```fsharp
Result<Result<MyType, string>, string list>
```

這很容易導致易損壞的程式碼，例如模式比對"stringly 型別 」 的錯誤：

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

此外，它很吸引人，適當地抑制在 「 簡單 」 的函式會傳回 「 好了 」 的型別所需的任何例外狀況：

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

不幸的是，`tryReadAllText`無數個檔案在系統，可以發生的情況為基礎的多個例外狀況，以及這段程式碼會立即捨棄任何項目可能實際上出錯您環境中的資訊。 如果您將此程式碼取代結果型別時，您會回到 「 stringly 型別 」 的錯誤訊息剖析：

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

並將例外狀況物件本身放置在`Error`建構函式只會強制您正確地處理在呼叫站台，而不是函式中的例外狀況類型。 有效地執行此動作會建立檢查例外狀況，也就是都是聲名狼藉 unfun 作為 API 的呼叫者處理。

理想的替代方法，上述範例是以攔截*特定*例外狀況，並傳回有意義的值，該例外狀況的內容中。 如果您修改`tryReadAllText`函式，如下所示，`None`有更多的意義：

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

而不是做為全部擷取，此函式會立即正確處理的情況時找不到檔案，並將該意義指派給傳回。 不捨棄任何內容的資訊，或強制呼叫者處理可能不在該點在程式碼相關的案例時，此傳回值可以對應到此錯誤的情況下。

類型，例如`Result<'Success, 'Error>`適用於基本作業不巢狀的方式，而 F # 選擇性型別非常適合做為項目無法傳回時，代表*東西*或*nothing*. 它們不能取代例外狀況，不過，和不應嘗試將例外狀況。 相反地，它們應套用明智地址的例外狀況和錯誤管理原則的特定層面目標的方式。

## <a name="partial-application-and-point-free-programming"></a>部分應用程式和無點的程式設計

F # 支援部分的應用程式，因此，程式的各種方式無端點的樣式。 這可以是有幫助模組內的項目，實作的程式碼重複使用，但它通常不是要公開可公開 （expose） 的項目。 一般情況下，無點的程式設計不本身，作為，而且可以加入重大的認知障礙不沉浸在樣式中的人員。

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>請勿使用部分的應用程式及對公用 Api 中

有一些例外狀況，使用公用 Api 中的部分應用程式會造成混淆的取用者。 通常`let`-F # 程式碼中的繫結的值是**值**，而非**函式值**。 混合在一起，值和函式值可能會導致儲存少數幾行程式碼，但是也會處理一堆認知的額外負荷，尤其是這類結合運算子`>>`撰寫函式。

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>考慮工具產生的影響無點的程式設計

局部調用函式不會標示其引數。 這會有影響的工具。 請考慮下列兩個函式：

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

兩者都是有效的函式，但`funcWithApplication`是局部調用的函式。 當您停留在編輯器中其型別時，您會看到這個：

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

在呼叫位置，Visual Studio 這類的工具中的工具提示不會讓您有意義的資訊，內幕消息`string`和`int`實際代表輸入的類型。

如果您遇到像點免程式碼`funcWithApplication`可公開使用，建議您執行完整的 η 擴充，以便工具可以挑選上有意義的名稱，引數。

此外，偵錯點免程式碼可能相當困難，不可能。 偵錯工具需要依賴繫結至名稱的值 (例如`let`繫結)，因此您可以檢查執行的中間值中途。 當您的程式碼不有任何值，以檢查時，任何偵錯。 在未來，偵錯工具可能會有所演進合成根據先前執行的路徑，這些值，但不是個不錯的主意 hedge 了上*潛在*偵錯功能。

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>請考慮減少內部重複使用在這項技術的部分應用程式

相較於上一點，部分應用程式會是絕佳的工具，以降低應用程式或 API 的更深入的內部資訊內的重複使用。 它可以是單元測試更複雜的 Api，其中未定案通常是太痛苦了處理的實作很有幫助。 例如，下列的程式碼示範如何完成哪些最模擬架構讓您無須在這類架構的外部相依性，而不必了解相關 bespoke API。

例如，請考慮下列解決方案拓撲：

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj` 可能會公開程式碼，像是所示：

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

單元測試`Transactions.doTransaction`在`ImplementationLogic.Tests.fspoj`很簡單：

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

部分套用`doTransaction`使用模擬的內容物件可讓您所有的單元測試中呼叫函式，而不必每次建構的模擬 （mock） 的內容：

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

這項技術應該不通用於您整個程式碼基底，但是它是一個好的方法，以減少重複使用複雜的內部項目和單元測試這些內部項目。

## <a name="access-control"></a>存取控制

F # 提供多個選項[存取控制](../language-reference/access-control.md)、 繼承自.NET 執行階段中可用。 這些不是只用於類型-您也可以使用它們的函式。

* 偏好非`public`類型和成員，直到您需要它們來公開取用。 這樣也可以降低至哪些取用者幾
* 致力於讓您將所有的協助程式功能`private`。
* 請考慮使用`[<AutoOpen>]`helper 函式，如果它們變成許多私用模組上。

## <a name="type-inference-and-generics"></a>型別推斷和泛型

型別推斷可讓您輸入的未定案很多。 在 F # 編譯器自動產生可協助您撰寫更一般的程式碼幾乎不必額外費心與您的組件上。 不過，這些功能不普遍良好。

* 請考慮使用明確的類型，在公用 Api 標記引數名稱，並不依賴類型推斷此。

    原因在於**您**應該控制您的 API，不是編譯器的形狀。 雖然編譯器能夠推斷類型，為您在正常作業，就可以有您的 API 變更的形狀，如果它會依賴內部項目已變更類型。 這可能是您要的結果，但它幾乎肯定會導致下游取用者再也不必處理重大 API 變更。 相反地，如果您明確地控制您的公用 API 的形狀，您可以控制這些重大變更。 以 DDD 術語來說，這可以視為防損毀層。

* 請考慮您的泛型引數來提供有意義的名稱。

    除非您要撰寫真正泛型程式碼，並非專屬於特定的網域，有意義的名稱可以幫助其他程式設計人員了解他們正在處理中的網域。 例如，名為的型別參數`'Document`互動與文件的內容中資料庫讓您更清楚，一般文件類型可接受函式或您正在使用的成員。

* 請考慮使用 PascalCase 的泛型型別參數命名。

    這是一般的方法做事在.NET 中，所以建議您使用 PascalCase 而不是為 snake_case 加上或 camelCase。

最後，自動一般化並不一定對象是剛接觸 F # 或大型的程式碼基底的人是一大福音。 在中使用的一般元件沒有額外的認知。 此外，如果自動一般化的函式不適用於採用不同輸入類型 (let 單獨如果它們要這麼做)，則沒有任何實質就是在該時間點的泛用的好處。 請務必考慮您要撰寫的程式碼會實際從泛型中獲益。

## <a name="performance"></a>效能

F # 值是根據預設，可讓您避免某些 bug （特別是那些包含並行和平行處理原則） 的類別不可變的。 不過，在某些情況下，為了達到最佳的 （或甚至是合理的） 的執行時間或記憶體配置的高效率工作的範圍可能最適合實作使用狀態的就地變化。 這可自由選擇是否搭配 F # 中`mutable`關鍵字。

不過，使用`mutable`F # 中可能會覺得相悖功能的單純性。 這是正常的如果您調整至單純性的期望[參考透明度](https://en.wikipedia.org/wiki/Referential_transparency)。 參考透明度-不純正性-撰寫 F # 函式時的最終目的。 這可讓您在效能關鍵的程式碼的變化型實作覆寫功能的介面。

### <a name="wrap-mutable-code-in-immutable-interfaces"></a>將可變動的程式碼包裝在不可變的介面

為目標的參考透明度，請務必撰寫程式碼不會公開可變動的 underbelly 效能關鍵的函式。 例如，下列程式碼會實作`Array.contains`F # 核心程式庫中的函式：

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

多次呼叫此函式不會變更基礎的陣列，也不會要求您維護中使用它的任何可變動狀態。 即使幾乎每一行程式碼，在其中使用變動時，它是參考透明。

### <a name="consider-encapsulating-mutable-data-in-classes"></a>請考慮將封裝在類別中可變動的資料

前面的範例會使用單一函式，來封裝使用可變動的資料作業。 這不一定能夠以更複雜的資料集。 請考慮下列會設定函式：

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

此程式碼是高效能，但它會公開的呼叫端會負責維護的變動為基礎的資料結構。 這可以包裝在不含基礎的成員可以變更的類別內：

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

`Closure1Table` 封裝基礎的變動為基礎的資料結構，因此未強制執行以維護基礎資料結構的呼叫端。 類別是強大的方式來封裝資料和而不會公開給呼叫者的詳細資料是以變動為基礎的常式。

### <a name="prefer-let-mutable-to-reference-cells"></a>偏好`let mutable`來參考儲存格

參考儲存格可代表值，而不是值本身的參考。 雖然它們可以用於效能關鍵的程式碼，但是它們通常不建議。 參考下列範例：

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

使用參考儲存格現在 「 污染 」 具有來取值 （dereference），並重新參考基礎資料所有後續的程式碼。 請改為考慮`let mutable`:

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

Lambda 運算式的中間的變動的單一點，除了所有其他程式碼，接觸`acc`可以這樣做並無一般需要使用不同的方式`let`-繫結不可變的值。 這會讓您更輕鬆地隨著時間而變更。

## <a name="object-programming"></a>物件的程式設計

F # 提供物件和物件導向 (OO) 概念的完整支援。 雖然許多 OO 概念是功能強大且實用，但並非全部都適合使用。 下列清單提供高層級的 OO 功能的類別上的指導方針。

**請考慮在許多情況下使用這些功能：**

* 點標記法 (`x.Length`)
* 執行個體成員
* 隱含的建構函式
* 靜態成員
* 索引子標記法 (`arr.[x]`)
* 具名和選擇性引數
* 介面和介面實作

**不會送達這些功能的第一次，但請謹慎套用它們何時可方便地解決問題：**

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

* 繼承為基礎的型別階層架構和實作繼承
* Null 和 `Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>偏好撰寫比繼承

[撰寫比繼承](https://en.wikipedia.org/wiki/Composition_over_inheritance)是長久以來的慣用句，良好的 F # 程式碼可以符合。 基本原則是，您不應該公開 （expose） 的基底類別並強制繼承自該基底類別，以取得功能的呼叫端。

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>使用物件運算式實作介面，如果您不需要類別

[物件運算式](../language-reference/object-expressions.md)可讓您實作介面即時，繫結實作的介面值，而不需要這麼做在類別內。 這是很方便，尤其是如果您_只_需要實作介面並不需要完整的類別。

例如，以下是執行中的程式碼[Ionide](http://ionide.io/)提供的程式碼修正動作，如果您已新增一個符號，您還沒有`open`陳述式：

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

因為類別不需要與 Visual Studio 程式碼 API 互動時，物件運算式都是這樣的理想工具。 它們也是單元測試，當您想要去除測試常式的介面，以臨機操作方式的重要依據。

## <a name="type-abbreviations"></a>類型縮寫

[類型縮寫](../language-reference/type-abbreviations.md)是便利的方式來將標籤指派給另一個類型，例如函式簽章或更複雜的類型。 例如，下列別名會將標籤指派給需要哪些技能來定義與計算[CNTK](https://www.microsoft.com/en-us/cognitive-toolkit/)、 深入學習程式庫：

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

`Computation`名稱是便利的方式來表示任何符合函式，它是別名的簽章。 就像這樣使用類型縮寫很方便，而且允許更簡潔的程式碼。

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>請避免使用類型縮寫來代表您的網域

雖然類型縮寫是方便命名函式簽章，但它們可能會造成混淆的情況，當縮寫其他類型。 請考慮這個縮寫：

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

這可能是令人困惑，以多種方式：

* `BufferSize` 不是抽象概念;這是整數的只是另一個名稱。
* 如果`BufferSize`公開在公用 API 中，它可以輕鬆地被錯誤解譯不只是表示`int`。 一般而言，網域類型有多個屬性，而不是基本型別，例如`int`。 這個縮寫違反的假設。
* 大小寫的`BufferSize`(PascalCase) 表示這個型別含有更多資料。
* 此別名並未提供相較於提供具名引數的函式的更的清楚。
* 已編譯的 IL; 的縮寫將沒有資訊清單它只是一個整數，與此別名是編譯時期建構。

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) =
        ...
```

在 [摘要] 類型縮寫就是它們均**不**它們縮寫類型的抽象概念。 在上述範例中，`BufferSize`就`int`實際上與任何其他的資料或從項目以外的型別系統的任何權益`int`已經有。
