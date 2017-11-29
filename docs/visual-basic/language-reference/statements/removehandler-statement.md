---
title: "RemoveHandler 陳述式"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 82d130c6536df7d72977a028333293b4e0ee89de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="removehandler-statement"></a><span data-ttu-id="26cb2-102">RemoveHandler 陳述式</span><span class="sxs-lookup"><span data-stu-id="26cb2-102">RemoveHandler Statement</span></span>
<span data-ttu-id="26cb2-103">移除事件和事件處理常式之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="26cb2-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26cb2-104">語法</span><span class="sxs-lookup"><span data-stu-id="26cb2-104">Syntax</span></span>  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="26cb2-105">組件</span><span class="sxs-lookup"><span data-stu-id="26cb2-105">Parts</span></span>  
  
|<span data-ttu-id="26cb2-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="26cb2-106">Term</span></span>|<span data-ttu-id="26cb2-107">定義</span><span class="sxs-lookup"><span data-stu-id="26cb2-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="26cb2-108">要處理事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="26cb2-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="26cb2-109">目前正在處理事件的程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="26cb2-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26cb2-110">備註</span><span class="sxs-lookup"><span data-stu-id="26cb2-110">Remarks</span></span>  
 <span data-ttu-id="26cb2-111">`AddHandler`和`RemoveHandler`陳述式可讓您能夠啟動和停止程式執行期間，隨時特定事件的事件處理。</span><span class="sxs-lookup"><span data-stu-id="26cb2-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26cb2-112">對於自訂事件，`RemoveHandler`陳述式會叫用此事件`RemoveHandler`存取子。</span><span class="sxs-lookup"><span data-stu-id="26cb2-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="26cb2-113">如需有關自訂事件的詳細資訊，請參閱[Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="26cb2-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="26cb2-114">範例</span><span class="sxs-lookup"><span data-stu-id="26cb2-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="26cb2-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26cb2-115">See Also</span></span>  
 [<span data-ttu-id="26cb2-116">AddHandler 陳述式</span><span class="sxs-lookup"><span data-stu-id="26cb2-116">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [<span data-ttu-id="26cb2-117">Handles</span><span class="sxs-lookup"><span data-stu-id="26cb2-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="26cb2-118">Event 陳述式</span><span class="sxs-lookup"><span data-stu-id="26cb2-118">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="26cb2-119">事件</span><span class="sxs-lookup"><span data-stu-id="26cb2-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
