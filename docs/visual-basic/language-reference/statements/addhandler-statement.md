---
title: "AddHandler 陳述式"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords: AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07fbfe04ccd01b7d0f99338ef2682238830099dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="addhandler-statement"></a><span data-ttu-id="c3609-102">AddHandler 陳述式</span><span class="sxs-lookup"><span data-stu-id="c3609-102">AddHandler Statement</span></span>
<span data-ttu-id="c3609-103">將事件與事件處理常式在執行階段。</span><span class="sxs-lookup"><span data-stu-id="c3609-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3609-104">語法</span><span class="sxs-lookup"><span data-stu-id="c3609-104">Syntax</span></span>  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="c3609-105">組件</span><span class="sxs-lookup"><span data-stu-id="c3609-105">Parts</span></span>  
 `event`  
 <span data-ttu-id="c3609-106">要處理的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="c3609-106">The name of the event to handle.</span></span>  
  
 `eventhandler`  
 <span data-ttu-id="c3609-107">處理事件的程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="c3609-107">The name of a procedure that handles the event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3609-108">備註</span><span class="sxs-lookup"><span data-stu-id="c3609-108">Remarks</span></span>  
 <span data-ttu-id="c3609-109">`AddHandler`和`RemoveHandler`陳述式可讓您能夠啟動和停止程式執行期間的事件處理。</span><span class="sxs-lookup"><span data-stu-id="c3609-109">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="c3609-110">簽章`eventhandler`程序必須符合事件簽章`event`。</span><span class="sxs-lookup"><span data-stu-id="c3609-110">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="c3609-111">`Handles` 關鍵字和 `AddHandler` 陳述式都可以讓您指定由特定程序處理特定事件，但兩者存有差異。</span><span class="sxs-lookup"><span data-stu-id="c3609-111">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="c3609-112">`AddHandler` 陳述式會在執行階段將程序連接到事件。</span><span class="sxs-lookup"><span data-stu-id="c3609-112">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="c3609-113">當定義程序以指定它處理特定事件時，使用 `Handles` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c3609-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="c3609-114">如需詳細資訊，請參閱[處理](../../../visual-basic/language-reference/statements/handles-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="c3609-114">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3609-115">對於自訂事件，`AddHandler`陳述式會叫用此事件`AddHandler`存取子。</span><span class="sxs-lookup"><span data-stu-id="c3609-115">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="c3609-116">如需有關自訂事件的詳細資訊，請參閱[Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="c3609-116">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3609-117">範例</span><span class="sxs-lookup"><span data-stu-id="c3609-117">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c3609-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3609-118">See Also</span></span>  
 [<span data-ttu-id="c3609-119">RemoveHandler 陳述式</span><span class="sxs-lookup"><span data-stu-id="c3609-119">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [<span data-ttu-id="c3609-120">Handles</span><span class="sxs-lookup"><span data-stu-id="c3609-120">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="c3609-121">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="c3609-121">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="c3609-122">事件</span><span class="sxs-lookup"><span data-stu-id="c3609-122">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
