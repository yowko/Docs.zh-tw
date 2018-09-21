---
title: HScrollBar 和 VScrollBar 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- HScrollBar
- VScrollBar
helpviewer_keywords:
- ScrollBar control [Windows Forms]
- HScrollBar control [Windows Forms], about HScrollBar
- VScrollBar control [Windows Forms], about VScrollBar control
- ScrollBar control [Windows Forms], about ScrollBar control
- scroll bars [Windows Forms], about scroll bars
ms.assetid: 8b307679-1cae-41d8-99aa-3d1efd207cd6
ms.openlocfilehash: 2c6436e77753322733580acba5a20d6bb220f29c
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46561431"
---
# <a name="hscrollbar-and-vscrollbar-controls-overview-windows-forms"></a>HScrollBar 和 VScrollBar 控制項概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.ScrollBar>控制項可用來提供輕鬆瀏覽一長串，項目或大量的資訊，請水平或垂直方式捲動應用程式或控制項內。 捲軸是通用的項目，在 Windows 介面中，因此<xref:System.Windows.Forms.ScrollBar>控制項通常會搭配控制項不是衍生自<xref:System.Windows.Forms.ScrollableControl>類別。 同樣地，許多開發人員選擇納入<xref:System.Windows.Forms.ScrollBar>控制撰寫自己的使用者控制項時。  
  
 <xref:System.Windows.Forms.HScrollBar> （水平） 和<xref:System.Windows.Forms.VScrollBar>（垂直） 的控制項獨立運作，從其他控制項，並有自己的事件、 屬性和方法集。 <xref:System.Windows.Forms.ScrollBar> 控制項不會附加至文字方塊、 清單方塊、 下拉式方塊或 MDI 表單內建的捲軸相同 (<xref:System.Windows.Forms.TextBox>控制項有<xref:System.Windows.Forms.TextBox.ScrollBars%2A>屬性，以顯示或隱藏會附加至控制項的捲軸)。  
  
 <xref:System.Windows.Forms.ScrollBar>控制項會使用<xref:System.Windows.Forms.ScrollBar.Scroll>事件監視 （有時也稱為捲動方塊） 的捲動方塊移動捲軸上。 使用<xref:System.Windows.Forms.ScrollBar.Scroll>事件提供捲軸值的存取，因為它被拖曳。  
  
## <a name="value-property"></a>值屬性  
 <xref:System.Windows.Forms.ScrollBar.Value%2A> （即，根據預設，0） 的屬性是`integer`捲軸的捲動方塊的位置對應的值。 最小值捲動方塊位置時，它會移動到最左邊的位置 （適用於水平捲軸） 或 （適用於垂直捲軸） 的最高位置。 捲動方塊時的最大值、 捲軸方塊移到最右邊或底部位置。 同樣地，中間範圍的最底部之間的值會放置前端邊緣的中間的捲軸捲動方塊。  
  
 除了使用滑鼠點按的捲軸列的值變更，使用者也可以拖曳捲動方塊到在軸上的任意點。 產生的值取決於捲軸 方塊中，位置，但它一定會在各種<xref:System.Windows.Forms.ScrollBar.Minimum%2A>至<xref:System.Windows.Forms.ScrollBar.Maximum%2A>使用者所設定的屬性。  
  
## <a name="largechange-and-smallchange-properties"></a>LargeChange 和 SmallChange 屬性  
 當使用者按下 PAGE UP 或 PAGE DOWN 鍵，或按一下捲軸軌跡任一邊的捲軸 方塊中，在<xref:System.Windows.Forms.ScrollBar.Value%2A>屬性變更中設定的值根據<xref:System.Windows.Forms.ScrollBar.LargeChange%2A>屬性。  
  
 當使用者按下其中一個箭號的索引鍵，或按一下捲軸按鈕中，其中<xref:System.Windows.Forms.ScrollBar.Value%2A>屬性變更中設定的值根據<xref:System.Windows.Forms.ScrollBar.SmallChange%2A>屬性。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.HScrollBar>  
 <xref:System.Windows.Forms.VScrollBar>  
 [適用於.NET Framework 2.0 的新增功能至 Windows Forms](https://msdn.microsoft.com/library/c61a923d-3d6a-4c8c-820c-e94c83f3f9a8)  
 [在 Windows Forms 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
