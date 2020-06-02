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
# <a name="guidelines-for-collections"></a>集合方針
專為操作具有一些通用特性之物件群組而設計的任何類型，都可視為集合。 這種類型幾乎都適合用來執行 <xref:System.Collections.IEnumerable> 或 <xref:System.Collections.Generic.IEnumerable%601> ，因此在本節中，我們只會考慮將其中一個或兩個介面都實作為集合的類型。

 ❌請勿在公用 Api 中使用弱式類型集合。

 所有代表集合專案的傳回值和參數類型，都應該是確切的專案類型，而不是其任何基底類型（這僅適用于集合的公用成員）。

 ❌請勿 <xref:System.Collections.ArrayList> <xref:System.Collections.Generic.List%601> 在公用 api 中使用或。

 這些類型是設計用來在內部執行時使用的資料結構，而不是在公用 Api 中。 `List<T>`已針對效能和能力進行優化，並以 Api 和彈性的 cleanness 成本為代價。 例如，如果您傳回 `List<T>` ，當用戶端程式代碼修改集合時，您就不會收到通知。 此外，也 `List<T>` 會公開許多 <xref:System.Collections.Generic.List%601.BinarySearch%2A> 在許多情況下都不實用或適用的成員，例如。 下列兩節描述專為在公用 Api 中使用而設計的類型（抽象）。

 ❌請勿 `Hashtable` `Dictionary<TKey,TValue>` 在公用 api 中使用或。

 這些類型是設計用來在內部執行時使用的資料結構。 公用 Api 應使用 <xref:System.Collections.IDictionary> 、 `IDictionary <TKey, TValue>` 或執行一或兩個介面的自訂類型。

 ❌除了方法的傳回型別以外，請不要使用 <xref:System.Collections.Generic.IEnumerator%601> 、 <xref:System.Collections.IEnumerator> 或任何其他實作用其中任何介面的型別 `GetEnumerator` 。

 從以外的方法傳回枚舉器的類型 `GetEnumerator` 無法搭配 `foreach` 語句使用。

 ❌請勿 `IEnumerator<T>` `IEnumerable<T>` 在相同的類型上同時執行和。 這同樣適用于非泛型介面 `IEnumerator` 和 `IEnumerable` 。

## <a name="collection-parameters"></a>集合參數
 ✔️可以使用最少特殊化的型別做為參數型別。 大部分以集合作為參數的成員都會使用 `IEnumerable<T>` 介面。

 ❌請避免使用 <xref:System.Collections.Generic.ICollection%601> 或 <xref:System.Collections.ICollection> 做為參數，只是用來存取 `Count` 屬性。

 相反地，請考慮使用 `IEnumerable<T>` 或 `IEnumerable` ，並動態檢查物件是否執行 `ICollection<T>` 或 `ICollection` 。

## <a name="collection-properties-and-return-values"></a>集合屬性和傳回值
 ❌請勿提供可設定的集合屬性。

 使用者可以藉由先清除集合，然後再新增新內容，來取代集合的內容。 如果取代整個集合是常見的案例，請考慮在 `AddRange` 集合上提供方法。

 ✔️請使用 `Collection<T>` 或的子類別 `Collection<T>` ，以取得代表讀取/寫入集合的屬性或傳回值。

 如果不 `Collection<T>` 符合某些需求（例如，集合不得執行 <xref:System.Collections.IList> ），請藉由執行、或來使用自訂 `IEnumerable<T>` 集合 `ICollection<T>` <xref:System.Collections.Generic.IList%601> 。

 ✔️請使用 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 、的子類別 `ReadOnlyCollection<T>` ，或在少數情況下， `IEnumerable<T>` 針對代表唯讀集合的屬性或傳回值。

 一般來說，偏好 `ReadOnlyCollection<T>` 。 如果不符合某些需求（例如，集合不得執行 `IList` ），請藉由執行、或來使用自訂集合 `IEnumerable<T>` `ICollection<T>` `IList<T>` 。 如果您確實執行自訂的唯讀集合，則會執行 `ICollection<T>.IsReadOnly` 來傳回 `true` 。

 如果您確定您想要支援的唯一案例是順向反復專案，您可以直接使用 `IEnumerable<T>` 。

 ✔️考慮使用泛型基底集合的子類別，而不是直接使用集合。

 這可讓您取得更好的名稱，以及加入不存在於基底集合類型上的 helper 成員。 這特別適用于高階 Api。

 ✔️考慮 `Collection<T>` `ReadOnlyCollection<T>` 從非常常用的方法和屬性傳回或的子類別。

 這可讓您在未來新增 helper 方法或變更集合的執行。

 ✔️如果集合中儲存的專案具有唯一索引鍵（名稱、識別碼等），請考慮使用金鑰集合。 「索引集合」是一種集合，可以透過整數和金鑰來編制索引，而且通常是藉由繼承自來執行 `KeyedCollection<TKey,TItem>` 。

 索引集合通常會有較大的記憶體佔用量，如果記憶體額外負荷高於擁有金鑰的優點，則不應使用。

 ❌請勿從集合屬性或傳回集合的方法傳回 null 值。 改為傳回空的集合或空陣列。

 一般規則是 null 和空的（0專案）集合或陣列應視為相同。

