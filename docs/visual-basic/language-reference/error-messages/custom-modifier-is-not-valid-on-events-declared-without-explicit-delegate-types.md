---
title: "'Custom' 修飾詞在沒有以明確委派類型宣告的事件中無效"
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: 169cb49cc5abc76b7c52785392d0083b81a99450
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803879"
---
# <a name="custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>'Custom' 修飾詞在沒有以明確委派類型宣告的事件中無效
不同於非自訂事件`Custom Event`宣告需要`As`事件名稱，明確地指定事件的委派型別後面的子句。  
  
 非自訂事件可以是定義使用`As`子句和明確委派類型，或立即使用參數清單後面的事件名稱。  
  
 **錯誤 ID:** BC31122  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 定義自訂事件的委派具有相同的參數清單。  
  
     例如，如果`Custom Event`已定義`Custom Event Test(ByVal sender As Object, ByVal i As Integer)`，則對應的委派會是如下所示。  
  
     [!code-vb[VbVbalrEventError#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#18)]  
  
2. 將自訂事件的參數清單`As`子句指定的委派型別。  
  
     此範例中，再繼續`Custom Event`宣告重新撰寫，如下所示。  
  
     [!code-vb[VbVbalrEventError#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#19)]  
  
## <a name="example"></a>範例  
 這個範例會宣告`Custom Event`，並指定必要`As`子句與委派型別。  
  
 [!code-vb[VbVbalrEventError#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)
- [Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [事件](../../../visual-basic/programming-guide/language-features/events/index.md)
