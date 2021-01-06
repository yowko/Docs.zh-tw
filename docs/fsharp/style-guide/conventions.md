---
title: F# 編碼慣例
description: '瞭解撰寫 F # 程式碼時的一般指導方針和慣用語。'
ms.date: 01/5/2021
ms.openlocfilehash: e69ceb2f3c37404ca8d8ed972f985340e62ecb59
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938685"
---
# <a name="f-coding-conventions"></a>F# 編碼慣例

下列慣例是從使用大型 F # 基底的經驗來制定的。 [良好 F # 程式碼的五個準則](index.md#five-principles-of-good-f-code)是每個建議的基礎。 它們與 [f # 元件設計指導方針](component-design-guidelines.md)相關，但適用于任何 f # 程式碼，而不只是程式庫之類的元件。

## <a name="organizing-code"></a>組織程式碼

F # 提供兩種主要的方式來組織程式碼：模組和命名空間。 這些都很類似，但有下列差異：

* 命名空間會編譯為 .NET 命名空間。 模組會編譯為靜態類別。
* 命名空間一律為最上層。 模組可以是最上層的，也可以嵌套在其他模組內。
* 命名空間可以橫跨多個檔案。 模組無法。
* 模組可以使用和裝飾 `[<RequireQualifiedAccess>]` `[<AutoOpen>]` 。

下列指導方針可協助您使用這些程式碼來組織程式碼。

### <a name="prefer-namespaces-at-the-top-level"></a>偏好最上層的命名空間

對於任何公開取用的程式碼，命名空間都優先于最上層的模組。 因為它們會編譯為 .NET 命名空間，所以可以從 c # 取用，而不會有任何問題。

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

使用最上層模組可能不會在從 F # 呼叫時出現不同的情況，但針對 c # 取用者，呼叫者可能會因為必須符合此模組而感到驚訝 `MyClass` `MyCode` 。

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>謹慎申請 `[<AutoOpen>]`

此 `[<AutoOpen>]` 結構可會污染可供呼叫端使用的範圍，而發生問題的答案是「魔術」。 這不是件好事。 這項規則的例外狀況是 F # 核心程式庫本身 (但這項事實也有點有爭議的) 。

但是，如果您有想要與公用 API 分開組織的公用 API 的協助程式功能，這是一個便利的方式。

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

這可讓您將函式公用 API 中的實作詳細資料完全分開，而不需要在每次呼叫時都完整限定協助程式。

此外，您可以在命名空間層級公開擴充方法和運算式產生器，以整齊地表示 `[<AutoOpen>]` 。

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>`[<RequireQualifiedAccess>]`在名稱可能發生衝突時使用，或者您覺得它有助於提高可讀性

將 `[<RequireQualifiedAccess>]` 屬性新增至模組，表示模組可能無法開啟，而且模組的元素參考需要明確的存取權。 例如， `Microsoft.FSharp.Collections.List` 模組有這個屬性。

當模組中的函式和值有可能與其他模組中的名稱衝突的名稱時，這非常有用。 需要限定存取權可能會大幅增加資源庫的長期維護和 evolvability。

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>排序 `open` 語句拓撲

在 F # 中，宣告的順序很重要，包括 `open` 語句。 這與 c # 不同，它的效果與檔案 `using` `using static` 中這些語句的順序無關。

在 F # 中，開啟至範圍的專案可以遮蔽其他已經存在的專案。 這表示重新排列 `open` 語句可以改變程式碼的意義。 因此，所有語句的任意排序 (例如 `open` ，不建議使用順序) ，以免您產生可能預期的不同行為。

