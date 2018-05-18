---
title: 'F # 元件的設計指導方針'
description: '了解撰寫 F # 預定由其他呼叫端元件的指導方針。'
ms.date: 05/14/2018
ms.openlocfilehash: 7859baac76be01b2cfbdc8602b6cc417cfe5106f
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2018
---
# <a name="f-component-design-guidelines"></a>F # 元件的設計指導方針

這份文件是一組元件的設計方針 F # 程式，並根據 F # 元件設計指導方針，v14，Microsoft 研究和[另一個版本](https://fsharp.org/specs/component-design-guidelines/)原來 curated 和 F # Software Foundation 所維護。

本文件假設您熟悉以 F # 的程式設計。 非常感謝 F # 社群的參與，很有幫助的意見反應，本指南的各種版本上。

## <a name="overview"></a>總覽

本文件探討某些與 F # 元件設計和編碼相關的問題。 元件可能表示下列其中一項：

* F # 專案中有該專案內外部的取用者層。
* 跨組件界限提供給耗用量 F # 程式碼程式庫。
* 預定由任何.NET 語言跨組件界限文件庫。
* 例如適用於散發的封裝儲存機制，透過文件庫[NuGet](https://nuget.org)。

請遵循本文中所述的技巧[良好的 F # 程式碼的五個原則](index.md#five-principles-of-good-f-code)，因此利用兩者功能，以及適當地進行程式設計的物件。

在方法中，不論元件和程式庫的設計工具時嘗試製作最容易供開發人員的 API 面實際且 prosaic 問題數目。 暴增的應用程式的[.NET 程式庫設計方針](../../standard/design-guidelines/index.md)操縱您建立一致的整套愉快取用的 Api。

## <a name="general-guidelines"></a>一般方針

有幾個通用的指導方針適用於 F # 程式庫，不論程式庫的目標對象。

### <a name="learn-the-net-library-design-guidelines"></a>了解.NET 程式庫設計指導方針

F # 程式碼撰寫您所執行的類型，不論是非常有用的具備的實用知識[.NET 程式庫設計方針](../../standard/design-guidelines/index.md)。 大多數其他 F # 和.NET 程式設計人員會熟悉下列指導方針，並預期以符合它們的.NET 程式碼。

.NET 程式庫設計指導方針提供一般指引命名、 設計類別和介面、 成員設計 （屬性、 方法、 事件等） 和詳細資訊，而且很有用的各種不同的設計指導方針的參考第一個點。

### <a name="add-xml-documentation-comments-to-your-code"></a>將 XML 文件註解加入至您的程式碼

XML 文件的公用 Api 上可確保使用者可以取得很好的 Intellisense 和 Quickinfo 時使用這些型別和成員，以及啟用建置文件庫的檔案。 請參閱[XML 文件](../language-reference/xml-documentation.md)各種可用於 xmldoc 註解內其他標記的 xml 標記的資訊。

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo : otherPoint:Point -> float
```

您可以使用任一的簡短形式 XML 註解 (`/// comment`)，或標準 XML 註解 (`///<summary>comment</summary>`)。

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a>請考慮使用明確的簽章檔案 (.fsi) 穩定的程式庫和應用程式開發介面的元件

使用 F # 程式庫中的明確的簽章檔案提供公用 API，但是這兩個可協助確保您知道您的媒體櫃的完整公用介面以及提供清楚的分隔之間公用文件和內部簡潔的摘要實作詳細資料。 請注意，簽章新增檔案人事變更公用 API 中，需要在實作和簽章檔案中進行的變更。 如此一來，簽章檔案應該通常只會引進當應用程式開發介面已經成為目的並不會再預期會有重大變更。

### <a name="always-follow-best-practices-for-using-strings-in-net"></a>永遠會接在.NET 中使用字串的最佳作法

請遵循[在.NET 中使用字串的最佳作法](../../standard/base-types/best-practices-strings.md)指引。 特別是，一律明確地陳述*文化特性的意圖*中的轉換和字串的比較 （如果適用的話）。

## <a name="guidelines-for-f-facing-libraries"></a>F # 的指導方針-對向程式庫

本節提供的建議用於開發公用 F #-對向程式庫。亦即，公開要供 F # 開發人員的公用 Api 的程式庫。 沒有為 F # 適用的各種不同的程式庫設計建議。 如果沒有遵循特定建議，.NET 程式庫設計指導方針是後援的指引。

### <a name="naming-conventions"></a>命名規範

#### <a name="use-net-naming-and-capitalization-conventions"></a>使用.NET 命名和大小寫慣例

下表依照.NET 命名和大小寫慣例。 有小新增項目也包含 F # 建構。

| 建構 | 案例 | 組件 | 範例 | 注意 |
|-----------|------|------|----------|-------|
| 具象型別 | PascalCase | 名詞 / 形容詞 | 清單中，Double，複雜 | 具象型別是結構、 類別、 列舉型別、 委派、 記錄、 和等位。 雖然型別名稱是 OCaml 在過去是小寫，F # 已採用類型的.NET 命名配置。
| DLL           | PascalCase |                 | Fabrikam.Core.dll |  |
| 等位標記     | PascalCase | 名詞 | 部分新增成功 | 請勿在公用 Api 中使用前置詞。 （選擇性） 使用的前置詞時內部，例如 '' 輸入小組 = TAlpha | TBeta | TDelta。 ' ' |
| Event - 事件          | PascalCase | 動詞命令 | ValueChanged / ValueChanging |  |
| 例外狀況     | PascalCase |      | WebException | 名稱應該以"Exception"為結尾。 |
| 欄位          | PascalCase | 名詞 | CurrentName  | |
| 介面型別 |  PascalCase | 名詞 / 形容詞 | IDisposable | 名稱應該以"I"開頭。 |
| 方法 |  PascalCase |  動詞命令 | ToString | |
| 命名空間 | PascalCase | | Microsoft.FSharp.Core | 通常使用`<Organization>.<Technology>[.<Subnamespace>]`，不過卸除組織，如果組織的技術無關。 |
| 參數 | camelCase | 名詞 |  類型名稱、 轉換、 範圍 | |
| 讓值 （內部） | camelCase 或 PascalCase | 名詞 / 動詞命令 |  getValue myTable |
| 讓值 （外部） | camelCase 或 PascalCase | 名詞/動詞命令  | List.map Dates.Today | let 繫結值通常是公用的遵循傳統功能的設計模式時。 不過，通常使用 PascalCase 時可以從其他.NET 語言使用的識別項。 |
| 屬性  | PascalCase  | 名詞 / 形容詞  | IsEndOfFile，背景色彩  | 布林值屬性通常不使用，因為可以而且應該是肯定的如 IsEndOfFile，不 IsNotEndOfFile 所示。

#### <a name="avoid-abbreviations"></a>避免縮寫

.NET 方針不鼓勵使用縮寫 (例如，「 使用`OnButtonClick`而不是`OnBtnClick`")。 常用的縮寫，例如`Async`的 「 非同步 」，所容許之。 功能性程式設計，有時會忽略這項指導方針例如，`List.iter`用於 「 重複 」 的縮寫。 基於這個理由，使用縮寫通常會在 F # 中儘可容許-到-F # 的程式設計，但仍通常應該避免在公用元件的設計。

#### <a name="avoid-casing-name-collisions"></a>避免發生名稱衝突的大小寫慣例

.NET 指導方針會假設，單獨的大小寫慣例不能用來區分名稱發生衝突，因為某些用戶端語言 (例如，Visual Basic) 皆不區分大小寫。

#### <a name="use-acronyms-where-appropriate"></a>在適當時使用首字母縮略字

首字母縮略字，例如 XML 不縮寫，且都廣泛利用 uncapitalized 格式 (Xml) 的.NET 程式庫中。 只應該使用廣為人知且知名首字母縮略字。

#### <a name="use-pascalcase-for-generic-parameter-names"></a>泛型參數名稱使用 PascalCase

不要在公用 Api，包括 F # 的泛型參數名稱使用 PascalCase-對向程式庫。 特別是，使用名稱`T`， `U`， `T1`，`T2`任意的泛型參數，以及特定名稱有意義，然後 F #-向程式庫會使用名稱`Key`， `Value`， `Arg`(但不是例如`TKey`)。

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a>使用 PascalCase 或 camelCase 公用函式和 F # 模組中的值

camelCase 用於設計用於的公用函式不合格 (例如， `invalidArg`)，以及 < 標準集合函數 > （例如 List.map）。 在這兩個這些情況下，函式名稱像是多語言中關鍵字。

### <a name="object-type-and-module-design"></a>物件、 類型和模組的設計

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a>使用命名空間或模組來包含您的類型和模組

在元件中的每個 F # 檔案應該以命名空間宣告或模組宣告開頭。

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

或

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

使用模組和命名空間來組織最上層的程式碼之間的差異如下所示：

* 命名空間可以跨越多個檔案
* 命名空間不能包含 F # 函式，除非它們是在內部的模組中
* 任何給定的模組的程式碼必須包含在單一檔案
* 最上層的模組可以包含 F # 函式，而不需要內部的模組

最上層命名空間或模組之間選擇會影響程式碼的編譯的形式，並因此將會影響其他.NET 語言檢視應該您的 API 最終取用外部 F # 程式碼。

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a>使用內建的物件類型的作業的方法和屬性

當處理物件，所以最好先確保您可以使用的功能會實作為該類型的方法和屬性。

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

大量的功能，為給定成員需要一定中實作該成員，但應該是您可以使用該功能部分。

#### <a name="use-classes-to-encapsulate-mutable-state"></a>使用類別來封裝可變狀態

在 F # 中，這只需要進行其中狀態不已封裝的另一個語言建構，例如關閉、 序列運算式中或非同步的計算。

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a>使用介面來群組相關的作業

您可以使用介面型別來代表一組作業。 這是慣用和其他選項，例如 tuple 的函式或函式的記錄。

```fsharp
type Serializer =
    abstract Serialize<'T> : preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T> : preserveRefEq: bool -> pickle: string -> 'T
```

優先以：

```fsharp
type Serializer<'T> = {
    Serialize : bool -> 'T -> string
    Deserialize : bool -> string -> 'T
}
```

介面是在.NET 中，您可用來達成什麼函式通常五月，第一級的概念。 此外，它們可以用來編碼至您程式中，記錄的函式不能存在的類型。

#### <a name="use-a-module-to-group-functions-which-act-on-collections"></a>使用要處理的群組函式的模組集合

當您定義集合型別時，請考慮提供一組標準的作業類似`CollectionType.map`和`CollectionType.iter`) 對於新的集合類型。

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

如果您包含這類模組，請遵循 FSharp.Core 中找到的函式的標準命名慣例。

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a>使用適用於通用的標準函式，尤其是在數學和 DSL 程式庫群組函式模組

例如，`Microsoft.FSharp.Core.Operators`是自動開啟最上層函式的集合 (例如`abs`和`sin`) FSharp.Core.dll 所提供。

同樣地，統計資料的程式庫可能包含具有函式的模組`erf`和`erfc`、 此模組為了明確或自動開啟。

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a>請考慮使用 RequireQualifiedAccess 並仔細套用 AutoOpen 屬性

加入`[<RequireQualifiedAccess>]`模組的屬性表示模組可能未開啟，而且參考的模組項目需要明確限定存取。 例如，`Microsoft.FSharp.Collections.List`模組有這個屬性。

當函式和模組中的值有可能會與其他模組中的名稱發生衝突的名稱，這非常有用。 需要完整存取權可以大幅增加長期的可維護性和 evolvability 的文件庫。

加入`[<AutoOpen>]`模組的屬性表示開啟包含命名空間時，就會開啟模組。 `[<AutoOpen>]`屬性可能也會套用到組件，表示參考組件時就會自動開啟模組。

例如，統計資料的程式庫**MathsHeaven.Statistics**可能包含`module MathsHeaven.Statistics.Operators`含有函式`erf`和`erfc`。 它可合理地標示為此模組`[<AutoOpen>]`。 這表示`open MathsHeaven.Statistics`也會開啟此模組並將名稱`erf`和`erfc`納入範圍。 使用另一個良好`[<AutoOpen>]`為包含擴充方法的模組。

過度使用的`[<AutoOpen>]`污染的命名空間和屬性將導致應小心使用。 針對特定的文件庫中特定網域，明智地使用`[<AutoOpen>]`可能會導致更好的可用性。

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a>請考慮在則適合使用已知的運算子的類別上定義運算子成員

有時候類別可用來建立模型數學建構，例如向量。 正在模型化的網域有已知的運算子，定義為 「 內建函式類別的成員時很有幫助。

```fsharp
type Vector(x:float) =

    member v.X = x

    static member (*) (vector:Vector, scalar:float) = Vector(vector.X * scalar)

    static member (+) (vector1:Vector, vector2:Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

本指南會對應至這些類型的一般.NET 指引。 不過，它可能在 F # 程式碼撰寫這可讓這些型別，以用於搭配 F # 函式和方法的成員條件約束，例如 List.sumBy 此外重要。

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a>請考慮使用 CompiledName 提供。其他.NET 語言取用者的的網路的易記名稱

有時候您可能想要的 F # 消費者命名樣式中的項目 (例如大小寫，使它顯示在靜態成員就好像模組繫結函式)，但它編譯的組件時，有不同的樣式名稱。 您可以使用`[<CompiledName>]`非 F # 程式碼使用組件提供不同的樣式屬性。

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

使用`[<CompiledName>]`，您可以使用非 F # 組件的取用者的.NET 命名慣例。

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a>使用方法多載成員函式，如果這麼做可以提供更簡單的應用程式開發介面

方法多載是功能強大的工具，以簡化的 API，可能需要執行類似的功能，不過多了不同的選項或引數。

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

在 F # 中，是較常見的引數數目，而不是引數型別多載。

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a>隱藏記錄和等位型別的表示，如果這些型別的設計可能發展

避免洩露之物件的實體表示。 例如的具象表示<xref:System.DateTime>值不會由外部的公用 API 的.NET 程式庫設計。 在執行階段，Common Language Runtime 知道認可將在整個執行的實作。 不過，已編譯程式碼不本身挑選的相依性的具象表示法。

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a>避免使用實作繼承的擴充性

在 F # 中，很少使用實作繼承。 此外，繼承階層架構通常是很複雜而難以變更的新要求到達時。 繼承實作仍然在 F # 的相容性和罕見的情況下，它很最佳解決方案，會造成問題，但設計多型，例如介面實作時，應該在 F # 程式中尋找的替代技術。

### <a name="function-and-member-signatures"></a>函式和成員的簽章

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a>傳回少量的多個不相關的值時，使用 tuple 的傳回值

以下是使用 tuple，傳回型別中的理想範例：

```fsharp
val divrem : BigInteger -> BigInteger -> BigInteger * BigInteger
```

傳回型別包含許多元件，或單一識別實體相關的元件，請考慮使用具名型別，而不 tuple。

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a>使用`Async<T>`進行非同步程式設計，F # 應用程式開發介面界限

如果沒有對應的同步作業，名為`Operation`傳回`T`，非同步處理作業應該命名為`AsyncOperation`如果它傳回`Async<T>`或`OperationAsync`如果它傳回`Task<T>`。 常用的.NET 型別公開 Begin/End 方法，請請考慮使用`Async.FromBeginEnd`為外觀提供 F # 非同步程式設計模型的.NET Api 來撰寫擴充方法。

```fsharp
type SomeType =
    member this.Compute(x:int) : int =
        ...
    member this.AsyncCompute(x:int) : Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a>例外狀況

例外狀況是在.NET; 例外狀況也就是說，它們不應該進行經常在執行階段。 這樣做，所包含的資訊時，有價值。 例外狀況是核心的第一個類別的.NET; 概念it 因此一部分的元件介面的設計應該使用適當的應用程式的例外狀況，如下所示。

#### <a name="follow-the-net-guidelines-for-exceptions"></a>請遵循例外狀況的.NET 方針

[.NET 程式庫設計方針](../../standard/design-guidelines/exceptions.md)提供絕佳的建議使用的所有.NET 程式設計內容中的例外狀況。 部分這些指導方針如下：

* 請勿用於一般控制流程的例外狀況。 雖然這項技術通常用於 OCaml 等語言，它會是容易發生錯誤的而且可以是.net 效率不佳。 相反地，請考慮傳回`None`選項值，指出是一般或預期執行一次失敗。

* 文件時未正確使用函式的元件擲回的例外狀況。

* 可能的話，會採用現有系統的命名空間中的例外狀況。 避免<xref:System.ApplicationException>，但是。

* 未擲回<xref:System.Exception>時它將逸出，對使用者程式碼。 這包括避免使用`failwith`， `failwithf`，這是很方便的函式用於指令碼和程式碼開發，但應該從 F # 程式庫程式碼改為擲回特定例外狀況類型中移除。

* 使用`nullArg`， `invalidArg`，和`invalidOp`做為擲回的機制<xref:System.ArgumentNullException>， <xref:System.ArgumentException>，和<xref:System.InvalidOperationException>適當的時候。

#### <a name="consider-using-option-values-for-return-types-when-failure-is-not-an-exceptional-scenario"></a>請考慮使用傳回型別選項的值時失敗不是例外狀況

例外狀況的.NET 方法是，它們應該是 「 例外 」;也就是說，它們應該進行相對較少。 不過，某些作業 （例如，搜尋資料表） 可能會經常失敗。 F # 選項值是絕佳的方式來表示這些作業的傳回型別。 這些作業 signature 開頭的名稱前置詞"try":

```fsharp
// bad: throws exception if no element meets criteria
member this.FindFirstIndex(pred : 'T -> bool) : int =
    ...

// bad: returns -1 if no element meets criteria
member this.FindFirstIndex(pred : 'T -> bool) : int =
    ...

// good: returns None if no element meets criteria
member this.TryFindFirstIndex(pred : 'T -> bool) : int option =
    ...
```

### <a name="extension-members"></a>擴充成員

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a>請仔細套用 F # 擴充成員在 F #-到-F # 元件

F # 擴充成員通常只應位於與大部分的其模式的使用中的型別相關聯的內建作業的終止作業。 一個常見用途就是提供更慣用語 F # 各種不同的.NET 類型的 Api:

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a>等位型別

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a>使用差別聯的集而不是類別階層架構樹狀結構的資料

類似樹狀目錄結構是遞迴定義。 這是造成不便使用繼承，但精緻的差別等位。

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

代表類似樹狀目錄資料的差別等位也可讓您受益於 exhaustiveness 在模式比對。

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a>使用`[<RequireQualifiedAccess>]`上其大小寫的名稱不是完全唯一的聯集類型

您可能會發現自己位於網域中相同名稱的不同事物，例如差別聯集的情況下最適當的名稱。 您可以使用`[<RequireQualifiedAccess>]`要區分大小寫的名稱以避免觸發遮蔽的排序相依的令人困惑錯誤`open`陳述式

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a>如果這些型別的設計可能發展，隱藏差別聯集的表示如二進位相容的應用程式開發介面

等位型別依賴 F # 的模式比對的表單簡潔的程式設計模型。 如先前所述，您應該避免洩露具體資料表示法，如果這些型別的設計可能發展。

例如，差別聯集的表示法可以隱藏使用私用或內部宣告，或使用簽章檔案。

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

如果您隨意洩露差別聯的集，您可能會發現很難版本程式庫而不會中斷使用者程式碼。 相反地，請考慮提供一個或多個作用中的模式，以允許模式比對您的型別值。

作用中的模式提供的替代方式為 F # 取用者提供的模式比對，同時避免直接公開 F # 聯集類型。

### <a name="inline-functions-and-member-constraints"></a>內嵌函式和成員條件約束

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a>定義泛型數值的演算法，以統計方式解析的泛型型別與隱含的成員條件約束中使用內嵌函式

算術成員條件約束和 F # 比較條件約束是標準的 F # 的程式設計。 例如，請參考下列程式碼：

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

此函式的類型如下所示：

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

這是適合的函式中的數學程式庫的公用 api。

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a>請避免使用以模擬型別類別和鴨子輸入成員條件約束

可以模擬"住輸入 」 使用 F # 成員條件約束。 不過，可讓成員使用這個屬性應該不能在一般用於 F #-到-F # 程式庫設計。 這是因為不太熟悉或非標準的隱含條件約束為基礎的程式庫設計傾向於使使用者程式碼，使其成為卻往往缺乏彈性並繫結一個特定架構的模式。

此外，很可能會大量使用這種方式中的成員條件約束導致非常長的編譯時間。

### <a name="operator-definitions"></a>運算子定義

#### <a name="avoid-defining-custom-symbolic-operators"></a>應避免定義自訂的符號運算子

自訂運算子在某些情況下，而非常有用的影響力裝置在大型的主體內的實作程式碼。 文件庫的新使用者，具名函式通常是容易使用。 此外，自訂符號運算子就很難文件，而且使用者尋找更難查詢運算子，因為 IDE，並搜尋引擎中的現有限制的說明。

如此一來，所以最好來發行您的功能，為具名函式和成員，和此外公開運算子，這項功能才影響力的優點勝過文件集和認知讓它們的成本。

### <a name="units-of-measure"></a>測量單位

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a>謹慎使用 F # 程式碼中加入的類型安全的測量單位

檢視由其他.NET 語言時，會清除輸入的其他資訊的單位量值。 請注意，進行.NET 元件、 工具和反映會看到 san 單位類型。 例如，C# 取用者將會看見`float`而不是`float<kg>`。

### <a name="type-abbreviations"></a>類型縮寫

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a>請仔細來簡化 F # 程式碼中使用類型縮寫

.NET 元件、 工具和反映不會看到類型縮寫的名稱。 類型縮寫的重要使用方式也可以將出現越複雜，比它實際上是，這可能會感到困惑取用者的網域。

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a>避免其成員和屬性應該在本質上不同所縮寫類型上的可用的公用類型的類型縮寫

在此情況下，所縮寫類型會顯示有關所定義的實際類型的表示法太多。 相反地，請考慮換行中的類別類型或單一案例差別等位的縮寫 （或重要效能時，請考慮使用結構型別包裝縮寫）。

例如，它會嘗試定義多重對應視為特殊案例的 F # 地圖，例如：

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

不過，這個類型上的邏輯點標記法作業不會在地圖上的作業相同 (比方說，是合理 lookup 運算子對應）。[索引鍵] 傳回空的清單，如果索引鍵不在字典中，而非引發例外狀況。

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a>從其他.NET 語言使用的程式庫的指導方針

在設計為從其他.NET 語言使用的程式庫時，務必遵守[.NET 程式庫設計方針](../../standard/design-guidelines/index.md)。 在本文件中，這些程式庫會標示為香草.NET 程式庫，而不是 F #-面對使用 F # 的程式庫建構不受限制。 設計香草.NET 程式庫表示藉由減少使用 F # 提供熟悉且慣用語 Api 與.NET Framework 的其餘部分一致-公用 API 中的特定建構。 下列各節中說明的規則。

### <a name="namespace-and-type-sesign-for-libraries-for-use-from-other-net-languages"></a>命名空間和類型 sesign （適用於從其他.NET 語言使用的程式庫）

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a>套用至元件的公用 API 的.NET 命名慣例

請特別注意，可讓您使用縮寫的名稱和.NET 大小寫方針。

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a>做為命名空間、 類型和成員的主要組織性結構為您的元件

包含公用的功能的所有檔案都開頭應該是`namespace`宣告和命名空間中公開的實體應該是型別。 請勿使用 F # 模組。

使用非公用模組來保存實作程式碼、 公用程式類型和公用程式函式。

靜態類型應該是慣用的模組，透過它們允許使用多載和其他的.NET API 設計概念，不能使用 F # 模組內未來發展的 api。

例如，取代下列的公用 API:

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

請考慮改用：

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a>如果類型的設計不會發展，在香草.NET 應用程式開發介面中使用 F # 記錄類型

F # 記錄類型編譯為一個簡單的.NET 類別。 這些是適用於應用程式開發介面中的某些簡單、 穩定 」 類型。 您應該考慮使用`[<NoEquality>]`和`[<NoComparison>]`屬性來隱藏自動產生的介面。 也請避免使用香草.NET 應用程式開發介面中的可變動的資料錄欄位，這些會公開為公用的欄位。 務必考慮是否類別會提供 API 的未來發展的更有彈性的選項。

例如，下列的 F # 程式碼會公開公用 API 的 C# 取用者：

F # 中：

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing : int
        SecondThing : string }
```

C#: 

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a>隱藏 F # 聯集類型的香草.NET 應用程式開發介面中的表示法

F # 等位型別不常用於跨元件界限，即使 F #-到-F # 程式碼撰寫。 它們是絕佳的實作裝置時的內部使用的元件和程式庫。

設計時香草.NET API，請考慮使用私用宣告或簽章檔案中隱藏聯集類型的表示法。

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

您可能也會擴充以提供所需的等位表示在內部使用與成員的類型。網路對向應用程式開發介面。

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True

    /// A public member for use from C#
    member x.Evaluate =
        match x with
        | And(a,b) -> a.Evaluate && b.Evaluate
        | Not a -> not a.Evaluate
        | True -> true

    /// A public member for use from C#
    static member CreateAnd(a,b) = And(a,b)
```

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a>設計 GUI 和其他元件使用的架構設計模式

另外還有許多不同的架構在.NET 中，例如 WinForms、 WPF 和 ASP.NET。 如果您要設計這些架構中使用的元件，則應該使用針對每個命名和設計慣例。 例如，針對 WPF 程式設計，採用 WPF 設計模式，您要設計的類別。 在使用者介面的程式設計模型，使用 設計模式，例如事件與通知為基礎的集合，例如位於<xref:System.Collections.ObjectModel>。

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a>物件和成員設計 （適用於從其他.NET 語言使用的程式庫）

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a>使用 CLIEvent 屬性公開.NET 事件

建構`DelegateEvent`與特定的.NET 委派會採用物件的型別和`EventArgs`(而非`Event`，這只是使用`FSharpHandler`預設的型別)，讓事件發行在其他.NET 語言的熟悉方式。

```fsharp
type MyBadType() =
    let myEv = new Event<int>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish

type MyEventArgs(x:int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-which-return-net-tasks"></a>公開非同步作業，做為傳回.NET 工作的方法

在.NET 中使用工作來表示使用中的非同步計算。 工作處於較不撰寫 F # 比一般`Async<T>`物件，因為它們代表 「 執行 」 工作，並且不能執行的平行的組合，或其中隱藏取消信號，以及其他的傳播方式一起構成內容參數。

不過，如果即使如此，傳回工作的方法就是.net 非同步程式設計的標準表示法。

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int) : Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

您會經常也想要接受明確的取消語彙基元：

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x:int) : Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a>使用.NET 委派型別，而不是 F # 函式類型

以下 「 F # 函式類型 」 表示"箭號 」 型別想`int -> int`。

而不是下列項目：

```fsharp
member this.Transform(f:int->int) =
    ...
```

請執行：

```fsharp
member this.Transform(f:Func<int,int>) =
    ...
```

F # 函式類型會顯示為`class FSharpFunc<T,U>`其他.NET 語言，因此較不適合用於語言功能和工具了解委派類型。 當製作目標為.NET Framework 3.5 或更新版本，較高順序方法`System.Func`和`System.Action`委派是右應用程式開發介面，可讓.NET 開發人員使用這些 Api 以低人事方式發行。 (系統定義的委派類型時以.NET Framework 2.0 為目標，會更受到限制，請考慮使用預先定義的委派類型，例如`System.Converter<T,U>`或定義特定的委派型別。)

翻轉一邊.NET 委派不是理所當然的 F #-對向程式庫 (請參閱下一節 F #-對向程式庫)。 如此一來，開發香草.NET 程式庫的高階方法時的一般實作策略，是以編寫所有使用 F # 函式類型的實作，並建立在實際的 F # 之上的精簡外觀為使用委派的公用 API實作。

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a>使用 TryGetValue 模式，而不是傳回 F # 選項值，並優先使用方法多載採用 F # 選項值做為引數

常見的應用程式開發介面中的 F # 選項類型使用的模式是較佳的香草中實作.NET 應用程式開發介面使用標準.NET 設計的技術。 而不是傳回的 F # 選項值，請考慮使用 bool 的傳回型別加上"TryGetValue 」 模式與 out 參數。 而不使用 F # 選項值做為參數，請考慮使用方法多載或選擇性引數。

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal : byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x : int, y : int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x : int) = x

member this.ParamOverload(x : int, y : int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a>使用.NET 集合介面型別 IEnumerable\<T\>和\<索引鍵、 值\>參數和傳回值

避免使用的具象集合類型，例如.NET 陣列`T[]`，F # 類型`list<T>`，`Map<Key,Value>`和`Set<T>`，與.NET 的具象集合類型，例如`Dictionary<Key,Value>`。 .NET 程式庫設計方針有關於使用類似的各種集合類型的時機很好的建議`IEnumerable<T>`。 有些使用的陣列 (`T[]`) 是可接受在某些情況下，效能地面上。 請注意，特別是`seq<T>`是只 F # 的別名`IEnumerable<T>`，而因此 seq 通常是適當的型別香草.NET API。

而不是 F # 的清單：

```fsharp
member this.PrintNames(names : string list) =
    ...
```

使用 F # 順序：

```fsharp
member this.PrintNames(names : seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a>做為唯一的方法的輸入類型使用的單位類型，定義零引數的方法，或做為唯一會傳回定義傳回 void 方法的型別

避免的單位類型的其他用途。 這些是很好的：

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x : int) = ()
```

這是不正確：

```fsharp
member this.WrongUnit( x:unit, z:int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a>檢查有 null 值香草.NET API 界限上

F # 實作程式碼通常會有較少的 null 值，因為不可變的設計模式，以及使用 F # 型別的 null 常值的限制。 其他.NET 語言通常會使用 null 做為值更頻繁。 因為這個緣故，F # 程式碼公開.NET API 的香草應該檢查應用程式開發介面緣 null 的參數，以及更深入流入 F # 實作程式碼時，防止這些值。 `isNull`函式或模式比對`null`模式可用。

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a>請避免使用 tuple 做為傳回值

相反地，偏好傳回持有的彙總的資料，或使用 out 參數傳回多個值的具名型別。 雖然.NET 中存在的 tuple 與結構 （包括結構 tuple 的 C# 語言支援），它們通常不會提供理想和預期 API 適用於.NET 開發人員。

#### <a name="avoid-the-use-of-currying-of-parameters"></a>避免使用的參數對

相反地，使用.NET 呼叫慣例``Method(arg1,arg2,…,argN)``。

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

秘訣： 如果您在設計文件庫，從任何.NET 語言使用，就沒有替代執行某些實驗 C# 和 Visual Basic 程式設計，確保您的程式庫 」 操作權限 」 從這些語言項目。 您也可以使用.NET 反映程式與 Visual Studio 物件瀏覽器之類的工具，以確保文件庫和其文件會出現如預期般對開發人員。

## <a name="appendix"></a>附錄

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a>設計 F # 程式碼使用其他.NET 語言的端對端範例

請考慮下列類別：

```fsharp
open System

type Point1(angle,radius) =
    new() = Point1(angle=0.0, radius=0.0)
    member x.Angle = angle
    member x.Radius = radius
    member x.Stretch(l) = Point1(angle=x.Angle, radius=x.Radius * l)
    member x.Warp(f) = Point1(angle=f(x.Angle), radius=x.Radius)
    static member Circle(n) =
        [ for i in 1..n -> Point1(angle=2.0*Math.PI/float(n), radius=1.0) ]
```

推斷的 F # 類型的這個類別如下所示：

```fsharp
type Point1 =
    new : unit -> Point1
    new : angle:double * radius:double -> Point1
    static member Circle : n:int -> Point1 list
    member Stretch : l:double -> Point1
    member Warp : f:(double -> double) -> Point1
    member Angle : double
    member Radius : double
```

讓我們看看這個 F # 型別對程式設計人員使用其他.NET 語言的顯示方式。 例如，大約 C# 「 簽章 」 如下所示：

```csharp
// C# signature for the unadjusted Point1 class
public class Point1
{
    public Point1();

    public Point1(double angle, double radius);

    public static Microsoft.FSharp.Collections.List<Point1> Circle(int count);

    public Point1 Stretch(double factor);

    public Point1 Warp(Microsoft.FSharp.Core.FastFunc<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

有一些重點来注意的 F # 如何表示這裡建構。 例如: 

* 已保留中繼資料，例如引數名稱。

* F # 方法會採用兩個引數會變成 C# 方法會採用兩個引數。

* 函式和清單會變成對應的型別在 F # 程式庫的參考。

下列程式碼顯示如何調整這個程式碼以下列項目納入考量。

```fsharp
namespace SuperDuperFSharpLibrary.Types

type RadialPoint(angle:double, radius:double) =

    /// Return a point at the origin
    new() = RadialPoint(angle=0.0, radius=0.0)

    /// The angle to the point, from the x-axis
    member x.Angle = angle

    /// The distance to the point, from the origin
    member x.Radius = radius

    /// Return a new point, with radius multiplied by the given factor
    member x.Stretch(factor) =
        RadialPoint(angle=angle, radius=radius * factor)

    /// Return a new point, with angle transformed by the function
    member x.Warp(transform:Func<_,_>) =
        RadialPoint(angle=transform.Invoke angle, radius=radius)

    /// Return a sequence of points describing an approximate circle using
    /// the given count of points
    static member Circle(count) =
        seq { for i in 1..count ->
                RadialPoint(angle=2.0*Math.PI/float(count), radius=1.0) }
```

推斷的 F # 類型的程式碼如下所示：

```fsharp
type RadialPoint =
    new : unit -> RadialPoint
    new : angle:double * radius:double -> RadialPoint
    static member Circle : count:int -> seq<RadialPoint>
    member Stretch : factor:double -> RadialPoint
    member Warp : transform:System.Func<double,double> -> RadialPoint
    member Angle : double
    member Radius : double
```

C# 簽章現在如下所示：

```csharp
public class RadialPoint
{
    public RadialPoint();

    public RadialPoint(double angle, double radius);

    public static System.Collections.Generic.IEnumerable<RadialPoint> Circle(int count);

    public RadialPoint Stretch(double factor);

    public RadialPoint Warp(System.Func<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

修正對準備使用這種類型時香草的.NET 程式庫的一部分，如下所示：

* 調整數個名稱： `Point1`， `n`， `l`，和`f`變成`RadialPoint`， `count`， `factor`，和`transform`分別。

* 使用傳回型別`seq<RadialPoint>`而不是`RadialPoint list`藉由變更清單建構使用`[ ... ]`序列建構使用`IEnumerable<RadialPoint>`。

* 使用.NET 委派型別`System.Func`而不是 F # 函式類型。

這可讓您使用 C# 程式碼中最沒用。
