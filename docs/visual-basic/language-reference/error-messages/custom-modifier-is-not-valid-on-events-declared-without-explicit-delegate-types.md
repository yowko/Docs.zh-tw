---
title: "'Custom' 修飾詞在沒有以明確委派類型宣告的事件中無效"
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: 88cdeccd7a3411b57a77116bde64d0a2cf8e537d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874537"
---
# <a name="custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>'Custom' 修飾詞在沒有以明確委派類型宣告的事件中無效

不同于非自訂事件，宣告 `Custom Event` 需要有 `As` 明確指定事件之委派類型的事件名稱後面的子句。  
  
 您可以使用子句和明確的委派類型來定義非自訂事件 `As` ，或以緊接在事件名稱後面的參數清單來定義。  
  
 **錯誤識別碼：** BC31122  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 使用與自訂事件相同的參數清單來定義委派。  
  
     例如，如果 `Custom Event` 是由定義，則 `Custom Event Test(ByVal sender As Object, ByVal i As Integer)` 對應的委派會如下所示。  
  
     [!code-vb[VbVbalrEventError#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#18)]  
  
2. 將自訂事件的參數清單取代為 `As` 指定委派類型的子句。  
  
     繼續進行此範例，會 `Custom Event` 以下列方式改寫宣告。  
  
     [!code-vb[VbVbalrEventError#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#19)]  
  
## <a name="example"></a>範例  

 這個範例會宣告 `Custom Event` ，並 `As` 使用委派類型指定必要的子句。  
  
 [!code-vb[VbVbalrEventError#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- [Event 陳述式](../statements/event-statement.md)
- [Delegate 陳述式](../statements/delegate-statement.md)
- [事件](../../programming-guide/language-features/events/index.md)
