---
title: TrackBar 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
ms.openlocfilehash: 27a43befd69bc3fb33f8027bd32fc4d66414951c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54711995"
---
# <a name="trackbar-control-overview-windows-forms"></a>TrackBar 控制項概觀 (Windows Form)
Windows Form <xref:System.Windows.Forms.TrackBar> （有時也稱為 「 滑桿 」 控制項） 的控制項用來巡覽大量的資訊，或適用於以視覺方式調整數字設定。 <xref:System.Windows.Forms.TrackBar>控制項有兩個部分： 基本原則是，也就是滑桿和刻度標記。 基本原則是可調整的部分。 其位置與相對應<xref:System.Windows.Forms.TrackBar.Value%2A>屬性。 刻度標記會定期間距的視覺指標。 Trackbar 移動中指定，並可以在水平或垂直對齊的變化。 例如，您可能會使用追蹤列來控制系統游標閃爍頻率或滑鼠速度。  
  
## <a name="key-properties"></a>索引鍵內容  
 索引鍵屬性<xref:System.Windows.Forms.TrackBar>控制項<xref:System.Windows.Forms.TrackBar.Value%2A>， <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>， <xref:System.Windows.Forms.TrackBar.Minimum%2A>，和<xref:System.Windows.Forms.TrackBar.Maximum%2A>。 <xref:System.Windows.Forms.TrackBar.TickFrequency%2A> 是的刻度的間距。 <xref:System.Windows.Forms.TrackBar.Minimum%2A> 和<xref:System.Windows.Forms.TrackBar.Maximum%2A>是可以表示追蹤列的最小和最大值。  
  
 其他兩個重要屬性是<xref:System.Windows.Forms.TrackBar.SmallChange%2A>和<xref:System.Windows.Forms.TrackBar.LargeChange%2A>。 值<xref:System.Windows.Forms.TrackBar.SmallChange%2A>屬性是捲動方塊移動以回應具有按下左或向右箭號索引鍵的位置數目。 值<xref:System.Windows.Forms.TrackBar.LargeChange%2A>屬性是捲動方塊移動以回應具有 PAGE UP 或 PAGE DOWN 按鍵，或以回應滑鼠按一下捲動方塊的任一端的追蹤列上的位置數目。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.TrackBar>
- [TrackBar 控制項](../../../../docs/framework/winforms/controls/trackbar-control-windows-forms.md)
