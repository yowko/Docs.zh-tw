---
title: 抽象類別
description: 瞭解F#抽象類別，使部分或所有成員不會被啟用，並代表一組不同物件類型的一般功能。
ms.date: 05/16/2016
ms.openlocfilehash: d7fc87178cff7c5c824992c97198b49f87025f00
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082953"
---
# <a name="abstract-classes"></a>抽象類別

*抽象類別*是讓部分或所有成員不會執行的類別，以便讓衍生類別能夠提供執行。

## <a name="syntax"></a>語法

```fsharp
// Abstract class syntax.
[<AbstractClass>]
type [ accessibility-modifier ] abstract-class-name =
[ inherit base-class-or-interface-name ]
[ abstract-member-declarations-and-member-definitions ]

// Abstract member syntax.
abstract member member-name : type-signature
```

## <a name="remarks"></a>備註

在物件導向程式設計中，抽象類別會當做階層的基類使用，並代表一組不同物件類型的一般功能。 顧名思義，抽象類別通常不會直接對應到問題網域中的具體實體。 不過，它們確實代表有多少不同的具體實體具有共同的功能。

抽象類別必須具有`AbstractClass`屬性。 它們可以有已實和未執行的成員。 套用至類別時，使用「*抽象*」一詞，與其他 .net 語言相同。不過，套用至方法（和屬性）時，使用「抽象」（ *abstract* ）一詞與F#其他 .net 語言中的使用方式稍有不同。 在F#中，當方法以`abstract`關鍵字標記時，這表示成員在該類型的虛擬函式的內部資料表中有一個專案，稱為「*虛擬分派插槽*」。 換句話說，方法是虛擬的，但是`virtual`在F#語言中不使用關鍵字。 無論方法`abstract`是否已實作為，都會在虛擬方法上使用關鍵字。 虛擬分派位置的宣告與該分派插槽的方法定義不同。 因此，在F#另一個 .net 語言中，虛擬方法宣告和定義的對等，是抽象方法宣告和個別定義的組合，其中包含`default`關鍵字或`override`關鍵字。 如需詳細資訊和範例，請參閱[方法](./members/methods.md)。

只有在有已宣告但未定義的抽象方法時，才會將類別視為抽象。 因此，具有抽象方法的類別不一定是抽象類別。 除非類別有未定義的抽象方法，否則請不要使用**AbstractClass**屬性。

在先前的語法中，*協助工具修飾*詞`public`可以`private`是`internal`、或。 如需詳細資訊，請參閱[存取控制](access-control.md)。

如同其他類型，抽象類別可以有基類和一或多個基底介面。 每個基類或介面都會與`inherit`關鍵字一起出現在不同的行上。

抽象類別的類型定義可以包含完整定義的成員，但也可以包含抽象成員。 Abstract 成員的語法會分別顯示在先前的語法中。 在此語法中，成員的*型*別簽章是一份清單，其中包含依`->`序排列的參數類型和傳回型別，並以標記和/或`*` token 分隔，以適用于擴充和元組參數。 抽象成員類型簽章的語法與簽章檔案中所使用的語法相同，以及 IntelliSense 在 Visual Studio Code 編輯器中所顯示的語法。

下列程式碼說明抽象類別圖形，其中包含兩個非抽象衍生類別：方形和 Circle。 此範例示範如何使用抽象類別、方法和屬性。 在此範例中，「抽象類別」圖形代表具體實體 circle 和正方形的通用元素。 所有圖形（在二維座標系統中）的一般功能會被抽象化成 Shape 類別：格線上的位置、旋轉角度，以及區域和周邊屬性。 這些可以覆寫，但位置除外，個別圖形無法變更的行為。

可以覆寫旋轉方法，如同 Circle 類別，這是因為其對稱而旋轉不變。 因此，在 Circle 類別中，旋轉方法會由不執行任何動作的方法所取代。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

**輸出：**

```console
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a>另請參閱

- [類別](classes.md)
- [成員](./members/index.md)
- [方法](./members/methods.md)
- [屬性](./members/Properties.md)
