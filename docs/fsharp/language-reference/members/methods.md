---
title: 方法 (F#)
description: '了解 F # 方法的類型，可用來公開及實作的功能與行為物件和型別相關聯的函式的方式。'
ms.date: 05/16/2016
ms.openlocfilehash: 6cd354eaa4698bb194fd8fc04b09348e708cb0f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="methods"></a>方法

A*方法*的函式的型別相關聯。 在物件導向程式設計中，方法用來公開及實作的功能與行為物件和型別。


## <a name="syntax"></a>語法

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-nameparameter-list [ : return-type ]=
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-nameparameter-list [ : return-type ]=
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member self-identifier.method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member [inline] self-identifier.method-name : type-signature
[ attributes ]
default member [inline] self-identifier.method-nameparameter-list[ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override member [inline] self-identifier.method-nameparameter-list [ : return-type ]=
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue([ default-value ])>] input) [ : return-type ]
```

## <a name="remarks"></a>備註
在上一個語法中，您可以查看各種形式的方法宣告和定義。 在較長的方法主體，分行符號後面接著等號 （=），並縮排的整個方法主體。

屬性可以套用至方法宣告中。 在之前的方法定義的語法，而且通常會列在個別行。 如需詳細資訊，請參閱[屬性](../attributes.md)。

方法會標記`inline`。 如需 `inline` 的資訊，請參閱[內嵌函式](../functions/inline-functions.md)。

可以在型別; 中的遞迴使用的非內嵌方法。不需要明確使用`rec`關鍵字。


## <a name="instance-methods"></a>執行個體方法
執行個體方法宣告與`member`關鍵字和*自我識別項*，後面接著句號 （.） 的方法名稱和參數。 在本例中的為`let`繫結，*參數清單*可以是一種模式。 一般而言，您住的方法在括號內 tuple 表單時，也就是方式方法的參數會顯示 F # 其他.NET Framework 語言中建立時。 不過，局部調用的表單 （以空格分隔的參數） 也是很常見，而且也支援其他模式。

下列範例說明如何定義和使用非抽象的執行個體方法。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

在執行個體方法，請勿使用 let 繫結所定義之存取欄位使用自我識別項。 存取其他成員和屬性時，請使用自我識別項。


## <a name="static-methods"></a>靜態方法
關鍵字`static`用來指定可以沒有執行個體中呼叫的方法，並不是物件執行個體相關聯。 否則，方法是執行個體方法。

下一節中的範例示範使用宣告的欄位`let`關鍵字，以宣告的屬性成員`member`關鍵字和靜態方法，以宣告`static`關鍵字。

下列範例說明如何定義和使用靜態方法。 假設這些方法的定義位於`SomeType`前一節中的類別。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a>抽象和虛擬方法
關鍵字`abstract`表示一種方法具有虛擬分派位置，而且可能沒有定義類別中。 A*虛擬分派插槽*是物件導向的型別中呼叫的函式在執行階段用來查閱虛擬函式的內部維護資料表中的項目。 虛擬分派機制是實作的機制*多型*、 物件導向程式設計的重要功能。 有沒有定義至少一個抽象方法的類別是*抽象類別*，這表示沒有任何執行個體，可以建立該類別。 如需抽象類別的詳細資訊，請參閱[抽象類別](../abstract-classes.md)。

抽象方法宣告不包括方法主體。 相反地，方法的名稱被後面接著冒號 （:） 及方法的類型簽章。 方法的類型簽章時顯示的 IntelliSense，當您將滑鼠指標暫停方法名稱在 Visual Studio 程式碼編輯器中，除了沒有參數的名稱相同。 當您以互動方式使用時，解譯器 fsi.exe，也會顯示類型簽章。 方法的類型簽章的格式是 out 參數，後面接著的傳回型別，以適當的分隔符號符號類型的清單。 局部調用的參數會以分隔`->`而且 tuple 參數會以分隔`*`。 傳回值一律分開的引數所`->`符號。 可以用括號，將複雜的參數，例如當函式型別是參數，或表示當做為單一參數，而不是兩個參數會被視為 tuple。

您也可以提供抽象方法 default 定義加入至類別定義並使用`default`關鍵字，如本主題中的語法區塊所示。 相同類別中已定義抽象方法相當於其他.NET Framework 語言中的虛擬方法。 定義是否存在，`abstract`關鍵字新分派位置在資料表中建立的虛擬函式類別。

不論是否基底類別會實作抽象方法，衍生的類別可以提供抽象方法的實作。 若要在衍生類別中實作抽象方法，定義在衍生類別中，除非使用具有相同名稱和簽章的方法`override`或`default`關鍵字，並提供方法主體。 關鍵字`override`和`default`完全意義相同。 使用`override`新的方法會覆寫基底類別實作; 如果使用`default`當您建立實作在原始的抽象宣告的類別相同。 請勿使用`abstract`方法會實作抽象基底類別中宣告的方法上的關鍵字。

下列範例說明抽象方法`Rotate`具有預設實作中，.NET Framework 的虛擬方法的對等項目。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

下列範例將說明衍生的類別中覆寫基底類別方法。 在此情況下，覆寫變更的行為，使方法不會執行任何動作。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a>多載的方法
多載的方法都是的方法中指定的型別具有相同名稱但具有不同的引數。 在 F # 中，而不是多載的方法通常用選擇性引數。 不過，多載的方法允許在語言中，前提是引數為 tuple 形式，局部調用不表單。

## <a name="optional-arguments"></a>選擇性引數

從 F # 4.1 開始，您也可以使用預設參數值的選擇性引數中的方法。  這是為了促進與 C# 程式碼的互通。  下列範例示範的語法：

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

請注意，傳入的值`DefaultParameterValue`必須符合的輸入的類型。  在上述範例中，它是`int`。  嘗試將傳遞至非整數值`DefaultParameterValue`會導致編譯錯誤。

## <a name="example-properties-and-methods"></a>範例： 屬性和方法
下列範例包含的類型具有欄位、 私用函式、 屬性和靜態方法的範例。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a>另請參閱
[成員](index.md)
