---
title: "'<eventname>' 是個事件，不可直接呼叫"
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 3366bc215a45cd7de9dc2de285758a78144df509
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874321"
---
# <a name="eventname-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="18c01-102">'\<eventname>' 是個事件，不可直接呼叫</span><span class="sxs-lookup"><span data-stu-id="18c01-102">'\<eventname>' is an event, and cannot be called directly</span></span>

<span data-ttu-id="18c01-103">「<`eventname`>」是事件，所以無法直接呼叫。</span><span class="sxs-lookup"><span data-stu-id="18c01-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="18c01-104">使用 `RaiseEvent` 語句來引發事件。</span><span class="sxs-lookup"><span data-stu-id="18c01-104">Use a `RaiseEvent` statement to raise an event.</span></span>  
  
 <span data-ttu-id="18c01-105">程序呼叫會指定程式名稱的事件。</span><span class="sxs-lookup"><span data-stu-id="18c01-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="18c01-106">事件處理常式是一種程式，但事件本身是必須引發和處理的信號裝置。</span><span class="sxs-lookup"><span data-stu-id="18c01-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>  
  
 <span data-ttu-id="18c01-107">**錯誤識別碼：** BC32022</span><span class="sxs-lookup"><span data-stu-id="18c01-107">**Error ID:** BC32022</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="18c01-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="18c01-108">To correct this error</span></span>  
  
1. <span data-ttu-id="18c01-109">使用 `RaiseEvent` 語句來發出事件的信號，並叫用處理它的程式或程式。</span><span class="sxs-lookup"><span data-stu-id="18c01-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18c01-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18c01-110">See also</span></span>

- [<span data-ttu-id="18c01-111">RaiseEvent 陳述式</span><span class="sxs-lookup"><span data-stu-id="18c01-111">RaiseEvent Statement</span></span>](../statements/raiseevent-statement.md)
