---
title: "集合方針 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
caps.latest.revision: 4
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 4
---
# 集合方針
任何類型，專門設計來管理群組的物件都有某些共同特性可視為集合。 這幾乎都適合這種型別實作 <xref:System.Collections.IEnumerable> 或 <xref:System.Collections.Generic.IEnumerable%601>, ，因此本節中，我們只考慮實作一個或兩個介面的型別是集合。  
  
 **X 不** 公用 Api 中使用弱式型別的集合。  
  
 所有傳回值和參數，表示集合項目類型應該是正確的項目類型，不是任何基底類型 （這只適用於集合的公用成員）。  
  
 **X 不** 使用 <xref:System.Collections.ArrayList> 或 <xref:System.Collections.Generic.List%601> 公用 Api 中。  
  
 這些型別是設計用於在內部實作中，不在公用 Api 中的資料結構。`List<T>` 已針對效能與 cleanness Api 和彈性的情況下的電源最佳化。 例如，如果您傳回 `List<T>`, ，您將以往無法接收通知，當用戶端程式碼修改集合。 此外， `List<T>` 會公開許多成員，例如 <xref:System.Collections.Generic.List%601.BinarySearch%2A>, ，不實用，甚至在許多情況下適用。 下列兩個區段描述類型 （抽象） 特別為公用 Api 中使用而設計。  
  
 **X 不** 使用 `Hashtable` 或 `Dictionary<TKey,TValue>` 公用 Api 中。  
  
 這些型別是設計用於在內部實作的資料結構。 應該使用公用 Api <xref:System.Collections.IDictionary>, ，`IDictionary <TKey, TValue>`, ，或實作一或兩個介面的自訂型別。  
  
 **X 不** 使用 <xref:System.Collections.Generic.IEnumerator%601>, ，<xref:System.Collections.IEnumerator>, ，或實作介面，其中的傳回型別為以外的其他任何類型 `GetEnumerator` 方法。  
  
 除了從方法傳回列舉值的型別 `GetEnumerator` 無法搭配 `foreach` 陳述式。  
  
 **X 不** 同時實作 `IEnumerator<T>` 和 `IEnumerable<T>` 上相同的型別。 同樣也適用於非泛型介面 `IEnumerator` 和 `IEnumerable`。  
  
## Parameters 集合  
 **✓ 執行** 可能的最低特製化的型別做為參數型別。 取得集合，為參數使用的大部分成員 `IEnumerable<T>` 介面。  
  
 **X 避免** 使用 <xref:System.Collections.Generic.ICollection%601> 或 <xref:System.Collections.ICollection> 做為參數，只是為了存取 `Count` 屬性。  
  
 相反地，請考慮使用 `IEnumerable<T>` 或 `IEnumerable` 和動態檢查物件是否實作 `ICollection<T>` 或 `ICollection`。  
  
## 集合屬性和傳回值  
 **X 不** 提供可設定的集合屬性。  
  
 使用者可以先清除集合，然後再新增新的內容取代集合的內容。 如果取代整個集合是常見的案例，請考慮提供 `AddRange` 集合上的方法。  
  
 **✓ 執行** 使用 `Collection<T>` 或子類別的 `Collection<T>` 屬性或傳回值表示的讀取\/寫入集合。  
  
 如果 `Collection<T>` 不符合某些需求 \(例如，集合必須不實作 <xref:System.Collections.IList>\)，使用自訂的集合，藉由實作 `IEnumerable<T>`, ，`ICollection<T>`, ，或 <xref:System.Collections.Generic.IList%601>。  
  
 **✓ 執行** 使用 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>, ，子類別的 `ReadOnlyCollection<T>`, ，或在極少數的情況下 `IEnumerable<T>` 屬性或傳回的值代表的唯讀集合。  
  
 一般來說，偏好 `ReadOnlyCollection<T>`。 如果不符合某些需求 \(例如，集合必須不實作 `IList`\)，使用自訂的集合，藉由實作 `IEnumerable<T>`, ，`ICollection<T>`, ，或 `IList<T>`。 如果您實作自訂的唯讀集合，實作 `ICollection<T>.ReadOnly` 傳回 false。  
  
 在要確定只有您會想要支援的案例是順向的反覆項目的情況下，您可以直接使用 `IEnumerable<T>`。  
  
 **✓ 考慮** 使用泛型基底集合的子類別，而不直接使用集合。  
  
 這可讓更佳的名稱以及加入未出現在基底集合型別上的協助程式成員。 這特別適用於高階 Api。  
  
 **✓ 考慮** 傳回的子類別 `Collection<T>` 或 `ReadOnlyCollection<T>` 從相當常用的方法和屬性。  
  
 這會讓您加入 helper 方法，或變更在未來的集合實作。  
  
 **✓ 考慮** 使用索引鍵的集合，如果儲存在集合中的項目都有唯一索引鍵 （名稱、 識別碼等。）。 索引的集合的集合，可以編製索引的整數和金鑰，且通常由繼承自 `KeyedCollection<TKey,TItem>`。  
  
 索引的集合通常足跡較大的記憶體，而且不應該使用的記憶體負荷超過型索引鍵的好處在於如果。  
  
 **X 不** 集合屬性中，或從傳回集合的方法會傳回 null 值。 而是傳回空集合或空陣列。  
  
 一般規則是應該是 null 和空白 （0 個項目） 的集合或陣列視為相同。  
  
