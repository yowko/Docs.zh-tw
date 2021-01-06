---
title: F# 元件設計指導
description: '瞭解撰寫適用于其他呼叫者取用之 F # 元件的指導方針。'
ms.date: 05/14/2018
ms.openlocfilehash: 24be2a422c97b9334f749e3d9dfcccd0feec219b
ms.sourcegitcommit: e395fabeeea5c705d243d246fa64446839ac85b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2021
ms.locfileid: "97856103"
---
# <a name="f-component-design-guidelines"></a>F# 元件設計指導

本檔是一組 F # 程式設計的元件設計方針，以 F # 元件設計指導方針、v14、Microsoft Research 以及 F # Software Foundation 原本策劃和維護的版本為基礎。

本檔假設您已熟悉 F # 程式設計。 很多人都感謝 F # 團體參與本指南的各種版本的投稿和實用意見反應。

## <a name="overview"></a>總覽

本檔探討一些與 F # 元件設計和程式碼相關的問題。 元件可以表示下列其中一項：

* 在 F # 專案中，具有該專案內外部取用者的圖層。
* 適用于跨元件界限的 F # 程式碼耗用量的程式庫。
* 一種程式庫，可供跨元件界限的任何 .NET 語言取用。
* 適用于透過套件存放庫（例如 [NuGet](https://nuget.org)）散發的程式庫。

本文所述的技術會遵循 [良好 F # 程式碼的五個準則](index.md#five-principles-of-good-f-code)，因此會適當地使用功能和物件程式設計。

無論是哪一種方法，元件和程式庫設計師在嘗試製作最容易使用的 API 時，都面臨許多實際和平凡的問題。 Conscientious 應用程式的 [.net 程式庫設計指導方針](../../standard/design-guidelines/index.md) ，將引導您建立一組一致的 api，以供使用。

## <a name="general-guidelines"></a>一般指導方針

F # 程式庫有一些適用的通用指導方針，而不考慮程式庫的目標物件。

### <a name="learn-the-net-library-design-guidelines"></a>瞭解 .NET 程式庫設計指導方針

無論您正在進行的 F # 程式碼撰寫種類為何，都有很大的説明，讓您瞭解 [.net 程式庫設計指導方針](../../standard/design-guidelines/index.md)。 大部分其他 F # 和 .NET 程式設計人員都將熟悉這些指導方針，並預期 .NET 程式碼必須符合這些方針。

.NET 程式庫設計指導方針提供有關命名、設計類別和介面、成員設計 (屬性、方法、事件等 ) 等等的一般指引，而且是各種設計指導的實用第一個參考重點。

### <a name="add-xml-documentation-comments-to-your-code"></a>將 XML 檔批註新增至您的程式碼

適用于公用 Api 的 XML 檔可確保使用者在使用這些類型和成員時，可以取得絕佳的 Intellisense 和 Quickinfo，並為文件庫啟用建立檔檔。 請參閱 [Xml 檔](../language-reference/xml-documentation.md) ，瞭解可用於 xmldoc 批註內其他標記的各種 xml 標記。

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo: otherPoint:Point -> float
```

您可以使用簡短形式的 XML 批註 (`/// comment`) ，或 () 的標準 XML 批註 `///<summary>comment</summary>` 。

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a>請考慮針對穩定的程式庫和元件 Api 使用明確的簽章檔案 ( fsi) 。

使用 F # 程式庫中的明確簽章檔案可提供公用 API 的簡潔摘要，這有助於確保您知道媒體櫃的完整公開介面，並提供公開檔和內部實作為詳細資料的清楚分隔。 簽章檔案會藉由要求在執行和簽章檔案中進行變更，而增加了變更公用 API 的分歧。 如此一來，通常只會在 API 已 solidified，且不再需要大幅變更時，才會引進簽名檔。

### <a name="always-follow-best-practices-for-using-strings-in-net"></a>一律遵循在 .NET 中使用字串的最佳作法

遵循 [在 .net 中使用字串的最佳作法](../../standard/base-types/best-practices-strings.md) 指引。 尤其是，在適當的) 的情況下，一律明確地在字串轉換和比較 (中陳述 *文化意圖* 。

## <a name="guidelines-for-f-facing-libraries"></a>F # 面向程式庫的指導方針

本節說明開發公用 F # 面向程式庫的建議;也就是說，程式庫會公開公用 Api，供 F # 開發人員使用。 針對 F #，有各種適用的程式庫設計建議。 如果沒有遵循的特定建議，.NET 程式庫設計指導方針就是回溯指引。

### <a name="naming-conventions"></a>命名規範

#### <a name="use-net-naming-and-capitalization-conventions"></a>使用 .NET 命名和大小寫慣例

下表會遵循 .NET 命名和大小寫慣例。 另外還包含 F # 結構的新增功能。

| 建構 | 案例 | 部分 | 範例 | 注意 |
|-----------|------|------|----------|-------|
| 具體類型 | PascalCase | 名詞/形容詞 | 清單、雙重、複雜 | 具體類型是結構、類別、列舉、委派、記錄和等位。 雖然型別名稱在 OCaml 中通常是小寫，但 F # 已採用類型的 .NET 命名配置。
| DLL           | PascalCase |                 | Fabrikam.Core.dll |  |
| 聯集標記     | PascalCase | 名詞 | 部分、新增、成功 | 請勿在公用 Api 中使用前置詞。 （選擇性）在內部使用前置詞，例如 `type Teams = TAlpha | TBeta | TDelta.` |
| 事件          | PascalCase | 動詞命令 | ValueChanged/ValueChanging |  |
| 例外狀況     | PascalCase |      | WebException | 名稱的結尾應該是「例外狀況」。 |
| 欄位          | PascalCase | 名詞 | CurrentName  | |
| 介面型別 |  PascalCase | 名詞/形容詞 | IDisposable | 名稱應該以 "I" 開頭。 |
| 方法 |  PascalCase |  動詞命令 | ToString | |
| 命名空間 | PascalCase | | Fsharp.core 核心 | 一般來說 `<Organization>.<Technology>[.<Subnamespace>]` ，如果該技術與組織無關，就會捨棄組織。 |
| 參數 | camelCase | 名詞 |  typeName、轉換、範圍 | |
| let 值 (內部)  | camelCase 或 PascalCase | 名詞/動詞 |  getValue、myTable |
| 讓值 (外部)  | camelCase 或 PascalCase | 名詞/動詞  | List. map，日期. Today | 在遵循傳統的功能設計模式時，let 系結值通常是公用的。 不過，當識別碼可以從其他 .NET 語言使用時，通常會使用 PascalCase。 |
| 屬性  | PascalCase  | 名詞/形容詞  | IsEndOfFile、背景色彩  | 布林值屬性通常使用的是，而且應該是肯定，如同在 IsEndOfFile 中，不會 IsNotEndOfFile。

#### <a name="avoid-abbreviations"></a>避免縮寫

.NET 指導方針不鼓勵使用縮寫 (例如「使用 `OnButtonClick` 而非」 `OnBtnClick` ) 。 常見的縮寫（例如「 `Async` 非同步」）是容許的。 這項指導方針有時會被忽略，以進行功能性程式設計;例如，會 `List.iter` 使用 "反覆運算" 的縮寫。 基於這個理由，使用縮寫通常可以在 F # 對 F # 程式設計中獲得更高的程度，但仍應避免在公用元件設計中使用。

#### <a name="avoid-casing-name-collisions"></a>避免大小寫名稱衝突

.NET 指導方針表示單獨使用大小寫，因為某些用戶端語言 (例如 Visual Basic) 不區分大小寫。

#### <a name="use-acronyms-where-appropriate"></a>適當時使用縮寫

XML 之類的縮寫不是縮寫，而是廣泛用於 .NET 程式庫中的 uncapitalized 格式 (Xml) 。 只應使用知名且廣泛辨識的縮寫。

#### <a name="use-pascalcase-for-generic-parameter-names"></a>使用 PascalCase 進行泛型參數名稱

請在公用 Api 中使用泛型參數名稱的 PascalCase，包括 F # 面向的程式庫。 尤其是，針對 `T` `U` 任意泛型參數使用、、、等名稱 `T1` `T2` ，而且當特定名稱有意義時，對於 F # 對應的程式庫，請使用如 `Key` 、 `Value` 、 `Arg` (但不是 `TKey`) 的名稱。

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a>將 PascalCase 或 camelCase 用於 F # 模組中的公用函式和值

camelCase 適用于設計為使用非限定 (的公用函式，例如 `invalidArg`) ，以及「標準集合函式」 (例如，List. map) 。 在這兩種情況下，函式名稱的作用相當於語言中的關鍵字。

### <a name="object-type-and-module-design"></a>物件、類型和模組設計

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a>使用命名空間或模組來包含您的類型和模組

元件中的每個 F # 檔案都應該以命名空間宣告或模組宣告做為開頭。

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

使用模組與命名空間來組織最上層程式碼的差異如下：

* 命名空間可以橫跨多個檔案
* 命名空間不能包含 F # 函數，除非它們在內部模組內
* 任何指定模組的程式碼都必須包含在單一檔案中
* 最上層模組可以包含 F # 函式，而不需要內部模組

最上層命名空間或模組之間的選擇會影響程式碼的編譯格式，因此，如果您的 API 最終是在 F # 程式碼之外使用，則會影響其他 .NET 語言的視圖。

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a>針對物件類型的作業使用方法和屬性

使用物件時，最好確保取用的功能會實作為該類型上的方法和屬性。

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

指定成員的大量功能不一定要在該成員中實作為，但該功能的取用部分應該是。

#### <a name="use-classes-to-encapsulate-mutable-state"></a>使用類別封裝可變動狀態

在 F # 中，這只需要在尚未由另一種語言結構（例如，關閉、序列運算式或非同步計算）封裝的狀態下完成。

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a>使用介面來分組相關的作業

使用介面類別型來代表一組作業。 這是其他選項的慣用選項，例如函數的元組或函式的記錄。

```fsharp
type Serializer =
    abstract Serialize<'T> : preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T> : preserveRefEq: bool -> pickle: string -> 'T
```

依喜好設定：

```fsharp
type Serializer<'T> = {
    Serialize: bool -> 'T -> string
    Deserialize: bool -> string -> 'T
}
```

介面是 .NET 中的第一級概念，您可以用來達成函子一般提供的功能。 此外，它們也可以用來將存在類型編碼到您的程式中，而無法使用哪些功能記錄。

#### <a name="use-a-module-to-group-functions-that-act-on-collections"></a>使用模組將處理集合的函式分組

當您定義集合類型時，請考慮為新的集合類型提供一組標準的作業，例如 `CollectionType.map` 和 `CollectionType.iter`) 。

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

如果您包含這類別模組，請遵循 Fsharp.core 中所找到函式的標準命名慣例。

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a>使用模組來分組一般標準函式的功能，特別是在數學和 DSL 程式庫中

例如， `Microsoft.FSharp.Core.Operators` 會自動開啟最上層函式的集合 (例如 `abs` 和 FSharp.Core.dll 所 `sin` 提供的) 。

同樣地，統計資料連結庫可能包含具有函式的模組， `erf` 以及 `erfc` 此模組是設計為明確或自動開啟的。

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a>考慮使用 RequireQualifiedAccess 並小心套用 AutoOpen 屬性

將 `[<RequireQualifiedAccess>]` 屬性新增至模組，表示模組可能無法開啟，而且模組的元素參考需要明確的存取權。 例如， `Microsoft.FSharp.Collections.List` 模組有這個屬性。

當模組中的函式和值有可能與其他模組中的名稱衝突的名稱時，這非常有用。 需要限定存取權可能會大幅增加資源庫的長期維護和 evolvability。

將 `[<AutoOpen>]` 屬性加入至模組時，表示當包含的命名空間開啟時，將會開啟模組。 `[<AutoOpen>]`屬性也可以套用至元件，以指出參考元件時自動開啟的模組。

例如，統計資料連結庫 **MathsHeaven。統計資料** 可能包含 `module MathsHeaven.Statistics.Operators` 包含函數 `erf` 和 `erfc` 。 將此模組標示為是合理的 `[<AutoOpen>]` 。 這表示 `open MathsHeaven.Statistics` 也會開啟此模組，並將名稱 `erf` 和移 `erfc` 至範圍中。 的另一種用法 `[<AutoOpen>]` 是針對包含擴充方法的模組。

過度 `[<AutoOpen>]` 使用潛在客戶污染命名空間，而屬性應謹慎使用。 針對特定網域中的特定程式庫，合理使用 `[<AutoOpen>]` 可能會導致更好的可用性。

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a>請考慮在適當使用已知運算子的類別上定義運算子成員

有時類別會用來建立數學結構（例如向量）的模型。 當模型化的網域有已知運算子時，將它們定義為類別內建的成員會很有説明。

```fsharp
type Vector(x: float) =

    member v.X = x

    static member (*) (vector: Vector, scalar: float) = Vector(vector.X * scalar)

    static member (+) (vector1: Vector, vector2: Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

本指南對應于這些類型的一般 .NET 指引。 不過，這在 F # 程式碼中可能也很重要，因為這可讓這些型別搭配使用 F # 函式和具有成員條件約束的方法，例如 sumBy。

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a>請考慮使用 CompiledName 來提供。其他 .NET 語言取用者的網路易記名稱

有時您可能會想要為 F # 取用者以一種樣式來命名某個樣式 (例如，以小寫的成員形式出現，使其看起來像是模組系結函式) ，但在編譯成元件時，名稱會有不同的樣式。 您可以使用 `[<CompiledName>]` 屬性，為使用元件的非 F # 程式碼提供不同的樣式。

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

藉由使用 `[<CompiledName>]` ，您可以針對元件的非 F # 取用者使用 .net 命名慣例。

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a>使用成員函式的方法多載，如果這樣做會提供更簡單的 API

方法多載是一種功能強大的工具，可簡化可能需要執行類似功能的 API，但使用不同的選項或引數。

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

在 F # 中，在引數數目而非引數類型上多載更為常見。

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a>如果這些類型的設計可能會進化，則隱藏記錄和聯集類型的表示

避免洩漏物件的具體標記法。 例如， <xref:System.DateTime> .net 程式庫設計的外部公用 API 不會顯示值的具體標記法。 在執行時間，通用語言執行平臺會知道將在執行期間使用的認可的實作為。 不過，已編譯的程式碼不會自行收取具體標記法的相依性。

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a>避免使用擴充性的實作為繼承

在 F # 中，很少使用執行繼承。 此外，繼承階層通常很複雜，而且在新的需求抵達時很難變更。 在 F # 中，繼承實行仍存在於 F # 中，以提供最適合問題的解決方案，但在設計多型（例如介面執行）時，您應該在 F # 程式中尋找替代的技巧。

### <a name="function-and-member-signatures"></a>函式和成員特徵標記

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a>傳回少量的多個不相關值時，使用元組來傳回值

以下是在傳回型別中使用元組的絕佳範例：

```fsharp
val divrem: BigInteger -> BigInteger -> BigInteger * BigInteger
```

針對包含許多元件的傳回型別，或元件與單一可識別實體相關的位置，請考慮使用命名的型別，而不是元組。

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a>`Async<T>`在 F # API 界限上用於非同步程式設計

如果有一個名為的對應同步作業會傳回 `Operation` `T` ，則非同步作業應命名為， `AsyncOperation` 如果它傳回 `Async<T>` 或傳回 `OperationAsync` `Task<T>` 。 對於公開 Begin/End 方法的常用 .NET 型別，請考慮使用 `Async.FromBeginEnd` 將擴充方法撰寫為外觀，以提供 F # 非同步程式設計模型給這些 .Net api。

```fsharp
type SomeType =
    member this.Compute(x:int): int =
        ...
    member this.AsyncCompute(x:int): Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a>例外狀況

請參閱 [錯誤管理](conventions.md#error-management) ，以瞭解例外狀況、結果和選項的適當用法。

### <a name="extension-members"></a>延伸模組成員

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a>謹慎地在 F # 到 F # 元件中套用 F # 擴充功能成員

F # 延伸模組成員通常只適用于在大部分使用模式中，與型別相關聯之內建作業的封閉作業。 其中一個常見用途是提供針對各種 .NET 類型更慣用至 F # 的 Api：

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a>聯集類型

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a>針對樹狀結構資料使用差異聯集，而非類別階層

以遞迴方式定義類似樹狀結構的結構。 這對繼承很麻煩，但是具有差異聯集的優雅。

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

以差異聯集表示類似樹狀結構的資料也可讓您在模式比對中受益于 exhaustiveness。

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a>使用 `[<RequireQualifiedAccess>]` 案例名稱不是足夠唯一的等位類型

您可能會發現某個網域中的相同名稱是不同專案的最佳名稱，例如差異聯集案例。 您可以使用 `[<RequireQualifiedAccess>]` 來區分大小寫名稱，以避免因為因遮蔽而相依于語句順序而觸發混淆錯誤 `open`

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a>如果這些類型的設計可能會進化，請隱藏二進位相容性聯集的區分等位表示

等位型別依賴 F # 模式比對形式來提供簡潔的程式設計模型。 如先前所述，如果這些類型的設計可能會進化，您應該避免暴露具體的資料標記法。

例如，您可以使用私用或內部宣告或使用簽章檔案來隱藏差異聯集的標記法。

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

如果您不小心地顯示差異聯集，您可能會發現不需要中斷使用者程式碼就能為您的程式庫進行版本。 相反地，請考慮公開一或多個使用中的模式，以允許您類型值的模式比對。

現用模式提供了一種替代方式，可提供 F # 取用者與模式比對，同時避免直接公開 F # 等位類型。

### <a name="inline-functions-and-member-constraints"></a>內嵌函式和成員條件約束

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a>使用具有隱含成員條件約束和靜態解析泛型型別的內嵌函式來定義泛型數值演算法

算術成員條件約束和 F # 比較準則約束是 F # 程式設計的標準。 例如，請參考下列程式碼：

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

這是適用于數學程式庫中公用 API 的功能。

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a>避免使用成員條件約束來模擬型別類別和打字型別

您可以使用 F # 成員條件約束來模擬「打字打字」。 不過，使用此功能的成員通常不應該用於 F # 對 F # 程式庫設計中。 這是因為根據不熟悉或非標準隱含條件約束的程式庫設計，通常會導致使用者的程式碼變差，並系結至一個特定的架構模式。

此外，在這種情況下大量使用成員條件約束很有可能會導致編譯時間很長。

### <a name="operator-definitions"></a>運算子定義

#### <a name="avoid-defining-custom-symbolic-operators"></a>避免定義自訂符號運算子

自訂運算子在某些情況下是不可或缺的，而且在大型的實作為程式碼主體內是非常有用的標記裝置。 針對程式庫的新使用者，命名函式通常更容易使用。 此外，自訂符號運算子可能很難記載，而且使用者發現因為 IDE 和搜尋引擎有現有的限制，所以更難以查閱運算子的說明。

因此，最好以命名函式和成員的形式發行您的功能，並在標記權益超過檔和擁有這些專案的認知成本時，另外公開此功能的運算子。

### <a name="units-of-measure"></a>測量單位

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a>針對 F # 程式碼中新增的型別安全，謹慎使用測量單位

其他 .NET 語言查看時，會清除度量單位的其他輸入資訊。 請注意，.NET 元件、工具和反映將會看到類型-san 單位。 例如，c # 取用者會看到 `float` 而不是 `float<kg>` 。

### <a name="type-abbreviations"></a>類型縮寫

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a>謹慎使用類型縮寫以簡化 F # 程式碼

.NET 元件、工具和反映將不會看到類型的縮寫名稱。 類型縮寫的顯著用法也可能使定義域比實際的更複雜，這可能會讓取用者混淆。

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a>避免其成員和屬性本質上不同于要縮寫之類型上的公用類型的類型縮寫

在此情況下，要縮寫的型別會顯示太多關於所定義之實際型別的標記法。 相反地，請考慮將縮寫包裝在類別類型或單一案例的差異聯集 (或者，當效能為必要時，請考慮使用結構類型將縮寫) 包裝。

例如，將多個地圖定義為 F # 地圖的特殊案例很吸引人，例如：

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

不過，這種類型上的邏輯點標記運算與地圖上的作業不同，例如，lookup 運算子對應是合理的。[key] 如果索引鍵不在字典中，則傳回空的清單，而不是引發例外狀況。

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a>從其他 .NET 語言使用的程式庫指導方針

設計用來從其他 .NET 語言使用的程式庫時，請務必遵守 [.net 程式庫設計指導方針](../../standard/design-guidelines/index.md)。 在本檔中，這些程式庫會標示為香草 .NET 程式庫，而非使用 F # 結構的 F # 對應程式庫，而不受限制。 設計香草 .NET 程式庫表示讓熟悉且慣用的 Api 與其余 .NET Framework 保持一致，方法是將在公用 API 中使用 F # 特定的結構降至最低。 下列各節將說明這些規則。

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a>適用于程式庫的命名空間和型別設計 (可用於其他 .NET 語言) 

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a>將 .NET 命名慣例套用至元件的公用 API

請特別注意縮寫名稱和 .NET 大寫準則的使用。

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a>使用命名空間、類型和成員作為元件的主要組織結構

所有包含公用功能的檔案都應該以宣告開頭 `namespace` ，且命名空間中的唯一公開實體應該是類型。 請勿使用 F # 模組。

使用非公用模組來保存實作為程式碼、公用程式類型和公用程式函式。

靜態類型應優先于模組，因為它們可讓 API 的未來演進使用多載和其他可能不會在 F # 模組中使用的 .NET API 設計概念。

例如，取代下列公用 API：

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

請改為考慮：

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a>如果類型的設計不會進化，請在香草 .NET Api 中使用 F # 記錄類型

F # 記錄類型會編譯成簡單的 .NET 類別。 這些適用于 Api 中一些簡單、穩定的類型。 請考慮使用 `[<NoEquality>]` 和 `[<NoComparison>]` 屬性來抑制自動產生介面。 也請避免在香草 .NET Api 中使用可變動的記錄欄位，因為這些欄位會公開公用欄位。 請一律考慮類別是否會為未來的 API 演進提供更有彈性的選項。

例如，下列 F # 程式碼會向 c # 取用者公開公用 API：

F#：

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing: int
        SecondThing: string }
```

C#：

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a>在香草 .NET Api 中隱藏 F # 聯集類型的標記法

F # 等位類型通常不會跨元件界限使用，即使是 F # 對 F # 程式碼。 它們是在元件和程式庫內部使用的絕佳實作為裝置。

設計香草 .NET API 時，請考慮使用私用宣告或簽章檔案來隱藏聯集類型的表示。

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

您也可以增強在內部使用聯集表示的類型，以提供所需的成員。.NET 面向的 API。

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

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a>使用架構的設計模式來設計 GUI 和其他元件

.NET 中提供許多不同的架構，例如 WinForms、WPF 和 ASP.NET。 如果您要設計要在這些架構中使用的元件，則應該使用每個的命名和設計慣例。 例如，針對 WPF 程式設計，採用 WPF 設計模式來設計您所設計的類別。 針對使用者介面程式設計中的模型，請使用如中所找到的設計模式，例如事件和以通知為基礎的集合 <xref:System.Collections.ObjectModel> 。

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a>程式庫的物件和成員設計 (，以供其他 .NET 語言使用) 

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a>使用 CLIEvent 屬性來公開 .NET 事件

`DelegateEvent`使用特定的 .net 委派型別來建立，此型別會採用物件並 `EventArgs` (，而不是 `Event` 使用預設的型別，而是使用 `FSharpHandler` 預設的型別) 讓事件以熟悉的方式發佈到其他 .net 語言。

```fsharp
type MyBadType() =
    let myEv = new Event<int>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish

type MyEventArgs(x: int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-that-return-net-tasks"></a>將非同步作業公開為傳回 .NET 工作的方法

工作會在 .NET 中用來代表使用中的非同步計算。 工作通常比 F # 物件的複合少 `Async<T>` ，因為它們代表「已在執行」的工作，而且無法以執行平行組合的方式組合在一起，或隱藏取消信號和其他內容參數的傳播。

不過，無論如何，傳回工作的方法都是 .NET 上非同步程式設計的標準標記法。

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int): Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

您通常也會想要接受明確的解除標記：

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x: int): Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a>使用 .NET 委派型別，而非 F # 函式類型

