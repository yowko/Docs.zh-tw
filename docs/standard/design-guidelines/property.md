---
title: "屬性設計 | Microsoft Docs"
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
helpviewer_keywords: 
  - "成員設計方針屬性"
  - "屬性 [.NET Framework] 設計指導方針"
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 屬性設計
雖然技術上來說非常類似方法屬性，它們是根據它們的使用案例相當不同。 它們應該視為智慧型欄位。 有的欄位，呼叫的語法和方法的彈性。  
  
 **✓ 執行** 建立僅供取用屬性，如果呼叫端不應該變更屬性的值。  
  
 請記住，如果類型的屬性是可變動參考類型，可以變更屬性值，即使屬性是 get 專用。  
  
 **X 不** 提供組專用的屬性的 setter 具有 getter 比更廣泛的存取範圍。  
  
 比方說，務必使用屬性 setter 公用和受保護的 getter。  
  
 如果無法提供屬性 getter，請改為實作做為方法的功能。 請考慮開始使用的方法名稱 `Set` ，並遵循與您會有什麼屬性。 例如， <xref:System.AppDomain> 方法呼叫都 `SetCachePath` 而不需要僅限集的屬性，稱為 `CachePath`。  
  
 **✓ 執行** 所有屬性，確保預設值，不會造成安全性漏洞或太沒有效率的程式碼中提供合理的預設值。  
  
 **✓ 執行** 讓屬性以設定任何順序，即使這樣造成暫存物件的無效狀態。  
  
 很常見的是一個屬性的部分值可能是無效的點彼此相關的兩個或多個屬性指定相同的物件上的其他屬性的值。 在這種情況下，直到物件實際上一起使用相互關聯的屬性應延遲造成無效的狀態例外狀況。  
  
 **✓ 執行** 保留先前的值，如果屬性 setter 會擲回例外狀況。  
  
 **X 避免** 擲回例外狀況，從屬性 getter。  
  
 屬性 getter 應該是簡單的作業，而且不能有任何先決條件。 如果 getter 可能擲回例外狀況，它應該可能重新設計為方法。 請注意，這項規則不適用於索引子，其中我們期望的結果驗證引數例外狀況。  
  
### 索引的屬性設計  
 索引的屬性是特殊的屬性，可以有參數，並且可使用特殊語法類似於陣列索引。  
  
 索引的屬性通常稱為索引子。 索引子應該只用於 Api 提供存取的邏輯集合中的項目。 例如，字串是個字元，而且在索引子的集合 <xref:System.String?displayProperty=fullName> 已新增至存取其所有字元。  
  
 **✓ 考慮** 使用索引子來提供資料儲存在內部陣列的存取權。  
  
 **✓ 考慮** 提供索引子型別上表示的項目集合。  
  
 **X 避免** 使用索引具有多個參數的屬性。  
  
 如果設計需要多個參數，請考慮是否真的邏輯集合表示存取子的屬性。 如果不存在，請改為使用方法。 請考慮開始使用的方法名稱 `Get` 或 `Set`。  
  
 **X 避免** 以外的參數類型的索引子 <xref:System.Int32?displayProperty=fullName>, ，<xref:System.Int64?displayProperty=fullName>, ，<xref:System.String?displayProperty=fullName>, ，<xref:System.Object?displayProperty=fullName>, ，或列舉。  
  
 如果設計需要其他類型的參數，極力重新評估是否 API 真的表示邏輯集合存取子。 如果不存在，請使用方法。 請考慮開始使用的方法名稱 `Get` 或 `Set`。  
  
 **✓ 執行** 使用名稱 `Item` 的索引屬性，除非有明顯較佳的名稱 \(例如，請參閱 <xref:System.String.Chars%2A> 屬性 `System.String`\)。  
  
 在 C\# 索引子為可由預設的具名項目。<xref:System.Runtime.CompilerServices.IndexerNameAttribute> 可以用來自訂此名稱。  
  
 **X 不** 提供索引子和語意相等的方法。  
  
 **X 不** 提供多個系列中一種類型的多載索引子。  
  
 這會強制執行 C\# 編譯器。  
  
 **X 不** 使用非預設索引屬性。  
  
 這會強制執行 C\# 編譯器。  
  
### 屬性變更通知事件  
 有時候很有用來提供事件通知使用者的屬性值中的變更。 例如， `System.Windows.Forms.Control` 引發 `TextChanged` 事件之後的值及其 `Text` 屬性已變更。  
  
 **✓ 考慮** 引發變更通知事件時修改高階 Api （通常是設計工具元件） 中的屬性值。  
  
 如果有良好的案例，讓使用者知道物件的屬性變更時，該物件應該引發屬性變更通知事件。  
  
 不過，不太值得低階 api，例如基底類型或集合引發這類事件的額外負荷。 例如， <xref:System.Collections.Generic.List%601> 將不會引發新的項目加入至清單時，這類事件和 `Count` 屬性變更。  
  
 **✓ 考慮** 引發變更通知事件透過外部人力的屬性值變更時。  
  
 如果屬性值變更時透過某些外力 （在物件上呼叫方法的方法以外），會引發事件會指出向開發人員，正在變更的值，而且已變更。 例如， `Text` 文字方塊控制項的屬性。 當使用者輸入的文字 `TextBox`, ，屬性值會自動變更。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [成員設計方針](../../../docs/standard/design-guidelines/member.md)   
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)