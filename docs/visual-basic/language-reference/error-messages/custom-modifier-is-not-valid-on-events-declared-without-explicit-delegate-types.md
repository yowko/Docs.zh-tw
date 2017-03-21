---
title: "&quot;Custom&quot; 修飾詞宣告沒有以明確委派類型的事件無效 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31122
- bc31122
dev_langs:
- VB
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
caps.latest.revision: 9
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 0e70fca6a0608df5db43156f70196b4e5c9b2339
ms.lasthandoff: 03/13/2017

---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>'Custom' 修飾詞宣告沒有以明確委派類型的事件無效
不同於非自訂事件`Custom Event`宣告需要`As`明確指定事件的委派類型的事件名稱後面的子句。  
  
 非自訂事件可能會定義與`As`子句和明確委派類型，或立即使用參數清單之後的事件名稱。  
  
 **錯誤識別碼︰** BC31122  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  定義自訂事件的委派具有相同的參數清單。  
  
     例如，如果`Custom Event`所定義`Custom Event Test(ByVal sender As Object, ByVal i As Integer)`，則對應的委派會是下列。  
  
     [!code-vb[VbVbalrEventError #&18;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]  
  
2.  取代參數清單的自訂事件`As`子句指定的委派型別。  
  
     此範例中，繼續`Custom Event`宣告重新撰寫，如下所示。  
  
     [!code-vb[VbVbalrEventError #&19;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]  
  
## <a name="example"></a>範例  
 這個範例會宣告`Custom Event`，並指定必要`As`具有委派型別子句。  
  
 [!code-vb[VbVbalrEventError #&2;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [事件](../../../visual-basic/programming-guide/language-features/events/index.md)
