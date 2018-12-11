---
title: 屬性設計
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
author: KrzysztofCwalina
ms.openlocfilehash: 1d119b48f0524b3e997aa2cb9ea2cbbd855afdf0
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131452"
---
# <a name="property-design"></a><span data-ttu-id="dfe34-102">屬性設計</span><span class="sxs-lookup"><span data-stu-id="dfe34-102">Property Design</span></span>
<span data-ttu-id="dfe34-103">雖然技術上的方法非常類似屬性，它們是根據它們的使用案例相當不同。</span><span class="sxs-lookup"><span data-stu-id="dfe34-103">Although properties are technically very similar to methods, they are quite different in terms of their usage scenarios.</span></span> <span data-ttu-id="dfe34-104">應該會看到它們做為智慧的欄位。</span><span class="sxs-lookup"><span data-stu-id="dfe34-104">They should be seen as smart fields.</span></span> <span data-ttu-id="dfe34-105">它們有呼叫欄位的語法，與彈性的方法。</span><span class="sxs-lookup"><span data-stu-id="dfe34-105">They have the calling syntax of fields, and the flexibility of methods.</span></span>  
  
 <span data-ttu-id="dfe34-106">**✓ DO** 建立 get 專用的屬性，如果呼叫端應該不能變更屬性的值。</span><span class="sxs-lookup"><span data-stu-id="dfe34-106">**✓ DO** create get-only properties if the caller should not be able to change the value of the property.</span></span>  
  
 <span data-ttu-id="dfe34-107">請記住，如果的型別屬性是可變動參考類型，可以變更屬性值，即使屬性是 get 專用。</span><span class="sxs-lookup"><span data-stu-id="dfe34-107">Keep in mind that if the type of the property is a mutable reference type, the property value can be changed even if the property is get-only.</span></span>  
  
 <span data-ttu-id="dfe34-108">**X DO NOT** 提供具有更廣泛的存取範圍，getter 與 setter 設定專用的屬性。</span><span class="sxs-lookup"><span data-stu-id="dfe34-108">**X DO NOT** provide set-only properties or properties with the setter having broader accessibility than the getter.</span></span>  
  
 <span data-ttu-id="dfe34-109">比方說，務必使用屬性與公用 setter 和受保護的 getter。</span><span class="sxs-lookup"><span data-stu-id="dfe34-109">For example, do not use properties with a public setter and a protected getter.</span></span>  
  
 <span data-ttu-id="dfe34-110">如果無法提供的屬性 getter，請改為實作做為方法的功能。</span><span class="sxs-lookup"><span data-stu-id="dfe34-110">If the property getter cannot be provided, implement the functionality as a method instead.</span></span> <span data-ttu-id="dfe34-111">請考慮開始使用的方法名稱`Set`並在後面加什麼您會有具名屬性。</span><span class="sxs-lookup"><span data-stu-id="dfe34-111">Consider starting the method name with `Set` and follow with what you would have named the property.</span></span> <span data-ttu-id="dfe34-112">比方說，<xref:System.AppDomain>有一個方法，叫做`SetCachePath`而不是僅限集的屬性，稱為`CachePath`。</span><span class="sxs-lookup"><span data-stu-id="dfe34-112">For example, <xref:System.AppDomain> has a method called `SetCachePath` instead of having a set-only property called `CachePath`.</span></span>  
  
 <span data-ttu-id="dfe34-113">**✓ DO** 提供合理的預設值給所有屬性，確保 預設值，不會造成安全性漏洞或方面出了沒有效率的程式碼中。</span><span class="sxs-lookup"><span data-stu-id="dfe34-113">**✓ DO** provide sensible default values for all properties, ensuring that the defaults do not result in a security hole or terribly inefficient code.</span></span>  
  
 <span data-ttu-id="dfe34-114">**✓ DO** 讓屬性以設定任何順序，即使這樣造成暫存物件的無效狀態。</span><span class="sxs-lookup"><span data-stu-id="dfe34-114">**✓ DO** allow properties to be set in any order even if this results in a temporary invalid state of the object.</span></span>  
  
 <span data-ttu-id="dfe34-115">很常見的兩個或多個要相互關聯的其中一個屬性的某些值可能是無效的點屬性指定相同的物件上的其他屬性的值。</span><span class="sxs-lookup"><span data-stu-id="dfe34-115">It is common for two or more properties to be interrelated to a point where some values of one property might be invalid given the values of other properties on the same object.</span></span> <span data-ttu-id="dfe34-116">在此情況下，造成無效的狀態例外狀況應該延遲直到物件實際上一起使用相互關聯的屬性。</span><span class="sxs-lookup"><span data-stu-id="dfe34-116">In such cases, exceptions resulting from the invalid state should be postponed until the interrelated properties are actually used together by the object.</span></span>  
  
 <span data-ttu-id="dfe34-117">**✓ DO** 保留先前的值，如果屬性 setter 擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="dfe34-117">**✓ DO** preserve the previous value if a property setter throws an exception.</span></span>  
  
 <span data-ttu-id="dfe34-118">**X AVOID** 擲回例外狀況，從屬性 getter。</span><span class="sxs-lookup"><span data-stu-id="dfe34-118">**X AVOID** throwing exceptions from property getters.</span></span>  
  
 <span data-ttu-id="dfe34-119">屬性 getter 應該是簡單的作業，而且不應該有任何前置條件。</span><span class="sxs-lookup"><span data-stu-id="dfe34-119">Property getters should be simple operations and should not have any preconditions.</span></span> <span data-ttu-id="dfe34-120">如果 getter 可以擲回例外狀況，它應該可能重新設計為方法。</span><span class="sxs-lookup"><span data-stu-id="dfe34-120">If a getter can throw an exception, it should probably be redesigned to be a method.</span></span> <span data-ttu-id="dfe34-121">請注意，這項規則不適用於索引子，其中我們希望因為驗證引數的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="dfe34-121">Notice that this rule does not apply to indexers, where we do expect exceptions as a result of validating the arguments.</span></span>  
  
