---
title: 抽象類別 (F#)
description: '了解 F # 抽象類別，可保留未提供的部分或所有成員，然後代表通用的功能多樣的物件類型。'
ms.date: 05/16/2016
ms.openlocfilehash: c472e9d164ae78bde716bb5102e54f4e698b61b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562385"
---
# <a name="abstract-classes"></a>抽象類別

*抽象類別*會保留未提供，部分或所有成員，如此可以由衍生類別中提供實作的類別。

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
在物件導向程式設計中，抽象類別作為基底類別階層架構，並代表通用的功能多樣的物件類型。 名稱 「 抽象 」 一詞可知，抽象類別通常未對應到的問題領域中的具象實體直接。 不過，它們並代表什麼許多不同的具象實體具有共通點。

抽象類別都必須有`AbstractClass`屬性。 他們可以實作和未提供的成員。 使用詞彙的*抽象*時套用至類別是與其他.NET 語言; 相同不過，使用詞彙的*抽象*時套用至方法 （和屬性） 會稍有不同在 F # 從其在其他.NET 語言中使用。 在 F # 中，當方法會標示`abstract`關鍵字，這會指出成員有一個項目，稱為*虛擬分派插槽*，該類型的虛擬函式的內部資料表中。 換句話說，方法是虛擬的雖然`virtual`關鍵字不是 F # 語言中。 關鍵字`abstract`不論方法是否實作虛擬方法上使用。 該分派位置定義的是方法的虛擬的分派插槽的宣告。 因此，F # 的虛擬方法宣告和定義在另一種.NET 語言中的相當的抽象方法宣告和不同的定義，其中一種組合`default`關鍵字或`override`關鍵字。 如需詳細資訊和範例，請參閱[方法](members/methods.md)。

類別會被視為只有在抽象方法已宣告但未定義抽象的。 因此，具有抽象方法的類別不一定是抽象類別。 除非類別具有未定義抽象方法，否則請勿使用**AbstractClass**屬性。

在先前的語法，*存取範圍修飾詞*可以`public`，`private`或`internal`。 如需詳細資訊，請參閱[存取控制](access-control.md)。

如同其他類型，基底類別和一或多個基底介面，可以有抽象類別。 每個基底類別或介面會出現在不同行搭配`inherit`關鍵字。

抽象類別的型別定義可以包含完整定義的成員，但它也可以包含抽象成員。 先前語法中分別顯示抽象成員的語法。 在此語法中，*類型簽章*成員的清單，其中包含的參數類型的順序和傳回型別，以分隔`->`語彙基元和/或`*`的局部調用視語彙基元和採用 tuple 形式參數。 抽象成員的類型簽章的語法是相同簽章檔案中使用，而且在 Visual Studio 程式碼編輯器中 intellisense 所示。

下列程式碼說明具有兩個非抽象衍生的類別，Square 和圓形的形狀的抽象類別。 此範例示範如何使用抽象類別、 方法和屬性。 在範例中，圖形的抽象類別代表的具象實體圓形和正方形的常見項目。 （在二維座標系統中） 的所有形狀的常見功能會縮小圖形類別抽象： 方格、 旋轉的角度和區域和周邊屬性上的位置。 這些可以被覆寫，除了位置，其中個別圖形不能變更的行為。

旋轉方法可以覆寫，如同圓形類別，這是因為其對稱性旋轉而異。 因此在圓形類別中，不做任何動作的方法取代旋轉方法。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

**輸出：**

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a>另請參閱
[類別](classes.md)

[成員](members/index.md)

[方法](members/methods.md)

[屬性](members/Properties.md)
