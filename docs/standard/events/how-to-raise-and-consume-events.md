---
title: 如何：引發和使用事件
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], raising
- raising events
- events [.NET Framework], samples
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa933e0fc589d0dbfec741e9db7fb11222cfdf38
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44193213"
---
# <a name="how-to-raise-and-consume-events"></a><span data-ttu-id="1dcc1-102">如何：引發和使用事件</span><span class="sxs-lookup"><span data-stu-id="1dcc1-102">How to: Raise and Consume Events</span></span>
<span data-ttu-id="1dcc1-103">本主題中的範例將示範如何使用事件。</span><span class="sxs-lookup"><span data-stu-id="1dcc1-103">The examples in this topic show how to work with events.</span></span> <span data-ttu-id="1dcc1-104">包括 <xref:System.EventHandler> 委派、<xref:System.EventHandler%601> 委派和自訂委派的範例，用以說明包含和不包含資料的事件。</span><span class="sxs-lookup"><span data-stu-id="1dcc1-104">They include examples of the <xref:System.EventHandler> delegate, the <xref:System.EventHandler%601> delegate, and a custom delegate, to illustrate events with and without data.</span></span>  
  
 <span data-ttu-id="1dcc1-105">範例將使用[事件](../../../docs/standard/events/index.md)一文中所述的概念。</span><span class="sxs-lookup"><span data-stu-id="1dcc1-105">The examples use concepts described in the [Events](../../../docs/standard/events/index.md) article.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1dcc1-106">範例</span><span class="sxs-lookup"><span data-stu-id="1dcc1-106">Example</span></span>  
 <span data-ttu-id="1dcc1-107">第一個範例將示範如何引發和使用沒有資料的事件。</span><span class="sxs-lookup"><span data-stu-id="1dcc1-107">The first example shows how to raise and consume an event that doesn't have data.</span></span> <span data-ttu-id="1dcc1-108">它包含名為 `Counter` 的類別，該類別中包含名為 `ThresholdReached` 的事件。</span><span class="sxs-lookup"><span data-stu-id="1dcc1-108">It contains a class named `Counter` that has an event named `ThresholdReached`.</span></span> <span data-ttu-id="1dcc1-109">當計數器的值等於或超過臨界值時，就會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="1dcc1-109">This event is raised when a counter value equals or exceeds a threshold value.</span></span> <span data-ttu-id="1dcc1-110">由於未提供任何事件資料，因此 <xref:System.EventHandler> 委派會與事件產生關聯。</span><span class="sxs-lookup"><span data-stu-id="1dcc1-110">The <xref:System.EventHandler> delegate is associated with the event, because no event data is provided.</span></span>  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="1dcc1-111">範例</span><span class="sxs-lookup"><span data-stu-id="1dcc1-111">Example</span></span>  
 <span data-ttu-id="1dcc1-112">下一個範例將示範如何引發和使用有提供資料的事件。</span><span class="sxs-lookup"><span data-stu-id="1dcc1-112">The next example shows how to raise and consume an event that provides data.</span></span> <span data-ttu-id="1dcc1-113"><xref:System.EventHandler%601> 委派會與事件相關聯，而且會提供自訂事件資料物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1dcc1-113">The <xref:System.EventHandler%601> delegate is associated with the event, and an instance of a custom event data object is provided.</span></span>  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="1dcc1-114">範例</span><span class="sxs-lookup"><span data-stu-id="1dcc1-114">Example</span></span>  
 <span data-ttu-id="1dcc1-115">下一個範例將示範如何宣告事件的委派。</span><span class="sxs-lookup"><span data-stu-id="1dcc1-115">The next example shows how to declare a delegate for an event.</span></span> <span data-ttu-id="1dcc1-116">委派的名稱為 `ThresholdReachedEventHandler`。</span><span class="sxs-lookup"><span data-stu-id="1dcc1-116">The delegate is named `ThresholdReachedEventHandler`.</span></span> <span data-ttu-id="1dcc1-117">這只是一個範例。</span><span class="sxs-lookup"><span data-stu-id="1dcc1-117">This is just an illustration.</span></span> <span data-ttu-id="1dcc1-118">通常，您可以使用 <xref:System.EventHandler> 或 <xref:System.EventHandler%601> 委派，所以不需要為事件宣告委派。</span><span class="sxs-lookup"><span data-stu-id="1dcc1-118">Typically, you do not have to declare a delegate for an event, because you can use either the <xref:System.EventHandler> or the <xref:System.EventHandler%601> delegate.</span></span> <span data-ttu-id="1dcc1-119">在某些少見的案例中您會需要宣告委派，像是讓無法使用泛型的舊版程式碼使用您的類別。</span><span class="sxs-lookup"><span data-stu-id="1dcc1-119">You should declare a delegate only in rare scenarios, such as making your class available to legacy code that cannot use generics.</span></span>  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="1dcc1-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1dcc1-120">See also</span></span>

- [<span data-ttu-id="1dcc1-121">事件</span><span class="sxs-lookup"><span data-stu-id="1dcc1-121">Events</span></span>](../../../docs/standard/events/index.md)
