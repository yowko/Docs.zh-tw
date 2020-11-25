---
title: 如何：使用事件屬性處理多個事件
description: 瞭解如何使用事件屬性處理多個事件。 定義委派集合、事件索引鍵、& 事件屬性。 執行 add & remove 存取子方法。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- event properties [.NET]
- multiple events [.NET]
- event handling [.NET], with multiple events
- events [.NET], multiple
ms.assetid: 30047cba-e2fd-41c6-b9ca-2ad7a49003db
ms.openlocfilehash: 7484ad06e80e6ce131f48431fbdd1e812ce0bfa0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734318"
---
# <a name="how-to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="cc03b-105">如何：使用事件屬性處理多個事件</span><span class="sxs-lookup"><span data-stu-id="cc03b-105">How to: Handle Multiple Events Using Event Properties</span></span>

<span data-ttu-id="cc03b-106">為了要使用事件屬性，您會在引發事件的類別中定義事件屬性，然後在處理事件的類別中設定事件屬性的委派。</span><span class="sxs-lookup"><span data-stu-id="cc03b-106">To use event properties, you define the event properties in the class that raises the events, and then set the delegates for the event properties in classes that handle the events.</span></span> <span data-ttu-id="cc03b-107">若要在類別中實作多個事件屬性，該類別內部必須儲存及維護為每個事件所定義的委派。</span><span class="sxs-lookup"><span data-stu-id="cc03b-107">To implement multiple event properties in a class, the class must internally store and maintain the delegate defined for each event.</span></span> <span data-ttu-id="cc03b-108">型的方法是實作以事件索引鍵編製索引的委派集合。</span><span class="sxs-lookup"><span data-stu-id="cc03b-108">A typical approach is to implement a delegate collection that is indexed by an event key.</span></span>  
  
 <span data-ttu-id="cc03b-109">若要儲存每個事件的委派，您可以使用 <xref:System.ComponentModel.EventHandlerList> 類別，或實作您自己的集合。</span><span class="sxs-lookup"><span data-stu-id="cc03b-109">To store the delegates for each event, you can use the <xref:System.ComponentModel.EventHandlerList> class, or implement your own collection.</span></span> <span data-ttu-id="cc03b-110">集合類別必須提供方法，根據事件索引鍵來設定、存取和擷取事件處理常式委派。</span><span class="sxs-lookup"><span data-stu-id="cc03b-110">The collection class must provide methods for setting, accessing, and retrieving the event handler delegate based on the event key.</span></span> <span data-ttu-id="cc03b-111">例如，您可以使用 <xref:System.Collections.Hashtable> 類別，或是從 <xref:System.Collections.DictionaryBase> 類別衍生自訂類別。</span><span class="sxs-lookup"><span data-stu-id="cc03b-111">For example, you could use a <xref:System.Collections.Hashtable> class, or derive a custom class from the <xref:System.Collections.DictionaryBase> class.</span></span> <span data-ttu-id="cc03b-112">委派集合的實作詳細資料不需要公開至類別之外。</span><span class="sxs-lookup"><span data-stu-id="cc03b-112">The implementation details of the delegate collection do not need to be exposed outside your class.</span></span>  
  
 <span data-ttu-id="cc03b-113">類別內的每個事件屬性，都會定義一個 add 存取子方法和一個 remove 存取子方法。</span><span class="sxs-lookup"><span data-stu-id="cc03b-113">Each event property within the class defines an add accessor method and a remove accessor method.</span></span> <span data-ttu-id="cc03b-114">事件屬性的 add 存取子會在委派集合中加入輸入委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="cc03b-114">The add accessor for an event property adds the input delegate instance to the delegate collection.</span></span> <span data-ttu-id="cc03b-115">事件屬性的 remove 存取子會從委派集合中移除輸入委派執行個體。 </span><span class="sxs-lookup"><span data-stu-id="cc03b-115">The remove accessor for an event property removes the input delegate instance from the delegate collection.</span></span> <span data-ttu-id="cc03b-116">事件屬性存取子會使用事件屬性的預先定義索引鍵，從委派集合新增和移除執行個體。</span><span class="sxs-lookup"><span data-stu-id="cc03b-116">The event property accessors use the predefined key for the event property to add and remove instances from the delegate collection.</span></span>  
  
### <a name="to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="cc03b-117">使用事件屬性處理多個事件</span><span class="sxs-lookup"><span data-stu-id="cc03b-117">To handle multiple events using event properties</span></span>  
  
1. <span data-ttu-id="cc03b-118">定義在類別中引發事件的委派集合。</span><span class="sxs-lookup"><span data-stu-id="cc03b-118">Define a delegate collection within the class that raises the events.</span></span>  
  
2. <span data-ttu-id="cc03b-119">定義每個事件的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="cc03b-119">Define a key for each event.</span></span>  
  
3. <span data-ttu-id="cc03b-120">在引發事件的類別中定義事件屬性。</span><span class="sxs-lookup"><span data-stu-id="cc03b-120">Define the event properties in the class that raises the events.</span></span>  
  
4. <span data-ttu-id="cc03b-121">使用委派集合實作事件屬性的 add 和 remove 存取子方法。</span><span class="sxs-lookup"><span data-stu-id="cc03b-121">Use the delegate collection to implement the add and remove accessor methods for the event properties.</span></span>  
  
5. <span data-ttu-id="cc03b-122">使用公用事件屬性，在處理事件的類別中新增和移除事件處理常式委派。</span><span class="sxs-lookup"><span data-stu-id="cc03b-122">Use the public event properties to add and remove event handler delegates in the classes that handle the events.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc03b-123">範例</span><span class="sxs-lookup"><span data-stu-id="cc03b-123">Example</span></span>  

 <span data-ttu-id="cc03b-124">下列 C# 範例會使用 <xref:System.ComponentModel.EventHandlerList> 實作事件屬性 `MouseDown` 及 `MouseUp`，以儲存每個事件的委派。</span><span class="sxs-lookup"><span data-stu-id="cc03b-124">The following C# example implements the event properties `MouseDown` and `MouseUp`, using an <xref:System.ComponentModel.EventHandlerList> to store each event's delegate.</span></span> <span data-ttu-id="cc03b-125">事件屬性建構的關鍵字會以粗體顯示。</span><span class="sxs-lookup"><span data-stu-id="cc03b-125">The keywords of the event property constructs are in bold type.</span></span>  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="cc03b-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc03b-126">See also</span></span>

- <xref:System.ComponentModel.EventHandlerList?displayProperty=nameWithType>
- [<span data-ttu-id="cc03b-127">事件</span><span class="sxs-lookup"><span data-stu-id="cc03b-127">Events</span></span>](index.md)
- <xref:System.Web.UI.Control.Events%2A?displayProperty=nameWithType>
- [<span data-ttu-id="cc03b-128">如何：宣告自訂事件以節省記憶體</span><span class="sxs-lookup"><span data-stu-id="cc03b-128">How to: Declare Custom Events To Conserve Memory</span></span>](../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
