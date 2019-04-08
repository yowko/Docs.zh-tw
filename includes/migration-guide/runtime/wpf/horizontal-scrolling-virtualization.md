---
ms.openlocfilehash: 0825233c0dae131fa9d00565348fac6fdf0be063
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760628"
---
### <a name="horizontal-scrolling-and-virtualization"></a>水平捲動和虛擬化

|   |   |
|---|---|
|詳細資料|此變更會套用至以正交於主要捲動方向之方向執行自身虛擬化的 <xref:System.Windows.Controls.ItemsControl?displayProperty=name> (主要範例是 EnableColumnVirtualization=&quot;True&quot; 的 <xref:System.Windows.Controls.DataGrid?displayProperty=name>)。  某些水平捲動作業的結果已變更，產生的結果更直覺，且更類似於可比較的垂直作業的結果。<p/>這些作業包括 [捲動至此處] 和 [右邊緣]，以使用以滑鼠右鍵按一下水平捲軸所取得之功能表中的名稱。  這兩個都會計算候選位移並呼叫 <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)>。<p/>捲動至新的位移後，「此處」或「右邊緣」的定義可能已變更，因為最近取消虛擬化的內容已變更 <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> 的值。<p/>在 .NET Framework 4.6.2 之前，捲軸作業會直接使用候選位移，即使它可能已不再是「此處」或位於「右邊緣」。  這會導致類似捲動指標「反彈」的效果，以範例來說明最為合適。 假設 <xref:System.Windows.Controls.DataGrid?displayProperty=name> 具有 ExtentWidth=1000 和 Width=200。  捲動到「右邊緣」會使用候選位移 1000 - 200 = 800。  捲動到該位移時，新的資料行會取消虛擬化；假設它們非常寬，因此 <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> 變更為 2000。  捲軸在 HorizontalOffset=800 結束，而指標會「反彈」回到捲軸中央附近，精確來說是在 800/2000 等於 40% 的位置。<p/>發生這種情況時，變更是重新計算新的候選位移，然後再試一次。 (這是垂直捲動目前運作的方式)。 <p/>此變更會為使用者產生更為可預測且直覺式的體驗，但它會影響依賴 <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=name> 於水平捲動後 (無論是由使用者叫用或是明確呼叫 <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset(System.Double)>) 之確切值的所有應用程式。|
|建議|在因為取消虛擬化而可能變更 <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> 的任何水平捲動之後，為 <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset?displayProperty=name> 使用預測值的應用程式應該改為擷取實際值 (以及 <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth?displayProperty=name> 的值)。|
|範圍|次要|
|版本|4.6.2|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Windows.Controls.Primitives.IScrollInfo?displayProperty=nameWithType></li></ul>|

