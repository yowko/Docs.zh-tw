---
title: AddHandler 陳述式
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07fbfe04ccd01b7d0f99338ef2682238830099dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="addhandler-statement"></a>AddHandler 陳述式
將事件與事件處理常式在執行階段。  
  
## <a name="syntax"></a>語法  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>組件  
 `event`  
 要處理的事件名稱。  
  
 `eventhandler`  
 處理事件的程序的名稱。  
  
## <a name="remarks"></a>備註  
 `AddHandler`和`RemoveHandler`陳述式可讓您能夠啟動和停止程式執行期間的事件處理。  
  
 簽章`eventhandler`程序必須符合事件簽章`event`。  
  
 `Handles` 關鍵字和 `AddHandler` 陳述式都可以讓您指定由特定程序處理特定事件，但兩者存有差異。 `AddHandler` 陳述式會在執行階段將程序連接到事件。 當定義程序以指定它處理特定事件時，使用 `Handles` 關鍵字。 如需詳細資訊，請參閱[處理](../../../visual-basic/language-reference/statements/handles-clause.md)。  
  
> [!NOTE]
>  對於自訂事件，`AddHandler`陳述式會叫用此事件`AddHandler`存取子。 如需有關自訂事件的詳細資訊，請參閱[Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)。  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [RemoveHandler 陳述式](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)  
 [事件](../../../visual-basic/programming-guide/language-features/events/index.md)
