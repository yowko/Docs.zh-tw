---
title: AddHandler 語句（Visual Basic）
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: 95277f532488b0cf56114e5ee94dc3528e3a2e02
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004538"
---
# <a name="addhandler-statement"></a><span data-ttu-id="5bbf5-102">AddHandler 陳述式</span><span class="sxs-lookup"><span data-stu-id="5bbf5-102">AddHandler Statement</span></span>
<span data-ttu-id="5bbf5-103">在執行時間將事件與事件處理常式產生關聯。</span><span class="sxs-lookup"><span data-stu-id="5bbf5-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bbf5-104">語法</span><span class="sxs-lookup"><span data-stu-id="5bbf5-104">Syntax</span></span>  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="5bbf5-105">組件</span><span class="sxs-lookup"><span data-stu-id="5bbf5-105">Parts</span></span>  
|||
|---|---|
|<span data-ttu-id="5bbf5-106">event</span><span class="sxs-lookup"><span data-stu-id="5bbf5-106">event</span></span>|<span data-ttu-id="5bbf5-107">要處理的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="5bbf5-107">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="5bbf5-108">處理事件的程式名稱。</span><span class="sxs-lookup"><span data-stu-id="5bbf5-108">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="5bbf5-109">備註</span><span class="sxs-lookup"><span data-stu-id="5bbf5-109">Remarks</span></span>  
 <span data-ttu-id="5bbf5-110">@No__t-0 和 @no__t 1 語句可讓您在程式執行期間的任何時間啟動和停止事件處理。</span><span class="sxs-lookup"><span data-stu-id="5bbf5-110">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="5bbf5-111">@No__t 0 程式的簽章必須符合事件 `event` 的簽章。</span><span class="sxs-lookup"><span data-stu-id="5bbf5-111">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="5bbf5-112">`Handles` 關鍵字和 `AddHandler` 陳述式都可以讓您指定由特定程序處理特定事件，但兩者存有差異。</span><span class="sxs-lookup"><span data-stu-id="5bbf5-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="5bbf5-113">`AddHandler` 陳述式會在執行階段將程序連接到事件。</span><span class="sxs-lookup"><span data-stu-id="5bbf5-113">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="5bbf5-114">當定義程序以指定它處理特定事件時，使用 `Handles` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="5bbf5-114">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="5bbf5-115">如需詳細資訊，請參閱[控制碼](../../../visual-basic/language-reference/statements/handles-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="5bbf5-115">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5bbf5-116">若為自訂事件，`AddHandler` 語句會叫用事件的 @no__t 1 存取子。</span><span class="sxs-lookup"><span data-stu-id="5bbf5-116">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="5bbf5-117">如需自訂事件的詳細資訊，請參閱[Event 語句](../../../visual-basic/language-reference/statements/event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="5bbf5-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bbf5-118">範例</span><span class="sxs-lookup"><span data-stu-id="5bbf5-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="5bbf5-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bbf5-119">See also</span></span>

- [<span data-ttu-id="5bbf5-120">RemoveHandler 陳述式</span><span class="sxs-lookup"><span data-stu-id="5bbf5-120">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="5bbf5-121">Handles</span><span class="sxs-lookup"><span data-stu-id="5bbf5-121">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="5bbf5-122">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="5bbf5-122">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="5bbf5-123">事件</span><span class="sxs-lookup"><span data-stu-id="5bbf5-123">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
