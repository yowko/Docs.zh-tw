---
title: "'<eventname>' 是個事件，不可直接呼叫"
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: bf900566bdb4ecf8d8961a12b5dd67ba426caf27
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59305594"
---
# <a name="eventname-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="3e2d5-102">'\<事件名稱 >' 是個事件，並不能直接呼叫</span><span class="sxs-lookup"><span data-stu-id="3e2d5-102">'\<eventname>' is an event, and cannot be called directly</span></span>
<span data-ttu-id="3e2d5-103">' <`eventname`>' 是個事件，並因此無法直接呼叫。</span><span class="sxs-lookup"><span data-stu-id="3e2d5-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="3e2d5-104">使用`RaiseEvent`陳述式來引發事件。</span><span class="sxs-lookup"><span data-stu-id="3e2d5-104">Use a `RaiseEvent` statement to raise an event.</span></span>  
  
 <span data-ttu-id="3e2d5-105">程序呼叫指定的程序名稱的事件。</span><span class="sxs-lookup"><span data-stu-id="3e2d5-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="3e2d5-106">事件處理常式是程序，但事件本身發出訊號的裝置，它必須引發並處理。</span><span class="sxs-lookup"><span data-stu-id="3e2d5-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>  
  
 <span data-ttu-id="3e2d5-107">**錯誤 ID:** BC32022</span><span class="sxs-lookup"><span data-stu-id="3e2d5-107">**Error ID:** BC32022</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3e2d5-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="3e2d5-108">To correct this error</span></span>  
  
1. <span data-ttu-id="3e2d5-109">使用`RaiseEvent`陳述式來對事件發出信號，並叫用程序或處理程序。</span><span class="sxs-lookup"><span data-stu-id="3e2d5-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e2d5-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e2d5-110">See also</span></span>

- [<span data-ttu-id="3e2d5-111">RaiseEvent 陳述式</span><span class="sxs-lookup"><span data-stu-id="3e2d5-111">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
