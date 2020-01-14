---
title: 屬性設計
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
ms.openlocfilehash: 5d5cdbfdb38c7aebaca6cbcdeb63959ac12884e0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709123"
---
# <a name="property-design"></a>屬性設計
雖然屬性的技術與方法非常類似，但它們在使用案例方面的差異很大。 它們應該會視為智慧型欄位。 它們具有欄位的呼叫語法，以及方法的彈性。  
  
 如果呼叫端應該無法變更屬性的值，則**✓**會建立僅限取得的屬性。  
  
 請記住，如果屬性的型別是可變動的參考型別，即使屬性是 get only，屬性值也可以變更。  
  
 **X**不提供僅限設定的屬性或屬性，其 setter 具有比 getter 更廣的存取範圍。  
  
 例如，請勿使用具有公用 setter 和 protected getter 的屬性。  
  
 如果無法提供屬性 getter，請改為將此功能當做方法來執行。 請考慮使用 `Set` 啟動方法名稱，並遵循您所命名的屬性。 例如，<xref:System.AppDomain> 有一個稱為 `SetCachePath` 的方法，而不是擁有稱為 `CachePath`的僅限集合屬性。  
  
 **✓**會為所有屬性提供合理的預設值，確保預設值不會導致安全性漏洞或驗證效率不佳的程式碼。  
  
 **✓ DO**允許以任何順序設定屬性，即使這會導致物件的暫時無效狀態。  
  
 兩個或多個屬性通常會相互關聯，因為相同物件上的其他屬性值可能會使某個屬性的某些值無效。 在這種情況下，從無效狀態產生的例外狀況應該會延後，直到物件實際使用相互關聯的屬性為止。  
  
 如果屬性 setter 擲回例外狀況， **✓ DO**會保留先前的值。  
  
 **X 避免**從屬性 getter 擲回例外狀況。  
  
 屬性 getter 應該是簡單的作業，而且不應該有任何前置條件。 如果 getter 可能會擲回例外狀況，則可能會重新設計為方法。 請注意，此規則不適用於索引子，因為驗證引數會導致例外狀況。  
  
### <a name="indexed-property-design"></a>索引屬性設計  
 索引屬性是特殊的屬性，可以具有參數，而且可以使用類似于陣列索引編制的特殊語法來呼叫。  
  
 索引屬性通常稱為索引子。 索引子只能用於提供邏輯集合中專案存取權的 Api。 例如，字串是字元的集合，並已新增 <xref:System.String?displayProperty=nameWithType> 上的索引子來存取其字元。  
  
 **✓請考慮**使用索引子來提供內部陣列中所儲存之資料的存取權。  
  
 **✓請考慮**在代表專案集合的類型上提供索引子。  
  
 **X 避免**使用具有一個以上參數的索引屬性。  
  
 如果設計需要多個參數，請重新考慮屬性是否真的代表邏輯集合的存取子。 如果不存在，請改用方法。 請考慮使用 `Get` 或 `Set`來啟動方法名稱。  
  
 **X 避免**具有 <xref:System.Int32?displayProperty=nameWithType>、<xref:System.Int64?displayProperty=nameWithType>、<xref:System.String?displayProperty=nameWithType>、<xref:System.Object?displayProperty=nameWithType>或列舉以外參數類型的索引子。  
  
 如果設計需要其他類型的參數，請強烈重新評估 API 是否真的代表邏輯集合的存取子。 如果不存在，請使用方法。 請考慮使用 `Get` 或 `Set`來啟動方法名稱。  
  
 除非有明顯較好的名稱（例如，請參閱 `System.String`上的 <xref:System.String.Chars%2A> 屬性），否則**✓**會使用索引屬性的名稱 `Item`。  
  
 在C#中，索引子預設會命名為 Item。 <xref:System.Runtime.CompilerServices.IndexerNameAttribute> 可以用來自訂此名稱。  
  
 **X**不會同時提供具有相同語義的索引子和方法。  
  
 **X 不會**在一種類型中提供一個以上多載的索引子系列。  
  
 這是由C#編譯器強制執行。  
  
 **X**不使用非預設的索引屬性。  
  
 這是由C#編譯器強制執行。  
  
### <a name="property-change-notification-events"></a>屬性變更通知事件  
 有時候，提供事件通知使用者屬性值的變更會很有用。 例如，`System.Windows.Forms.Control` 會在其 `Text` 屬性的值變更後引發 `TextChanged` 事件。  
  
 當高層級 Api （通常是設計工具元件）中的屬性值被修改時， **✓請考慮**引發變更通知事件。  
  
 如果有一個很好的案例，讓使用者知道何時會變更物件的屬性，物件應該會引發屬性的變更通知事件。  
  
 不過，針對低層級 Api （例如基底類型或集合）引發這類事件的額外負荷不太值得。 例如，<xref:System.Collections.Generic.List%601> 不會在新的專案加入至清單，而且 `Count` 屬性變更時引發這類事件。  
  
 當屬性的值透過外部強制變更時， **✓請考慮**引發變更通知事件。  
  
 如果屬性值透過某些外部強制進行變更（透過在物件上呼叫方法以外的方式），則引發事件會向開發人員指出值已變更且已變更。 文字方塊控制項的 `Text` 屬性就是一個很好的例子。 當使用者在 `TextBox`中輸入文字時，屬性值會自動變更。  
  
 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>請參閱

- [成員設計方針](../../../docs/standard/design-guidelines/member.md)
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
