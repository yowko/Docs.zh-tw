---
title: 屬性 '<propertyname>' 不會在所有程式碼路徑上傳回值
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: 0736e2cbcdea1422d40161c88f898d487f72e3bc
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162384"
---
# <a name="bc42107-property-propertyname-doesnt-return-a-value-on-all-code-paths"></a>BC42107：屬性 ' \<propertyname> ' 未傳回所有程式碼路徑的值

屬性 ' \<propertyname> ' 在所有程式碼路徑上都不會傳回值。 使用結果時，Null 參考例外狀況可能在執行階段時發生。

屬性 `Get` 程式在其程式碼中至少有一個可能的路徑不會傳回值。

 您可以使用下列任何一種方式，從屬性程式傳回值 `Get` ：

- 將值指派給屬性名稱，然後執行 `Exit Property` 語句。

- 將值指派給屬性名稱，然後執行 `End Get` 語句。

- 在 [Return 語句](../statements/return-statement.md)中包含值。

如果控制權傳遞給 `Exit Property` 或， `End Get` 而且您尚未指派任何值給屬性名稱，則程式會傳回 `Get` 屬性之資料類型的預設值。 如需詳細資訊，請參閱 [Function 語句](../statements/function-statement.md)中的「行為」。

根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。

**錯誤識別碼：** BC42107

## <a name="to-correct-this-error"></a>更正這個錯誤

- 檢查您的控制流程邏輯，並確定您在每個導致傳回的語句之前指派一個值。

  如果您一律使用語句，則可更輕鬆地確保從程式傳回的每個傳回值 `Return` 。 如果您這樣做，之前的最後一個語句 `End Get` 應該是 `Return` 語句。

## <a name="see-also"></a>另請參閱

- [屬性程序](../../programming-guide/language-features/procedures/property-procedures.md)
- [Property Statement](../statements/property-statement.md)
- [Get 陳述式](../statements/get-statement.md)
