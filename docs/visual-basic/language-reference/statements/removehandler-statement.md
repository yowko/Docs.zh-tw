---
title: RemoveHandler 語句（Visual Basic）
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 47f35bd76d7734878e7b5b206b4aecd856276593
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582014"
---
# <a name="removehandler-statement"></a>RemoveHandler 陳述式
移除事件與事件處理常式之間的關聯。  
  
## <a name="syntax"></a>語法  
  
```vb  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`event`|正在處理的事件名稱。|  
|`eventhandler`|目前處理事件的程式名稱。|  
  
## <a name="remarks"></a>備註  
 @No__t_0 和 `RemoveHandler` 語句可讓您在程式執行期間的任何時間，啟動和停止特定事件的事件處理。  
  
> [!NOTE]
> 若為自訂事件，`RemoveHandler` 語句會叫用事件的 `RemoveHandler` 存取子。 如需自訂事件的詳細資訊，請參閱[Event 語句](../../../visual-basic/language-reference/statements/event-statement.md)。  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>請參閱

- [AddHandler 陳述式](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)
- [事件](../../../visual-basic/programming-guide/language-features/events/index.md)
