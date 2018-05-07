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
---
# <a name="property-design"></a>屬性設計
雖然技術上非常類似於方法內容，但它們是根據它們的使用案例相當不同。 這些應該視為智慧型欄位。 有的欄位，呼叫的語法和方法的彈性。  
  
 **✓ 不要**建立 get 專用的屬性，如果呼叫端應該不能變更屬性的值。  
  
 請記住，如果類型的屬性是可變動參考類型，可以變更屬性值，即使屬性是 get-only。  
  
 **X 不**提供具有更廣泛的存取範圍，getter 與 setter 設定專用的屬性。  
  
 例如，務必使用屬性具有公用 setter 和受保護的 getter。  
  
 如果無法提供屬性 getter，請改為實作做為方法的功能。 請考慮從開始的方法名稱與`Set`和之後，您會有什麼屬性。 例如，<xref:System.AppDomain>已呼叫的方法`SetCachePath`而不需僅限組屬性稱為`CachePath`。  
  
 **✓ 不要**提供合理的預設值給所有屬性，確保 預設值，不會造成安全性漏洞或方面出了沒有效率的程式碼中。  
  
 **✓ 不要**讓屬性以設定任何順序，即使這樣造成暫存物件的無效狀態。  
  
 通常會是一個屬性的某些值可能是無效的點彼此相關的兩個或多個屬性指定相同的物件上的其他屬性的值。 在這種情況下，直到物件實際上在一起使用相互關聯的屬性應延遲造成無效的狀態例外狀況。  
  
 **✓ 不要**保留先前的值，如果屬性 setter 擲回例外狀況。  
  
 **請避免 x**擲回例外狀況，從屬性 getter。  
  
 Getter 屬性應該是簡單的操作，而且不能有任何先決條件。 如果 getter 可以擲回例外狀況，它應該可能重新設計的方法。 請注意，這項規則不適用於索引子，其中我們期望的結果驗證引數的例外狀況。  
  
### <a name="indexed-property-design"></a>設計索引的屬性  
 索引的屬性是特殊的屬性可以有參數，可以使用類似陣列編製索引的特殊語法來呼叫。  
  
 索引的屬性通常稱為索引子。 索引子應該只能用於應用程式開發介面可提供存取權的邏輯集合中的項目。 例如，字串是字元和集合上的索引子<xref:System.String?displayProperty=nameWithType>已新增至存取其所有字元。  
  
 **✓ 考慮**使用索引子來提供資料儲存在內部陣列的存取權。  
  
 **✓ 考慮**提供索引子型別上表示的項目集合。  
  
 **請避免 x**使用索引的屬性與一個以上的參數。  
  
 如果設計需要多個參數，請考慮是否真的邏輯集合表示的存取子的屬性。 如果不存在，請改為使用方法。 請考慮從開始的方法名稱與`Get`或`Set`。  
  
 **請避免 x**以外的參數類型的索引子<xref:System.Int32?displayProperty=nameWithType>， <xref:System.Int64?displayProperty=nameWithType>， <xref:System.String?displayProperty=nameWithType>， <xref:System.Object?displayProperty=nameWithType>，或列舉。  
  
 如果設計需要其他類型的參數，強烈重新評估是否真的邏輯集合表示的存取子的 API。 如果未出現，請使用方法。 請考慮從開始的方法名稱與`Get`或`Set`。  
  
 **✓ 不要**使用名稱`Item`的索引屬性，除非有明顯更適合的名稱 (例如，請參閱<xref:System.String.Chars%2A>屬性`System.String`)。  
  
 在 C# 中，索引子為可由預設的具名項目。 <xref:System.Runtime.CompilerServices.IndexerNameAttribute>可以用來自訂此名稱。  
  
 **X 不**提供索引子和語意相等的方法。  
  
 **X 不**提供一個類型中的多載索引子的一個以上的系列。  
  
 這會強制執行由 C# 編譯器。  
  
 **X 不**使用非預設索引的屬性。  
  
 這會強制執行由 C# 編譯器。  
  
### <a name="property-change-notification-events"></a>屬性變更通知事件  
 有時候很有用提供事件通知使用者屬性值中的變更。 例如，`System.Windows.Forms.Control`引發`TextChanged`事件之後的值及其`Text`屬性已變更。  
  
 **✓ 考慮**引發變更通知事件時修改高階應用程式開發介面 （通常是設計工具元件） 中的屬性值。  
  
 如果沒有良好的案例，讓使用者知道物件的屬性變更時，該物件應該會引發屬性變更通知事件。  
  
 不過，它不太可能值得引發這類事件，例如基底類型或集合的低層級 api 的額外負荷。 例如，<xref:System.Collections.Generic.List%601>將不會引發新的項目加入至清單時，這類事件和`Count`屬性變更。  
  
 **✓ 考慮**引發變更通知事件時透過外部強制變更屬性的值。  
  
 如果屬性值變更時透過某些外部 force （在物件上呼叫方法的方法以外），會引發事件指出，開發人員正在變更的值，而且已變更。 例如，`Text`文字方塊控制項的屬性。 當使用者輸入的文字`TextBox`，會自動變更的屬性值。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [成員設計方針](../../../docs/standard/design-guidelines/member.md)  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
