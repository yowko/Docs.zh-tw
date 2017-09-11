---
title: "區別委派和事件"
description: "區別委派和事件"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0fdc8629-2fdb-4a7c-a433-5b9d04eaf911
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4020df1a63cbcdeb7e7b5d9d49cfe6444a43655e
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---

# <a name="distinguising-delegates-and-events"></a><span data-ttu-id="7b012-104">區別委派和事件</span><span class="sxs-lookup"><span data-stu-id="7b012-104">Distinguising Delegates and Events</span></span>

[<span data-ttu-id="7b012-105">上一個</span><span class="sxs-lookup"><span data-stu-id="7b012-105">Previous</span></span>](modern-events.md)

<span data-ttu-id="7b012-106">決定以 `delegates` 為基礎的設計與以 `events` 為基礎的設計時，不熟悉 .NET Core 平台的開發人員通常十分糾結。</span><span class="sxs-lookup"><span data-stu-id="7b012-106">Developers that are new to the .NET Core platform often struggle when deciding between a design based on `delegates` and a design based on `events`.</span></span> <span data-ttu-id="7b012-107">這是很難理解的概念，因為兩個語言功能非常類似。</span><span class="sxs-lookup"><span data-stu-id="7b012-107">This is a difficult concept, because the two language features are very similar.</span></span> <span data-ttu-id="7b012-108">事件甚至是使用委派的語言支援所建置。</span><span class="sxs-lookup"><span data-stu-id="7b012-108">Events are even built using the language support for delegates.</span></span> 

<span data-ttu-id="7b012-109">它們都提供晚期繫結案例︰元件透過呼叫只在執行階段才知道的方法來進行通訊。</span><span class="sxs-lookup"><span data-stu-id="7b012-109">They both offer a late binding scenario: they enable scenarios where a component communicates by calling a method that is only known at runtime.</span></span> <span data-ttu-id="7b012-110">兩者都支援單一和多個訂閱者方法。</span><span class="sxs-lookup"><span data-stu-id="7b012-110">They both support single and multiple subscriber methods.</span></span> <span data-ttu-id="7b012-111">您可能會發現這稱為單點傳送和多點傳送支援。</span><span class="sxs-lookup"><span data-stu-id="7b012-111">You may find this referred to as singlecast and multicast support.</span></span> <span data-ttu-id="7b012-112">它們同時支援使用類似的語法來新增和移除處理常式。</span><span class="sxs-lookup"><span data-stu-id="7b012-112">They both support similar syntax for adding and removing handlers.</span></span> <span data-ttu-id="7b012-113">最後，引發事件與呼叫委派會使用完全相同的方法呼叫語法。</span><span class="sxs-lookup"><span data-stu-id="7b012-113">Finally, raising an event and calling a delegate use exactly the same method call syntax.</span></span> <span data-ttu-id="7b012-114">兩者甚至都支援相同的 `Invoke()` 方法語法，以與 `?.` 運算子搭配使用。</span><span class="sxs-lookup"><span data-stu-id="7b012-114">They even both support the same `Invoke()` method syntax for use with the `?.` operator.</span></span>

<span data-ttu-id="7b012-115">具有所有這些相似性時，會很難決定其使用時機。</span><span class="sxs-lookup"><span data-stu-id="7b012-115">With all those similarities, it is easy to have trouble determining when to use which.</span></span>

## <a name="listening-to-events-is-optional"></a><span data-ttu-id="7b012-116">接聽事件為選擇性</span><span class="sxs-lookup"><span data-stu-id="7b012-116">Listening to Events is Optional</span></span>

