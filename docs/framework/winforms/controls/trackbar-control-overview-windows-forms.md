---
title: TrackBar 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
ms.openlocfilehash: 6901405100df4633c84850757f55b756bc9a0199
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741463"
---
# <a name="trackbar-control-overview-windows-forms"></a>TrackBar 控制項概觀 (Windows Form)
Windows Forms <xref:System.Windows.Forms.TrackBar> 控制項（有時也稱為「滑杆」控制項）是用來流覽大量資訊，或用來以視覺方式調整數值設定。 <xref:System.Windows.Forms.TrackBar> 控制項有兩個部分： thumb （也稱為滑杆）和刻度標記。 捲動方塊是可以調整的部分。 其位置會對應至 <xref:System.Windows.Forms.TrackBar.Value%2A> 屬性。 刻度是以固定間隔分隔的視覺指示器。 並排會以您指定的增量移動，而且可以水準或垂直對齊。 例如，您可以使用追蹤列來控制系統的游標閃爍頻率或滑鼠速度。  
  
## <a name="key-properties"></a>索引鍵內容  
 <xref:System.Windows.Forms.TrackBar> 控制項的索引鍵屬性是 <xref:System.Windows.Forms.TrackBar.Value%2A>、<xref:System.Windows.Forms.TrackBar.TickFrequency%2A>、<xref:System.Windows.Forms.TrackBar.Minimum%2A>和 <xref:System.Windows.Forms.TrackBar.Maximum%2A>。 <xref:System.Windows.Forms.TrackBar.TickFrequency%2A> 是刻度的間距。 <xref:System.Windows.Forms.TrackBar.Minimum%2A> 和 <xref:System.Windows.Forms.TrackBar.Maximum%2A> 是可在追蹤列上表示的最小和最大值。  
  
 另外還有兩個重要的屬性 <xref:System.Windows.Forms.TrackBar.SmallChange%2A> 和 <xref:System.Windows.Forms.TrackBar.LargeChange%2A>。 <xref:System.Windows.Forms.TrackBar.SmallChange%2A> 屬性的值是捲動方塊的位置數目，以回應按下向左鍵或向右鍵。 [<xref:System.Windows.Forms.TrackBar.LargeChange%2A>] 屬性的值是捲動方塊的位置數，以回應按下 PAGE UP 或 PAGE DOWN 鍵，或在捲軸兩側的追蹤列上按一下滑鼠右鍵。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.TrackBar>
- [TrackBar 控制項](trackbar-control-windows-forms.md)