相反地，我們建議您將它們排序[拓撲](https://en.wikipedia.org/wiki/Topological_sorting);也就是說，依照您的系統層級定義順序來排序您的 `open` 語句。  也可以考慮在不同拓撲層級內進行英數位元排序。

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

請注意，分行符號會分隔拓撲層，之後每個圖層會以順序的方式排序。 這會完全組織程式碼，而不會不小心地遮蔽值。

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>使用類別包含具有副作用的值

初始化某個值時，有許多次可能會有副作用，例如將內容具現化至資料庫或其他遠端資源。 將模組中的這類專案初始化是很吸引人，並在後續的函式中使用：

```fsharp
// This is bad!
module MyApi =
    let dep1 = File.ReadAllText "/Users/<name>/connectionstring.txt"
    let dep2 = Environment.GetEnvironmentVariable "DEP_2"

    let private r = Random()
    let dep3() = r.Next() // Problematic if multiple threads use this

    let function1 arg = doStuffWith dep1 dep2 dep3 arg
    let function2 arg = doSutffWith dep1 dep2 dep3 arg
```

這通常不是個好主意，原因如下：

首先，應用程式設定會使用和推送至程式碼基底 `dep1` `dep2` 。 這在較大的程式碼基底中很難維護。

第二，如果您的元件本身會使用多個執行緒，則靜態初始化的資料不應該包含不安全線程的值。 這顯然是違反的 `dep3` 。

最後，模組初始化會編譯成整個編譯單位的靜態函式。 如果該模組中的 let 系結值初始化發生任何錯誤，則會將它列為， `TypeInitializationException` 然後針對應用程式的整個存留期進行快取。 這可能很難診斷。 通常您可以嘗試的內部例外狀況，但如果沒有，則不會告訴根本原因為何。

相反地，只要使用簡單的類別來保存相依性即可：

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member _.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member _.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

這會啟用下列功能：

1. 將任何相依狀態推送至 API 本身之外。
2. 您現在可以在 API 外部進行設定。
3. 相依值的初始化錯誤不太可能會被資訊清單為 `TypeInitializationException` 。
4. API 現在更容易測試。

## <a name="error-management"></a>錯誤管理

大型系統中的錯誤管理是一項複雜且差別細微的工作，而且沒有任何銀級的專案可確保您的系統具有容錯能力且運作正常。 下列指導方針應提供導覽此困難空間的指引。

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>代表您的網域內建類型中的錯誤案例和不合法的狀態

使用 [差異](../language-reference/discriminated-unions.md)聯集時，F # 讓您能夠在類型系統中代表錯誤的程式狀態。 例如：

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

在此情況下，有三種已知方式可從銀行帳戶提款 money。 每個錯誤案例都是以類型表示，因此可在整個程式中安全地處理。

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn $"Successfully withdrew %f{am}"
    | InsufficientFunds balance -> printfn $"Failed: balance is %f{balance}"
    | CardExpired expiredDate -> printfn $"Failed: card expired on {expiredDate}"
    | UndisclosedFailure -> printfn "Failed: unknown"
```

一般情況下，如果您可以針對在網域中可能會 **失敗** 的不同方式建立模型，則錯誤處理常式代碼不會再被視為您必須在一般程式流程中處理的某些專案。 它只是一般程式流程的一部分，不是 **例外** 狀況。 這有兩個主要優點：

1. 當您的網域隨著時間變更時，更容易維護。
2. 錯誤案例更容易進行單元測試。

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>當錯誤無法以類型表示時，請使用例外狀況

並非所有錯誤都可以在問題網域中表示。 這類錯誤本質上很 *例外* ，因此能夠在 F # 中引發和攔截例外狀況。

首先，建議您閱讀 [例外狀況設計指導方針](../../standard/design-guidelines/exceptions.md)。 這些也適用于 F #。

F # 中可用來引發例外狀況的主要結構，應該依照下列喜好設定順序來考慮：

| 函數 | 語法 | 目的 |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | `System.ArgumentNullException`使用指定的引數名稱引發。 |
| `invalidArg` | `invalidArg "argumentName" "message"` | `System.ArgumentException`使用指定的引數名稱和訊息來引發。 |
| `invalidOp` | `invalidOp "message"` | `System.InvalidOperationException`使用指定的訊息引發。 |
|`raise`| `raise (ExceptionType("message"))` | 擲回例外狀況的一般用途機制。 |
| `failwith` | `failwith "message"` | `System.Exception`使用指定的訊息引發。 |
| `failwithf` | `failwithf "format string" argForFormatString` | `System.Exception`使用格式字串及其輸入所決定的訊息來引發。 |

使用 `nullArg` 、 `invalidArg` 和 `invalidOp` 做為要擲回的機制 `ArgumentNullException` `ArgumentException` 和 `InvalidOperationException` 適當時機。

和函式 `failwith` `failwithf` 通常應該避免，因為它們會引發基底 `Exception` 類型，而不是特定的例外狀況。 根據例外狀況 [設計指導方針](../../standard/design-guidelines/exceptions.md)，您會想要在可以的情況下引發更明確的例外狀況。

### <a name="use-exception-handling-syntax"></a>使用例外狀況處理語法

F # 透過語法支援例外狀況模式 `try...with` ：

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

如果您想要讓程式碼保持乾淨，請在發生例外狀況的情況時，協調要執行的功能。 處理這種情況的其中一種方法，就是使用 [主動模式](../language-reference/active-patterns.md) ，將發生例外狀況本身的功能分組。 例如，您可能會使用 API，當它擲回例外狀況時，會將寶貴的資訊包含在例外狀況中繼資料中。 在主動模式內的已攔截例外狀況內，解除包裝有用的值，並傳回該值，在某些情況下可能會很有説明。

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>請勿使用 monadic 錯誤處理來取代例外狀況

例外狀況通常會在功能程式設計中視為 taboo。 事實上，例外狀況違反了純度，因此可以放心地將它們視為無法正常運作。 不過，這會忽略程式碼必須執行的實際情況，而且可能發生執行階段錯誤。 一般來說，撰寫程式碼時假設大部分的專案都不是單純也不是總計，以將不愉快的意外情況降到最低。

請務必考慮下列與 .NET 執行時間和跨語言生態系統中的相關性和」適當性相關的例外狀況核心優勢/層面：

1. 它們包含詳細的診斷資訊，在對問題進行偵錯工具時很有説明。
2. 執行時間和其他 .NET 語言都能充分瞭解它們。
3. 相 *較于在* 特定的程式碼中執行部分部分的部分，它們可以減少重複使用的程式碼。

第三個點很重要。 針對重要複雜的作業，無法使用例外狀況可能會導致處理如下的結構：

```fsharp
Result<Result<MyType, string>, string list>
```

這可能會導致「stringly 型別」錯誤的模式比對等脆弱的程式碼：

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

此外，對於會傳回 "更好" 類型的 "simple" 函式，忍受任何例外狀況可能很吸引人：

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

可惜的是， `tryReadAllText` 可能會擲回許多例外狀況，而這些例外狀況可能會發生在檔案系統上，而此程式碼會捨棄您的環境中可能發生錯誤的任何資訊。 如果您以結果型別取代此程式碼，則會回到「stringly 型別」的錯誤訊息剖析：

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

然後，將例外狀況物件本身放在函式中， `Error` 就會強制您在呼叫位置（而不是在函式中）適當處理例外狀況類型。 這麼做可有效地建立已檢查的例外狀況，這些例外狀況是 unfun 來處理成為 API 的呼叫者。

上述範例的一個好方法是攔截 *特定* 的例外狀況，並在該例外狀況的內容中傳回有意義的值。 如果您依照下列方式修改函式 `tryReadAllText` ， `None` 有更多意義：

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

這個函式現在會在找不到檔案時適當地處理案例，並將該意義指派給傳回，而不是全部運作。 這個傳回值可以對應至該錯誤案例，而不會捨棄任何內容相關資訊，或強制呼叫端處理在程式碼中該點可能不相關的案例。

等型別 `Result<'Success, 'Error>` 適用于不會進行嵌套的基本作業，而且 F # 選用型別最適合用來表示何時有可能傳回 *某事物* 或 *任何* 東西。 不過，它們不是例外狀況的取代，而且不應該用於嘗試取代例外狀況。 相反地，應謹慎套用，以依目標的方式處理例外狀況和錯誤管理原則的特定層面。

## <a name="partial-application-and-point-free-programming"></a>部分應用程式和無點程式設計

F # 支援部分的應用程式，因此，您可以使用不同的方式來以無點的樣式進行程式設計。 這對於在模組內重複使用程式碼或執行某些工作很有説明，但它並不是公開的內容。 一般來說，無點程式設計並不是本身的作用，而且可以為不是可以沉浸在樣式中的人員新增重要的認知屏障。

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>請勿在公用 Api 中使用部分應用程式和 currying

只要稍微例外，在公用 Api 中使用部分應用程式可能會對取用者造成混淆。 `let`F # 程式碼中的系結值通常是 **值**，而不是 **函數值**。 將值與函式值混合在一起可能會導致在 exchange 中儲存少量的程式碼，以達相當多的認知負擔，特別是當結合運算子（例如） `>>` 來撰寫函數時。

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>考慮無點程式設計的工具含意

擴充函式不會標記其引數。 這會影響工具。 請考慮下列兩個功能：

```fsharp
let func name age =
    printfn $"My name is {name} and I am %d{age} years old!"

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

兩者都是有效的函式，但 `funcWithApplication` 是一個局部函數。 當您將滑鼠停留在編輯器中的類型上時，就會看到：

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

在呼叫位置，工具（例如 Visual Studio）中的工具提示會提供您類型簽章，但因為沒有定義任何名稱，所以不會顯示名稱。 名稱對於良好的 API 設計很重要，因為它們可協助呼叫端更清楚瞭解 API 背後的意義。 在公用 API 中使用無點程式碼，可讓呼叫端更難理解。

如果您遇到可公開取用的無點程式碼 `funcWithApplication` ，則建議進行完整η展開，讓工具可以針對引數使用有意義的名稱。

此外，如果不可能，則偵錯工具的程式碼可能會很困難。 偵錯工具依賴系結至名稱的值 (例如，系結 `let`) ，以便您可以在執行時檢查中繼值。 當您的程式碼沒有要檢查的值時，就不會有任何要進行的偵錯工具。 未來，偵錯工具可能會發展，以根據先前執行的路徑來合成這些值，但不建議您在 *可能* 的偵錯工具上建立您的理由。

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>將部分應用程式視為減少內部重複使用的技術

相較于上一個重點，部分應用程式是一項絕佳的工具，可減少應用程式內的重複使用或更深入的 API 內部。 對於執行更複雜 Api 的單元測試而言很有説明，因為未定案通常是很棘手的問題。 例如，下列程式碼會示範如何完成大部分的模擬架構，而不需要對這類架構進行外部相依性，以及瞭解相關的定制 API。

例如，請考慮下列解決方案拓撲：

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

中的單元測試 `Transactions.doTransaction` `ImplementationLogic.Tests.fsproj` 很簡單：

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

部分套用 `doTransaction` 模擬內容物件可讓您在所有單元測試中呼叫函式，而不需要每次都要建立模擬內容：

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

這項技術不應該通用地套用至整個程式碼基底，但這是減少複雜內部和單元測試這些內部的好方法。

## <a name="access-control"></a>存取控制

F # 有多個 [存取控制](../language-reference/access-control.md)選項，可從 .net 執行時間中的可用內容繼承。 這些都不只適用于型別，您也可以將它們用於函數。

* 偏好非 `public` 類型和成員，直到您需要它們可供公開取用為止。 這也可減少取用者的需求。
* 努力保留所有協助程式功能 `private` 。
* 請考慮在 helper 函式的 `[<AutoOpen>]` 私用模組上使用，如果它們變成很多。

## <a name="type-inference-and-generics"></a>型別推斷和泛型

型別推斷可以節省您輸入許多未定案的內容。 F # 編譯器中的自動一般化可協助您撰寫更多的一般程式碼，幾乎不需要額外投入您的部分。 不過，這些功能並不普遍。

* 請考慮在公用 Api 中以明確類型標記引數名稱，而不依賴此的型別推斷。

    這是因為 **您** 應該控制 API 的圖形，而不是編譯器的形式。 雖然編譯器可以在推斷類型時進行精確的工作，但如果它所依賴的本質具有變更類型，則您的 API 圖形可能會變更。 這可能是您想要的結果，但它幾乎會產生突破性的 API 變更，下游取用者就必須處理這些變更。 相反地，如果您明確控制公用 API 的形狀，就可以控制這些重大變更。 在 DDD 方面，可以將這視為反損毀層。

* 請考慮為您的泛型引數提供有意義的名稱。

    除非您要撰寫非特定網域專屬的真正泛型程式碼，否則有意義的名稱可協助其他程式設計人員瞭解他們所使用的網域。 例如，在與檔資料庫互動的內容中命名的型別參數，可讓您所使用的函式 `'Document` 或成員接受一般檔案類型更加清楚。

* 請考慮使用 PascalCase 來命名泛型型別參數。

    這是在 .NET 中執行作業的一般方式，因此建議您使用 PascalCase，而不是 snake_case 或 camelCase。

最後，對於 F # 或大型程式碼基底的人員而言，自動一般化不一定是 boon。 使用一般的元件時，有認知負擔。 此外，如果自動一般化的函式不會搭配不同的輸入類型使用 (請單獨使用這些函式，以作為這類) ，如此一來，這些函式就不會在該時間點成為泛型。 請一律考慮您所撰寫的程式碼是否會真正受益于泛型。

## <a name="performance"></a>效能

### <a name="consider-structs-for-small-types-with-high-allocation-rates"></a>針對具有高配置速率的小型類型考慮結構

使用結構 (也稱為實值型別) 通常可以針對某些程式碼產生更高的效能，因為它通常可避免設定物件。 不過，結構不一定是「更快速」的按鈕：如果結構中的資料大小超過16個位元組，複製資料通常可能會比使用參考型別更多的 CPU 時間。

若要判斷是否應該使用結構，請考慮下列條件：

- 如果您的資料大小是16個位元組或更小。
- 如果您可能有許多這些類型的實例在執行中程式的記憶體中。

如果第一個條件適用，您通常應該使用結構。 如果兩者都適用，您幾乎都應該使用結構。 在某些情況下，您可能會在某些情況下套用先前的條件，但使用結構不會比使用參考型別更好或更糟，但很可能很罕見。 不過，一定要在進行這類變更時進行測量，而不是在假設或直覺上運作。

#### <a name="consider-struct-tuples-when-grouping-small-value-types-with-high-allocation-rates"></a>以高配置速率分組較小數值型別時，請考慮結構元組

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

當您使用 [BenchmarkDotNet](https://benchmarkdotnet.org/)之類的統計效能評定工具來評定這些函式時，您會發現 `runWithStructTuple` 使用結構元組的函式會以更快的速度執行40%，並且不會配置任何記憶體。

不過，在您自己的程式碼中，這些結果不一定是如此。 如果您將函式標示為 `inline` ，則使用參考元組的程式碼可能會取得一些額外的優化，或可配置的程式碼可能只會經過優化。 當效能考慮時，您應該一律測量結果，而且永遠不會根據假設或直覺來操作。

#### <a name="consider-struct-records-when-the-type-is-small-and-has-high-allocation-rates"></a>當類型很小且配置速率很高時，請考慮結構記錄

稍早所述的經驗法則也保留 [F # 記錄類型](../language-reference/records.md)。 請考慮下列用來處理這些資料類型的資料類型和函數：

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

這類似于先前的元組程式碼，但這次範例會使用記錄和內嵌的內建函式。

當您使用 [BenchmarkDotNet](https://benchmarkdotnet.org/)之類的統計效能評定工具來對這些函式進行基準測試時，您會發現 `processStructPoint` 執行速度快到60%，而且在 managed 堆積上未配置任何內容。

#### <a name="consider-struct-discriminated-unions-when-the-data-type-is-small-with-high-allocation-rates"></a>當資料類型很小且具有高配置速率時，請考慮結構區分等位

先前有關結構元組和記錄效能的觀察也保留給 [F #](../language-reference/discriminated-unions.md)差異聯集。 請考慮下列程式碼：

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

通常會針對網域模型定義像這樣的單一案例差異聯集。 當您使用 [BenchmarkDotNet](https://benchmarkdotnet.org/)之類的統計效能評定工具來對這些函式進行基準測試時，您會發現其 `structReverseName` 執行速度比小型字串快 25% `reverseName` 。 針對大型字串，兩者都會執行相同的。 因此，在此情況下，最好是使用結構。 如先前所述，一律測量並不會在假設或直覺上運作。

雖然先前的範例顯示結構差異聯集產生較佳的效能，但在建立定義域模型時，通常會有較大的區分等位。 較大的資料類型（例如，如果它們是結構，視其上的作業而定）可能不會同時執行，因為可能會涉及更多的複製。

### <a name="functional-programming-and-mutation"></a>功能性程式設計和變化

F # 值預設為固定值，可讓您避免特定類別的 bug (特別是) 平行存取和平行處理原則的類別。 不過，在某些情況下，若要達到最佳 (，或甚至合理) 執行時間或記憶體配置的效率，最好是使用狀態的就地變化來實行工作範圍。 您可以使用關鍵字搭配 F # 來加入宣告。 `mutable`

`mutable`在 F # 中使用可能會覺得功能純度很可能。 這是可理解的，但功能的純度可能會有效能目標。 折衷的是封裝變化，讓呼叫端不需要在意呼叫函式時會發生什麼事。 這可讓您針對效能關鍵程式碼，透過以變化為基礎的執行來撰寫功能介面。

#### <a name="wrap-mutable-code-in-immutable-interfaces"></a>將可變的程式碼包裝在不可變的介面中

使用參考透明度做為目標時，請務必撰寫不會公開效能關鍵函式之可變 underbelly 的程式碼。 例如，下列程式碼會 `Array.contains` 在 F # 核心程式庫中實作為函式：

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

多次呼叫此函式並不會變更基礎陣列，也不會要求您維持任何使用中的可變狀態。 它是參考上透明的，雖然幾乎每一行程式碼都會使用變化。

#### <a name="consider-encapsulating-mutable-data-in-classes"></a>考慮將可變數據封裝在類別中

先前的範例使用單一函式來封裝使用可變動資料的作業。 對於更複雜的資料集而言，這不一定足夠。 請考慮下列函數集：

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

這段程式碼的效能很高，但它會公開呼叫端負責維護的變化式資料結構。 這可以包裝在類別內，但不能變更任何基礎成員：

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

`Closure1Table` 封裝基礎以變化為基礎的資料結構，因此不會強制呼叫者維護基礎資料結構。 類別是一種功能強大的方法，可封裝以變化為基礎的資料和常式，而不會向呼叫端公開詳細資料。

#### <a name="prefer-let-mutable-to-reference-cells"></a>偏好 `let mutable` 參考資料格

參考資料格是一種表示值參考的方法，而不是值本身。 雖然它們可用於效能關鍵的程式碼，但不建議使用。 請考慮下列範例：

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

使用參考儲存格現在會「干擾」所有後續的程式碼，而且必須對基礎資料進行取值和重新參考。 請改 `let mutable` 為考慮：

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

除了 lambda 運算式中間的單一變化點之外，其他所有接觸的程式碼都 `acc` 可以使用與一般系結不可變的值不同的方式來達成 `let` 。 這可讓您更輕鬆地隨著時間變更。

## <a name="object-programming"></a>物件程式設計

F # 對於物件和麵向物件的 (OO) 概念具有完整的支援。 雖然許多 OO 概念都很強大且很有用，但並非全部都適合使用。 下列清單提供高階各類 OO 功能的指引。

**在許多情況下，請考慮使用這些功能：**

* 點標記法 (`x.Length`) 
* 執行個體成員
* 隱含的函式
* 靜態成員
* 索引子標記法 (`arr.[x]`) 
* 指名的和選擇性引數
* 介面和介面的實現

**請先找不到這些功能，但在方便解決問題時，請謹慎套用這些功能：**

* 方法多載
* 封裝的可變數據
* 類型上的運算子
* Auto 屬性
* 執行 `IDisposable` 和 `IEnumerable`
* 類型延伸模組
* 事件
* 結構
* 委派
* 列舉

**一般來說，除非您必須使用這些功能，否則請避免這些功能：**

* 繼承型型別階層和執行繼承
* Null 和 `Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>偏好透過繼承撰寫

[超越繼承的組合](https://en.wikipedia.org/wiki/Composition_over_inheritance) 是良好的 F # 程式碼可以遵守的長期用法。 基本原則是，您不應該公開基類，並強制呼叫端繼承自該基類以取得功能。

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>如果您不需要類別，請使用物件運算式來執行介面

[物件運算式](../language-reference/object-expressions.md) 可讓您即時執行介面，將實介面系結至值，而不需要在類別內部執行此動作。 這很方便，尤其是當您 _只_ 需要執行介面，且不需要完整類別時更是如此。

例如，以下是在 [Ionide](https://ionide.io/) 中執行的程式碼，如果您已新增沒有語句的符號，則會提供程式碼修正動作 `open` ：

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

由於與 Visual Studio Code API 互動時，不需要類別，因此物件運算式是理想的工具。 當您想要以臨機操作的方式，以測試常式來取代介面時，它們也非常適合單元測試。

## <a name="consider-type-abbreviations-to-shorten-signatures"></a>請考慮輸入縮寫以縮短簽章

[類型縮寫](../language-reference/type-abbreviations.md) 是將標籤指派給另一種類型的便利方法，例如函式簽章或更複雜的型別。 例如，下列別名會將標籤指派給使用 [CNTK](/cognitive-toolkit/)（深度學習程式庫）定義計算所需的內容：

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

`Computation`名稱是一種便利的方式，用來表示任何符合其別名的簽章的函式。 使用這類的類型縮寫很方便，而且可讓程式碼更簡潔。

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>避免使用類型縮寫來表示您的網域

雖然型別縮寫對於為函式簽章提供名稱很方便，但在縮寫其他類型時可能會造成混淆。 請考慮以下縮寫：

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

這可能會讓您以多種方式造成混淆：

* `BufferSize` 不是抽象概念;這只是整數的另一個名稱。
* 如果 `BufferSize` 在公用 API 中公開，就可以輕易地將它誤解為非單純的表示 `int` 。 一般而言，網欄位型別具有多個屬性，而且不是基本類型，例如 `int` 。 此縮寫違反該假設。
*  (的大小寫 `BufferSize`) 表示此型別會保存更多資料。
* 相較于將具名引數提供給函式，此別名不會提供更高的清晰度。
* 縮寫不會在編譯的 IL 中資訊清單;它只是一個整數，而此別名是編譯時期的結構。

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

總而言之，類型縮寫的缺點是它們在縮寫的類型上 **不** 是抽象概念。 在上述範例中， `BufferSize` 只是 `int` 在幕後，沒有額外的資料，也不會有任何來自型別系統的優點，除了已有的內容之外 `int` 。

使用類型縮寫來表示網域的替代方法是使用單一案例差異聯集。 先前的範例可以模型化，如下所示：

```fsharp
type BufferSize = BufferSize of int
```

如果您撰寫的程式碼會以 `BufferSize` 和其基礎值運作，您必須建立一個，而不是傳入任何任意整數：

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

這樣可以減少錯誤地將任意整數傳遞給函式的可能性 `send` ，因為呼叫端必須在 `BufferSize` 呼叫函式之前，先建立型別來包裝值。
