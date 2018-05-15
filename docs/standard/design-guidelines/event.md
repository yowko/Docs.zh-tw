---
title: 事件設計
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 48d1ad0f02ae34675c0a910d7651d718c060db60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="event-design"></a><span data-ttu-id="3127e-102">事件設計</span><span class="sxs-lookup"><span data-stu-id="3127e-102">Event Design</span></span>
<span data-ttu-id="3127e-103">事件是最常使用的回呼 （允許呼叫使用者程式碼架構的建構） 形式。</span><span class="sxs-lookup"><span data-stu-id="3127e-103">Events are the most commonly used form of callbacks (constructs that allow the framework to call into user code).</span></span> <span data-ttu-id="3127e-104">其他的回撥機制包括委派、 虛擬成員和介面為基礎的外掛程式取得的成員。資料可用性研究表示大部分的開發人員可以更輕鬆地使用事件，比使用其他的回撥機制。</span><span class="sxs-lookup"><span data-stu-id="3127e-104">Other callback mechanisms include members taking delegates, virtual members, and interface-based plug-ins. Data from usability studies indicate that the majority of developers are more comfortable using events than they are using the other callback mechanisms.</span></span> <span data-ttu-id="3127e-105">事件會正確地切割整合與 Visual Studio 和許多語言。</span><span class="sxs-lookup"><span data-stu-id="3127e-105">Events are nicely integrated with Visual Studio and many languages.</span></span>  
  
 <span data-ttu-id="3127e-106">請務必請注意，有兩個群組的事件： 狀態系統的變更，呼叫前的事件，以及之後的狀態變更時，引發的事件之前引發的事件呼叫後的事件。</span><span class="sxs-lookup"><span data-stu-id="3127e-106">It is important to note that there are two groups of events: events raised before a state of the system changes, called pre-events, and events raised after a state changes, called post-events.</span></span> <span data-ttu-id="3127e-107">預先事件的一個範例是`Form.Closing`，在關閉表單之前引發的。</span><span class="sxs-lookup"><span data-stu-id="3127e-107">An example of a pre-event would be `Form.Closing`, which is raised before a form is closed.</span></span> <span data-ttu-id="3127e-108">後續事件的一個範例是`Form.Closed`，表單關閉之後，這會引發。</span><span class="sxs-lookup"><span data-stu-id="3127e-108">An example of a post-event would be `Form.Closed`, which is raised after a form is closed.</span></span>  
  
 <span data-ttu-id="3127e-109">**✓ 不要**使用詞彙 「 引發 」 事件，而非 「 引發 」 或 「 觸發程序。 」</span><span class="sxs-lookup"><span data-stu-id="3127e-109">**✓ DO** use the term "raise" for events rather than "fire" or "trigger."</span></span>  
  
 <span data-ttu-id="3127e-110">**✓ 不要**使用<xref:System.EventHandler%601?displayProperty=nameWithType>而不是以手動方式建立新的委派來做為事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="3127e-110">**✓ DO** use <xref:System.EventHandler%601?displayProperty=nameWithType> instead of manually creating new delegates to be used as event handlers.</span></span>  
  
 <span data-ttu-id="3127e-111">**✓ 考慮**使用的子類別<xref:System.EventArgs>當做事件引數，除非您完全確定事件則不需要執行任何資料的事件處理方法，在這種情況下您可以使用`EventArgs`直接輸入。</span><span class="sxs-lookup"><span data-stu-id="3127e-111">**✓ CONSIDER** using a subclass of <xref:System.EventArgs> as the event argument, unless you are absolutely sure the event will never need to carry any data to the event handling method, in which case you can use the `EventArgs` type directly.</span></span>  
  
 <span data-ttu-id="3127e-112">如果您在出貨 API 使用`EventArgs`直接管理，您絕對不會再加入要執行與事件，而不會中斷相容性的任何資料。</span><span class="sxs-lookup"><span data-stu-id="3127e-112">If you ship an API using `EventArgs` directly, you will never be able to add any data to be carried with the event without breaking compatibility.</span></span> <span data-ttu-id="3127e-113">如果您使用子類別，即使如果一開始會完全空白的您將能夠將屬性加入至時所需的子類別。</span><span class="sxs-lookup"><span data-stu-id="3127e-113">If you use a subclass, even if initially completely empty, you will be able to add properties to the subclass when needed.</span></span>  
  
 <span data-ttu-id="3127e-114">**✓ 不要**用來引發的每個事件的受保護的虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="3127e-114">**✓ DO** use a protected virtual method to raise each event.</span></span> <span data-ttu-id="3127e-115">這只適用於未密封的類別、 結構、 密封的類別，或靜態事件上的非靜態事件。</span><span class="sxs-lookup"><span data-stu-id="3127e-115">This is only applicable to nonstatic events on unsealed classes, not to structs, sealed classes, or static events.</span></span>  
  
 <span data-ttu-id="3127e-116">方法的目的是要提供一個方式來處理事件使用覆寫衍生類別。</span><span class="sxs-lookup"><span data-stu-id="3127e-116">The purpose of the method is to provide a way for a derived class to handle the event using an override.</span></span> <span data-ttu-id="3127e-117">覆寫是更有彈性、 更快更自然的方式，來處理基底類別衍生類別中的事件。</span><span class="sxs-lookup"><span data-stu-id="3127e-117">Overriding is a more flexible, faster, and more natural way to handle base class events in derived classes.</span></span> <span data-ttu-id="3127e-118">依照慣例，方法名稱應以 「 On 」 開頭，且後面的事件名稱。</span><span class="sxs-lookup"><span data-stu-id="3127e-118">By convention, the name of the method should start with "On" and be followed with the name of the event.</span></span>  
  
 <span data-ttu-id="3127e-119">在衍生的類別不可以選擇在其覆寫中呼叫方法的基底實作。</span><span class="sxs-lookup"><span data-stu-id="3127e-119">The derived class can choose not to call the base implementation of the method in its override.</span></span> <span data-ttu-id="3127e-120">準備這個方法所需的正確運作的基底類別中不能包含任何處理。</span><span class="sxs-lookup"><span data-stu-id="3127e-120">Be prepared for this by not including any processing in the method that is required for the base class to work correctly.</span></span>  
  
 <span data-ttu-id="3127e-121">**✓ 不要**採用一個參數會引發事件的受保護方法。</span><span class="sxs-lookup"><span data-stu-id="3127e-121">**✓ DO** take one parameter to the protected method that raises an event.</span></span>  
  
 <span data-ttu-id="3127e-122">參數命名為`e`和輸入應該為事件引數類別。</span><span class="sxs-lookup"><span data-stu-id="3127e-122">The parameter should be named `e` and should be typed as the event argument class.</span></span>  
  
 <span data-ttu-id="3127e-123">**X 不**時引發的非靜態事件傳遞 null 做為傳送者。</span><span class="sxs-lookup"><span data-stu-id="3127e-123">**X DO NOT** pass null as the sender when raising a nonstatic event.</span></span>  
  
 <span data-ttu-id="3127e-124">**✓ 不要**時引發的靜態事件傳遞 null 做為傳送者。</span><span class="sxs-lookup"><span data-stu-id="3127e-124">**✓ DO** pass null as the sender when raising a static event.</span></span>  
  
 <span data-ttu-id="3127e-125">**X 不**時引發事件會傳遞 null 做為事件資料參數。</span><span class="sxs-lookup"><span data-stu-id="3127e-125">**X DO NOT** pass null as the event data parameter when raising an event.</span></span>  
  
 <span data-ttu-id="3127e-126">您應該傳遞`EventArgs.Empty`若不想將任何資料傳遞至事件處理方法。</span><span class="sxs-lookup"><span data-stu-id="3127e-126">You should pass `EventArgs.Empty` if you don’t want to pass any data to the event handling method.</span></span> <span data-ttu-id="3127e-127">開發人員希望此參數不可以是 null。</span><span class="sxs-lookup"><span data-stu-id="3127e-127">Developers expect this parameter not to be null.</span></span>  
  
 <span data-ttu-id="3127e-128">**✓ 考慮**引發事件，使用者可以取消。</span><span class="sxs-lookup"><span data-stu-id="3127e-128">**✓ CONSIDER** raising events that the end user can cancel.</span></span> <span data-ttu-id="3127e-129">這只適用於預先事件。</span><span class="sxs-lookup"><span data-stu-id="3127e-129">This only applies to pre-events.</span></span>  
  
 <span data-ttu-id="3127e-130">使用<xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType>或其為允許使用者在取消事件的事件引數的子類別。</span><span class="sxs-lookup"><span data-stu-id="3127e-130">Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> or its subclass as the event argument to allow the end user to cancel events.</span></span>  
  
