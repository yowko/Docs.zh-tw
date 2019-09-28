---
title: CType 函式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: 4a0391b0a5d76f36803b433369d4832c02b05e09
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592103"
---
# <a name="ctype-function-visual-basic"></a>CType 函式 (Visual Basic)

傳回將運算式明確轉換成指定之資料類型、物件、結構、類別或介面的結果。

## <a name="syntax"></a>語法

```vb
CType(expression, typename)
```

## <a name="parts"></a>組件

`expression` 任何有效的運算式。 如果 `expression` 的值超出 `typename` 允許的範圍，Visual Basic 會擲回例外狀況。

`typename` 在 @no__t 2 語句的 @no__t 1 子句內的任何運算式，也就是任何資料類型、物件、結構、類別或介面的名稱。

## <a name="remarks"></a>備註

> [!TIP]
> 您也可以使用下列函數來執行類型轉換：
>
> - 類型轉換函式，例如 `CByte`、`CDbl` 和 `CInt`，其會執行特定資料類型的轉換。 如需詳細資訊，請參閱[類型轉換函數](../../../visual-basic/language-reference/functions/type-conversion-functions.md)。
> - [DirectCast 運算子](../../../visual-basic/language-reference/operators/directcast-operator.md)或[TryCast 運算子](../../../visual-basic/language-reference/operators/trycast-operator.md)。 這些運算子需要一個型別繼承自或執行另一個型別。 轉換成 `Object` 資料類型時，它們可以提供比 `CType` 更好的效能。

`CType` 是以內嵌方式編譯，這表示轉換程式碼是評估運算式之程式碼的一部分。 在某些情況下，程式碼的執行速度會更快，因為不會呼叫任何程式來執行轉換。

如果沒有從 `expression` 定義轉換為 `typename` （例如，從 `Integer` 到 `Date`），Visual Basic 會顯示編譯時期錯誤訊息。

如果轉換在執行時間失敗，則會擲回適當的例外狀況。 如果縮小轉換失敗，@no__t 0 是最常見的結果。 如果未定義轉換，則會擲回中的 @no__t 0。 例如，如果 `expression` 的類型為 `Object`，而且其執行時間類型沒有轉換成 `typename`，就會發生這種情況。

如果 `expression` 或 `typename` 的資料類型是您已定義的類別或結構，您可以在該類別或結構上定義 `CType` 做為轉換運算子。 這讓 `CType` 作為多載*運算子*。 如果您這樣做，您可以控制從類別或結構轉換的行為，包括可以擲回的例外狀況。

## <a name="overloading"></a>多載化

@No__t-0 運算子也可以在程式碼外部定義的類別或結構上多載。 如果您的程式碼會在這類類別或結構之間進行轉換，請務必瞭解其 @no__t 0 運算子的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。

## <a name="converting-dynamic-objects"></a>轉換動態物件

動態物件的類型轉換是由使用 <xref:System.Dynamic.DynamicObject.TryConvert%2A> 或 @no__t 1 方法的使用者定義動態轉換所執行。 如果您使用的是動態物件，請使用 <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> 方法來轉換動態物件。

## <a name="example"></a>範例

下列範例會使用 `CType` 函式將運算式轉換成 `Single` 資料類型。

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

如需其他範例，請參閱[隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [轉換函式](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md)
- [如何：定義轉換運算子 @ no__t-0
- [.NET Framework 中的型別轉換](../../../standard/base-types/type-conversion.md)
