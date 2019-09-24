---
title: 屬性
description: 瞭解F#屬性，這是代表與物件相關聯之值的成員。
ms.date: 05/16/2016
ms.openlocfilehash: c71d61e033501c2d535b5582c82d36ed8cb2241b
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216427"
---
# <a name="properties"></a>屬性

*屬性*（property）是代表與物件相關聯之值的成員。

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

屬性代表物件導向程式設計中的「具有」關聯性，代表與物件實例相關聯的資料，或針對具有類型的靜態屬性。

您可以透過兩種方式宣告屬性，取決於您是否要明確指定屬性的基礎值（也稱為備份存放區），還是要讓編譯器自動為您產生備份存放區。 一般而言，如果屬性具有非一般的實作為，而當屬性只是值或變數的簡單包裝函式時，您應該使用更明確的方式。 若要明確宣告屬性，請使用`member`關鍵字。 這個宣告式語法後面會接著指定`get`和`set`方法（也稱為*存取*子）的語法。 語法一節中顯示的各種明確語法形式，會用於讀取/寫入、唯讀和僅限寫入的屬性。 若為唯讀屬性，您只`get`需定義方法; 對於僅限寫入屬性， `set`只定義方法。 請注意，當屬性同時`get`具有和`set`存取子時，替代語法可讓您指定每個存取子的不同屬性和存取範圍修飾詞，如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

對於同時`get`具有`set`和`set`方法的讀取/寫入屬性，和的順序可以反轉。`get` 或者，您可以只提供針對`get`所顯示的語法，以及僅針對`set`所顯示的語法，而不是使用結合的語法。 這麼做可讓您更輕鬆地將個別`get`或`set`方法標記為批註，如果這是您可能需要做的事情。 下列程式碼顯示使用結合語法的替代方法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

保存屬性資料的私用值稱為「*備份存放區*」。 若要讓編譯器自動建立備份存放區，請使用關鍵字`member val`，省略自我識別碼，然後提供運算式來初始化屬性。 如果屬性是可變動的，請包含`with get, set`。 例如，下列類別類型包含兩個自動實作為屬性。 `Property1`是唯讀的，而且會初始化為提供給主要函式的引數， `Property2`而且是可設定的屬性，初始化為空字串：

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

自動執行的屬性是型別初始化的一部分，因此必須包含在其他任何成員定義之前，就像型別`let`定義中`do`的系結和系結一樣。 請注意，初始化自動執行之屬性的運算式，只會在初始化時評估，而且不會在每次存取屬性時進行評估。 這種行為與明確實作為屬性的行為相較之下。 這實際上的意思是，將這些屬性初始化的程式碼會新增至類別的函式。 請考慮下列顯示這項差異的程式碼：

```fsharp
type MyClass() =
    let random  = new System.Random()
    member val AutoProperty = random.Next() with get, set
    member this.ExplicitProperty = random.Next()

let class1 = new MyClass()

printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
```

**輸出**

```console
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

上述程式碼的輸出顯示重複呼叫時，AutoProperty 的值不變，而 ExplicitProperty 會在每次呼叫時變更。 這會示範每次不會評估自動執行之屬性的運算式，這是明確屬性的 getter 方法。

>[!WARNING]
>有一些程式庫（例如 Entity Framework （`System.Data.Entity`），它會在基類處理常式中執行自訂作業，而這些函式無法與自動執行之屬性的初始化搭配運作。 在這些情況下，請嘗試使用明確的屬性。

屬性可以是類別、結構、區分等位、記錄、介面和類型延伸的成員，而且也可以在物件運算式中定義。

屬性可以套用至屬性。 若要將屬性套用至屬性，請在屬性前面的個別行上寫入屬性。 如需詳細資訊，請參閱[屬性](../attributes.md)。

根據預設，屬性是公用的。 協助工具修飾詞也可以套用至屬性。 若要套用協助工具修飾詞，請在屬性名稱前面加上它（如果它要套用`get`至和`set`方法），如果有不同的存取範圍`set` ，請在`get`和關鍵字之前加入每個存取子的必要項。 *協助工具修飾*詞可以是下列其中一項： `public`、 `private`、 `internal`。 如需詳細資訊，請參閱[存取控制](../access-control.md)。

每次存取屬性時，都會執行屬性部署。

## <a name="static-and-instance-properties"></a>靜態和實例屬性

屬性可以是靜態或實例屬性。 靜態屬性可以在不使用實例的情況下叫用，並用於與類型相關聯的值，而不是個別物件。 若為靜態屬性，請省略自我識別碼。 實例屬性需要自我識別碼。

下列靜態屬性定義是以您具有靜態欄位`myStaticValue`的實例為基礎，該屬性是屬性的備份存放區。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

屬性也可以是類似陣列，在這種情況下，它們稱為*索引的屬性*。 如需詳細資訊，請參閱已[編制索引的屬性](indexed-properties.md)。

## <a name="type-annotation-for-properties"></a>屬性的類型注釋

在許多情況下，編譯器會有足夠的資訊可從備份存放區的類型推斷屬性的類型，但您可以藉由加入類型注釋來明確設定類型。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a>使用屬性集存取子

您可以`set` `<-`使用運算子來設定提供存取子的屬性。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

輸出為**20**。

## <a name="abstract-properties"></a>抽象屬性

屬性可以是抽象的。 如同方法， `abstract`只是表示有與屬性相關聯的虛擬分派。 抽象屬性可以是真正抽象的，也就是沒有相同類別中的定義。 因此，包含這類屬性的類別是抽象類別。 或者，abstract 也可以表示屬性是虛擬的，在此情況下，定義必須存在於相同的類別中。 請注意，抽象屬性不得為私用，如果一個存取子是抽象的，另一個則必須是 abstract。 如需抽象類別的詳細資訊，請參閱[抽象類別](../abstract-classes.md)。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a>另請參閱

- [成員](index.md)
- [方法](methods.md)
