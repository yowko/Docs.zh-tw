---
title: 集合方針
ms.date: 10/22/2008
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
ms.openlocfilehash: 2306462d933e71d0d23021a0e036e8cc23100c68
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821082"
---
# <a name="guidelines-for-collections"></a>集合方針
任何專為操作一組具有一般特性的物件而設計的型別，都可以被視為一個集合。 這類型別幾乎一律適合用來執行 <xref:System.Collections.IEnumerable> 或 <xref:System.Collections.Generic.IEnumerable%601> ，所以在本節中，我們只會考慮將這些介面的其中一個或兩個都實作為集合的類型。

 ❌ 請勿在公用 Api 中使用弱式型別集合。

 所有傳回值的型別和代表收集項目的參數都應該是確切的專案類型，而不是它的任何基底類型 (這只適用于集合) 的公用成員。

 ❌ 請勿 <xref:System.Collections.ArrayList> <xref:System.Collections.Generic.List%601> 在公用 api 中使用或。

 這些類型是設計用來內部執行的資料結構，而不是公用 Api。 `List<T>` 已針對效能和強大功能進行優化，以 cleanness Api 和彈性。 例如，如果您傳回 `List<T>` ，當用戶端程式代碼修改集合時，您將無法接收通知。 此外，也 `List<T>` 會公開許多 <xref:System.Collections.Generic.List%601.BinarySearch%2A> 在許多情況下都不實用或適用的成員（例如）。 下列兩節描述特別針對公用 Api 中使用所設計)  (抽象類別型。

 ❌ 請勿 `Hashtable` `Dictionary<TKey,TValue>` 在公用 api 中使用或。

 這些類型是設計用來內部執行的資料結構。 公用 Api 應該使用 <xref:System.Collections.IDictionary> 、 `IDictionary <TKey, TValue>` 或執行一或兩個介面的自訂類型。

 ❌ 請勿使用 <xref:System.Collections.Generic.IEnumerator%601> 、 <xref:System.Collections.IEnumerator> 或任何其他實作為這些介面的型別，除了方法的傳回型別以外 `GetEnumerator` 。

 從以外的方法傳回列舉值的類型， `GetEnumerator` 不能與語句一起使用 `foreach` 。

 ❌ 請勿同時 `IEnumerator<T>` `IEnumerable<T>` 在相同的類型上執行和。 這同樣適用于非泛型介面 `IEnumerator` 和 `IEnumerable` 。

## <a name="collection-parameters"></a>集合參數
 ✔️請盡可能使用最少的特製化型別作為參數類型。 大部分採用集合做為參數的成員都會使用 `IEnumerable<T>` 介面。

 ❌ 請避免使用 <xref:System.Collections.Generic.ICollection%601> 或 <xref:System.Collections.ICollection> 作為參數，只是用來存取 `Count` 屬性。

 相反地，請考慮使用 `IEnumerable<T>` 或 `IEnumerable` ，以動態方式檢查物件是否為 `ICollection<T>` 或 `ICollection` 。

## <a name="collection-properties-and-return-values"></a>集合屬性和傳回值
 ❌ 請勿提供可設定的集合屬性。

 使用者可以先清除集合，然後加入新的內容，以取代集合的內容。 如果將整個集合取代為常見的案例，請考慮在 `AddRange` 集合上提供方法。

 ✔️請使用 `Collection<T>` 或的子類別 `Collection<T>` ，以取得代表讀取/寫入集合的屬性或傳回值。

 如果不 `Collection<T>` 符合某些需求 (例如，集合不能實 <xref:System.Collections.IList>) ，請執行、或來使用自訂集合 `IEnumerable<T>` `ICollection<T>` <xref:System.Collections.Generic.IList%601> 。

 ✔️請使用 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 、或的子類別， `ReadOnlyCollection<T>` 或在少數案例中， `IEnumerable<T>` 代表唯讀集合的屬性或傳回值。

 一般來說，偏好使用 `ReadOnlyCollection<T>` 。 如果它不符合某些需求 (例如，集合不能實 `IList`) ，請執行、或來使用自訂集合 `IEnumerable<T>` `ICollection<T>` `IList<T>` 。 如果您執行的是自訂唯讀集合，則會執行， `ICollection<T>.IsReadOnly` 以傳回 `true` 。

 如果您確定您要支援的唯一案例是僅向前反覆運算，您可以直接使用 `IEnumerable<T>` 。

 ✔️考慮使用泛型基底集合的子類別，而不是直接使用集合。

 這可讓您取得更好的名稱，以及新增不存在於基底集合類型上的 helper 成員。 這特別適用于高層級 Api。

 ✔️考慮 `Collection<T>` `ReadOnlyCollection<T>` 從非常常用的方法和屬性傳回或的子類別。

 這可讓您在未來加入 helper 方法或變更集合的執行。

 ✔️如果儲存在集合中的專案具有唯一的索引鍵 (名稱、識別碼等 ) ，請考慮使用索引集合。 索引集合是可由整數和索引鍵編制索引的集合，通常是藉由繼承自來執行 `KeyedCollection<TKey,TItem>` 。

 索引集合通常會有較大的記憶體佔用量，如果記憶體額外負荷超過擁有金鑰的優點，則不應使用。

 ❌ 請勿從集合屬性或傳回集合的方法傳回 null 值。 改為傳回空集合或空的陣列。

 一般規則是 null 和空白 (0 專案) 集合或陣列應視為相同。

### <a name="snapshots-versus-live-collections"></a>快照集與即時集合
 代表某個時間點狀態的集合稱為快照集集合。 例如，包含資料庫查詢所傳回之資料列的集合將會是快照集。 一律代表目前狀態的集合稱為即時集合。 例如， `ComboBox` 專案集合是即時集合。

 ❌ 請勿從屬性傳回快照集集合。 屬性應該會傳回即時集合。

 屬性 getter 應該是非常輕量的作業。 傳回快照集需要在 O (n) 作業中建立內部集合的複本。

 ✔️請使用快照集集合或即時 `IEnumerable<T>` (或它的子類型) 來表示變動 (的集合，也就是可以變更，而不需要明確地修改集合) 。

 一般來說，代表共用資源的所有集合 (例如，目錄) 中的檔案都是暫時性的。 這類集合很難或無法實作為即時集合，除非實作為僅向前的列舉值。

## <a name="choosing-between-arrays-and-collections"></a>在陣列和集合之間進行選擇
 ✔️會偏好陣列的集合。

 集合可讓您更充分掌控內容、可以隨時間演進，而且更容易使用。 此外，不建議針對唯讀案例使用陣列，因為複製陣列的成本很高。 可用性研究顯示某些開發人員更熟悉使用以集合為基礎的 Api。

 但是，如果您正在開發低層級的 Api，則使用陣列來進行讀寫案例可能比較理想。 陣列擁有較小的記憶體使用量，有助於減少工作集，而對陣列中的元素的存取會更快，因為它是由執行時間優化。

 ✔️考慮使用低層級 Api 中的陣列，將記憶體耗用量降至最低，並將效能最大化。

 ✔️確實使用位元組陣列，而不是位元組的集合。

 ❌ 如果屬性必須傳回新陣列 (例如，在每次呼叫屬性 getter 時) 內部陣列的複本，請不要使用屬性的陣列。

## <a name="implementing-custom-collections"></a>執行自訂集合
 ✔️ `Collection<T>` `ReadOnlyCollection<T>` `KeyedCollection<TKey,TItem>` 在設計新的集合時，請考慮從、或進行繼承。

 ✔️ `IEnumerable<T>` 在設計新的集合時，就會執行。 請考慮採用 `ICollection<T>` 或甚至 `IList<T>` 是有意義的地方。

 在執行這類自訂集合時，請遵循和盡可能緊密地建立的 API 模式 `Collection<T>` `ReadOnlyCollection<T>` 。 也就是說，明確地執行相同的成員，將參數命名為這兩個集合的名稱，依此類推。

 ✔️考慮採用非泛型集合介面 (`IList` 和 `ICollection`) ，如果集合通常會傳遞至採用這些介面作為輸入的 api。

 ❌ 避免在具有與集合概念不相關之複雜 Api 的類型上執行集合介面。

 ❌ 請勿繼承自非泛型基底集合，例如 `CollectionBase` 。 請改用 `Collection<T>`、`ReadOnlyCollection<T>` 和 `KeyedCollection<TKey,TItem>`。

### <a name="naming-custom-collections"></a>命名自訂集合
 因為有 `IEnumerable` 兩個原因，所以會建立實) 的集合 (類型： (1) 以結構專屬的作業建立新的資料結構，而且通常與現有的資料結構有不同的效能特性 (例如、  <xref:System.Collections.Generic.List%601> 、 <xref:System.Collections.Generic.LinkedList%601> 、 <xref:System.Collections.Generic.Stack%601>) 和 (2) 建立特殊集合來保存一組特定的專案 (例如，  <xref:System.Collections.Specialized.StringCollection>) 。 資料結構最常用於應用程式和程式庫的內部執行。 特殊化的集合主要是在 Api 中公開 (作為屬性和參數類型) 。

 ✔️請在執行或的抽象概念名稱中使用 "Dictionary" 尾碼 `IDictionary` `IDictionary<TKey,TValue>` 。

 ✔️請在實 (的型別名稱或任何其子系) 的名稱中使用 "Collection" 後置詞 `IEnumerable` ，並代表專案清單。

 ✔️請為自訂資料結構使用適當的資料結構名稱。

 ❌ 請避免使用任何尾碼來隱含特定的實作為集合抽象的名稱，例如 "LinkedList" 或 "Hashtable"。

 ✔️考慮在集合名稱前面加上專案類型的名稱。 例如，儲存型別 (的專案集合 `Address` `IEnumerable<Address>` 應該命名為) `AddressCollection` 。 如果專案類型是介面，則可以省略專案類型的 "I" 前置詞。 因此， <xref:System.IDisposable> 可以呼叫專案的集合 `DisposableCollection` 。

 如果對應的可寫入集合可能已存在於架構中，✔️請考慮在唯讀集合的名稱中使用 "ReadOnly" 前置詞。

 例如，應呼叫字串的唯讀集合 `ReadOnlyStringCollection` 。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [架構設計指導方針](index.md)
- [使用指導方針](usage-guidelines.md)
