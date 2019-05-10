---
title: Sub 或 Function 未定義 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 3a56d5596c79900bb5818a6ed7f8736859b5ea15
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593204"
---
# <a name="sub-or-function-not-defined-visual-basic"></a>Sub 或 Function 未定義 (Visual Basic)
A`Sub`或`Function`必須定義，才能呼叫。 可能導致本錯誤的原因包括：  
  
- 拼錯下列程序名稱。  
  
- 嘗試從另一個專案呼叫的程序，而不需明確新增至該專案中的參考**參考** 對話方塊。  
  
- 指定看不到呼叫的程序的程序。  
  
- Windows 動態連結程式庫 (DLL) 常式或 Macintosh 不在指定的文件庫或程式碼資源的程式碼資源常式宣告。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請確定程序名稱拼字正確。  
  
2. 尋找包含您想要呼叫的程序的專案名稱**參考** 對話方塊。 如果沒有出現，請按一下**瀏覽**按鈕來搜尋它。 選取的專案名稱，左邊的核取方塊，然後按一下**確定**。  
  
3. 請檢查常式的名稱。  
  
## <a name="see-also"></a>另請參閱

- [錯誤類型](../../../visual-basic/programming-guide/language-features/error-types.md)
- [管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)
- [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)
