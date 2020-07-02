---
ms.openlocfilehash: 35fc4782ebbba33f5fc6668712af9d89d00cafe9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614618"
---
### <a name="wpf-changing-a-primary-key-when-displaying-ado-data-in-a-masterdetail-scenario"></a>WPF 在主要/詳細資料案例中顯示 ADO 資料時會變更主索引鍵

#### <a name="details"></a>詳細資料

假設您有 `Order` 類型的 ADO 項目集合，並具有名為 &quot;OrderDetails&quot; 的關係，透過主索引鍵 &quot;OrderID&quot; 將它與 `Detail` 類型的項目集合相關聯。 在 WPF 應用程式中，您可以將清單控制項繫結到指定訂單的詳細資料：

```xaml
<ListBox ItemsSource="{Binding Path=OrderDetails}" >
```

其中 DataContext 是 `Order`。 WPF 會取得屬性的值 `OrderDetails` -所有專案的集合 D， `Detail` 其 `OrderID` 符合 `OrderID` 主要專案的。 當您變更主要專案的主鍵時，就會發生行為變更 `OrderID` 。 ADO 會自動變更 Details 集合中每個受影響記錄的 `OrderID` (也就是複製到集合 D 的項目)。  但 D 會發生什麼情況？

- 舊的行為：集合 D 已清除。 主要項目*不會*針對屬性 `OrderDetails` 引發變更通知。 ListBox 會繼續使用集合 D (它現在是空的)。
- 新的行為：系統不會變更集合 D。 其每個項目都會針對 `OrderID` 屬性引發變更通知。 ListBox 會繼續使用集合 D，並以新的 `OrderID` 來顯示詳細資料。 WPF 會透過以不同的方式建立集合 D 來實作新的行為，也就是搭配將 `followParent` 引數設定為 `true` 來呼叫 ADO 方法 <xref:System.Data.DataRowView.CreateChildView(System.Data.DataRelation,System.Boolean)?displayProperty=nameWithType>。

#### <a name="suggestion"></a>建議

應用程式能透過使用下列 AppContext 參數來取得新的行為。

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Data.DoNotUseFollowParentWhenBindingToADODataRelation=false"/>
  </runtime>
</configuration>
```

針對以 .NET 4.7.1 或更舊版本為目標的應用程式，此參數的預設值為 `true` (舊行為)，而針對以 .NET 4.7.2 或更新版本為目標的應用程式，預設值則為 `false` (新行為)。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.7.2       |
| 類型    | 正在重定目標 |
