---
title: 如何：實作自訂事件存取子 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 759a7a4518a371449723a23669816bbc0fbc0dee
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45677093"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a><span data-ttu-id="bcd77-102">如何：實作自訂事件存取子 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="bcd77-102">How to: Implement Custom Event Accessors (C# Programming Guide)</span></span>
<span data-ttu-id="bcd77-103">事件是一種特殊的多點傳送委派，只能從宣告所在類別內叫用。</span><span class="sxs-lookup"><span data-stu-id="bcd77-103">An event is a special kind of multicast delegate that can only be invoked from within the class that  it is declared in.</span></span> <span data-ttu-id="bcd77-104">在事件引發時，用戶端程式碼透過提供應該叫用的方法參考，來訂閱事件。</span><span class="sxs-lookup"><span data-stu-id="bcd77-104">Client code subscribes to the event by providing a reference to a method that should be invoked when the event is fired.</span></span> <span data-ttu-id="bcd77-105">這些方法會透過類似屬性存取子的事件存取子新增至委派叫用清單，不同之處在於事件存取子名為 `add` 和 `remove`。</span><span class="sxs-lookup"><span data-stu-id="bcd77-105">These methods are added to the delegate's invocation list through event accessors, which resemble property accessors, except that event accessors are named `add` and `remove`.</span></span> <span data-ttu-id="bcd77-106">在大部分情況下，您不必提供自訂事件存取子。</span><span class="sxs-lookup"><span data-stu-id="bcd77-106">In most cases, you do not have to supply custom event accessors.</span></span> <span data-ttu-id="bcd77-107">當程式碼中不提供任何自訂事件存取子時，編譯器會自動新增它們。</span><span class="sxs-lookup"><span data-stu-id="bcd77-107">When no custom event accessors are supplied in your code, the compiler will add them automatically.</span></span> <span data-ttu-id="bcd77-108">不過，在某些情況下，您可能必須提供自訂行為。</span><span class="sxs-lookup"><span data-stu-id="bcd77-108">However, in some cases you may have to provide custom behavior.</span></span> <span data-ttu-id="bcd77-109">[如何：實作介面事件](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)主題示範其中一個這類案例。</span><span class="sxs-lookup"><span data-stu-id="bcd77-109">One such case is shown in the topic [How to:  Implement Interface Events](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcd77-110">範例</span><span class="sxs-lookup"><span data-stu-id="bcd77-110">Example</span></span>  
 <span data-ttu-id="bcd77-111">下例示範如何實作自訂新增和移除事件存取子。</span><span class="sxs-lookup"><span data-stu-id="bcd77-111">The following example shows how to implement custom add and remove event accessors.</span></span> <span data-ttu-id="bcd77-112">雖然您可以替代存取子中的任何程式碼，但建議您先鎖定事件，再新增或移除新的事件處理常式方法。</span><span class="sxs-lookup"><span data-stu-id="bcd77-112">Although you can substitute any code inside the accessors, we recommend that you lock the event before you add or remove a new event handler method.</span></span>  
  
[!code-csharp[IDrawingObject.OnDraw](codesnippet/CSharp/how-to-implement-interface-events_1.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a><span data-ttu-id="bcd77-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="bcd77-113">See Also</span></span>

- [<span data-ttu-id="bcd77-114">事件</span><span class="sxs-lookup"><span data-stu-id="bcd77-114">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
- [<span data-ttu-id="bcd77-115">event</span><span class="sxs-lookup"><span data-stu-id="bcd77-115">event</span></span>](../../../csharp/language-reference/keywords/event.md)