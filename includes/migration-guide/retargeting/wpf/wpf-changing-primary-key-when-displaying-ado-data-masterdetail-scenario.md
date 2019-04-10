---
ms.openlocfilehash: 1d9841b9c8989a07820c75ac07940c90e5c0753e
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760795"
---
### <a name="wpf-changing-a-primary-key-when-displaying-ado-data-in-a-masterdetail-scenario"></a>WPF 在主要/詳細資料案例中顯示 ADO 資料時會變更主索引鍵

|   |   |
|---|---|
|詳細資料|假設您有 <code>Order</code> 類型的 ADO 項目集合，並具有名為 &quot;OrderDetails&quot; 的關係，透過主索引鍵 &quot;OrderID&quot; 將它與 <code>Detail</code> 類型的項目集合相關聯。 在 WPF 應用程式中，您可以將清單控制項繫結到指定訂單的詳細資料：<pre><code class="lang-xml">&lt;ListBox ItemsSource=&quot;{Binding Path=OrderDetails}&quot; &gt;&#13;&#10;</code></pre>其中 DataContext 是 <code>Order</code>。 WPF 會取得 <code>OrderDetails</code> 屬性的值，也就是所有 <code>Detail</code> 項目的集合 D，這些項目的 <code>OrderID</code> 會符合主要項目的 <code>OrderID</code>。當您變更主要項目的主索引鍵 <code>OrderID</code> 時，就會發生此行為變更。 ADO 會自動變更 Details 集合中每個受影響記錄的 <code>OrderID</code> (也就是複製到集合 D 的項目)。  但 D 會發生什麼情況？<ul><li>舊的行為： 系統會清除集合 D。   主要項目<em>不會</em>針對屬性 <code>OrderDetails</code> 引發變更通知。  ListBox 會繼續使用集合 D (它現在是空的)。</li><li>新的行為：系統不會變更集合 D。   其每個項目都會針對 <code>OrderID</code> 屬性引發變更通知。  ListBox 會繼續使用集合 D，並以新的 <code>OrderID</code> 來顯示詳細資料。</li></ul>WPF 會透過以不同的方式建立集合 D 來實作新的行為，也就是搭配將 <code>followParent</code> 引數設定為 <code>true</code> 來呼叫 ADO 方法 <xref:System.Data.DataRowView.CreateChildView(System.Data.DataRelation,System.Boolean)?displayProperty=nameWithType>。|
|建議|應用程式能透過使用下列 AppContext 參數來取得新的行為。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Data.DoNotUseFollowParentWhenBindingToADODataRelation=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;&#13;&#10;</code></pre>針對以 .NET 4.7.1 或更舊版本為目標的應用程式，此參數的預設值為 <code>true</code> (舊行為)，而針對以 .NET 4.7.2 或更新版本為目標的應用程式，預設值則為 <code>false</code> (新行為)。|
|範圍|次要|
|版本|4.7.2|
|類型|正在重定目標|

