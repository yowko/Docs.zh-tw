---
title: "如何：讓物件變數不參考執行個體 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3b33aef06300bf35b7138ec5b40747532a77140a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>如何：讓物件變數不參考執行個體 (Visual Basic)
您可以取消從任何物件執行個體的物件變數設定為[Nothing](../../../../visual-basic/language-reference/nothing.md)。  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>取消關聯的任何物件執行個體的物件變數  
  
-   將變數設`Nothing`指派陳述式中。  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>穩固程式設計  
 如果您的程式碼嘗試存取已設定為物件變數的成員`Nothing`、 <xref:System.NullReferenceException> ，就會發生。 如果您設定物件變數`Nothing`通常，如果是可行的變數未初始化，則是個不錯的主意括住中的成員存取`Try...Catch...Finally`區塊。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 如果您使用物件變數包含機密或敏感性資料的物件時，您可以將變數設`Nothing`當您在未主動處理使用其中一個物件。 這可以減少取得資料的存取權的惡意程式碼的機會。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.NullReferenceException>  
 [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [物件變數指派](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Nothing](../../../../visual-basic/language-reference/nothing.md)  
 [Try...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [疑難排解例外狀況：System.NullReferenceException](http://msdn.microsoft.com/library/4822b0b4-8105-43fb-887a-3cc51ff02899)
