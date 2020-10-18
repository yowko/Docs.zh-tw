---
title: 變數 '<variablename>' 已在指派值之前使用
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: 6db8626701267f2051b289b267e7b2d9da51c283
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162215"
---
# <a name="bc42104-variable-variablename-is-used-before-it-has-been-assigned-a-value"></a>BC42104：變數 ' \<variablename> ' 已在指派值之前使用

變數 ' \<variablename> ' 是在指派值之前使用。 可能會在執行階段產生 null 參考例外狀況。

 應用程式在其程式碼中至少有一個可能的路徑，可在指派任何值之前讀取變數。

 如果變數從未獲派值，則會持有其資料類型的預設值。 若是參考資料類型，該預設值為 [Nothing](../nothing.md)。 在某些情況下，讀取具有 `Nothing` 值的參考變數可能會導致 <xref:System.NullReferenceException> 。

 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。

 **錯誤識別碼：** BC42104

## <a name="to-correct-this-error"></a>更正這個錯誤

- 檢查您的控制流程邏輯，並確定變數具有有效的值，控制項才會傳遞至任何讀取它的語句。

- 保證變數一律具有有效值的其中一種方式，就是將它初始化為其宣告的一部分。 請參閱 [Dim 語句](../statements/dim-statement.md)中的「初始化」。

## <a name="see-also"></a>另請參閱

- [Dim 陳述式](../statements/dim-statement.md)
- [變數宣告](../../programming-guide/language-features/variables/variable-declaration.md)
- [變數的疑難排解](../../programming-guide/language-features/variables/troubleshooting-variables.md)
