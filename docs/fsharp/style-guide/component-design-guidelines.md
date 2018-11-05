---
title: F# 元件的設計指導方針
description: 了解撰寫 F# 元件供其他呼叫端耗用量的指導方針。
ms.date: 05/14/2018
ms.openlocfilehash: 446cba0f810af9517b655ef5741ddf7a919676d5
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "43488283"
---
# <a name="f-component-design-guidelines"></a>F# 元件的設計指導方針

這份文件是一組元件的設計方針 F# 程式，並根據 F# 元件設計指導方針，v14，Microsoft Research 與[另一個版本](https://fsharp.org/specs/component-design-guidelines/)原來策劃和由 F# Software Foundation 維護。

本文件假設您熟悉 F# 程式設計。 非常感謝 F# 社群貢獻的有用的回饋，本指南的不同版本。

## <a name="overview"></a>總覽

本文件探討某些與 F# 元件設計和編碼相關的問題。 元件可以代表下列其中一項：

* F# 專案具有該專案內的外部取用者中的層。
* 跨組件界限是供取用 F# 程式碼程式庫。
* 跨組件界限是供取用任何.NET 語言程式庫。
* 例如適用於透過套件存放庫發佈的程式庫[NuGet](https://nuget.org)。

請遵循本文中所述的技巧[五個良好的 F# 程式碼原則](index.md#five-principles-of-good-f-code)，因此使用兩者的功能和物件視程式設計。

方法，不論元件和程式庫的設計工具嘗試製作最容易供開發人員的 API 時面臨的一些實用又 prosaic 的問題。 暴增的應用程式的[.NET 程式庫設計方針](../../standard/design-guidelines/index.md)引導您建立一組一致的使用愉快的 Api。

## <a name="general-guidelines"></a>一般方針

有幾個通用的指導方針適用於 F# 程式庫，不論程式庫的目標對象。

### <a name="learn-the-net-library-design-guidelines"></a>了解.NET 程式庫設計方針

F# 撰寫程式碼執行的類型，不論是非常有用的具備的實用知識[.NET 程式庫設計方針](../../standard/design-guidelines/index.md)。 大部分其他 F# 和.NET 程式設計人員會很熟悉這些方針，並預期.NET 程式碼，以符合它們。

.NET 程式庫設計方針提供有關命名、 設計類別和介面、 成員 （屬性、 方法、 事件等） 的設計和等等的一般指導方針，並會很有用的第一個點的各種不同的設計指引的參考。

### <a name="add-xml-documentation-comments-to-your-code"></a>將 XML 文件註解新增至您的程式碼

公用 Api 上的 XML 文件確保使用者可以取得絕佳的 Intellisense 和 Quickinfo 時使用這些類型和成員，以及啟用建置文件庫的檔案。 請參閱[XML 文件](../language-reference/xml-documentation.md)有關各種可用 xmldoc 註解內的其他標記的 xml 標記。

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo : otherPoint:Point -> float
```

您可以使用其中一個的簡短形式 XML 註解 (`/// comment`)，或標準的 XML 註解 (`///<summary>comment</summary>`)。

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a>請考慮使用明確的簽章檔 (.fsi) 穩定的程式庫和元件的 Api

使用明確的簽章檔案中的 F# 程式庫提供簡潔的公用 API，這兩個可協助確保您知道您的程式庫的完整公用介面以及提供清楚的分隔公開文件之間和內部摘要實作詳細資料。 請注意，簽章檔案會新增摩擦，在變更公用 API 中，需要在實作和簽章檔案中進行的變更。 如此一來，簽章檔案時，應該通常只有引進 API 已成為目的並不會再預期有顯著的變更。

### <a name="always-follow-best-practices-for-using-strings-in-net"></a>一律遵循 在.NET 中使用字串的最佳作法

請遵循[在.NET 中使用字串的最佳作法](../../standard/base-types/best-practices-strings.md)指引。 特別是，一律明確地陳述*文化特性的意圖*中轉換字串的比較 （如果適用的話）。

## <a name="guidelines-for-f-facing-libraries"></a>F# 的指導方針-面向的程式庫

此章節提供建議，用於開發公用 F#-面向的程式庫;也就是公開供 F# 開發人員所使用的公用 Api 的程式庫。 有適用於特別 F# 的各種不同的程式庫設計建議。 如果沒有遵循的特定建議事項，.NET 程式庫設計方針會是後援的指引。

### <a name="naming-conventions"></a>命名規範

#### <a name="use-net-naming-and-capitalization-conventions"></a>使用.NET 名稱和大小寫慣例

下表會遵循.NET 命名和大小寫慣例。 有小型的新增項目也包含 F# 建構。

| 建構 | 案例 | 組件 | 範例 | 注意 |
|-----------|------|------|----------|-------|
| 具象類型 | PascalCase | 名詞 / 形容詞 | 清單、 Double、 複雜 | 具象型別是結構、 類別、 列舉、 委派、 記錄、 和等位。 雖然型別名稱是傳統上在 OCaml 小寫，F# 已採用類型的.NET 命名配置。
| DLL           | PascalCase |                 | Fabrikam.Core.dll |  |
| 等位標記     | PascalCase | 名詞 | 部分新增成功 | 請勿使用公用 Api 中的前置詞。 （選擇性） 使用的前置詞，當內部，例如 '' 輸入小組 = TAlpha | TBeta | TDelta。 ' ' |
| Event - 事件          | PascalCase | 動詞命令 | ValueChanged / ValueChanging |  |
| 例外狀況     | PascalCase |      | WebException | 名稱應該以"Exception"結尾。 |
| 欄位          | PascalCase | 名詞 | CurrentName  | |
| 介面型別 |  PascalCase | 名詞 / 形容詞 | IDisposable | 名稱應該以"I"開頭。 |
| 方法 |  PascalCase |  動詞命令 | ToString | |
| 命名空間 | PascalCase | | Microsoft.FSharp.Core | 通常會使用`<Organization>.<Technology>[.<Subnamespace>]`，不過卸除的組織，如果組織的技術無關。 |
| 參數 | camelCase | 名詞 |  類型名稱、 轉換、 範圍 | |
| 讓值 （內部） | camelCase 或 PascalCase | 名詞 / 動詞命令 |  getValue myTable |
| 讓值 （外部） | camelCase 或 PascalCase | 名詞/動詞命令  | List.map Dates.Today | let 繫結值通常是公用的遵循傳統的功能性設計模式時。 不過，通常使用 PascalCase 的識別碼可以使用其他.NET 語言時。 |
| 屬性  | PascalCase  | 名詞 / 形容詞  | IsEndOfFile，背景色彩  | 布林值屬性通常不使用，因為可以且應該是肯定的如同 IsEndOfFile，不 IsNotEndOfFile。

#### <a name="avoid-abbreviations"></a>避免縮寫

.NET 指導方針不鼓勵使用縮寫 (例如，「 使用`OnButtonClick`而非`OnBtnClick`")。 常用的縮寫，例如`Async`所容許的 「 非同步 」、。 函式程式設計，有時候會忽略此指導方針比方說，`List.iter`用於 「 逐一查看 」 的縮寫。 基於這個理由，使用縮寫傾向於容許更高的程度上，在 F#-至-F# 程式設計，但仍通常應該避免在公用元件設計中。

#### <a name="avoid-casing-name-collisions"></a>避免名稱衝突的大小寫

.NET 指導方針會假設，單獨的大小寫不能用來釐清發生名稱衝突，因為某些用戶端語言 (例如，Visual Basic) 都不區分大小寫。

#### <a name="use-acronyms-where-appropriate"></a>在適當時使用縮寫

首字母縮略字，例如 XML 不縮寫，且廣泛用於 uncapitalized 格式 (Xml) 的.NET 程式庫。 只應該使用已知且眾所公認的縮寫。

#### <a name="use-pascalcase-for-generic-parameter-names"></a>對泛型參數名稱使用 PascalCase

要針對公用 Api，包括 F# 中的泛型參數名稱使用 PascalCase-面向的程式庫。 特別的是，使用名稱，例如`T`， `U`， `T1`，`T2`任意的泛型參數，以及當特定名稱進行方面來看，然後 F#-面向的程式庫會使用名稱，例如`Key`， `Value`， `Arg`(但不是例如`TKey`)。

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a>使用 PascalCase 或 camelCase 公用函式] 和 [F# 模組中的值

camelCase 用於專為使用的公用函式不合格 (比方說， `invalidArg`)，以及 「 標準集合函式 」 （例如，List.map）。 在這兩種情況，函式名稱做為許多語言的關鍵字。

### <a name="object-type-and-module-design"></a>物件、 類型和模組的設計

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a>使用命名空間或模組來包含您的類型和模組

在元件中的每個 F# 檔案應該以命名空間宣告或模組宣告為開頭。

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

使用模組與命名空間來組織程式碼在最上層的差異如下所示：

* 命名空間可以跨多個檔案
* 命名空間不能包含 F# 函式，除非它們是在內部的模組中
* 任何指定的模組的程式碼必須包含在單一檔案
* 最上層模組可以包含 F# 函式而不需要內部的模組

最上層命名空間或模組之間的選擇會影響程式碼中，已編譯的形式，並因此會影響其他.NET 語言檢視應您的 API 最終取用外部 F# 程式碼。

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a>使用內建函式物件類型的作業的方法和屬性

當處理物件，最好是確定可取用的功能都實作為方法和屬性，該型別上。

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

大量的功能，為給定成員需要不一定會實作在該成員，但應該是可取用的一項，該功能。

#### <a name="use-classes-to-encapsulate-mutable-state"></a>使用類別來封裝可變動狀態

在 F# 中，這只需要完成，狀態未已封裝的另一個語言建構，例如關閉、 序列運算式中或非同步計算。

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a>使用介面來群組的相關作業

您可以使用介面型別來代表一組作業。 這是慣用的其他選項，例如 tuple 的函式或函式的記錄。

```fsharp
type Serializer =
    abstract Serialize<'T> : preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T> : preserveRefEq: bool -> pickle: string -> 'T
```

在到：

```fsharp
type Serializer<'T> = {
    Serialize : bool -> 'T -> string
    Deserialize : bool -> string -> 'T
}
```

介面是在.NET 中，您可用來達成什麼函式會正常提供您的第一級概念。 此外，它們可以用來編碼您的程式，記錄的函式不能存在的類型。

#### <a name="use-a-module-to-group-functions-which-act-on-collections"></a>在集合上使用群組函式，處理模組

當您定義集合型別時，請考慮提供一組標準的作業要`CollectionType.map`和`CollectionType.iter`) 新的集合類型。

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

如果您包含這類模組，請遵循 FSharp.Core 中找到的函式的標準命名慣例。

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a>使用群組函式模組通用的標準函式，尤其是在數學與 DSL 程式庫

比方說，`Microsoft.FSharp.Core.Operators`是最上層函式會自動開啟的集合 (例如`abs`和`sin`) 提供 FSharp.Core.dll。

同樣地，統計資料的程式庫可能包含具有函式的模組`erf`和`erfc`，此模組可明確或自動開啟。

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a>請考慮使用 RequireQualifiedAccess 並仔細套用 AutoOpen 屬性

新增`[<RequireQualifiedAccess>]`模組的屬性表示模組可能未開啟，而且參考的模組項目需要明確限定存取。 比方說，`Microsoft.FSharp.Collections.List`模組有這個屬性。

當函式和模組中的值有可能會與其他模組中的名稱發生衝突的名稱，這非常有用。 需要完整存取權可能會大幅增加的長期維護性和可演化性程式庫。

新增`[<AutoOpen>]`至模組的屬性表示開啟包含命名空間時，將會開啟模組。 `[<AutoOpen>]`屬性可能也會套用到組件，表示當組件參考時，會自動開啟模組。

比方說，統計資料的媒體櫃**MathsHeaven.Statistics**可能會包含`module MathsHeaven.Statistics.Operators`包含函式`erf`和`erfc`。 它是合理的作法是將標示為此模組`[<AutoOpen>]`。 這表示`open MathsHeaven.Statistics`也會開啟此模組並將名稱`erf`和`erfc`進入範圍內。 使用另一個良好`[<AutoOpen>]`會包含擴充方法的模組。

過度使用的`[<AutoOpen>]`污染的命名空間和屬性的潛在客戶應該小心使用。 針對特定的程式庫中特定網域，審慎使用`[<AutoOpen>]`可能會導致更好的可用性。

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a>請考慮在其中使用已知的運算子是適當的類別上定義運算子的成員

有時候類別用來建立模型的數學建構，例如向量。 正在模型化的網域有已知的運算子，定義為 「 內建函式類別的成員時，很有幫助。

```fsharp
type Vector(x:float) =

    member v.X = x

    static member (*) (vector:Vector, scalar:float) = Vector(vector.X * scalar)

    static member (+) (vector1:Vector, vector2:Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

本指南會對應至這些類型的一般.NET 指導方針。 不過，可以在 F# 編碼，因為這可讓這些型別可用於搭配 F# 函式和方法成員的條件約束，例如 List.sumBy 此外重要。

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a>請考慮使用 CompiledName 來提供。其他.NET 語言取用者的 NET 的易記名稱

有時您可能想要一個樣式中的項目命名為 F# 的取用者 (例如大小寫，使它顯示在靜態成員函式模組繫結一樣)，但有不同的樣式名稱，編譯成組件時。 您可以使用`[<CompiledName>]`非 F# 程式碼使用組件提供不同的樣式屬性。

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

使用`[<CompiledName>]`，您可以使用非 F# 取用者的組件的.NET 命名慣例。

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a>使用方法多載成員函式，如果這麼做可以提供更簡單的 API

方法多載是功能強大的工具簡化的 API，可能需要執行類似的功能，但使用不同的選項或引數。

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

在 F# 中，它是較常見的引數數目，而不是引數型別多載。

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a>隱藏記錄和聯集類型的表示，如果這些類型的設計都可能發展

以免洩露物件的具象表示法。 比方說，具象表示法的<xref:System.DateTime>值不會揭露外部、 公用 API 的.NET 程式庫設計。 在執行階段，Common Language Runtime 會知道將會在整個執行的認可的實作。 不過，已編譯程式碼不本身挑選的相依性的實體表示法。

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a>避免使用實作繼承的擴充性

在 F# 中，很少會使用實作繼承。 此外，繼承階層架構通常是複雜且難以變更的新要求到達時。 繼承實作仍然存在於 F# 的相容性和罕見的情況下，它是問題，最佳的解決方案，但設計多型，例如介面實作時，替代技術應該要在 F# 程式中的搜尋。

### <a name="function-and-member-signatures"></a>函式和成員的簽章

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a>使用傳回值的 tuple，傳回一小部分的多個不相關的值時

以下是使用 tuple，傳回的型別中的理想範例：

```fsharp
val divrem : BigInteger -> BigInteger -> BigInteger * BigInteger
```

傳回類型，而且包含許多元件，或在單一的識別實體相關的元件，請考慮使用具名型別，而不 tuple。

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a>使用`Async<T>`進行非同步程式設計，在 F# API 界限處

如果沒有對應的同步作業，名為`Operation`，會傳回`T`，則應命名為非同步作業`AsyncOperation`如果它傳回`Async<T>`或`OperationAsync`如果它傳回`Task<T>`。 為常用的.NET 型別公開 Begin/End 方法，請考慮使用`Async.FromBeginEnd`為外觀提供 F# 非同步程式設計模型的.NET Api 來撰寫擴充方法。

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

請參閱[錯誤管理](conventions.md#error-management)若要了解例外狀況、 結果和選項的適當用法。

### <a name="extension-members"></a>擴充成員

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a>請仔細套用 F# 擴充成員在 F#-至-F# 元件

F# 擴充成員通常只應位於與大多數的其模式的使用中的型別相關聯的內建作業的結束的作業。 常見用途之一是提供更慣用 F# 的各種.NET 類型的 Api:

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

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a>而不是類別階層架構的差別聯的集用於樹狀結構的資料

類似樹狀目錄結構是以遞迴方式定義。 這是很冗長，因此具有繼承，但差別聯集與雅緻。

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

表示差別等位類似樹狀目錄中的資料也可讓您受益於 exhaustiveness 在模式比對。

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a>使用`[<RequireQualifiedAccess>]`上其大小寫的名稱不是夠唯一的聯集類型

您可能會發現自己位於網域中相同名稱的不同項目，例如差異等位的情況下最適當的名稱。 您可以使用`[<RequireQualifiedAccess>]`若要區分大小寫的名稱，以避免觸發令人困惑所造成的錯誤，以遮蔽相依的排序`open`陳述式

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a>如果這些類型的設計都可能發展，隱藏差別聯集的表示二進位相容的 api

等位類型均依賴 F# 模式比對 form 的簡潔的程式撰寫模型。 如先前所述，您應該避免洩漏具體資料表示法，如果這些類型的設計都可能發展。

例如，已區分的聯集的表示法可能會隱藏使用私用或內部的宣告，或使用簽章檔案。

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

如果您廣泛地顯示差別聯的集，您可能會發現很難版本您的程式庫而不會中斷使用者程式碼。 相反地，請考慮顯示一或多個作用中的模式，以允許進行模式比對您類型的值。

作用中的模式提供 F# 取用者提供的模式比對，同時避免直接公開 F# 聯集類型的替代方式。

### <a name="inline-functions-and-member-constraints"></a>內嵌函式和成員的條件約束

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a>定義泛型的數值演算法與隱含的成員條件約束和以統計方式解析的泛型型別使用內嵌函式

算術成員條件約束和 F# 比較條件約束是 F# 程式設計的標準。 例如，請參考下列程式碼：

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

這是適合的函式，如需數學程式庫中的公用 API。

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a>請避免使用成員條件約束，以模擬型別類別和鴨子類型

就可以模擬"住輸入 「 使用 F# 成員條件約束。 不過，可讓成員使用這個屬性不在一般應在 F#-至-F# 程式庫設計。 這是因為在不熟悉或非標準隱含的條件約束為基礎的程式庫設計很容易導致使用者程式碼變得不具彈性且繫結至一個特定的架構模式。

此外，很可能會大量使用這種方式中的成員條件約束導致非常長的編譯時間。

### <a name="operator-definitions"></a>運算子定義

#### <a name="avoid-defining-custom-symbolic-operators"></a>應避免定義自訂的符號運算子

自訂運算子是不可或缺，在某些情況下，非常有用的影響力裝置極為龐大的實作程式碼內。 程式庫的新使用者，通常是容易使用具名函式。 此外，自訂的符號運算子可能很難文件，而且使用者尋找更難查詢運算子，因為 IDE 和搜尋引擎中的現有限制的說明。

如此一來，最好是發佈您的功能，為具名函式和成員，和此外公開 （expose） 運算子，這項功能只有當影響力的優點勝的文件和認知的成本來保留它們。

### <a name="units-of-measure"></a>測量單位

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a>小心使用 F# 程式碼中新增的型別安全的測量單位

檢視其他.NET 語言時，會清除輸入的其他資訊的單位量值。 請注意，.NET 元件、 工具和反映將會看到 san-單元的類型。 例如，C# 取用者會看到`float`而非`float<kg>`。

### <a name="type-abbreviations"></a>類型縮寫

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a>請仔細來簡化 F# 程式碼中使用類型縮寫

.NET 元件、 工具和反映不會看到類型縮寫的名稱。 類型縮寫的重要使用方式也可以讓出現越複雜，比它實際上是，這可能會感到困惑的取用者的網域。

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a>避免其成員和屬性應該在縮寫的型別上的可用本質上不同的公用類型的類型縮寫

在此情況下，在縮寫的類型會顯示太多有關所定義的實際類型的表示法。 相反地，包裝在類別類型或單一案例的已區分聯集的縮寫，請考慮 （或者，當效能很重要時，請考慮使用結構型別來包裝縮寫）。

例如，您會嘗試定義多重對應視為特殊案例的 F# 地圖，例如：

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

不過，這個型別上的邏輯的點標記法作業不是在地圖上的作業相同，比方說，是合理的 lookup 運算子對應。[索引鍵] 傳回空的清單，如果索引鍵不在字典中，而不是引發例外狀況。

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a>使用其他.NET 語言的程式庫的指導方針

在設計時使用其他.NET 語言的程式庫，請務必遵守[.NET 程式庫設計方針](../../standard/design-guidelines/index.md)。 本文件中，這些程式庫會標示為普通的.NET 程式庫，而不是 F#-面向的程式庫，使用 F# 建構不受任何限制。 設計開啟了香草的.NET 程式庫表示的最小化使用 F# 提供熟悉且慣用的 Api 與.NET Framework 的其餘部分一致-公用 API 中的特定建構。 下列各節中說明的規則。

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a>命名空間和類型的設計 （適用於讓您使用其他.NET 語言的程式庫）

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a>套用至您的元件的公用 API 的.NET 命名慣例

請特別注意使用縮寫的名稱和.NET 的大小寫方針。

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a>針對您元件的主要組織性結構為使用命名空間、 類型和成員

包含公開功能的所有檔案的都開頭`namespace`宣告，並只公開實體命名空間中的應該是類型。 請勿使用 F# 模組。

您可以使用非公用模組來保存實作程式碼、 公用程式類型和公用程式函式。

靜態類型應該是慣用的模組，透過它們允許使用多載和其他的.NET API 設計概念，不能使用 F# 模組內的 API 的未來發展。

比方說，取代下列的公用 API:

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

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a>如果類型的設計不會演化，vanilla.NET Api 中使用 F# 記錄型別

F# 記錄型別會編譯為一個簡單的.NET 類別。 這些是適用於 Api 中的一些簡單的穩定類型。 您應該考慮使用`[<NoEquality>]`和`[<NoComparison>]`屬性來隱藏自動產生的介面。 也請避免使用 vanilla.NET Api 中的可變動的記錄欄位，這些會公開為公用欄位。 請務必考慮是否類別會提供 API 的未來發展更具彈性的選項。

例如，下列 F# 程式碼會公開給 C# 取用者的公用 API:

F# 中：

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

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a>隱藏 F# 聯集類型 vanilla.NET Api 中的表示法

F# 等位型別不常用於跨元件界限，甚至是 F#-至-F# 撰寫程式碼。 也就是絕佳的實作裝置時在元件和程式庫內部使用。

在設計一種普通的.NET API 時，請考慮隱藏使用私用宣告或簽章檔案的聯集類型的表示法。

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

您可能也會擴充以提供所需的等位的表示法在內部使用與成員的類型.NET 後端 API。

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

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a>設計 GUI 和其他元件使用的 framework 的設計模式

另外還有許多不同的架構在.NET 內，例如 WinForms、 WPF 和 ASP.NET。 如果您要設計用於這些架構的元件，則應該使用命名與設計慣例，每個。 例如，針對 WPF 程式設計，採用 WPF 設計模式，您要設計的類別。 在使用者介面程式設計模型，使用 設計模式，例如事件和通知為基礎的集合，例如位於<xref:System.Collections.ObjectModel>。

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a>物件和成員的設計 （適用於讓您使用其他.NET 語言的程式庫）

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a>若要公開.NET 事件使用 CLIEvent 屬性

建構`DelegateEvent`與特定的.NET 委派接受物件的型別和`EventArgs`(而非`Event`，這只是使用`FSharpHandler`預設的型別)，讓事件發佈在其他.NET 語言的熟悉方式。

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

#### <a name="expose-asynchronous-operations-as-methods-which-return-net-tasks"></a>傳回.NET 工作方法公開非同步作業

在.NET 中使用工作來代表使用中的非同步計算。 工作處於較不撰寫 F# 比一般`Async<T>`物件，因為它們代表 「 執行 」 工作，並且組合在一起，執行平行的組合，或其中隱藏取消訊號和其他的傳播方式內容相關的參數。

不過，儘管如此，傳回工作的方法是在.NET 上的非同步程式設計的標準表示法。

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int) : Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

您會經常也要接受明確取消語彙基元：

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x:int) : Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a>使用.NET 的委派型別，而不是 F# 函式類型

這裡的 「 F# 函式類型 」 表示 「 箭頭 」 類型如`int -> int`。

而不是這個：

```fsharp
member this.Transform(f:int->int) =
    ...
```

請執行：

```fsharp
member this.Transform(f:Func<int,int>) =
    ...
```

F# 函式型別會顯示為`class FSharpFunc<T,U>`用於其他.NET 語言，因此較不適合用於語言功能和工具，了解委派類型。 撰寫目標設為.NET Framework 3.5 或更新版本，較高順序方法時`System.Func`和`System.Action`委派是正確的 Api，可讓.NET 開發人員使用這些 Api 以低摩擦方式發行。 (系統定義的委派類型時以.NET Framework 2.0 為目標，會更受到限制，請考慮使用預先定義的委派類型，例如`System.Converter<T,U>`或特定的委派型別定義。)

相反地，.NET 委派不自然的 F#-面向的程式庫 (請參閱下一節，在 F#-面向的程式庫)。 如此一來，常見的實作策略開發 vanilla.NET 程式庫的高階方法時是以編寫所有使用 F# 函式類型的實作，然後再建立一個精簡型的外觀，利用實際的 F# 為使用委派的公用 API實作。

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a>使用 TryGetValue 模式，而不是傳回 F# 選項值，並想要包含 F# 選項值做為引數的方法多載

在 Api 中的 F# 選項類型所用的常見模式是較佳 vanilla 中實作使用標準的.NET 的.NET Api 設計的技術。 而不是傳回的 F# 選項值，請考慮使用 bool 傳回型別，再加上"TryGetValue 」 模式與 out 參數。 而非採用 F# 選項值做為參數，請考慮使用方法多載或選擇性引數。

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

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a>使用.NET 集合介面型別 IEnumerable\<T\>和 IDictionary\<索引鍵、 值\>參數和傳回值

避免使用的具象集合類型，例如.NET 陣列`T[]`，F# 型別`list<T>`，`Map<Key,Value>`並`Set<T>`，以及.NET 的具象集合類型，例如`Dictionary<Key,Value>`。 .NET 程式庫設計方針有很好的建議，有關何時使用各種集合類型，例如`IEnumerable<T>`。 某些使用陣列 (`T[]`) 是可接受在某些情況下，效能地面上。 請注意，特別`seq<T>`是只是 F# 別名，以供`IEnumerable<T>`，並因此 seq 通常是一種普通的.NET API 的適當類型。

而不是 F# 清單：

```fsharp
member this.PrintNames(names : string list) =
    ...
```

使用 F# 順序：

```fsharp
member this.PrintNames(names : seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a>作為唯一的輸入類型的方法中的單位類型，定義零引數的方法，或作為唯一會傳回型別定義傳回 void 的方法

避免的單位類型的其他用途。 這些是很好：

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x : int) = ()
```

這是不正確：

```fsharp
member this.WrongUnit( x:unit, z:int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a>檢查開啟了香草的.NET API 界限上的 null 值

F# 實作程式碼通常會有較少 null 值的詳細資訊，所以不可變的設計模式，以及使用 F# 類型的 null 常值的限制。 其他.NET 語言通常會使用 null 值更為頻繁。 基於這個原因，應該檢查參數為 null 的 API 界限上，F# 程式碼公開一種普通的.NET API，並將其深入流入的 F# 實作程式碼時，防止這些值中。 `isNull`函式 」 或 「 模式比對`null`模式可用。

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a>請避免使用當做傳回值的 tuple

相反地，想傳回保留彙總的資料，或使用 out 參數傳回多個值的具名型別。 雖然在.NET 中存在的 tuple 和結構元組 （包括結構元組 C# 語言支援），它們通常不會提供理想的和預期的 API 適用於.NET 開發人員。

#### <a name="avoid-the-use-of-currying-of-parameters"></a>避免使用調用的參數

請改用.NET 呼叫慣例``Method(arg1,arg2,…,argN)``。

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

提示： 如果您設計讓您使用任何.NET 語言的程式庫，就無法取代的實際執行一些實驗性 C# 和 Visual Basic 程式設計，確保您的程式庫 」 操作權限 」 的這些語言。 您也可以使用.NET 反射程式和 Visual Studio 物件瀏覽器之類的工具，以確保程式庫和其文件會出現如預期般對開發人員。

## <a name="appendix"></a>附錄

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a>其他.NET 語言設計用於使用 F# 程式碼的端對端範例

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

推斷的 F# 類型的這個類別如下所示：

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

讓我們看看這個 F# 型別使用另一種.NET 語言的程式設計人員的顯示方式。 例如，大約 C# 「 簽章 」 如下所示：

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

有幾個重點来注意的 F# 如何代表這裡建構。 例如: 

* 已保留中繼資料，例如引數名稱。

* F# 方法採用兩個引數會變成 C# 方法採用兩個引數。

* 函式和清單會變成 F# 文件庫中的對應型別的參考。

下列程式碼示範如何調整此程式碼以納入考量的這些項目。

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

推斷的 F# 程式碼的類型如下所示：

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

若要準備使用這個型別因為 vanilla 的.NET 程式庫的一部分，如下所示，進行修正：

* 調整數個名稱： `Point1`， `n`， `l`，和`f`成為`RadialPoint`， `count`， `factor`，以及`transform`分別。

* 使用傳回型別`seq<RadialPoint>`而非`RadialPoint list`藉由變更清單建構 using`[ ... ]`序列建構使用`IEnumerable<RadialPoint>`。

* 使用.NET 的委派型別`System.Func`而不是以 F# 函式型別。

這可讓您使用 C# 程式碼到目前為止還棒。
