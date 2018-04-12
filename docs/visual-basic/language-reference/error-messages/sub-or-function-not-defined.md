---
title: Sub 或 Function 未定義 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6237ca26b06bdffa06499607e634b3222725c189
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="sub-or-function-not-defined-visual-basic"></a>Sub 或 Function 未定義 (Visual Basic)
A`Sub`或`Function`必須定義，才能呼叫。 可能導致本錯誤的原因包括：  
  
-   拼錯的程序名稱。  
  
-   嘗試從另一個專案中呼叫程序，而不需要明確加入至該專案中參考**參考** 對話方塊。  
  
-   指定看不到呼叫的程序的程序。  
  
-   宣告 Windows 動態連結程式庫 (DLL) 常式或 Macintosh 不在指定的文件庫或程式碼資源的資源程式碼的常式。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確定程序名稱拼寫正確。  
  
2.  尋找包含您想要呼叫的程序的專案名稱**參考** 對話方塊。 如果沒有出現，請按一下**瀏覽**按鈕，以進行搜尋。 選取的專案名稱，左邊的核取方塊，然後按一下**確定**。  
  
3.  請檢查常式的名稱。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤類型](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)
