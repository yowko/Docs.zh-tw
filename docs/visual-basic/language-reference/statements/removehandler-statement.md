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
ms.openlocfilehash: 0d982768707948bd6c616445509e16a462b86f2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597984"
---
# <a name="removehandler-statement"></a>RemoveHandler 陳述式
移除事件和事件處理常式之間的關聯。  
  
## <a name="syntax"></a>語法  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`event`|要處理事件的名稱。|  
|`eventhandler`|目前正在處理事件的程序的名稱。|  
  
## <a name="remarks"></a>備註  
 `AddHandler`和`RemoveHandler`陳述式可讓您能夠啟動和停止程式執行期間，隨時特定事件的事件處理。  
  
> [!NOTE]
>  對於自訂事件，`RemoveHandler`陳述式會叫用此事件`RemoveHandler`存取子。 如需有關自訂事件的詳細資訊，請參閱[Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)。  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [AddHandler 陳述式](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)  
 [事件](../../../visual-basic/programming-guide/language-features/events/index.md)
