---
title: Sub 或 Function 未定義
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 24e290ce1193cd6bc6a0ec8985902576332423f2
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870516"
---
# <a name="sub-or-function-not-defined-visual-basic"></a>Sub 或 Function 未定義 (Visual Basic)

`Sub` `Function` 必須定義或，才能呼叫。 可能導致本錯誤的原因包括：  
  
- 程式名稱拼寫錯誤。  
  
- 嘗試從另一個專案呼叫程式，但未在 [ **參考** ] 對話方塊中明確加入該專案的參考。  
  
- 指定呼叫程式看不到的程式。  
  
- 宣告不在指定的程式庫或程式碼資源中的 Windows 動態連結程式庫 (DLL) 常式或 Macintosh 程式碼資源常式。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請確定程式名稱的拼寫正確。  
  
2. 在 [ **參考** ] 對話方塊中，尋找包含您想要呼叫之程式的專案名稱。 如果未出現，請按一下 [ **流覽]** 按鈕來進行搜尋。 選取專案名稱左邊的核取方塊，然後按一下 **[確定]**。  
  
3. 檢查常式的名稱。  
  
## <a name="see-also"></a>另請參閱

- [錯誤類型](../../programming-guide/language-features/error-types.md)
- [管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)
- [Sub 陳述式](../statements/sub-statement.md)
- [Function 陳述式](../statements/function-statement.md)
