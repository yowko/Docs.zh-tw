---
title: "集合方針"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 09a2a075e21de6968989575385db07ab39eb627f
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2018
---
# <a name="guidelines-for-collections"></a>集合方針
可以被視為特別設計用來管理群組物件都有某些共同特性的任何類型的集合。 這幾乎都適合實作這類類型<xref:System.Collections.IEnumerable>或<xref:System.Collections.Generic.IEnumerable%601>，因此本節中，我們只考慮實作一或兩個介面的型別是集合。  
  
 **X 不**在公用 Api 中使用弱式型別的的集合。  
  
 所有傳回值以及參數代表集合項目類型應該是正確的項目類型，不其任何基底類型 （這只適用於集合中的公用成員）。  
  
 **X 不**使用<xref:System.Collections.ArrayList>或<xref:System.Collections.Generic.List%601>在公用 Api。  
  
 這些類型是設計為可在內部實作中，不能在公用 Api 的資料結構。 `List<T>` 已針對效能，但要付出的應用程式開發介面與彈性 cleanness 電源最佳化。 例如，如果您傳回`List<T>`，您將永遠無法接收通知，當用戶端程式碼會修改集合。 此外，`List<T>`公開許多成員，例如<xref:System.Collections.Generic.List%601.BinarySearch%2A>，不實用或適用於許多案例。 下列兩節則描述專為使用公用 Api 中設計的類型 （抽象）。  
  
 **X 不**使用`Hashtable`或`Dictionary<TKey,TValue>`在公用 Api。  
  
 這些類型是設計為可在內部實作的資料結構。 應該使用公用 Api <xref:System.Collections.IDictionary>， `IDictionary <TKey, TValue>`，或實作一或兩個介面的自訂型別。  
  
 **X 不**使用<xref:System.Collections.Generic.IEnumerator%601>， <xref:System.Collections.IEnumerator>，或實作介面，其中除了為傳回類型的任何其他型別`GetEnumerator`方法。  
  
 除了從方法傳回列舉值的型別`GetEnumerator`不能與`foreach`陳述式。  
  
 **X 不**同時實作`IEnumerator<T>`和`IEnumerable<T>`上相同的型別。 同樣適用於非泛型介面`IEnumerator`和`IEnumerable`。  
  
## <a name="collection-parameters"></a>集合參數  
 **✓ 不要**使用可能的最低特製化類型做為參數類型。 取得集合，作為參數使用的大部分成員`IEnumerable<T>`介面。  
  
 **請避免 x**使用<xref:System.Collections.Generic.ICollection%601>或<xref:System.Collections.ICollection>做為參數，只是為了存取`Count`屬性。  
  
 相反地，請考慮使用`IEnumerable<T>`或`IEnumerable`和動態檢查物件是否實作`ICollection<T>`或`ICollection`。  
  
## <a name="collection-properties-and-return-values"></a>集合屬性和傳回值  
 **X 不**提供可設定的集合屬性。  
  
 使用者可以先清除集合，然後將加入新的內容取代集合的內容。 如果取代整個集合是常見的案例，請考慮提供`AddRange`集合上的方法。  
  
 **✓ 不要**使用`Collection<T>`或的子類別`Collection<T>`針對屬性或傳回值表示讀取/寫入集合。  
  
 如果`Collection<T>`不符合某些需求 (例如，集合必須不會實作<xref:System.Collections.IList>)，使用自訂的集合，藉由實作`IEnumerable<T>`， `ICollection<T>`，或<xref:System.Collections.Generic.IList%601>。  
  
 **✓ 不要**使用<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>的子類別`ReadOnlyCollection<T>`，或在極少數的情況下`IEnumerable<T>`針對屬性或傳回值表示唯讀的集合。  
  
 通常，最好`ReadOnlyCollection<T>`。 如果不符合某些需求 (例如，集合必須不會實作`IList`)，使用自訂的集合，藉由實作`IEnumerable<T>`， `ICollection<T>`，或`IList<T>`。 如果您實作自訂的唯讀集合，實作`ICollection<T>.IsReadOnly`傳回`true`。  
  
 在要確定只有您想要支援的案例是順向的反覆項目的情況下，您可以直接使用`IEnumerable<T>`。  
  
 **✓ 考慮**使用泛型基底集合的子類別，而不直接使用集合。  
  
 如此可更佳的名稱，以及加入未出現在基底集合類型上的協助程式成員。 這是特別適用於高階應用程式開發介面。  
  
 **✓ 考慮**傳回的子類別`Collection<T>`或`ReadOnlyCollection<T>`從相當常用的方法和屬性。  
  
 這會讓您可新增 helper 方法，或變更在未來的集合實作。  
  
 **✓ 考慮**使用索引鍵的集合，如果儲存在集合中的項目具有唯一索引鍵 （名稱、 識別碼、 等等。）。 索引鍵的集合是以一個整數和索引鍵編製的索引，且通常由繼承自集合`KeyedCollection<TKey,TItem>`。  
  
 索引的集合通常較大的記憶體使用量，而不是記憶體負擔會超過優點必須要有金鑰。  
  
 **X 不**集合屬性中或從方法傳回集合，傳回 null 值。 而是傳回空集合或空陣列。  
  
 一般規則是應該是 null 和空白 （0 的項目） 的集合或陣列視為相同。  
  
