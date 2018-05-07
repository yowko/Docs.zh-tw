---
title: 變數&#39; &lt;variablename&gt; &#39;已在指派值之前使用
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: d314f952bd6e11adaac642ba63ed292f48cda805
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="variable-39ltvariablenamegt39-is-used-before-it-has-been-assigned-a-value"></a>變數&#39; &lt;variablename&gt; &#39;已在指派值之前使用
變數 '\<變數名稱 >' 已在指派值之前使用。 可能會在執行階段產生 null 參考例外狀況。  
  
 應用程式已通過程式碼會讀取變數指派任何值之前，至少一個可能的路徑。  
  
 如果變數從未獲派值，則會持有其資料類型的預設值。 參考資料型別，該預設值是[Nothing](../../../visual-basic/language-reference/nothing.md)。 在某些情況下，讀取具有 `Nothing` 值的參考變數可能會導致 <xref:System.NullReferenceException> 。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC42104  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請檢查控制項流程邏輯，並確定變數具有有效的值，控制權會傳遞給讀取它的任何陳述式之前。  
  
-   若要保證變數一律具有有效的值的方法之一是初始化為其宣告的一部分。 請參閱中的初始化 」 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [變數宣告](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [變數的疑難排解](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