<span data-ttu-id="7b012-117">決定要使用之語言功能的最重要考量為是否都必須要有附加的訂閱者。</span><span class="sxs-lookup"><span data-stu-id="7b012-117">The most important consideration in determining which language feature to use is whether or not there must be an attached subscriber.</span></span> <span data-ttu-id="7b012-118">如果您的程式碼必須呼叫訂閱者所提供的程式碼，則應該使用以委派為基礎的設計。</span><span class="sxs-lookup"><span data-stu-id="7b012-118">If your code must call the code supplied by the subscriber, you should use a design based on delegates.</span></span> <span data-ttu-id="7b012-119">如果您的程式碼可以完成其所有工作，而不需要呼叫任何訂閱者，則應該使用以事件為基礎的設計。</span><span class="sxs-lookup"><span data-stu-id="7b012-119">If your code can complete all its work without calling any subscribers, you should use a design based on events.</span></span> 

<span data-ttu-id="7b012-120">請考慮本節期間所建置的範例。</span><span class="sxs-lookup"><span data-stu-id="7b012-120">Consider the examples built during this section.</span></span> <span data-ttu-id="7b012-121">必須將電腦函式提供給您使用 `List.Sort()` 所建置的程式碼，才能適當地排序項目。</span><span class="sxs-lookup"><span data-stu-id="7b012-121">The code you built using `List.Sort()` must be given a comparer function in order to properly sort the elements.</span></span> <span data-ttu-id="7b012-122">必須提供具有委派的 LINQ 查詢，才能判斷要傳回的項目。</span><span class="sxs-lookup"><span data-stu-id="7b012-122">LINQ queries must be supplied with delegates in order to determine what elements to return.</span></span> <span data-ttu-id="7b012-123">兩者都是使用委派所建置的設計。</span><span class="sxs-lookup"><span data-stu-id="7b012-123">Both used a design built with delegates.</span></span>

<span data-ttu-id="7b012-124">請考量 `Progress` 事件。</span><span class="sxs-lookup"><span data-stu-id="7b012-124">Consider the `Progress` event.</span></span> <span data-ttu-id="7b012-125">它會報告工作的進度。</span><span class="sxs-lookup"><span data-stu-id="7b012-125">It reports progress on a task.</span></span>
<span data-ttu-id="7b012-126">不論是否有任何接聽程式，工作都會繼續進行。</span><span class="sxs-lookup"><span data-stu-id="7b012-126">The task continues to proceed whether or not there are any listeners.</span></span>
<span data-ttu-id="7b012-127">`FileSearcher` 是另一個範例。</span><span class="sxs-lookup"><span data-stu-id="7b012-127">The `FileSearcher` is another example.</span></span> <span data-ttu-id="7b012-128">它仍然會搜尋並尋找所有看到的檔案，即使未附加任何事件訂閱者也是一樣。</span><span class="sxs-lookup"><span data-stu-id="7b012-128">It would still search and find all the files that were sought, even with no event subscribers attached.</span></span>
<span data-ttu-id="7b012-129">UX 控制項仍然會正常運作，即使沒有任何訂閱者接聽事件也是一樣。</span><span class="sxs-lookup"><span data-stu-id="7b012-129">UX controls still work correctly, even when there are no subscribers listening to the events.</span></span> <span data-ttu-id="7b012-130">它們都會使用以事件為基礎的設計。</span><span class="sxs-lookup"><span data-stu-id="7b012-130">They both use designs based on events.</span></span>

## <a name="return-values-require-delegates"></a><span data-ttu-id="7b012-131">傳回值需要委派</span><span class="sxs-lookup"><span data-stu-id="7b012-131">Return Values Require Delegates</span></span>

<span data-ttu-id="7b012-132">另一個考量是您要用於委派方法的方法原型。</span><span class="sxs-lookup"><span data-stu-id="7b012-132">Another consideration is the method prototype you would want for your delegate method.</span></span> <span data-ttu-id="7b012-133">如您所見，用於事件的委派都會有 void 傳回型別。</span><span class="sxs-lookup"><span data-stu-id="7b012-133">As you've seen, the delegates used for events all have a void return type.</span></span> <span data-ttu-id="7b012-134">您也已看到有慣用語可建立事件處理常式，以透過修改事件引數物件的屬性，將資訊傳回給事件來源。</span><span class="sxs-lookup"><span data-stu-id="7b012-134">You've also seen that there are idioms to create event handlers that do pass information back to event sources through modifying properties of the event argument object.</span></span> <span data-ttu-id="7b012-135">雖然這些慣用語確實可以運作，但不像從方法傳回值一樣自然。</span><span class="sxs-lookup"><span data-stu-id="7b012-135">While these idioms do work, they are not as natural as returning a value from a method.</span></span>

