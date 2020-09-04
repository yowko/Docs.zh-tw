---
description: event - C# 參考
title: event - C# 參考
ms.date: 07/20/2015
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
helpviewer_keywords:
- event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
ms.openlocfilehash: dff93496dfeceaf67777abe0b02ee2d620b3a5ca
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2020
ms.locfileid: "89466036"
---
# <a name="event-c-reference"></a><span data-ttu-id="1bbc4-103">事件 (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="1bbc4-103">event (C# reference)</span></span>

<span data-ttu-id="1bbc4-104">`event` 關鍵字用來在發行者類別中宣告事件。</span><span class="sxs-lookup"><span data-stu-id="1bbc4-104">The `event` keyword is used to declare an event in a publisher class.</span></span>

## <a name="example"></a><span data-ttu-id="1bbc4-105">範例</span><span class="sxs-lookup"><span data-stu-id="1bbc4-105">Example</span></span>

<span data-ttu-id="1bbc4-106">下例範例示範如何宣告及引發使用 <xref:System.EventHandler> 作為基礎委派類型的事件。</span><span class="sxs-lookup"><span data-stu-id="1bbc4-106">The following example shows how to declare and raise an event that uses <xref:System.EventHandler> as the underlying delegate type.</span></span> <span data-ttu-id="1bbc4-107">如需同時示範如何使用泛型 <xref:System.EventHandler%601> 委派型別，以及如何訂閱事件並建立事件處理常式方法的完整程式碼範例，請參閱 [如何發行符合 .Net 指導方針的事件](../../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="1bbc4-107">For the complete code example that also shows how to use the generic <xref:System.EventHandler%601> delegate type and how to subscribe to an event and create an event handler method, see [How to publish events that conform to .NET Guidelines](../../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).</span></span>

[!code-csharp[csrefKeywordsModifiers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#7)]

<span data-ttu-id="1bbc4-108">事件是一種特殊的多點傳送委派，只能從宣告委派的類別或結構內叫用 (發行者類別)。</span><span class="sxs-lookup"><span data-stu-id="1bbc4-108">Events are a special kind of multicast delegate that can only be invoked from within the class or struct where they are declared (the publisher class).</span></span> <span data-ttu-id="1bbc4-109">如果其他類別或結構訂閱了事件，當發行者類別引發事件時，就會呼叫其事件處理常式方法。</span><span class="sxs-lookup"><span data-stu-id="1bbc4-109">If other classes or structs subscribe to the event, their event handler methods will be called when the publisher class raises the event.</span></span> <span data-ttu-id="1bbc4-110">如需詳細資訊與程式碼範例，請參閱[事件](../../programming-guide/events/index.md)及[委派](../../programming-guide/delegates/index.md)。</span><span class="sxs-lookup"><span data-stu-id="1bbc4-110">For more information and code examples, see [Events](../../programming-guide/events/index.md) and [Delegates](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="1bbc4-111">事件可以標記為 [public](./public.md)、 [private](./private.md)、 [protected](./protected.md)、 [internal](./internal.md)、 [protected internal](./protected-internal.md)或 [private protected](./private-protected.md)。</span><span class="sxs-lookup"><span data-stu-id="1bbc4-111">Events can be marked as [public](./public.md), [private](./private.md), [protected](./protected.md), [internal](./internal.md), [protected internal](./protected-internal.md), or [private protected](./private-protected.md).</span></span> <span data-ttu-id="1bbc4-112">這些存取修飾詞定義類別使用者如何存取事件。</span><span class="sxs-lookup"><span data-stu-id="1bbc4-112">These access modifiers define how users of the class can access the event.</span></span> <span data-ttu-id="1bbc4-113">如需詳細資訊，請參閱[存取修飾詞](../../programming-guide/classes-and-structs/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="1bbc4-113">For more information, see [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

## <a name="keywords-and-events"></a><span data-ttu-id="1bbc4-114">關鍵字和事件</span><span class="sxs-lookup"><span data-stu-id="1bbc4-114">Keywords and events</span></span>

<span data-ttu-id="1bbc4-115">下列關鍵字適用於事件。</span><span class="sxs-lookup"><span data-stu-id="1bbc4-115">The following keywords apply to events.</span></span>

|<span data-ttu-id="1bbc4-116">關鍵字</span><span class="sxs-lookup"><span data-stu-id="1bbc4-116">Keyword</span></span>|<span data-ttu-id="1bbc4-117">描述</span><span class="sxs-lookup"><span data-stu-id="1bbc4-117">Description</span></span>|<span data-ttu-id="1bbc4-118">取得詳細資訊</span><span class="sxs-lookup"><span data-stu-id="1bbc4-118">For more information</span></span>|
|-------------|-----------------|--------------------------|
|[<span data-ttu-id="1bbc4-119">static</span><span class="sxs-lookup"><span data-stu-id="1bbc4-119">static</span></span>](./static.md)|<span data-ttu-id="1bbc4-120">隨時向呼叫端提供事件，即使沒有任何類別執行個體存在。</span><span class="sxs-lookup"><span data-stu-id="1bbc4-120">Makes the event available to callers at any time, even if no instance of the class exists.</span></span>|[<span data-ttu-id="1bbc4-121">靜態類別和靜態類別成員</span><span class="sxs-lookup"><span data-stu-id="1bbc4-121">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|
|[<span data-ttu-id="1bbc4-122">virtual</span><span class="sxs-lookup"><span data-stu-id="1bbc4-122">virtual</span></span>](./virtual.md)|<span data-ttu-id="1bbc4-123">允許衍生類別使用 [override](./override.md) 關鍵字覆寫事件行為。</span><span class="sxs-lookup"><span data-stu-id="1bbc4-123">Allows derived classes to override the event behavior by using the [override](./override.md) keyword.</span></span>|[<span data-ttu-id="1bbc4-124">繼承</span><span class="sxs-lookup"><span data-stu-id="1bbc4-124">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)|
|[<span data-ttu-id="1bbc4-125">sealed</span><span class="sxs-lookup"><span data-stu-id="1bbc4-125">sealed</span></span>](./sealed.md)|<span data-ttu-id="1bbc4-126">指定它對衍生類別不再是虛擬。</span><span class="sxs-lookup"><span data-stu-id="1bbc4-126">Specifies that for derived classes it is no longer virtual.</span></span>||
|[<span data-ttu-id="1bbc4-127">抽象</span><span class="sxs-lookup"><span data-stu-id="1bbc4-127">abstract</span></span>](./abstract.md)|<span data-ttu-id="1bbc4-128">編譯器不會產生 `add` 和 `remove` 事件存取子區塊，因此衍生類別必須提供自己的實作。</span><span class="sxs-lookup"><span data-stu-id="1bbc4-128">The compiler will not generate the `add` and `remove` event accessor blocks and therefore derived classes must provide their own implementation.</span></span>||

<span data-ttu-id="1bbc4-129">事件可使用 [static](./static.md) 關鍵字宣告為靜態事件。</span><span class="sxs-lookup"><span data-stu-id="1bbc4-129">An event may be declared as a static event by using the [static](./static.md) keyword.</span></span> <span data-ttu-id="1bbc4-130">這可隨時向呼叫端提供事件，即使沒有任何類別執行個體存在。</span><span class="sxs-lookup"><span data-stu-id="1bbc4-130">This makes the event available to callers at any time, even if no instance of the class exists.</span></span> <span data-ttu-id="1bbc4-131">如需詳細資訊，請參閱 [靜態類別和靜態類別成員](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="1bbc4-131">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

<span data-ttu-id="1bbc4-132">事件可使用 [virtual](./virtual.md) 關鍵字標示為虛擬事件。</span><span class="sxs-lookup"><span data-stu-id="1bbc4-132">An event can be marked as a virtual event by using the [virtual](./virtual.md) keyword.</span></span> <span data-ttu-id="1bbc4-133">這可讓衍生類別使用 [override](./override.md) 關鍵字覆寫事件行為。</span><span class="sxs-lookup"><span data-stu-id="1bbc4-133">This enables derived classes to override the event behavior by using the [override](./override.md) keyword.</span></span> <span data-ttu-id="1bbc4-134">如需詳細資訊，請參閱[繼承](../../programming-guide/classes-and-structs/inheritance.md)。</span><span class="sxs-lookup"><span data-stu-id="1bbc4-134">For more information, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span> <span data-ttu-id="1bbc4-135">事件覆寫虛擬事件也可以 [sealed](./sealed.md)，指定它對衍生類別不再是虛擬。</span><span class="sxs-lookup"><span data-stu-id="1bbc4-135">An event overriding a virtual event can also be [sealed](./sealed.md), which specifies that for derived classes it is no longer virtual.</span></span> <span data-ttu-id="1bbc4-136">最後，您可以宣告事件為 [abstract](./abstract.md)，也就是編譯器不會產生 `add` 和 `remove` 事件存取子區塊。</span><span class="sxs-lookup"><span data-stu-id="1bbc4-136">Lastly, an event can be declared [abstract](./abstract.md), which means that the compiler will not generate the `add` and `remove` event accessor blocks.</span></span> <span data-ttu-id="1bbc4-137">因此，衍生類別必須提供自己的實作。</span><span class="sxs-lookup"><span data-stu-id="1bbc4-137">Therefore derived classes must provide their own implementation.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1bbc4-138">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="1bbc4-138">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1bbc4-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bbc4-139">See also</span></span>

- [<span data-ttu-id="1bbc4-140">C # 參考</span><span class="sxs-lookup"><span data-stu-id="1bbc4-140">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1bbc4-141">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1bbc4-141">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1bbc4-142">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="1bbc4-142">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="1bbc4-143">add</span><span class="sxs-lookup"><span data-stu-id="1bbc4-143">add</span></span>](./add.md)
- [<span data-ttu-id="1bbc4-144">remove</span><span class="sxs-lookup"><span data-stu-id="1bbc4-144">remove</span></span>](./remove.md)
- [<span data-ttu-id="1bbc4-145">修飾詞</span><span class="sxs-lookup"><span data-stu-id="1bbc4-145">Modifiers</span></span>](index.md)
- [<span data-ttu-id="1bbc4-146">如何將委派合併 (多播委派) </span><span class="sxs-lookup"><span data-stu-id="1bbc4-146">How to combine delegates (Multicast Delegates)</span></span>](../../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
