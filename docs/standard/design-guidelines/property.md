---
title: 屬性設計
ms.date: 10/22/2008
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
ms.openlocfilehash: 1cf41a08c641e9251084e5dcac6c46bc54857717
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828734"
---
# <a name="property-design"></a>屬性設計
雖然屬性在技術上與方法非常類似，但它們在使用案例方面是相當不同的。 它們應該會被視為智慧型欄位。 它們具有欄位的呼叫語法，以及方法的彈性。

 如果呼叫端應該無法變更屬性的值，則✔️建立僅取得屬性。

 請記住，如果屬性的型別是可變動的參考型別，即使屬性是只有取得的屬性值，也可以變更屬性值。

 ❌ 請勿提供僅限設定的屬性或屬性，而且 setter 的存取範圍比 getter 更廣。

 例如，請勿使用具有公用 setter 的屬性和受保護的 getter。

 如果無法提供屬性 getter，請改以方法的形式來執行此功能。 請考慮使用來啟動方法名稱 `Set` ，並遵循您的命名屬性。 例如， <xref:System.AppDomain> 有一個呼叫的方法， `SetCachePath` 而不是呼叫僅限設定的屬性 `CachePath` 。

 ✔️確實會為所有屬性提供合理的預設值，以確保預設值不會導致安全性漏洞或效率不佳的程式碼。

 ✔️允許以任何順序設定屬性，即使這會導致物件的暫時無效狀態。

 有兩個或多個屬性與某個屬性的某些值可能不正確點（指定相同物件的其他屬性值）是很常見的。 在這種情況下，必須先延遲無效狀態所產生的例外狀況，才能將相關的屬性實際與物件一起使用。

 如果屬性 setter 擲回例外狀況，✔️會保留先前的值。

 ❌ 避免從屬性 getter 擲回例外狀況。

 屬性 getter 應該是簡單的作業，而且不應該有任何前置條件。 如果 getter 可能會擲回例外狀況，則應該重新設計成方法。 請注意，此規則不適用於索引子，因為驗證引數的結果會是例外狀況。

### <a name="indexed-property-design"></a>索引屬性設計
 索引屬性是一個特殊的屬性，它可以有參數，而且可以使用類似于陣列索引的特殊語法來呼叫。

 索引屬性通常稱為索引子。 索引子只能在提供邏輯集合中專案存取權的 Api 中使用。 例如，字串是字元的集合，而中的索引子 <xref:System.String?displayProperty=nameWithType> 已加入來存取其字元。

 ✔️考慮使用索引子來提供對內部陣列中所儲存之資料的存取權。

 ✔️考慮提供代表專案集合之類型的索引子。

 ❌ 避免使用具有一個以上參數的索引屬性。

 如果設計需要多個參數，請重新考慮屬性是否真的代表邏輯集合的存取子。 如果沒有，請改用方法。 請考慮使用或啟動方法 `Get` 名稱 `Set` 。

 ❌ 避免使用 <xref:System.Int32?displayProperty=nameWithType> 、、 <xref:System.Int64?displayProperty=nameWithType> <xref:System.String?displayProperty=nameWithType> 、 <xref:System.Object?displayProperty=nameWithType> 或列舉以外之參數類型的索引子。

 如果設計需要其他類型的參數，請強烈重新評估 API 是否真的代表邏輯集合的存取子。 如果沒有，請使用方法。 請考慮使用或啟動方法 `Get` 名稱 `Set` 。

 ✔️ `Item` 除非有明顯較佳的名稱 (例如，請參閱) 上的屬性，否則請使用已編制索引之屬性的名稱 <xref:System.String.Chars%2A> `System.String` 。

 在 c # 中，索引子是依預設命名的專案。 <xref:System.Runtime.CompilerServices.IndexerNameAttribute>可以用來自訂此名稱。

 ❌ 請勿提供在語義上相等的索引子和方法。

 ❌ 請勿在一種類型中提供多個多載的索引子系列。

 C # 編譯器會強制執行這項功能。

 ❌ 請勿使用非預設的索引屬性。

 C # 編譯器會強制執行這項功能。

### <a name="property-change-notification-events"></a>屬性變更通知事件
 有時提供事件，以通知使用者屬性值的變更，會很有用。 例如， `System.Windows.Forms.Control` `TextChanged` 在屬性的值變更之後引發事件 `Text` 。

 ✔️考慮當高階 Api 中的屬性值 (通常會修改) 的設計工具元件時引發變更通知事件。

 如果有一個很好的案例，讓使用者知道物件的屬性何時變更，則物件應該會引發屬性的變更通知事件。

 不過，對低層級 Api （例如基底類型或集合）引發這類事件的額外負荷不太可能。 例如， <xref:System.Collections.Generic.List%601> 當新專案加入清單中，且屬性變更時，不會引發這類事件 `Count` 。

 ✔️當屬性的值透過外部強制變更時，請考慮引發變更通知事件。

 如果屬性值是透過某些外部強制 (的方式變更，而不是在物件) 上呼叫方法，則引發事件向開發人員指出值正在變更且已變更。 文字方塊控制項的屬性就是一個很好的例子 `Text` 。 當使用者在中輸入文字時 `TextBox` ，屬性值會自動變更。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [成員設計方針](member.md)
- [架構設計指導方針](index.md)
