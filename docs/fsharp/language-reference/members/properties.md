---
title: 屬性 (F#)
description: '深入了解 F # 屬性，也就是成員代表與物件相關聯的值。'
ms.date: 05/16/2016
ms.openlocfilehash: 75d21415b44ccc1c26ef5f478d5f5de20c3412e8
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46537409"
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

屬性代表 「 擁有 」 關聯性，在物件導向程式設計中，表示物件執行個體或靜態屬性，與類型相關聯的資料。

您可以宣告兩種方式，取決於您是否要明確指定為 屬性 的 基礎值 （也稱為 「 備份存放區 」），或如果您想要讓編譯器自動產生您的備份存放區中的屬性。 一般而言，您應該使用更明確的方式，如果屬性有非一般的實作和自動的方式在屬性時只是簡單包裝函式的值或變數。 若要明確宣告屬性時，使用`member`關鍵字。 這個宣告式語法後面指定的語法`get`並`set`方法，也稱為*存取子*。 各種形式的明確語法 」 一節所示的語法用於讀取/寫入、 唯讀和唯寫屬性。 唯讀屬性，您只會定義`get`方法; 唯寫屬性，定義只`set`方法。 請注意，當屬性具有`get`和`set`存取子，替代語法可以可讓您指定屬性和不同的每個存取子，如下列程式碼所示的存取範圍修飾詞。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

讀取/寫入屬性，同時擁有`get`並`set`方法時，順序`get`和`set`可反轉。 或者，您可以在其中提供所顯示的語法`get`只顯示的語法和`set`只而不是使用合併的語法。 如此一來更輕鬆地標記為註解個別`get`或`set`方法，如果是您可能需要執行的項目。 此替代方案，使用合併的語法是由下列程式碼所示。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

私用值屬性的資料呼叫該按住不放*備份存放區*。 若要讓編譯器自動建立的備份存放區，使用關鍵字`member val`，省略自我識別項，然後提供運算式以初始化屬性。 如果屬性是可變動的包括`with get, set`。 比方說，下列的類別類型包含兩個自動實作的屬性。 `Property1` 是唯讀的而且初始化為提供的主要建構函式的引數和`Property2`是可設定的屬性初始化為空字串：

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

自動實作的屬性是一個型別，初始化的一部分，讓它們必須包含其他成員定義之前一樣`let`繫結和`do`型別定義中的繫結。 請注意在初始化時，以及每次存取該屬性時不只會評估運算式，以初始化自動實作的屬性。 此行為是明確地實作之屬性的行為相反。 這實際上就表示，初始化這些屬性的程式碼會新增至類別的建構函式。 請考慮下列程式碼顯示這項差異：

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

上述程式碼的輸出會顯示值的 AutoProperty 是不變時重複呼叫而 ExplicitProperty 變更每次呼叫時。 這示範自動實作屬性的運算式不會評估每次都是明確的屬性的 getter 方法。

>[!WARNING]
有一些程式庫，例如 Entity Framework (`System.Data.Entity`)，也不使用初始化自動實作屬性的基底類別建構函式中執行的自訂作業。 在這些情況下，請嘗試使用明確的屬性。

屬性可以是類別、 結構、 差別聯的集、 記錄、 介面和型別延伸模組的成員，也可以在物件運算式中定義。

屬性可以套用至屬性。 若要將屬性套用至屬性，撰寫屬性的屬性之前的個別行上。 如需詳細資訊，請參閱[屬性](../attributes.md)。

根據預設，屬性是公用的。 存取範圍修飾詞也可以套用至屬性。 若要套用的存取範圍修飾詞，將其新增的屬性名稱之前，立即若它用來同時適用於`get`並`set`方法，將它之前新增`get`和`set`關鍵字，如果不同的存取範圍是每個存取子的必要項。 *存取範圍修飾詞*可以是下列其中之一： `public`， `private`， `internal`。 如需詳細資訊，請參閱[存取控制](../access-control.md)。

屬性的實作會執行每次存取時的屬性。

## <a name="static-and-instance-properties"></a>靜態和執行個體屬性

屬性可以是靜態或執行個體屬性。 沒有執行個體就可以叫用靜態屬性，以及用於不具有個別物件的類型相關聯的值。 靜態屬性，請省略自我識別項。 執行個體屬性需要自我識別項。

下列的靜態屬性定義為基礎的案例中，您有靜態欄位`myStaticValue`也就是屬性的備份存放區。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

屬性也可以與陣列在此情況下呼叫它們*編製索引屬性*。 如需詳細資訊，請參閱 <<c0> [ 編製索引的屬性](indexed-properties.md)。

## <a name="type-annotation-for-properties"></a>屬性的型別註釋

在許多情況下，編譯器有足夠的資訊來推斷的類型屬性，以從備份存放區的類型，但您可以明確設定類型，加上型別註釋。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a>使用屬性 set 存取子

您可以設定屬性，可提供`set`存取子使用`<-`運算子。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

輸出是**20**。

## <a name="abstract-properties"></a>抽象屬性

屬性可以是抽象的。 如同方法`abstract`只是表示是虛擬的分派與屬性相關聯。 抽象屬性可以是真正抽象的也就是沒有相同的類別中定義。 包含這類屬性的類別，因此是抽象類別。 或者，屬性是虛擬的，和在此情況下，必須存在於相同的類別定義，可以只是抽象。 請注意，抽象屬性不是私人的而且如果其中一個存取子是 abstract，另也必須為抽象。 如需抽象類別的詳細資訊，請參閱[抽象類別](../abstract-classes.md)。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a>另請參閱

- [成員](index.md)
- [方法](methods.md)