<span data-ttu-id="7b012-136">請注意，這兩種啟發學習法可能通常都存在︰如果委派方法傳回值，則在某個方面可能會影響演算法。</span><span class="sxs-lookup"><span data-stu-id="7b012-136">Notice that these two heuristics may often both be present: If your delegate method returns a value, it will likely impact the algorithm in some way.</span></span>

## <a name="event-listeners-often-have-longer-lifetimes"></a><span data-ttu-id="7b012-137">事件接聽程式通常會有較長的存留期</span><span class="sxs-lookup"><span data-stu-id="7b012-137">Event Listeners Often Have Longer Lifetimes</span></span> 

<span data-ttu-id="7b012-138">這是稍弱的理由。</span><span class="sxs-lookup"><span data-stu-id="7b012-138">This is a slightly weaker justification.</span></span> <span data-ttu-id="7b012-139">不過，事件來源在一段長時間後引發事件時，您可能會發現事件設計更為自然。</span><span class="sxs-lookup"><span data-stu-id="7b012-139">However, you may find that event-based designs are more natural when the event source will be raising events over a long period of time.</span></span> <span data-ttu-id="7b012-140">您可以在許多系統上看到 UX 控制項之此項作業的範例。</span><span class="sxs-lookup"><span data-stu-id="7b012-140">You can see examples of this for UX controls on many systems.</span></span> <span data-ttu-id="7b012-141">訂閱事件之後，事件來源可能會在整個程式存留期引發事件。</span><span class="sxs-lookup"><span data-stu-id="7b012-141">Once you subscribe to an event, the event source may raise events throughout the lifetime of the program.</span></span>
<span data-ttu-id="7b012-142">(不再需要事件時，即可取消與事件的訂閱)。</span><span class="sxs-lookup"><span data-stu-id="7b012-142">(You can unsubscribe from events when you no longer need them.)</span></span>

<span data-ttu-id="7b012-143">與許多委派設計相反，其中使用委派作為方法的引數，而且在該方法傳回之後不會使用委派。</span><span class="sxs-lookup"><span data-stu-id="7b012-143">Contrast that with many delegate-based designs, where a delegate is used as an argument to a method, and the delegate is not used after that method returns.</span></span>

## <a name="evaluate-carefully"></a><span data-ttu-id="7b012-144">仔細評估</span><span class="sxs-lookup"><span data-stu-id="7b012-144">Evaluate Carefully</span></span>

<span data-ttu-id="7b012-145">上述考量不是很難和快速的規則。</span><span class="sxs-lookup"><span data-stu-id="7b012-145">The above considerations are not hard and fast rules.</span></span> <span data-ttu-id="7b012-146">相反地，它們所代表的指引可協助您決定最適合您特定使用方式的選項。</span><span class="sxs-lookup"><span data-stu-id="7b012-146">Instead, they represent guidance that can help you decide which choice is best for your particular usage.</span></span> <span data-ttu-id="7b012-147">因為它們十分類似，所以您甚至可以建立原型，並考慮哪個使用起來更自然。</span><span class="sxs-lookup"><span data-stu-id="7b012-147">Because they are similar, you can even prototype both, and consider which would be more natural to work with.</span></span> <span data-ttu-id="7b012-148">它們也都會處理晚期繫結案例。</span><span class="sxs-lookup"><span data-stu-id="7b012-148">They both handle late binding scenarios well.</span></span> <span data-ttu-id="7b012-149">請使用用來溝通最佳設計的案例。</span><span class="sxs-lookup"><span data-stu-id="7b012-149">Use the one that communicates your design the best.</span></span>

