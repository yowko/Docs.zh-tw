---
title: "繼承事件處理常式，在 Visual Basic 疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- troubleshooting events
- inherited events
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: f64395975821226d42664bbf78b04120d49a38bc
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="ff90d-102">Visual Basic 中的繼承事件處理常式疑難排解</span><span class="sxs-lookup"><span data-stu-id="ff90d-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="ff90d-103">本主題列出常見的問題發生的事件處理常式繼承之元件中。</span><span class="sxs-lookup"><span data-stu-id="ff90d-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="ff90d-104">程序</span><span class="sxs-lookup"><span data-stu-id="ff90d-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="ff90d-105">事件處理常式中的程式碼會執行兩次每次呼叫</span><span class="sxs-lookup"><span data-stu-id="ff90d-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
-   <span data-ttu-id="ff90d-106">繼承的事件處理常式，不能包含[處理](../../../../visual-basic/language-reference/statements/handles-clause.md)子句。</span><span class="sxs-lookup"><span data-stu-id="ff90d-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="ff90d-107">基底類別中的方法已經與事件相關聯，並據此將會引發。</span><span class="sxs-lookup"><span data-stu-id="ff90d-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="ff90d-108">移除`Handles`子句從繼承的方法。</span><span class="sxs-lookup"><span data-stu-id="ff90d-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     <span data-ttu-id="ff90d-109">[!code-vb[VbVbalrEvents #&32;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ff90d-109">[!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]</span></span>  
  
-   <span data-ttu-id="ff90d-110">如果繼承的方法沒有`Handles`關鍵字，確認您的程式碼不包含額外[AddHandler 陳述式](../../../../visual-basic/language-reference/statements/addhandler-statement.md)或任何其他方法處理相同的事件。</span><span class="sxs-lookup"><span data-stu-id="ff90d-110">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff90d-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff90d-111">See Also</span></span>  
 [<span data-ttu-id="ff90d-112">事件</span><span class="sxs-lookup"><span data-stu-id="ff90d-112">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
