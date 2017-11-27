---
title: "屬性 (F#)"
description: "深入了解 F # 的屬性，表示與物件相關聯的值的成員。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 98b363a5-ee6a-4b7b-b8ae-b244f2a0b316
ms.openlocfilehash: 53b93b20310c557ad9c30226bc08f85cbf2f3010
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="properties"></a>屬性

*屬性*成員代表與物件相關聯的值。


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
屬性代表 」 有 「 在物件導向程式設計中，表示物件執行個體或靜態屬性，與類型相關聯的資料關聯性。

您可以宣告兩種方式，根據您是否要明確指定 （也稱為 「 備份存放區 」） 的基礎值的屬性，或如果您想要允許編譯器自動產生您的備份存放區中的屬性。 一般而言，您應該使用更明確地，如果此屬性有非一般的實作和自動的方式只的簡單包裝函式的值或變數的屬性時。 若要明確宣告的屬性，使用`member`關鍵字。 此宣告式語法後面指定的語法`get`和`set`方法，也稱為*存取子*。 各種形式的語法 > 一節中所顯示的明確語法可用來讀取/寫入，以及唯讀、 唯寫屬性。 唯讀屬性，只定義`get`方法; 唯寫屬性，定義僅`set`方法。 請注意，當屬性同時具有`get`和`set`存取子中，替代語法可以可讓您指定屬性和存取範圍修飾詞不同的每個存取子，如下列程式碼所示。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

讀取/寫入屬性，同時具有`get`和`set`方法中，順序`get`和`set`可以反轉。 或者，您可以提供如所顯示的語法`get`只顯示的語法和`set`只而不是使用合併的語法。 這樣可以更輕鬆地註解個別`get`或`set`方法，如果這是您可能必須進行。 這個替代方案，使用合併的語法是以下列程式碼所示。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

私用值的資料內容會呼叫該保留*支援存放區*。 若要讓編譯器會自動建立的備份存放區，使用關鍵字`member val`，請省略自我識別項，然後提供運算式以初始化屬性。 如果屬性是可變動，包括`with get, set`。 例如，下列類別類型包含兩個自動實作的屬性。 `Property1`是唯讀的而且初始化為提供的主要建構函式的引數和`Property2`是可設定的屬性初始化為空字串：

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

自動實作的屬性屬於型別，初始化讓它們必須包含其他成員定義之前就像是`let`繫結和`do`類型定義中的繫結。 請注意，在啟動時，以及每次在屬性經過存取未初始化自動實作的屬性運算式只會評估。 這是屬性的行為的行為的明確實作。 這實際上就表示，初始化這些屬性的程式碼會加入至類別的建構函式。 請考慮下列程式碼會顯示這項差異：

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

```
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

上述程式碼的輸出顯示，AutoProperty 的值不變時重複呼叫而 ExplicitProperty 改變每次呼叫時。 這會顯示自動實作屬性的運算式不會評估每次，因為是明確的屬性的 getter 方法。


>[!WARNING]
某些程式庫，例如 Entity Framework (`System.Data.Entity`) 不適用於初始化自動實作屬性的基底類別建構函式中執行的自訂作業。 在這些情況下，請嘗試使用明確的內容。

屬性可以是類別、 結構、 差別聯的集、 記錄、 介面和類型擴充功能的成員，也可以定義物件運算式中。

屬性可以套用至屬性。 若要將屬性套用至屬性，請在不同行的屬性之前寫入屬性。 如需詳細資訊，請參閱[屬性](../attributes.md)。

根據預設，屬性都是公用的。 存取範圍修飾詞也可以套用至屬性。 若要套用的存取範圍修飾詞，將它加入的屬性名稱前面如果它用來套用至兩者`get`和`set`方法，將它之前加入`get`和`set`關鍵字，如果不同的存取範圍是所需的每個存取子。 *存取範圍修飾詞*可以是下列其中之一： `public`， `private`， `internal`。 如需詳細資訊，請參閱[存取控制](../access-control.md)。

屬性的實作會執行每次存取時的屬性。


## <a name="static-and-instance-properties"></a>靜態和執行個體屬性
可以是靜態或執行個體屬性的屬性。 靜態屬性可以叫用沒有執行個體和相關聯的類型，不能搭配個別物件的值會使用。 靜態屬性，請省略自我識別項。 執行個體屬性需要自我識別項。

下列的靜態屬性定義為基礎的案例中，您有靜態欄位`myStaticValue`也就是支援的存放區的屬性。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

屬性也可以是陣列形式，在此情況下呼叫它們*索引屬性*。 如需詳細資訊，請參閱[編製索引的屬性](indexed-properties.md)。


## <a name="type-annotation-for-properties"></a>屬性的類型註釋
在許多情況下，編譯器有足夠的資訊來推斷來自備份存放區類型的屬性類型，但您可以明確地設定類型，加入類型註釋。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a>使用屬性 set 存取子
您可以設定屬性，可提供`set`存取子使用`<-`運算子。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

輸出是**20**。


## <a name="abstract-properties"></a>抽象屬性
屬性可以是抽象的。 如同方法`abstract`只是表示是虛擬的分派與屬性相關聯。 抽象屬性可以是真正抽象的也就是沒有相同的類別中定義。 包含這類屬性的類別，因此是抽象類別。 或者，抽象只可以表示屬性是虛擬的而且在此情況下，定義中必須要有相同的類別。 請注意，抽象屬性不是私人的是否其中一個存取子是抽象的另也必須是抽象。 如需抽象類別的詳細資訊，請參閱[抽象類別](../abstract-classes.md)。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a>另請參閱
[成員](index.md)

[方法](methods.md)
