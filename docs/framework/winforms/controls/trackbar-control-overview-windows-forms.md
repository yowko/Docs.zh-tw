---
title: "TrackBar 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: TrackBar
helpviewer_keywords:
- sliders [Windows Forms], about sliders
- TrackBar control [Windows Forms], about TrackBar control
- slider controls [Windows Forms], about slider controls
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e62fc49a8a08c79138df080246b99b6fe891162e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="trackbar-control-overview-windows-forms"></a>TrackBar 控制項概觀 (Windows Form)
Windows Form<xref:System.Windows.Forms.TrackBar>控制項 （有時也稱為 「 滑桿 」 控制項） 用來瀏覽大量的資訊或以視覺方式調整數字設定。 <xref:System.Windows.Forms.TrackBar>控制項有兩個部分： 也稱為滑桿，與刻度標記縮圖。 基本原則是可調整的部分。 它的位置對應至<xref:System.Windows.Forms.TrackBar.Value%2A>屬性。 刻度是定期為間距的視覺指標。 Trackbar 移動您指定和可以對齊水平或垂直增量。 例如，您可能會使用追蹤列來控制系統游標閃爍頻率或滑鼠速度。  
  
## <a name="key-properties"></a>索引鍵內容  
 索引鍵屬性<xref:System.Windows.Forms.TrackBar>控制是<xref:System.Windows.Forms.TrackBar.Value%2A>， <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>， <xref:System.Windows.Forms.TrackBar.Minimum%2A>，和<xref:System.Windows.Forms.TrackBar.Maximum%2A>。 <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>是刻度的間距。 <xref:System.Windows.Forms.TrackBar.Minimum%2A>和<xref:System.Windows.Forms.TrackBar.Maximum%2A>是可以在追蹤列表示的最小和最大值。  
  
 其他兩個重要的屬性是<xref:System.Windows.Forms.TrackBar.SmallChange%2A>和<xref:System.Windows.Forms.TrackBar.LargeChange%2A>。 值<xref:System.Windows.Forms.TrackBar.SmallChange%2A>屬性是回應需要按下的左或向右箭號鍵移動捲動方塊的位置數目。 值<xref:System.Windows.Forms.TrackBar.LargeChange%2A>屬性是捲動方塊回應具有 PAGE UP 或 PAGE DOWN 按鍵，移動或以回應滑鼠按一下捲動方塊的任一端追蹤列上的位置數目。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.TrackBar>  
 [TrackBar 控制項](../../../../docs/framework/winforms/controls/trackbar-control-windows-forms.md)
