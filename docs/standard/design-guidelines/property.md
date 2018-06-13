---
title: 屬性設計
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a4aec965753fe8f89b8bd89469f8dc5739a6a7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577089"
---
# <a name="property-design"></a><span data-ttu-id="366dc-102">屬性設計</span><span class="sxs-lookup"><span data-stu-id="366dc-102">Property Design</span></span>
<span data-ttu-id="366dc-103">雖然技術上非常類似於方法內容，但它們是根據它們的使用案例相當不同。</span><span class="sxs-lookup"><span data-stu-id="366dc-103">Although properties are technically very similar to methods, they are quite different in terms of their usage scenarios.</span></span> <span data-ttu-id="366dc-104">這些應該視為智慧型欄位。</span><span class="sxs-lookup"><span data-stu-id="366dc-104">They should be seen as smart fields.</span></span> <span data-ttu-id="366dc-105">有的欄位，呼叫的語法和方法的彈性。</span><span class="sxs-lookup"><span data-stu-id="366dc-105">They have the calling syntax of fields, and the flexibility of methods.</span></span>  
  
 <span data-ttu-id="366dc-106">**✓ 不要**建立 get 專用的屬性，如果呼叫端應該不能變更屬性的值。</span><span class="sxs-lookup"><span data-stu-id="366dc-106">**✓ DO** create get-only properties if the caller should not be able to change the value of the property.</span></span>  
  
 <span data-ttu-id="366dc-107">請記住，如果類型的屬性是可變動參考類型，可以變更屬性值，即使屬性是 get-only。</span><span class="sxs-lookup"><span data-stu-id="366dc-107">Keep in mind that if the type of the property is a mutable reference type, the property value can be changed even if the property is get-only.</span></span>  
  
 <span data-ttu-id="366dc-108">**X 不**提供具有更廣泛的存取範圍，getter 與 setter 設定專用的屬性。</span><span class="sxs-lookup"><span data-stu-id="366dc-108">**X DO NOT** provide set-only properties or properties with the setter having broader accessibility than the getter.</span></span>  
  
 <span data-ttu-id="366dc-109">例如，務必使用屬性具有公用 setter 和受保護的 getter。</span><span class="sxs-lookup"><span data-stu-id="366dc-109">For example, do not use properties with a public setter and a protected getter.</span></span>  
  
 <span data-ttu-id="366dc-110">如果無法提供屬性 getter，請改為實作做為方法的功能。</span><span class="sxs-lookup"><span data-stu-id="366dc-110">If the property getter cannot be provided, implement the functionality as a method instead.</span></span> <span data-ttu-id="366dc-111">請考慮從開始的方法名稱與`Set`和之後，您會有什麼屬性。</span><span class="sxs-lookup"><span data-stu-id="366dc-111">Consider starting the method name with `Set` and follow with what you would have named the property.</span></span> <span data-ttu-id="366dc-112">例如，<xref:System.AppDomain>已呼叫的方法`SetCachePath`而不需僅限組屬性稱為`CachePath`。</span><span class="sxs-lookup"><span data-stu-id="366dc-112">For example, <xref:System.AppDomain> has a method called `SetCachePath` instead of having a set-only property called `CachePath`.</span></span>  
  
 <span data-ttu-id="366dc-113">**✓ 不要**提供合理的預設值給所有屬性，確保 預設值，不會造成安全性漏洞或方面出了沒有效率的程式碼中。</span><span class="sxs-lookup"><span data-stu-id="366dc-113">**✓ DO** provide sensible default values for all properties, ensuring that the defaults do not result in a security hole or terribly inefficient code.</span></span>  
  
 <span data-ttu-id="366dc-114">**✓ 不要**讓屬性以設定任何順序，即使這樣造成暫存物件的無效狀態。</span><span class="sxs-lookup"><span data-stu-id="366dc-114">**✓ DO** allow properties to be set in any order even if this results in a temporary invalid state of the object.</span></span>  
  
 <span data-ttu-id="366dc-115">通常會是一個屬性的某些值可能是無效的點彼此相關的兩個或多個屬性指定相同的物件上的其他屬性的值。</span><span class="sxs-lookup"><span data-stu-id="366dc-115">It is common for two or more properties to be interrelated to a point where some values of one property might be invalid given the values of other properties on the same object.</span></span> <span data-ttu-id="366dc-116">在這種情況下，直到物件實際上在一起使用相互關聯的屬性應延遲造成無效的狀態例外狀況。</span><span class="sxs-lookup"><span data-stu-id="366dc-116">In such cases, exceptions resulting from the invalid state should be postponed until the interrelated properties are actually used together by the object.</span></span>  
  
 <span data-ttu-id="366dc-117">**✓ 不要**保留先前的值，如果屬性 setter 擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="366dc-117">**✓ DO** preserve the previous value if a property setter throws an exception.</span></span>  
  
 <span data-ttu-id="366dc-118">**請避免 x**擲回例外狀況，從屬性 getter。</span><span class="sxs-lookup"><span data-stu-id="366dc-118">**X AVOID** throwing exceptions from property getters.</span></span>  
  
 <span data-ttu-id="366dc-119">Getter 屬性應該是簡單的操作，而且不能有任何先決條件。</span><span class="sxs-lookup"><span data-stu-id="366dc-119">Property getters should be simple operations and should not have any preconditions.</span></span> <span data-ttu-id="366dc-120">如果 getter 可以擲回例外狀況，它應該可能重新設計的方法。</span><span class="sxs-lookup"><span data-stu-id="366dc-120">If a getter can throw an exception, it should probably be redesigned to be a method.</span></span> <span data-ttu-id="366dc-121">請注意，這項規則不適用於索引子，其中我們期望的結果驗證引數的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="366dc-121">Notice that this rule does not apply to indexers, where we do expect exceptions as a result of validating the arguments.</span></span>  
  
