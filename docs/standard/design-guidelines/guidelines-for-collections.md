---
title: 集合方針
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
ms.openlocfilehash: 50497de6569b448ab036af8a1fbf76a47565e2bb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741873"
---
# <a name="guidelines-for-collections"></a>集合方針
專為操作具有一些通用特性之物件群組而設計的任何類型，都可視為集合。 這種類型幾乎都適合用來執行 <xref:System.Collections.IEnumerable> 或 <xref:System.Collections.Generic.IEnumerable%601>，因此在本節中，我們只會考慮將其中一個或兩個介面都實作為集合的類型。

 ❌ 請勿在公用 Api 中使用弱式類型集合。

 所有代表集合專案的傳回值和參數類型，都應該是確切的專案類型，而不是其任何基底類型（這僅適用于集合的公用成員）。

 ❌ 請勿在公用 Api 中使用 <xref:System.Collections.ArrayList> 或 <xref:System.Collections.Generic.List%601>。

 這些類型是設計用來在內部執行時使用的資料結構，而不是在公用 Api 中。 `List<T>` 已針對效能和能力進行優化，但 cleanness Api 和彈性的成本。 例如，如果您傳回 `List<T>`，當用戶端程式代碼修改集合時，您就不會收到通知。 此外，`List<T>` 會公開許多在許多情況下都不實用或適用的成員，例如 <xref:System.Collections.Generic.List%601.BinarySearch%2A>。 下列兩節描述專為在公用 Api 中使用而設計的類型（抽象）。

 ❌ 請勿在公用 Api 中使用 `Hashtable` 或 `Dictionary<TKey,TValue>`。

 這些類型是設計用來在內部執行時使用的資料結構。 公用 Api 應該使用 <xref:System.Collections.IDictionary>、`IDictionary <TKey, TValue>`，或可執行一或兩個介面的自訂類型。

 ❌ 不使用 <xref:System.Collections.Generic.IEnumerator%601>、<xref:System.Collections.IEnumerator>或任何其他實作為這些介面的其他型別，但 `GetEnumerator` 方法的傳回型別除外。

 從 `GetEnumerator` 以外的方法傳回枚舉器的類型，不能與 `foreach` 語句搭配使用。

 ❌ 不會同時在相同的類型上同時執行 `IEnumerator<T>` 和 `IEnumerable<T>`。 這同樣適用于非泛型介面 `IEnumerator` 和 `IEnumerable`。

## <a name="collection-parameters"></a>集合參數
 ✔️可以使用最少特殊化的型別做為參數型別。 大部分以集合作為參數的成員都會使用 `IEnumerable<T>` 介面。

 ❌ 避免使用 <xref:System.Collections.Generic.ICollection%601> 或 <xref:System.Collections.ICollection> 做為參數，只是用來存取 `Count` 屬性。

 相反地，請考慮使用 `IEnumerable<T>` 或 `IEnumerable`，並動態檢查物件是否會執行 `ICollection<T>` 或 `ICollection`。

## <a name="collection-properties-and-return-values"></a>集合屬性和傳回值
 ❌ 不提供可設定的集合屬性。

 使用者可以藉由先清除集合，然後再新增新內容，來取代集合的內容。 如果取代整個集合是常見的案例，請考慮在集合上提供 `AddRange` 方法。

 ✔️確實使用 `Collection<T>` 或 `Collection<T>` 的子類別，以取得代表讀取/寫入集合的屬性或傳回值。

 如果 `Collection<T>` 不符合某些需求（例如，集合不能實作為 <xref:System.Collections.IList>），請藉由執行 `IEnumerable<T>`、`ICollection<T>`或 <xref:System.Collections.Generic.IList%601>來使用自訂集合。

 ✔️確實使用 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>、`ReadOnlyCollection<T>`的子類別，或在罕見的情況下 `IEnumerable<T>` 屬性或代表唯讀集合的傳回值。

 一般來說，偏好 `ReadOnlyCollection<T>`。 如果不符合某些需求（例如，集合不能實作為 `IList`），請藉由執行 `IEnumerable<T>`、`ICollection<T>`或 `IList<T>`來使用自訂集合。 如果您確實執行自訂的唯讀集合，請執行 `ICollection<T>.IsReadOnly` 以傳回 `true`。

 如果您確定您想要支援的唯一案例是順向反復專案，您可以直接使用 `IEnumerable<T>`。

 ✔️考慮使用泛型基底集合的子類別，而不是直接使用集合。

 這可讓您取得更好的名稱，以及加入不存在於基底集合類型上的 helper 成員。 這特別適用于高階 Api。

 ✔️考慮從非常常用的方法和屬性傳回 `Collection<T>` 或 `ReadOnlyCollection<T>` 的子類別。

 這可讓您在未來新增 helper 方法或變更集合的執行。

 ✔️如果集合中儲存的專案具有唯一索引鍵（名稱、識別碼等），請考慮使用金鑰集合。 「索引集合」是一種集合，可以透過整數和金鑰來編制索引，而且通常是藉由繼承自 `KeyedCollection<TKey,TItem>`來執行。

 索引集合通常會有較大的記憶體佔用量，如果記憶體額外負荷高於擁有金鑰的優點，則不應使用。

 ❌ 不會從集合屬性或傳回集合的方法傳回 null 值。 改為傳回空的集合或空陣列。

 一般規則是 null 和空的（0專案）集合或陣列應視為相同。

