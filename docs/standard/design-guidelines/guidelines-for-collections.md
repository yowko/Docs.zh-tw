---
title: 集合方針
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
ms.openlocfilehash: cc853be2310cf72c4eb559f625c6a37a44ed7db8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276045"
---
# <a name="guidelines-for-collections"></a><span data-ttu-id="5a88a-102">集合方針</span><span class="sxs-lookup"><span data-stu-id="5a88a-102">Guidelines for Collections</span></span>
<span data-ttu-id="5a88a-103">專為操作具有一些通用特性之物件群組而設計的任何類型，都可視為集合。</span><span class="sxs-lookup"><span data-stu-id="5a88a-103">Any type designed specifically to manipulate a group of objects having some common characteristic can be considered a collection.</span></span> <span data-ttu-id="5a88a-104">這種類型幾乎都適合用來執行 <xref:System.Collections.IEnumerable> 或 <xref:System.Collections.Generic.IEnumerable%601> ，因此在本節中，我們只會考慮將其中一個或兩個介面都實作為集合的類型。</span><span class="sxs-lookup"><span data-stu-id="5a88a-104">It is almost always appropriate for such types to implement <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601>, so in this section we only consider types implementing one or both of those interfaces to be collections.</span></span>

 <span data-ttu-id="5a88a-105">❌請勿在公用 Api 中使用弱式類型集合。</span><span class="sxs-lookup"><span data-stu-id="5a88a-105">❌ DO NOT use weakly typed collections in public APIs.</span></span>

 <span data-ttu-id="5a88a-106">所有代表集合專案的傳回值和參數類型，都應該是確切的專案類型，而不是其任何基底類型（這僅適用于集合的公用成員）。</span><span class="sxs-lookup"><span data-stu-id="5a88a-106">The type of all return values and parameters representing collection items should be the exact item type, not any of its base types (this applies only to public members of the collection).</span></span>

 <span data-ttu-id="5a88a-107">❌請勿 <xref:System.Collections.ArrayList> <xref:System.Collections.Generic.List%601> 在公用 api 中使用或。</span><span class="sxs-lookup"><span data-stu-id="5a88a-107">❌ DO NOT use <xref:System.Collections.ArrayList> or <xref:System.Collections.Generic.List%601> in public APIs.</span></span>

 <span data-ttu-id="5a88a-108">這些類型是設計用來在內部執行時使用的資料結構，而不是在公用 Api 中。</span><span class="sxs-lookup"><span data-stu-id="5a88a-108">These types are data structures designed to be used in internal implementation, not in public APIs.</span></span> <span data-ttu-id="5a88a-109">`List<T>`已針對效能和能力進行優化，並以 Api 和彈性的 cleanness 成本為代價。</span><span class="sxs-lookup"><span data-stu-id="5a88a-109">`List<T>` is optimized for performance and power at the cost of cleanness of the APIs and flexibility.</span></span> <span data-ttu-id="5a88a-110">例如，如果您傳回 `List<T>` ，當用戶端程式代碼修改集合時，您就不會收到通知。</span><span class="sxs-lookup"><span data-stu-id="5a88a-110">For example, if you return `List<T>`, you will not ever be able to receive notifications when client code modifies the collection.</span></span> <span data-ttu-id="5a88a-111">此外，也 `List<T>` 會公開許多 <xref:System.Collections.Generic.List%601.BinarySearch%2A> 在許多情況下都不實用或適用的成員，例如。</span><span class="sxs-lookup"><span data-stu-id="5a88a-111">Also, `List<T>` exposes many members, such as <xref:System.Collections.Generic.List%601.BinarySearch%2A>, that are not useful or applicable in many scenarios.</span></span> <span data-ttu-id="5a88a-112">下列兩節描述專為在公用 Api 中使用而設計的類型（抽象）。</span><span class="sxs-lookup"><span data-stu-id="5a88a-112">The following two sections describe types (abstractions) designed specifically for use in public APIs.</span></span>

 <span data-ttu-id="5a88a-113">❌請勿 `Hashtable` `Dictionary<TKey,TValue>` 在公用 api 中使用或。</span><span class="sxs-lookup"><span data-stu-id="5a88a-113">❌ DO NOT use `Hashtable` or `Dictionary<TKey,TValue>` in public APIs.</span></span>

 <span data-ttu-id="5a88a-114">這些類型是設計用來在內部執行時使用的資料結構。</span><span class="sxs-lookup"><span data-stu-id="5a88a-114">These types are data structures designed to be used in internal implementation.</span></span> <span data-ttu-id="5a88a-115">公用 Api 應使用 <xref:System.Collections.IDictionary> 、 `IDictionary <TKey, TValue>` 或執行一或兩個介面的自訂類型。</span><span class="sxs-lookup"><span data-stu-id="5a88a-115">Public APIs should use <xref:System.Collections.IDictionary>, `IDictionary <TKey, TValue>`, or a custom type implementing one or both of the interfaces.</span></span>

 <span data-ttu-id="5a88a-116">❌除了方法的傳回型別以外，請不要使用 <xref:System.Collections.Generic.IEnumerator%601> 、 <xref:System.Collections.IEnumerator> 或任何其他實作用其中任何介面的型別 `GetEnumerator` 。</span><span class="sxs-lookup"><span data-stu-id="5a88a-116">❌ DO NOT use <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Collections.IEnumerator>, or any other type that implements either of these interfaces, except as the return type of a `GetEnumerator` method.</span></span>

 <span data-ttu-id="5a88a-117">從以外的方法傳回枚舉器的類型 `GetEnumerator` 無法搭配 `foreach` 語句使用。</span><span class="sxs-lookup"><span data-stu-id="5a88a-117">Types returning enumerators from methods other than `GetEnumerator` cannot be used with the `foreach` statement.</span></span>

 <span data-ttu-id="5a88a-118">❌請勿 `IEnumerator<T>` `IEnumerable<T>` 在相同的類型上同時執行和。</span><span class="sxs-lookup"><span data-stu-id="5a88a-118">❌ DO NOT implement both `IEnumerator<T>` and `IEnumerable<T>` on the same type.</span></span> <span data-ttu-id="5a88a-119">這同樣適用于非泛型介面 `IEnumerator` 和 `IEnumerable` 。</span><span class="sxs-lookup"><span data-stu-id="5a88a-119">The same applies to the nongeneric interfaces `IEnumerator` and `IEnumerable`.</span></span>

