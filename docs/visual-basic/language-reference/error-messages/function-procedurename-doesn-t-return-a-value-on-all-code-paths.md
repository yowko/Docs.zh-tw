---
title: 函式&#39;&lt;程序名稱&gt;&#39;不&#39;t 傳回有關所有程式碼路徑的值
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: b6cc5143aafb6c2554b183a1fc5fb3b1331ec5d0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552186"
---
# <a name="function-39ltprocedurenamegt39-doesn39t-return-a-value-on-all-code-paths"></a>函式&#39;&lt;程序名稱&gt;&#39;不&#39;t 傳回有關所有程式碼路徑的值
函式 '\<程序名稱 >' 並未傳回有關所有程式碼路徑的值。 您是否遺漏了 'Return' 陳述式？  
  
 A`Function`程序中的至少一個通過程式碼不會傳回值的可能的路徑。  
  
 您可以傳回值，以從`Function`程序，在下列任一方式：  
  
-   包含值[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)。  
  
-   將值指派給`Function`程序名稱，然後再執行`Exit Function`陳述式。  
  
-   將值指派給`Function`程序名稱，然後再執行`End Function`陳述式。  
  
 如果控制權傳遞給`Exit Function`或`End Function`和您不指派任何值給程序名稱、 程序傳回的傳回資料類型的預設值。 如需詳細資訊，請參閱 「 行為 」 中[Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC42105  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   檢查控制項流程邏輯，並確定您指定的值會導致傳回每個陳述式之前。  
  
     很容易就能保證每一次從程序傳回將傳回值，如果您總是使用`Return`陳述式。 如果您這麼做，最後一個陳述式前面`End Function`應該是`Return`陳述式。  
  
## <a name="see-also"></a>另請參閱
- [函式程序](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)
- [專案設計工具、編譯頁面 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
