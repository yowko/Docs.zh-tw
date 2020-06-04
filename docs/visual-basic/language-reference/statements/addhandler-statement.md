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
ms.openlocfilehash: de995a13b34678410e2af74b59f2d0c467982b75
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408480"
---
# <a name="addhandler-statement"></a>AddHandler 陳述式
在執行時間將事件與事件處理常式產生關聯。  
  
## <a name="syntax"></a>語法  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>組件  
|||
|---|---|
|event|要處理的事件名稱。|  
|`eventhandler`|處理事件的程式名稱。|
|||
  
## <a name="remarks"></a>備註  
 `AddHandler`和 `RemoveHandler` 語句可讓您在程式執行期間的任何時間啟動和停止事件處理。  
  
 程式的簽章 `eventhandler` 必須符合事件的簽章 `event` 。  
  
 `Handles` 關鍵字和 `AddHandler` 陳述式都可以讓您指定由特定程序處理特定事件，但兩者存有差異。 `AddHandler` 陳述式會在執行階段將程序連接到事件。 當定義程序以指定它處理特定事件時，使用 `Handles` 關鍵字。 如需詳細資訊，請參閱[控制碼](handles-clause.md)。  
  
> [!NOTE]
> 若為自訂事件，語句會叫用 `AddHandler` 事件的 `AddHandler` 存取子。 如需自訂事件的詳細資訊，請參閱[Event 語句](event-statement.md)。  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>另請參閱

- [RemoveHandler 陳述式](removehandler-statement.md)
- [控制代碼](handles-clause.md)
- [Event 陳述式](event-statement.md)
- [事件](../../programming-guide/language-features/events/index.md)