## <a name="collection-parameters"></a><span data-ttu-id="5a88a-120">集合參數</span><span class="sxs-lookup"><span data-stu-id="5a88a-120">Collection Parameters</span></span>
 <span data-ttu-id="5a88a-121">✔️可以使用最少特殊化的型別做為參數型別。</span><span class="sxs-lookup"><span data-stu-id="5a88a-121">✔️ DO use the least-specialized type possible as a parameter type.</span></span> <span data-ttu-id="5a88a-122">大部分以集合作為參數的成員都會使用 `IEnumerable<T>` 介面。</span><span class="sxs-lookup"><span data-stu-id="5a88a-122">Most members taking collections as parameters use the `IEnumerable<T>` interface.</span></span>

 <span data-ttu-id="5a88a-123">❌請避免使用 <xref:System.Collections.Generic.ICollection%601> 或 <xref:System.Collections.ICollection> 做為參數，只是用來存取 `Count` 屬性。</span><span class="sxs-lookup"><span data-stu-id="5a88a-123">❌ AVOID using <xref:System.Collections.Generic.ICollection%601> or <xref:System.Collections.ICollection> as a parameter just to access the `Count` property.</span></span>

 <span data-ttu-id="5a88a-124">相反地，請考慮使用 `IEnumerable<T>` 或 `IEnumerable` ，並動態檢查物件是否執行 `ICollection<T>` 或 `ICollection` 。</span><span class="sxs-lookup"><span data-stu-id="5a88a-124">Instead, consider using `IEnumerable<T>` or `IEnumerable` and dynamically checking whether the object implements `ICollection<T>` or `ICollection`.</span></span>

