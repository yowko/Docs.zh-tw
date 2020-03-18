---
title: 內置數值轉換 - C# 參考
ms.date: 10/22/2019
helpviewer_keywords:
- implicit numeric conversions [C#]
- explicit numeric conversion [C#]
- numeric conversions [C#], implicit
- numeric conversions [C#], explicit
- conversions [C#], implicit numeric
- conversions [C#], explicit numeric
ms.openlocfilehash: 5380e8480c39d1940df13b2ecb50a0f394367388
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399599"
---
# <a name="built-in-numeric-conversions-c-reference"></a>內置數值轉換（C# 參考）

C# 提供一組[積分](integral-numeric-types.md)和[浮點](floating-point-numeric-types.md)數數值型別。 任何兩種數位類型（隱式或顯式類型）之間存在轉換。 您必須使用[強制轉換運算子`()`](../operators/type-testing-and-cast.md#cast-operator-)調用顯式轉換。

## <a name="implicit-numeric-conversions"></a>隱含數值轉換

下表顯示了內置數數值型別之間的預定義隱式轉換：

|從|至|
|----------|--------|
|[sbyte](integral-numeric-types.md)|`short`、`int`、`long`、`float`、`double` 或 `decimal`|
|[位元組](integral-numeric-types.md)|`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`|
|[short](integral-numeric-types.md)|`int`、`long`、`float`、`double` 或 `decimal`|
|[ushort](integral-numeric-types.md)|`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`。|
|[Int](integral-numeric-types.md)|`long`、`float`、`double` 或 `decimal`|
|[uint](integral-numeric-types.md)|`long`、`ulong`、`float`、`double` 或 `decimal`|
|[長](integral-numeric-types.md)|`float`、`double` 或 `decimal`|
|[ulong](integral-numeric-types.md)|`float`、`double` 或 `decimal`|
|[浮動](floating-point-numeric-types.md)|`double`|

> [!NOTE]
> 從`int` `uint`、 、 `long`、 或`ulong``float`到`long`和`ulong``double`到 和 到 的隱式轉換可能會導致精度損失， 但永遠不會損失數量級。 其他隱式數位轉換永遠不會丟失任何資訊。

另請注意

- 任何[積分數數值型別](integral-numeric-types.md)都隱式轉換為任何[浮點數數值型別](floating-point-numeric-types.md)。

- 沒有對 和`byte``sbyte`類型的隱式轉換。 沒有來自 `double` 與 `decimal` 類型的隱含轉換。

- `decimal` 類型和 `float` 或 `double` 類型之間沒有隱含轉換。

- 類型`int`常量運算式的值（例如，由整數文本表示的值）可以隱式轉換為`sbyte`、、、、、、、、、、、、、`ulong``byte``short``ushort``uint`或 ，如果該值位於目標型別的範圍內：

  ```csharp
  byte a = 13;
  byte b = 300;  // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

  如前面的示例所示，如果常量值不在目標型別範圍內，則會發生編譯器錯誤[CS0031。](../../misc/cs0031.md)

## <a name="explicit-numeric-conversions"></a>明確數值轉換

下表顯示了沒有[隱式轉換](#implicit-numeric-conversions)的內置數位類型之間的預定義顯式轉換：

|從|至|
|----------|--------|
|[sbyte](integral-numeric-types.md)|`byte`、`ushort`、`uint` 或 `ulong`|
|[位元組](integral-numeric-types.md)|`sbyte`|
|[short](integral-numeric-types.md)|`sbyte`、`byte`、`ushort`、`uint` 或 `ulong`|
|[ushort](integral-numeric-types.md)|`sbyte`、`byte` 或 `short`|
|[Int](integral-numeric-types.md)|`sbyte`、`byte`、`short`、`ushort`、`uint` 或 `ulong`|
|[uint](integral-numeric-types.md)|`sbyte`、`byte`、`short`、`ushort` 或 `int`|
|[長](integral-numeric-types.md)|`sbyte`、`byte`、`short`、`ushort`、`int`、`uint` 或 `ulong`。|
|[ulong](integral-numeric-types.md)|`sbyte`、`byte`、`short`、`ushort`、`int`、`uint` 或 `long`。|
|[浮動](floating-point-numeric-types.md)|`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong` 或 `decimal`|
|[雙](floating-point-numeric-types.md)|`sbyte`、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、 `byte` `short` `ushort` `int` `uint` `long` `ulong` `float``decimal`|
|[十進位](floating-point-numeric-types.md)|`sbyte`、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、 `byte` `short` `ushort` `int` `uint` `long` `ulong` `float``double`|

> [!NOTE]
> 顯式數位轉換可能會導致資料丟失或引發異常（通常是<xref:System.OverflowException>）。

另請注意

- 將整數型別的值轉換為另一個整數型別時，結果取決於溢位[檢查內容](../keywords/checked-and-unchecked.md)。 在已檢查的內容中，如果來源值在目標類型的範圍內，轉換將會成功。 否則會擲回 <xref:System.OverflowException>。 在未檢查的內容中，轉換一律會成功，並按照如下所示繼續進行：

  - 如果來源類型大於目的地類型，會藉由捨棄其「額外」最高有效位元，來截斷來源值。 然後會將結果視為目標類型的值。

  - 如果源類型小於目標型別，則源值是符號擴展或零擴展，以便其大小與目標型別相同。 如果來源類型帶正負號，則會使用正負號擴充；如果來源類型不帶正負號，則會使用零擴充。 然後會將結果視為目標類型的值。

  - 如果來源類型與目標類型的大小相同，則來源值將視為目標類型的值。

- 當您將 `decimal` 值轉換為整數型別時，這個值會捨入到最接近整數值的零。 如果產生的整數值超出目的地類型的範圍，就會擲回 <xref:System.OverflowException>。

- 當您將 `double` 或 `float` 值轉換為整數型別時，這個值會往零的方向捨入到最接近的整數值。 如果產生的整數值超出目的地類型的範圍，結果隨溢位[檢查內容](../keywords/checked-and-unchecked.md)而異。 在已檢查的內容中會擲回 <xref:System.OverflowException>，而在未經檢查的內容中，結果是目的地類型的未指定值。

- 當您將 `double` 轉換成 `float` 時，`double` 值會捨入到最接近 `float` 值。 如果`double`該值太小或太大，無法放入類型，`float`則結果為零或無窮大。

- 當您將 `float` 或 `double` 轉換成 `decimal` 時，來源值會轉換成 `decimal` 表示，必要時捨入到最接近第 28 個小數位數後的數字。 視來源值的值而定，可能會發生下列一種結果：

  - 如果來源值太小無法以 `decimal` 表示，結果就會變成零。

  - 如果來源值是 NaN (不是數字)、無限大或太大，無法以 `decimal` 表示，就會擲回 <xref:System.OverflowException>。

- 轉換為`decimal``float`或`double`時，源值將分別舍入到最近`float`值`double`或值。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [隱含數值轉換](~/_csharplang/spec/conversions.md#implicit-numeric-conversions)
- [明確數值轉換](~/_csharplang/spec/conversions.md#explicit-numeric-conversions)

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [轉換和類型轉換](../../programming-guide/types/casting-and-type-conversions.md)
