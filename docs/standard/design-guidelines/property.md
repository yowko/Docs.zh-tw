---
title: 屬性設計
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
author: KrzysztofCwalina
ms.openlocfilehash: 1d119b48f0524b3e997aa2cb9ea2cbbd855afdf0
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131452"
---
# <a name="property-design"></a>屬性設計
雖然技術上的方法非常類似屬性，它們是根據它們的使用案例相當不同。 應該會看到它們做為智慧的欄位。 它們有呼叫欄位的語法，與彈性的方法。  
  
 **✓ DO** 建立 get 專用的屬性，如果呼叫端應該不能變更屬性的值。  
  
 請記住，如果的型別屬性是可變動參考類型，可以變更屬性值，即使屬性是 get 專用。  
  
 **X DO NOT** 提供具有更廣泛的存取範圍，getter 與 setter 設定專用的屬性。  
  
 比方說，務必使用屬性與公用 setter 和受保護的 getter。  
  
 如果無法提供的屬性 getter，請改為實作做為方法的功能。 請考慮開始使用的方法名稱`Set`並在後面加什麼您會有具名屬性。 比方說，<xref:System.AppDomain>有一個方法，叫做`SetCachePath`而不是僅限集的屬性，稱為`CachePath`。  
  
 **✓ DO** 提供合理的預設值給所有屬性，確保 預設值，不會造成安全性漏洞或方面出了沒有效率的程式碼中。  
  
 **✓ DO** 讓屬性以設定任何順序，即使這樣造成暫存物件的無效狀態。  
  
 很常見的兩個或多個要相互關聯的其中一個屬性的某些值可能是無效的點屬性指定相同的物件上的其他屬性的值。 在此情況下，造成無效的狀態例外狀況應該延遲直到物件實際上一起使用相互關聯的屬性。  
  
 **✓ DO** 保留先前的值，如果屬性 setter 擲回例外狀況。  
  
 **X AVOID** 擲回例外狀況，從屬性 getter。  
  
 屬性 getter 應該是簡單的作業，而且不應該有任何前置條件。 如果 getter 可以擲回例外狀況，它應該可能重新設計為方法。 請注意，這項規則不適用於索引子，其中我們希望因為驗證引數的例外狀況。  
  
### <a name="indexed-property-design"></a>索引的屬性設計  
 索引的屬性是特殊的屬性可以有參數，可以使用類似於陣列編製索引的特殊語法來呼叫。  
  
 索引的屬性通常稱為 「 索引子 」。 索引子應該只用於存取項目邏輯的集合中的 Api。 例如，字串是字元和索引子上的集合<xref:System.String?displayProperty=nameWithType>已新增至存取其所有字元。  
  
 **✓ CONSIDER** 使用索引子來提供資料儲存在內部陣列的存取權。  
  
 **✓ CONSIDER** 提供索引子型別上表示的項目集合。  
  
 **X AVOID** 使用索引的屬性與一個以上的參數。  
  
 如果設計需要多個參數，請重新考慮是否真的邏輯的集合來表示存取子的屬性。 如果不存在，請改為使用方法。 開始使用的方法名稱，請考慮`Get`或`Set`。  
  
 **X AVOID** 以外的參數類型的索引子 <xref:System.Int32?displayProperty=nameWithType>， <xref:System.Int64?displayProperty=nameWithType>， <xref:System.String?displayProperty=nameWithType>， <xref:System.Object?displayProperty=nameWithType>，或列舉。  
  
 如果設計需要其他類型的參數，強重新評估是否 API 真的表示的邏輯集合存取子。 如果沒有，請使用方法。 開始使用的方法名稱，請考慮`Get`或`Set`。  
  
 **✓ DO** 使用名稱 `Item` 的索引屬性，除非有明顯更適合的名稱 (例如，請參閱<xref:System.String.Chars%2A> 屬性 `System.String`)。  
  
 在 C# 中，索引子會是預設名為項目。 <xref:System.Runtime.CompilerServices.IndexerNameAttribute>可用來自訂此名稱。  
  
 **X DO NOT** 提供索引子和語意相等的方法。  
  
 **X DO NOT** 提供一個類型中的多載索引子的一個以上的系列。  
  
 這會強制執行 C# 編譯器。  
  
 **X DO NOT** 使用非預設索引的屬性。  
  
 這會強制執行 C# 編譯器。  
  
### <a name="property-change-notification-events"></a>屬性變更通知事件  
 有時候最好提供事件通知中的屬性值變更的使用者。 例如，`System.Windows.Forms.Control`引發`TextChanged`的值之後的事件其`Text`屬性已變更。  
  
 **✓ CONSIDER** 引發變更通知事件時修改高階應用程式開發介面 （通常是設計工具元件） 中的屬性值。  
  
 如果沒有良好的案例，讓使用者知道何時要變更物件的屬性，該物件應該引發屬性變更通知事件。  
  
 不過，它不太可能是值得引發這類事件，例如基底類型或集合的低層級 api 的額外負荷。 例如，<xref:System.Collections.Generic.List%601>不會引發新的項目新增至清單時，這類事件和`Count`屬性變更。  
  
 **✓ CONSIDER** 引發變更通知事件時透過外部強制變更屬性的值。  
  
 如果屬性值變更透過某些外力 （在物件上呼叫方法以外的方式），會引發事件指出開發人員的值變更，而且已變更。 是一個好例子`Text`文字方塊控制項的屬性。 當使用者輸入文字中的`TextBox`，屬性值會自動變更。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## <a name="see-also"></a>另請參閱

- [成員設計方針](../../../docs/standard/design-guidelines/member.md)  
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
