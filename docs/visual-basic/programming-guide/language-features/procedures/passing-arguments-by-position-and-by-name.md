---
title: 依位置和名稱傳遞引數 (Visual Basic)
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
ms.openlocfilehash: 2fa07a4ecf31b9dc0fee91593e793f3b00c5a83b
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524442"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>依位置和名稱傳遞引數 (Visual Basic)

當您呼叫 `Sub` 或 `Function` 程式時，您可以*依位置*傳遞引數（以它們出現在程式定義中的順序），也可以*依名稱*傳遞它們，而不考慮位置。

當您依名稱傳遞引數時，您可以指定引數的宣告名稱，後面接著冒號和等號（`:=`），後面接著引數值。 您可以依任何順序提供具名引數。

例如，下列 `Sub` 程式會採用三個引數：

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

當您呼叫此程式時，您可以依位置、名稱或混合使用兩者來提供引數。

## <a name="passing-arguments-by-position"></a>依位置傳遞引數

您可以呼叫 `Display` 方法，其其引數是由位置傳遞，並以逗號分隔，如下列範例所示：

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

如果您省略位置引數清單中的選擇性引數，則必須使用逗號來保存其位置。 下列範例會呼叫不含 `age` 引數的 `Display` 方法：

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a>依名稱傳遞引數

或者，您可以使用以名稱傳遞的引數（也以逗號分隔）來呼叫 `Display`，如下列範例所示：

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

當您呼叫具有多個選擇性引數的程式時，以這種方式依名稱傳遞引數特別有用。 如果您依名稱提供引數，則不需要使用連續的逗號來表示遺漏的位置引數。 以名稱傳遞引數也能讓您更輕鬆地追蹤您要傳遞的引數，以及您要省略哪一個。

## <a name="mixing-arguments-by-position-and-by-name"></a>依位置和名稱來混合引數

您可以在單一程序呼叫中，依位置和名稱提供引數，如下列範例所示：

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

在上述範例中，不需要額外的逗號來保存省略之 `age` 引數的位置，因為 `birth` 是以名稱傳遞。

在15.5 之前的 Visual Basic 版本中，當您以位置和名稱的混合來提供引數時，位置引數必須全部排在最前面。 當您依名稱提供引數之後，所有剩餘的引數都必須以名稱傳遞。  例如，下列對 `Display` 方法的呼叫會顯示編譯器錯誤[BC30241：預期的具名引數](../../../misc/bc30241.md)。

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

從 Visual Basic 15.5 開始，如果結束位置引數位於正確的位置，位置引數就可以跟隨具名引數。 如果在 Visual Basic 15.5 下編譯，則先前對 `Display` 方法的呼叫會編譯成功，且不再產生編譯器錯誤[BC30241](../../../misc/bc30241.md)。

當您想要使用具名引數，讓程式碼更容易閱讀時，這項混合和比對名稱和位置引數的功能特別有用。 例如，下列 `Person` 類別的函式需要 `Person` 類型的兩個引數，兩者都可以 `Nothing`。

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

當 `father` 和 `mother` 引數的值 `Nothing` 時，使用混合名稱和位置引數有助於讓程式碼的意圖清楚明瞭：

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

若要遵循具有具名引數的位置引數，您必須將下列專案加入至您的 Visual Basic 專案（\*. vbproj）檔案：

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

如需詳細資訊，請參閱[設定 Visual Basic 語言版本](../../../language-reference/configure-language-version.md)。

## <a name="restrictions-on-supplying-arguments-by-name"></a>依名稱提供引數的限制

您無法依名稱傳遞引數，以避免輸入必要的引數。 您只能省略選擇性的引數。

您無法依名稱傳遞參數陣列。 這是因為當您呼叫程式時，會為參數陣列提供不限數目的逗點分隔引數，而且編譯器無法將多個引數與單一名稱建立關聯。

## <a name="see-also"></a>請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)
- [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)
- [選擇性參數](./optional-parameters.md)
- [參數陣列](./parameter-arrays.md)
- [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)
- [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
