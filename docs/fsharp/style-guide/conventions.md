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
# <a name="f-coding-conventions"></a>F# 編碼慣例

以下約定是從使用大型 F# 代碼庫的經驗中制定的。 [好的 F# 代碼的五個原則](index.md#five-principles-of-good-f-code)是每個建議的基礎。 它們與[F# 元件設計指南](component-design-guidelines.md)相關，但適用于任何 F# 代碼，而不僅僅是庫等元件。

## <a name="organizing-code"></a>組織代碼

F# 具有兩種組織代碼的主要方法：模組和命名空間。 這些相似，但確實有以下差異：

* 命名空間編譯為 .NET 命名空間。 模組編譯為靜態類。
* 命名空間始終是頂層。 模組可以是頂級的，可以嵌套在其他模組中。
* 命名空間可以跨多個檔。 模組不能。
* 模組可以使用`[<RequireQualifiedAccess>]`和`[<AutoOpen>]`進行修飾。

以下指南將説明您使用這些準則來組織代碼。

### <a name="prefer-namespaces-at-the-top-level"></a>首選頂層的命名空間

對於任何公共易用代碼，命名空間優先支援頂層模組。 因為它們編譯為 .NET 命名空間，因此它們可消耗來自 C#，沒有問題。

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

僅從 F# 調用時，使用頂級模組可能看起來不同，但對於 C# 消費者，調用方可能會因為必須符合`MyClass``MyCode`該模組的資格而感到驚訝。

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>小心塗抹`[<AutoOpen>]`

構造`[<AutoOpen>]`會污染調用方可用的範圍，而對事物來源的答案是"神奇"。 這不是一件好事。 此規則的一個例外是 F# 核心庫本身（儘管這一事實也有點爭議）。

但是，如果您具有公共 API 的説明器功能，您希望獨立于該公共 API 進行組織，則這樣做會很方便。

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

這樣，您就可以將實現詳細資訊與函數的公共 API 進行乾淨分離，而無需在每次調用協助程式時完全限定協助程式。

此外，在命名空間級別公開擴充方法和運算式產生器可以使用 整齊地表示。 `[<AutoOpen>]`

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>每當`[<RequireQualifiedAccess>]`名稱可能發生衝突或您覺得它有助於可讀性時使用

將`[<RequireQualifiedAccess>]`屬性添加到模組表示可能無法打開模組，並且對模組元素的引用需要顯式限定訪問。 例如，`Microsoft.FSharp.Collections.List`模組具有此屬性。

當模組中的函數和值具有可能與其他模組中的名稱衝突的名稱時，這非常有用。 要求合格的訪問可以大大提高庫的長期可維護性和可進化性。

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>從`open`拓撲上對語句進行排序

在 F#中，聲明的順序很重要，包括與語句一`open`起。 這與 C# 不同，C#`using``using static`的影響與檔中這些語句的順序無關。

在 F# 中，打開到作用域中的元素可能會隱藏其他已經存在的元素。 這意味著重新排序`open`語句可能會更改代碼的含義。 因此，不建議對所有`open`語句進行任何任意排序（例如，以 Alpha 數位方式排序），以免生成您可能期望的不同行為。