### <a name="indexed-property-design"></a><span data-ttu-id="366dc-122">設計索引的屬性</span><span class="sxs-lookup"><span data-stu-id="366dc-122">Indexed Property Design</span></span>  
 <span data-ttu-id="366dc-123">索引的屬性是特殊的屬性可以有參數，可以使用類似陣列編製索引的特殊語法來呼叫。</span><span class="sxs-lookup"><span data-stu-id="366dc-123">An indexed property is a special property that can have parameters and can be called with special syntax similar to array indexing.</span></span>  
  
 <span data-ttu-id="366dc-124">索引的屬性通常稱為索引子。</span><span class="sxs-lookup"><span data-stu-id="366dc-124">Indexed properties are commonly referred to as indexers.</span></span> <span data-ttu-id="366dc-125">索引子應該只能用於應用程式開發介面可提供存取權的邏輯集合中的項目。</span><span class="sxs-lookup"><span data-stu-id="366dc-125">Indexers should be used only in APIs that provide access to items in a logical collection.</span></span> <span data-ttu-id="366dc-126">例如，字串是字元和集合上的索引子<xref:System.String?displayProperty=nameWithType>已新增至存取其所有字元。</span><span class="sxs-lookup"><span data-stu-id="366dc-126">For example, a string is a collection of characters, and the indexer on <xref:System.String?displayProperty=nameWithType> was added to access its characters.</span></span>  
  
 <span data-ttu-id="366dc-127">**✓ 考慮**使用索引子來提供資料儲存在內部陣列的存取權。</span><span class="sxs-lookup"><span data-stu-id="366dc-127">**✓ CONSIDER** using indexers to provide access to data stored in an internal array.</span></span>  
  
 <span data-ttu-id="366dc-128">**✓ 考慮**提供索引子型別上表示的項目集合。</span><span class="sxs-lookup"><span data-stu-id="366dc-128">**✓ CONSIDER** providing indexers on types representing collections of items.</span></span>  
  
 <span data-ttu-id="366dc-129">**請避免 x**使用索引的屬性與一個以上的參數。</span><span class="sxs-lookup"><span data-stu-id="366dc-129">**X AVOID** using indexed properties with more than one parameter.</span></span>  
  
 <span data-ttu-id="366dc-130">如果設計需要多個參數，請考慮是否真的邏輯集合表示的存取子的屬性。</span><span class="sxs-lookup"><span data-stu-id="366dc-130">If the design requires multiple parameters, reconsider whether the property really represents an accessor to a logical collection.</span></span> <span data-ttu-id="366dc-131">如果不存在，請改為使用方法。</span><span class="sxs-lookup"><span data-stu-id="366dc-131">If it does not, use methods instead.</span></span> <span data-ttu-id="366dc-132">請考慮從開始的方法名稱與`Get`或`Set`。</span><span class="sxs-lookup"><span data-stu-id="366dc-132">Consider starting the method name with `Get` or `Set`.</span></span>  
  
 <span data-ttu-id="366dc-133">**請避免 x**以外的參數類型的索引子<xref:System.Int32?displayProperty=nameWithType>， <xref:System.Int64?displayProperty=nameWithType>， <xref:System.String?displayProperty=nameWithType>， <xref:System.Object?displayProperty=nameWithType>，或列舉。</span><span class="sxs-lookup"><span data-stu-id="366dc-133">**X AVOID** indexers with parameter types other than <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, or an enum.</span></span>  
  
 <span data-ttu-id="366dc-134">如果設計需要其他類型的參數，強烈重新評估是否真的邏輯集合表示的存取子的 API。</span><span class="sxs-lookup"><span data-stu-id="366dc-134">If the design requires other types of parameters, strongly reevaluate whether the API really represents an accessor to a logical collection.</span></span> <span data-ttu-id="366dc-135">如果未出現，請使用方法。</span><span class="sxs-lookup"><span data-stu-id="366dc-135">If it does not, use a method.</span></span> <span data-ttu-id="366dc-136">請考慮從開始的方法名稱與`Get`或`Set`。</span><span class="sxs-lookup"><span data-stu-id="366dc-136">Consider starting the method name with `Get` or `Set`.</span></span>  
  
 <span data-ttu-id="366dc-137">**✓ 不要**使用名稱`Item`的索引屬性，除非有明顯更適合的名稱 (例如，請參閱<xref:System.String.Chars%2A>屬性`System.String`)。</span><span class="sxs-lookup"><span data-stu-id="366dc-137">**✓ DO** use the name `Item` for indexed properties unless there is an obviously better name (e.g., see the <xref:System.String.Chars%2A> property on `System.String`).</span></span>  
  
 <span data-ttu-id="366dc-138">在 C# 中，索引子為可由預設的具名項目。</span><span class="sxs-lookup"><span data-stu-id="366dc-138">In C#, indexers are by default named Item.</span></span> <span data-ttu-id="366dc-139"><xref:System.Runtime.CompilerServices.IndexerNameAttribute>可以用來自訂此名稱。</span><span class="sxs-lookup"><span data-stu-id="366dc-139">The <xref:System.Runtime.CompilerServices.IndexerNameAttribute> can be used to customize this name.</span></span>  
  
 <span data-ttu-id="366dc-140">**X 不**提供索引子和語意相等的方法。</span><span class="sxs-lookup"><span data-stu-id="366dc-140">**X DO NOT** provide both an indexer and methods that are semantically equivalent.</span></span>  
  
 <span data-ttu-id="366dc-141">**X 不**提供一個類型中的多載索引子的一個以上的系列。</span><span class="sxs-lookup"><span data-stu-id="366dc-141">**X DO NOT** provide more than one family of overloaded indexers in one type.</span></span>  
  
 <span data-ttu-id="366dc-142">這會強制執行由 C# 編譯器。</span><span class="sxs-lookup"><span data-stu-id="366dc-142">This is enforced by the C# compiler.</span></span>  
  
 <span data-ttu-id="366dc-143">**X 不**使用非預設索引的屬性。</span><span class="sxs-lookup"><span data-stu-id="366dc-143">**X DO NOT** use nondefault indexed properties.</span></span>  
  
 <span data-ttu-id="366dc-144">這會強制執行由 C# 編譯器。</span><span class="sxs-lookup"><span data-stu-id="366dc-144">This is enforced by the C# compiler.</span></span>  
  
