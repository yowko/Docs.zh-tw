---
title: 決定何時實作事件架構非同步模式
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: 04bdc94bceeed313d519658afb853a77e218989e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398589"
---
# <a name="deciding-when-to-implement-the-event-based-asynchronous-pattern"></a><span data-ttu-id="64929-102">決定何時實作事件架構非同步模式</span><span class="sxs-lookup"><span data-stu-id="64929-102">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="64929-103">事件架構非同步模式提供的模式可公開類別的非同步行為。</span><span class="sxs-lookup"><span data-stu-id="64929-103">The Event-based Asynchronous Pattern provides a pattern for exposing the asynchronous behavior of a class.</span></span> <span data-ttu-id="64929-104">引進此模式之後，[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 定義兩種模式來公開非同步行為：以 <xref:System.IAsyncResult?displayProperty=nameWithType> 介面為基礎的非同步模式與事件架構模式。</span><span class="sxs-lookup"><span data-stu-id="64929-104">With the introduction of this pattern, the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] defines two patterns for exposing asynchronous behavior: the Asynchronous Pattern based on the <xref:System.IAsyncResult?displayProperty=nameWithType> interface, and the event-based pattern.</span></span> <span data-ttu-id="64929-105">本主題說明適合實作這兩種模式的時機。</span><span class="sxs-lookup"><span data-stu-id="64929-105">This topic describes when it is appropriate for you to implement both patterns.</span></span>  
  
 <span data-ttu-id="64929-106">如需使用 <xref:System.IAsyncResult> 介面進行非同步程式設計的詳細資訊，請參閱[非同步程式設計模型 (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)。</span><span class="sxs-lookup"><span data-stu-id="64929-106">For more information about asynchronous programming with the <xref:System.IAsyncResult> interface, see [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md).</span></span>  
  
## <a name="general-principles"></a><span data-ttu-id="64929-107">一般準則</span><span class="sxs-lookup"><span data-stu-id="64929-107">General Principles</span></span>  
 <span data-ttu-id="64929-108">一般而言，您應該儘可能使用事件架構非同步模式來公開非同步功能。</span><span class="sxs-lookup"><span data-stu-id="64929-108">In general, you should expose asynchronous features using the Event-based Asynchronous Pattern whenever possible.</span></span> <span data-ttu-id="64929-109">不過，事件架構模式無法符合一些需求。</span><span class="sxs-lookup"><span data-stu-id="64929-109">However, there are some requirements that the event-based pattern cannot meet.</span></span> <span data-ttu-id="64929-110">在那些情況下，除了事件架構模式之外，您可能還必須實作 <xref:System.IAsyncResult> 模式。</span><span class="sxs-lookup"><span data-stu-id="64929-110">In those cases, you may need to implement the <xref:System.IAsyncResult> pattern in addition to the event-based pattern.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="64929-111">實作 <xref:System.IAsyncResult> 模式但未一併實作事件架構模式的情況非常罕見。</span><span class="sxs-lookup"><span data-stu-id="64929-111">It is rare for the <xref:System.IAsyncResult> pattern to be implemented without the event-based pattern also being implemented.</span></span>  
  
## <a name="guidelines"></a><span data-ttu-id="64929-112">方針</span><span class="sxs-lookup"><span data-stu-id="64929-112">Guidelines</span></span>  
 <span data-ttu-id="64929-113">下列清單說明實作事件架構非同步模式時的指導方針：</span><span class="sxs-lookup"><span data-stu-id="64929-113">The following list describes the guidelines for when you should implement Event-based Asynchronous Pattern:</span></span>  
  
-   <span data-ttu-id="64929-114">使用事件架構模式作為預設 API 來公開類別的非同步行為。</span><span class="sxs-lookup"><span data-stu-id="64929-114">Use the event-based pattern as the default API to expose asynchronous behavior for your class.</span></span>  
  
-   <span data-ttu-id="64929-115">當您的類別主要用於用戶端應用程式 (例如 Windows Forms) 時，請不要公開 <xref:System.IAsyncResult> 模式。</span><span class="sxs-lookup"><span data-stu-id="64929-115">Do not expose the <xref:System.IAsyncResult> pattern when your class is primarily used in a client application, for example Windows Forms.</span></span>  
  
-   <span data-ttu-id="64929-116">只有在為符合您的需求時，才公開 <xref:System.IAsyncResult> 模式。</span><span class="sxs-lookup"><span data-stu-id="64929-116">Only expose the <xref:System.IAsyncResult> pattern when it is necessary for meeting your requirements.</span></span> <span data-ttu-id="64929-117">例如，與現有 API 的相容性可能需要您公開 <xref:System.IAsyncResult> 模式。</span><span class="sxs-lookup"><span data-stu-id="64929-117">For example, compatibility with an existing API may require you to expose the <xref:System.IAsyncResult> pattern.</span></span>  
  
-   <span data-ttu-id="64929-118">沒有一併公開事件架構模式時，請不要公開 <xref:System.IAsyncResult> 模式。</span><span class="sxs-lookup"><span data-stu-id="64929-118">Do not expose the <xref:System.IAsyncResult> pattern without also exposing the event-based pattern.</span></span>  
  
-   <span data-ttu-id="64929-119">如果您必須公開 <xref:System.IAsyncResult> 模式，請以進階選項的方式執行此動作。</span><span class="sxs-lookup"><span data-stu-id="64929-119">If you must expose the <xref:System.IAsyncResult> pattern, do so as an advanced option.</span></span> <span data-ttu-id="64929-120">例如，如果您透過產生 <xref:System.IAsyncResult> 模式的選項來產生 Proxy 物件，預設會產生事件架構模式。</span><span class="sxs-lookup"><span data-stu-id="64929-120">For example, if you generate a proxy object, generate the event-based pattern by default, with an option to generate the <xref:System.IAsyncResult> pattern.</span></span>  
  
-   <span data-ttu-id="64929-121">請在您的 <xref:System.IAsyncResult> 模式實作上建置事件架構模式實作。</span><span class="sxs-lookup"><span data-stu-id="64929-121">Build your event-based pattern implementation on your <xref:System.IAsyncResult> pattern implementation.</span></span>  
  
-   <span data-ttu-id="64929-122">避免在相同類別上公開這兩個事件架構模式和 <xref:System.IAsyncResult> 模式。</span><span class="sxs-lookup"><span data-stu-id="64929-122">Avoid exposing both the event-based pattern and the <xref:System.IAsyncResult> pattern on the same class.</span></span> <span data-ttu-id="64929-123">在「較高層級的」類別上公開事件架構模式，並在「較低層級的」類別上公開 <xref:System.IAsyncResult> 模式。</span><span class="sxs-lookup"><span data-stu-id="64929-123">Expose the event-based pattern on "higher level" classes and the <xref:System.IAsyncResult> pattern on "lower level" classes.</span></span> <span data-ttu-id="64929-124">例如，比較 <xref:System.Net.WebClient> 元件上的事件架構模式與 <xref:System.Web.HttpRequest> 類別上的 <xref:System.IAsyncResult> 模式。</span><span class="sxs-lookup"><span data-stu-id="64929-124">For example, compare the event-based pattern on the <xref:System.Net.WebClient> component with the <xref:System.IAsyncResult> pattern on the <xref:System.Web.HttpRequest> class.</span></span>  
  
    -   <span data-ttu-id="64929-125">當基於相容性需要時，請在相同類別上公開事件架構模式與 <xref:System.IAsyncResult> 模式。</span><span class="sxs-lookup"><span data-stu-id="64929-125">Expose the event-based pattern and the <xref:System.IAsyncResult> pattern on the same class when compatibility requires it.</span></span> <span data-ttu-id="64929-126">例如，如果您已發行使用 <xref:System.IAsyncResult> 模式的 API，則需要保留 <xref:System.IAsyncResult> 模式以提供回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="64929-126">For example, if you have already released an API that uses the <xref:System.IAsyncResult> pattern, you would need to retain the <xref:System.IAsyncResult> pattern for backward compatibility.</span></span>  
  
    -   <span data-ttu-id="64929-127">如果產生的物件模型複雜度超過個別實作的優點，請在相同類別上公開事件架構模式與 <xref:System.IAsyncResult> 模式。</span><span class="sxs-lookup"><span data-stu-id="64929-127">Expose the event-based pattern and the <xref:System.IAsyncResult> pattern on the same class if the resulting object model complexity outweighs the benefit of separating the implementations.</span></span> <span data-ttu-id="64929-128">最好在單一類別上公開這兩個模式，而不是避免公開事件架構模式。</span><span class="sxs-lookup"><span data-stu-id="64929-128">It is better to expose both patterns on a single class than to avoid exposing the event-based pattern.</span></span>  
  
    -   <span data-ttu-id="64929-129">如果您必須在單一類別上公開事件架構模式和 <xref:System.IAsyncResult> 模式，請以進階選項的方式，使用設為 <xref:System.ComponentModel.EditorBrowsableState.Advanced> 的 <xref:System.ComponentModel.EditorBrowsableAttribute> 來標示 <xref:System.IAsyncResult> 模式實作。</span><span class="sxs-lookup"><span data-stu-id="64929-129">If you must expose both the event-based pattern and <xref:System.IAsyncResult> pattern on a single class, use <xref:System.ComponentModel.EditorBrowsableAttribute> set to <xref:System.ComponentModel.EditorBrowsableState.Advanced> to mark the <xref:System.IAsyncResult> pattern implementation as an advanced feature.</span></span> <span data-ttu-id="64929-130">這會向 Visual Studio IntelliSense 這類設計環境表示，不要顯示 <xref:System.IAsyncResult> 屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="64929-130">This indicates to design environments, such as Visual Studio IntelliSense, not to display the <xref:System.IAsyncResult> properties and methods.</span></span> <span data-ttu-id="64929-131">這些屬性和方法仍完全可供使用，但透過 IntelliSense 處理的開發人員會有較清楚的 API 檢視。</span><span class="sxs-lookup"><span data-stu-id="64929-131">These properties and methods are still fully usable, but the developer working through IntelliSense has a clearer view of the API.</span></span>  
  
## <a name="criteria-for-exposing-the-iasyncresult-pattern-in-addition-to-the-event-based-pattern"></a><span data-ttu-id="64929-132">除了公開事件架構模式之外還公開 IAsyncResult 模式的準則</span><span class="sxs-lookup"><span data-stu-id="64929-132">Criteria for Exposing the IAsyncResult Pattern in Addition to the Event-based Pattern</span></span>  
 <span data-ttu-id="64929-133">雖然在先前所述的案例下，事件架構非同步模式有許多優點，但也有一些缺點，如果您最以效能為重，應多加注意。</span><span class="sxs-lookup"><span data-stu-id="64929-133">While the Event-based Asynchronous Pattern has many benefits under the previously mentioned scenarios, it does have some drawbacks, which you should be aware of if performance is your most important requirement.</span></span>  
  
 <span data-ttu-id="64929-134">有三種案例，事件架構模式與 <xref:System.IAsyncResult> 模式都不會處理：</span><span class="sxs-lookup"><span data-stu-id="64929-134">There are three scenarios that the event-based pattern does not address as well as the <xref:System.IAsyncResult> pattern:</span></span>  
  
-   <span data-ttu-id="64929-135">封鎖等候一個 <xref:System.IAsyncResult></span><span class="sxs-lookup"><span data-stu-id="64929-135">Blocking wait on one <xref:System.IAsyncResult></span></span>  
  
-   <span data-ttu-id="64929-136">封鎖等候多個 <xref:System.IAsyncResult> 物件</span><span class="sxs-lookup"><span data-stu-id="64929-136">Blocking wait on many <xref:System.IAsyncResult> objects</span></span>  
  
-   <span data-ttu-id="64929-137">輪詢 <xref:System.IAsyncResult> 是否完成</span><span class="sxs-lookup"><span data-stu-id="64929-137">Polling for completion on the <xref:System.IAsyncResult></span></span>  
  
 <span data-ttu-id="64929-138">您可以使用事件架構模式來處理這些案例，但這樣做會比使用 <xref:System.IAsyncResult> 模式更麻煩。</span><span class="sxs-lookup"><span data-stu-id="64929-138">You can address these scenarios by using the event-based pattern, but doing so is more cumbersome than using the <xref:System.IAsyncResult> pattern.</span></span>  
  
 <span data-ttu-id="64929-139">開發人員經常針對有極高效能需求的服務使用 <xref:System.IAsyncResult> 模式。</span><span class="sxs-lookup"><span data-stu-id="64929-139">Developers often use the <xref:System.IAsyncResult> pattern for services that typically have very high performance requirements.</span></span> <span data-ttu-id="64929-140">例如，輪詢完成案例就是高效能伺服器技巧。</span><span class="sxs-lookup"><span data-stu-id="64929-140">For example, the polling for completion scenario is a high-performance server technique.</span></span>  
  
 <span data-ttu-id="64929-141">此外，因為事件架構模式會建立較多物件 (特別是 <xref:System.EventArgs>) 且會跨執行緒進行同步處理，所以效率會比 <xref:System.IAsyncResult> 差。</span><span class="sxs-lookup"><span data-stu-id="64929-141">Additionally, the event-based pattern is less efficient than the <xref:System.IAsyncResult> pattern because it creates more objects, especially <xref:System.EventArgs>, and because it synchronizes across threads.</span></span>  
  
 <span data-ttu-id="64929-142">如果您決定使用 <xref:System.IAsyncResult> 模式，下列清單顯示一些可遵循的建議：</span><span class="sxs-lookup"><span data-stu-id="64929-142">The following list shows some recommendations to follow if you decide to use the <xref:System.IAsyncResult> pattern:</span></span>  
  
-   <span data-ttu-id="64929-143">只有在您具體需要支援 <xref:System.Threading.WaitHandle> 或 <xref:System.IAsyncResult> 物件時，才公開 <xref:System.IAsyncResult> 模式。</span><span class="sxs-lookup"><span data-stu-id="64929-143">Only expose the <xref:System.IAsyncResult> pattern when you specifically require support for <xref:System.Threading.WaitHandle> or <xref:System.IAsyncResult> objects.</span></span>  
  
-   <span data-ttu-id="64929-144">只有在您現有的 API 使用 <xref:System.IAsyncResult> 模式時，才公開 <xref:System.IAsyncResult> 模式。</span><span class="sxs-lookup"><span data-stu-id="64929-144">Only expose the <xref:System.IAsyncResult> pattern when you have an existing API that uses the <xref:System.IAsyncResult> pattern.</span></span>  
  
-   <span data-ttu-id="64929-145">如果您的現有 API 以 <xref:System.IAsyncResult> 模式為基礎，也請考慮在下一版公開事件架構模式。</span><span class="sxs-lookup"><span data-stu-id="64929-145">If you have an existing API based on the <xref:System.IAsyncResult> pattern, consider also exposing the event-based pattern in your next release.</span></span>  
  
-   <span data-ttu-id="64929-146">只有在您有高效能需求，且已驗證事件架構模式無法符合該需求，但 <xref:System.IAsyncResult> 模式能符合時，才公開 <xref:System.IAsyncResult> 模式。</span><span class="sxs-lookup"><span data-stu-id="64929-146">Only expose <xref:System.IAsyncResult> pattern if you have high performance requirements which you have verified cannot be met by the event-based pattern but can be met by the <xref:System.IAsyncResult> pattern.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64929-147">請參閱</span><span class="sxs-lookup"><span data-stu-id="64929-147">See Also</span></span>  
 [<span data-ttu-id="64929-148">操作說明：實作支援事件架構非同步模式的元件</span><span class="sxs-lookup"><span data-stu-id="64929-148">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="64929-149">事件架構非同步模式 (EAP)</span><span class="sxs-lookup"><span data-stu-id="64929-149">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [<span data-ttu-id="64929-150">實作事件架構非同步模式</span><span class="sxs-lookup"><span data-stu-id="64929-150">Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="64929-151">實作事件架構非同步模式的最佳作法</span><span class="sxs-lookup"><span data-stu-id="64929-151">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="64929-152">事件架構非同步模式概觀</span><span class="sxs-lookup"><span data-stu-id="64929-152">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
