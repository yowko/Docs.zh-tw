---
title: 弱式事件模式
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: 92d0a61c2bbf9cc668b969c3e1420914b9f9f150
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650775"
---
# <a name="weak-event-patterns"></a><span data-ttu-id="30300-102">弱式事件模式</span><span class="sxs-lookup"><span data-stu-id="30300-102">Weak Event Patterns</span></span>
<span data-ttu-id="30300-103">在應用程式，它可能會附加到事件來源的處理常式不會終結協調的方式處理常式附加至來源接聽程式物件。</span><span class="sxs-lookup"><span data-stu-id="30300-103">In applications, it is possible that handlers that are attached to event sources will not be destroyed in coordination with the listener object that attached the handler to the source.</span></span> <span data-ttu-id="30300-104">這種情況可能會導致記憶體流失無關。</span><span class="sxs-lookup"><span data-stu-id="30300-104">This situation can lead to memory leaks.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="30300-105">導入了可用來解決這個問題，提供的專用的管理員類別的特定事件，並針對該事件的接聽程式上實作介面的設計模式。</span><span class="sxs-lookup"><span data-stu-id="30300-105">introduces a design pattern that can be used to address this issue, by providing a dedicated manager class for particular events and implementing an interface on listeners for that event.</span></span> <span data-ttu-id="30300-106">這種設計模式就所謂*弱式事件模式*。</span><span class="sxs-lookup"><span data-stu-id="30300-106">This design pattern is known as the *weak event pattern*.</span></span>  
  
## <a name="why-implement-the-weak-event-pattern"></a><span data-ttu-id="30300-107">為何要實作弱式事件模式？</span><span class="sxs-lookup"><span data-stu-id="30300-107">Why Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="30300-108">接聽事件可能會導致記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="30300-108">Listening for events can lead to memory leaks.</span></span> <span data-ttu-id="30300-109">接聽事件的一般技巧是使用將處理常式附加至事件來源上的特定語言的語法。</span><span class="sxs-lookup"><span data-stu-id="30300-109">The typical technique for listening to an event is to use the language-specific syntax that attaches a handler to an event on a source.</span></span> <span data-ttu-id="30300-110">例如，在C#，語法是： `source.SomeEvent += new SomeEventHandler(MyEventHandler)`。</span><span class="sxs-lookup"><span data-stu-id="30300-110">For example, in C#, that syntax is: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span></span>  
  
 <span data-ttu-id="30300-111">這項技術會建立強式參考從事件來源的事件接聽程式。</span><span class="sxs-lookup"><span data-stu-id="30300-111">This technique creates a strong reference from the event source to the event listener.</span></span> <span data-ttu-id="30300-112">一般情況下，將事件處理常式附加接聽程式會造成接聽程式 （除非明確移除事件處理常式），會受到來源的物件存留期物件存留期。</span><span class="sxs-lookup"><span data-stu-id="30300-112">Ordinarily, attaching an event handler for a listener causes the listener to have an object lifetime that is influenced by the object lifetime of the source (unless the event handler is explicitly removed).</span></span> <span data-ttu-id="30300-113">但在某些情況下，您可能想要其他因素所控制的接聽程式的物件存留期例如是否目前屬於視覺化樹狀結構的應用程式，而不是由來源的存留期。</span><span class="sxs-lookup"><span data-stu-id="30300-113">But in certain circumstances, you might want the object lifetime of the listener to be controlled by other factors, such as whether it currently belongs to the visual tree of the application, and not by the lifetime of the source.</span></span> <span data-ttu-id="30300-114">一般事件模式時的來源物件存留期超出接聽程式的物件存留期時，會導致記憶體流失： 接聽程式存留的時間比預期長。</span><span class="sxs-lookup"><span data-stu-id="30300-114">Whenever the source object lifetime extends beyond the object lifetime of the listener, the normal event pattern leads to a memory leak: the listener is kept alive longer than intended.</span></span>  
  
 <span data-ttu-id="30300-115">弱式事件模式是設計用來解決此記憶體流失問題。</span><span class="sxs-lookup"><span data-stu-id="30300-115">The weak event pattern is designed to solve this memory leak problem.</span></span> <span data-ttu-id="30300-116">接聽程式需要註冊事件，但是接聽程式不會明確知道何時要取消註冊時，可以使用弱式事件模式。</span><span class="sxs-lookup"><span data-stu-id="30300-116">The weak event pattern can be used whenever a listener needs to register for an event, but the listener does not explicitly know when to unregister.</span></span> <span data-ttu-id="30300-117">每當來源的物件存留期超過有用的物件存留期，接聽程式時，可以也使用弱式事件模式。</span><span class="sxs-lookup"><span data-stu-id="30300-117">The weak event pattern can also be used whenever the object lifetime of the source exceeds the useful object lifetime of the listener.</span></span> <span data-ttu-id="30300-118">(在此情況下，*有用*由您決定。)弱式事件模式可讓註冊和接收事件，而不會影響物件存留期特性，以任何方式接聽程式接聽程式。</span><span class="sxs-lookup"><span data-stu-id="30300-118">(In this case, *useful* is determined by you.) The weak event pattern allows the listener to register for and receive the event without affecting the object lifetime characteristics of the listener in any way.</span></span> <span data-ttu-id="30300-119">作用中，從來源的隱含的參考不會判斷是否適合進行記憶體回收的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="30300-119">In effect, the implied reference from the source does not determine whether the listener is eligible for garbage collection.</span></span> <span data-ttu-id="30300-120">參考是弱式參考，因此命名的弱式事件模式和相關[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="30300-120">The reference is a weak reference, thus the naming of the weak event pattern and the related [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)].</span></span> <span data-ttu-id="30300-121">接聽程式可以是記憶體回收或否則損毀，而且來源可以繼續，而不需要保留構成處理常式現在已終結的物件參考。</span><span class="sxs-lookup"><span data-stu-id="30300-121">The listener can be garbage collected or otherwise destroyed, and the source can continue without retaining noncollectible handler references to a now destroyed object.</span></span>  
  