### <a name="snapshots-versus-live-collections"></a>快照集與即時集合
 代表某個時間點之狀態的集合稱為快照集集合。 例如，包含資料庫查詢所傳回之資料列的集合會是快照集。 一律代表目前狀態的集合稱為「即時集合」。 例如，`ComboBox` 專案的集合是即時集合。

 ❌ 不會從屬性傳回快照集集合。 屬性應該會傳回即時集合。

 屬性 getter 應該是非常輕量的作業。 傳回快照集需要在 O （n）運算中建立內部集合的複本。

 ✔️確實使用快照集集合或即時 `IEnumerable<T>` （或其子類型）來代表暫時性的集合（也就是在不明確修改集合的情況下可以變更）。

 一般來說，代表共用資源的所有集合（例如目錄中的檔案）都是變動的。 這類集合非常難以或無法實作為即時集合，除非它只是順向列舉值。

## <a name="choosing-between-arrays-and-collections"></a>在陣列與集合之間選擇
 ✔️偏好針對陣列進行集合。

 集合可讓您更充分掌控內容、隨著時間而演變，而且更為有用。 此外，不建議針對唯讀案例使用陣列，因為複製陣列的成本是「不」。 可用性研究顯示，有些開發人員會覺得使用以集合為基礎的 Api 更加熟悉。

 不過，如果您正在開發低層級的 Api，則使用陣列來進行讀寫案例可能會是較好的方式。 陣列的記憶體使用量較小，這有助於減少工作集，而且陣列中的元素存取速度較快，因為它是由執行時間優化。

 ✔️考慮在低層級 Api 中使用陣列，以將記憶體耗用量降到最低，並將效能最大化。

 ✔️確實使用位元組陣列，而不是位元組的集合。

 如果屬性必須在每次呼叫屬性 getter 時傳回新的陣列（例如，內部陣列的複本），則 ❌ 不使用屬性的陣列。

## <a name="implementing-custom-collections"></a>執行自訂集合
 ✔️在設計新的集合時，請考慮從 `Collection<T>`、`ReadOnlyCollection<T>`或 `KeyedCollection<TKey,TItem>` 繼承。

 ✔️在設計新的集合時，執行 `IEnumerable<T>`。 請考慮在合理的地方執行 `ICollection<T>` 或甚至 `IList<T>`。

 在執行這類自訂集合時，請遵循 `Collection<T>` 所建立的 API 模式，並盡可能 `ReadOnlyCollection<T>`。 也就是說，請明確地執行相同的成員，將這些參數命名為這兩個集合的名稱，依此類推。

 ✔️如果集合經常會傳遞給採用這些介面做為輸入的 Api，請考慮執行非泛型集合介面（`IList` 和 `ICollection`）。

 ❌ 避免在具有與集合概念無關之複雜 Api 的類型上，執行集合介面。

 ❌ 不會繼承自非泛型基底集合，例如 `CollectionBase`。 請改用 `Collection<T>`、`ReadOnlyCollection<T>`和 `KeyedCollection<TKey,TItem>`。

### <a name="naming-custom-collections"></a>命名自訂集合
 集合（實 `IEnumerable`的型別）主要是為了兩個原因而建立：（1）建立具有結構特定作業的新資料結構，以及通常與現有資料結構（例如，<xref:System.Collections.Generic.List%601>、<xref:System.Collections.Generic.LinkedList%601>、<xref:System.Collections.Generic.Stack%601>）和（2）不同的效能特性，以建立用於保存特定專案集（例如 <xref:System.Collections.Specialized.StringCollection>）的特殊集合。 資料結構最常用於應用程式和程式庫的內部執行。 專門的集合主要是在 Api 中公開（作為屬性和參數類型）。

 ✔️請在執行 `IDictionary` 或 `IDictionary<TKey,TValue>`的抽象概念名稱中使用「字典」尾碼。

 ✔️請在實 `IEnumerable` （或其子系）的型別名稱中使用 "Collection" 後置詞，並代表專案清單。

 ✔️請針對自訂資料結構使用適當的資料結構名稱。

 ❌ 避免在集合抽象的名稱中使用任何尾碼，例如 "Linkedlist<t>" 或 "Hashtable"。

 ✔️考慮在集合名稱前面加上專案類型的名稱。 例如，儲存類型 `Address` （執行 `IEnumerable<Address>`）之專案的集合應該命名為 `AddressCollection`。 如果專案類型是介面，則可以省略專案類型的 "I" 前置詞。 因此，可以 `DisposableCollection`呼叫 <xref:System.IDisposable> 專案的集合。

 如果對應的可寫入集合可能已加入或已存在於架構中，✔️請考慮在唯讀集合的名稱中使用 "ReadOnly" 前置詞。

 例如，應該 `ReadOnlyStringCollection`呼叫字串的唯讀集合。

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [用法方針](../../../docs/standard/design-guidelines/usage-guidelines.md)
