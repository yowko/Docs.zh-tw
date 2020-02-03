---
title: 事件設計
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
ms.openlocfilehash: b44ee5933f8629b4dddbf3be1b79b2e77b0254f7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741683"
---
# <a name="event-design"></a><span data-ttu-id="ec377-102">事件設計</span><span class="sxs-lookup"><span data-stu-id="ec377-102">Event Design</span></span>
<span data-ttu-id="ec377-103">事件是最常使用的回呼形式（可讓架構呼叫使用者程式碼的結構）。</span><span class="sxs-lookup"><span data-stu-id="ec377-103">Events are the most commonly used form of callbacks (constructs that allow the framework to call into user code).</span></span> <span data-ttu-id="ec377-104">其他回呼機制包含取得委派、虛擬成員和以介面為基礎之外掛程式的成員。來自可用性研究的資料表示大部分的開發人員都使用事件，而不是使用其他回呼機制.</span><span class="sxs-lookup"><span data-stu-id="ec377-104">Other callback mechanisms include members taking delegates, virtual members, and interface-based plug-ins. Data from usability studies indicate that the majority of developers are more comfortable using events than they are using the other callback mechanisms.</span></span> <span data-ttu-id="ec377-105">事件與 Visual Studio 和多種語言完美整合。</span><span class="sxs-lookup"><span data-stu-id="ec377-105">Events are nicely integrated with Visual Studio and many languages.</span></span>

 <span data-ttu-id="ec377-106">請務必注意，有兩個事件群組：在系統狀態變更之前引發的事件（稱為前置事件），以及狀態變更後引發的事件，稱為「後置事件」。</span><span class="sxs-lookup"><span data-stu-id="ec377-106">It is important to note that there are two groups of events: events raised before a state of the system changes, called pre-events, and events raised after a state changes, called post-events.</span></span> <span data-ttu-id="ec377-107">預先事件的範例會 `Form.Closing`，在表單關閉之前引發。</span><span class="sxs-lookup"><span data-stu-id="ec377-107">An example of a pre-event would be `Form.Closing`, which is raised before a form is closed.</span></span> <span data-ttu-id="ec377-108">Post 事件的範例會 `Form.Closed`，這會在表單關閉後引發。</span><span class="sxs-lookup"><span data-stu-id="ec377-108">An example of a post-event would be `Form.Closed`, which is raised after a form is closed.</span></span>

 <span data-ttu-id="ec377-109">✔️確實會針對事件使用「引發」一詞，而非「引發」或「觸發程式」。</span><span class="sxs-lookup"><span data-stu-id="ec377-109">✔️ DO use the term "raise" for events rather than "fire" or "trigger."</span></span>

 <span data-ttu-id="ec377-110">✔️確實使用 <xref:System.EventHandler%601?displayProperty=nameWithType>，而不是手動建立新的委派，以作為事件處理常式使用。</span><span class="sxs-lookup"><span data-stu-id="ec377-110">✔️ DO use <xref:System.EventHandler%601?displayProperty=nameWithType> instead of manually creating new delegates to be used as event handlers.</span></span>

 <span data-ttu-id="ec377-111">✔️考慮使用 <xref:System.EventArgs> 的子類別做為事件引數，除非您絕對確定事件永遠不需要將任何資料傳送至事件處理方法，在此情況下，您可以直接使用 `EventArgs` 類型。</span><span class="sxs-lookup"><span data-stu-id="ec377-111">✔️ CONSIDER using a subclass of <xref:System.EventArgs> as the event argument, unless you are absolutely sure the event will never need to carry any data to the event handling method, in which case you can use the `EventArgs` type directly.</span></span>

 <span data-ttu-id="ec377-112">如果您使用 `EventArgs` 直接寄送 API，您永遠都無法在不中斷相容性的情況下，新增任何要攜帶事件的資料。</span><span class="sxs-lookup"><span data-stu-id="ec377-112">If you ship an API using `EventArgs` directly, you will never be able to add any data to be carried with the event without breaking compatibility.</span></span> <span data-ttu-id="ec377-113">如果您使用子類別，即使一開始完全空白，您也可以在需要時將屬性新增至子類別。</span><span class="sxs-lookup"><span data-stu-id="ec377-113">If you use a subclass, even if initially completely empty, you will be able to add properties to the subclass when needed.</span></span>

 <span data-ttu-id="ec377-114">✔️確實使用受保護的虛擬方法來引發每個事件。</span><span class="sxs-lookup"><span data-stu-id="ec377-114">✔️ DO use a protected virtual method to raise each event.</span></span> <span data-ttu-id="ec377-115">這只適用于未密封類別上的非靜態事件，而不適用於結構、密封類別或靜態事件。</span><span class="sxs-lookup"><span data-stu-id="ec377-115">This is only applicable to nonstatic events on unsealed classes, not to structs, sealed classes, or static events.</span></span>

 <span data-ttu-id="ec377-116">方法的目的是要提供方法，讓衍生類別使用覆寫來處理事件。</span><span class="sxs-lookup"><span data-stu-id="ec377-116">The purpose of the method is to provide a way for a derived class to handle the event using an override.</span></span> <span data-ttu-id="ec377-117">覆寫是更有彈性、更快速且更自然的方式來處理衍生類別中的基類事件。</span><span class="sxs-lookup"><span data-stu-id="ec377-117">Overriding is a more flexible, faster, and more natural way to handle base class events in derived classes.</span></span> <span data-ttu-id="ec377-118">依照慣例，方法名稱的開頭應該是 "On"，後面接著事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="ec377-118">By convention, the name of the method should start with "On" and be followed with the name of the event.</span></span>

 <span data-ttu-id="ec377-119">衍生的類別可以選擇不要在其覆寫中呼叫方法的基底實作為。</span><span class="sxs-lookup"><span data-stu-id="ec377-119">The derived class can choose not to call the base implementation of the method in its override.</span></span> <span data-ttu-id="ec377-120">請不要在基類所需的方法中包含任何處理，就可以正確地運作。</span><span class="sxs-lookup"><span data-stu-id="ec377-120">Be prepared for this by not including any processing in the method that is required for the base class to work correctly.</span></span>

 <span data-ttu-id="ec377-121">✔️請對引發事件的受保護方法執行一個參數。</span><span class="sxs-lookup"><span data-stu-id="ec377-121">✔️ DO take one parameter to the protected method that raises an event.</span></span>

 <span data-ttu-id="ec377-122">參數應該命名為 `e`，且應輸入為事件引數類別。</span><span class="sxs-lookup"><span data-stu-id="ec377-122">The parameter should be named `e` and should be typed as the event argument class.</span></span>

 <span data-ttu-id="ec377-123">當引發非靜態事件時，❌ 不要傳遞 null 做為寄件者。</span><span class="sxs-lookup"><span data-stu-id="ec377-123">❌ DO NOT pass null as the sender when raising a nonstatic event.</span></span>

 <span data-ttu-id="ec377-124">✔️在引發靜態事件時，傳遞 null 做為寄件者。</span><span class="sxs-lookup"><span data-stu-id="ec377-124">✔️ DO pass null as the sender when raising a static event.</span></span>

 <span data-ttu-id="ec377-125">當引發事件時，❌ 不會傳遞 null 做為事件資料參數。</span><span class="sxs-lookup"><span data-stu-id="ec377-125">❌ DO NOT pass null as the event data parameter when raising an event.</span></span>

 <span data-ttu-id="ec377-126">如果您不想要將任何資料傳遞至事件處理方法，則應該傳遞 `EventArgs.Empty`。</span><span class="sxs-lookup"><span data-stu-id="ec377-126">You should pass `EventArgs.Empty` if you don’t want to pass any data to the event handling method.</span></span> <span data-ttu-id="ec377-127">開發人員預期此參數不是 null。</span><span class="sxs-lookup"><span data-stu-id="ec377-127">Developers expect this parameter not to be null.</span></span>

 <span data-ttu-id="ec377-128">✔️考慮引發終端使用者可以取消的事件。</span><span class="sxs-lookup"><span data-stu-id="ec377-128">✔️ CONSIDER raising events that the end user can cancel.</span></span> <span data-ttu-id="ec377-129">這只適用于前置事件。</span><span class="sxs-lookup"><span data-stu-id="ec377-129">This only applies to pre-events.</span></span>

 <span data-ttu-id="ec377-130">使用 <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> 或其子類別做為事件引數，以允許終端使用者取消事件。</span><span class="sxs-lookup"><span data-stu-id="ec377-130">Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> or its subclass as the event argument to allow the end user to cancel events.</span></span>

