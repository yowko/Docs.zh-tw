---
title: 如何：讓物件變數不參考執行個體
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 61bb06401ebd1e479c9256a80a12d87240831063
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91080249"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>如何：讓物件變數不參考執行個體 (Visual Basic)

您可以藉由將物件變數設定為 [Nothing](../../../language-reference/nothing.md)，將物件變數與任何物件實例解除關聯。  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>將物件變數與任何物件實例解除關聯  
  
- `Nothing`在指派語句中將變數設為。  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>穩固程式設計  

 如果您的程式碼嘗試存取已設定為的物件變數成員 `Nothing` ，則 <xref:System.NullReferenceException> 會發生。 如果您經常將物件變數設定為 `Nothing` ，或變數未初始化，則將成員存取放在區塊中是很好的做法 `Try...Catch...Finally` 。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  

 如果您針對包含機密資料或機密資料的物件使用物件變數，您可以在 `Nothing` 不主動處理其中一個物件時，將變數設為。 這樣可減少惡意程式碼存取資料的機會。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.NullReferenceException>
- [物件變數](object-variables.md)
- [物件變數指派](object-variable-assignment.md)
- [什麼](../../../language-reference/nothing.md)
- [Try...Catch...Finally 陳述式](../../../language-reference/statements/try-catch-finally-statement.md)
