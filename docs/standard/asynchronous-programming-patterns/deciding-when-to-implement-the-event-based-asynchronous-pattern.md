---
title: "決定何時實作事件架構非同步模式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: a00046aa-785d-4f7f-a8e5-d06475ea50da
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 48de1b736c251a61a2ad34975c77bc2bca139626
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="deciding-when-to-implement-the-event-based-asynchronous-pattern"></a><span data-ttu-id="c9bbc-102">決定何時實作事件架構非同步模式</span><span class="sxs-lookup"><span data-stu-id="c9bbc-102">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="c9bbc-103">事件架構非同步模式提供模式來公開非同步行為之類別。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-103">The Event-based Asynchronous Pattern provides a pattern for exposing the asynchronous behavior of a class.</span></span> <span data-ttu-id="c9bbc-104">此模式中，介紹[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]定義兩種模式來公開非同步行為： 非同步模式根據<xref:System.IAsyncResult?displayProperty=nameWithType>介面和事件為基礎的模式。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-104">With the introduction of this pattern, the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] defines two patterns for exposing asynchronous behavior: the Asynchronous Pattern based on the <xref:System.IAsyncResult?displayProperty=nameWithType> interface, and the event-based pattern.</span></span> <span data-ttu-id="c9bbc-105">本主題說明它是適合您實作這兩種模式。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-105">This topic describes when it is appropriate for you to implement both patterns.</span></span>  
  
 <span data-ttu-id="c9bbc-106">如需有關使用非同步程式設計<xref:System.IAsyncResult>介面，請參閱[事件架構非同步模式 (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-106">For more information about asynchronous programming with the <xref:System.IAsyncResult> interface, see [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  
  
## <a name="general-principles"></a><span data-ttu-id="c9bbc-107">一般原則</span><span class="sxs-lookup"><span data-stu-id="c9bbc-107">General Principles</span></span>  
 <span data-ttu-id="c9bbc-108">一般情況下，您應該使用事件架構非同步模式盡可能的非同步功能公開。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-108">In general, you should expose asynchronous features using the Event-based Asynchronous Pattern whenever possible.</span></span> <span data-ttu-id="c9bbc-109">不過，有一些以事件為基礎的模式無法滿足的需求。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-109">However, there are some requirements that the event-based pattern cannot meet.</span></span> <span data-ttu-id="c9bbc-110">在這些情況下，您可能需要實作<xref:System.IAsyncResult>除了以事件為基礎模式的模式。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-110">In those cases, you may need to implement the <xref:System.IAsyncResult> pattern in addition to the event-based pattern.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c9bbc-111">很少<xref:System.IAsyncResult>模式實作不具也實作以事件為基礎的模式。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-111">It is rare for the <xref:System.IAsyncResult> pattern to be implemented without the event-based pattern also being implemented.</span></span>  
  
## <a name="guidelines"></a><span data-ttu-id="c9bbc-112">方針</span><span class="sxs-lookup"><span data-stu-id="c9bbc-112">Guidelines</span></span>  
 <span data-ttu-id="c9bbc-113">下列清單說明當您應該實作事件架構非同步模式的指導方針：</span><span class="sxs-lookup"><span data-stu-id="c9bbc-113">The following list describes the guidelines for when you should implement Event-based Asynchronous Pattern:</span></span>  
  
-   <span data-ttu-id="c9bbc-114">作為預設應用程式開發介面的事件為基礎的模式來公開您的類別的非同步行為。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-114">Use the event-based pattern as the default API to expose asynchronous behavior for your class.</span></span>  
  
-   <span data-ttu-id="c9bbc-115">不會公開<xref:System.IAsyncResult>模式時您的類別主要用於用戶端應用程式，例如 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-115">Do not expose the <xref:System.IAsyncResult> pattern when your class is primarily used in a client application, for example Windows Forms.</span></span>  
  
-   <span data-ttu-id="c9bbc-116">只會公開<xref:System.IAsyncResult>模式需要時將它以符合您的需求。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-116">Only expose the <xref:System.IAsyncResult> pattern when it is necessary for meeting your requirements.</span></span> <span data-ttu-id="c9bbc-117">例如，與現有的 API 相容性可能需要您公開<xref:System.IAsyncResult>模式。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-117">For example, compatibility with an existing API may require you to expose the <xref:System.IAsyncResult> pattern.</span></span>  
  
-   <span data-ttu-id="c9bbc-118">不會公開<xref:System.IAsyncResult>模式，而不會也讓事件為基礎的模式。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-118">Do not expose the <xref:System.IAsyncResult> pattern without also exposing the event-based pattern.</span></span>  
  
-   <span data-ttu-id="c9bbc-119">如果您必須公開<xref:System.IAsyncResult>模式，這樣一個進階選項。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-119">If you must expose the <xref:System.IAsyncResult> pattern, do so as an advanced option.</span></span> <span data-ttu-id="c9bbc-120">例如，如果您產生 proxy 物件，產生事件為基礎的模式根據預設，與選項，以產生<xref:System.IAsyncResult>模式。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-120">For example, if you generate a proxy object, generate the event-based pattern by default, with an option to generate the <xref:System.IAsyncResult> pattern.</span></span>  
  
-   <span data-ttu-id="c9bbc-121">根據事件架構模式實作您<xref:System.IAsyncResult>模式實作。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-121">Build your event-based pattern implementation on your <xref:System.IAsyncResult> pattern implementation.</span></span>  
  
-   <span data-ttu-id="c9bbc-122">避免公開這兩個以事件為基礎的模式和<xref:System.IAsyncResult>相同類別上的模式。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-122">Avoid exposing both the event-based pattern and the <xref:System.IAsyncResult> pattern on the same class.</span></span> <span data-ttu-id="c9bbc-123">公開"較高層級"類別的事件基礎模式和<xref:System.IAsyncResult>模式上的 「 層級降低 」 類別。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-123">Expose the event-based pattern on "higher level" classes and the <xref:System.IAsyncResult> pattern on "lower level" classes.</span></span> <span data-ttu-id="c9bbc-124">例如，在比較以事件為基礎模式<xref:System.Net.WebClient>元件<xref:System.IAsyncResult>模式上<xref:System.Web.HttpRequest>類別。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-124">For example, compare the event-based pattern on the <xref:System.Net.WebClient> component with the <xref:System.IAsyncResult> pattern on the <xref:System.Web.HttpRequest> class.</span></span>  
  
    -   <span data-ttu-id="c9bbc-125">公開 （expose) 事件為基礎的模式和<xref:System.IAsyncResult>相容性需求時，在相同類別上的模式。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-125">Expose the event-based pattern and the <xref:System.IAsyncResult> pattern on the same class when compatibility requires it.</span></span> <span data-ttu-id="c9bbc-126">例如，如果您已經釋放的 API，會使用<xref:System.IAsyncResult>模式中，您需要保留<xref:System.IAsyncResult>回溯相容性模式。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-126">For example, if you have already released an API that uses the <xref:System.IAsyncResult> pattern, you would need to retain the <xref:System.IAsyncResult> pattern for backward compatibility.</span></span>  
  
    -   <span data-ttu-id="c9bbc-127">公開 （expose) 事件為基礎的模式和<xref:System.IAsyncResult>模式相同類別上，如果產生的物件模型複雜性上限分開實作的優點。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-127">Expose the event-based pattern and the <xref:System.IAsyncResult> pattern on the same class if the resulting object model complexity outweighs the benefit of separating the implementations.</span></span> <span data-ttu-id="c9bbc-128">最好是公開比避免公開以事件為基礎模式的單一類別的兩個模式。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-128">It is better to expose both patterns on a single class than to avoid exposing the event-based pattern.</span></span>  
  
    -   <span data-ttu-id="c9bbc-129">如果您必須公開這兩個以事件為基礎的模式和<xref:System.IAsyncResult>模式的單一類別，使用<xref:System.ComponentModel.EditorBrowsableAttribute>設<xref:System.ComponentModel.EditorBrowsableState.Advanced>標示<xref:System.IAsyncResult>模式實作，做為進階功能。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-129">If you must expose both the event-based pattern and <xref:System.IAsyncResult> pattern on a single class, use <xref:System.ComponentModel.EditorBrowsableAttribute> set to <xref:System.ComponentModel.EditorBrowsableState.Advanced> to mark the <xref:System.IAsyncResult> pattern implementation as an advanced feature.</span></span> <span data-ttu-id="c9bbc-130">這表示設計環境，例如[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]IntelliSense、 顯示<xref:System.IAsyncResult>屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-130">This indicates to design environments, such as [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] IntelliSense, not to display the <xref:System.IAsyncResult> properties and methods.</span></span> <span data-ttu-id="c9bbc-131">這些屬性和方法仍然完整地使用，但開發人員使用透過 IntelliSense 可以清楚地檢視應用程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-131">These properties and methods are still fully usable, but the developer working through IntelliSense has a clearer view of the API.</span></span>  
  
