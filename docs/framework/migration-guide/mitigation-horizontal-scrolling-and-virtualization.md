---
title: "風險降低：水平捲動和虛擬化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5bafd9b-a3b3-4f92-8241-2aad254fb1a9
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 40eaf185e9c0c60493e9a2e5428c58b7463789fe
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-horizontal-scrolling-and-virtualization"></a>風險降低：水平捲動和虛擬化
此變更會套用到以正交於主要捲動方向之方向執行自身的虛擬化的 <xref:System.Windows.Controls.ItemsControl>。 (主要範例是 <xref:System.Windows.Controls.DataGrid.EnableColumnVirtualization%2A> 設定為 `true` 的 <xref:System.Windows.Controls.DataGrid> 控制項)。某些水平捲動作業的結果已變更，產生的結果更直覺，且更類似於可比較的垂直作業的結果。  具體的作業包括 [捲動至此處] 和 [右邊緣]，以使用以滑鼠右鍵按一下水平捲軸所取得之功能表中的名稱。  這兩個都會計算候選位移並呼叫 <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset%2A?displayProperty=fullName>。  捲動至新的位移後，「此處」或「右邊緣」的定義可能已變更，因為最近取消虛擬化的內容已變更 <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A?displayProperty=fullName> 的值。  
  
## <a name="description-of-the-change"></a>變更的描述  
 在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 之前，捲軸作業會直接使用候選位移，即使它可能已不再是「此處」或位於「右邊緣」。  這會導致類似捲動指標「反彈」的效果，以範例說明最為合適。  假設 <xref:System.Windows.Controls.DataGrid> 控制項的 <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A> 設為 1000，而 <xref:System.Windows.FrameworkElement.Width%2A> 設為 200。  捲動到「右邊緣」會使用候選位移 1000 - 200 = 800。  捲動到該位移時，新的資料行會取消虛擬化；假設它們非常寬，因此 <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A> 變更為 2000。  捲軸在 <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A>= 800 結束，而指標會反彈回到捲軸中央附近，精確來說是在 800/2000 等於 40% 的位置。  
  
 從 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 開始，發生這種情況時，會重新計算新的候選位移。 (這是垂直捲動目前運作的方式)。  
  
## <a name="impact"></a>影響  
 此變更會為使用者產生更為可預測且直覺式的體驗，但它會影響依賴 <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A?displayProperty=fullName> 於水平捲動後 (無論是由使用者叫用或是明確呼叫 <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset%2A?displayProperty=fullName>) 之確切值的所有應用程式。  
  
## <a name="mitigation"></a>緩和  
 在因為取消虛擬化而可能變更 <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A> 的任何水平捲動之後，為 <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A?displayProperty=fullName> 使用預測值的應用程式應該改為擷取實際的值 (以及 <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A> 的值)。  
  
## <a name="see-also"></a>另請參閱  
 [執行階段變更](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-2.md)

