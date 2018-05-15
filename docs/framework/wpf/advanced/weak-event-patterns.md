---
title: 弱式事件模式
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: 4b1e8649e5d550ffa2c7ee614cb9102f86a83ff8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="weak-event-patterns"></a><span data-ttu-id="6711e-102">弱式事件模式</span><span class="sxs-lookup"><span data-stu-id="6711e-102">Weak Event Patterns</span></span>
<span data-ttu-id="6711e-103">在應用程式，它可能會附加到事件來源的處理常式不會終結搭配此處理常式附加到來源的接聽程式物件。</span><span class="sxs-lookup"><span data-stu-id="6711e-103">In applications, it is possible that handlers that are attached to event sources will not be destroyed in coordination with the listener object that attached the handler to the source.</span></span> <span data-ttu-id="6711e-104">這種情況可能會導致記憶體流失無關。</span><span class="sxs-lookup"><span data-stu-id="6711e-104">This situation can lead to memory leaks.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="6711e-105"> 導入了可用來解決這個問題，提供專用的管理員類別的特定事件，該事件的接聽項上實作介面的設計模式。</span><span class="sxs-lookup"><span data-stu-id="6711e-105"> introduces a design pattern that can be used to address this issue, by providing a dedicated manager class for particular events and implementing an interface on listeners for that event.</span></span> <span data-ttu-id="6711e-106">此設計模式又稱為*弱式事件模式*。</span><span class="sxs-lookup"><span data-stu-id="6711e-106">This design pattern is known as the *weak event pattern*.</span></span>  
  