### <a name="snapshots-versus-live-collections"></a>快照集與即時集合
 代表某個時間點之狀態的集合稱為快照集集合。 例如，包含資料庫查詢所傳回之資料列的集合會是快照集。 一律代表目前狀態的集合稱為「即時集合」。 例如，專案的集合 `ComboBox` 是即時集合。

 ❌不要從屬性傳回快照集集合。 屬性應該會傳回即時集合。

 屬性 getter 應該是非常輕量的作業。 傳回快照集需要在 O （n）運算中建立內部集合的複本。

 ✔️確實使用快照集集合或即時 `IEnumerable<T>` （或其子類型）來代表暫時性的集合（也就是，在不明確修改集合的情況下可以變更）。

 一般來說，代表共用資源的所有集合（例如目錄中的檔案）都是變動的。 這類集合非常難以或無法實作為即時集合，除非它只是順向列舉值。

## <a name="choosing-between-arrays-and-collections"></a>在陣列與集合之間選擇
 ✔️偏好針對陣列進行集合。

 集合可讓您更充分掌控內容、隨著時間而演變，而且更為有用。 此外，不建議針對唯讀案例使用陣列，因為複製陣列的成本是「不」。 可用性研究顯示，有些開發人員會覺得使用以集合為基礎的 Api 更加熟悉。

 不過，如果您正在開發低層級的 Api，則使用陣列來進行讀寫案例可能會是較好的方式。 陣列的記憶體使用量較小，這有助於減少工作集，而且陣列中的元素存取速度較快，因為它是由執行時間優化。

 ✔️考慮在低層級 Api 中使用陣列，以將記憶體耗用量降到最低，並將效能最大化。

 ✔️確實使用位元組陣列，而不是位元組的集合。

 ❌如果屬性必須在每次呼叫屬性 getter 時傳回新的陣列（例如內部陣列的複本），請勿使用屬性的陣列。

## <a name="implementing-custom-collections"></a>執行自訂集合
 ✔️ `Collection<T>` `ReadOnlyCollection<T>` `KeyedCollection<TKey,TItem>` 在設計新的集合時，請考慮從、或繼承。

 ✔️ `IEnumerable<T>` 在設計新的集合時執行。 請考慮 `ICollection<T>` `IList<T>` 在合理的地方執行或。

 在執行這類自訂集合時，請盡可能遵循和所建立的 API 模式 `Collection<T>` `ReadOnlyCollection<T>` 。 也就是說，請明確地執行相同的成員，將這些參數命名為這兩個集合的名稱，依此類推。

 ✔️請考慮執行非泛型集合介面（ `IList` 和 `ICollection` ），如果集合通常會傳遞給採用這些介面做為輸入的 api。

 ❌避免在具有與集合概念無關之複雜 Api 的類型上，執行集合介面。

 ❌請勿繼承自非泛型基底集合，例如 `CollectionBase` 。 請改用 `Collection<T>`、`ReadOnlyCollection<T>` 和 `KeyedCollection<TKey,TItem>`。

### <a name="naming-custom-collections"></a>命名自訂集合
 建立的集合（實 `IEnumerable` 作為型別）主要有兩個原因：（1）建立具有結構特定作業的新資料結構，以及通常與現有資料結構（例如、、、）不同的效能特性 <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.LinkedList%601> <xref:System.Collections.Generic.Stack%601> ，以及（2）建立用於保存特定專案集（例如）的特製化集合 <xref:System.Collections.Specialized.StringCollection> 。 資料結構最常用於應用程式和程式庫的內部執行。 專門的集合主要是在 Api 中公開（作為屬性和參數類型）。

 ✔️在執行或的抽象概念名稱中使用「字典」 `IDictionary` 尾碼 `IDictionary<TKey,TValue>` 。

 ✔️確實在實作為型別（或其子系）的型別名稱中使用「集合」尾碼 `IEnumerable` ，並代表專案清單。

 ✔️請針對自訂資料結構使用適當的資料結構名稱。

 ❌請避免在集合抽象的名稱中使用任何尾碼，例如 "Linkedlist<t>" 或 "Hashtable"。

 ✔️考慮在集合名稱前面加上專案類型的名稱。 例如，儲存類型 `Address` （執行）之專案的集合 `IEnumerable<Address>` 應該命名為 `AddressCollection` 。 如果專案類型是介面，則可以省略專案類型的 "I" 前置詞。 因此， <xref:System.IDisposable> 可以呼叫專案的集合 `DisposableCollection` 。

 如果對應的可寫入集合可能已加入或已存在於架構中，✔️請考慮在唯讀集合的名稱中使用 "ReadOnly" 前置詞。

 例如，應呼叫字串的唯讀集合 `ReadOnlyStringCollection` 。

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。**

## <a name="see-also"></a>另請參閱

- [架構設計方針](index.md)
- [使用指導方針](usage-guidelines.md)