### <a name="custom-event-handler-design"></a><span data-ttu-id="3127e-131">自訂事件處理常式設計</span><span class="sxs-lookup"><span data-stu-id="3127e-131">Custom Event Handler Design</span></span>  
 <span data-ttu-id="3127e-132">某些情況下，在其中`EventHandler<T>`無法使用，例如當架構需要使用較早版本的 CLR，因為不支援泛型。</span><span class="sxs-lookup"><span data-stu-id="3127e-132">There are cases in which `EventHandler<T>` cannot be used, such as when the framework needs to work with earlier versions of the CLR, which did not support Generics.</span></span> <span data-ttu-id="3127e-133">在這種情況下，您可能需要設計和開發自訂的事件處理常式委派。</span><span class="sxs-lookup"><span data-stu-id="3127e-133">In such cases, you might need to design and develop a custom event handler delegate.</span></span>  
  
 <span data-ttu-id="3127e-134">**✓ 不要**用於事件處理常式的傳回類型為 void。</span><span class="sxs-lookup"><span data-stu-id="3127e-134">**✓ DO** use a return type of void for event handlers.</span></span>  
  
 <span data-ttu-id="3127e-135">事件處理常式可以叫用多個事件處理常式方法，可能位於多個物件。</span><span class="sxs-lookup"><span data-stu-id="3127e-135">An event handler can invoke multiple event handling methods, possibly on multiple objects.</span></span> <span data-ttu-id="3127e-136">允許事件處理方法會傳回值，如果有多個傳回值，每個事件的引動過程。</span><span class="sxs-lookup"><span data-stu-id="3127e-136">If event handling methods were allowed to return a value, there would be multiple return values for each event invocation.</span></span>  
  
 <span data-ttu-id="3127e-137">**✓ 不要**使用`object`做為事件處理常式的第一個參數的類型，並為它`sender`。</span><span class="sxs-lookup"><span data-stu-id="3127e-137">**✓ DO** use `object` as the type of the first parameter of the event handler, and call it `sender`.</span></span>  
  
 <span data-ttu-id="3127e-138">**✓ 不要**使用<xref:System.EventArgs?displayProperty=nameWithType>或做為事件處理常式中，第二個參數的類型及其子類別，並為它`e`。</span><span class="sxs-lookup"><span data-stu-id="3127e-138">**✓ DO** use <xref:System.EventArgs?displayProperty=nameWithType> or its subclass as the type of the second parameter of the event handler, and call it `e`.</span></span>  
  
 <span data-ttu-id="3127e-139">**X 不**上事件處理常式有兩個以上的參數。</span><span class="sxs-lookup"><span data-stu-id="3127e-139">**X DO NOT** have more than two parameters on event handlers.</span></span>  
  
 <span data-ttu-id="3127e-140">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="3127e-140">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="3127e-141">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="3127e-141">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3127e-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3127e-142">See Also</span></span>  
 [<span data-ttu-id="3127e-143">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="3127e-143">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="3127e-144">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="3127e-144">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