## <a name="why-implement-the-weak-event-pattern"></a><span data-ttu-id="6711e-107">為什麼實作弱式事件模式？</span><span class="sxs-lookup"><span data-stu-id="6711e-107">Why Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="6711e-108">接聽事件可能會導致記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="6711e-108">Listening for events can lead to memory leaks.</span></span> <span data-ttu-id="6711e-109">接聽事件的典型技巧是使用附加至來源上的事件處理常式的特定語言的語法。</span><span class="sxs-lookup"><span data-stu-id="6711e-109">The typical technique for listening to an event is to use the language-specific syntax that attaches a handler to an event on a source.</span></span> <span data-ttu-id="6711e-110">例如，在 C# 中，該語法是： `source.SomeEvent += new SomeEventHandler(MyEventHandler)`。</span><span class="sxs-lookup"><span data-stu-id="6711e-110">For example, in C#, that syntax is: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span></span>  
  
 <span data-ttu-id="6711e-111">這項技術建立的事件接聽程式從事件來源的強式參考。</span><span class="sxs-lookup"><span data-stu-id="6711e-111">This technique creates a strong reference from the event source to the event listener.</span></span> <span data-ttu-id="6711e-112">一般來說，附加事件處理常式，接聽程式會導致物件存留期 （除非明確移除事件處理常式），會受到來源的物件存留期，接聽程式。</span><span class="sxs-lookup"><span data-stu-id="6711e-112">Ordinarily, attaching an event handler for a listener causes the listener to have an object lifetime that is influenced by the object lifetime of the source (unless the event handler is explicitly removed).</span></span> <span data-ttu-id="6711e-113">但在某些情況下，您可能想物件存留期的接聽程式會由其他因素，例如是否目前屬於應用程式，而不是由來源的存留期的視覺化樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="6711e-113">But in certain circumstances, you might want the object lifetime of the listener to be controlled by other factors, such as whether it currently belongs to the visual tree of the application, and not by the lifetime of the source.</span></span> <span data-ttu-id="6711e-114">一般事件模式時的來源物件存留期超出接聽程式的物件存留期時，會導致記憶體流失： 接聽程式就會保持運作時間比預期長。</span><span class="sxs-lookup"><span data-stu-id="6711e-114">Whenever the source object lifetime extends beyond the object lifetime of the listener, the normal event pattern leads to a memory leak: the listener is kept alive longer than intended.</span></span>  
  
 <span data-ttu-id="6711e-115">弱式事件模式是設計用來解決此記憶體流失問題。</span><span class="sxs-lookup"><span data-stu-id="6711e-115">The weak event pattern is designed to solve this memory leak problem.</span></span> <span data-ttu-id="6711e-116">每當需要註冊事件接聽程式，但是接聽程式無法明確知道何時要取消註冊時，可以使用弱式事件模式。</span><span class="sxs-lookup"><span data-stu-id="6711e-116">The weak event pattern can be used whenever a listener needs to register for an event, but the listener does not explicitly know when to unregister.</span></span> <span data-ttu-id="6711e-117">來源的物件存留期超過有用的物件存留期的接聽程式時，也可以使用弱式事件模式。</span><span class="sxs-lookup"><span data-stu-id="6711e-117">The weak event pattern can also be used whenever the object lifetime of the source exceeds the useful object lifetime of the listener.</span></span> <span data-ttu-id="6711e-118">(在此情況下，*有用*由您決定。)弱式事件模式可讓要註冊，且不會影響物件存留期的特性以任何方式接聽程式接收到事件的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="6711e-118">(In this case, *useful* is determined by you.) The weak event pattern allows the listener to register for and receive the event without affecting the object lifetime characteristics of the listener in any way.</span></span> <span data-ttu-id="6711e-119">作用中，從來源的隱含的參考不會判斷是否接聽程式都可進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="6711e-119">In effect, the implied reference from the source does not determine whether the listener is eligible for garbage collection.</span></span> <span data-ttu-id="6711e-120">參考是弱式參考，因此命名的弱式事件模式和相關[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6711e-120">The reference is a weak reference, thus the naming of the weak event pattern and the related [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)].</span></span> <span data-ttu-id="6711e-121">接聽程式可以是記憶體回收或其他方式終結，和來源可以繼續，但不保留不可回收處理常式現在已終結物件參考。</span><span class="sxs-lookup"><span data-stu-id="6711e-121">The listener can be garbage collected or otherwise destroyed, and the source can continue without retaining noncollectible handler references to a now destroyed object.</span></span>  
  
## <a name="who-should-implement-the-weak-event-pattern"></a><span data-ttu-id="6711e-122">人員應該實作弱式事件模式？</span><span class="sxs-lookup"><span data-stu-id="6711e-122">Who Should Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="6711e-123">實作弱式事件模式有趣的是主要用於控制項作者。</span><span class="sxs-lookup"><span data-stu-id="6711e-123">Implementing the weak event pattern is interesting primarily for control authors.</span></span> <span data-ttu-id="6711e-124">控制項的作者，會負責的行為與您的控制項及插入它的應用程式之影響的內含項目。</span><span class="sxs-lookup"><span data-stu-id="6711e-124">As a control author, you are largely responsible for the behavior and containment of your control and the impact it has on applications in which it is inserted.</span></span> <span data-ttu-id="6711e-125">這包括控制項物件存留期行為，特別是描述的記憶體流失問題的處理。</span><span class="sxs-lookup"><span data-stu-id="6711e-125">This includes the control object lifetime behavior, in particular the handling of the described memory leak problem.</span></span>  
  
 <span data-ttu-id="6711e-126">某些情況下原本就是應用程式為自己弱式事件模式的應用程式。</span><span class="sxs-lookup"><span data-stu-id="6711e-126">Certain scenarios inherently lend themselves to the application of the weak event pattern.</span></span> <span data-ttu-id="6711e-127">這類案例之一是資料繫結。</span><span class="sxs-lookup"><span data-stu-id="6711e-127">One such scenario is data binding.</span></span> <span data-ttu-id="6711e-128">在資料繫結，是很常見的來源物件變成完全獨立的接聽程式物件，因為它是繫結的目標。</span><span class="sxs-lookup"><span data-stu-id="6711e-128">In data binding, it is common for the source object to be completely independent of the listener object, which is a target of a binding.</span></span> <span data-ttu-id="6711e-129">許多層面[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]資料繫結已經具有弱式事件模式中事件的實作方式套用。</span><span class="sxs-lookup"><span data-stu-id="6711e-129">Many aspects of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] data binding already have the weak event pattern applied in how the events are implemented.</span></span>  
  