## <a name="collection-properties-and-return-values"></a><span data-ttu-id="5a88a-125">集合屬性和傳回值</span><span class="sxs-lookup"><span data-stu-id="5a88a-125">Collection Properties and Return Values</span></span>
 <span data-ttu-id="5a88a-126">❌請勿提供可設定的集合屬性。</span><span class="sxs-lookup"><span data-stu-id="5a88a-126">❌ DO NOT provide settable collection properties.</span></span>

 <span data-ttu-id="5a88a-127">使用者可以藉由先清除集合，然後再新增新內容，來取代集合的內容。</span><span class="sxs-lookup"><span data-stu-id="5a88a-127">Users can replace the contents of the collection by clearing the collection first and then adding the new contents.</span></span> <span data-ttu-id="5a88a-128">如果取代整個集合是常見的案例，請考慮在 `AddRange` 集合上提供方法。</span><span class="sxs-lookup"><span data-stu-id="5a88a-128">If replacing the whole collection is a common scenario, consider providing the `AddRange` method on the collection.</span></span>

 <span data-ttu-id="5a88a-129">✔️請使用 `Collection<T>` 或的子類別 `Collection<T>` ，以取得代表讀取/寫入集合的屬性或傳回值。</span><span class="sxs-lookup"><span data-stu-id="5a88a-129">✔️ DO use `Collection<T>` or a subclass of `Collection<T>` for properties or return values representing read/write collections.</span></span>

 <span data-ttu-id="5a88a-130">如果不 `Collection<T>` 符合某些需求（例如，集合不得執行 <xref:System.Collections.IList> ），請藉由執行、或來使用自訂 `IEnumerable<T>` 集合 `ICollection<T>` <xref:System.Collections.Generic.IList%601> 。</span><span class="sxs-lookup"><span data-stu-id="5a88a-130">If `Collection<T>` does not meet some requirement (e.g., the collection must not implement <xref:System.Collections.IList>), use a custom collection by implementing `IEnumerable<T>`, `ICollection<T>`, or <xref:System.Collections.Generic.IList%601>.</span></span>

 <span data-ttu-id="5a88a-131">✔️請使用 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 、的子類別 `ReadOnlyCollection<T>` ，或在少數情況下， `IEnumerable<T>` 針對代表唯讀集合的屬性或傳回值。</span><span class="sxs-lookup"><span data-stu-id="5a88a-131">✔️ DO use <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>, a subclass of `ReadOnlyCollection<T>`, or in rare cases `IEnumerable<T>` for properties or return values representing read-only collections.</span></span>

 <span data-ttu-id="5a88a-132">一般來說，偏好 `ReadOnlyCollection<T>` 。</span><span class="sxs-lookup"><span data-stu-id="5a88a-132">In general, prefer `ReadOnlyCollection<T>`.</span></span> <span data-ttu-id="5a88a-133">如果不符合某些需求（例如，集合不得執行 `IList` ），請藉由執行、或來使用自訂集合 `IEnumerable<T>` `ICollection<T>` `IList<T>` 。</span><span class="sxs-lookup"><span data-stu-id="5a88a-133">If it does not meet some requirement (e.g., the collection must not implement `IList`), use a custom collection by implementing `IEnumerable<T>`, `ICollection<T>`, or `IList<T>`.</span></span> <span data-ttu-id="5a88a-134">如果您確實執行自訂的唯讀集合，則會執行 `ICollection<T>.IsReadOnly` 來傳回 `true` 。</span><span class="sxs-lookup"><span data-stu-id="5a88a-134">If you do implement a custom read-only collection, implement `ICollection<T>.IsReadOnly` to return `true`.</span></span>

 <span data-ttu-id="5a88a-135">如果您確定您想要支援的唯一案例是順向反復專案，您可以直接使用 `IEnumerable<T>` 。</span><span class="sxs-lookup"><span data-stu-id="5a88a-135">In cases where you are sure that the only scenario you will ever want to support is forward-only iteration, you can simply use `IEnumerable<T>`.</span></span>

 <span data-ttu-id="5a88a-136">✔️考慮使用泛型基底集合的子類別，而不是直接使用集合。</span><span class="sxs-lookup"><span data-stu-id="5a88a-136">✔️ CONSIDER using subclasses of generic base collections instead of using the collections directly.</span></span>

 <span data-ttu-id="5a88a-137">這可讓您取得更好的名稱，以及加入不存在於基底集合類型上的 helper 成員。</span><span class="sxs-lookup"><span data-stu-id="5a88a-137">This allows for a better name and for adding helper members that are not present on the base collection types.</span></span> <span data-ttu-id="5a88a-138">這特別適用于高階 Api。</span><span class="sxs-lookup"><span data-stu-id="5a88a-138">This is especially applicable to high-level APIs.</span></span>

 <span data-ttu-id="5a88a-139">✔️考慮 `Collection<T>` `ReadOnlyCollection<T>` 從非常常用的方法和屬性傳回或的子類別。</span><span class="sxs-lookup"><span data-stu-id="5a88a-139">✔️ CONSIDER returning a subclass of `Collection<T>` or `ReadOnlyCollection<T>` from very commonly used methods and properties.</span></span>

 <span data-ttu-id="5a88a-140">這可讓您在未來新增 helper 方法或變更集合的執行。</span><span class="sxs-lookup"><span data-stu-id="5a88a-140">This will make it possible for you to add helper methods or change the collection implementation in the future.</span></span>

 <span data-ttu-id="5a88a-141">✔️如果集合中儲存的專案具有唯一索引鍵（名稱、識別碼等），請考慮使用金鑰集合。</span><span class="sxs-lookup"><span data-stu-id="5a88a-141">✔️ CONSIDER using a keyed collection if the items stored in the collection have unique keys (names, IDs, etc.).</span></span> <span data-ttu-id="5a88a-142">「索引集合」是一種集合，可以透過整數和金鑰來編制索引，而且通常是藉由繼承自來執行 `KeyedCollection<TKey,TItem>` 。</span><span class="sxs-lookup"><span data-stu-id="5a88a-142">Keyed collections are collections that can be indexed by both an integer and a key and are usually implemented by inheriting from `KeyedCollection<TKey,TItem>`.</span></span>

 <span data-ttu-id="5a88a-143">索引集合通常會有較大的記憶體佔用量，如果記憶體額外負荷高於擁有金鑰的優點，則不應使用。</span><span class="sxs-lookup"><span data-stu-id="5a88a-143">Keyed collections usually have larger memory footprints and should not be used if the memory overhead outweighs the benefits of having the keys.</span></span>

 <span data-ttu-id="5a88a-144">❌請勿從集合屬性或傳回集合的方法傳回 null 值。</span><span class="sxs-lookup"><span data-stu-id="5a88a-144">❌ DO NOT return null values from collection properties or from methods returning collections.</span></span> <span data-ttu-id="5a88a-145">改為傳回空的集合或空陣列。</span><span class="sxs-lookup"><span data-stu-id="5a88a-145">Return an empty collection or an empty array instead.</span></span>

 <span data-ttu-id="5a88a-146">一般規則是 null 和空的（0專案）集合或陣列應視為相同。</span><span class="sxs-lookup"><span data-stu-id="5a88a-146">The general rule is that null and empty (0 item) collections or arrays should be treated the same.</span></span>

