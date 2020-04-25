---
title: C# 型別和變數 - C# 語言教學課程
description: 了解如何在 C# 中定義類型和宣告變數
ms.date: 04/24/2020
ms.assetid: f8a8051e-0049-43f1-b594-9c84cc7b1224
ms.openlocfilehash: 6a3bd3dc802f0d080fd96036067f709e62faf426
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141000"
---
# <a name="types-and-variables"></a>型別與變數

C# 中有兩種型別：*實值型別*和*參考型別*。 實值型別的變數直接包含其資料，而參考型別的變數則將參考儲存到其資料，後者即是物件。 有了參考型別，兩個變數都可以參考相同的物件，因此對某個變數的作業可能會影響另一個變數所參考的物件。 使用實數值型別時，每個變數都有自己的資料複本，而且其中一個作業不可能影響另一個（ `ref`和`out`參數變數除外）。

C # 的實值型別會進一步分成*簡單*型別、*列舉*型別、*結構*型別和*可為 null*的實值型別。 C # 的參考型別會進一步分割成*類別類型*、*介面類別型*、*陣列類型*和*委派類型*。

下列大綱提供 c # 型別系統的總覽。

- [值類型][ValueTypes]
  - [簡單型別][SimpleTypes]
    - 帶正負號的整數︰`sbyte`、`short`、`int`、`long`
    - 不帶正負號的整數︰`byte`、`ushort`、`uint`、`ulong`
    - Unicode 字元：`char`
    - IEEE 二進位浮點：`float`、`double`
    - 高精確度十進位浮點：`decimal`
    - 布林值：`bool`
  - [列舉類型][EnumTypes]
    - 使用者定義型別，格式為 `enum E {...}`
  - [結構型別][StructTypes]
    - 使用者定義型別，格式為 `struct S {...}`
  - [可為 null 的實數值型別][NullableTypes]
    - 含有 `null` 值的所有其他數值型別的擴充
  - [元組數值型別][TupleTypes]
    - 使用者定義型別，格式為 `(T1, T2, ...)`
- [參考型別][ReferenceTypes]
  - [類別類型][ClassTypes]
    - 所有其他型別的基底類別︰`object`
    - Unicode 字串：`string`
    - 使用者定義型別，格式為 `class C {...}`
  - [介面型別][InterfaceTypes]
    - 使用者定義型別，格式為 `interface I {...}`
  - [陣列類型][ArrayTypes]
    - 單一維度和多維度，例如 `int[]` 和 `int[,]`
  - [委派型別][DelegateTypes]
    - 使用者定義型別，格式為 `delegate int D(...)`

[ValueTypes]: ../language-reference/builtin-types/value-types.md
[SimpleTypes]: ../language-reference/builtin-types/value-types.md#built-in-value-types
[EnumTypes]: ../language-reference/builtin-types/enum.md
[StructTypes]: ../language-reference/builtin-types/struct.md
[NullableTypes]: ../language-reference/builtin-types/nullable-value-types.md
[TupleTypes]: ../tuples.md
[ReferenceTypes]: ../language-reference/keywords/reference-types.md
[ClassTypes]: ../language-reference/keywords/class.md
[InterfaceTypes]: ../language-reference/keywords/interface.md
[DelegateTypes]: ../language-reference/keywords/delegate.md
[ArrayTypes]: ../programming-guide/arrays/index.md

如需數值型別的詳細資訊，請參閱[整數型別](../language-reference/builtin-types/integral-numeric-types.md)和[浮點數型別表](../language-reference/builtin-types/floating-point-numeric-types.md)。

C # `bool`的型別用來代表布林值，也就是`true`或`false`的值。

C# 中的字元和字串處理使用 Unicode 編碼方式。 `char` 型別代表 UTF-16 程式碼單位，而 `string` 型別代表一系列的 UTF-16 程式碼單位。

C# 程式使用*型別宣告*來建立新型別。 型別宣告指定新型別的名稱成員。 C # 的型別類別有五種是使用者可定義的：類別類型、結構類型、介面類別型、列舉類型和委派類型。