## <a name="how-to-implement-the-weak-event-pattern"></a><span data-ttu-id="6711e-130">如何實作弱式事件模式</span><span class="sxs-lookup"><span data-stu-id="6711e-130">How to Implement the Weak Event Pattern</span></span>  
 <span data-ttu-id="6711e-131">有三種方式來實作弱式事件模式。</span><span class="sxs-lookup"><span data-stu-id="6711e-131">There are three ways to implement weak event pattern.</span></span> <span data-ttu-id="6711e-132">下表列出這三種方法，並提供一些您應該何時使用每個的指引。</span><span class="sxs-lookup"><span data-stu-id="6711e-132">The following table lists the three approaches and provides some guidance for when you should use each.</span></span>  
  
|<span data-ttu-id="6711e-133">方法</span><span class="sxs-lookup"><span data-stu-id="6711e-133">Approach</span></span>|<span data-ttu-id="6711e-134">何時實作</span><span class="sxs-lookup"><span data-stu-id="6711e-134">When to Implement</span></span>|  
|--------------|-----------------------|  
|<span data-ttu-id="6711e-135">使用現有的弱式事件管理員類別</span><span class="sxs-lookup"><span data-stu-id="6711e-135">Use an existing weak event manager class</span></span>|<span data-ttu-id="6711e-136">如果您想要訂閱的事件都有對應<xref:System.Windows.WeakEventManager>，使用現有的弱式事件管理員。</span><span class="sxs-lookup"><span data-stu-id="6711e-136">If the event you want to subscribe to has a corresponding <xref:System.Windows.WeakEventManager>, use the existing weak event manager.</span></span> <span data-ttu-id="6711e-137">如需包含 WPF 的弱式事件管理員的清單，請參閱中的繼承階層<xref:System.Windows.WeakEventManager>類別。</span><span class="sxs-lookup"><span data-stu-id="6711e-137">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span> <span data-ttu-id="6711e-138">不過，請注意，有相對較少的弱式事件管理員隨附的 WPF 中，因此您可能需要選擇其中一種其他方法。</span><span class="sxs-lookup"><span data-stu-id="6711e-138">Note, however, that there are relatively few weak event managers that are included with WPF, so you will probably need to choose one of the other approaches.</span></span>|  
|<span data-ttu-id="6711e-139">使用一般的弱式事件管理員類別</span><span class="sxs-lookup"><span data-stu-id="6711e-139">Use a generic weak event manager class</span></span>|<span data-ttu-id="6711e-140">使用泛型<xref:System.Windows.WeakEventManager%602>時的現有<xref:System.Windows.WeakEventManager>無法使用，您想要輕鬆地實作，而且您不擔心效率。</span><span class="sxs-lookup"><span data-stu-id="6711e-140">Use a generic <xref:System.Windows.WeakEventManager%602> when an existing <xref:System.Windows.WeakEventManager> is not available, you want an easy way to implement, and you are not concerned about efficiency.</span></span> <span data-ttu-id="6711e-141">泛型<xref:System.Windows.WeakEventManager%602>比現有或自訂的弱式事件管理員比較沒有效率。</span><span class="sxs-lookup"><span data-stu-id="6711e-141">The generic <xref:System.Windows.WeakEventManager%602> is less efficient than an existing or custom weak event manager.</span></span> <span data-ttu-id="6711e-142">例如，泛型類別會詳細反映來探索事件指定事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="6711e-142">For example, the generic class does more reflection to discover the event given the event's name.</span></span> <span data-ttu-id="6711e-143">此外，程式碼以使用泛型來註冊事件<xref:System.Windows.WeakEventManager%602>更詳細資訊，比使用的現有或自訂<xref:System.Windows.WeakEventManager>。</span><span class="sxs-lookup"><span data-stu-id="6711e-143">Also, the code to register the event by using the generic <xref:System.Windows.WeakEventManager%602> is more verbose than using an existing or custom <xref:System.Windows.WeakEventManager>.</span></span>|  
|<span data-ttu-id="6711e-144">建立自訂的弱式事件管理員類別</span><span class="sxs-lookup"><span data-stu-id="6711e-144">Create a custom weak event manager class</span></span>|<span data-ttu-id="6711e-145">建立自訂<xref:System.Windows.WeakEventManager>時的現有<xref:System.Windows.WeakEventManager>不提供，而且您想最佳的效率。</span><span class="sxs-lookup"><span data-stu-id="6711e-145">Create a custom <xref:System.Windows.WeakEventManager> when an existing <xref:System.Windows.WeakEventManager> is not available and you want the best efficiency.</span></span> <span data-ttu-id="6711e-146">使用自訂<xref:System.Windows.WeakEventManager>來訂閱事件將會更有效率，但您沒有承受撰寫更多的程式碼開頭的成本。</span><span class="sxs-lookup"><span data-stu-id="6711e-146">Using a custom <xref:System.Windows.WeakEventManager> to subscribe to an event will be more efficient, but you do incur the cost of writing more code at the beginning.</span></span>|  
  
 <span data-ttu-id="6711e-147">下列章節說明如何實作弱式事件模式。</span><span class="sxs-lookup"><span data-stu-id="6711e-147">The following sections describe how to implement the weak event pattern.</span></span>  <span data-ttu-id="6711e-148">基於本討論內容的詳細資訊，來訂閱事件具有下列特性。</span><span class="sxs-lookup"><span data-stu-id="6711e-148">For purposes of this discussion, the event to subscribe to has the following characteristics.</span></span>  
  
