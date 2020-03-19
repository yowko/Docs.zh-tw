---
title: 方法
description: 瞭解 F# 方法如何與用於公開和實現物件和類型的功能和行為的類型關聯的函數。
ms.date: 11/04/2019
ms.openlocfilehash: 6f5ae76ea450b07763eb58d0c95b18b30f634551
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400208"
---
# <a name="methods"></a>方法

*方法*是與類型關聯的函數。 在物件導向的程式設計中，使用方法公開和實現物件和類型的功能和行為。

## <a name="syntax"></a>語法

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-name parameter-list [ : return-type ] =
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member method-name : type-signature
[ attributes ]
default self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue( default-value )>] input) [ : return-type ]
```

## <a name="remarks"></a>備註

在前面的語法中，您可以看到各種形式的方法聲明和定義。 在較長的方法實體中，分行符號遵循等號 （*），整個方法體縮進。

屬性可以應用於任何方法聲明。 它們先于方法定義的語法，通常列在單獨的行上。 如需詳細資訊，請參閱[屬性](../attributes.md)。

可以標記`inline`方法。 如需 `inline` 的資訊，請參閱[內嵌函式](../functions/inline-functions.md)。

非內聯方法可以在類型中遞迴使用;無需顯式使用 關鍵字`rec`。

## <a name="instance-methods"></a>實例方法

實例方法使用`member`關鍵字和*自識別碼*聲明，後跟句點 （.） 和方法名稱和參數。 與綁定的情況`let`一樣，*參數清單*可以是一種模式。 通常，將方法參數以元組形式包裹在括弧中，這是方法在其他 .NET Framework 語言中創建時在 F# 中顯示的方法。 但是，咖喱形式（由空格分隔的參數）也很常見，並且還支援其他模式。

下面的示例說明了非抽象實例方法的定義和使用。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

在實例方法中，不要使用自識別碼訪問使用 let 綁定定義的欄位。 訪問其他成員和屬性時，請使用自識別碼。

## <a name="static-methods"></a>靜態方法

關鍵字`static`用於指定可以在沒有實例的情況下調用方法，並且不與物件實例關聯。 否則，方法是實例方法。

下一節中的示例顯示使用 關鍵字聲明的`let`欄位、使用`member`關鍵字聲明的屬性成員以及用 關鍵字聲明的`static`靜態方法。

下面的示例說明了靜態方法的定義和使用。 假設這些方法定義位於上一節中的`SomeType`類中。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a>抽象和虛擬方法

關鍵字`abstract`指示方法具有虛擬調度槽，並且類中可能沒有定義。 *虛擬調度槽*是內部維護的函數表中的條目，用於在運行時查找物件導向的類型的虛擬函式呼叫。 虛擬調度機制是實現*多態性的*機制，是物件導向程式設計的一個重要特徵。 至少有一個沒有定義的抽象方法的類是*抽象類別*，這意味著不能創建該類的實例。 有關抽象類別的詳細資訊，請參閱[抽象類別](../abstract-classes.md)。

抽象方法聲明不包括方法體。 相反，方法的名稱後跟冒號 （:)和 方法的類型簽名。 方法的類型簽名與 IntelliSense 在 Visual Studio 代碼編輯器中將滑鼠指標懸停在方法名稱上時顯示的簽名相同，但沒有參數名稱。 當您以對話模式工作時，解譯器 fsi.exe 也會顯示類型簽名。 方法的類型簽名是通過列出參數的類型（後跟返回類型）以及適當的分隔符號符號來形成的。 咖喱參數由 分隔`->`，元組參數由 分隔。 `*` 傳回值始終由`->`符號與參數分隔。 括弧可用於對複雜參數進行分組，例如當函數類型為參數時，或指示元組何時被視為單個參數而不是兩個參數。

還可以通過將定義添加到類並使用`default`關鍵字來提供抽象方法預設定義，如本主題中的語法塊所示。 在同一類中具有定義的抽象方法等效于其他 .NET Framework 語言中的虛擬方法。 無論定義是否存在，關鍵字都會`abstract`在類的虛擬函數表中創建一個新的調度槽。

無論基類是否實現其抽象方法，派生類都可以提供抽象方法的實現。 要在派生類中實現抽象方法，請定義派生類中具有相同名稱和簽名的方法，但使用`override`or`default`關鍵字除外，並提供方法正文。 關鍵字`override`和`default`含義完全相同的東西。 如果`override`新方法重寫基類實現，請使用 ;在`default`與原始抽象聲明相同的類中創建實現時使用。 不要在`abstract`實現基類中聲明為抽象的方法上使用 關鍵字。

下面的示例演示了具有預設實現`Rotate`（等效于 .NET Framework 虛擬方法）的抽象方法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

下面的示例演示了重寫基類方法的派生類。 在這種情況下，重寫會更改行為，以便方法不執行任何操作。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a>多載的方法

重載方法是給定類型中名稱相同但參數不同的方法。 在 F# 中，通常使用可選參數而不是重載方法。 但是，在語言中允許重載方法，前提是參數以元組形式，而不是咖喱形式。

## <a name="optional-arguments"></a>選擇性引數

從 F# 4.1 開始，還可以在方法中具有具有預設參數值的可選參數。  這有助於促進 C# 代碼的交互操作。  下面的示例演示了語法：

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    _.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

請注意，傳入`DefaultParameterValue`的值必須與輸入類型匹配。  在上述示例中，它是 一個`int`。  嘗試將非整數值傳遞到中`DefaultParameterValue`將導致編譯錯誤。

## <a name="example-properties-and-methods"></a>示例：屬性和方法

下面的示例包含一個類型，其中包含欄位、私有函數、屬性和靜態方法的示例。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a>另請參閱

- [成員](index.md)
