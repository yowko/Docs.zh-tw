---
description: 瞭解 C 中內建數數值型別之間的隱含和明確轉換#
title: '內建的數值轉換-c # 參考'
ms.date: 10/22/2019
helpviewer_keywords:
- implicit numeric conversions [C#]
- explicit numeric conversion [C#]
- numeric conversions [C#], implicit
- numeric conversions [C#], explicit
- conversions [C#], implicit numeric
- conversions [C#], explicit numeric
ms.openlocfilehash: ee5def3b5e0e067919a8c8335db701dbb6dd4d88
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142241"
---
# <a name="built-in-numeric-conversions-c-reference"></a>內建的數值轉換 (c # 參考) 

C # 提供一組 [整數](integral-numeric-types.md) 和 [浮點](floating-point-numeric-types.md) 數數值型別。 任兩個數數值型別（隱含或明確）之間存在轉換。 您必須使用 [cast 運算式](../operators/type-testing-and-cast.md#cast-expression) 來執行明確的轉換。

## <a name="implicit-numeric-conversions"></a>隱含數值轉換

下表顯示內建數數值型別之間預先定義的隱含轉換：

|寄件者|收件者|
|----------|--------|
|[sbyte](integral-numeric-types.md)|`short`、`int`、`long`、`float`、`double` 或 `decimal`|
|[byte](integral-numeric-types.md)|`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`|
|[short](integral-numeric-types.md)|`int`、`long`、`float`、`double` 或 `decimal`|
|[ushort](integral-numeric-types.md)|`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`。|
|[int](integral-numeric-types.md)|`long`、`float`、`double` 或 `decimal`|
|[uint](integral-numeric-types.md)|`long`、`ulong`、`float`、`double` 或 `decimal`|
|[long](integral-numeric-types.md)|`float`、`double` 或 `decimal`|
|[ulong](integral-numeric-types.md)|`float`、`double` 或 `decimal`|
|[float](floating-point-numeric-types.md)|`double`|

> [!NOTE]
> 從 `int` 、 `uint` 、 `long` 或 `ulong` 到 `float` 和 from 或 to 的隱含 `long` 轉換 `ulong` `double` 可能會導致精確度遺失，但永遠不會遺失量值的順序。 其他的隱含數值轉換絕不會遺失任何資訊。

另請注意，

- 任何 [整數數數值型別](integral-numeric-types.md) 都可以隱含地轉換成任何 [浮點數](floating-point-numeric-types.md)型別。

- 和類型沒有隱含的轉換 `byte` `sbyte` 。 沒有來自 `double` 與 `decimal` 類型的隱含轉換。

- `decimal` 類型和 `float` 或 `double` 類型之間沒有隱含轉換。

- 型別的常數運算式值 `int` (例如，整數常值所代表的值) 可以隱含地轉換成 `sbyte` 、 `byte` 、 `short` 、 `ushort` 、 `uint` 或 `ulong` ，如果它是在目的地類型的範圍內：

  ```csharp
  byte a = 13;
  byte b = 300;  // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

  如先前的範例所示，如果常數值不在目的類型範圍內，就會發生編譯器錯誤 [CS0031](../../misc/cs0031.md) 。

## <a name="explicit-numeric-conversions"></a>明確數值轉換

下表顯示內建數數值型別（沒有 [隱含轉換](#implicit-numeric-conversions)）之間的預先定義明確轉換：

|寄件者|收件者|
|----------|--------|
|[sbyte](integral-numeric-types.md)|`byte`、`ushort`、`uint` 或 `ulong`|
|[byte](integral-numeric-types.md)|`sbyte`|
|[short](integral-numeric-types.md)|`sbyte`、`byte`、`ushort`、`uint` 或 `ulong`|
|[ushort](integral-numeric-types.md)|`sbyte`、`byte` 或 `short`|
|[int](integral-numeric-types.md)|`sbyte`、`byte`、`short`、`ushort`、`uint` 或 `ulong`|
|[uint](integral-numeric-types.md)|`sbyte`、`byte`、`short`、`ushort` 或 `int`|
|[long](integral-numeric-types.md)|`sbyte`、`byte`、`short`、`ushort`、`int`、`uint` 或 `ulong`。|
|[ulong](integral-numeric-types.md)|`sbyte`、`byte`、`short`、`ushort`、`int`、`uint` 或 `long`。|
|[float](floating-point-numeric-types.md)|`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong` 或 `decimal`|
|[double](floating-point-numeric-types.md)|`sbyte`、 `byte` 、 `short` 、 `ushort` 、 `int` 、 `uint` 、 `long` `ulong` `float` 、、或 `decimal`|
|[decimal](floating-point-numeric-types.md)|`sbyte`、 `byte` 、 `short` 、 `ushort` 、 `int` 、 `uint` 、 `long` `ulong` `float` 、、或 `double`|

> [!NOTE]
> 明確的數值轉換可能會造成資料遺失或擲回例外狀況，通常是 <xref:System.OverflowException> 。

另請注意，

- 將整數型別的值轉換為另一個整數型別時，結果取決於溢位[檢查內容](../keywords/checked-and-unchecked.md)。 在已檢查的內容中，如果來源值在目標類型的範圍內，轉換將會成功。 否則會擲回 <xref:System.OverflowException>。 在未檢查的內容中，轉換一律會成功，並按照如下所示繼續進行：

  - 如果來源類型大於目的地類型，會藉由捨棄其「額外」最高有效位元，來截斷來源值。 然後會將結果視為目標類型的值。

  - 如果來源類型小於目的地類型，則來源值會是「簽章」或「零延伸」，使其大小與目的地類型相同。 如果來源類型帶正負號，則會使用正負號擴充；如果來源類型不帶正負號，則會使用零擴充。 然後會將結果視為目標類型的值。

  - 如果來源類型與目標類型的大小相同，則來源值將視為目標類型的值。

- 當您將 `decimal` 值轉換為整數型別時，這個值會捨入到最接近整數值的零。 如果產生的整數值超出目的地類型的範圍，就會擲回 <xref:System.OverflowException>。

- 當您將 `double` 或 `float` 值轉換為整數型別時，這個值會往零的方向捨入到最接近的整數值。 如果產生的整數值超出目的地類型的範圍，結果隨溢位[檢查內容](../keywords/checked-and-unchecked.md)而異。 在已檢查的內容中會擲回 <xref:System.OverflowException>，而在未經檢查的內容中，結果是目的地類型的未指定值。

- 當您將 `double` 轉換成 `float` 時，`double` 值會捨入到最接近 `float` 值。 如果 `double` 值太小或太大而無法放入 `float` 類型中，則結果為零或無限大。

- 當您將 `float` 或 `double` 轉換成 `decimal` 時，來源值會轉換成 `decimal` 表示，必要時捨入到最接近第 28 個小數位數後的數字。 視來源值的值而定，可能會發生下列一種結果：

  - 如果來源值太小無法以 `decimal` 表示，結果就會變成零。

  - 如果來源值是 NaN (不是數字)、無限大或太大，無法以 `decimal` 表示，就會擲回 <xref:System.OverflowException>。

- 當您轉換 `decimal` 成 `float` 或時 `double` ，來源值會分別四捨五入為最接近或最接近的 `float` `double` 值。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：

- [隱含數值轉換](~/_csharplang/spec/conversions.md#implicit-numeric-conversions)
- [明確數值轉換](~/_csharplang/spec/conversions.md#explicit-numeric-conversions)

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- [轉換和類型轉換](../../programming-guide/types/casting-and-type-conversions.md)
