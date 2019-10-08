---
title: HOW TO：讓物件變數不參考任何實例（Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: e647f2f891b06aa1767faac49b01df98ea31ec1c
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004909"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>HOW TO：讓物件變數不參考任何實例（Visual Basic）
您可以藉由將物件變數設定為 [[無](../../../../visual-basic/language-reference/nothing.md)]，將它與任何物件實例取消關聯。  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>取消物件變數與任何物件實例的關聯  
  
- 在指派語句中，將變數設定為 `Nothing`。  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>穩固程式設計  
 如果您的程式碼嘗試存取已設定為 `Nothing` 之物件變數的成員，就會發生 <xref:System.NullReferenceException>。 如果您經常將物件變數設定為 `Nothing`，或是變數尚未初始化，則在 @no__t 1 區塊中括住成員存取是個不錯的主意。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 如果您使用物件變數做為包含機密或敏感性資料的物件，當您不積極處理其中一個物件時，可以將此變數設定為 `Nothing`。 這可減少惡意程式碼取得資料存取權的機會。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.NullReferenceException>
- [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [物件變數指派](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [Try...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
