---
title: CType Function
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: 88d609146648fe1b0c3124b99a65e85293fc0707
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406426"
---
# <a name="ctype-function-visual-basic"></a>CType 函式 (Visual Basic)

傳回將運算式明確轉換成指定之資料類型、物件、結構、類別或介面的結果。

## <a name="syntax"></a>語法

```vb
CType(expression, typename)
```

## <a name="parts"></a>組件

`expression`任何有效的運算式。 如果的值 `expression` 超出允許的範圍，Visual Basic 會擲回 `typename` 例外狀況。

`typename`語句中子句內任何合法的運算式 `As` `Dim` ，也就是任何資料類型、物件、結構、類別或介面的名稱。

## <a name="remarks"></a>備註

> [!TIP]
> 您也可以使用下列函數來執行類型轉換：
>
> - 類型轉換函式 `CByte` ，例如、 `CDbl` 和， `CInt` 會執行特定資料類型的轉換。 如需詳細資訊，請參閱 [類型轉換函數](type-conversion-functions.md)。
> - [DirectCast 運算子](../operators/directcast-operator.md)或[TryCast 運算子](../operators/trycast-operator.md)。 這些運算子需要一個型別繼承自或執行另一個型別。 它們可以提供比 `CType` 資料類型來回轉換時更好的效能 `Object` 。

`CType`是以內嵌方式編譯，這表示轉換程式碼是評估運算式之程式碼的一部分。 在某些情況下，程式碼的執行速度會更快，因為不會呼叫任何程式來執行轉換。

如果未將任何轉換從定義 `expression` 為 `typename` （例如，從 `Integer` 到 `Date` ），Visual Basic 會顯示編譯時期錯誤訊息。

如果轉換在執行時間失敗，則會擲回適當的例外狀況。 如果縮小轉換失敗， <xref:System.OverflowException> 則是最常見的結果。 如果未定義轉換，則會擲回 <xref:System.InvalidCastException> 。 例如，如果 `expression` 的型別為 `Object` ，而且其執行時間型別沒有轉換成，就可能發生這種情況 `typename` 。

如果或的資料類型 `expression` `typename` 是您已定義的類別或結構，您可以 `CType` 在該類別或結構上將定義為轉換運算子。 這會使成為多載 `CType` *運算子*。 如果您這樣做，您可以控制從類別或結構轉換的行為，包括可以擲回的例外狀況。

## <a name="overloading"></a>多載化

`CType`運算子也可以在程式碼外部定義的類別或結構上多載。 如果您的程式碼會在這類類別或結構之間進行轉換，請確定您瞭解其 `CType` 運算子的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。

## <a name="converting-dynamic-objects"></a>轉換動態物件

動態物件的類型轉換是由使用或方法的使用者定義動態轉換所 <xref:System.Dynamic.DynamicObject.TryConvert%2A> 執行 <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> 。 如果您使用的是動態物件，請使用 <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> 方法來轉換動態物件。

## <a name="example"></a>範例

下列範例會使用 `CType` 函數，將運算式轉換為 `Single` 資料類型。

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

如需其他範例，請參閱[隱含和明確轉換](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [Type Conversion Functions](type-conversion-functions.md)
- [轉換函式](conversion-functions.md)
- [Operator Statement](../statements/operator-statement.md)
- [How to: Define a Conversion Operator](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [.NET Framework 中的類型轉換](../../../standard/base-types/type-conversion.md)
