---
title: 針對繼承事件處理常式進行疑難排解
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: 4e7bedd1de5197fcf8b69091f4cc878f41b01cd5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405102"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Visual Basic 中的繼承事件處理常式疑難排解
本主題列出繼承元件中的事件處理常式所引發的常見問題。  
  
## <a name="procedures"></a>程序  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>事件處理常式中的程式碼會針對每個呼叫執行兩次  
  
- 繼承的事件處理常式不能包含[Handles](../../../language-reference/statements/handles-clause.md)子句。 基類中的方法已經與事件相關聯，並會據此引發。 請 `Handles` 從繼承的方法中移除子句。  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- 如果繼承的方法沒有 `Handles` 關鍵字，請確認您的程式碼未包含額外的[AddHandler 語句](../../../language-reference/statements/addhandler-statement.md)，或任何處理相同事件的其他方法。  
  
## <a name="see-also"></a>另請參閱

- [事件](index.md)