### <a name="snapshots-versus-live-collections"></a><span data-ttu-id="5a88a-147">快照集與即時集合</span><span class="sxs-lookup"><span data-stu-id="5a88a-147">Snapshots Versus Live Collections</span></span>
 <span data-ttu-id="5a88a-148">代表某個時間點之狀態的集合稱為快照集集合。</span><span class="sxs-lookup"><span data-stu-id="5a88a-148">Collections representing a state at some point in time are called snapshot collections.</span></span> <span data-ttu-id="5a88a-149">例如，包含資料庫查詢所傳回之資料列的集合會是快照集。</span><span class="sxs-lookup"><span data-stu-id="5a88a-149">For example, a collection containing rows returned from a database query would be a snapshot.</span></span> <span data-ttu-id="5a88a-150">一律代表目前狀態的集合稱為「即時集合」。</span><span class="sxs-lookup"><span data-stu-id="5a88a-150">Collections that always represent the current state are called live collections.</span></span> <span data-ttu-id="5a88a-151">例如，專案的集合 `ComboBox` 是即時集合。</span><span class="sxs-lookup"><span data-stu-id="5a88a-151">For example, a collection of `ComboBox` items is a live collection.</span></span>

 <span data-ttu-id="5a88a-152">❌不要從屬性傳回快照集集合。</span><span class="sxs-lookup"><span data-stu-id="5a88a-152">❌ DO NOT return snapshot collections from properties.</span></span> <span data-ttu-id="5a88a-153">屬性應該會傳回即時集合。</span><span class="sxs-lookup"><span data-stu-id="5a88a-153">Properties should return live collections.</span></span>

 <span data-ttu-id="5a88a-154">屬性 getter 應該是非常輕量的作業。</span><span class="sxs-lookup"><span data-stu-id="5a88a-154">Property getters should be very lightweight operations.</span></span> <span data-ttu-id="5a88a-155">傳回快照集需要在 O （n）運算中建立內部集合的複本。</span><span class="sxs-lookup"><span data-stu-id="5a88a-155">Returning a snapshot requires creating a copy of an internal collection in an O(n) operation.</span></span>

 <span data-ttu-id="5a88a-156">✔️確實使用快照集集合或即時 `IEnumerable<T>` （或其子類型）來代表暫時性的集合（也就是，在不明確修改集合的情況下可以變更）。</span><span class="sxs-lookup"><span data-stu-id="5a88a-156">✔️ DO use either a snapshot collection or a live `IEnumerable<T>` (or its subtype) to represent collections that are volatile (i.e., that can change without explicitly modifying the collection).</span></span>

 <span data-ttu-id="5a88a-157">一般來說，代表共用資源的所有集合（例如目錄中的檔案）都是變動的。</span><span class="sxs-lookup"><span data-stu-id="5a88a-157">In general, all collections representing a shared resource (e.g., files in a directory) are volatile.</span></span> <span data-ttu-id="5a88a-158">這類集合非常難以或無法實作為即時集合，除非它只是順向列舉值。</span><span class="sxs-lookup"><span data-stu-id="5a88a-158">Such collections are very difficult or impossible to implement as live collections unless the implementation is simply a forward-only enumerator.</span></span>

