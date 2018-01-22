---
title: "HScrollBar 和 VScrollBar 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8fbdb3778959d1691200cde49e485d8a63c6e645
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="hscrollbar-and-vscrollbar-controls-overview-windows-forms"></a>HScrollBar 和 VScrollBar 控制項概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.ScrollBar>控制項可用來捲動的水平或垂直應用程式或控制項內提供輕鬆瀏覽一長串的項目或大量的資訊。 捲軸是通用的項目，Windows 介面，所以<xref:System.Windows.Forms.ScrollBar>控制項則通常會搭配控制項不是衍生自<xref:System.Windows.Forms.ScrollableControl>類別。 同樣地，許多開發人員選擇加入<xref:System.Windows.Forms.ScrollBar>控制製作自己的使用者控制項時。  
  
 <xref:System.Windows.Forms.HScrollBar> （水平） 和<xref:System.Windows.Forms.VScrollBar>（垂直） 的控制項是其他控制項從獨立運作，並且有它們自己的事件、 屬性和方法。 <xref:System.Windows.Forms.ScrollBar>控制項不會附加至文字方塊、 清單方塊、 下拉式方塊或 MDI 表單的內建的捲軸相同 (<xref:System.Windows.Forms.TextBox>控制項有<xref:System.Windows.Forms.TextBox.ScrollBars%2A>屬性，即可顯示或隱藏附加到控制項的捲軸)。  
  
 <xref:System.Windows.Forms.ScrollBar>會控制使用<xref:System.Windows.Forms.ScrollBar.Scroll>事件監視 （有時稱為 「 捲動方塊 」） 的捲動方塊的移動捲軸上。 使用<xref:System.Windows.Forms.ScrollBar.Scroll>事件提供正在拖曳捲軸值的存取。  
  
## <a name="value-property"></a>值屬性  
 <xref:System.Windows.Forms.ScrollBar.Value%2A> （即，根據預設，0） 的屬性是`integer`捲軸的捲動方塊的位置對應的值。 最小值捲動方塊位置時，它會移動到最左邊的位置 （適用於水平捲軸） 或 （適用於垂直捲軸） 上方的位置。 捲動方塊時的最大值、 捲軸方塊移至最右側或底部的位置。 同樣地，中間範圍的最底部之間的值將放在前置邊緣的中間捲軸的捲動方塊。  
  
 除了使用滑鼠點按動作來變更捲軸值，使用者也可以拖曳捲動方塊的軸上的任何位置。 產生的值取決於捲動方塊的位置，但它一定會在各種<xref:System.Windows.Forms.ScrollBar.Minimum%2A>至<xref:System.Windows.Forms.ScrollBar.Maximum%2A>使用者所設定的屬性。  
  
## <a name="largechange-and-smallchange-properties"></a>LargeChange 和 SmallChange 屬性  
 當使用者按下 PAGE UP 或 PAGE DOWN 鍵，或在捲軸追蹤任一邊的捲軸 方塊中，按一下<xref:System.Windows.Forms.ScrollBar.Value%2A>屬性變更的設定值根據<xref:System.Windows.Forms.ScrollBar.LargeChange%2A>屬性。  
  
 當使用者按下一個箭號的索引鍵或按下捲軸按鈕中，其中<xref:System.Windows.Forms.ScrollBar.Value%2A>屬性變更的設定值根據<xref:System.Windows.Forms.ScrollBar.SmallChange%2A>屬性。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.HScrollBar>  
 <xref:System.Windows.Forms.VScrollBar>  
 [Windows form 的新增項目，適用於.NET Framework 2.0](http://msdn.microsoft.com/library/c61a923d-3d6a-4c8c-820c-e94c83f3f9a8)  
 [在 Windows Forms 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
