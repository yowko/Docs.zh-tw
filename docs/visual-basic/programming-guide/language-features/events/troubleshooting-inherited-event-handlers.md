---
title: Visual Basic 中的繼承事件處理常式疑難排解
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: 704ca667a6d14ade7be0192e872f5e40791cb864
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830184"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Visual Basic 中的繼承事件處理常式疑難排解
本主題列出常見的問題所引發的繼承元件中的事件處理常式。  
  
## <a name="procedures"></a>程序  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>事件處理常式中的程式碼會執行兩次的每個呼叫  
  
-   不能包含繼承的事件處理常式[處理](../../../../visual-basic/language-reference/statements/handles-clause.md)子句。 基底類別中的方法已與事件相關聯，並據此將會引發。 移除`Handles`子句從繼承的方法。  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
-   如果繼承的方法沒有`Handles`關鍵字，確認您的程式碼不包含額外[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md)或任何其他方法處理相同的事件。  
  
## <a name="see-also"></a>另請參閱

- [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)
