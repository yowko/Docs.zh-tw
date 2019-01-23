---
title: RemoveHandler 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 27cdd2753507c6fc4d5c5041607e2ccb425b81b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560616"
---
# <a name="removehandler-statement"></a><span data-ttu-id="4cd11-102">RemoveHandler 陳述式</span><span class="sxs-lookup"><span data-stu-id="4cd11-102">RemoveHandler Statement</span></span>
<span data-ttu-id="4cd11-103">移除的事件與事件處理常式之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="4cd11-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cd11-104">語法</span><span class="sxs-lookup"><span data-stu-id="4cd11-104">Syntax</span></span>  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="4cd11-105">組件</span><span class="sxs-lookup"><span data-stu-id="4cd11-105">Parts</span></span>  
  
|<span data-ttu-id="4cd11-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="4cd11-106">Term</span></span>|<span data-ttu-id="4cd11-107">定義</span><span class="sxs-lookup"><span data-stu-id="4cd11-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="4cd11-108">所處理的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="4cd11-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="4cd11-109">目前正在處理事件的程序名稱。</span><span class="sxs-lookup"><span data-stu-id="4cd11-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4cd11-110">備註</span><span class="sxs-lookup"><span data-stu-id="4cd11-110">Remarks</span></span>  
 <span data-ttu-id="4cd11-111">`AddHandler`和`RemoveHandler`陳述式可讓您能夠啟動和停止程式執行期間隨時特定事件的事件處理。</span><span class="sxs-lookup"><span data-stu-id="4cd11-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4cd11-112">自訂事件，如`RemoveHandler`陳述式會叫用事件的`RemoveHandler`存取子。</span><span class="sxs-lookup"><span data-stu-id="4cd11-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="4cd11-113">如需有關自訂事件的詳細資訊，請參閱 < [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="4cd11-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cd11-114">範例</span><span class="sxs-lookup"><span data-stu-id="4cd11-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4cd11-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cd11-115">See also</span></span>
- [<span data-ttu-id="4cd11-116">AddHandler 陳述式</span><span class="sxs-lookup"><span data-stu-id="4cd11-116">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="4cd11-117">Handles</span><span class="sxs-lookup"><span data-stu-id="4cd11-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="4cd11-118">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="4cd11-118">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="4cd11-119">事件</span><span class="sxs-lookup"><span data-stu-id="4cd11-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
