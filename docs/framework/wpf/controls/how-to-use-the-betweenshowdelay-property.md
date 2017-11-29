---
title: "如何：使用 BetweenShowDelay 屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolTip control [WPF], BetweenShowDelay time property
- BetweenShowDelay time property [WPF]
ms.assetid: 984ea76d-f2a2-4326-a02e-f97ec3d036d6
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dca6dc7c6238ef4accc921818090237d17ce1cbd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-betweenshowdelay-property"></a>如何：使用 BetweenShowDelay 屬性
這個範例示範如何使用<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>時間屬性，如此工具提示會顯示快速 — 有少量或沒有延遲，當使用者將從一個工具提示直接到另一個滑鼠指標。  
  
## <a name="example"></a>範例  
 在下列範例中，<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>屬性設定為一秒 （1000年毫秒為單位） 和<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>設為兩秒 （2000年毫秒為單位），兩者的工具提示<xref:System.Windows.Shapes.Ellipse>控制項。 如果您顯示其中一個橢圓形的工具提示，然後在其上移動至另一個橢圓形兩秒暫停中將滑鼠指標，第二個橢圓形的工具提示會立即顯示。  
  
 下列案例中，任一<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>套用，因而導致等候 1 秒，才會出現第二個橢圓形的工具提示：  
  
-   移至所花費的時間，如果第二個按鈕是超過兩秒。  
  
-   如果在第一個橢圓形的時間間隔的開頭看不到工具提示。  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
[!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [操作說明主題](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [工具提示概觀](../../../../docs/framework/wpf/controls/tooltip-overview.md)
