---
title: Lambda 運算式不是有效的第一個運算式中 &#39;選取案例 &#39;陳述式
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e91401d6891d4e38014bb716a337560885cf73a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-39select-case39-statement"></a>Lambda 運算式不是有效的第一個運算式中 &#39;選取案例 &#39;陳述式
您無法使用 lambda 運算式中的測試運算式`Select Case`陳述式。 Lambda 運算式定義傳回函式和測試運算式的`Select Case`陳述式必須是基本資料類型。  
  
 下列程式碼會造成這個錯誤：  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 **錯誤 ID:** BC36635  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   檢查您的程式碼，以判斷不同的條件式建構 (例如 `If...Then...Else` 陳述式) 是否可行。  
  
-   您可能想要呼叫的函式，如下列程式碼所示：  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a>另請參閱  
 [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [If...Then...Else 陳述式](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Select...Case 陳述式](../../../visual-basic/language-reference/statements/select-case-statement.md)