相反，我們建議您[按拓撲分類](https://en.wikipedia.org/wiki/Topological_sorting)它們;也就是說，按定義系統`open`_圖層_的順序對語句進行排序。 也可以考慮在不同的拓撲層內進行字母數位排序。

例如，下面是 F# 編譯器服務公共 API 檔的拓撲排序：

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

請注意，分行符號將拓撲圖層分開，之後將按字母數位對每一層進行排序。 這樣可以乾淨地組織代碼，而不會意外地隱藏值。

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>使用類包含具有副作用的值

初始化值很多時候會產生副作用，例如將上下文具現化到資料庫或其他遠端資源。 在模組中初始化此類內容並將其用於後續函數是很有誘惑力的：

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

由於幾個原因，這通常是一個壞主意：

首先，應用程式佈建被推送到 代碼庫中`dep1`， `dep2` 這在較大的代碼庫中很難維護。

其次，靜態初始化資料不應包括不安全的執行緒值（如果元件本身將使用多個執行緒）。 這顯然被`dep3`違反。

最後，模組初始化編譯為整個編譯單元的靜態建構函式。 如果該模組中的允許綁定值初始化中出現任何錯誤，則該初始化將表現為`TypeInitializationException`然後緩存整個應用程式的存留期。 這可能很難診斷。 通常有一個內部異常，你可以嘗試推理，但如果沒有，那麼沒有告訴根本原因是什麼。

相反，只需使用簡單類來保存依賴項：

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member _.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member _.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

這支援以下功能：

1. 將任何從屬狀態推送到 API 本身之外。
2. 配置現在可以在 API 之外完成。
3. 從屬值的初始化錯誤不太可能表現為`TypeInitializationException`。
4. API 現在更易於測試。

## <a name="error-management"></a>錯誤管理

大型系統中的錯誤管理是一項複雜而細緻的工作，在確保系統具有容錯性和良好行為方面沒有銀彈。 以下指南應為導航此困難空間提供指導。

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>在域固有的類型中表示錯誤案例和非法狀態

使用["歧視聯合"，F#](../language-reference/discriminated-unions.md)使您能夠在類型系統中表示錯誤的程式狀態。 例如：

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

在這種情況下，有三種已知方式從銀行帳戶提取資金可能會失敗。 每個錯誤案例都以類型表示，因此可以在整個程式中安全地處理。

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

通常，如果可以對域中某些內容可能**失敗**的不同方式進行建模，則錯誤處理代碼不再被視為除常規程式流之外必須處理的內容。 它只是正常程式流的一部分，不被認為是**例外**。 這有兩個主要好處：

1. 隨著域隨時間的變化而更易於維護。
2. 錯誤案例更易於單元測試。

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>當無法用類型表示錯誤時，請使用異常

並非所有錯誤都可以在問題域中表示。 這些類型的故障在性質上*是例外*的，因此能夠提高和捕獲 F# 中的異常。

首先，建議您閱讀[例外設計指南](../../standard/design-guidelines/exceptions.md)。 這些也適用于 F#。

F# 中用於引發異常的主要構造應考慮以下首選項順序：

| 函式 | 語法 | 目的 |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | 使用指定的`System.ArgumentNullException`參數名稱引發 a。 |
| `invalidArg` | `invalidArg "argumentName" "message"` | 使用指定的`System.ArgumentException`參數名稱和消息引發 。 |
| `invalidOp` | `invalidOp "message"` | 使用指定`System.InvalidOperationException`的消息引發 a。 |
|`raise`| `raise (ExceptionType("message"))` | 用於引發異常的通用機制。 |
| `failwith` | `failwith "message"` | 使用指定`System.Exception`的消息引發 a。 |
| `failwithf` | `failwithf "format string" argForFormatString` | 使用格式`System.Exception`字串及其輸入確定的消息引發 。 |

使用`nullArg` `invalidArg` ，`invalidOp`並作為投擲`ArgumentNullException`的機制，`ArgumentException`並在`InvalidOperationException`適當時使用 。

通常`failwith`應避免`failwithf`和 函數，因為它們會引發基`Exception`類型，而不是特定的異常。 根據[例外設計指南](../../standard/design-guidelines/exceptions.md)，您希望在可以時提出更具體的異常。

### <a name="using-exception-handling-syntax"></a>使用異常處理語法

F# 通過`try...with`語法支援異常模式：

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

如果要保持代碼整潔，在面對模式匹配的異常時要執行的功能可能會有點棘手。 處理這種情況的一種方法是使用[活動模式](../language-reference/active-patterns.md)作為將圍繞錯誤案例的功能分組具有異常本身的方法。 例如，您可能正在使用 API，當它引發異常時，該 API 會將有價值的資訊包含在異常中繼資料中。 在某些情況下，在活動模式內展開捕獲的異常正文中的有用值並返回該值可能會有所説明。

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>請勿使用單體錯誤處理來替換異常

異常在函數式程式設計中被視為一些禁忌。 事實上，異常會侵犯純度，因此可以放心地考慮它們不太有效。 但是，這忽略了代碼必須運行的位置，並且可能發生執行階段錯誤。 通常，編寫代碼時假定大多數事物既不是純的也不是完全的，以儘量減少令人不快的意外。

在 .NET 運行時和整個跨語言生態系統中的相關性和適當性方面，必須考慮異常的以下核心優勢/方面：

1. 它們包含詳細的診斷資訊，這在調試問題時非常有用。
2. 運行時和其他 .NET 語言都很好地理解它們。
3. 與通過臨時實現語義的某些子集來*避免*異常的代碼相比，它們可以減少重要的樣板。

第三點至關重要。 對於不處理非大型複雜操作，不使用異常可能會導致處理這樣的結構：

```fsharp
Result<Result<MyType, string>, string list>
```

這很容易導致脆弱的代碼，如模式匹配的"字串類型"錯誤：

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

此外，對於返回"更好"類型的"簡單"函數的渴望，可以接受任何異常是很有誘惑力的：

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

遺憾的是，`tryReadAllText`可以基於檔案系統上可能發生的無數事情引發大量異常，並且此代碼會丟棄有關環境中實際出錯的任何資訊。 如果使用此代碼類型替換此代碼，則返回"字串鍵入"錯誤訊息分析：

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

將異常物件本身放在建構函式中`Error`只會強制您在調用網站而不是函數中正確處理異常類型。 這樣做可以有效地創建已檢查的異常，這些異常作為 API 的調用方處理起來非常不有趣。

上述示例的一個很好的替代方法是在該異常上下文中捕獲*特定*異常並返回有意義的值。 如果修改函數`tryReadAllText`如下所示，`None`則具有更多含義：

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

現在，當找不到檔並將該含義分配給返回時，此函數將正確處理案例，而不是充當"全部捕獲"功能。 此傳回值可以映射到該錯誤情況，同時不會放棄任何上下文資訊或強制調用方處理代碼中此時可能不相關的案例。

類型（如`Result<'Success, 'Error>`適用于未嵌套的基本操作）和 F# 可選類型非常適合表示某些內容可以返回*或**什麼都不*返回時。 但是，它們不是異常的替換，不應用於嘗試替換異常。 相反，應明智地應用它們，以有針對性的方式處理異常和錯誤管理政策的具體方面。

## <a name="partial-application-and-point-free-programming"></a>部分應用和無點程式設計

F# 支援部分應用程式，因此，以各種方式以無點樣式進行程式設計。 這有利於模組內的代碼重用或某些內容的實現，但這不是公開的內容。 一般來說，無點程式設計本身並不是一種美德，它可以為不沉浸于這種風格的人增加一個重大的認知障礙。

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>請勿在公共 API 中使用部分應用程式和咖喱

除了很少的情況外，在公共 API 中使用部分應用程式可能會令消費者感到困惑。 通常，F#`let`代碼中的綁定值是**值**，而不是**函數值**。 將值和函數值混合在一起可以節省少量程式碼，以換取相當多的認知開銷，特別是如果與組合函數等`>>`運算子結合使用時。

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>考慮無點程式設計的工具含義

庫瑞德函數不標記其參數。 這具有工具含義。 請考慮以下兩個函數：

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

兩者都是有效的函數，`funcWithApplication`但都是一個咖喱函數。 當您在編輯器中懸停在它們的類型上時，您將看到：

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

在呼叫網站，Visual Studio 等工具工具提示不會為您提供有關`string`和`int`輸入類型實際表示的內容的有意義的資訊。

如果您遇到這樣的`funcWithApplication`無點代碼是公共易用的，建議執行完全 +擴展，以便工具可以獲取有意義的參數名稱。

此外，調試無點代碼可能具有挑戰性，如果不是不可能的話。 調試工具依賴于綁定到名稱的值（例如綁定`let`），以便在執行中途檢查中間值。 當代碼沒有要檢查的值時，將沒有任何要調試的值。 將來，調試工具可能會根據以前執行的路徑來合成這些值，但最好對*潛在的*調試功能進行對沖。

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>將部分應用視為減少內部樣板的技術

與前一點不同，部分應用程式是減少應用程式內部的樣板或 API 的深層內部的絕妙工具。 對於單元測試更複雜的 API 的實現很有説明，其中樣板通常需要處理。 例如，以下代碼演示如何完成大多數類比框架所賦予您的內容，而無需對此類框架進行外部依賴，並且必須學習相關的定制 API。

例如，請考慮以下解決方案地形：

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj`可能會公開代碼，例如：

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member _.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

單元`ImplementationLogic.Tests.fsproj`測試`Transactions.doTransaction`非常簡單：

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

使用類比`doTransaction`上下文物件進行部分應用允許您在所有單元測試中調用函數，而無需每次都構造類比上下文：

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

此技術不應普遍應用於整個代碼庫，但它是減少複雜內部和單元測試這些內部的樣板的好方法。

## <a name="access-control"></a>存取控制

F# 具有多個[存取控制](../language-reference/access-control.md)選項，從 .NET 運行時中可用的選項繼承。 這些不僅可用於類型 - 您也可以將它們用於函數。

* 首選非`public`類型和成員，直到您需要它們是公共消耗品。 這也最大限度地減少了消費者對之的耦合。
* 努力保持所有説明器的功能`private`。
* 請考慮在説明器`[<AutoOpen>]`函數的專用模組上使用這些函數（如果它們變為大量）。

## <a name="type-inference-and-generics"></a>型別推斷和泛型

型別推斷可以節省您輸入大量樣板。 F# 編譯器中的自動泛化可以説明您編寫更通用的代碼，而您幾乎不需要額外的工作。 但是，這些功能並非普遍良好。

* 請考慮在公共 API 中標記具有顯式類型的參數名稱，並且不要為此依賴類型推斷。

    原因是**您應該**控制 API 的形狀，而不是編譯器。 儘管編譯器可以出色地推斷類型，但如果它所依賴的內部類型已更改，則 API 的形狀可能會發生變化。 這可能是你想要的，但它幾乎肯定會導致一個突破的API更改，然後下游消費者將不得不處理。 相反，如果您顯式控制公共 API 的形狀，則可以控制這些重大更改。 用 DDD 術語來說，這可以被視為反腐敗層。

* 請考慮為泛型參數指定一個有意義的名稱。

    除非您正在編寫不特定于特定域的真正通用代碼，否則有意義的名稱可以説明其他程式師瞭解他們正在處理的域。 例如，在與文檔資料庫交互的`'Document`上下文中命名的類型參數使正在使用的函數或成員可以接受通用文件類型更加清晰。

* 請考慮使用 PascalCase 命名泛型型別參數。

    這是在 .NET 中執行操作的一般方法，因此建議您使用 PascalCase 而不是snake_case或駱駝Case。

最後，對於 F# 或大型代碼庫的新增人員而言，自動泛化並不總是一個福音。 使用萬用群組件存在認知開銷。 此外，如果自動通用化函數不用於不同的輸入類型（更不用說它們打算用作此類函數），那麼在那個時間點，它們是泛型函數沒有實際的好處。 始終考慮您編寫的代碼是否實際上將受益于泛型。

## <a name="performance"></a>效能

### <a name="prefer-structs-for-small-data-types"></a>首選小型資料類型的結構

使用結構（也稱為數值型別）通常會導致某些代碼的性能更高，因為它通常避免分配物件。 但是，結構並不總是一個"更快"按鈕：如果結構中的資料大小超過 16 個位元組，則複製資料通常會導致比使用參考型別花費更多的 CPU 時間。

要確定是否應使用結構，請考慮以下條件：

- 如果資料的大小為 16 位元組或更小。
- 如果運行程式中的記憶體中可能有許多此類資料類型駐留在記憶體中。

如果應用第一個條件，通常應使用結構。 如果兩者都適用，您幾乎總是應該使用結構。 可能在某些情況下，應用前面的條件，但使用結構並不比使用參考型別更好或更差，但它們可能很少見。 但是，在進行這樣的更改時，始終要衡量，而不是根據假設或直覺行事，這一點很重要。

#### <a name="prefer-struct-tuples-when-grouping-small-value-types"></a>在分組小數值型別時，首選結構組合

請考慮以下兩個函數：

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

當您使用基準資料測試控管（如[基準點網](https://benchmarkdotnet.org/)）對這些函數進行基準測試時，您會發現使用`runWithStructTuple`結構元數的函數運行速度要快 40%，並且不分配記憶體。

但是，這些結果並不總是在您自己的代碼中如此。 如果將函數標記為`inline`，使用參考元數的代碼可能會獲得一些額外的優化，或者分配的代碼可以簡單地進行優化。 您應該始終在績效方面衡量結果，並且絕不基於假設或直覺操作。

#### <a name="prefer-struct-records-when-the-data-type-is-small"></a>資料類型較小時更喜歡結構記錄

前面描述的經驗法則也適用于[F# 記錄類型](../language-reference/records.md)。 請考慮處理它們的以下資料類型和函數：

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

這與前面的元組代碼類似，但這次示例使用記錄和內聯內建函式。

當您使用基準資料測試控管（如[基準點網](https://benchmarkdotnet.org/)）對這些函數進行基準測試時，您會發現`processStructPoint`運行速度接近 60%，並且在託管堆上不分配任何內容。

#### <a name="prefer-struct-discriminated-unions-when-the-data-type-is-small"></a>在資料類型較小時，首選結構區分結合

以前關於具有結構元數和記錄的表現的觀察也適用于[F_ 歧視聯盟](../language-reference/discriminated-unions.md)。 請考慮下列程式碼：

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

為域建模定義像這樣的單一案例"歧視聯合"很常見。 當您使用基準資料測試控管（如[基準點網](https://benchmarkdotnet.org/)）對這些函數進行基準測試時，您會發現`structReverseName`運行速度比`reverseName`小字串快 25%。 對於大字串，兩者執行大致相同。 因此，在這種情況下，最好使用結構。 如前所述，始終根據假設或直覺進行測量和操作。

儘管前面的示例顯示結構歧視聯合產生了更好的性能，但建模域時通常具有較大的"歧視聯合"。 如果較大的資料類型根據它們的操作進行結構，則它們可能無法很好地執行，因為可能涉及更多的複製。

### <a name="functional-programming-and-mutation"></a>函數程式設計和突變

預設情況下，F# 值是不可變的，這允許您避免某些類 bug（尤其是涉及併發和並行性的錯誤類）。 但是，在某些情況下，為了實現執行時間或記憶體分配的最佳（甚至合理）效率，最好使用就地狀態突變來實現工作跨度。 這在加入宣告的基礎上是可能的，F# 與`mutable`關鍵字。

`mutable`在 F# 中使用可能會感覺與功能純度不一致。 這是可以理解的，但無處不在的功能純度可能與性能目標相悖。 一種妥協是封裝突變，這樣調用方就不必關心調用函數時會發生什麼。 這允許您通過基於突變的實現為性能關鍵代碼編寫功能介面。

#### <a name="wrap-mutable-code-in-immutable-interfaces"></a>在不可變介面中包裝可變代碼

以參考透明度為目標，編寫不公開性能關鍵函數可變下層代碼至關重要。 例如，以下代碼在`Array.contains`F# 核心庫中實現函數：

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

多次調用此函數不會更改基礎陣列，也不要求您在使用該函數時保持任何可變狀態。 它具有參考性透明，即使其中幾乎每行代碼都使用突變。

#### <a name="consider-encapsulating-mutable-data-in-classes"></a>考慮在類中封裝可變數據

前面的示例使用單個函數來使用可變數據封裝操作。 對於更複雜的資料集，這並不總是足夠。 請考慮以下函數集：

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

此代碼是執行的，但它公開調用方負責維護的基於突變的資料結構。 這可以包裝在類中，而沒有可以更改的基礎成員：

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

`Closure1Table`封裝基於突變的基礎資料結構，從而不強制調用方維護基礎資料結構。 類是封裝基於突變的資料和常式而不向調用方公開詳細資訊的強大方法。

#### <a name="prefer-let-mutable-to-reference-cells"></a>更喜歡`let mutable`引用儲存格

引用儲存格是表示對值的引用而不是值本身的一種方式。 儘管它們可用於性能關鍵型代碼，但不建議它們。 請考慮下列範例：

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

使用引用儲存格現在"污染"所有後續代碼，必須取消引用和重新引用基礎資料。 相反，請考慮`let mutable`：

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

除了 lambda 運算式中間的單點突變之外，所有其他涉及`acc`的代碼都可以以與正常`let`綁定不可變值的使用沒有什麼不同的方式執行此操作。 這將使隨著時間的推移更容易改變。

## <a name="object-programming"></a>物件程式設計

F# 完全支持對象和麵向物件 （OO） 概念。 儘管許多 OO 概念功能強大且有用，但並非所有概念都是理想的使用。 以下清單提供了有關高級別 OO 功能類別的指導。

**考慮在許多情況下使用這些功能：**

* 點標記法`x.Length`（ ）
* 實例成員
* 隱式建構函式
* 靜態成員
* 索引子標記法`arr.[x]`（ ）
* 命名和可選參數
* 介面和介面實現

**不要首先訪問這些功能，但在它們方便解決問題時，請明智地應用它們：**

* 方法多載
* 封裝的可變數據
* 類型上的運算子
* 自動屬性
* 實施`IDisposable`和`IEnumerable`
* 類型擴展
* 事件
* 結構
* 委派
* 列舉

**通常避免這些功能，除非您必須使用它們：**

* 基於繼承的類型層次結構和實現繼承
* 空和`Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>首選組合而不是繼承

[繼承的組成](https://en.wikipedia.org/wiki/Composition_over_inheritance)是一個長期存在的習慣用法，好的 F# 代碼可以遵循。 基本原則是，不應公開基類，並強制調用方從該基類繼承以獲取功能。

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>如果不需要類，請使用物件運算式實現介面

[物件運算式](../language-reference/object-expressions.md)允許您動態實現介面，將實現的介面綁定到值，而無需在類內部執行此操作。 這很方便，特別是當您_只需要_實現介面，並且不需要完整類時。

例如，如果您添加了沒有用於以下語句的`open`符號，則下面是在[Ionide](http://ionide.io/)中運行的代碼，以提供代碼修復操作：

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

由於與 Visual Studio 代碼 API 交互時不需要類，因此物件運算式是理想的工具。 當您想要以臨時方式與測試常式建立介面時，它們對於單元測試也很有價值。

## <a name="consider-type-abbreviations-to-shorten-signatures"></a>考慮類型縮寫以縮短簽名

[類型縮寫](../language-reference/type-abbreviations.md)是將標籤分配給另一種類型（如函數簽名或更複雜的類型）的便捷方法。 例如，以下別名將標籤分配給使用[CNTK（](https://docs.microsoft.com/cognitive-toolkit/)深度學習庫）定義計算所需的內容：

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

該`Computation`名稱是表示與它所混疊的簽名匹配的任何函數的便捷方式。 使用像這樣的類型縮寫很方便，並允許更簡潔的代碼。

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>避免使用類型縮寫來表示您的域

儘管類型縮寫對於為函數簽名指定名稱很方便，但當縮寫其他類型時，它們可能會令人困惑。 請考慮此縮寫：

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

這可以通過多種方式令人困惑：

* `BufferSize`不是抽象的;不是抽象的。它只是整數的另一個名稱。
* 如果在`BufferSize`公共 API 中公開，很容易被誤解為不僅僅是`int`。 通常，欄位型別具有多個屬性，並且不是基元類型，如`int`。 此縮寫違反了這一假設。
* （PascalCase） 的`BufferSize`套管意味著此類型包含更多資料。
* 與向函數提供具名引數相比，此別名的清晰度不會提高。
* 縮寫不會在編譯的 IL 中體現;因此，縮寫不會以 IL 表示。它只是一個整數，這個別名是一個編譯時構造。

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

總之，類型縮寫的陷阱是，**它們不是**對縮寫類型的抽象。 在前面的示例中，`BufferSize`只是一個`int`封面，沒有額外的資料，也沒有從類型系統的任何好處，除了`int`已經擁有。

使用類型縮寫來表示域的另一種方法是使用單一案例區分結合。 前面的示例可以建模如下：

```fsharp
type BufferSize = BufferSize of int
```

如果編寫的代碼按`BufferSize`及其基礎值運行，則需要構造一個代碼，而不是傳遞任何任意整數：

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

這降低了錯誤地將任意整數傳遞到`send`函數的可能性，因為調用方必須在調用函數之前構造一個`BufferSize`類型來包裝值。