## <a name="choosing-between-arrays-and-collections"></a><span data-ttu-id="5a88a-159">在陣列與集合之間選擇</span><span class="sxs-lookup"><span data-stu-id="5a88a-159">Choosing Between Arrays and Collections</span></span>
 <span data-ttu-id="5a88a-160">✔️偏好針對陣列進行集合。</span><span class="sxs-lookup"><span data-stu-id="5a88a-160">✔️ DO prefer collections over arrays.</span></span>

 <span data-ttu-id="5a88a-161">集合可讓您更充分掌控內容、隨著時間而演變，而且更為有用。</span><span class="sxs-lookup"><span data-stu-id="5a88a-161">Collections provide more control over contents, can evolve over time, and are more usable.</span></span> <span data-ttu-id="5a88a-162">此外，不建議針對唯讀案例使用陣列，因為複製陣列的成本是「不」。</span><span class="sxs-lookup"><span data-stu-id="5a88a-162">In addition, using arrays for read-only scenarios is discouraged because the cost of cloning the array is prohibitive.</span></span> <span data-ttu-id="5a88a-163">可用性研究顯示，有些開發人員會覺得使用以集合為基礎的 Api 更加熟悉。</span><span class="sxs-lookup"><span data-stu-id="5a88a-163">Usability studies have shown that some developers feel more comfortable using collection-based APIs.</span></span>

 <span data-ttu-id="5a88a-164">不過，如果您正在開發低層級的 Api，則使用陣列來進行讀寫案例可能會是較好的方式。</span><span class="sxs-lookup"><span data-stu-id="5a88a-164">However, if you are developing low-level APIs, it might be better to use arrays for read-write scenarios.</span></span> <span data-ttu-id="5a88a-165">陣列的記憶體使用量較小，這有助於減少工作集，而且陣列中的元素存取速度較快，因為它是由執行時間優化。</span><span class="sxs-lookup"><span data-stu-id="5a88a-165">Arrays have a smaller memory footprint, which helps reduce the working set, and access to elements in an array is faster because it is optimized by the runtime.</span></span>

 <span data-ttu-id="5a88a-166">✔️考慮在低層級 Api 中使用陣列，以將記憶體耗用量降到最低，並將效能最大化。</span><span class="sxs-lookup"><span data-stu-id="5a88a-166">✔️ CONSIDER using arrays in low-level APIs to minimize memory consumption and maximize performance.</span></span>

 <span data-ttu-id="5a88a-167">✔️確實使用位元組陣列，而不是位元組的集合。</span><span class="sxs-lookup"><span data-stu-id="5a88a-167">✔️ DO use byte arrays instead of collections of bytes.</span></span>

 <span data-ttu-id="5a88a-168">❌如果屬性必須在每次呼叫屬性 getter 時傳回新的陣列（例如內部陣列的複本），請勿使用屬性的陣列。</span><span class="sxs-lookup"><span data-stu-id="5a88a-168">❌ DO NOT use arrays for properties if the property would have to return a new array (e.g., a copy of an internal array) every time the property getter is called.</span></span>

