---
title: RemoveHandler 語句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 3a839a7d05d05066f6c0f774a683c8fc83c19643
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957730"
---
# <a name="removehandler-statement"></a><span data-ttu-id="6fd19-102">RemoveHandler 陳述式</span><span class="sxs-lookup"><span data-stu-id="6fd19-102">RemoveHandler Statement</span></span>
<span data-ttu-id="6fd19-103">移除事件與事件處理常式之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="6fd19-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fd19-104">語法</span><span class="sxs-lookup"><span data-stu-id="6fd19-104">Syntax</span></span>  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="6fd19-105">組件</span><span class="sxs-lookup"><span data-stu-id="6fd19-105">Parts</span></span>  
  
|<span data-ttu-id="6fd19-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="6fd19-106">Term</span></span>|<span data-ttu-id="6fd19-107">定義</span><span class="sxs-lookup"><span data-stu-id="6fd19-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="6fd19-108">正在處理的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="6fd19-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="6fd19-109">目前處理事件的程式名稱。</span><span class="sxs-lookup"><span data-stu-id="6fd19-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fd19-110">備註</span><span class="sxs-lookup"><span data-stu-id="6fd19-110">Remarks</span></span>  
 <span data-ttu-id="6fd19-111">`AddHandler` 和`RemoveHandler`語句可讓您在程式執行期間的任何時間, 啟動和停止特定事件的事件處理。</span><span class="sxs-lookup"><span data-stu-id="6fd19-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6fd19-112">若為自訂事件`RemoveHandler` , 語句會叫用`RemoveHandler`事件的存取子。</span><span class="sxs-lookup"><span data-stu-id="6fd19-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="6fd19-113">如需自訂事件的詳細資訊, 請參閱[Event 語句](../../../visual-basic/language-reference/statements/event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="6fd19-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fd19-114">範例</span><span class="sxs-lookup"><span data-stu-id="6fd19-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="6fd19-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6fd19-115">See also</span></span>

- [<span data-ttu-id="6fd19-116">AddHandler 陳述式</span><span class="sxs-lookup"><span data-stu-id="6fd19-116">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="6fd19-117">Handles</span><span class="sxs-lookup"><span data-stu-id="6fd19-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="6fd19-118">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="6fd19-118">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="6fd19-119">事件</span><span class="sxs-lookup"><span data-stu-id="6fd19-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
