---
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
ms.openlocfilehash: eb1805ed55921497fea88e6b39989c876ef003d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713563"
---
# <a name="event-c-reference"></a><span data-ttu-id="381d0-102">事件（C# 引用）</span><span class="sxs-lookup"><span data-stu-id="381d0-102">event (C# reference)</span></span>

<span data-ttu-id="381d0-103">`event` 關鍵字用來在發行者類別中宣告事件。</span><span class="sxs-lookup"><span data-stu-id="381d0-103">The `event` keyword is used to declare an event in a publisher class.</span></span>

## <a name="example"></a><span data-ttu-id="381d0-104">範例</span><span class="sxs-lookup"><span data-stu-id="381d0-104">Example</span></span>

<span data-ttu-id="381d0-105">下例範例示範如何宣告及引發使用 <xref:System.EventHandler> 作為基礎委派類型的事件。</span><span class="sxs-lookup"><span data-stu-id="381d0-105">The following example shows how to declare and raise an event that uses <xref:System.EventHandler> as the underlying delegate type.</span></span> <span data-ttu-id="381d0-106">有關演示如何使用泛型<xref:System.EventHandler%601>委託類型以及如何訂閱事件和創建事件處理常式方法的完整代碼示例，請參閱[如何發佈符合 .NET 框架準則的事件](../../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="381d0-106">For the complete code example that also shows how to use the generic <xref:System.EventHandler%601> delegate type and how to subscribe to an event and create an event handler method, see [How to publish events that conform to .NET Framework Guidelines](../../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).</span></span>

[!code-csharp[csrefKeywordsModifiers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#7)]

<span data-ttu-id="381d0-107">事件是一種特殊的多點傳送委派，只能從宣告委派的類別或結構內叫用 (發行者類別)。</span><span class="sxs-lookup"><span data-stu-id="381d0-107">Events are a special kind of multicast delegate that can only be invoked from within the class or struct where they are declared (the publisher class).</span></span> <span data-ttu-id="381d0-108">如果其他類別或結構訂閱了事件，當發行者類別引發事件時，就會呼叫其事件處理常式方法。</span><span class="sxs-lookup"><span data-stu-id="381d0-108">If other classes or structs subscribe to the event, their event handler methods will be called when the publisher class raises the event.</span></span> <span data-ttu-id="381d0-109">如需詳細資訊與程式碼範例，請參閱[事件](../../programming-guide/events/index.md)及[委派](../../programming-guide/delegates/index.md)。</span><span class="sxs-lookup"><span data-stu-id="381d0-109">For more information and code examples, see [Events](../../programming-guide/events/index.md) and [Delegates](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="381d0-110">事件可以標記為[公共](./public.md)、[私有](./private.md)、[受保護](./protected.md)、[內部](./internal.md)、[受保護的內部](./protected-internal.md)或[私有保護](./private-protected.md)。</span><span class="sxs-lookup"><span data-stu-id="381d0-110">Events can be marked as [public](./public.md), [private](./private.md), [protected](./protected.md), [internal](./internal.md), [protected internal](./protected-internal.md), or [private protected](./private-protected.md).</span></span> <span data-ttu-id="381d0-111">這些存取修飾詞定義類別使用者如何存取事件。</span><span class="sxs-lookup"><span data-stu-id="381d0-111">These access modifiers define how users of the class can access the event.</span></span> <span data-ttu-id="381d0-112">如需詳細資訊，請參閱[存取修飾詞](../../programming-guide/classes-and-structs/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="381d0-112">For more information, see [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

## <a name="keywords-and-events"></a><span data-ttu-id="381d0-113">關鍵字和事件</span><span class="sxs-lookup"><span data-stu-id="381d0-113">Keywords and events</span></span>

<span data-ttu-id="381d0-114">下列關鍵字適用於事件。</span><span class="sxs-lookup"><span data-stu-id="381d0-114">The following keywords apply to events.</span></span>

|<span data-ttu-id="381d0-115">關鍵字</span><span class="sxs-lookup"><span data-stu-id="381d0-115">Keyword</span></span>|<span data-ttu-id="381d0-116">描述</span><span class="sxs-lookup"><span data-stu-id="381d0-116">Description</span></span>|<span data-ttu-id="381d0-117">取得詳細資訊</span><span class="sxs-lookup"><span data-stu-id="381d0-117">For more information</span></span>|
|-------------|-----------------|--------------------------|
|[<span data-ttu-id="381d0-118">靜態</span><span class="sxs-lookup"><span data-stu-id="381d0-118">static</span></span>](./static.md)|<span data-ttu-id="381d0-119">隨時向呼叫端提供事件，即使沒有任何類別執行個體存在。</span><span class="sxs-lookup"><span data-stu-id="381d0-119">Makes the event available to callers at any time, even if no instance of the class exists.</span></span>|[<span data-ttu-id="381d0-120">靜態類別和靜態類別成員</span><span class="sxs-lookup"><span data-stu-id="381d0-120">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|
|[<span data-ttu-id="381d0-121">虛擬</span><span class="sxs-lookup"><span data-stu-id="381d0-121">virtual</span></span>](./virtual.md)|<span data-ttu-id="381d0-122">允許衍生類別使用 [override](./override.md) 關鍵字覆寫事件行為。</span><span class="sxs-lookup"><span data-stu-id="381d0-122">Allows derived classes to override the event behavior by using the [override](./override.md) keyword.</span></span>|[<span data-ttu-id="381d0-123">繼承</span><span class="sxs-lookup"><span data-stu-id="381d0-123">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)|
|[<span data-ttu-id="381d0-124">密封</span><span class="sxs-lookup"><span data-stu-id="381d0-124">sealed</span></span>](./sealed.md)|<span data-ttu-id="381d0-125">指定它對衍生類別不再是虛擬。</span><span class="sxs-lookup"><span data-stu-id="381d0-125">Specifies that for derived classes it is no longer virtual.</span></span>||
|[<span data-ttu-id="381d0-126">抽象</span><span class="sxs-lookup"><span data-stu-id="381d0-126">abstract</span></span>](./abstract.md)|<span data-ttu-id="381d0-127">編譯器不會產生 `add` 和 `remove` 事件存取子區塊，因此衍生類別必須提供自己的實作。</span><span class="sxs-lookup"><span data-stu-id="381d0-127">The compiler will not generate the `add` and `remove` event accessor blocks and therefore derived classes must provide their own implementation.</span></span>||

<span data-ttu-id="381d0-128">事件可使用 [static](./static.md) 關鍵字宣告為靜態事件。</span><span class="sxs-lookup"><span data-stu-id="381d0-128">An event may be declared as a static event by using the [static](./static.md) keyword.</span></span> <span data-ttu-id="381d0-129">這可隨時向呼叫端提供事件，即使沒有任何類別執行個體存在。</span><span class="sxs-lookup"><span data-stu-id="381d0-129">This makes the event available to callers at any time, even if no instance of the class exists.</span></span> <span data-ttu-id="381d0-130">有關詳細資訊，請參閱[靜態類和靜態類成員](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="381d0-130">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

<span data-ttu-id="381d0-131">事件可使用 [virtual](./virtual.md) 關鍵字標示為虛擬事件。</span><span class="sxs-lookup"><span data-stu-id="381d0-131">An event can be marked as a virtual event by using the [virtual](./virtual.md) keyword.</span></span> <span data-ttu-id="381d0-132">這可讓衍生類別使用 [override](./override.md) 關鍵字覆寫事件行為。</span><span class="sxs-lookup"><span data-stu-id="381d0-132">This enables derived classes to override the event behavior by using the [override](./override.md) keyword.</span></span> <span data-ttu-id="381d0-133">如需詳細資訊，請參閱[繼承](../../programming-guide/classes-and-structs/inheritance.md)。</span><span class="sxs-lookup"><span data-stu-id="381d0-133">For more information, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span> <span data-ttu-id="381d0-134">事件覆寫虛擬事件也可以 [sealed](./sealed.md)，指定它對衍生類別不再是虛擬。</span><span class="sxs-lookup"><span data-stu-id="381d0-134">An event overriding a virtual event can also be [sealed](./sealed.md), which specifies that for derived classes it is no longer virtual.</span></span> <span data-ttu-id="381d0-135">最後，您可以宣告事件為 [abstract](./abstract.md)，也就是編譯器不會產生 `add` 和 `remove` 事件存取子區塊。</span><span class="sxs-lookup"><span data-stu-id="381d0-135">Lastly, an event can be declared [abstract](./abstract.md), which means that the compiler will not generate the `add` and `remove` event accessor blocks.</span></span> <span data-ttu-id="381d0-136">因此，衍生類別必須提供自己的實作。</span><span class="sxs-lookup"><span data-stu-id="381d0-136">Therefore derived classes must provide their own implementation.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="381d0-137">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="381d0-137">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="381d0-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="381d0-138">See also</span></span>

- [<span data-ttu-id="381d0-139">C# 參考</span><span class="sxs-lookup"><span data-stu-id="381d0-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="381d0-140">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="381d0-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="381d0-141">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="381d0-141">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="381d0-142">新增</span><span class="sxs-lookup"><span data-stu-id="381d0-142">add</span></span>](./add.md)
- [<span data-ttu-id="381d0-143">移除</span><span class="sxs-lookup"><span data-stu-id="381d0-143">remove</span></span>](./remove.md)
- [<span data-ttu-id="381d0-144">修飾詞</span><span class="sxs-lookup"><span data-stu-id="381d0-144">Modifiers</span></span>](index.md)
- [<span data-ttu-id="381d0-145">如何組合委託（多播代表）</span><span class="sxs-lookup"><span data-stu-id="381d0-145">How to combine delegates (Multicast Delegates)</span></span>](../../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
