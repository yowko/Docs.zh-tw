---
title: '如何執行自訂事件存取子-c # 程式設計手冊'
description: 瞭解如何執行自訂事件存取子。 查看程式碼範例，並查看其他可用的資源。
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 4094aa1fedbceb68790b484608b3ea0ebc1e5cf6
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302135"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a><span data-ttu-id="025d4-104">如何執行自訂事件存取子（c # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="025d4-104">How to implement custom event accessors (C# Programming Guide)</span></span>
<span data-ttu-id="025d4-105">事件是一種特殊的多點傳送委派，只能從宣告所在類別內叫用。</span><span class="sxs-lookup"><span data-stu-id="025d4-105">An event is a special kind of multicast delegate that can only be invoked from within the class that  it is declared in.</span></span> <span data-ttu-id="025d4-106">在事件引發時，用戶端程式碼透過提供應該叫用的方法參考，來訂閱事件。</span><span class="sxs-lookup"><span data-stu-id="025d4-106">Client code subscribes to the event by providing a reference to a method that should be invoked when the event is fired.</span></span> <span data-ttu-id="025d4-107">這些方法會透過類似屬性存取子的事件存取子新增至委派叫用清單，不同之處在於事件存取子名為 `add` 和 `remove`。</span><span class="sxs-lookup"><span data-stu-id="025d4-107">These methods are added to the delegate's invocation list through event accessors, which resemble property accessors, except that event accessors are named `add` and `remove`.</span></span> <span data-ttu-id="025d4-108">在大部分情況下，您不必提供自訂事件存取子。</span><span class="sxs-lookup"><span data-stu-id="025d4-108">In most cases, you do not have to supply custom event accessors.</span></span> <span data-ttu-id="025d4-109">當程式碼中不提供任何自訂事件存取子時，編譯器會自動新增它們。</span><span class="sxs-lookup"><span data-stu-id="025d4-109">When no custom event accessors are supplied in your code, the compiler will add them automatically.</span></span> <span data-ttu-id="025d4-110">不過，在某些情況下，您可能必須提供自訂行為。</span><span class="sxs-lookup"><span data-stu-id="025d4-110">However, in some cases you may have to provide custom behavior.</span></span> <span data-ttu-id="025d4-111">其中一個這類案例如[如何執行介面事件](./how-to-implement-interface-events.md)主題中所示。</span><span class="sxs-lookup"><span data-stu-id="025d4-111">One such case is shown in the topic [How to implement interface events](./how-to-implement-interface-events.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="025d4-112">範例</span><span class="sxs-lookup"><span data-stu-id="025d4-112">Example</span></span>  
 <span data-ttu-id="025d4-113">下例示範如何實作自訂新增和移除事件存取子。</span><span class="sxs-lookup"><span data-stu-id="025d4-113">The following example shows how to implement custom add and remove event accessors.</span></span> <span data-ttu-id="025d4-114">雖然您可以替代存取子中的任何程式碼，但建議您先鎖定事件，再新增或移除新的事件處理常式方法。</span><span class="sxs-lookup"><span data-stu-id="025d4-114">Although you can substitute any code inside the accessors, we recommend that you lock the event before you add or remove a new event handler method.</span></span>  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a><span data-ttu-id="025d4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="025d4-115">See also</span></span>

- [<span data-ttu-id="025d4-116">事件</span><span class="sxs-lookup"><span data-stu-id="025d4-116">Events</span></span>](./index.md)
- [<span data-ttu-id="025d4-117">event</span><span class="sxs-lookup"><span data-stu-id="025d4-117">event</span></span>](../../language-reference/keywords/event.md)