### <a name="indexed-property-design"></a><span data-ttu-id="dfe34-122">索引的屬性設計</span><span class="sxs-lookup"><span data-stu-id="dfe34-122">Indexed Property Design</span></span>  
 <span data-ttu-id="dfe34-123">索引的屬性是特殊的屬性可以有參數，可以使用類似於陣列編製索引的特殊語法來呼叫。</span><span class="sxs-lookup"><span data-stu-id="dfe34-123">An indexed property is a special property that can have parameters and can be called with special syntax similar to array indexing.</span></span>  
  
 <span data-ttu-id="dfe34-124">索引的屬性通常稱為 「 索引子 」。</span><span class="sxs-lookup"><span data-stu-id="dfe34-124">Indexed properties are commonly referred to as indexers.</span></span> <span data-ttu-id="dfe34-125">索引子應該只用於存取項目邏輯的集合中的 Api。</span><span class="sxs-lookup"><span data-stu-id="dfe34-125">Indexers should be used only in APIs that provide access to items in a logical collection.</span></span> <span data-ttu-id="dfe34-126">例如，字串是字元和索引子上的集合<xref:System.String?displayProperty=nameWithType>已新增至存取其所有字元。</span><span class="sxs-lookup"><span data-stu-id="dfe34-126">For example, a string is a collection of characters, and the indexer on <xref:System.String?displayProperty=nameWithType> was added to access its characters.</span></span>  
  
 <span data-ttu-id="dfe34-127">**✓ CONSIDER** 使用索引子來提供資料儲存在內部陣列的存取權。</span><span class="sxs-lookup"><span data-stu-id="dfe34-127">**✓ CONSIDER** using indexers to provide access to data stored in an internal array.</span></span>  
  
 <span data-ttu-id="dfe34-128">**✓ CONSIDER** 提供索引子型別上表示的項目集合。</span><span class="sxs-lookup"><span data-stu-id="dfe34-128">**✓ CONSIDER** providing indexers on types representing collections of items.</span></span>  
  
 <span data-ttu-id="dfe34-129">**X AVOID** 使用索引的屬性與一個以上的參數。</span><span class="sxs-lookup"><span data-stu-id="dfe34-129">**X AVOID** using indexed properties with more than one parameter.</span></span>  
  
 <span data-ttu-id="dfe34-130">如果設計需要多個參數，請重新考慮是否真的邏輯的集合來表示存取子的屬性。</span><span class="sxs-lookup"><span data-stu-id="dfe34-130">If the design requires multiple parameters, reconsider whether the property really represents an accessor to a logical collection.</span></span> <span data-ttu-id="dfe34-131">如果不存在，請改為使用方法。</span><span class="sxs-lookup"><span data-stu-id="dfe34-131">If it does not, use methods instead.</span></span> <span data-ttu-id="dfe34-132">開始使用的方法名稱，請考慮`Get`或`Set`。</span><span class="sxs-lookup"><span data-stu-id="dfe34-132">Consider starting the method name with `Get` or `Set`.</span></span>  
  
 <span data-ttu-id="dfe34-133">**X AVOID** 以外的參數類型的索引子 <xref:System.Int32?displayProperty=nameWithType>， <xref:System.Int64?displayProperty=nameWithType>， <xref:System.String?displayProperty=nameWithType>， <xref:System.Object?displayProperty=nameWithType>，或列舉。</span><span class="sxs-lookup"><span data-stu-id="dfe34-133">**X AVOID** indexers with parameter types other than <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, or an enum.</span></span>  
  
 <span data-ttu-id="dfe34-134">如果設計需要其他類型的參數，強重新評估是否 API 真的表示的邏輯集合存取子。</span><span class="sxs-lookup"><span data-stu-id="dfe34-134">If the design requires other types of parameters, strongly reevaluate whether the API really represents an accessor to a logical collection.</span></span> <span data-ttu-id="dfe34-135">如果沒有，請使用方法。</span><span class="sxs-lookup"><span data-stu-id="dfe34-135">If it does not, use a method.</span></span> <span data-ttu-id="dfe34-136">開始使用的方法名稱，請考慮`Get`或`Set`。</span><span class="sxs-lookup"><span data-stu-id="dfe34-136">Consider starting the method name with `Get` or `Set`.</span></span>  
  
 <span data-ttu-id="dfe34-137">**✓ DO** 使用名稱 `Item` 的索引屬性，除非有明顯更適合的名稱 (例如，請參閱<xref:System.String.Chars%2A> 屬性 `System.String`)。</span><span class="sxs-lookup"><span data-stu-id="dfe34-137">**✓ DO** use the name `Item` for indexed properties unless there is an obviously better name (e.g., see the <xref:System.String.Chars%2A> property on `System.String`).</span></span>  
  
 <span data-ttu-id="dfe34-138">在 C# 中，索引子會是預設名為項目。</span><span class="sxs-lookup"><span data-stu-id="dfe34-138">In C#, indexers are by default named Item.</span></span> <span data-ttu-id="dfe34-139"><xref:System.Runtime.CompilerServices.IndexerNameAttribute>可用來自訂此名稱。</span><span class="sxs-lookup"><span data-stu-id="dfe34-139">The <xref:System.Runtime.CompilerServices.IndexerNameAttribute> can be used to customize this name.</span></span>  
  
 <span data-ttu-id="dfe34-140">**X DO NOT** 提供索引子和語意相等的方法。</span><span class="sxs-lookup"><span data-stu-id="dfe34-140">**X DO NOT** provide both an indexer and methods that are semantically equivalent.</span></span>  
  
 <span data-ttu-id="dfe34-141">**X DO NOT** 提供一個類型中的多載索引子的一個以上的系列。</span><span class="sxs-lookup"><span data-stu-id="dfe34-141">**X DO NOT** provide more than one family of overloaded indexers in one type.</span></span>  
  
 <span data-ttu-id="dfe34-142">這會強制執行 C# 編譯器。</span><span class="sxs-lookup"><span data-stu-id="dfe34-142">This is enforced by the C# compiler.</span></span>  
  
 <span data-ttu-id="dfe34-143">**X DO NOT** 使用非預設索引的屬性。</span><span class="sxs-lookup"><span data-stu-id="dfe34-143">**X DO NOT** use nondefault indexed properties.</span></span>  
  
 <span data-ttu-id="dfe34-144">這會強制執行 C# 編譯器。</span><span class="sxs-lookup"><span data-stu-id="dfe34-144">This is enforced by the C# compiler.</span></span>  
  
