---
title: 變數 '<variablename>' 在封閉區塊中隱藏了變數
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 474a920c9cfdfba7a8157320d9c88b8677958425
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406517"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a>變數 '\<variablename>' 在封閉區塊中隱藏了變數
區塊中包含的變數與另一個區域變數具有相同的名稱。  
  
 **錯誤識別碼：** BC30616  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 將封閉區塊中的變數重新命名，使其與其他任何區域變數不同。 例如：  
  
    ```vb  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
- 此錯誤的常見原因是在 `Catch e As Exception` 事件處理常式內使用。 如果是這種情況，請將 `Catch` 區塊變數命名為， `ex` 而不是 `e` 。  
  
- 這個錯誤的另一個常見來源，是嘗試存取在不同區塊中的區塊內所宣告的本機變數 `Try` `Catch` 。 若要修正此錯誤，請在結構外宣告變數 `Try...Catch...Finally` 。  
  
## <a name="see-also"></a>另請參閱

- [Try...Catch...Finally 陳述式](../statements/try-catch-finally-statement.md)
- [變數宣告](../../programming-guide/language-features/variables/variable-declaration.md)