## <a name="implementing-custom-collections"></a><span data-ttu-id="5a88a-169">執行自訂集合</span><span class="sxs-lookup"><span data-stu-id="5a88a-169">Implementing Custom Collections</span></span>
 <span data-ttu-id="5a88a-170">✔️ `Collection<T>` `ReadOnlyCollection<T>` `KeyedCollection<TKey,TItem>` 在設計新的集合時，請考慮從、或繼承。</span><span class="sxs-lookup"><span data-stu-id="5a88a-170">✔️ CONSIDER inheriting from `Collection<T>`, `ReadOnlyCollection<T>`, or `KeyedCollection<TKey,TItem>` when designing new collections.</span></span>

 <span data-ttu-id="5a88a-171">✔️ `IEnumerable<T>` 在設計新的集合時執行。</span><span class="sxs-lookup"><span data-stu-id="5a88a-171">✔️ DO implement `IEnumerable<T>` when designing new collections.</span></span> <span data-ttu-id="5a88a-172">請考慮 `ICollection<T>` `IList<T>` 在合理的地方執行或。</span><span class="sxs-lookup"><span data-stu-id="5a88a-172">Consider implementing `ICollection<T>` or even `IList<T>` where it makes sense.</span></span>

 <span data-ttu-id="5a88a-173">在執行這類自訂集合時，請盡可能遵循和所建立的 API 模式 `Collection<T>` `ReadOnlyCollection<T>` 。</span><span class="sxs-lookup"><span data-stu-id="5a88a-173">When implementing such custom collection, follow the API pattern established by `Collection<T>` and `ReadOnlyCollection<T>` as closely as possible.</span></span> <span data-ttu-id="5a88a-174">也就是說，請明確地執行相同的成員，將這些參數命名為這兩個集合的名稱，依此類推。</span><span class="sxs-lookup"><span data-stu-id="5a88a-174">That is, implement the same members explicitly, name the parameters like these two collections name them, and so on.</span></span>

 <span data-ttu-id="5a88a-175">✔️請考慮執行非泛型集合介面（ `IList` 和 `ICollection` ），如果集合通常會傳遞給採用這些介面做為輸入的 api。</span><span class="sxs-lookup"><span data-stu-id="5a88a-175">✔️ CONSIDER implementing nongeneric collection interfaces (`IList` and `ICollection`) if the collection will often be passed to APIs taking these interfaces as input.</span></span>

 <span data-ttu-id="5a88a-176">❌避免在具有與集合概念無關之複雜 Api 的類型上，執行集合介面。</span><span class="sxs-lookup"><span data-stu-id="5a88a-176">❌ AVOID implementing collection interfaces on types with complex APIs unrelated to the concept of a collection.</span></span>

 <span data-ttu-id="5a88a-177">❌請勿繼承自非泛型基底集合，例如 `CollectionBase` 。</span><span class="sxs-lookup"><span data-stu-id="5a88a-177">❌ DO NOT inherit from nongeneric base collections such as `CollectionBase`.</span></span> <span data-ttu-id="5a88a-178">請改用 `Collection<T>`、`ReadOnlyCollection<T>` 和 `KeyedCollection<TKey,TItem>`。</span><span class="sxs-lookup"><span data-stu-id="5a88a-178">Use `Collection<T>`, `ReadOnlyCollection<T>`, and `KeyedCollection<TKey,TItem>` instead.</span></span>

