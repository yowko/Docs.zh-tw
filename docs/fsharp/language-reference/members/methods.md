---
title: 方法
description: '瞭解 F # 方法是一種與型別相關聯的函式，用來公開和執行物件和類型的功能和行為。'
ms.date: 11/04/2019
ms.openlocfilehash: 6f5ae76ea450b07763eb58d0c95b18b30f634551
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224108"
---
# <a name="methods"></a>方法

*方法*是與型別相關聯的函式。 在物件導向程式設計中，會使用方法來公開和執行物件和類型的功能和行為。

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

在先前的語法中，您可以看到各種形式的方法宣告和定義。 在較長的方法主體中，換行字元會在等號 (=) 之後，而整個方法主體會縮排。

屬性可以套用至任何方法宣告。 它們優先于方法定義的語法，且通常會列在個別行上。 如需詳細資訊，請參閱[屬性](../attributes.md)。

可以標示方法 `inline` 。 如需 `inline` 的資訊，請參閱[內嵌函式](../functions/inline-functions.md)。

非內嵌方法可以在型別內以遞迴方式使用;不需要明確使用 `rec` 關鍵字。

## <a name="instance-methods"></a>實例方法

實例方法是以 `member` 關鍵字和 *自我識別碼*宣告，後面接著一個句點 (. ) 和方法名稱和參數。 如同系結的情況 `let` ， *參數清單* 可以是模式。 通常，您會在元組形式的括弧中括住方法參數，這是方法在以其他 .NET Framework 語言建立時，在 F # 中的顯示方式。 不過，局部分隔形式 (參數以空格分隔) 也很常見，而且也支援其他模式。

下列範例說明非抽象實例方法的定義和使用方式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

在實例方法中，請勿使用自我識別碼來存取使用 let 系結所定義的欄位。 存取其他成員和屬性時，請使用自我識別碼。

## <a name="static-methods"></a>靜態方法

關鍵字 `static` 是用來指定在沒有實例的情況下呼叫方法，而且不會與物件實例相關聯。 否則，方法是實例方法。

下一節中的範例會顯示使用關鍵字宣告的欄位 `let` 、使用關鍵字宣告的屬性成員 `member` ，以及使用關鍵字宣告的靜態方法 `static` 。

下列範例說明靜態方法的定義和使用方式。 假設這些方法定義是在 `SomeType` 上一節的類別中。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a>抽象和虛擬方法

關鍵字 `abstract` 指出方法具有虛擬分派位置，而且在類別中可能沒有定義。 *虛擬分派*位置是在內部維護的函式資料表中的專案，可在執行時間用來查詢物件導向型別中的虛擬函式呼叫。 虛擬分派機制是實架構的 *機制，這*是物件導向程式設計的一項重要功能。 至少有一個沒有定義之抽象方法的類別是 *抽象類別*，這表示不可以建立該類別的實例。 如需抽象類別的詳細資訊，請參閱 [抽象類別](../abstract-classes.md)。

抽象方法宣告不包含方法主體。 相反地，方法的名稱後面會接著冒號 (： ) 和方法的類型簽章。 當您將滑鼠指標暫停在 Visual Studio Code 編輯器中的方法名稱上方（但不含參數名稱）時，方法的類型簽章與 IntelliSense 所顯示的類型簽章相同。 當您以互動方式工作時，解譯器也會顯示型別簽章（fsi.exe）。 方法的類型簽章是藉由列出參數的類型，後面接著傳回型別，並以適當的分隔符號號來形成。 局部擴充參數會以分隔 `->` ，而且元組參數會以分隔 `*` 。 傳回值一律與引數以 `->` 符號分隔。 括弧可以用來將複雜參數分組，例如當函式類型是參數時，或指出元組視為單一參數，而不是兩個參數。

您也可以將定義新增至類別，並使用 `default` 關鍵字（如本主題中的語法區塊所示），以提供抽象方法的預設定義。 在相同類別中具有定義的抽象方法，相當於其他 .NET Framework 語言中的虛擬方法。 無論定義是否存在， `abstract` 關鍵字都會在類別的虛擬函式資料表中建立新的分派位置。

無論基類是否實作為抽象方法，衍生類別都可以提供抽象方法的執行。 若要在衍生類別中執行抽象方法，請在衍生類別中定義具有相同名稱和簽章的方法（使用 `override` 或關鍵字除外 `default` ），並提供方法主體。 關鍵字 `override` 和 `default` 表示完全相同的內容。 `override`如果新的方法會覆寫基類執行，請使用， `default` 當您在與原始抽象宣告相同的類別中建立實值時，請使用。 請勿 `abstract` 在執行基類中宣告為抽象方法的方法上使用關鍵字。

下列範例說明 `Rotate` 具有預設實值的抽象方法，相當於 .NET Framework 的虛擬方法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

下列範例說明會覆寫基類方法的衍生類別。 在此情況下，覆寫會變更行為，使該方法不會執行任何動作。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a>多載方法

多載方法是在指定類型中具有相同名稱但有不同引數的方法。 在 F # 中，通常會使用選擇性引數，而不是多載的方法。 但是，如果引數是採用元組格式，而非局部引數，則允許在語言中使用多載的方法。

## <a name="optional-arguments"></a>選擇性引數

從 F # 4.1 開始，您也可以在方法中有選擇性的引數搭配預設參數值。  這是為了協助加速與 c # 程式碼的交互操作。  下列範例示範語法：

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    _.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

請注意，傳入的值 `DefaultParameterValue` 必須符合輸入類型。  在上述範例中，它是 `int` 。  嘗試傳遞非整數值 `DefaultParameterValue` 會導致編譯錯誤。

## <a name="example-properties-and-methods"></a>範例：屬性和方法

下列範例包含型別，其中包含欄位、私用函式、屬性和靜態方法的範例。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a>另請參閱

- [成員](index.md)
