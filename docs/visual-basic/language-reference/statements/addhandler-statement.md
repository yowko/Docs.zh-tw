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
ms.openlocfilehash: db8131dc82aed40e725c9375efef274fb6917d41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603648"
---
# <a name="addhandler-statement"></a><span data-ttu-id="e86f7-102">AddHandler 陳述式</span><span class="sxs-lookup"><span data-stu-id="e86f7-102">AddHandler Statement</span></span>
<span data-ttu-id="e86f7-103">將事件與事件處理常式在執行階段。</span><span class="sxs-lookup"><span data-stu-id="e86f7-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e86f7-104">語法</span><span class="sxs-lookup"><span data-stu-id="e86f7-104">Syntax</span></span>  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="e86f7-105">組件</span><span class="sxs-lookup"><span data-stu-id="e86f7-105">Parts</span></span>  
 `event`  
 <span data-ttu-id="e86f7-106">要處理的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="e86f7-106">The name of the event to handle.</span></span>  
  
 `eventhandler`  
 <span data-ttu-id="e86f7-107">處理事件的程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="e86f7-107">The name of a procedure that handles the event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e86f7-108">備註</span><span class="sxs-lookup"><span data-stu-id="e86f7-108">Remarks</span></span>  
 <span data-ttu-id="e86f7-109">`AddHandler`和`RemoveHandler`陳述式可讓您能夠啟動和停止程式執行期間的事件處理。</span><span class="sxs-lookup"><span data-stu-id="e86f7-109">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="e86f7-110">簽章`eventhandler`程序必須符合事件簽章`event`。</span><span class="sxs-lookup"><span data-stu-id="e86f7-110">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="e86f7-111">`Handles` 關鍵字和 `AddHandler` 陳述式都可以讓您指定由特定程序處理特定事件，但兩者存有差異。</span><span class="sxs-lookup"><span data-stu-id="e86f7-111">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="e86f7-112">`AddHandler` 陳述式會在執行階段將程序連接到事件。</span><span class="sxs-lookup"><span data-stu-id="e86f7-112">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="e86f7-113">當定義程序以指定它處理特定事件時，使用 `Handles` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="e86f7-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="e86f7-114">如需詳細資訊，請參閱[處理](../../../visual-basic/language-reference/statements/handles-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="e86f7-114">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e86f7-115">對於自訂事件，`AddHandler`陳述式會叫用此事件`AddHandler`存取子。</span><span class="sxs-lookup"><span data-stu-id="e86f7-115">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="e86f7-116">如需有關自訂事件的詳細資訊，請參閱[Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="e86f7-116">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e86f7-117">範例</span><span class="sxs-lookup"><span data-stu-id="e86f7-117">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e86f7-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e86f7-118">See Also</span></span>  
 [<span data-ttu-id="e86f7-119">RemoveHandler 陳述式</span><span class="sxs-lookup"><span data-stu-id="e86f7-119">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [<span data-ttu-id="e86f7-120">Handles</span><span class="sxs-lookup"><span data-stu-id="e86f7-120">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="e86f7-121">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="e86f7-121">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="e86f7-122">事件</span><span class="sxs-lookup"><span data-stu-id="e86f7-122">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
