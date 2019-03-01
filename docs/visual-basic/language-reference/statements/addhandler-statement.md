---
title: AddHandler 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: dd57f63b5741822de7b11c1fafe90452a767aa34
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965640"
---
# <a name="addhandler-statement"></a><span data-ttu-id="51498-102">AddHandler 陳述式</span><span class="sxs-lookup"><span data-stu-id="51498-102">AddHandler Statement</span></span>
<span data-ttu-id="51498-103">將事件與事件處理常式在執行階段。</span><span class="sxs-lookup"><span data-stu-id="51498-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51498-104">語法</span><span class="sxs-lookup"><span data-stu-id="51498-104">Syntax</span></span>  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="51498-105">組件</span><span class="sxs-lookup"><span data-stu-id="51498-105">Parts</span></span>  
|||
|---|---|
|<span data-ttu-id="51498-106">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="51498-106">event</span></span>|<span data-ttu-id="51498-107">要處理的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="51498-107">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="51498-108">處理事件的程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="51498-108">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="51498-109">備註</span><span class="sxs-lookup"><span data-stu-id="51498-109">Remarks</span></span>  
 <span data-ttu-id="51498-110">`AddHandler`和`RemoveHandler`陳述式可讓您能夠啟動和停止程式執行期間隨時的事件處理。</span><span class="sxs-lookup"><span data-stu-id="51498-110">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="51498-111">簽章`eventhandler`程序必須符合的事件簽章`event`。</span><span class="sxs-lookup"><span data-stu-id="51498-111">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="51498-112">
  `Handles\` 關鍵字和 `AddHandler\` 陳述式都可以讓您指定由特定程序處理特定事件，但兩者存有差異。</span><span class="sxs-lookup"><span data-stu-id="51498-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="51498-113">
  `AddHandler\` 陳述式會在執行階段將程序連接到事件。</span><span class="sxs-lookup"><span data-stu-id="51498-113">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="51498-114">當定義程序以指定它處理特定事件時，使用 `Handles` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="51498-114">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="51498-115">如需詳細資訊，請參閱 <<c0> [ 處理](../../../visual-basic/language-reference/statements/handles-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="51498-115">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51498-116">自訂事件，如`AddHandler`陳述式會叫用事件的`AddHandler`存取子。</span><span class="sxs-lookup"><span data-stu-id="51498-116">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="51498-117">如需有關自訂事件的詳細資訊，請參閱 < [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="51498-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="51498-118">範例</span><span class="sxs-lookup"><span data-stu-id="51498-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="51498-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51498-119">See also</span></span>
- [<span data-ttu-id="51498-120">RemoveHandler 陳述式</span><span class="sxs-lookup"><span data-stu-id="51498-120">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="51498-121">Handles</span><span class="sxs-lookup"><span data-stu-id="51498-121">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="51498-122">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="51498-122">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="51498-123">事件</span><span class="sxs-lookup"><span data-stu-id="51498-123">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
