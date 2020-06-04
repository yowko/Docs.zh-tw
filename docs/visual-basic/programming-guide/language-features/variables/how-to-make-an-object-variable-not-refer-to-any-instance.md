---
title: 如何：讓物件變數不參考執行個體
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: cce2e59cb76652937868a731ad308872d1aba2f3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410447"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>如何：讓物件變數不參考執行個體 (Visual Basic)
您可以藉由將物件變數設定為 [[無](../../../language-reference/nothing.md)]，將它與任何物件實例取消關聯。  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>取消物件變數與任何物件實例的關聯  
  
- 在指派語句中，將變數設定為 `Nothing` 。  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>穩固程式設計  
 如果您的程式碼嘗試存取已設定為之物件變數的成員 `Nothing` ， <xref:System.NullReferenceException> 就會發生。 如果您將物件變數設定為 [ `Nothing` 經常]，或者如果可能是變數未初始化，最好將成員存取括在 `Try...Catch...Finally` 區塊中。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 如果您針對包含機密或敏感性資料的物件使用物件變數，則可以在 `Nothing` 不積極處理其中一個物件時，將該變數設定為。 這可減少惡意程式碼取得資料存取權的機會。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.NullReferenceException>
- [物件變數](object-variables.md)
- [物件變數指派](object-variable-assignment.md)
- [Nothing](../../../language-reference/nothing.md)
- [Try...Catch...Finally 陳述式](../../../language-reference/statements/try-catch-finally-statement.md)
