---
title: 方法
description: 了解如何F#方法是用來公開及實作的功能和行為的物件與型別的型別相關聯的函式。
ms.date: 05/16/2016
ms.openlocfilehash: 03150cc67f79bfde58cf27e4a9d4dfa9e9ff3f55
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666491"
---
# <a name="methods"></a>方法

A*方法*是與類型相關聯的函式。 在物件導向程式設計中，方法用來公開及實作的功能和行為的物件和型別。

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

在先前的語法中，您可以看到各種形式的方法宣告和定義。 在較長的方法主體，換行符號後面接著等號 （=），而整個方法本文縮排。

屬性可以套用至任何方法宣告。 在之前的方法定義的語法，而且通常會列在不同行。 如需詳細資訊，請參閱[屬性](../attributes.md)。

方法會標記`inline`。 如需 `inline` 的資訊，請參閱[內嵌函式](../functions/inline-functions.md)。

非內嵌方法可以是遞迴的類型; 內使用不需要明確使用`rec`關鍵字。

## <a name="instance-methods"></a>執行個體方法

執行個體方法會以宣告`member`關鍵字和*自我識別項*，後面接著句號 （.） 的方法名稱和參數。 在此情況下，如`let`繫結*參數清單*可以是一種模式。 一般而言，括住括弧括住 tuple 的形式，也就是方式方法的參數會出現在方法F#在其他.NET Framework 語言中的建立時。 不過，局部調用的形式 （以空格分隔的參數） 也很常見，而且也支援其他模式。

下列範例說明如何定義和使用非抽象的執行個體方法。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

執行個體在方法內，請勿使用自我識別項來使用 let 繫結來定義存取欄位。 存取其他成員和屬性時，請使用自我識別項。

## <a name="static-methods"></a>靜態方法

關鍵字`static`用來指定可以沒有執行個體中呼叫的方法，並不是物件執行個體相關聯。 否則，方法是執行個體方法。

下一節中的範例示範使用宣告的欄位`let`關鍵字，以宣告的屬性成員`member`關鍵字，並以宣告的靜態方法`static`關鍵字。

下列範例說明如何定義和使用靜態方法。 假設這些方法的定義位於`SomeType`上一節中的類別。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a>抽象和虛擬方法

關鍵字`abstract`表示一種方法有虛擬分派位置，而且可能沒有定義類別中。 A*虛擬分派介面槽*是物件導向的型別中，呼叫的函式在執行階段用來查閱虛擬函式的內部維護表格中的項目。 虛擬分派機制是實作的機制*多型*，物件導向程式設計的重要功能。 具有至少一個抽象的方法，而不需定義的類別是*抽象類別*，這表示該類別，可以建立任何執行個體。 如需抽象類別的詳細資訊，請參閱[抽象類別](../abstract-classes.md)。

抽象方法宣告不包含方法主體。 相反地，方法的名稱被後面接著冒號 （:） 和方法的型別簽章。 方法的型別簽章會顯示 intellisense，當您暫停滑鼠指標的方法名稱在 Visual Studio 程式碼編輯器 」 中，除了沒有參數的名稱相同。 當您以互動方式使用時，解譯器 fsi.exe，也會顯示型別簽章。 方法的型別簽章是 out 參數，後面接著傳回的型別，使用適當的分隔符號類型的清單所形成的。 局部調用的參數會以分隔`->`並以分隔 tuple 參數`*`。 傳回值一律會分開的引數`->`符號。 可以用括號，將複雜的參數，例如，當函式型別為參數，或表示做為單一參數，而不是兩個參數，當處理 tuple。

您也可以讓抽象方法 default 定義加入至類別的定義並使用`default`關鍵字，如本主題中的語法區塊所示。 相同類別中有定義的抽象方法相當於其他.NET Framework 語言中的虛擬方法。 定義是否存在，`abstract`關鍵字會建立一個新分派位置虛擬函式資料表中的類別。

不論是否基底類別實作其抽象方法，衍生的類別可以提供抽象方法的實作。 若要在衍生類別中實作抽象方法，定義在衍生類別中，除了使用具有相同名稱和簽章的方法`override`或`default`關鍵字，並提供方法主體。 關鍵字`override`和`default`表示完全相同的動作。 使用 `override`新的方法會覆寫基底類別實作; 如果使用`default`當您建立實作在與原始的抽象宣告相同的類別。 請勿使用`abstract`方法會實作已宣告為抽象基底類別中的方法上的關鍵字。

下列範例說明抽象方法`Rotate`，其預設實作，相當於.NET Framework 的虛擬方法。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

下列範例說明在衍生的類別會覆寫基底類別方法。 在此情況下，覆寫變更的行為，使方法不做任何動作。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a>多載的方法

多載的方法是指定的型別中具有相同名稱但有不同的引數的方法。 在F#，而不是多載的方法通常用於選擇性引數。 不過，多載的方法允許在語言中，前提是引數是 tuple 形式，不局部調用形式。

## <a name="optional-arguments"></a>選擇性引數

開頭為F#4.1，您也可以在方法中有預設參數值的選擇性引數。  這是為了協助使用 C# 程式碼的互通性。  下列範例示範的語法：

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

請注意，傳入的值`DefaultParameterValue`必須符合的輸入的類型。  在上述範例中，它是`int`。  嘗試傳遞非整數值至`DefaultParameterValue`會導致編譯錯誤。

## <a name="example-properties-and-methods"></a>範例：屬性和方法

下列範例包含具有範例的欄位、 私用函式、 屬性和靜態方法的類型。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a>另請參閱

- [成員](index.md)