---
title: HOW TO：使用 BetweenShowDelay 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- ToolTip control [WPF], BetweenShowDelay time property
- BetweenShowDelay time property [WPF]
ms.assetid: 984ea76d-f2a2-4326-a02e-f97ec3d036d6
ms.openlocfilehash: b6d55c72c8264546949833fc086937a8b1fe2540
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59139590"
---
# <a name="how-to-use-the-betweenshowdelay-property"></a>HOW TO：使用 BetweenShowDelay 屬性
此範例示範如何使用<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>時間屬性，如此工具提示會顯示快速 — 幾乎沒有任何延遲，當使用者將從一個工具提示直接到另一個滑鼠指標。  
  
## <a name="example"></a>範例  
 在下列範例中，<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>屬性設定為一秒 （1000年毫秒為單位） 和<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>設定為兩秒鐘 （2000年毫秒為單位），兩者的工具提示<xref:System.Windows.Shapes.Ellipse>控制項。 如果您顯示的工具提示的其中一個的省略符號，然後在其上移動至另一個橢圓形內兩秒] 及 [暫停滑鼠指標，第二個橢圓形的工具提示就會立即顯示。  
  
 在下列案例中，任一<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>套用，因而導致等候 1 秒才會出現第二個橢圓形的工具提示：  
  
-   移至所花費的時間，如果第二個按鈕是超過兩秒。  
  
-   如果在第一個橢圓形的時間間隔的開頭看不到工具提示。  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
[!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [HOW-TO 主題](tooltip-how-to-topics.md)
- [工具提示概觀](tooltip-overview.md)
