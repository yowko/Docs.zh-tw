---
title: "RemoveHandler 陳述式 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
dev_langs:
- VB
helpviewer_keywords:
- RemoveHandler keyword
- RemoveHandler statement
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
caps.latest.revision: 14
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
ms.openlocfilehash: 6e614a1dce4894dcd18509854f3cae149665cbf0
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="removehandler-statement"></a><span data-ttu-id="c4c5d-102">RemoveHandler 陳述式</span><span class="sxs-lookup"><span data-stu-id="c4c5d-102">RemoveHandler Statement</span></span>
<span data-ttu-id="c4c5d-103">移除的事件與事件處理常式之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="c4c5d-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4c5d-104">語法</span><span class="sxs-lookup"><span data-stu-id="c4c5d-104">Syntax</span></span>  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="c4c5d-105">組件</span><span class="sxs-lookup"><span data-stu-id="c4c5d-105">Parts</span></span>  
  
|<span data-ttu-id="c4c5d-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="c4c5d-106">Term</span></span>|<span data-ttu-id="c4c5d-107">定義</span><span class="sxs-lookup"><span data-stu-id="c4c5d-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="c4c5d-108">要處理事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="c4c5d-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="c4c5d-109">目前正在處理的事件程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="c4c5d-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4c5d-110">備註</span><span class="sxs-lookup"><span data-stu-id="c4c5d-110">Remarks</span></span>  
 <span data-ttu-id="c4c5d-111">`AddHandler`和`RemoveHandler`陳述式可讓您能夠啟動和停止程式執行期間的特定事件的事件處理。</span><span class="sxs-lookup"><span data-stu-id="c4c5d-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4c5d-112">自訂事件，`RemoveHandler`陳述式會叫用此事件`RemoveHandler`存取子。</span><span class="sxs-lookup"><span data-stu-id="c4c5d-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="c4c5d-113">如需自訂事件的詳細資訊，請參閱[Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="c4c5d-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4c5d-114">範例</span><span class="sxs-lookup"><span data-stu-id="c4c5d-114">Example</span></span>  
 <span data-ttu-id="c4c5d-115">[!code-vb[VbVbalrEvents #&17;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c4c5d-115">[!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4c5d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4c5d-116">See Also</span></span>  
 <span data-ttu-id="c4c5d-117">[AddHandler 陳述式](../../../visual-basic/language-reference/statements/addhandler-statement.md) </span><span class="sxs-lookup"><span data-stu-id="c4c5d-117">[AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md) </span></span>  
<span data-ttu-id="c4c5d-118"> [控制代碼](../../../visual-basic/language-reference/statements/handles-clause.md) </span><span class="sxs-lookup"><span data-stu-id="c4c5d-118"> [Handles](../../../visual-basic/language-reference/statements/handles-clause.md) </span></span>  
<span data-ttu-id="c4c5d-119"> [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md) </span><span class="sxs-lookup"><span data-stu-id="c4c5d-119"> [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) </span></span>  
<span data-ttu-id="c4c5d-120"> [事件](../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="c4c5d-120"> [Events](../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>