### <a name="custom-event-handler-design"></a><span data-ttu-id="ec377-131">自訂事件處理常式設計</span><span class="sxs-lookup"><span data-stu-id="ec377-131">Custom Event Handler Design</span></span>
 <span data-ttu-id="ec377-132">在某些情況下，`EventHandler<T>` 無法使用，例如，當架構需要使用舊版 CLR 時，這不支援泛型。</span><span class="sxs-lookup"><span data-stu-id="ec377-132">There are cases in which `EventHandler<T>` cannot be used, such as when the framework needs to work with earlier versions of the CLR, which did not support Generics.</span></span> <span data-ttu-id="ec377-133">在這種情況下，您可能需要設計和開發自訂事件處理常式委派。</span><span class="sxs-lookup"><span data-stu-id="ec377-133">In such cases, you might need to design and develop a custom event handler delegate.</span></span>

 <span data-ttu-id="ec377-134">✔️針對事件處理常式使用 void 的傳回類型。</span><span class="sxs-lookup"><span data-stu-id="ec377-134">✔️ DO use a return type of void for event handlers.</span></span>

 <span data-ttu-id="ec377-135">事件處理常式可以叫用多個事件處理方法，可能會在多個物件上叫用。</span><span class="sxs-lookup"><span data-stu-id="ec377-135">An event handler can invoke multiple event handling methods, possibly on multiple objects.</span></span> <span data-ttu-id="ec377-136">如果允許事件處理方法傳回值，每個事件調用都會有多個傳回值。</span><span class="sxs-lookup"><span data-stu-id="ec377-136">If event handling methods were allowed to return a value, there would be multiple return values for each event invocation.</span></span>

 <span data-ttu-id="ec377-137">✔️確實使用 `object` 做為事件處理常式第一個參數的型別，並將它呼叫 `sender`。</span><span class="sxs-lookup"><span data-stu-id="ec377-137">✔️ DO use `object` as the type of the first parameter of the event handler, and call it `sender`.</span></span>

 <span data-ttu-id="ec377-138">✔️確實使用 <xref:System.EventArgs?displayProperty=nameWithType> 或其子類別做為事件處理常式第二個參數的型別，並將它呼叫 `e`。</span><span class="sxs-lookup"><span data-stu-id="ec377-138">✔️ DO use <xref:System.EventArgs?displayProperty=nameWithType> or its subclass as the type of the second parameter of the event handler, and call it `e`.</span></span>

 <span data-ttu-id="ec377-139">❌ 在事件處理常式上不能有兩個以上的參數。</span><span class="sxs-lookup"><span data-stu-id="ec377-139">❌ DO NOT have more than two parameters on event handlers.</span></span>

 <span data-ttu-id="ec377-140">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="ec377-140">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="ec377-141">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition[ 節錄。](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)*</span><span class="sxs-lookup"><span data-stu-id="ec377-141">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ec377-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec377-142">See also</span></span>

- [<span data-ttu-id="ec377-143">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="ec377-143">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="ec377-144">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="ec377-144">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
