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
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="ea167-102">Visual Basic 中的繼承事件處理常式疑難排解</span><span class="sxs-lookup"><span data-stu-id="ea167-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="ea167-103">本主題列出繼承元件中的事件處理常式所引發的常見問題。</span><span class="sxs-lookup"><span data-stu-id="ea167-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="ea167-104">程序</span><span class="sxs-lookup"><span data-stu-id="ea167-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="ea167-105">事件處理常式中的程式碼會針對每個呼叫執行兩次</span><span class="sxs-lookup"><span data-stu-id="ea167-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
- <span data-ttu-id="ea167-106">繼承的事件處理常式不能包含[Handles](../../../../visual-basic/language-reference/statements/handles-clause.md)子句。</span><span class="sxs-lookup"><span data-stu-id="ea167-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="ea167-107">基類中的方法已經與事件相關聯，並會據此引發。</span><span class="sxs-lookup"><span data-stu-id="ea167-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="ea167-108">請從繼承的方法中移除 `Handles` 子句。</span><span class="sxs-lookup"><span data-stu-id="ea167-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- <span data-ttu-id="ea167-109">如果繼承的方法沒有 `Handles` 關鍵字，請確認您的程式碼未包含額外的[AddHandler 語句](../../../../visual-basic/language-reference/statements/addhandler-statement.md)，或任何處理相同事件的其他方法。</span><span class="sxs-lookup"><span data-stu-id="ea167-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea167-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="ea167-110">See also</span></span>

- [<span data-ttu-id="ea167-111">事件</span><span class="sxs-lookup"><span data-stu-id="ea167-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
