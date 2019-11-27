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
ms.openlocfilehash: fd2ef1c25233cc1eaad6bcde68923688393b471d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345098"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Visual Basic 中的繼承事件處理常式疑難排解
本主題列出繼承元件中的事件處理常式所引發的常見問題。  
  
## <a name="procedures"></a>程序  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>事件處理常式中的程式碼會針對每個呼叫執行兩次  
  
- 繼承的事件處理常式不能包含[Handles](../../../../visual-basic/language-reference/statements/handles-clause.md)子句。 基類中的方法已經與事件相關聯，並會據此引發。 請從繼承的方法中移除 `Handles` 子句。  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- 如果繼承的方法沒有 `Handles` 關鍵字，請確認您的程式碼未包含額外的[AddHandler 語句](../../../../visual-basic/language-reference/statements/addhandler-statement.md)，或任何處理相同事件的其他方法。  
  
## <a name="see-also"></a>請參閱

- [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)
