---
title: "Sub 或 Function 未定義 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID35
dev_langs:
- VB
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7d32bc9c8f13b245e6333c4460cab541f6e9409e
ms.lasthandoff: 03/13/2017

---
# <a name="sub-or-function-not-defined-visual-basic"></a>Sub 或 Function 未定義 (Visual Basic)
A`Sub`或`Function`必須定義，才能呼叫。 可能導致本錯誤的原因包括：  
  
-   程序名稱的拼字錯誤。  
  
-   嘗試從另一個專案呼叫的程序，而不需要明確地將參考加入專案中**參考**對話方塊。  
  
-   指定看不到呼叫的程序的程序。  
  
-   Windows 動態連結程式庫 (DLL) 常式或 Macintosh 不在指定的文件庫或程式碼資源的程式碼資源常式宣告。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確定該程序名稱拼寫正確。  
  
2.  找出包含您想要呼叫的程序的專案名稱**參考**對話方塊。 如果沒有出現，按一下 [**瀏覽**] 按鈕，以進行搜尋。 選取的專案名稱，左邊的核取方塊，然後按一下**確定**。  
  
3.  請檢查常式的名稱。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤類型](../../../visual-basic/programming-guide/language-features/error-types.md)   
 [管理專案中的參考](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)   
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)
