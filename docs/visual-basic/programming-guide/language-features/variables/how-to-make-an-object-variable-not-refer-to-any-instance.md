---
title: HOW TO：讓物件變數不參考任何執行個體 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 373d4ae84c44b212ad02b0b4266af75921e40423
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818682"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>HOW TO：讓物件變數不參考任何執行個體 (Visual Basic)
您可以藉由將它設定為取消關聯的物件變數，從任何物件執行個體[Nothing](../../../../visual-basic/language-reference/nothing.md)。  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>若要解除關聯的物件變數，從任何物件執行個體  
  
-   將變數設定為`Nothing`指派陳述式中。  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>穩固程式設計  
 如果您的程式碼嘗試存取已設定為物件變數的成員`Nothing`、 <xref:System.NullReferenceException> ，就會發生。 如果您設定物件變數`Nothing`通常，如果有可能未初始化的變數，則會是個不錯的主意，來括住在成員存取`Try...Catch...Finally`區塊。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 如果您使用物件變數包含機密或敏感性資料的物件時，您可以將變數設`Nothing`時您都不需要主動處理的其中一個這些物件。 這可以減少取得資料的存取權的惡意程式碼的機會。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.NullReferenceException>
- [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [物件變數指派](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [Try...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
