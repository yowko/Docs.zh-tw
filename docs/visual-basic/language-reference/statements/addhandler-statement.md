---
title: AddHandler 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: c110116af75d4fb39c016b8d6afcdb707fa6599b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350182"
---
# <a name="addhandler-statement"></a>AddHandler 陳述式
Associates an event with an event handler at run time.  
  
## <a name="syntax"></a>語法  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>組件  
|||
|---|---|
|event|The name of the event to handle.|  
|`eventhandler`|The name of a procedure that handles the event.|
|||
  
## <a name="remarks"></a>備註  
 The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.  
  
 The signature of the `eventhandler` procedure must match the signature of the event `event`.  
  
 `Handles` 關鍵字和 `AddHandler` 陳述式都可以讓您指定由特定程序處理特定事件，但兩者存有差異。 `AddHandler` 陳述式會在執行階段將程序連接到事件。 當定義程序以指定它處理特定事件時，使用 `Handles` 關鍵字。 For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).  
  
> [!NOTE]
> For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor. For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>請參閱

- [RemoveHandler 陳述式](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)
- [事件](../../../visual-basic/programming-guide/language-features/events/index.md)
