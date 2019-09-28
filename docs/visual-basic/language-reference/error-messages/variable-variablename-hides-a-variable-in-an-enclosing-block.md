---
title: 變數 '<variablename>' 在封閉區塊中隱藏了變數
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 4312abef83728f432e2f6a492e5acad3450719b1
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592055"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a>變數 ' @no__t 0variablename > ' 隱藏封閉區塊中的變數
區塊中包含的變數與另一個區域變數具有相同的名稱。  
  
 **錯誤識別碼：** BC30616  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 將封閉區塊中的變數重新命名，使其與其他任何區域變數不同。 例如:  
  
    ```vb  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
- 此錯誤的常見原因是在事件處理常式內使用 `Catch e As Exception`。 如果是這種情況，請將 `Catch` 區塊變數命名為 `ex`，而不是 `e`。  
  
- 此錯誤的另一個常見來源，是嘗試存取在個別 `Catch` 區塊的 @no__t 0 區塊內所宣告的區域變數。 若要修正此錯誤，請在 `Try...Catch...Finally` 結構之外宣告變數。  
  
## <a name="see-also"></a>另請參閱

- [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [變數宣告](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
