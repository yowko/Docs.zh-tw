---
title: "event (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
dev_langs:
- CSharp
helpviewer_keywords:
- event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
caps.latest.revision: 28
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: db9c558653904d81e0b73ec339e89f267b34a13b
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="event-c-reference"></a><span data-ttu-id="ad881-102">event (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="ad881-102">event (C# Reference)</span></span>
<span data-ttu-id="ad881-103">`event` 關鍵字用來在發行者類別中宣告事件。</span><span class="sxs-lookup"><span data-stu-id="ad881-103">The `event` keyword is used to declare an event in a publisher class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad881-104">範例</span><span class="sxs-lookup"><span data-stu-id="ad881-104">Example</span></span>  
 <span data-ttu-id="ad881-105">下例示範如何宣告及引發將 <xref:System.EventHandler> 用為基礎委派類型的事件。</span><span class="sxs-lookup"><span data-stu-id="ad881-105">The following example shows how to declare and raise an event that uses <xref:System.EventHandler> as the underlying delegate type.</span></span> <span data-ttu-id="ad881-106">如需也示範如何使用泛型 <xref:System.EventHandler%601> 委派類型，以及如何訂閱事件並建立事件處理常式方法的完整程式碼範例，請參閱[如何：發行符合 .NET Framework 方針的事件](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="ad881-106">For the complete code example that also shows how to use the generic <xref:System.EventHandler%601> delegate type and how to subscribe to an event and create an event handler method, see [How to: Publish Events that Conform to .NET Framework Guidelines](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).</span></span>  
  
 <span data-ttu-id="ad881-107">[!code-cs[csrefKeywordsModifiers#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/event_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ad881-107">[!code-cs[csrefKeywordsModifiers#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/event_1.cs)]</span></span>  
  
 <span data-ttu-id="ad881-108">事件是一種特殊的多點傳送委派，只能從宣告委派的類別或結構內叫用 (發行者類別)。</span><span class="sxs-lookup"><span data-stu-id="ad881-108">Events are a special kind of multicast delegate that can only be invoked from within the class or struct where they are declared (the publisher class).</span></span> <span data-ttu-id="ad881-109">如果其他類別或結構訂閱了事件，當發行者類別引發事件時，就會呼叫其事件處理常式方法。</span><span class="sxs-lookup"><span data-stu-id="ad881-109">If other classes or structs subscribe to the event, their event handler methods will be called when the publisher class raises the event.</span></span> <span data-ttu-id="ad881-110">如需詳細資訊與程式碼範例，請參閱[事件](../../../csharp/programming-guide/events/index.md)及[委派](../../../csharp/programming-guide/delegates/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ad881-110">For more information and code examples, see [Events](../../../csharp/programming-guide/events/index.md) and [Delegates](../../../csharp/programming-guide/delegates/index.md).</span></span>  
  
 <span data-ttu-id="ad881-111">事件可以標記為 [public](../../../csharp/language-reference/keywords/public.md)、[private](../../../csharp/language-reference/keywords/private.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md) 或 `protected``internal`。</span><span class="sxs-lookup"><span data-stu-id="ad881-111">Events can be marked as [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or `protected``internal`.</span></span> <span data-ttu-id="ad881-112">這些存取修飾詞定義類別使用者如何存取事件。</span><span class="sxs-lookup"><span data-stu-id="ad881-112">These access modifiers define how users of the class can access the event.</span></span> <span data-ttu-id="ad881-113">如需詳細資訊，請參閱[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="ad881-113">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
## <a name="keywords-and-events"></a><span data-ttu-id="ad881-114">關鍵字和事件</span><span class="sxs-lookup"><span data-stu-id="ad881-114">Keywords and Events</span></span>  
 <span data-ttu-id="ad881-115">下列關鍵字適用於事件。</span><span class="sxs-lookup"><span data-stu-id="ad881-115">The following keywords apply to events.</span></span>  
  
|<span data-ttu-id="ad881-116">關鍵字</span><span class="sxs-lookup"><span data-stu-id="ad881-116">Keyword</span></span>|<span data-ttu-id="ad881-117">描述</span><span class="sxs-lookup"><span data-stu-id="ad881-117">Description</span></span>|<span data-ttu-id="ad881-118">如需詳細資訊</span><span class="sxs-lookup"><span data-stu-id="ad881-118">For more information</span></span>|  
|-------------|-----------------|--------------------------|  
|[<span data-ttu-id="ad881-119">static</span><span class="sxs-lookup"><span data-stu-id="ad881-119">static</span></span>](../../../csharp/language-reference/keywords/static.md)|<span data-ttu-id="ad881-120">隨時向呼叫端提供事件，即使沒有任何類別執行個體存在。</span><span class="sxs-lookup"><span data-stu-id="ad881-120">Makes the event available to callers at any time, even if no instance of the class exists.</span></span>|[<span data-ttu-id="ad881-121">靜態類別和靜態類別成員</span><span class="sxs-lookup"><span data-stu-id="ad881-121">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|  
|[<span data-ttu-id="ad881-122">virtual</span><span class="sxs-lookup"><span data-stu-id="ad881-122">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)|<span data-ttu-id="ad881-123">允許衍生類別使用 [override](../../../csharp/language-reference/keywords/override.md) 關鍵字覆寫事件行為。</span><span class="sxs-lookup"><span data-stu-id="ad881-123">Allows derived classes to override the event behavior by using the [override](../../../csharp/language-reference/keywords/override.md) keyword.</span></span>|[<span data-ttu-id="ad881-124">繼承</span><span class="sxs-lookup"><span data-stu-id="ad881-124">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)|  
|[<span data-ttu-id="ad881-125">sealed</span><span class="sxs-lookup"><span data-stu-id="ad881-125">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)|<span data-ttu-id="ad881-126">指定它對衍生類別不再是虛擬。</span><span class="sxs-lookup"><span data-stu-id="ad881-126">Specifies that for derived classes it is no longer virtual.</span></span>||  
|[<span data-ttu-id="ad881-127">abstract</span><span class="sxs-lookup"><span data-stu-id="ad881-127">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)|<span data-ttu-id="ad881-128">編譯器不會產生 `add` 和 `remove` 事件存取子區塊，因此衍生類別必須提供自己的實作。</span><span class="sxs-lookup"><span data-stu-id="ad881-128">The compiler will not generate the `add` and `remove` event accessor blocks and therefore derived classes must provide their own implementation.</span></span>||  
  
 <span data-ttu-id="ad881-129">事件可使用 [static](../../../csharp/language-reference/keywords/static.md) 關鍵字宣告為靜態事件。</span><span class="sxs-lookup"><span data-stu-id="ad881-129">An event may be declared as a static event by using the [static](../../../csharp/language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="ad881-130">這可隨時向呼叫端提供事件，即使沒有任何類別執行個體存在。</span><span class="sxs-lookup"><span data-stu-id="ad881-130">This makes the event available to callers at any time, even if no instance of the class exists.</span></span> <span data-ttu-id="ad881-131">如需詳細資訊，請參閱[靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="ad881-131">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="ad881-132">事件可使用 [virtual](../../../csharp/language-reference/keywords/virtual.md) 關鍵字標示為虛擬事件。</span><span class="sxs-lookup"><span data-stu-id="ad881-132">An event can be marked as a virtual event by using the [virtual](../../../csharp/language-reference/keywords/virtual.md) keyword.</span></span> <span data-ttu-id="ad881-133">這可讓衍生類別使用 [override](../../../csharp/language-reference/keywords/override.md) 關鍵字覆寫事件行為。</span><span class="sxs-lookup"><span data-stu-id="ad881-133">This enables derived classes to override the event behavior by using the [override](../../../csharp/language-reference/keywords/override.md) keyword.</span></span> <span data-ttu-id="ad881-134">如需詳細資訊，請參閱[繼承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)。</span><span class="sxs-lookup"><span data-stu-id="ad881-134">For more information, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span></span> <span data-ttu-id="ad881-135">事件覆寫虛擬事件也可以 [sealed](../../../csharp/language-reference/keywords/sealed.md)，指定它對衍生類別不再是虛擬。</span><span class="sxs-lookup"><span data-stu-id="ad881-135">An event overriding a virtual event can also be [sealed](../../../csharp/language-reference/keywords/sealed.md), which specifies that for derived classes it is no longer virtual.</span></span> <span data-ttu-id="ad881-136">最後，您可以宣告事件為 [abstract](../../../csharp/language-reference/keywords/abstract.md)，也就是編譯器不會產生 `add` 和 `remove` 事件存取子區塊。</span><span class="sxs-lookup"><span data-stu-id="ad881-136">Lastly, an event can be declared [abstract](../../../csharp/language-reference/keywords/abstract.md), which means that the compiler will not generate the `add` and `remove` event accessor blocks.</span></span> <span data-ttu-id="ad881-137">因此，衍生類別必須提供自己的實作。</span><span class="sxs-lookup"><span data-stu-id="ad881-137">Therefore derived classes must provide their own implementation.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="ad881-138">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="ad881-138">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ad881-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad881-139">See Also</span></span>  
 <span data-ttu-id="ad881-140">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="ad881-140">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="ad881-141"> [C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ad881-141"> [C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="ad881-142"> [C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="ad881-142"> [C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="ad881-143"> [add](../../../csharp/language-reference/keywords/add.md) </span><span class="sxs-lookup"><span data-stu-id="ad881-143"> [add](../../../csharp/language-reference/keywords/add.md) </span></span>  
<span data-ttu-id="ad881-144"> [remove](../../../csharp/language-reference/keywords/remove.md) </span><span class="sxs-lookup"><span data-stu-id="ad881-144"> [remove](../../../csharp/language-reference/keywords/remove.md) </span></span>  
<span data-ttu-id="ad881-145"> [修飾詞](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="ad881-145"> [Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
<span data-ttu-id="ad881-146"> [如何：組合委派 (多點傳送委派)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)</span><span class="sxs-lookup"><span data-stu-id="ad881-146"> [How to: Combine Delegates (Multicast Delegates)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)</span></span>
