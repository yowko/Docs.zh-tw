---
title: HScrollBar 和 VScrollBar 控制項概觀
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
ms.openlocfilehash: abe0c8da9723f17cb80715454f6ab7297724a21f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728168"
---
# <a name="hscrollbar-and-vscrollbar-controls-overview-windows-forms"></a>HScrollBar 和 VScrollBar 控制項概觀 (Windows Form)
Windows Forms <xref:System.Windows.Forms.ScrollBar> 控制項是用來透過在應用程式或控制項內水準或垂直捲動，輕鬆地流覽長清單的專案或大量的資訊。 捲軸是 Windows 介面的通用元素，因此，<xref:System.Windows.Forms.ScrollBar> 控制項通常會與不是衍生自 <xref:System.Windows.Forms.ScrollableControl> 類別的控制項一起使用。 同樣地，許多開發人員在撰寫自己的使用者控制項時，也會選擇納入 <xref:System.Windows.Forms.ScrollBar> 控制項。  
  
 <xref:System.Windows.Forms.HScrollBar> （水準）和 <xref:System.Windows.Forms.VScrollBar> （垂直）控制項與其他控制項獨立運作，而且有自己的一組事件、屬性和方法。 <xref:System.Windows.Forms.ScrollBar> 控制項與附加至文字方塊、清單方塊、下拉式方塊或 MDI 表單的內建捲軸不同（<xref:System.Windows.Forms.TextBox> 控制項具有 <xref:System.Windows.Forms.TextBox.ScrollBars%2A> 屬性，可顯示或隱藏附加至控制項的捲軸）。  
  
 <xref:System.Windows.Forms.ScrollBar> 控制項使用 <xref:System.Windows.Forms.ScrollBar.Scroll> 事件來監視捲動方塊的移動（有時也稱為捲軸）。 使用 <xref:System.Windows.Forms.ScrollBar.Scroll> 事件會在拖曳時提供捲軸值的存取權。  
  
## <a name="value-property"></a>值屬性  
 [<xref:System.Windows.Forms.ScrollBar.Value%2A>] 屬性（預設為0）是對應到捲軸之捲動方塊位置的 `integer` 值。 當捲動方塊位置是最小值時，它會移至最左邊的位置（適用于水準捲軸）或頂端位置（適用于垂直捲動條）。 當捲動方塊為最大值時，捲動方塊會移到最右邊或底部的位置。 同樣地，範圍底端和頂端之間的值，會將捲動方塊的前置邊緣放在捲軸的中間。  
  
 除了使用滑鼠點按來變更捲軸值之外，使用者也可以將捲動方塊拖曳至橫條的任何點。 產生的值會根據捲動方塊的位置而定，但一定會在 <xref:System.Windows.Forms.ScrollBar.Minimum%2A> 的範圍內，以 <xref:System.Windows.Forms.ScrollBar.Maximum%2A> 使用者所設定的屬性。  
  
## <a name="largechange-and-smallchange-properties"></a>LargeChange 和 SmallChange 屬性  
 當使用者按 PAGE UP 或 PAGE DOWN 鍵，或按一下捲動方塊任一側的捲軸播放軌時，<xref:System.Windows.Forms.ScrollBar.Value%2A> 屬性會根據 <xref:System.Windows.Forms.ScrollBar.LargeChange%2A> 屬性中設定的值而變更。  
  
 當使用者按下其中一個方向鍵或按一下其中一個捲軸按鈕時，<xref:System.Windows.Forms.ScrollBar.Value%2A> 屬性會根據 <xref:System.Windows.Forms.ScrollBar.SmallChange%2A> 屬性中設定的值而變更。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.HScrollBar>
- <xref:System.Windows.Forms.VScrollBar>
- [在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)
