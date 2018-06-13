---
title: '&#39;&lt;eventname&gt; &#39;是事件中，而且不能直接呼叫'
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 4d8a7d716d2b7c52d1d027a1e7959d981bb0857e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587328"
---
# <a name="39lteventnamegt39-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="551f3-102">&#39;&lt;eventname&gt; &#39;是事件中，而且不能直接呼叫</span><span class="sxs-lookup"><span data-stu-id="551f3-102">&#39;&lt;eventname&gt;&#39; is an event, and cannot be called directly</span></span>
<span data-ttu-id="551f3-103">' <`eventname`>' 是個事件，並因此不能直接呼叫。</span><span class="sxs-lookup"><span data-stu-id="551f3-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="551f3-104">使用`RaiseEvent`陳述式來引發事件。</span><span class="sxs-lookup"><span data-stu-id="551f3-104">Use a `RaiseEvent` statement to raise an event.</span></span>  
  
 <span data-ttu-id="551f3-105">程序呼叫中指定事件的程序名稱。</span><span class="sxs-lookup"><span data-stu-id="551f3-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="551f3-106">事件處理常式是程序，但事件本身的信號裝置，必須引發和處理。</span><span class="sxs-lookup"><span data-stu-id="551f3-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>  
  
 <span data-ttu-id="551f3-107">**錯誤 ID:** BC32022</span><span class="sxs-lookup"><span data-stu-id="551f3-107">**Error ID:** BC32022</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="551f3-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="551f3-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="551f3-109">使用`RaiseEvent`對事件發出信號和叫用程序或處理程序的陳述式。</span><span class="sxs-lookup"><span data-stu-id="551f3-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="551f3-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="551f3-110">See Also</span></span>  
 [<span data-ttu-id="551f3-111">RaiseEvent 陳述式</span><span class="sxs-lookup"><span data-stu-id="551f3-111">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
