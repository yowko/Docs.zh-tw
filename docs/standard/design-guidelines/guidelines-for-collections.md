---
title: 集合方針
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3571ebb2fdd2bcdfd8be1f0087d096e01f18790a
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45674087"
---
# <a name="guidelines-for-collections"></a>集合方針
任何型別，專門設計來管理一組具有一些共同的特性的物件可以視為一個集合。 幾乎都是實作這種類型的適當<xref:System.Collections.IEnumerable>或<xref:System.Collections.Generic.IEnumerable%601>，所以在本節中，我們只考慮實作一個或多個這些介面的型別是集合。  
  
 **X DO NOT** 在公用 Api 中使用弱式型別的的集合。  
  
 所有傳回值以及代表集合的項目參數的類型應該是確切的項目類型，不是任何基底類型 （這只適用於集合的公用成員）。  
  
 **X DO NOT** 使用 <xref:System.Collections.ArrayList> 或 <xref:System.Collections.Generic.List%601> 在公用 Api。  
  
 這些類型是設計來在內部實作中，不在公用 Api 中的資料結構。 `List<T>` 已針對效能和但要付出的 Api 和彈性的 cleanness 電源最佳化。 例如，如果您傳回`List<T>`，您將以往無法接收通知，當用戶端程式碼會修改集合。 此外，`List<T>`公開許多成員，例如<xref:System.Collections.Generic.List%601.BinarySearch%2A>，不實用或適用於許多案例。 下列兩節會描述專為使用公用 Api 中的類型 （抽象）。  
  
 **X DO NOT** 使用 `Hashtable` 或 `Dictionary<TKey,TValue>` 在公用 Api。  
  
 這些類型是設計來在內部實作的資料結構。 應該使用公用 Api <xref:System.Collections.IDictionary>， `IDictionary <TKey, TValue>`，或實作一或兩個介面的自訂型別。  
  
 **X DO NOT** 使用 <xref:System.Collections.Generic.IEnumerator%601>， <xref:System.Collections.IEnumerator>，或實作介面，其中除了為傳回類型的任何其他型別 `GetEnumerator` 方法。  
  
 從方法傳回列舉值以外的類型`GetEnumerator`不能搭配`foreach`陳述式。  
  
 **X DO NOT** 同時實作 `IEnumerator<T>` 和 `IEnumerable<T>` 上相同的型別。 這同樣適用於非泛型介面`IEnumerator`和`IEnumerable`。  
  
## <a name="collection-parameters"></a>收集參數  
 **✓ DO** 使用可能的最低特製化類型做為參數類型。 取得集合，作為參數使用的大部分成員`IEnumerable<T>`介面。  
  
 **X AVOID** 使用 <xref:System.Collections.Generic.ICollection%601>或<xref:System.Collections.ICollection> 做為參數，只是為了存取 `Count` 屬性。  
  
 請考慮改用`IEnumerable<T>`或是`IEnumerable`並以動態方式檢查物件是否實作`ICollection<T>`或`ICollection`。  
  
## <a name="collection-properties-and-return-values"></a>集合屬性和傳回值  
 **X DO NOT** 提供可設定的集合屬性。  
  
 使用者可以取代集合的內容，先清除集合，然後再將新的內容。 如果取代整個集合是常見的案例，請考慮提供`AddRange`集合上的方法。  
  
 **✓ DO** 使用 `Collection<T>` 或的子類別 `Collection<T>` 針對屬性或傳回值表示讀取/寫入集合。  
  
 如果`Collection<T>`不符合某些需求 (例如，集合必須不會實作<xref:System.Collections.IList>)，藉由實作使用自訂的集合`IEnumerable<T>`， `ICollection<T>`，或<xref:System.Collections.Generic.IList%601>。  
  
 **✓ DO** 使用 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 的子類別 `ReadOnlyCollection<T>`，或在極少數的情況下 `IEnumerable<T>` 針對屬性或傳回值表示唯讀的集合。  
  
 一般情況下，偏好`ReadOnlyCollection<T>`。 如果不符合某些需求 (例如，集合必須不會實作`IList`)，藉由實作使用自訂的集合`IEnumerable<T>`， `ICollection<T>`，或`IList<T>`。 如果您實作自訂的唯讀集合，實作`ICollection<T>.IsReadOnly`傳回`true`。  
  
 在您會確定只有您會想要支援的案例是順向的反覆項目的情況下，您可以直接使用`IEnumerable<T>`。  
  
 **✓ CONSIDER** 使用泛型基底集合的子類別，而不直接使用集合。  
  
 這可讓更適合的名稱以及加入未出現在基底的集合型別上的 helper 成員。 這是特別適用於高階 Api。  
  
 **✓ CONSIDER** 傳回的子類別 `Collection<T>` 或 `ReadOnlyCollection<T>` 從相當常用的方法和屬性。  
  
 這會讓您可新增 helper 方法，或變更在未來的集合實作。  
  
 **✓ CONSIDER** 使用索引鍵的集合，如果儲存在集合中的項目具有唯一索引鍵 （名稱、 識別碼、 等等。）。 索引的集合是由整數和索引鍵編製的索引，通常由繼承自集合`KeyedCollection<TKey,TItem>`。  
  
 索引的集合通常會較大的記憶體使用量，而且不應在記憶體額外負荷超過索引鍵的效益。  
  
 **X DO NOT** 集合屬性中或從方法傳回集合，傳回 null 值。 而是傳回空集合或空陣列。  
  
 一般規則是，應該是 null 和空的 （0 個項目） 集合或陣列視為相同。  
  