這裡的「F # 函式類型」表示「箭號」類型 `int -> int` ，例如。

而不是：

```fsharp
member this.Transform(f: int->int) =
    ...
```

執行此動作：

```fsharp
member this.Transform(f: Func<int,int>) =
    ...
```

F # 函式類型會顯示為 `class FSharpFunc<T,U>` 其他 .net 語言，而且較不適合瞭解委派類型的語言功能和工具。 撰寫以 .NET Framework 3.5 或更高版本為目標的較高順序方法時， `System.Func` 和 `System.Action` 委派是正確發佈的 api，可讓 .net 開發人員以低摩擦的方式取用這些 api。  (以 .NET Framework 2.0 為目標時，系統定義的委派類型會受到更多限制;請考慮使用預先定義的委派類型，例如 `System.Converter<T,U>` 或定義特定的委派類型。 ) 

另一方面，.NET 委派不是 F # 面向程式庫的自然 (請參閱下一節的 F # 面向程式庫) 。 因此，開發香草 .NET 程式庫的高階方法時，常見的採用策略是使用 F # 函式類型來撰寫所有的實作者，然後使用委派作為實際 F # 實作為之上的精簡外觀來建立公用 API。

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a>使用 TryGetValue 模式，而不是傳回 F # 選項值，而且偏好使用方法多載，以 F # 選項值做為引數