## <a name="who-should-implement-the-weak-event-pattern"></a><span data-ttu-id="30300-122">誰應該實作弱式事件模式？</span><span class="sxs-lookup"><span data-stu-id="30300-122">Who Should Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="30300-123">實作弱式事件模式有趣的是主要是針對控制項作者。</span><span class="sxs-lookup"><span data-stu-id="30300-123">Implementing the weak event pattern is interesting primarily for control authors.</span></span> <span data-ttu-id="30300-124">身為控制項作者，您負責大部分的行為與您的控制項和它對應用程式，它會插入影響的內含項目。</span><span class="sxs-lookup"><span data-stu-id="30300-124">As a control author, you are largely responsible for the behavior and containment of your control and the impact it has on applications in which it is inserted.</span></span> <span data-ttu-id="30300-125">這包括控制物件存留期行為，特別是處理的所述的記憶體流失的問題。</span><span class="sxs-lookup"><span data-stu-id="30300-125">This includes the control object lifetime behavior, in particular the handling of the described memory leak problem.</span></span>  
  
 <span data-ttu-id="30300-126">某些情況下原本就是讓他們的弱式事件模式的應用程式。</span><span class="sxs-lookup"><span data-stu-id="30300-126">Certain scenarios inherently lend themselves to the application of the weak event pattern.</span></span> <span data-ttu-id="30300-127">這類案例之一是資料繫結。</span><span class="sxs-lookup"><span data-stu-id="30300-127">One such scenario is data binding.</span></span> <span data-ttu-id="30300-128">在資料繫結，它是很常見的來源物件是完全獨立於接聽程式物件，因為它是繫結的目標項目。</span><span class="sxs-lookup"><span data-stu-id="30300-128">In data binding, it is common for the source object to be completely independent of the listener object, which is a target of a binding.</span></span> <span data-ttu-id="30300-129">許多層面[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]資料繫結已經具有弱式事件模式中事件的實作方式套用。</span><span class="sxs-lookup"><span data-stu-id="30300-129">Many aspects of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] data binding already have the weak event pattern applied in how the events are implemented.</span></span>  
  