### <a name="snapshots-versus-live-collections"></a>快照集與即時的集合  
 集合表示在某個時間點狀態的時間稱為快照集集合。 例如，包含從資料庫查詢傳回的資料列的集合會是快照集。 集合一律會代表目前的狀態，稱為即時的集合。 比方說，許多`ComboBox`項目是即時的集合。  
  
 **X DO NOT** 屬性從傳回快照集的集合。 屬性應該傳回即時的集合。  
  
 屬性 getter 應該是非常輕量型的作業。 傳回快照集需要 o （n） 作業中建立一份內部集合。  
  
 **✓ DO** 使用快照集收集或即時 `IEnumerable<T>` （或它的子類型） 來表示為變動性的集合 （亦即，可以變更而不需明確修改集合）。  
  
 一般情況下，所有的集合，表示共用的資源 （例如，在目錄中的檔案） 是變動性。 這類集合是很難或無法實作做為即時的集合，除非實作就只是順向的列舉值。  
  
## <a name="choosing-between-arrays-and-collections"></a>陣列和集合之間進行選擇  
 **✓ DO** 集合，而不用陣列。  
  
 集合提供更充分掌控內容，可以隨著時間演進，而且更實用。 此外，因為複製陣列成本高昂，建議使用陣列的唯讀狀態的案例。 可用性研究顯示，有些開發人員會覺得較喜歡使用以集合為基礎的 Api。  
  
 不過，如果您正在開發的低階 Api，它可能是更好讀寫案例中使用陣列項目。 陣列有較小的記憶體耗用量，進而降低工作集，而且陣列中項目的存取速度，因為它會透過執行階段進行最佳化。  
  
 **✓ CONSIDER** 低階 Api 中使用陣列記憶體耗用量降到最低，並將效能最大化。  
  
 **✓ DO** 使用位元組陣列，而不是位元組的集合。  
  
 **X DO NOT** 使用屬性的陣列，如果屬性必須在呼叫屬性 getter 的每次會傳回新的陣列 （例如，內部陣列的複本）。  
  
## <a name="implementing-custom-collections"></a>實作自訂的集合  
 **✓ CONSIDER** 繼承自 `Collection<T>`， `ReadOnlyCollection<T>`，或 `KeyedCollection<TKey,TItem>` 設計新的集合時。  
  
 **✓ DO** 實作 `IEnumerable<T>` 設計新的集合時。 請考慮實作`ICollection<T>`甚至`IList<T>`派得上用場。  
  
 在實作這類的自訂集合時，請依照下列所建立的 API 模式`Collection<T>`和`ReadOnlyCollection<T>`儘可能密集地。 也就是明確地實作相同的成員，為參數命名，例如這兩個集合名稱，依此類推。  
  
 **✓ CONSIDER** 實作非泛型集合介面 (`IList` 和 `ICollection`) 如果集合將通常會傳遞至應用程式開發介面採用這些介面做為輸入。  
  
 **X AVOID** 型別上實作的集合介面具有複雜的應用程式開發介面不相關的概念的集合。  
  
 **X DO NOT** 例如繼承自非泛型基底集合 `CollectionBase`。 使用`Collection<T>`， `ReadOnlyCollection<T>`，和`KeyedCollection<TKey,TItem>`改。  
  
### <a name="naming-custom-collections"></a>命名自訂集合  
 集合 (型別都會實作`IEnumerable`) 會建立主要的原因有二: (1) 若要建立新的資料結構與結構特定作業通常比現有的資料結構的不同效能特性 (例如<xref:System.Collections.Generic.List%601>，<xref:System.Collections.Generic.LinkedList%601>， <xref:System.Collections.Generic.Stack%601>)，以及 (2) 若要建立特製化的集合，用於保存一組特定的項目 (例如<xref:System.Collections.Specialized.StringCollection>)。 在內部實作應用程式和程式庫中最常使用的資料結構。 特製化的集合是主要是為了公開 Api 中 （屬性和參數的型別）。  
  
 **✓ DO** 抽象層實作名稱中使用 「 字典 」 尾碼 `IDictionary` 或 `IDictionary<TKey,TValue>`。  
  
 **✓ DO** 實作的型別名稱中使用"Collection"後置詞 `IEnumerable` （或其任何子代） 及表示項目清單。  
  
 **✓ DO** 使用適當的資料結構名稱的自訂資料結構。  
  
 **X AVOID** 集合的抽象概念的名稱中使用隱含的特定實作，例如"LinkedList 」 或 「 雜湊表，「 任何尾碼。  
  
 **✓ CONSIDER** 前面加上的項目類型名稱的集合名稱。 例如，儲存項目類型的集合`Address`(實作`IEnumerable<Address>`) 應該命名為`AddressCollection`。 如果項目類型是介面，"I"前置詞之項目的型別，則可以省略。 因此，一堆<xref:System.IDisposable>項目可以稱為`DisposableCollection`。  
  
 **✓ CONSIDER** 的唯讀集合的名稱中使用"ReadOnly"前置詞，如果對應的可寫入集合可能會加入或已存在於架構。  
  
 比方說，應該呼叫唯讀的集合，這些字串`ReadOnlyStringCollection`。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
- [用法方針](../../../docs/standard/design-guidelines/usage-guidelines.md)
