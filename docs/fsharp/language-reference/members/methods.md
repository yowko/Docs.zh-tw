---
title: 方法
description: 瞭解方法如何F#是與型別相關聯的函式, 用來公開和實作用物件和類型的功能與行為。
ms.date: 05/16/2016
ms.openlocfilehash: 13503690a59ace13dacba93b6fce9ea3240c5cc2
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627447"
---
# <a name="methods"></a>方法

*方法*是與型別相關聯的函式。 在物件導向程式設計中, 方法是用來公開和執行物件和類型的功能與行為。

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

在先前的語法中, 您可以看到各種形式的方法宣告和定義。 在較長的方法主體中, 分行符號會在等號 (=) 之後, 而整個方法主體則會縮排。

屬性可以套用至任何方法宣告。 它們會在方法定義的語法前面, 而且通常會列在個別的行上。 如需詳細資訊，請參閱[屬性](../attributes.md)。

可以標記`inline`方法。 如需 `inline` 的資訊，請參閱[內嵌函式](../functions/inline-functions.md)。

非內嵌方法可以在型別中以遞迴方式使用;不需要明確使用`rec`關鍵字。

## <a name="instance-methods"></a>實例方法

實例方法是使用`member`關鍵字和*自我識別碼*來宣告, 後面接著句號 (.) 和方法名稱和參數。 如同系結的情況`let` ,*參數清單*可以是模式。 一般來說, 您會將方法參數以括弧括住在元組形式中, 這是方法F#在以其他 .NET Framework 語言建立時的出現方式。 不過, 擴充形式 (以空格分隔的參數) 也是常見的, 而且也支援其他模式。

下列範例說明非抽象實例方法的定義與使用方式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

在實例方法內, 請勿使用自我識別碼來存取使用 let 系結所定義的欄位。 存取其他成員和屬性時, 請使用自我識別碼。

## <a name="static-methods"></a>靜態方法

關鍵字`static`是用來指定方法不需要實例就可以呼叫, 而且不會與物件實例建立關聯。 否則, 方法為實例方法。

下一節中的範例會顯示使用`let`關鍵字宣告的欄位、 `member`以關鍵字宣告的屬性成員, 以及使用`static`關鍵字宣告的靜態方法。

下列範例說明如何定義和使用靜態方法。 假設這些方法定義是在上一`SomeType`節的類別中。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a>抽象和虛擬方法

關鍵字`abstract`表示方法具有虛擬分派位置, 而且在類別中可能沒有定義。 *虛擬分派*位置是在內部維護的函式資料表中的專案, 在執行時間用來查詢面向物件類型中的虛擬函式呼叫。 虛擬分派機制是一種執行*多*型的機制, 這是物件導向程式設計的一項重要功能。 至少有一個抽象方法沒有定義的類別是*抽象類別*, 這表示不能建立該類別的任何實例。 如需抽象類別的詳細資訊, 請參閱[抽象類別](../abstract-classes.md)。

抽象方法宣告不包含方法主體。 相反地, 方法的名稱後面會接著冒號 (:)和方法的類型簽章。 當您將滑鼠指標停留在 [Visual Studio Code 編輯器] 中的方法名稱上時, 方法的類型簽章與 IntelliSense 所顯示的相同, 但不含參數名稱。 當您以互動方式運作時, 解譯器 fsi.exe 也會顯示類型簽章。 方法的類型簽章是藉由列出參數的類型 (後面接著傳回類型) 和適當的分隔符號來形成。 擴充參數是以分隔`->` , 而元組參數則`*`是以分隔。 傳回值一律會與引數`->`以符號分隔。 括弧可用來將複雜的參數分組, 例如當函式類型為參數時, 或表示要將元組視為單一參數, 而不是兩個參數。

您也可以將定義新增至類別並使用`default`關鍵字 (如本主題中的語法區塊所示), 以提供抽象方法的預設定義。 在相同類別中具有定義的抽象方法, 相當於其他 .NET Framework 語言中的虛擬方法。 無論定義是否存在, `abstract`關鍵字都會在類別的虛擬函式資料表中建立新的分派位置。

不論基類是否會執行其抽象方法, 衍生的類別都可以提供抽象方法的執行。 若要在衍生類別中執行抽象方法, 請定義在衍生類別中具有相同名稱和簽章的方法 (使用`override`或`default`關鍵字除外), 並提供方法主體。 關鍵字`override` 和`default`都是完全相同的意思。 如果`override`新方法會覆寫基類執行, 請使用; `default`當您在與原始抽象宣告相同的類別中建立執行時, 請使用。 請不要在執行`abstract`基類中宣告為 abstract 之方法的方法上使用關鍵字。

下列範例說明具有預設實值`Rotate`的抽象方法, 這是 .NET Framework 虛擬方法的對等用法。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

下列範例說明會覆寫基類方法的衍生類別。 在此情況下, 覆寫會變更行為, 讓方法不會執行任何動作。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a>多載的方法

多載的方法是在指定類型中具有相同名稱, 但具有不同引數的方法。 在F#中, 通常會使用選擇性引數, 而不是多載的方法。 不過, 如果引數是元組形式, 而不是擴充形式, 則會允許在語言中使用多載的方法。

## <a name="optional-arguments"></a>選擇性引數

從F# 4.1 開始, 在方法中, 您也可以有選擇性的引數搭配預設參數值。  這是為了協助與C#程式碼互通。  下列範例示範語法:

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

請注意, 針對傳入的`DefaultParameterValue`值必須符合輸入類型。  在上述範例中, 它是`int`。  嘗試將非整數值傳遞至`DefaultParameterValue`會導致編譯錯誤。

## <a name="example-properties-and-methods"></a>範例：屬性和方法

下列範例包含的型別具有欄位、私用函式、屬性和靜態方法的範例。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a>另請參閱

- [成員](index.md)
