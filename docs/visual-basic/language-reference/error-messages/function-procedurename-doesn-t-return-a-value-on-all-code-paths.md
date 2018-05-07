---
title: 函式&#39;&lt;程序名稱&gt;&#39;規定&#39;t 傳回有關所有程式碼路徑的值
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: 4c18c6229eb170e8a688aaa2734ae8fbfa081061
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="function-39ltprocedurenamegt39-doesn39t-return-a-value-on-all-code-paths"></a>函式&#39;&lt;程序名稱&gt;&#39;規定&#39;t 傳回有關所有程式碼路徑的值
函式 '\<程序名稱 >' 並未傳回有關所有程式碼路徑的值。 您是否遺漏了 'Return' 陳述式？  
  
 A`Function`程序有至少一個通過程式碼不會傳回值的可能路徑。  
  
 您可以傳回值，以從`Function`任何下列方式的程序：  
  
-   包含中的值[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)。  
  
-   將值指定給`Function`程序名稱，然後執行`Exit Function`陳述式。  
  
-   將值指定給`Function`程序名稱，然後執行`End Function`陳述式。  
  
 如果控制權傳遞給`Exit Function`或`End Function`和您沒有指派任何值的程序名稱、 程序傳回的傳回資料類型的預設值。 如需詳細資訊，請參閱 「 行為 」 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC42105  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請檢查控制項流程邏輯，並確定您指派值之前傳回每個陳述式。  
  
     若要保證每一次從程序傳回將傳回值，如果您總是使用更容易`Return`陳述式。 如果您這麼做之前, 的最後一個陳述式`End Function`應該`Return`陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [函式程序](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
 [專案設計工具、編譯頁面 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