## <a name="criteria-for-exposing-the-iasyncresult-pattern-in-addition-to-the-event-based-pattern"></a><span data-ttu-id="c9bbc-132">準則來公開以事件為基礎模式除了 IAsyncResult 模式</span><span class="sxs-lookup"><span data-stu-id="c9bbc-132">Criteria for Exposing the IAsyncResult Pattern in Addition to the Event-based Pattern</span></span>  
 <span data-ttu-id="c9bbc-133">雖然事件架構非同步模式有許多好處，在先前所述的案例下，它也有一些缺點，您應該注意如果效能是您最重要的需求。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-133">While the Event-based Asynchronous Pattern has many benefits under the previously mentioned scenarios, it does have some drawbacks, which you should be aware of if performance is your most important requirement.</span></span>  
  
 <span data-ttu-id="c9bbc-134">有三種案例，以事件為基礎的模式不會處理與<xref:System.IAsyncResult>模式：</span><span class="sxs-lookup"><span data-stu-id="c9bbc-134">There are three scenarios that the event-based pattern does not address as well as the <xref:System.IAsyncResult> pattern:</span></span>  
  
-   <span data-ttu-id="c9bbc-135">封鎖等候上一個<xref:System.IAsyncResult></span><span class="sxs-lookup"><span data-stu-id="c9bbc-135">Blocking wait on one <xref:System.IAsyncResult></span></span>  
  