### 與即時集合快照集  
 集合代表在某個時間點的狀態表示的時間稱為快照集的集合。 例如，集合，其中包含從資料庫查詢傳回的資料列會是快照集。 一律代表對目前狀態的集合稱為即時的集合。 例如，集合的 `ComboBox` 項目是即時的集合。  
  
 **X 不** 屬性從傳回快照集的集合。 屬性應該會傳回實際的集合。  
  
 屬性 getter 應該非常輕量級的作業。 傳回快照集時，需要在 o （n） 作業中建立一份內部集合。  
  
 **✓ 執行** 使用快照集集合或即時 `IEnumerable<T>` （或它的子類型） 來表示為變動性的集合 （亦即，可以變更而不需明確地修改集合）。  
  
 一般情況下，表示共用的資源 （例如，在目錄中的檔案） 的所有集合都是動態的。 這類集合是很難或無法即時集合的形式實作，除非實作就只是順向的列舉值。  
  
## 陣列和集合之間選擇  
 **✓ 執行** 偏好陣列集合。  
  
 集合提供更充分掌控內容可以隨著時間演進，則更實用。 此外，因為複製陣列成本高昂，建議使用陣列的唯讀案例。 可用性研究顯示，有些開發人員習慣使用以集合為基礎的 Api。  
  
 不過，如果您正在開發的低階 Api，可能比較好讀寫案例中使用陣列。 需要較小的記憶體耗用量，有助於降低工作集，其中的陣列，陣列中項目的存取速度，因為它由執行階段最佳化。  
  
 **✓ 考慮** 低階 Api 中使用陣列來減少記憶體耗用量並提高效能。  
  
 **✓ 執行** 使用位元組陣列，而不是位元組的集合。  
  
 **X 不** 使用屬性的陣列，如果此屬性必須傳回每次呼叫屬性 getter 時 （例如，內部陣列的複本） 的新陣列。  
  
## 實作自訂集合  
 **✓ 考慮** 繼承自 `Collection<T>`, ，`ReadOnlyCollection<T>`, ，或 `KeyedCollection<TKey,TItem>` 設計新的集合時。  
  
 **✓ 執行** 實作 `IEnumerable<T>` 設計新的集合時。 請考慮實作 `ICollection<T>` ，甚至 `IList<T>` 派得上用場。  
  
 在實作這類自訂集合時，請遵循 「 API 」 模式所建立的 `Collection<T>` 和 `ReadOnlyCollection<T>` 十分接近。 也就是說，明確地實作相同的成員，為參數命名像這兩個集合的名稱，以及等等。  
  
 **✓ 考慮** 實作非泛型集合介面 \(`IList` 和 `ICollection`\) 如果集合將通常會傳遞至 Api 採取這些介面做為輸入。  
  
 **X 避免** 與複雜的 Api 不相關的概念的集合型別上實作集合介面。  
  
 **X 不** 例如繼承自非泛型基底集合 `CollectionBase`。 使用 `Collection<T>`, ，`ReadOnlyCollection<T>`, ，和 `KeyedCollection<TKey,TItem>` 改。  
  
### 命名自訂集合  
 集合 \(型別都會實作 `IEnumerable`\) 會建立主要的原因有二: （1） 若要建立新的資料結構與結構特定作業通常比現有的資料結構的不同效能特性 \(例如  <xref:System.Collections.Generic.List%601>, ，<xref:System.Collections.Generic.LinkedList%601>, ，<xref:System.Collections.Generic.Stack%601>\)，以及 （2） 建立特製化的集合來存放一組特定的項目 \(例如  <xref:System.Collections.Specialized.StringCollection>\)。 資料結構最常用在應用程式和程式庫的內部實作。 特定的集合是主要是為了在 （做為屬性和參數型別） 的 Api 中公開。  
  
 **✓ 執行** 實作的抽象名稱中使用 「 字典 」 尾碼 `IDictionary` 或 `IDictionary<TKey,TValue>`。  
  
 **✓ 執行** 實作的型別名稱中使用 「 集合 」 尾碼 `IEnumerable` （或其任何子代） 和表示項目清單。  
  
 **✓ 執行** 使用自訂資料結構的適當的資料結構名稱。  
  
 **X 避免** 名稱集合的抽象概念中使用特定的實作，例如 「 LinkedList 」 或 「 雜湊表 」，其中隱含的後置字元。  
  
 **✓ 考慮** 前置詞的項目類型名稱的集合名稱。 例如，儲存類型的項目集合 `Address` \(實作 `IEnumerable<Address>`\) 的名稱應該是 `AddressCollection`。 如果項目類型是介面，"I"前置詞的項目類型，則可以省略。 因此，一堆 <xref:System.IDisposable> 項目可以稱為 `DisposableCollection`。  
  
 **✓ 考慮** 的唯讀集合的名稱中使用"ReadOnly"前置詞，如果對應的可寫入集合可能加入或已存在於架構。  
  
 例如，字串的唯讀集合應該呼叫 `ReadOnlyStringCollection`。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)   
 [用法方針](../../../docs/standard/design-guidelines/usage-guidelines.md)