`class` 型別定義資料結構，其中包含資料成員 (欄位) 和函式成員 (方法、屬性及其他)。 類別型別支援單一繼承和多型，這些是可供衍生類別將基底類別延伸及特製化的機制。

`struct` 型別與類別型別相似，它代表具有資料成員和函式成員的結構。 不過，不同于類別，結構是實數值型別，通常不需要堆積配置。 結構類型不支援使用者指定的繼承，而且所有結構類型都隱含地繼承`object`自類型。

`interface` 型別將協定定義為一組具名的公用函式成員。 執行`class`的`struct`或`interface`必須提供介面的函式成員的實作為。 `interface` 可以繼承自多個基底介面，`class` 或 `struct`可實作多個介面。

`delegate` 型別代表對方法的參考，其中含有特定參數清單與傳回型別。 委派讓您可將方法視為實體，而實體能指派給變數或當作參數來傳遞。 委派類似函式語言提供的函式型別。 它們也類似于其他語言中的函式指標概念。 不同于函式指標，委派是物件導向且為型別安全。

`class`、 `struct`、 `interface`和`delegate`類型全都支援泛型，因此可以使用其他類型來參數化。

`enum` 型別是包含具名常數的不同型別。 每個 `enum` 型別都具有一個基礎型別，其必須是八種整數型別之一。 `enum` 型別的值組與基礎型別的值組相同。

C# 支援任何型別的單一維度及多維陣列。 不同于以上所列的類型，陣列類型不需要先宣告，就可以使用它們。 而陣列型別的建構方法，是在型別名稱之後加上方括弧。 例如，`int[]` 是 `int` 的單一維度陣列、`int[,]` 是 `int` 的雙維陣列，而 `int[][]` 是 `int` 的單一維度陣列的單一維度陣列。

可為 null 的實數值型別也不需要宣告，就可以使用它們。 針對每一個不可為 null 的`T`實數值型別，有一個對應的`T?`可為 null 實數值型別，可以`null`保留額外的值。 比方說，`int?` 是可包含任一 32 位元整數或值 `null` 的型別。

C # 的類型系統是統一的，因此可以將任何類型的值視為`object`。 C# 中的每個型別都直接或間接衍生自 `object` 類別型別，而 `object` 是所有型別的基底類別。 參考型別的值之所以會視為物件，只是將這些值當作 `object` 型別來檢視。 數值型別的值之所以會視為物件，只是透過執行 *boxing* 和 *unboxing* 作業。 在下列範例中，`int` 值會轉換成 `object`，並再次轉換回 `int`。

[!code-csharp[Boxing](../../../samples/snippets/csharp/tour/types-and-variables/Program.cs#L1-L10)]

當實數值型別的值指派給`object`參考時，會配置 "box" 來保存值。 該方塊是參考型別的實例，而值會複製到該方塊中。 相反地，當`object`參考轉換成實值型別時，就會檢查參考的`object`是否為正確值型別的方塊。 如果檢查成功，則會將方塊中的值複製到實數值型別。

C # 的統一型別系統實際上表示實值型別`object`會被視為「視需要」參考。 由於使用類型`object`的統一、一般用途程式庫可以與衍生自`object`的所有類型搭配使用，包括參考型別和實數值型別。

C# 中有數種*變數*，包括欄位、陣列元素、區域變數和參數。 變數表示儲存位置，每個變數都有一種型別，其決定哪些值可以儲存在變數中，如下所示。

- 不可為 Null 的實值型別
  - 該型別的值
- 可為 Null 的實值型別
  - `null` 值或該型別的值
- 物件
  - `null` 參考、任一參考型別之物件的參考，或是任一實值型別的 Boxed 值的參考
- 類別型別
  - `null` 參考、該類別型別之執行個體的參考，或衍生自該類別型別之類別執行個體的參考
- 介面類型
  - `null` 參考、實作該介面型別之類別型別的執行個體的參考，或實作該介面型別之實值型別的 Boxed 值的參考
- 陣列型別
  - `null` 參考、該陣列型別之執行個體的參考，或相容的陣列型別之執行個體的參考
- 委派類型
  - `null` 參考或相容的委派類型之執行個體的參考

> [!div class="step-by-step"]
> [上一頁](program-structure.md)
> [下一頁](expressions.md)
