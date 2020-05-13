---
title: F# 元件設計指導
description: '瞭解撰寫適用于其他呼叫者耗用量之 F # 元件的指導方針。'
ms.date: 05/14/2018
ms.openlocfilehash: 590bda0660d54ea73c590d31e694f3d499e0fd9f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209132"
---
# <a name="f-component-design-guidelines"></a>F# 元件設計指導

本檔是 F # 程式設計的一組元件設計方針，以 F # 元件設計方針、v14、Microsoft Research 和 F # Software Foundation 原先策劃並維護的版本為基礎。

本檔假設您已熟悉 F # 程式設計。 很多人都感謝 F # 的社區參與本指南各種版本的貢獻和有用的意見反應。

## <a name="overview"></a>概觀

本檔探討 F # 元件設計和程式碼的一些相關問題。 元件可以表示下列任何一項：

* F # 專案中的一層，其中包含該專案內的外部取用者。
* 一種程式庫，適用于跨元件界限的 F # 程式碼耗用量。
* 一種程式庫，適用于跨元件界限的任何 .NET 語言耗用量。
* 一種程式庫，用於透過套件存放庫（例如[NuGet](https://nuget.org)）散發。

本文中所述的技巧會遵循[良好 F # 程式碼的五個原則](index.md#five-principles-of-good-f-code)，因此會適當地使用功能和物件程式設計。

不論方法為何，元件和程式庫設計工具在嘗試製作最容易由開發人員使用的 API 時，都會面臨一些實際和平凡的問題。 Conscientious 應用程式的[.net 程式庫設計指導方針](../../standard/design-guidelines/index.md)，會引導您建立一組一致的 api，讓您有愉快的使用。

## <a name="general-guidelines"></a>一般指導方針

無論媒體櫃的目標物件為何，都有一些適用于 F # 程式庫的通用指導方針。

### <a name="learn-the-net-library-design-guidelines"></a>瞭解 .NET 程式庫設計指導方針

無論您執行的 F # 程式碼種類為何，都必須具備[.net 程式庫設計指導方針](../../standard/design-guidelines/index.md)的實用知識。 大部分其他的 F # 和 .NET 程式設計人員都將熟悉這些指導方針，並預期 .NET 程式碼符合它們。

.NET 程式庫設計指導方針提供有關命名、設計類別和介面、成員設計（屬性、方法、事件等）等的一般指引，而且是適用于各種設計指引的實用第一點參考。

### <a name="add-xml-documentation-comments-to-your-code"></a>將 XML 檔批註新增至您的程式碼

公用 Api 上的 XML 檔可確保使用者在使用這些類型和成員時，可以取得絕佳的 Intellisense 和 Quickinfo，並啟用程式庫的檔檔案。 請參閱[Xml 檔](../language-reference/xml-documentation.md)，以瞭解可用於 xmldoc 批註內其他標記的各種 xml 標記。

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo: otherPoint:Point -> float
```

您可以使用簡短形式 XML 批註（ `/// comment` ）或標準 XML 批註（ `///<summary>comment</summary>` ）。

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a>針對穩定的程式庫和元件 Api，請考慮使用明確的簽章檔案（. fsi.exe）

在 F # 程式庫中使用明確的簽章檔案，可提供公用 API 的簡潔摘要，協助確保您知道媒體櫃的完整公用介面，並提供公用檔和內部執行詳細資料的清楚分隔。 簽章檔案會要求在執行檔和簽章檔案中進行變更，藉此增加變更公用 API 的摩擦。 因此，通常只會在 API 已 solidified，且不再預期變更時，才會引進簽名檔案。

### <a name="always-follow-best-practices-for-using-strings-in-net"></a>一律遵循在 .NET 中使用字串的最佳作法

遵循[在 .net 中使用字串的最佳作法](../../standard/base-types/best-practices-strings.md)指引。 特別是，一律在轉換和比較字串時，明確陳述*文化目的*（如果適用）。

## <a name="guidelines-for-f-facing-libraries"></a>F # 面向程式庫的指導方針

本節提供開發公用 F # 面向程式庫的建議;也就是，程式庫會公開可供 F # 開發人員使用的公用 Api。 有各種不同的程式庫設計建議，特別適用于 F #。 如果沒有遵循的特定建議，.NET 程式庫設計指導方針就是回溯指引。

### <a name="naming-conventions"></a>命名慣例

#### <a name="use-net-naming-and-capitalization-conventions"></a>使用 .NET 命名和大小寫慣例

下表會遵循 .NET 命名和大小寫慣例。 另外還有一些小型的新增功能，也包括 F # 結構。

| 建構 | 案例 | 部分 | 範例 | 附註 |
|-----------|------|------|----------|-------|
| 具體類型 | PascalCase | 名詞/形容詞 | List、Double、Complex | 具體類型包括結構、類別、列舉、委派、記錄和等位。 雖然類型名稱在 OCaml 中是傳統小寫，但 F # 已採用類型的 .NET 命名配置。
| DLL           | PascalCase |                 | Fabrikam. Core .dll |  |
| 聯集標記     | PascalCase | 名詞 | 部分、新增、成功 | 請勿在公用 Api 中使用前置詞。 選擇性使用內部的前置詞，例如`type Teams = TAlpha | TBeta | TDelta.` |
| 事件          | PascalCase | 動詞命令 | ValueChanged/ValueChanging |  |
| 例外狀況     | PascalCase |      | WebException | 名稱的結尾應該是 "Exception"。 |
| 欄位          | PascalCase | 名詞 | CurrentName  | |
| 介面型別 |  PascalCase | 名詞/形容詞 | IDisposable | 名稱的開頭應為 "I"。 |
| 方法 |  PascalCase |  動詞命令 | ToString | |
| 命名空間 | PascalCase | | Fsharp.core 核心 | 通常 `<Organization>.<Technology>[.<Subnamespace>]` 會使用，但如果此技術與組織無關，則會捨棄組織。 |
| 參數 | camelCase | 名詞 |  類型名稱、轉換、範圍 | |
| let 值（內部） | camelCase 或 PascalCase | 名詞/動詞 |  getValue、myTable |
| let 值（外部） | camelCase 或 PascalCase | 名詞/動詞  | 清單。地圖，日期。今天 | 遵循傳統的功能設計模式時，let 系結的值通常是公用的。 不過，當識別碼可以從其他 .NET 語言使用時，通常會使用 PascalCase。 |
| 屬性  | PascalCase  | 名詞/形容詞  | IsEndOfFile，背景色彩  | 布林值屬性通常是使用，而且應該是肯定，如 IsEndOfFile，not IsNotEndOfFile。

#### <a name="avoid-abbreviations"></a>避免縮寫

.NET 指導方針不鼓勵使用縮寫（例如，「使用 `OnButtonClick` 而不是」 `OnBtnClick` ）。 一般的縮寫（例如 `Async` "非同步"）是容許的。 功能程式設計有時會忽略這種指導方針;例如，會 `List.iter` 使用「反復執行」的縮寫。 基於這個理由，使用縮寫傾向于 F # 對 F # 程式設計的程度更高，但在公用元件設計中，通常應該避免。

#### <a name="avoid-casing-name-collisions"></a>避免出現大小寫名稱衝突

.NET 方針表示，不能單獨使用大小寫來區分名稱衝突，因為有些用戶端語言（例如 Visual Basic）不區分大小寫。

#### <a name="use-acronyms-where-appropriate"></a>適當時使用縮寫

縮寫（例如 XML）不是縮寫，而且廣泛用於 .NET 程式庫中的 uncapitalized 格式（Xml）。 您應該只使用知名且廣泛辨識的縮略字。

#### <a name="use-pascalcase-for-generic-parameter-names"></a>針對泛型參數名稱使用 PascalCase

請在公用 Api 中使用 PascalCase 做為泛型參數名稱，包括 F # 面向的程式庫。 特別是， `T` `U` 針對任意的泛型參數使用、、、等名稱 `T1` `T2` ，而且當特定名稱合理時，針對 F # 對應的程式庫會使用 `Key` 、 `Value` 、 `Arg` （但不像）之類 `TKey` 的名稱。

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a>針對公用函式和 F # 模組中的值使用 PascalCase 或 camelCase

camelCase 適用于設計為不合格的公用函式（例如， `invalidArg` ），以及用於「標準集合函式」（例如，[清單]）的公用函數。 在這兩種情況下，函式名稱的運作方式非常類似于語言中的關鍵字。

### <a name="object-type-and-module-design"></a>物件、型別和模組設計

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a>使用命名空間或模組來包含您的類型和模組

元件中的每個 F # 檔案都應該以命名空間宣告或模組宣告為開頭。

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

使用模組和命名空間來組織最上層程式碼的差異如下：

* 命名空間可以跨越多個檔案
* 命名空間不能包含 F # 函式，除非它們位於內部模組內
* 任何指定模組的程式碼都必須包含在單一檔案中
* 最上層模組可以包含 F # 函式，而不需要內部模組

最上層命名空間或模組之間的選擇會影響已編譯的程式碼形式，因此，如果您的 API 最終是在 F # 程式碼之外使用，則會影響其他 .NET 語言的觀點。

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a>針對物件類型的內部作業使用方法和屬性

使用物件時，最好能確保可耗用的功能會實作為該類型的方法和屬性。

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

指定成員的大部分功能不一定要在該成員中執行，但是該功能的可耗用部分應該是。

#### <a name="use-classes-to-encapsulate-mutable-state"></a>使用類別封裝可變動的狀態

在 F # 中，這只需要在該狀態尚未由另一個語言結構（例如關閉、序列運算式或非同步計算）封裝的情況下完成。

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a>使用介面將相關的作業分組

使用介面類別型來代表一組作業。 這是慣用的其他選項，例如函數的元組或函式的記錄。

```fsharp
type Serializer =
    abstract Serialize<'T>: preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T>: preserveRefEq: bool -> pickle: string -> 'T
```

喜好設定：

```fsharp
type Serializer<'T> = {
    Serialize: bool -> 'T -> string
    Deserialize: bool -> string -> 'T
}
```

介面是 .NET 中的第一級概念，您可以用它來達到函子通常會提供給您的目標。 此外，它們可以用來將存在型別編碼到您的程式中，而不能使用哪些函式記錄。

#### <a name="use-a-module-to-group-functions-that-act-on-collections"></a>使用模組將作用於集合的函式群組在一起

當您定義集合類型時，請考慮提供新集合類型的一組標準作業， `CollectionType.map` `CollectionType.iter` 例如和）。

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

如果您包含這類別模組，請遵循 Fsharp.core 中找到之函式的標準命名慣例。

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a>使用模組將函式群組在一般的標準函式，特別是在數學和 DSL 程式庫中

例如， `Microsoft.FSharp.Core.Operators` 是由 fsharp.core 所提供的最上層函式的自動開啟集合（例如 `abs` 和 `sin` ）。

同樣地，統計資料連結庫可能會包含具有函數和的模組 `erf` `erfc` ，其中此模組是設計成明確或自動開啟的。

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a>請考慮使用 RequireQualifiedAccess 並謹慎套用 AutoOpen 屬性

將屬性加入模組中， `[<RequireQualifiedAccess>]` 表示模組可能無法開啟，而且對模組元素的參考需要明確限定的存取權。 例如， `Microsoft.FSharp.Collections.List` 模組具有這個屬性。

當模組中的函數和值有可能與其他模組中的名稱衝突的名稱時，這會很有用。 需要限定的存取權可能會大幅增加程式庫的長期維護性和 evolvability。

將 `[<AutoOpen>]` 屬性新增至模組，表示當包含的命名空間開啟時，將會開啟模組。 `[<AutoOpen>]`屬性也可以套用至元件，以指示在參考元件時自動開啟的模組。

例如，統計資料連結庫**MathsHeaven。統計資料**可能包含 `module MathsHeaven.Statistics.Operators` 包含函數 `erf` 和 `erfc` 。 將此模組標記為是合理的 `[<AutoOpen>]` 。 這表示 `open MathsHeaven.Statistics` 也會開啟此模組，並將名稱 `erf` 和帶入 `erfc` 範圍中。 的另一個好用適用 `[<AutoOpen>]` 于包含擴充方法的模組。

過度 `[<AutoOpen>]` 使用會導致污染命名空間，而屬性應謹慎使用。 針對特定網域中的特定程式庫，明智的使用 `[<AutoOpen>]` 可能會導致更好的可用性。

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a>請考慮在適當使用已知運算子的類別上定義運算子成員

有時候類別是用來建立數學結構（例如向量）的模型。 當模型化的網域具有已知的運算子時，將其定義為類別內建的成員會很有説明。

```fsharp
type Vector(x: float) =

    member v.X = x

    static member (*) (vector: Vector, scalar: float) = Vector(vector.X * scalar)

    static member (+) (vector1: Vector, vector2: Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

本指導方針對應至這些類型的一般 .NET 指引。 不過，在 F # 編碼中也可能更重要，因為這可讓這些類型與 F # 函式和方法搭配成員條件約束使用，例如 sumBy。

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a>請考慮使用 CompiledName 來提供。其他 .NET 語言取用者的網路易記名稱

有時候，您可能會想要針對 F # 取用者以一種樣式來命名專案（例如小寫的靜態成員，讓它看起來像是模組系結函式），但是在編譯成元件時，名稱的樣式是不同的。 您可以使用 `[<CompiledName>]` 屬性，為使用元件的非 F # 程式碼提供不同的樣式。

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

藉由使用 `[<CompiledName>]` ，您可以對元件的非 F # 取用者使用 .net 命名慣例。

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a>如果這樣做會提供更簡單的 API，請使用成員函式的方法多載

方法多載是一種功能強大的工具，可簡化可能需要執行類似功能的 API，但使用不同的選項或引數。

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

在 F # 中，多載引數數目，而不是引數的類型。

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a>如果這些類型的設計可能會進化，則隱藏記錄和聯集類型的標記法

避免洩漏物件的具體表示。 例如， <xref:System.DateTime> .net 程式庫設計的外部公用 API 不會顯示值的具體表示。 在執行時間，通用語言執行平臺會知道將在執行期間使用的已認可的執行。 不過，已編譯的程式碼本身並不會挑選具體表示的相依性。

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a>避免使用擴展的執行繼承

在 F # 中，很少使用執行繼承。 此外，繼承階層通常很複雜，而且在新的需求抵達時很難變更。 繼承執行仍然存在於 F # 中，以達到相容性和很罕見的情況，這是問題的最佳解決方案，但在設計多型（例如介面執行）時，應該在 F # 程式中尋找其他技術。

### <a name="function-and-member-signatures"></a>函式和成員簽章

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a>傳回少數多個不相關的值時，請使用元組做為傳回值

以下是在傳回型別中使用元組的絕佳範例：

```fsharp
val divrem: BigInteger -> BigInteger -> BigInteger * BigInteger
```

對於包含許多元件，或元件與單一可識別實體相關的傳回類型，請考慮使用命名類型，而不是元組。

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a>用於 `Async<T>` F # API 界限的非同步程式設計

如果有一個名為的對應同步作業會傳回 `Operation` `T` ，則如果非同步作業傳回，則應該將其命名為 `AsyncOperation` `Async<T>` `OperationAsync` `Task<T>` 。 對於公開 Begin/End 方法的常用 .NET 類型，請考慮使用 `Async.FromBeginEnd` 將擴充方法撰寫為外觀，以提供 F # 非同步程式設計模型給這些 .Net api。

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

若要瞭解例外狀況、結果和選項的適當用法，請參閱[錯誤管理](conventions.md#error-management)。

### <a name="extension-members"></a>延伸成員

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a>在 F #-F # 元件中仔細套用 F # 擴充成員

F # 延伸模組成員通常僅適用于內建作業關閉時的作業，而該類型與大部分的使用模式相關聯。 其中一個常見的用法是針對各種 .NET 類型提供更慣用至 F # 的 Api：

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

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a>使用區分聯集，而不是樹狀結構化資料的類別階層

類似樹狀結構的會以遞迴方式定義。 這對繼承並不難，但使用區分等位。

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

以區分等位來表示類似樹狀結構的資料也可讓您受益于模式比對中的 exhaustiveness。

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a>`[<RequireQualifiedAccess>]`在其大小寫不是完全唯一的聯集類型上使用

您可能會發現自己所在的網域，其名稱是不同專案的最佳名稱，例如區分聯集案例。 您可以使用 `[<RequireQualifiedAccess>]` 來區分大小寫名稱，以避免因為與語句順序相依而觸發混淆的錯誤 `open`

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a>如果這些類型的設計可能會進化，請隱藏二進位相容 Api 的區分等位的標記法

等位類型依賴于簡潔程式設計模型的 F # 模式比對表單。 如先前所述，如果這些類型的設計可能會進化，您應該避免洩漏具體的資料標記法。

例如，您可以使用私用或內部宣告或使用簽章檔案來隱藏區分聯集的標記法。

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

如果您不想要顯示區分的等位，可能會發現您不需要中斷使用者程式碼就能為您的程式庫進行版本。 相反地，請考慮顯示一或多個現用模式，以允許比類型的值進行模式比對。

現用模式提供了一種替代方式，可以使用模式比對來提供 F # 取用者，同時避免直接公開 F # 聯集類型。

### <a name="inline-functions-and-member-constraints"></a>內嵌函式和成員條件約束

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a>使用內嵌函式搭配隱含的成員條件約束和靜態解析的泛型型別來定義泛型數值演算法

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

在數學程式庫中，這是適用于公用 API 的功能。

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a>避免使用成員條件約束來模擬型別類別和未類型的輸入

您可以使用 F # 成員條件約束來模擬「未輸入」。 不過，使用此功能的成員不應該一般用於 F # 到 F # 程式庫設計。 這是因為以不熟悉或非標準隱含條件約束為基礎的程式庫設計，往往會使使用者程式碼變得不彈性，並系結至一個特定架構模式。

此外，以這種方式大量使用成員條件約束很有可能會產生非常長的編譯時間。

### <a name="operator-definitions"></a>運算子定義

#### <a name="avoid-defining-custom-symbolic-operators"></a>避免定義自訂符號運算子

自訂運算子在某些情況下是不可或缺的，而且在大型的實程式碼主體中非常有用的標記裝置。 針對程式庫的新使用者，命名函數通常較容易使用。 此外，自訂符號運算子可能難以記載，而且使用者會發現，因為 IDE 和搜尋引擎中現有的限制，而難以查閱運算子的說明。

因此，最好將您的功能發佈為命名函式和成員，而且只有在標記的優點超過檔和認知成本時，才會針對此功能公開運算子。

### <a name="units-of-measure"></a>測量單位

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a>小心使用在 F # 程式碼中新增型別安全的測量單位

其他 .NET 語言觀看時，會清除測量單位的其他輸入資訊。 請注意，.NET 元件、工具和反映將會看到類型-[san-單位]。 例如，c # 取用者會看到， `float` 而不是 `float<kg>` 。

### <a name="type-abbreviations"></a>類型縮寫

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a>小心使用類型縮寫來簡化 F # 程式碼

.NET 元件、工具和反映不會看到類型的縮寫名稱。 類型縮寫的顯著用法也可以讓定義域比實際的更為複雜，這可能會使取用者混淆。

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a>避免公用類型的類型縮寫，其成員和屬性本質上應該與要縮寫的類型所提供的不同

在此情況下，要縮寫的類型會顯示太多關於所定義之實際類型的表示。 相反地，請考慮將縮寫包裝在類別類型或單一案例的區分等位中（或者，當效能很重要時，請考慮使用結構類型來包裝縮寫）。

例如，將多個對應定義為 F # 對應的特殊案例很有吸引力，例如：

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

不過，此類型上的邏輯點標記法作業與對應上的作業不同，例如，查閱運算子對應是合理的。[key] 如果索引鍵不在字典中，則傳回空白清單，而不是引發例外狀況。

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a>從其他 .NET 語言使用之程式庫的指導方針

設計要從其他 .NET 語言使用的程式庫時，請務必遵守 .Net 連結[庫設計方針](../../standard/design-guidelines/index.md)。 在本檔中，這些程式庫會標記為 vanilla 的 .NET 程式庫，而不是使用 f # 的程式庫，而不受限制。 設計 vanilla .NET 程式庫表示提供熟悉和慣用的 Api，使其與其余 .NET Framework 一致，方法是將公用 API 中的 F # 特定結構的使用降至最低。 這些規則會在下列各節中說明。

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a>命名空間和類型設計（適用于用於其他 .NET 語言的程式庫）

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a>將 .NET 命名慣例套用至元件的公用 API

請特別注意使用縮寫名稱和 .NET 大小寫方針。

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a>使用命名空間、類型和成員做為元件的主要組織結構

包含公用功能的所有檔案都應該以宣告開頭 `namespace` ，而且命名空間中唯一的公開實體應該是類型。 請勿使用 F # 模組。

使用非公用模組來保存實作為程式碼、公用程式類型和公用程式函式。

靜態類型應優先于模組，因為它們可讓 API 的未來演變使用多載，以及可能不會在 F # 模組中使用的其他 .NET API 設計概念。

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

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a>如果類型的設計不會進化，請在 vanilla .NET Api 中使用 F # 記錄類型

F # 記錄類型會編譯成簡單的 .NET 類別。 這些適用于 Api 中的一些簡單、穩定的類型。 請考慮使用 `[<NoEquality>]` 和 `[<NoComparison>]` 屬性，以隱藏介面的自動產生。 也請避免在 vanilla .NET Api 中使用可變動的記錄欄位，因為這些會公開公用欄位。 請務必考慮類別是否會針對 API 的未來演進提供更有彈性的選項。

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

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a>隱藏 vanilla .NET Api 中的 F # 聯集類型標記法

F # 聯集類型不常用於整個元件界限，即使是 F # 對 F # 編碼也一樣。 它們是在元件和程式庫內部使用時的絕佳執行裝置。

設計 vanilla .NET API 時，請考慮使用私用宣告或簽章檔案來隱藏等位類型的標記法。

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

您也可以增強在內部使用聯集標記法的類型，以提供所需的。面向網路的 API。

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

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a>使用架構的設計模式設計 GUI 和其他元件

.NET 中有許多不同的架構可供使用，例如 WinForms、WPF 和 ASP.NET。 如果您要設計要在這些架構中使用的元件，則應該使用每個的命名和設計慣例。 例如，在 WPF 程式設計中，會針對您要設計的類別採用 WPF 設計模式。 對於使用者介面程式設計中的模型，請使用像是事件和以通知為基礎的集合之類的設計模式，例如在中找到的 <xref:System.Collections.ObjectModel> 。

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a>物件和成員設計（適用于從其他 .NET 語言使用的程式庫）

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a>使用 CLIEvent 屬性來公開 .NET 事件

`DelegateEvent`使用特定的 .net 委派類型 `EventArgs` （而不是 `Event` 預設使用此類型的）來建立， `FSharpHandler` 以便將事件以熟悉的方式發行至其他 .net 語言。

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

工作會在 .NET 中用來表示使用中的非同步計算。 工作的複合一般少於 F # `Async<T>` 物件，因為它們代表「已執行」的工作，而且無法以執行平行組合的方式組合在一起，或是隱藏取消信號和其他內容參數的傳播。

不過，無論如何，傳回工作的方法，都是 .NET 上非同步程式設計的標準標記法。

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int): Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

您通常也會想要接受明確的取消權杖：

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x: int): Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a>使用 .NET 委派類型，而不是 F # 函式類型

此處的 "F # 函式類型" 表示 "箭號" 類型 `int -> int` ，例如。

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

F # 函式類型會顯示為 `class FSharpFunc<T,U>` 其他 .net 語言，而且較不適合瞭解委派類型的語言功能和工具。 撰寫以 .NET Framework 3.5 或更高版本為目標的高階方法時， `System.Func` 和 `System.Action` 委派是正確發佈的 api，可讓 .net 開發人員以低摩擦的方式取用這些 api。 （以 .NET Framework 2.0 為目標時，系統定義的委派類型會受到限制; 請考慮使用預先定義的委派類型，例如 `System.Converter<T,U>` 或定義特定的委派類型）。

另一方面，對 F # 面向的程式庫而言，.NET 委派並非自然的（請參閱下一節的 F # 面向程式庫）。 因此，開發 vanilla .NET 程式庫的高階方法時，常見的實行策略是使用 F # 函式型別來撰寫所有的實作者，然後使用委派作為實際 F # 實作為的精簡外觀來建立公用 API。

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a>使用 TryGetValue 模式，而不是傳回 F # 選項值，而且偏好方法多載，以 F # 選項值做為引數

在 Api 中使用 F # 選項類型的常見模式，會在使用標準 .NET 設計技術的 vanilla .NET Api 中獲得更好的運用。 請考慮使用 bool 傳回類型加上 out 參數，而不是傳回 F # 選項值，如同 "TryGetValue" 模式。 而不是採用 F # 選項值做為參數，請考慮使用方法多載或選擇性引數。

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

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a>使用 .NET 集合介面類別型 IEnumerable \< T \> 和 IDictionary 索引 \< 鍵， \> 參數和傳回值的值

請避免使用具象的集合類型，例如 .NET 陣列 `T[]` 、F # `list<T>` 類型 `Map<Key,Value>` 和 `Set<T>` ，以及 .net 具體集合類型（例如） `Dictionary<Key,Value>` 。 .NET 程式庫設計指導方針有關於何時使用各種集合類型（例如）的良好建議 `IEnumerable<T>` 。 在某些情況下，某些情況下可接受陣列（）的某些使用 `T[]` ，而效能則是。 請注意 `seq<T>` ，這只是的 F # 別名 `IEnumerable<T>` ，因此 seq 通常是 VANILLA .net API 的適當類型。

而不是 F # 清單：

```fsharp
member this.PrintNames(names: string list) =
    ...
```

使用 F # 序列：

```fsharp
member this.PrintNames(names: seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a>使用 unit 類型做為方法的唯一輸入類型，以定義零引數方法，或當做唯一傳回類型來定義傳回 void 的方法

避免使用單位類型的其他用途。 這是很好的：

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x: int) = ()
```

這是不正確的：

```fsharp
member this.WrongUnit( x: unit, z: int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a>在 vanilla .NET API 界限上檢查是否有 null 值

F # 執行程式碼通常會有較少的 null 值，因為不變的設計模式和針對 F # 類型使用 null 常值的限制。 其他 .NET 語言通常會使用 null 做為值的頻率更高。 因此，公開 vanilla .NET API 的 F # 程式碼應該在 API 界限檢查參數是否為 null，並防止這些值更深入地轉換成 F # 的執行程式碼。 您 `isNull` 可以使用模式的函數或模式比對 `null` 。

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a>避免使用元組做為傳回值

相反地，偏好傳回包含匯總資料的已命名類型，或使用 out 參數傳回多個值。 雖然元組和結構元組存在於 .NET 中（包括結構元組的 c # 語言支援），但它們通常不會為 .NET 開發人員提供理想且預期的 API。

#### <a name="avoid-the-use-of-currying-of-parameters"></a>避免使用 currying 的參數

請改用 .NET 呼叫慣例 `Method(arg1,arg2,…,argN)` 。

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

提示：如果您要設計可從任何 .NET 語言使用的程式庫，則不會實際進行實驗性 c # 和 Visual Basic 程式設計，以確保您的程式庫能夠從這些語言中「感覺正確」。 您也可以使用 .NET 反映程式和 Visual Studio 物件瀏覽器等工具，確保程式庫和其檔會如預期般出現給開發人員。

## <a name="appendix"></a>附錄

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a>設計可供其他 .NET 語言使用之 F # 程式碼的端對端範例

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

讓我們看看這個 F # 型別如何使用另一個 .NET 語言來呈現給程式設計人員。 例如，大約的 c # "signature" 如下所示：

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

關於 F # 如何代表此處的結構，有一些值得注意的重點。 例如：

* 已保留引數名稱之類的中繼資料。

* 採用兩個引數的 F # 方法會變成接受兩個引數的 c # 方法。

* 函數和清單會變成 F # 程式庫中對應類型的參考。

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

C # 簽名現在如下所示：

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

為了準備此類型做為 vanilla .NET 程式庫的一部分而進行的修正，如下所示：

* 已調整數個名稱： `Point1` 、 `n` 、 `l` 和會 `f` `RadialPoint` 分別成為、 `count` 、 `factor` 和 `transform` 。

* 使用的傳回型別， `seq<RadialPoint>` 而不是使用 `RadialPoint list` 來變更清單結構，而不是使用 `[ ... ]` `IEnumerable<RadialPoint>` 。

* 使用 .NET 委派類型， `System.Func` 而不是 F # 函式類型。

這讓它在 c # 程式碼中的更好變得更大。