## <a name="how-to-implement-the-weak-event-pattern"></a><span data-ttu-id="30300-130">如何實作弱式事件模式</span><span class="sxs-lookup"><span data-stu-id="30300-130">How to Implement the Weak Event Pattern</span></span>  
 <span data-ttu-id="30300-131">有三種方式可以實作弱式事件模式。</span><span class="sxs-lookup"><span data-stu-id="30300-131">There are three ways to implement weak event pattern.</span></span> <span data-ttu-id="30300-132">下表列出這三種方法，並提供一些指引，當您應該使用的每個。</span><span class="sxs-lookup"><span data-stu-id="30300-132">The following table lists the three approaches and provides some guidance for when you should use each.</span></span>  
  
|<span data-ttu-id="30300-133">方法</span><span class="sxs-lookup"><span data-stu-id="30300-133">Approach</span></span>|<span data-ttu-id="30300-134">何時實作</span><span class="sxs-lookup"><span data-stu-id="30300-134">When to Implement</span></span>|  
|--------------|-----------------------|  
|<span data-ttu-id="30300-135">使用現有的弱式事件管理員類別</span><span class="sxs-lookup"><span data-stu-id="30300-135">Use an existing weak event manager class</span></span>|<span data-ttu-id="30300-136">如果您想要訂閱的事件都有對應<xref:System.Windows.WeakEventManager>，使用現有的弱式事件管理員。</span><span class="sxs-lookup"><span data-stu-id="30300-136">If the event you want to subscribe to has a corresponding <xref:System.Windows.WeakEventManager>, use the existing weak event manager.</span></span> <span data-ttu-id="30300-137">WPF 隨附的弱式事件管理員的清單，請參閱中的繼承階層<xref:System.Windows.WeakEventManager>類別。</span><span class="sxs-lookup"><span data-stu-id="30300-137">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span> <span data-ttu-id="30300-138">包含的弱式事件管理員是有限的因為您可能必須選擇其中一種其他方法。</span><span class="sxs-lookup"><span data-stu-id="30300-138">Because the included weak event managers are limited, you will probably need to choose one of the other approaches.</span></span>|  
|<span data-ttu-id="30300-139">使用一般的弱式事件管理員類別</span><span class="sxs-lookup"><span data-stu-id="30300-139">Use a generic weak event manager class</span></span>|<span data-ttu-id="30300-140">使用泛型<xref:System.Windows.WeakEventManager%602>時的現有<xref:System.Windows.WeakEventManager>無法使用，您想要輕鬆地實作，且您不擔心效率。</span><span class="sxs-lookup"><span data-stu-id="30300-140">Use a generic <xref:System.Windows.WeakEventManager%602> when an existing <xref:System.Windows.WeakEventManager> is not available, you want an easy way to implement, and you are not concerned about efficiency.</span></span> <span data-ttu-id="30300-141">泛型<xref:System.Windows.WeakEventManager%602>效率比現有或自訂的弱式事件管理員。</span><span class="sxs-lookup"><span data-stu-id="30300-141">The generic <xref:System.Windows.WeakEventManager%602> is less efficient than an existing or custom weak event manager.</span></span> <span data-ttu-id="30300-142">比方說，泛型類別會執行更多的反映，來探索指定的事件名稱的事件。</span><span class="sxs-lookup"><span data-stu-id="30300-142">For example, the generic class does more reflection to discover the event given the event's name.</span></span> <span data-ttu-id="30300-143">此外，程式碼以註冊事件，藉由使用泛型<xref:System.Windows.WeakEventManager%602>更詳細資訊，比使用現有或自訂<xref:System.Windows.WeakEventManager>。</span><span class="sxs-lookup"><span data-stu-id="30300-143">Also, the code to register the event by using the generic <xref:System.Windows.WeakEventManager%602> is more verbose than using an existing or custom <xref:System.Windows.WeakEventManager>.</span></span>|  
|<span data-ttu-id="30300-144">建立自訂的弱式事件管理員類別</span><span class="sxs-lookup"><span data-stu-id="30300-144">Create a custom weak event manager class</span></span>|<span data-ttu-id="30300-145">建立自訂<xref:System.Windows.WeakEventManager>時的現有<xref:System.Windows.WeakEventManager>不提供，而且您想最佳的效率。</span><span class="sxs-lookup"><span data-stu-id="30300-145">Create a custom <xref:System.Windows.WeakEventManager> when an existing <xref:System.Windows.WeakEventManager> is not available and you want the best efficiency.</span></span> <span data-ttu-id="30300-146">使用自訂<xref:System.Windows.WeakEventManager>訂閱事件將會更有效率，但是否會負擔撰寫更多的程式碼開頭的成本。</span><span class="sxs-lookup"><span data-stu-id="30300-146">Using a custom <xref:System.Windows.WeakEventManager> to subscribe to an event will be more efficient, but you do incur the cost of writing more code at the beginning.</span></span>|  
|<span data-ttu-id="30300-147">使用第三方弱式事件管理員</span><span class="sxs-lookup"><span data-stu-id="30300-147">Use a third-party weak event manager</span></span>|<span data-ttu-id="30300-148">NuGet 已[幾個弱式事件管理員](https://www.nuget.org/packages?q=weak+event+manager&prerel=false)許多 WPF 架構還支援模式 (比方說，請參閱[Prism 的鬆散偶合的事件訂用帳戶上的文件](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events))。</span><span class="sxs-lookup"><span data-stu-id="30300-148">NuGet has [several weak event managers](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) and many WPF frameworks also support the pattern (for instance, see [Prism's documentation on loosely coupled event subscription](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)).</span></span>|

 <span data-ttu-id="30300-149">下列各節說明如何實作弱式事件模式。</span><span class="sxs-lookup"><span data-stu-id="30300-149">The following sections describe how to implement the weak event pattern.</span></span>  <span data-ttu-id="30300-150">基於本文的討論，要訂閱事件具有下列特性。</span><span class="sxs-lookup"><span data-stu-id="30300-150">For purposes of this discussion, the event to subscribe to has the following characteristics.</span></span>  
  
- <span data-ttu-id="30300-151">事件名稱是`SomeEvent`。</span><span class="sxs-lookup"><span data-stu-id="30300-151">The event name is `SomeEvent`.</span></span>  
  
- <span data-ttu-id="30300-152">引發事件`EventSource`類別。</span><span class="sxs-lookup"><span data-stu-id="30300-152">The event is raised by the `EventSource` class.</span></span>  
  
- <span data-ttu-id="30300-153">事件處理常式都已型別： `SomeEventEventHandler` (或`EventHandler<SomeEventEventArgs>`)。</span><span class="sxs-lookup"><span data-stu-id="30300-153">The event handler has type: `SomeEventEventHandler` (or `EventHandler<SomeEventEventArgs>`).</span></span>  
  
- <span data-ttu-id="30300-154">這個事件會傳遞為參數的型別`SomeEventEventArgs`的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="30300-154">The event passes a parameter of type `SomeEventEventArgs` to the event handlers.</span></span>  
  
### <a name="using-an-existing-weak-event-manager-class"></a><span data-ttu-id="30300-155">使用現有的弱式事件管理員類別</span><span class="sxs-lookup"><span data-stu-id="30300-155">Using an Existing Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="30300-156">尋找現有的弱式事件管理員。</span><span class="sxs-lookup"><span data-stu-id="30300-156">Find an existing weak event manager.</span></span>  
  
     <span data-ttu-id="30300-157">WPF 隨附的弱式事件管理員的清單，請參閱中的繼承階層<xref:System.Windows.WeakEventManager>類別。</span><span class="sxs-lookup"><span data-stu-id="30300-157">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
2. <span data-ttu-id="30300-158">使用新的弱式事件管理員，而不是一般事件連結。</span><span class="sxs-lookup"><span data-stu-id="30300-158">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="30300-159">例如，如果您的程式碼使用下列模式來訂閱事件：</span><span class="sxs-lookup"><span data-stu-id="30300-159">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="30300-160">請將它變更為下列模式：</span><span class="sxs-lookup"><span data-stu-id="30300-160">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="30300-161">同樣地，如果您的程式碼使用下列模式來取消訂閱事件：</span><span class="sxs-lookup"><span data-stu-id="30300-161">Similarly, if your code uses the following pattern to unsubscribe from an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="30300-162">請將它變更為下列模式：</span><span class="sxs-lookup"><span data-stu-id="30300-162">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a><span data-ttu-id="30300-163">使用泛型的弱式事件管理員類別</span><span class="sxs-lookup"><span data-stu-id="30300-163">Using the Generic Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="30300-164">使用泛型<xref:System.Windows.WeakEventManager%602>類別而不是一般事件連結。</span><span class="sxs-lookup"><span data-stu-id="30300-164">Use the generic <xref:System.Windows.WeakEventManager%602> class instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="30300-165">當您使用<xref:System.Windows.WeakEventManager%602>若要註冊事件接聽程式，您會提供事件來源與<xref:System.EventArgs>型別做為型別參數至類別，並呼叫<xref:System.Windows.WeakEventManager%602.AddHandler%2A>如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="30300-165">When you use <xref:System.Windows.WeakEventManager%602> to register event listeners, you supply the event source and <xref:System.EventArgs> type as the type parameters to the class and call <xref:System.Windows.WeakEventManager%602.AddHandler%2A> as shown in the following code:</span></span>  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a><span data-ttu-id="30300-166">建立自訂的弱式事件管理員類別</span><span class="sxs-lookup"><span data-stu-id="30300-166">Creating a Custom Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="30300-167">將下列類別範本複製到您的專案中。</span><span class="sxs-lookup"><span data-stu-id="30300-167">Copy the following class template to your project.</span></span>  
  
     <span data-ttu-id="30300-168">這個類別繼承自<xref:System.Windows.WeakEventManager>類別。</span><span class="sxs-lookup"><span data-stu-id="30300-168">This class inherits from the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. <span data-ttu-id="30300-169">取代`SomeEventWeakEventManager`名稱與您自己的名稱。</span><span class="sxs-lookup"><span data-stu-id="30300-169">Replace the `SomeEventWeakEventManager` name with your own name.</span></span>  
  
3. <span data-ttu-id="30300-170">取代為您的活動相對應的名稱與先前所述的三個名稱。</span><span class="sxs-lookup"><span data-stu-id="30300-170">Replace the three names described previously with the corresponding names for your event.</span></span> <span data-ttu-id="30300-171">(`SomeEvent`， `EventSource`，和`SomeEventEventArgs`)</span><span class="sxs-lookup"><span data-stu-id="30300-171">(`SomeEvent`, `EventSource`, and `SomeEventEventArgs`)</span></span>  
  
4. <span data-ttu-id="30300-172">若要為其所管理的事件相同的可視性設定弱式事件管理員類別的可視性 （公用 / 內部 / 私用）。</span><span class="sxs-lookup"><span data-stu-id="30300-172">Set the visibility (public / internal / private) of the weak event manager class to the same visibility as event it manages.</span></span>  
  
5. <span data-ttu-id="30300-173">使用新的弱式事件管理員，而不是一般事件連結。</span><span class="sxs-lookup"><span data-stu-id="30300-173">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="30300-174">例如，如果您的程式碼使用下列模式來訂閱事件：</span><span class="sxs-lookup"><span data-stu-id="30300-174">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="30300-175">請將它變更為下列模式：</span><span class="sxs-lookup"><span data-stu-id="30300-175">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="30300-176">同樣地，如果您的程式碼使用下列模式來取消訂閱事件：</span><span class="sxs-lookup"><span data-stu-id="30300-176">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="30300-177">請將它變更為下列模式：</span><span class="sxs-lookup"><span data-stu-id="30300-177">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="30300-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30300-178">See also</span></span>

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [<span data-ttu-id="30300-179">路由事件概觀</span><span class="sxs-lookup"><span data-stu-id="30300-179">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="30300-180">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="30300-180">Data Binding Overview</span></span>](../data/data-binding-overview.md)
