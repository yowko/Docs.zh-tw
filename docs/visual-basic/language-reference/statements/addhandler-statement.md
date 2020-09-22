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
ms.openlocfilehash: 79dbe174209e91f13f5b43e8cdeb0b42edc4d163
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866714"
---
# <a name="addhandler-statement"></a><span data-ttu-id="82bcb-102">AddHandler 陳述式</span><span class="sxs-lookup"><span data-stu-id="82bcb-102">AddHandler Statement</span></span>

<span data-ttu-id="82bcb-103">在執行時間將事件與事件處理常式產生關聯。</span><span class="sxs-lookup"><span data-stu-id="82bcb-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82bcb-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="82bcb-104">Syntax</span></span>  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="82bcb-105">組件</span><span class="sxs-lookup"><span data-stu-id="82bcb-105">Parts</span></span>  

|||
|---|---|
|<span data-ttu-id="82bcb-106">event</span><span class="sxs-lookup"><span data-stu-id="82bcb-106">event</span></span>|<span data-ttu-id="82bcb-107">要處理的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="82bcb-107">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="82bcb-108">處理事件的程式名稱。</span><span class="sxs-lookup"><span data-stu-id="82bcb-108">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="82bcb-109">備註</span><span class="sxs-lookup"><span data-stu-id="82bcb-109">Remarks</span></span>  

 <span data-ttu-id="82bcb-110">`AddHandler`和 `RemoveHandler` 語句可讓您在程式執行期間隨時啟動和停止事件處理。</span><span class="sxs-lookup"><span data-stu-id="82bcb-110">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="82bcb-111">程式的簽章 `eventhandler` 必須與事件的簽章相符 `event` 。</span><span class="sxs-lookup"><span data-stu-id="82bcb-111">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="82bcb-112">`Handles` 關鍵字和 `AddHandler` 陳述式都可以讓您指定由特定程序處理特定事件，但兩者存有差異。</span><span class="sxs-lookup"><span data-stu-id="82bcb-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="82bcb-113">`AddHandler` 陳述式會在執行階段將程序連接到事件。</span><span class="sxs-lookup"><span data-stu-id="82bcb-113">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="82bcb-114">當定義程序以指定它處理特定事件時，使用 `Handles` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="82bcb-114">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="82bcb-115">如需詳細資訊，請參閱 [控制碼](handles-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="82bcb-115">For more information, see [Handles](handles-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82bcb-116">針對自訂事件，語句會叫用 `AddHandler` 事件的 `AddHandler` 存取子。</span><span class="sxs-lookup"><span data-stu-id="82bcb-116">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="82bcb-117">如需有關自訂事件的詳細資訊，請參閱 [事件語句](event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="82bcb-117">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="82bcb-118">範例</span><span class="sxs-lookup"><span data-stu-id="82bcb-118">Example</span></span>  

 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="82bcb-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82bcb-119">See also</span></span>

- [<span data-ttu-id="82bcb-120">RemoveHandler 陳述式</span><span class="sxs-lookup"><span data-stu-id="82bcb-120">RemoveHandler Statement</span></span>](removehandler-statement.md)
- [<span data-ttu-id="82bcb-121">處理</span><span class="sxs-lookup"><span data-stu-id="82bcb-121">Handles</span></span>](handles-clause.md)
- [<span data-ttu-id="82bcb-122">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="82bcb-122">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="82bcb-123">事件</span><span class="sxs-lookup"><span data-stu-id="82bcb-123">Events</span></span>](../../programming-guide/language-features/events/index.md)
