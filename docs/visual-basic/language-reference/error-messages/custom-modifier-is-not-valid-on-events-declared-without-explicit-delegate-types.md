---
title: '&#39;自訂&#39;修飾詞宣告沒有以明確委派類型的事件中無效'
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: 3f08bbbbbac4a01dfbac8d15cf9285c01262618a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>&#39;自訂&#39;修飾詞宣告沒有以明確委派類型的事件中無效
不同於非自訂事件`Custom Event`宣告需要`As`子句之後明確地指定事件的委派類型的事件名稱。  
  
 非自訂的事件可能會定義與`As`子句和明確委派類型，或立即使用參數清單之後的事件名稱。  
  
 **錯誤 ID:** BC31122  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  為自訂的事件定義相同的參數清單的委派。  
  
     例如，如果`Custom Event`所定義`Custom Event Test(ByVal sender As Object, ByVal i As Integer)`，則對應的委派會是如下所示。  
  
     [!code-vb[VbVbalrEventError#18](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]  
  
2.  取代參數清單的自訂事件`As`子句指定委派類型。  
  
     此範例中，再繼續`Custom Event`宣告重新撰寫，如下所示。  
  
     [!code-vb[VbVbalrEventError#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]  
  
## <a name="example"></a>範例  
 這個範例會宣告`Custom Event`，並指定所需`As`具有委派型別子句。  
  
 [!code-vb[VbVbalrEventError#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [事件](../../../visual-basic/programming-guide/language-features/events/index.md)
