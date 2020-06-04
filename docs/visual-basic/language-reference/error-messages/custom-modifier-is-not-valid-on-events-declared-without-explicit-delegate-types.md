---
title: "'Custom' 修飾詞在沒有以明確委派類型宣告的事件中無效"
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: 0c5a4188fedf9685afdd1cde4c1de93a0b43b919
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409775"
---
# <a name="custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>'Custom' 修飾詞在沒有以明確委派類型宣告的事件中無效
不同于非自訂事件，宣告 `Custom Event` 需要 `As` 遵循事件名稱的子句，以明確指定事件的委派類型。  
  
 非自訂事件可以使用 `As` 子句和明確委派類型，或緊接在事件名稱後面的參數清單來定義。  
  
 **錯誤識別碼：** BC31122  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 使用與自訂事件相同的參數清單來定義委派。  
  
     例如，如果 `Custom Event` 是由所定義 `Custom Event Test(ByVal sender As Object, ByVal i As Integer)` ，則對應的委派會如下所示。  
  
     [!code-vb[VbVbalrEventError#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#18)]  
  
2. 將自訂事件的參數清單取代為 `As` 指定委派類型的子句。  
  
     繼續執行此範例時，會 `Custom Event` 以下列方式改寫宣告。  
  
     [!code-vb[VbVbalrEventError#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#19)]  
  
## <a name="example"></a>範例  
 這個範例會宣告 `Custom Event` ，並使用委派類型來指定必要的 `As` 子句。  
  
 [!code-vb[VbVbalrEventError#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- [Event 陳述式](../statements/event-statement.md)
- [Delegate 陳述式](../statements/delegate-statement.md)
- [事件](../../programming-guide/language-features/events/index.md)
