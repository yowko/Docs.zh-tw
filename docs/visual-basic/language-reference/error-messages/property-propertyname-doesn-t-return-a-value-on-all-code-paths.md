---
title: 屬性 &#39;&lt;propertyname&gt;&#39; 沒有 &#39; t 傳回有關所有程式碼路徑的值
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c9ef5b2ac62412f5684cbc78ab6bebf6bc7b6752
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="property-39ltpropertynamegt39-doesn39t-return-a-value-on-all-code-paths"></a>屬性 &#39;&lt;propertyname&gt;&#39; 沒有 &#39; t 傳回有關所有程式碼路徑的值
屬性 '\<屬性名稱 >' 並未傳回有關所有程式碼路徑的值。 使用結果時，Null 參考例外狀況可能在執行階段時發生。  
  
 屬性`Get`程序有至少一個通過程式碼不會傳回值的可能路徑。  
  
 您可以從屬性傳回值`Get`任何下列方式的程序：  
  
-   將值指派給屬性名稱，然後執行`Exit Property`陳述式。  
  
-   將值指派給屬性名稱，然後執行`End Get`陳述式。  
  
-   包含中的值[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)。  
  
 如果控制權傳遞給`Exit Property`或`End Get`和您不指派任何值給屬性名稱，`Get`程序會傳回屬性的資料類型的預設值。 如需詳細資訊，請參閱 「 行為 」 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC42107  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請檢查控制項流程邏輯，並確定您指派值之前傳回每個陳述式。  
  
     若要保證每一次從程序傳回將傳回值，如果您總是使用更容易`Return`陳述式。 如果您這麼做之前, 的最後一個陳述式`End Get`應該`Return`陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [屬性程序](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Get 陳述式](../../../visual-basic/language-reference/statements/get-statement.md)
