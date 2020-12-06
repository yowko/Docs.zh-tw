---
title: 屬性
description: '瞭解 F # 屬性，這些屬性是代表與物件相關聯之值的成員。'
ms.date: 05/16/2016
ms.openlocfilehash: a2a4fbfc88831dcb5cad7a2da701969b2e98b2e3
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740194"
---
# <a name="properties"></a>屬性

*屬性* 是代表與物件相關聯之值的成員。

## <a name="syntax"></a>語法

```fsharp
// Property that has both get and set defined.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with [accessibility-modifier] get() =
    get-function-body
and [accessibility-modifier] set parameter =
    set-function-body

// Alternative syntax for a property that has get and set.
[ attributes-for-get ]
[ static ] member [accessibility-modifier-for-get] [self-identifier.]PropertyName =
    get-function-body
[ attributes-for-set ]
[ static ] member [accessibility-modifier-for-set] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName =
    get-function-body

// Alternative syntax for property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with get() =
    get-function-body

// Property that has set only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Automatically implemented properties.
[ attributes ]
[ static ] member val [accessibility-modifier] PropertyName = initialization-expression [ with get, set ]
```

## <a name="remarks"></a>備註

屬性代表物件導向程式設計中的「具有」關聯性，表示與物件實例相關聯的資料，或具有類型的靜態屬性。

您可以用兩種方式宣告屬性，取決於您是否要明確指定基礎值 (也稱為屬性的備份存放區) ，或者，如果您想要讓編譯器自動為您產生備份存放區。 一般而言，如果屬性具有非一般的實值，以及當屬性只是值或變數的簡單包裝函式時，您應該使用更明確的方式。 若要明確宣告屬性，請使用 `member` 關鍵字。 此宣告式語法後面接著指定 `get` 和 `set` 方法（也稱為 *存取* 子）的語法。 語法區段中顯示的各種明確語法形式適用于讀/寫、唯讀和僅限寫入屬性。 若為唯讀屬性，您只需定義 `get` 方法; 對於僅限寫入屬性，只定義 `set` 方法。 請注意，當屬性同時具有 `get` 和 `set` 存取子時，替代語法可讓您針對每個存取子指定不同的屬性和存取範圍修飾詞，如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

若為具有和方法的讀取/寫入屬性 `get` ， `set` 則和的順序 `get` `set` 可以反轉。 或者，您可以只提供顯示的語法 `get` ，以及顯示的語法， `set` 而不是使用結合的語法。 這麼做可讓您更輕鬆地將個人 `get` 或 `set` 方法批註起來，如果這是您可能需要做的事情。 下列程式碼顯示使用合併語法的替代方法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

保存屬性資料的私用值稱為「 *備份存放區*」。 若要讓編譯器自動建立備份存放區，請使用關鍵字 `member val` ，省略自我識別碼，然後提供運算式來初始化屬性。 如果屬性是可變動的，請包含 `with get, set` 。 例如，下列類別型別包含兩個自動執行的屬性。 `Property1` 是唯讀的，而且會初始化為提供給主要函式的引數，而且 `Property2` 是可設定的屬性，初始化為空字串：

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

自動執行的屬性是類型初始化的一部分，因此必須在任何其他成員定義之前包含它們，就像型別 `let` 定義中的系結和系結一樣 `do` 。 請注意，初始化自動執行之屬性的運算式只會在初始化時進行評估，而不是在每次存取屬性時進行評估。 這種行為與明確執行之屬性的行為不同。 這實際上是指將這些屬性初始化的程式碼會加入至類別的函式。 請考慮下列顯示這項差異的程式碼：

```fsharp
type MyClass() =
    let random  = new System.Random()
    member val AutoProperty = random.Next() with get, set
    member this.ExplicitProperty = random.Next()

let class1 = new MyClass()

printfn $"class1.AutoProperty = %d{class1.AutoProperty}"
printfn $"class1.ExplicitProperty = %d{class1.ExplicitProperty}"
```

**輸出**

```console
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

上述程式碼的輸出顯示，AutoProperty 的值會在重複呼叫時保持不變，而 ExplicitProperty 會在每次呼叫時變更。 這會示範每次不會評估自動執行之屬性的運算式，如同明確屬性的 getter 方法。

>[!WARNING]
>有一些程式庫（例如 Entity Framework () ）會在基類的函式 `System.Data.Entity` 中執行自訂作業，而這些函式在初始化自動執行的屬性時無法正常運作。 在這些情況下，請嘗試使用明確的屬性。

屬性可以是類別、結構、區分等位、記錄、介面和類型延伸的成員，也可以在物件運算式中定義。

屬性可以套用至屬性。 若要將屬性（attribute）套用至屬性（attribute），請將屬性（attribute）上的屬性（property）。 如需詳細資訊，請參閱[屬性](../attributes.md)。

依預設，屬性為 public。 存取範圍修飾詞也可以套用至屬性。 若要套用協助工具修飾詞，請在屬性名稱前面加入它（如果它要同時套用至 `get` 和方法） `set` ; `get` `set` 如果每個存取子需要不同的協助工具，請在和關鍵字之前加入。 *存取範圍修飾* 詞可以是下列其中一項： `public` 、 `private` 、 `internal` 。 如需詳細資訊，請參閱[存取控制](../access-control.md)。

每次存取屬性時，就會執行屬性執行。

## <a name="static-and-instance-properties"></a>靜態和實例屬性

屬性可以是靜態或實例屬性。 靜態屬性可以在沒有實例的情況下叫用，並用於與類型相關聯的值，而不是個別的物件。 若為靜態屬性，請省略自我識別碼。 實例屬性需要自我識別碼。

下列靜態屬性定義是以您有靜態欄位的案例為基礎，而該欄位 `myStaticValue` 是屬性的備份存放區。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

屬性也可以是類似陣列的，在這種情況下，它們稱為 *索引屬性*。 如需詳細資訊，請參閱 [索引屬性](indexed-properties.md)。

## <a name="type-annotation-for-properties"></a>屬性的類型注釋

在許多情況下，編譯器會有足夠的資訊從支援存放區的型別推斷屬性型別，但是您可以藉由加入型別注釋來明確設定型別。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a>使用屬性集存取子

您可以使用運算子來設定提供存取子的屬性 `set` `<-` 。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

輸出為 **20**。

## <a name="abstract-properties"></a>抽象屬性

屬性可以是抽象的。 如同方法一樣，這 `abstract` 表示有與屬性相關聯的虛擬分派。 抽象屬性可以是真正的抽象概念，也就是沒有相同類別中的定義。 因此，包含這類屬性的類別就是抽象類別。 或者，abstract 也可以表示屬性是虛擬的，而且在這種情況下，定義必須存在於相同的類別中。 請注意，抽象屬性不得為私用，而且如果一個存取子是抽象的，另一個存取子也必須是抽象的。 如需抽象類別的詳細資訊，請參閱 [抽象類別](../abstract-classes.md)。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a>另請參閱

- [成員](index.md)
- [方法](methods.md)