-   <span data-ttu-id="c9bbc-136">封鎖許多等候<xref:System.IAsyncResult>物件</span><span class="sxs-lookup"><span data-stu-id="c9bbc-136">Blocking wait on many <xref:System.IAsyncResult> objects</span></span>  
  
-   <span data-ttu-id="c9bbc-137">輪詢完成<xref:System.IAsyncResult></span><span class="sxs-lookup"><span data-stu-id="c9bbc-137">Polling for completion on the <xref:System.IAsyncResult></span></span>  
  
 <span data-ttu-id="c9bbc-138">您可以使用以事件為基礎的模式，來解決這些案例，但這樣做很比使用較繁瑣<xref:System.IAsyncResult>模式。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-138">You can address these scenarios by using the event-based pattern, but doing so is more cumbersome than using the <xref:System.IAsyncResult> pattern.</span></span>  
  
 <span data-ttu-id="c9bbc-139">開發人員經常使用<xref:System.IAsyncResult>模式通常會有極高的效能需求的服務。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-139">Developers often use the <xref:System.IAsyncResult> pattern for services that typically have very high performance requirements.</span></span> <span data-ttu-id="c9bbc-140">例如，輪詢完成案例是高效能伺服器技術。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-140">For example, the polling for completion scenario is a high-performance server technique.</span></span>  
  
 <span data-ttu-id="c9bbc-141">此外，事件為基礎的模式會比效率<xref:System.IAsyncResult>模式，因為它會建立多個物件，特別是<xref:System.EventArgs>，而且因為它會在執行緒之間同步處理。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-141">Additionally, the event-based pattern is less efficient than the <xref:System.IAsyncResult> pattern because it creates more objects, especially <xref:System.EventArgs>, and because it synchronizes across threads.</span></span>  
  
 <span data-ttu-id="c9bbc-142">下列清單顯示一些建議，如果您決定使用，請遵循<xref:System.IAsyncResult>模式：</span><span class="sxs-lookup"><span data-stu-id="c9bbc-142">The following list shows some recommendations to follow if you decide to use the <xref:System.IAsyncResult> pattern:</span></span>  
  
-   <span data-ttu-id="c9bbc-143">只會公開<xref:System.IAsyncResult>模式時您特別需要支援<xref:System.Threading.WaitHandle>或<xref:System.IAsyncResult>物件。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-143">Only expose the <xref:System.IAsyncResult> pattern when you specifically require support for <xref:System.Threading.WaitHandle> or <xref:System.IAsyncResult> objects.</span></span>  
  
-   <span data-ttu-id="c9bbc-144">只會公開<xref:System.IAsyncResult>模式時使用的現有 API<xref:System.IAsyncResult>模式。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-144">Only expose the <xref:System.IAsyncResult> pattern when you have an existing API that uses the <xref:System.IAsyncResult> pattern.</span></span>  
  
-   <span data-ttu-id="c9bbc-145">如果您有根據現有 API<xref:System.IAsyncResult>模式，請考慮也公開您的下一個版本中事件為基礎的模式。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-145">If you have an existing API based on the <xref:System.IAsyncResult> pattern, consider also exposing the event-based pattern in your next release.</span></span>  
  
-   <span data-ttu-id="c9bbc-146">只會公開<xref:System.IAsyncResult>模式，如果您有高的效能需求，因此您已確認無法符合 endpointlistener 事件為基礎的模式，但可以達成<xref:System.IAsyncResult>模式。</span><span class="sxs-lookup"><span data-stu-id="c9bbc-146">Only expose <xref:System.IAsyncResult> pattern if you have high performance requirements which you have verified cannot be met by the event-based pattern but can be met by the <xref:System.IAsyncResult> pattern.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9bbc-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9bbc-147">See Also</span></span>  
 [<span data-ttu-id="c9bbc-148">逐步解說：實作支援事件架構非同步模式的元件</span><span class="sxs-lookup"><span data-stu-id="c9bbc-148">Walkthrough: Implementing a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="c9bbc-149">事件架構非同步模式 (EAP)</span><span class="sxs-lookup"><span data-stu-id="c9bbc-149">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="c9bbc-150">使用事件架構非同步模式設計多執行緒程式</span><span class="sxs-lookup"><span data-stu-id="c9bbc-150">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="c9bbc-151">實作事件架構非同步模式</span><span class="sxs-lookup"><span data-stu-id="c9bbc-151">Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="c9bbc-152">實作事件架構非同步模式的最佳作法</span><span class="sxs-lookup"><span data-stu-id="c9bbc-152">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="c9bbc-153">事件架構非同步模式概觀</span><span class="sxs-lookup"><span data-stu-id="c9bbc-153">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
