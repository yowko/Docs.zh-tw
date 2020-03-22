---
title: 依位置和名稱傳遞引數
ms.date: 02/01/2018
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
ms.openlocfilehash: b6588335f7634cc87a9fc14cbfc4ba80baad1abb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400852"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>依位置和名稱傳遞引數 (Visual Basic)

調用`Sub`或`Function`過程時，可以*按位置*傳遞參數（按程序定義中顯示參數的順序）傳遞參數，也可以*按名稱*傳遞參數，而不考慮位置。

按名稱傳遞參數時，指定參數聲明的名稱後跟冒號和等號 （`:=`），後跟參數值。 您可以按任意順序提供具名引數。

例如，以下`Sub`過程採用三個參數：

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

調用此過程時，可以按位置、名稱或使用兩者的混合物提供參數。

## <a name="passing-arguments-by-position"></a>按位置傳遞參數

可以調用`Display`該方法，其參數通過位置，並通過逗號分隔，如以下示例所示：

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

如果在位置參數清單中省略可選參數，則必須使用逗號保留其位置。 下面的示例調用沒有`Display``age`參數的方法：

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a>按名稱傳遞參數

或者，可以使用通過名稱`Display`傳遞的參數進行調用，也可以用逗號分隔，如以下示例所示：

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

以這種方式按名稱傳遞參數在調用具有多個可選參數的過程時特別有用。 如果按名稱提供參數，則不必使用連續逗號來表示缺少的位置參數。 按名稱傳遞參數還便於跟蹤您傳遞的參數以及省略的參數。

## <a name="mixing-arguments-by-position-and-by-name"></a>按位置和名稱混合參數

您可以在單個程序呼叫中按位置和名稱提供參數，如以下示例所示：

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

在前面的示例中，不需要額外的逗號來保留省略`age`的參數的位置，因為`birth`是按名稱傳遞的。

在 15.5 之前的 Visual Basic 版本中，當您通過位置和名稱的混合提供參數時，位置參數必須都放在第一位。 按名稱提供參數後，所有剩餘的參數都必須按名稱傳遞。  例如，對`Display`該方法的以下調用顯示編譯器錯誤[BC30241：具名引數預期](../../../misc/bc30241.md)。

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

從 Visual Basic 15.5 開始，如果結束位置參數位於正確的位置，則位置參數可以遵循具名引數。 如果在 Visual Basic 15.5 下編譯，則對`Display`該方法的上一個調用將成功編譯，不再生成編譯器錯誤[BC30241](../../../misc/bc30241.md)。

當您希望使用具名引數使代碼更具可讀性時，這種以任意順序混合和匹配具名引數和位置參數的能力特別有用。 例如，以下`Person`類建構函式需要兩個類型的`Person`參數，這兩個參數都可以。 `Nothing`

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

使用混合命名和位置參數有助於在 和`father``mother`參數的值為`Nothing`時明確代碼的意圖：

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

要遵循具有具名引數的位置參數，必須向 Visual Basic 專案 （.vbproj）\*檔添加以下元素：

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

有關詳細資訊[，請參閱設置視覺化基礎語言版本](../../../language-reference/configure-language-version.md)。

## <a name="restrictions-on-supplying-arguments-by-name"></a>按名稱提供參數的限制

不能按名稱傳遞參數以避免輸入所需的參數。 只能省略可選參數。

不能按名稱傳遞參數陣列。 這是因為當您調用 過程時，為參數陣列提供無限數量的逗號分隔參數，並且編譯器不能將多個參數與單個名稱相關聯。

## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)
- [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)
- [可選參數](./optional-parameters.md)
- [參數陣列](./parameter-arrays.md)
- [選](../../../../visual-basic/language-reference/modifiers/optional.md)
- [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
