---
title: 屬性&#39; &lt;propertyname&gt; &#39;規定&#39;t 傳回有關所有程式碼路徑的值
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: 72bc7e45cadd2528f29c88bf6e80ee5f381052dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="property-39ltpropertynamegt39-doesn39t-return-a-value-on-all-code-paths"></a>屬性&#39; &lt;propertyname&gt; &#39;規定&#39;t 傳回有關所有程式碼路徑的值
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