### <a name="naming-custom-collections"></a><span data-ttu-id="5a88a-179">命名自訂集合</span><span class="sxs-lookup"><span data-stu-id="5a88a-179">Naming Custom Collections</span></span>
 <span data-ttu-id="5a88a-180">建立的集合（實 `IEnumerable` 作為型別）主要有兩個原因：（1）建立具有結構特定作業的新資料結構，以及通常與現有資料結構（例如、、、）不同的效能特性 <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.LinkedList%601> <xref:System.Collections.Generic.Stack%601> ，以及（2）建立用於保存特定專案集（例如）的特製化集合 <xref:System.Collections.Specialized.StringCollection> 。</span><span class="sxs-lookup"><span data-stu-id="5a88a-180">Collections (types that implement `IEnumerable`) are created mainly for two reasons: (1) to create a new data structure with structure-specific operations and often different performance characteristics than existing data structures (e.g.,  <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.LinkedList%601>, <xref:System.Collections.Generic.Stack%601>), and (2) to create a specialized collection for holding a specific set of items (e.g.,  <xref:System.Collections.Specialized.StringCollection>).</span></span> <span data-ttu-id="5a88a-181">資料結構最常用於應用程式和程式庫的內部執行。</span><span class="sxs-lookup"><span data-stu-id="5a88a-181">Data structures are most often used in the internal implementation of applications and libraries.</span></span> <span data-ttu-id="5a88a-182">專門的集合主要是在 Api 中公開（作為屬性和參數類型）。</span><span class="sxs-lookup"><span data-stu-id="5a88a-182">Specialized collections are mainly to be exposed in APIs (as property and parameter types).</span></span>

 <span data-ttu-id="5a88a-183">✔️在執行或的抽象概念名稱中使用「字典」 `IDictionary` 尾碼 `IDictionary<TKey,TValue>` 。</span><span class="sxs-lookup"><span data-stu-id="5a88a-183">✔️ DO use the "Dictionary" suffix in names of abstractions implementing `IDictionary` or `IDictionary<TKey,TValue>`.</span></span>

 <span data-ttu-id="5a88a-184">✔️確實在實作為型別（或其子系）的型別名稱中使用「集合」尾碼 `IEnumerable` ，並代表專案清單。</span><span class="sxs-lookup"><span data-stu-id="5a88a-184">✔️ DO use the "Collection" suffix in names of types implementing `IEnumerable` (or any of its descendants) and representing a list of items.</span></span>

 <span data-ttu-id="5a88a-185">✔️請針對自訂資料結構使用適當的資料結構名稱。</span><span class="sxs-lookup"><span data-stu-id="5a88a-185">✔️ DO use the appropriate data structure name for custom data structures.</span></span>

 <span data-ttu-id="5a88a-186">❌請避免在集合抽象的名稱中使用任何尾碼，例如 "Linkedlist<t>" 或 "Hashtable"。</span><span class="sxs-lookup"><span data-stu-id="5a88a-186">❌ AVOID using any suffixes implying particular implementation, such as "LinkedList" or "Hashtable," in names of collection abstractions.</span></span>

 <span data-ttu-id="5a88a-187">✔️考慮在集合名稱前面加上專案類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="5a88a-187">✔️ CONSIDER prefixing collection names with the name of the item type.</span></span> <span data-ttu-id="5a88a-188">例如，儲存類型 `Address` （執行）之專案的集合 `IEnumerable<Address>` 應該命名為 `AddressCollection` 。</span><span class="sxs-lookup"><span data-stu-id="5a88a-188">For example, a collection storing items of type `Address` (implementing `IEnumerable<Address>`) should be named `AddressCollection`.</span></span> <span data-ttu-id="5a88a-189">如果專案類型是介面，則可以省略專案類型的 "I" 前置詞。</span><span class="sxs-lookup"><span data-stu-id="5a88a-189">If the item type is an interface, the "I" prefix of the item type can be omitted.</span></span> <span data-ttu-id="5a88a-190">因此， <xref:System.IDisposable> 可以呼叫專案的集合 `DisposableCollection` 。</span><span class="sxs-lookup"><span data-stu-id="5a88a-190">Thus, a collection of <xref:System.IDisposable> items can be called `DisposableCollection`.</span></span>

 <span data-ttu-id="5a88a-191">如果對應的可寫入集合可能已加入或已存在於架構中，✔️請考慮在唯讀集合的名稱中使用 "ReadOnly" 前置詞。</span><span class="sxs-lookup"><span data-stu-id="5a88a-191">✔️ CONSIDER using the "ReadOnly" prefix in names of read-only collections if a corresponding writeable collection might be added or already exists in the framework.</span></span>

 <span data-ttu-id="5a88a-192">例如，應呼叫字串的唯讀集合 `ReadOnlyStringCollection` 。</span><span class="sxs-lookup"><span data-stu-id="5a88a-192">For example, a read-only collection of strings should be called `ReadOnlyStringCollection`.</span></span>

 <span data-ttu-id="5a88a-193">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="5a88a-193">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="5a88a-194">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。\*\*</span><span class="sxs-lookup"><span data-stu-id="5a88a-194">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="5a88a-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a88a-195">See also</span></span>

- [<span data-ttu-id="5a88a-196">架構設計方針</span><span class="sxs-lookup"><span data-stu-id="5a88a-196">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="5a88a-197">使用指導方針</span><span class="sxs-lookup"><span data-stu-id="5a88a-197">Usage Guidelines</span></span>](usage-guidelines.md)
