---
title: RemoveHandler 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: a815241f20be12b3b7b4f2b87d50a8965021bbf0
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871937"
---
# <a name="removehandler-statement"></a>RemoveHandler 陳述式

移除事件與事件處理常式之間的關聯。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`event`|正在處理的事件名稱。|  
|`eventhandler`|目前處理事件的程式名稱。|  
  
## <a name="remarks"></a>備註  

 `AddHandler`和 `RemoveHandler` 語句可讓您在程式執行期間，隨時啟動及停止特定事件的事件處理。  
  
> [!NOTE]
> 針對自訂事件，語句會叫用 `RemoveHandler` 事件的 `RemoveHandler` 存取子。 如需有關自訂事件的詳細資訊，請參閱 [事件語句](event-statement.md)。  
  
## <a name="example"></a>範例  

 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>另請參閱

- [AddHandler 陳述式](addhandler-statement.md)
- [處理](handles-clause.md)
- [Event 陳述式](event-statement.md)
- [事件](../../programming-guide/language-features/events/index.md)