### <a name="property-change-notification-events"></a><span data-ttu-id="366dc-145">屬性變更通知事件</span><span class="sxs-lookup"><span data-stu-id="366dc-145">Property Change Notification Events</span></span>  
 <span data-ttu-id="366dc-146">有時候很有用提供事件通知使用者屬性值中的變更。</span><span class="sxs-lookup"><span data-stu-id="366dc-146">Sometimes it is useful to provide an event notifying the user of changes in a property value.</span></span> <span data-ttu-id="366dc-147">例如，`System.Windows.Forms.Control`引發`TextChanged`事件之後的值及其`Text`屬性已變更。</span><span class="sxs-lookup"><span data-stu-id="366dc-147">For example, `System.Windows.Forms.Control` raises a `TextChanged` event after the value of its `Text` property has changed.</span></span>  
  
 <span data-ttu-id="366dc-148">**✓ 考慮**引發變更通知事件時修改高階應用程式開發介面 （通常是設計工具元件） 中的屬性值。</span><span class="sxs-lookup"><span data-stu-id="366dc-148">**✓ CONSIDER** raising change notification events when property values in high-level APIs (usually designer components) are modified.</span></span>  
  
 <span data-ttu-id="366dc-149">如果沒有良好的案例，讓使用者知道物件的屬性變更時，該物件應該會引發屬性變更通知事件。</span><span class="sxs-lookup"><span data-stu-id="366dc-149">If there is a good scenario for a user to know when a property of an object is changing, the object should raise a change notification event for the property.</span></span>  
  
 <span data-ttu-id="366dc-150">不過，它不太可能值得引發這類事件，例如基底類型或集合的低層級 api 的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="366dc-150">However, it is unlikely to be worth the overhead to raise such events for low-level APIs such as base types or collections.</span></span> <span data-ttu-id="366dc-151">例如，<xref:System.Collections.Generic.List%601>將不會引發新的項目加入至清單時，這類事件和`Count`屬性變更。</span><span class="sxs-lookup"><span data-stu-id="366dc-151">For example, <xref:System.Collections.Generic.List%601> would not raise such events when a new item is added to the list and the `Count` property changes.</span></span>  
  
 <span data-ttu-id="366dc-152">**✓ 考慮**引發變更通知事件時透過外部強制變更屬性的值。</span><span class="sxs-lookup"><span data-stu-id="366dc-152">**✓ CONSIDER** raising change notification events when the value of a property changes via external forces.</span></span>  
  
 <span data-ttu-id="366dc-153">如果屬性值變更時透過某些外部 force （在物件上呼叫方法的方法以外），會引發事件指出，開發人員正在變更的值，而且已變更。</span><span class="sxs-lookup"><span data-stu-id="366dc-153">If a property value changes via some external force (in a way other than by calling methods on the object), raise events indicate to the developer that the value is changing and has changed.</span></span> <span data-ttu-id="366dc-154">例如，`Text`文字方塊控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="366dc-154">A good example is the `Text` property of a text box control.</span></span> <span data-ttu-id="366dc-155">當使用者輸入的文字`TextBox`，會自動變更的屬性值。</span><span class="sxs-lookup"><span data-stu-id="366dc-155">When the user types text in a `TextBox`, the property value automatically changes.</span></span>  
  
 <span data-ttu-id="366dc-156">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="366dc-156">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="366dc-157">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="366dc-157">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="366dc-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="366dc-158">See Also</span></span>  
 [<span data-ttu-id="366dc-159">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="366dc-159">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="366dc-160">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="366dc-160">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
