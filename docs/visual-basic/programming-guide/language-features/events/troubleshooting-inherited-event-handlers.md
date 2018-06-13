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
ms.openlocfilehash: f6355cf7fc2e43651c1112d048220a8179968c76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646302"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="1bf6a-102">Visual Basic 中的繼承事件處理常式疑難排解</span><span class="sxs-lookup"><span data-stu-id="1bf6a-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="1bf6a-103">本主題列出常見繼承之元件中的事件處理常式會產生的問題。</span><span class="sxs-lookup"><span data-stu-id="1bf6a-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="1bf6a-104">程序</span><span class="sxs-lookup"><span data-stu-id="1bf6a-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="1bf6a-105">事件處理常式中的程式碼會執行兩次的每個呼叫</span><span class="sxs-lookup"><span data-stu-id="1bf6a-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
-   <span data-ttu-id="1bf6a-106">繼承的事件處理常式不能包含[處理](../../../../visual-basic/language-reference/statements/handles-clause.md)子句。</span><span class="sxs-lookup"><span data-stu-id="1bf6a-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="1bf6a-107">基底類別中的方法已經與事件相關聯，並據此將會引發。</span><span class="sxs-lookup"><span data-stu-id="1bf6a-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="1bf6a-108">移除`Handles`子句從繼承的方法。</span><span class="sxs-lookup"><span data-stu-id="1bf6a-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]  
  
-   <span data-ttu-id="1bf6a-109">如果繼承的方法沒有`Handles`關鍵字，確認您的程式碼不包含額外[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md)或任何其他方法處理相同的事件。</span><span class="sxs-lookup"><span data-stu-id="1bf6a-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bf6a-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bf6a-110">See Also</span></span>  
 [<span data-ttu-id="1bf6a-111">事件</span><span class="sxs-lookup"><span data-stu-id="1bf6a-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