Api 中 F # 選項類型的常見使用模式，是使用標準 .NET 設計技術，在香草 .NET Api 中進行更好的運用。 請考慮使用 bool 傳回型別加上 out 參數，如同 "TryGetValue" 模式，而不是傳回 F # 選項值。 而不是將 F # 選項值作為參數，而是考慮使用方法多載或選擇性引數。

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal: byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x: int, y: int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x: int) = x

member this.ParamOverload(x: int, y: int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a>使用 .NET 集合介面類別型 IEnumerable \<T\> 和 IDictionary \<Key,Value\> 作為參數和傳回值

避免使用具象的集合類型，例如 .NET 陣列、F # 型別和 .NET 具象的 `T[]` `list<T>` `Map<Key,Value>` `Set<T>` 集合類型（例如） `Dictionary<Key,Value>` 。 .NET 程式庫設計指導方針對於使用各種集合類型（例如）有很大的建議 `IEnumerable<T>` 。 在某些情況下，您可以在效能的情況下，使用陣列 () 的某些用途 `T[]` 。 請注意 `seq<T>` ，特別是的 F # 別名 `IEnumerable<T>` ，因此 seq 通常是香草 .net API 的適當類型。

而非 F # 清單：

```fsharp
member this.PrintNames(names: string list) =
    ...
```

使用 F # 序列：

```fsharp
member this.PrintNames(names: seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a>您可以使用單位類型作為方法的唯一輸入類型來定義零引數方法，或使用唯一的傳回型別來定義 void 傳回方法。

避免使用單位類型的其他用途。 這些都很好：

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x: int) = ()
```

這是不好的：

```fsharp
member this.WrongUnit( x: unit, z: int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a>在香草 .NET API 界限上檢查是否有 null 值

F # 的程式碼通常會有較少的 null 值，因為不可變的設計模式，以及對 F # 類型使用 null 常值的限制。 其他 .NET 語言通常會使用 null 做為值更頻繁。 因此，公開香草 .NET API 的 F # 程式碼應該在 API 界限上檢查 null 的參數，並防止這些值更深入地流向 F # 程式碼。 您 `isNull` 可以使用模式上的函數或模式比對 `null` 。

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a>避免使用元組作為傳回值

相反地，最好是傳回持有匯總資料的命名型別，或使用 out 參數傳回多個值。 雖然元組和結構元組存在於 .NET (包括結構元組) 的 c # 語言支援，但它們最常不提供適用于 .NET 開發人員的理想和預期 API。

#### <a name="avoid-the-use-of-currying-of-parameters"></a>避免使用參數的 currying

相反地，請使用 .NET 呼叫慣例 `Method(arg1,arg2,…,argN)` 。

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

秘訣：如果您要設計可從任何 .NET 語言使用的程式庫，則不會實際執行一些實驗性 c # 和 Visual Basic 程式設計，以確保您的程式庫能夠從這些語言中「感覺正確」。 您也可以使用 .NET 反映程式和 Visual Studio 物件瀏覽器之類的工具，以確保程式庫及其檔會如預期般出現給開發人員。

## <a name="appendix"></a>附錄

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a>設計其他 .NET 語言使用之 F # 程式碼的端對端範例

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

此類別的推斷 F # 類型如下所示：

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

讓我們來看看如何使用另一個 .NET 語言，讓程式設計人員看到 F # 型別。 例如，大約的 c # "signature" 如下所示：

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

關於 F # 如何在這裡表示結構，有一些重要的重點需要注意。 例如：

* 中繼資料（例如引數名稱）已保留。

* 採用兩個引數的 F # 方法會變成採用兩個引數的 c # 方法。

* 函數和清單會成為 F # 程式庫中對應類型的參考。

下列程式碼示範如何調整此程式碼，以將這些專案納入考慮。

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

程式碼的推斷 F # 類型如下所示：

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

C # 簽章現在如下所示：

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

準備此類型以做為香草 .NET 程式庫一部分的修正，如下所示：

* 已調整數個名稱： `Point1` 、 `n` 、 `l` 和會 `f` `RadialPoint` 分別成為、、 `count` `factor` 和 `transform` 。

* 使用的傳回型別， `seq<RadialPoint>` 而不是藉 `RadialPoint list` 由將使用的清單結構變更 `[ ... ]` 為的順序結構 `IEnumerable<RadialPoint>` 。

* 使用 .NET 委派型別， `System.Func` 而非 F # 函數類型。

這使得在 c # 程式碼中使用的更好變得更容易。
