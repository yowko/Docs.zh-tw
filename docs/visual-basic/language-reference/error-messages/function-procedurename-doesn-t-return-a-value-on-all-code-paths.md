---
title: "函式 &quot;&lt;m e&gt;&quot; 並未傳回有關所有程式碼路徑的值 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42105
- vbc42105
dev_langs:
- VB
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
caps.latest.revision: 12
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
ms.openlocfilehash: 288fdf7c4845b20283681d9eb3504ac314f1ddd2
ms.lasthandoff: 03/13/2017

---
# <a name="function-39ltprocedurenamegt39-doesn39t-return-a-value-on-all-code-paths"></a>函式 '&lt;m e&gt;' 並未傳回有關所有程式碼路徑的值
函式 '\<m e >' 並未傳回有關所有程式碼路徑的值。 您是否遺漏 'Return' 陳述式？  
  
 A`Function`程序將不會傳回值，其程式碼透過至少一個可能的路徑。  
  
 您可以傳回值，以從`Function`程序中任何以下列方式︰  
  
-   包含的值在[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)。  
  
-   指派值`Function`程序名稱，然後執行`Exit Function`陳述式。  
  
-   指派值`Function`程序名稱，然後執行`End Function`陳述式。  
  
 控制權會傳遞給`Exit Function`或`End Function`您尚未指派任何值的程序名稱、 程序傳回的傳回資料類型的預設值。 如需詳細資訊，請參閱 「 行為 」 中[Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告，或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼︰** BC42105  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   檢查控制項流程邏輯，並確定您指定的值，傳回每個陳述式之前。  
  
     很容易就能保證每一次從程序傳回傳回值，如果您總是使用`Return`陳述式。 如果您這麼做之前, 的最後一個陳述式`End Function`應該`Return`陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [Function 程序](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)   
 [專案設計工具、編譯頁面 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
