---
title: 物件或類別不支援事件的設定
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: bc75e031c2d05bea3aa64774a9d3817756e51e8b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409357"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a><span data-ttu-id="daeec-102">物件或類別不支援事件的設定</span><span class="sxs-lookup"><span data-stu-id="daeec-102">Object or class does not support the set of events</span></span>
<span data-ttu-id="daeec-103">您嘗試使用的 `WithEvents` 變數與元件無法做為指定事件集的事件來源。</span><span class="sxs-lookup"><span data-stu-id="daeec-103">You tried to use a `WithEvents` variable with a component that cannot work as an event source for the specified set of events.</span></span> <span data-ttu-id="daeec-104">例如，您想要接收物件的事件，然後建立第一個物件的另一個物件 `Implements` 。</span><span class="sxs-lookup"><span data-stu-id="daeec-104">For example, you wanted to sink the events of an object, then create another object that `Implements` the first object.</span></span> <span data-ttu-id="daeec-105">雖然您可能會認為您可以從實作為物件接收事件，但這不一定都是如此。</span><span class="sxs-lookup"><span data-stu-id="daeec-105">Although you might think you could sink the events from the implemented object, this is not always the case.</span></span> <span data-ttu-id="daeec-106">`Implements`只會實作為方法和屬性的介面。</span><span class="sxs-lookup"><span data-stu-id="daeec-106">`Implements` only implements an interface for methods and properties.</span></span> <span data-ttu-id="daeec-107">`WithEvents`不支援私 `UserControls` 用，因為 `ObjectEvent` 在執行時間無法使用引發所需的類型資訊。</span><span class="sxs-lookup"><span data-stu-id="daeec-107">`WithEvents` is not supported for private `UserControls`, because the type info needed to raise the `ObjectEvent` is not available at run time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="daeec-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="daeec-108">To correct this error</span></span>  
  
1. <span data-ttu-id="daeec-109">您無法接收不是來源事件之元件的事件。</span><span class="sxs-lookup"><span data-stu-id="daeec-109">You cannot sink events for a component that does not source events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daeec-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="daeec-110">See also</span></span>

- [<span data-ttu-id="daeec-111">WithEvents</span><span class="sxs-lookup"><span data-stu-id="daeec-111">WithEvents</span></span>](../modifiers/withevents.md)
- [<span data-ttu-id="daeec-112">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="daeec-112">Implements Statement</span></span>](../statements/implements-statement.md)