### <a name="property-change-notification-events"></a><span data-ttu-id="dfe34-145">屬性變更通知事件</span><span class="sxs-lookup"><span data-stu-id="dfe34-145">Property Change Notification Events</span></span>  
 <span data-ttu-id="dfe34-146">有時候最好提供事件通知中的屬性值變更的使用者。</span><span class="sxs-lookup"><span data-stu-id="dfe34-146">Sometimes it is useful to provide an event notifying the user of changes in a property value.</span></span> <span data-ttu-id="dfe34-147">例如，`System.Windows.Forms.Control`引發`TextChanged`的值之後的事件其`Text`屬性已變更。</span><span class="sxs-lookup"><span data-stu-id="dfe34-147">For example, `System.Windows.Forms.Control` raises a `TextChanged` event after the value of its `Text` property has changed.</span></span>  
  
 <span data-ttu-id="dfe34-148">**✓ CONSIDER** 引發變更通知事件時修改高階應用程式開發介面 （通常是設計工具元件） 中的屬性值。</span><span class="sxs-lookup"><span data-stu-id="dfe34-148">**✓ CONSIDER** raising change notification events when property values in high-level APIs (usually designer components) are modified.</span></span>  
  
 <span data-ttu-id="dfe34-149">如果沒有良好的案例，讓使用者知道何時要變更物件的屬性，該物件應該引發屬性變更通知事件。</span><span class="sxs-lookup"><span data-stu-id="dfe34-149">If there is a good scenario for a user to know when a property of an object is changing, the object should raise a change notification event for the property.</span></span>  
  
 <span data-ttu-id="dfe34-150">不過，它不太可能是值得引發這類事件，例如基底類型或集合的低層級 api 的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="dfe34-150">However, it is unlikely to be worth the overhead to raise such events for low-level APIs such as base types or collections.</span></span> <span data-ttu-id="dfe34-151">例如，<xref:System.Collections.Generic.List%601>不會引發新的項目新增至清單時，這類事件和`Count`屬性變更。</span><span class="sxs-lookup"><span data-stu-id="dfe34-151">For example, <xref:System.Collections.Generic.List%601> would not raise such events when a new item is added to the list and the `Count` property changes.</span></span>  
  
 <span data-ttu-id="dfe34-152">**✓ CONSIDER** 引發變更通知事件時透過外部強制變更屬性的值。</span><span class="sxs-lookup"><span data-stu-id="dfe34-152">**✓ CONSIDER** raising change notification events when the value of a property changes via external forces.</span></span>  
  
 <span data-ttu-id="dfe34-153">如果屬性值變更透過某些外力 （在物件上呼叫方法以外的方式），會引發事件指出開發人員的值變更，而且已變更。</span><span class="sxs-lookup"><span data-stu-id="dfe34-153">If a property value changes via some external force (in a way other than by calling methods on the object), raise events indicate to the developer that the value is changing and has changed.</span></span> <span data-ttu-id="dfe34-154">是一個好例子`Text`文字方塊控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="dfe34-154">A good example is the `Text` property of a text box control.</span></span> <span data-ttu-id="dfe34-155">當使用者輸入文字中的`TextBox`，屬性值會自動變更。</span><span class="sxs-lookup"><span data-stu-id="dfe34-155">When the user types text in a `TextBox`, the property value automatically changes.</span></span>  
  
 <span data-ttu-id="dfe34-156">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="dfe34-156">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="dfe34-157">*皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*</span><span class="sxs-lookup"><span data-stu-id="dfe34-157">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfe34-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfe34-158">See also</span></span>

- [<span data-ttu-id="dfe34-159">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="dfe34-159">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
- [<span data-ttu-id="dfe34-160">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="dfe34-160">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
