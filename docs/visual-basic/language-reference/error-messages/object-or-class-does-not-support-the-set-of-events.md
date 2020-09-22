---
title: 物件或類別不支援事件的設定
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: e55a5515d88bd2782e31fdea7c07e16c595d43b5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873651"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a><span data-ttu-id="d17f9-102">物件或類別不支援事件的設定</span><span class="sxs-lookup"><span data-stu-id="d17f9-102">Object or class does not support the set of events</span></span>

<span data-ttu-id="d17f9-103">您嘗試使用 `WithEvents` 具有元件的變數，而該元件無法做為指定事件集的事件來源。</span><span class="sxs-lookup"><span data-stu-id="d17f9-103">You tried to use a `WithEvents` variable with a component that cannot work as an event source for the specified set of events.</span></span> <span data-ttu-id="d17f9-104">例如，您想要接收物件的事件，然後建立第一個物件的另一個物件 `Implements` 。</span><span class="sxs-lookup"><span data-stu-id="d17f9-104">For example, you wanted to sink the events of an object, then create another object that `Implements` the first object.</span></span> <span data-ttu-id="d17f9-105">雖然您可能會想要從已執行的物件接收事件，但是這不一定是如此。</span><span class="sxs-lookup"><span data-stu-id="d17f9-105">Although you might think you could sink the events from the implemented object, this is not always the case.</span></span> <span data-ttu-id="d17f9-106">`Implements` 只會針對方法和屬性執行介面。</span><span class="sxs-lookup"><span data-stu-id="d17f9-106">`Implements` only implements an interface for methods and properties.</span></span> <span data-ttu-id="d17f9-107">`WithEvents` 不支援私 `UserControls` 用，因為 `ObjectEvent` 在執行時間無法使用引發所需的型別資訊。</span><span class="sxs-lookup"><span data-stu-id="d17f9-107">`WithEvents` is not supported for private `UserControls`, because the type info needed to raise the `ObjectEvent` is not available at run time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d17f9-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="d17f9-108">To correct this error</span></span>  
  
1. <span data-ttu-id="d17f9-109">您無法接收不是來源事件之元件的事件。</span><span class="sxs-lookup"><span data-stu-id="d17f9-109">You cannot sink events for a component that does not source events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d17f9-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d17f9-110">See also</span></span>

- [<span data-ttu-id="d17f9-111">WithEvents</span><span class="sxs-lookup"><span data-stu-id="d17f9-111">WithEvents</span></span>](../modifiers/withevents.md)
- [<span data-ttu-id="d17f9-112">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="d17f9-112">Implements Statement</span></span>](../statements/implements-statement.md)