-   <span data-ttu-id="6711e-149">事件名稱`SomeEvent`。</span><span class="sxs-lookup"><span data-stu-id="6711e-149">The event name is `SomeEvent`.</span></span>  
  
-   <span data-ttu-id="6711e-150">引發事件`EventSource`類別。</span><span class="sxs-lookup"><span data-stu-id="6711e-150">The event is raised by the `EventSource` class.</span></span>  
  
-   <span data-ttu-id="6711e-151">此事件處理常式有型別： `SomeEventEventHandler` (或`EventHandler<SomeEventEventArgs>`)。</span><span class="sxs-lookup"><span data-stu-id="6711e-151">The event handler has type: `SomeEventEventHandler` (or `EventHandler<SomeEventEventArgs>`).</span></span>  
  
-   <span data-ttu-id="6711e-152">這個事件會傳遞的型別參數`SomeEventEventArgs`的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="6711e-152">The event passes a parameter of type `SomeEventEventArgs` to the event handlers.</span></span>  
  
### <a name="using-an-existing-weak-event-manager-class"></a><span data-ttu-id="6711e-153">使用現有的弱式事件管理員類別</span><span class="sxs-lookup"><span data-stu-id="6711e-153">Using an Existing Weak Event Manager Class</span></span>  
  
1.  <span data-ttu-id="6711e-154">管理員尋找現有的弱式事件。</span><span class="sxs-lookup"><span data-stu-id="6711e-154">Find an existing weak event manager.</span></span>  
  
     <span data-ttu-id="6711e-155">如需包含 WPF 的弱式事件管理員的清單，請參閱中的繼承階層<xref:System.Windows.WeakEventManager>類別。</span><span class="sxs-lookup"><span data-stu-id="6711e-155">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
2.  <span data-ttu-id="6711e-156">使用新的弱式事件管理員，而不是一般事件連結。</span><span class="sxs-lookup"><span data-stu-id="6711e-156">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="6711e-157">例如，如果您的程式碼使用下列模式來訂閱事件：</span><span class="sxs-lookup"><span data-stu-id="6711e-157">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="6711e-158">請將它變更為下列模式：</span><span class="sxs-lookup"><span data-stu-id="6711e-158">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="6711e-159">同樣地，如果您的程式碼使用下列模式來取消訂閱事件：</span><span class="sxs-lookup"><span data-stu-id="6711e-159">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="6711e-160">請將它變更為下列模式：</span><span class="sxs-lookup"><span data-stu-id="6711e-160">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a><span data-ttu-id="6711e-161">使用泛型的弱式事件管理員類別</span><span class="sxs-lookup"><span data-stu-id="6711e-161">Using the Generic Weak Event Manager Class</span></span>  
  
