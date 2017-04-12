---
title: "屬性 &quot;&lt;propertyname&gt;&quot; 並未傳回有關所有程式碼路徑的值 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42107
- vbc42107
dev_langs:
- VB
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e7c94d827761ad26d517b44a06734c5db4480a62
ms.lasthandoff: 03/13/2017

---
# <a name="property-39ltpropertynamegt39-doesn39t-return-a-value-on-all-code-paths"></a>屬性 '&lt;propertyname&gt;' 並未傳回有關所有程式碼路徑的值
屬性 '\<propertyname >' 並未傳回有關所有程式碼路徑的值。 使用結果時，Null 參考例外狀況可能在執行階段時發生。  
  
 屬性`Get`程序將不會傳回值，其程式碼透過至少一個可能的路徑。  
  
 您可以從屬性傳回值`Get`程序中任何以下列方式︰  
  
-   將值指派給屬性的名稱，然後執行`Exit Property`陳述式。  
  
-   將值指派給屬性的名稱，然後執行`End Get`陳述式。  
  
-   包含的值在[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)。  
  
 控制權會傳遞給`Exit Property`或`End Get`您尚未指派任何值的屬性名稱，和`Get`程序會傳回屬性的資料類型的預設值。 如需詳細資訊，請參閱 「 行為 」 中[Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告，或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼︰** BC42107  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   檢查控制項流程邏輯，並確定您指定的值，傳回每個陳述式之前。  
  
     很容易就能保證每一次從程序傳回傳回值，如果您總是使用`Return`陳述式。 如果您這麼做之前, 的最後一個陳述式`End Get`應該`Return`陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [Property 程序](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Get 陳述式](../../../visual-basic/language-reference/statements/get-statement.md)
