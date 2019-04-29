---
title: 變數 '<variablename>' 已在指派值之前使用
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: 46551a917aeb794c8d35985076b67a315386f628
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766723"
---
# <a name="variable-variablename-is-used-before-it-has-been-assigned-a-value"></a>變數 '\<變數名稱 >' 已在指派值之前使用
變數 '\<變數名稱 >' 已在指派值之前使用。 可能會在執行階段產生 null 參考例外狀況。  
  
 應用程式必須至少一個可能的路徑，透過其讀取變數之前的任何值指派給它, 的程式碼。  
  
 如果變數從未獲派值，則會持有其資料類型的預設值。 若是參考資料類型，該預設值為 [Nothing](../../../visual-basic/language-reference/nothing.md)。 在某些情況下，讀取具有 `Nothing` 值的參考變數可能會導致 <xref:System.NullReferenceException> 。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC42104  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 檢查控制項流程邏輯，並確定該變數具有有效的值，控制權會傳遞給讀取它的任何陳述式之前。  
  
- 保證變數一律擁有有效的值的一個方式是初始化為其宣告的一部分。 請參閱中的 「 初始化 」 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)。  
  
## <a name="see-also"></a>另請參閱

- [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)
- [變數宣告](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [變數的疑難排解](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
