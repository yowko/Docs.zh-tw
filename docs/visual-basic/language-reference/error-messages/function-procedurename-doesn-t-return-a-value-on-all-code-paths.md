---
title: 函式 '<procedurename>' 並未傳回有關所有程式碼路徑的值
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: 19b305e337767dfb34718aed7b665f142851bd36
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163359"
---
# <a name="bc42105-function-procedurename-doesnt-return-a-value-on-all-code-paths"></a>BC42105：函式 ' \<procedurename> ' 未傳回所有程式碼路徑的值

函數 ' \<procedurename> ' 不會傳回所有程式碼路徑的值。 您是否遺漏了 ' Return ' 語句？

 `Function`程式在其程式碼中至少有一個可能的路徑不會傳回值。

 您可以使用下列任何一種方式，從程式傳回值 `Function` ：

- 在 [Return 語句](../statements/return-statement.md)中包含值。

- 將值指派給程式 `Function` 名稱，然後執行 `Exit Function` 語句。

- 將值指派給程式 `Function` 名稱，然後執行 `End Function` 語句。

 如果控制權傳遞給 `Exit Function` 或， `End Function` 而且您沒有將任何值指派給程式名稱，則程式會傳回傳回資料類型的預設值。 如需詳細資訊，請參閱 [Function 語句](../statements/function-statement.md)中的「行為」。

 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。

 **錯誤識別碼：** BC42105

## <a name="to-correct-this-error"></a>更正這個錯誤

- 檢查您的控制流程邏輯，並確定您在每個導致傳回的語句之前指派一個值。

     如果您一律使用語句，則可更輕鬆地確保從程式傳回的每個傳回值 `Return` 。 如果您這樣做，之前的最後一個語句 `End Function` 應該是 `Return` 語句。

## <a name="see-also"></a>另請參閱

- [Function 程序](../../programming-guide/language-features/procedures/function-procedures.md)
- [Function 陳述式](../statements/function-statement.md)
- [專案設計工具、編譯頁 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
