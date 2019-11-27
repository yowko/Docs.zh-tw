---
title: 如何：讓物件變數不參考執行個體
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 320dadb61c12f3339c5328dcef31c41503892c56
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352887"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>如何：讓物件變數不參考執行個體 (Visual Basic)
您可以藉由將物件變數設定為 [[無](../../../../visual-basic/language-reference/nothing.md)]，將它與任何物件實例取消關聯。  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>取消物件變數與任何物件實例的關聯  
  
- 將變數設定為指派語句中的 `Nothing`。  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>最佳化程式設計  
 如果您的程式碼嘗試存取已設定為 `Nothing`之物件變數的成員，就會發生 <xref:System.NullReferenceException>。 如果您將物件變數設定為經常 `Nothing`，或是變數尚未初始化，最好將成員存取放在 `Try...Catch...Finally` 區塊中。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 如果您針對包含機密或敏感性資料的物件使用物件變數，您可以將變數設定為在不積極處理其中一個物件時 `Nothing`。 這可減少惡意程式碼取得資料存取權的機會。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.NullReferenceException>
- [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [物件變數指派](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [Try...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
