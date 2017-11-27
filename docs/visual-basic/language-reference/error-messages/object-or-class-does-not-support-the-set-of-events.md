---
title: "物件或類別不支援事件的設定"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be4b9140222ef969bfb836fd74f45b8f662360b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a><span data-ttu-id="cb8a9-102">物件或類別不支援事件的設定</span><span class="sxs-lookup"><span data-stu-id="cb8a9-102">Object or class does not support the set of events</span></span>
<span data-ttu-id="cb8a9-103">您嘗試使用`WithEvents`變數無法為指定的事件集的事件來源的元件。</span><span class="sxs-lookup"><span data-stu-id="cb8a9-103">You tried to use a `WithEvents` variable with a component that cannot work as an event source for the specified set of events.</span></span> <span data-ttu-id="cb8a9-104">例如，您要接收到事件的物件，然後再建立另一個物件`Implements`的第一個物件。</span><span class="sxs-lookup"><span data-stu-id="cb8a9-104">For example, you wanted to sink the events of an object, then create another object that `Implements` the first object.</span></span> <span data-ttu-id="cb8a9-105">您可能會認為您可以從實作的物件接收到事件，但這不一定大小寫。</span><span class="sxs-lookup"><span data-stu-id="cb8a9-105">Although you might think you could sink the events from the implemented object, this is not always the case.</span></span> <span data-ttu-id="cb8a9-106">`Implements`只會實作介面方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="cb8a9-106">`Implements` only implements an interface for methods and properties.</span></span> <span data-ttu-id="cb8a9-107">`WithEvents`不支援私用`UserControls`，因為型別資訊所需引發`ObjectEvent`不在執行階段。</span><span class="sxs-lookup"><span data-stu-id="cb8a9-107">`WithEvents` is not supported for private `UserControls`, because the type info needed to raise the `ObjectEvent` is not available at run time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cb8a9-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="cb8a9-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="cb8a9-109">您無法接收事件的來源元件。</span><span class="sxs-lookup"><span data-stu-id="cb8a9-109">You cannot sink events for a component that does not source events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb8a9-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb8a9-110">See Also</span></span>  
 [<span data-ttu-id="cb8a9-111">WithEvents</span><span class="sxs-lookup"><span data-stu-id="cb8a9-111">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)  
 [<span data-ttu-id="cb8a9-112">Implements 陳述式</span><span class="sxs-lookup"><span data-stu-id="cb8a9-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
