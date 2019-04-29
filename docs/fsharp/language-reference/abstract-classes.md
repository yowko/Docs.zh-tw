---
title: 抽象類別
description: 深入了解F#抽象類別，讓所有或部分成員未提供，而且代表多樣化的物件類型的一般功能。
ms.date: 05/16/2016
ms.openlocfilehash: fecd3b2d550c6b8f59fa614f5d00c5f730a4896a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772771"
---
# <a name="abstract-classes"></a>抽象類別

*抽象類別*會保留所有或部分成員未提供，以便可以提供實作，由衍生類別的類別。

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

在物件導向程式設計中，抽象類別做為階層中，基底類別，並代表各種不同的一組物件類型的一般功能。 正如其名稱 「 抽象 」，抽象類別通常未對應到的問題領域中的具象實體直接。 不過，它們並代表什麼許多不同的具象實體有共通。

抽象類別必須具有`AbstractClass`屬性。 它們可以實作而且未提供的成員。 一詞的用法*抽象*套用至類別時，與其他.NET 語言; 相同不過，一詞的用法*抽象*時套用至方法 （和屬性） 會稍有不同的F#從其他.NET 語言中使用。 在F#，當方法會標示`abstract`關鍵字，這表示成員的項目，稱為*虛擬分派介面槽*，該類型的虛擬函式的內部資料表中。 換句話說，方法是虛擬的雖然`virtual`關鍵字不會在F#語言。 關鍵字`abstract`虛擬方法，不論是否方法在實作上使用。 虛擬分派位置的宣告，都是方法的獨立於該發送位置定義。 因此，F#虛擬方法宣告和定義在另一種.NET 語言中的等同項目是抽象方法宣告和不同的定義，使用的組合`default`關鍵字或`override`關鍵字。 如需詳細資訊和範例，請參閱 <<c0> [ 方法](members/methods.md)。

類別之所以被視為只有在已宣告但未定義的抽象方法的抽象的。 因此，具有抽象方法的類別不一定是抽象類別。 不使用類別中有未定義的抽象方法，除非**AbstractClass**屬性。

在先前的語法*存取範圍修飾詞*可以是`public`，`private`或`internal`。 如需詳細資訊，請參閱[存取控制](access-control.md)。

如同其他類型中，抽象類別可以有基底類別和一或多個基底介面。 每個基底類別或介面會出現在不同的行，並搭配`inherit`關鍵字。

抽象類別的型別定義可以包含完整定義的成員，但它也可以包含抽象成員。 抽象成員的語法分別顯示在先前的語法。 在這個語法中，*型別簽章*成員的清單，其中包含參數和類型的順序傳回型別，以分隔`->`語彙基元和/或`*`權杖來作為適當的局部調用和 tuple參數。 抽象成員型別簽章的語法是相同簽章檔案中使用，而且在 Visual Studio 程式碼編輯器中 intellisense 所示。

下列程式碼說明的抽象類別圖形，有兩個非抽象衍生的類別，正方形和圓形。 此範例示範如何使用抽象類別、 方法和屬性。 在範例中，抽象類別圖形表示的具象實體圓形和正方形的一般元素。 （在二維的座標系統） 的所有圖形的常見功能抽取出 Shape 類別： 方格、 旋轉的角度和面積和周長屬性上的位置。 這些可以被覆寫，除了位置，其中個別圖形不能變更的行為。

旋轉方法可以覆寫，如同 Circle 類別中，這是因為其對稱的旋轉而異。 因此在 Circle 類別中，旋轉方法會取代不執行任何動作的方法。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

**輸出：**

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a>另請參閱

- [類別](classes.md)
- [成員](members/index.md)
- [方法](members/methods.md)
- [屬性](members/Properties.md)