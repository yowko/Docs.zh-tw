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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803302"
---
# <a name="eventname-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="2dad7-102">'\<事件名稱 >' 是個事件，並不能直接呼叫</span><span class="sxs-lookup"><span data-stu-id="2dad7-102">'\<eventname>' is an event, and cannot be called directly</span></span>
<span data-ttu-id="2dad7-103">' <`eventname`>' 是個事件，並因此無法直接呼叫。</span><span class="sxs-lookup"><span data-stu-id="2dad7-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="2dad7-104">使用`RaiseEvent`陳述式來引發事件。</span><span class="sxs-lookup"><span data-stu-id="2dad7-104">Use a `RaiseEvent` statement to raise an event.</span></span>  
  
 <span data-ttu-id="2dad7-105">程序呼叫指定的程序名稱的事件。</span><span class="sxs-lookup"><span data-stu-id="2dad7-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="2dad7-106">事件處理常式是程序，但事件本身發出訊號的裝置，它必須引發並處理。</span><span class="sxs-lookup"><span data-stu-id="2dad7-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>  
  
 <span data-ttu-id="2dad7-107">**錯誤 ID:** BC32022</span><span class="sxs-lookup"><span data-stu-id="2dad7-107">**Error ID:** BC32022</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2dad7-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="2dad7-108">To correct this error</span></span>  
  
1. <span data-ttu-id="2dad7-109">使用`RaiseEvent`陳述式來對事件發出信號，並叫用程序或處理程序。</span><span class="sxs-lookup"><span data-stu-id="2dad7-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dad7-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2dad7-110">See also</span></span>

- [<span data-ttu-id="2dad7-111">RaiseEvent 陳述式</span><span class="sxs-lookup"><span data-stu-id="2dad7-111">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