1.  <span data-ttu-id="6711e-162">使用泛型<xref:System.Windows.WeakEventManager%602>類別而不是一般事件連結。</span><span class="sxs-lookup"><span data-stu-id="6711e-162">Use the generic <xref:System.Windows.WeakEventManager%602> class instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="6711e-163">當您使用<xref:System.Windows.WeakEventManager%602>註冊事件接聽程式，您會提供事件來源和<xref:System.EventArgs>做為類別，然後呼叫型別參數的型別<xref:System.Windows.WeakEventManager%602.AddHandler%2A>如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="6711e-163">When you use <xref:System.Windows.WeakEventManager%602> to register event listeners, you supply the event source and <xref:System.EventArgs> type as the type parameters to the class and call <xref:System.Windows.WeakEventManager%602.AddHandler%2A> as shown in the following code:</span></span>  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a><span data-ttu-id="6711e-164">建立自訂的弱式事件管理員類別</span><span class="sxs-lookup"><span data-stu-id="6711e-164">Creating a Custom Weak Event Manager Class</span></span>  
  
1.  <span data-ttu-id="6711e-165">將下列類別範本複製到您的專案。</span><span class="sxs-lookup"><span data-stu-id="6711e-165">Copy the following class template to your project.</span></span>  
  
     <span data-ttu-id="6711e-166">此類別繼承自<xref:System.Windows.WeakEventManager>類別。</span><span class="sxs-lookup"><span data-stu-id="6711e-166">This class inherits from the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2.  <span data-ttu-id="6711e-167">取代`SomeEventWeakEventManager`名稱與您自己的名稱。</span><span class="sxs-lookup"><span data-stu-id="6711e-167">Replace the `SomeEventWeakEventManager` name with your own name.</span></span>  
  
3.  <span data-ttu-id="6711e-168">取代對應事件的名稱與先前所述的三個名稱。</span><span class="sxs-lookup"><span data-stu-id="6711e-168">Replace the three names described previously with the corresponding names for your event.</span></span> <span data-ttu-id="6711e-169">(`SomeEvent`， `EventSource`，和`SomeEventEventArgs`)</span><span class="sxs-lookup"><span data-stu-id="6711e-169">(`SomeEvent`, `EventSource`, and `SomeEventEventArgs`)</span></span>  
  
4.  <span data-ttu-id="6711e-170">設為其所管理的事件相同的可見性的可見性 （公用 / 內部 / 私用） 弱式事件管理員類別。</span><span class="sxs-lookup"><span data-stu-id="6711e-170">Set the visibility (public / internal / private) of the weak event manager class to the same visibility as event it manages.</span></span>  
  
5.  <span data-ttu-id="6711e-171">使用新的弱式事件管理員，而不是一般事件連結。</span><span class="sxs-lookup"><span data-stu-id="6711e-171">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="6711e-172">例如，如果您的程式碼使用下列模式來訂閱事件：</span><span class="sxs-lookup"><span data-stu-id="6711e-172">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="6711e-173">請將它變更為下列模式：</span><span class="sxs-lookup"><span data-stu-id="6711e-173">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="6711e-174">同樣地，如果您的程式碼使用下列模式來取消訂閱事件：</span><span class="sxs-lookup"><span data-stu-id="6711e-174">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="6711e-175">請將它變更為下列模式：</span><span class="sxs-lookup"><span data-stu-id="6711e-175">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6711e-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6711e-176">See Also</span></span>  
 <xref:System.Windows.WeakEventManager>  
 <xref:System.Windows.IWeakEventListener>  
 [<span data-ttu-id="6711e-177">路由事件概觀</span><span class="sxs-lookup"><span data-stu-id="6711e-177">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="6711e-178">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="6711e-178">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