### <a name="snapshots-versus-live-collections"></a>快照集與即時的集合  
 集合表示在某個時間點的狀態的時間稱為快照集的集合。 例如，集合，其中包含從資料庫查詢傳回資料列將快照集。 一律代表對目前狀態的集合稱為即時的集合。 例如，集合`ComboBox`項目是即時的集合。  
  
 **X 不**屬性從傳回快照集的集合。 屬性應該會傳回實際的集合。  
  
 屬性 getter 應該非常輕量級的作業。 傳回快照集也需要 o （n） 作業中建立的內部集合的複本。  
  
 **✓ 不要**使用快照集收集或即時`IEnumerable<T>`（或它的子類型） 來表示為變動性的集合 （亦即，可以變更而不需明確修改集合）。  
  
 一般情況下，表示共用的資源 （例如，在目錄中的檔案） 的所有集合都是動態的。 這類集合是很難或難以實作做為即時的集合，除非實作就只是順向的列舉值。  
  
## <a name="choosing-between-arrays-and-collections"></a>陣列和集合之間選擇  
 **✓ 不要**集合，而不用陣列。  
  
 集合提供更充分掌控內容、 可以隨著時間，而且更有用。 此外，因為複製陣列的成本為代價，建議使用陣列的唯讀案例。 顯示可用性研究的部分開發人員認為更方便使用以集合為基礎的 Api。  
  
 不過，如果您正在開發低階 Api，可能最好使用讀寫案例的陣列。 陣列有較小的記憶體耗用量，如此有助於減少工作集，以及陣列中項目的存取速度，因為它已由執行階段最佳化。  
  
 **✓ 考慮**低階 Api 中使用陣列記憶體耗用量降到最低，並將效能最大化。  
  
 **✓ 不要**使用位元組陣列，而不是位元組的集合。  
  
 **X 不**使用屬性的陣列，如果屬性必須在呼叫屬性 getter 的每次會傳回新的陣列 （例如，內部陣列的複本）。  
  
## <a name="implementing-custom-collections"></a>實作自訂集合  
 **✓ 考慮**繼承自`Collection<T>`， `ReadOnlyCollection<T>`，或`KeyedCollection<TKey,TItem>`設計新的集合時。  
  
 **✓ 不要**實作`IEnumerable<T>`設計新的集合時。 請考慮實作`ICollection<T>`或甚至`IList<T>`很合理。  
  
 當實作這類自訂集合時，請依照下列所建立的應用程式開發介面模式`Collection<T>`和`ReadOnlyCollection<T>`十分接近。 也就是明確地實作相同的成員、 name 參數，這兩個集合的名稱，以及等等一樣。  
  
 **✓ 考慮**實作非泛型集合介面 (`IList`和`ICollection`) 如果集合將通常會傳遞至應用程式開發介面採用這些介面做為輸入。  
  
 **請避免 x**型別上實作的集合介面具有複雜的應用程式開發介面不相關的概念的集合。  
  
 **X 不**例如繼承自非泛型基底集合`CollectionBase`。 使用`Collection<T>`， `ReadOnlyCollection<T>`，和`KeyedCollection<TKey,TItem>`改為。  
  
### <a name="naming-custom-collections"></a>命名自訂集合  
 集合 (型別都會實作`IEnumerable`) 會建立主要是針對兩個原因: (1) 若要建立新的資料結構的特定結構的作業和通常比現有的資料結構的不同效能特性 (例如<xref:System.Collections.Generic.List%601>，<xref:System.Collections.Generic.LinkedList%601>， <xref:System.Collections.Generic.Stack%601>)，以及 (2) 若要建立特製化的集合，用以保存一組特定的項目 (例如<xref:System.Collections.Specialized.StringCollection>)。 在內部實作中的應用程式和程式庫最常使用的資料結構。 特製化的集合是主要是要公開 Api 中 （屬性和參數的型別）。  
  
 **✓ 不要**抽象層實作名稱中使用 「 字典 」 尾碼`IDictionary`或`IDictionary<TKey,TValue>`。  
  
 **✓ 不要**實作的型別名稱中使用"Collection"後置詞`IEnumerable`（或其任何子代） 及表示項目清單。  
  
 **✓ 不要**使用適當的資料結構名稱的自訂資料結構。  
  
 **請避免 x**集合的抽象概念的名稱中使用隱含的特定實作，例如"LinkedList 」 或 「 雜湊表，「 任何尾碼。  
  
 **✓ 考慮**前面加上的項目類型名稱的集合名稱。 例如，儲存類型的項目集合`Address`(實作`IEnumerable<Address>`) 應命名為`AddressCollection`。 如果項目類型是介面，"I"前置詞的項目類型，則可以省略。 因此，集合<xref:System.IDisposable>可以呼叫項目`DisposableCollection`。  
  
 **✓ 考慮**的唯讀集合的名稱中使用"ReadOnly"前置詞，如果對應的可寫入集合可能會加入或已存在於架構。  
  
 例如，應該呼叫字串的唯讀集合`ReadOnlyStringCollection`。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [用法方針](../../../docs/standard/design-guidelines/usage-guidelines.md)
