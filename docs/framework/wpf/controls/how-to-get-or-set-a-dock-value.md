---
title: HOW TO：取得或設定 Dock 值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock values [WPF], setting
- Dock values [WPF], getting
ms.assetid: fcf4ab8a-c7cd-4835-8d04-de1c999ab4a8
ms.openlocfilehash: fb6c8a7d62aa09a6e1d82cb4079d1425a7f39f8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910282"
---
# <a name="how-to-get-or-set-a-dock-value"></a>HOW TO：取得或設定 Dock 值
下列範例示範如何指派<xref:System.Windows.Controls.Dock>物件的值。 此範例會使用<xref:System.Windows.Controls.DockPanel.GetDock%2A>並<xref:System.Windows.Controls.DockPanel.SetDock%2A>方法<xref:System.Windows.Controls.DockPanel>。  
  
## <a name="example"></a>範例  
 此範例會建立的執行個體<xref:System.Windows.Controls.TextBlock>項目， `txt1`，並指派<xref:System.Windows.Controls.Dock>的值`Top`利用<xref:System.Windows.Controls.DockPanel.SetDock%2A>方法<xref:System.Windows.Controls.DockPanel>。 然後將附加的值<xref:System.Windows.Controls.Dock>屬性，以<xref:System.Windows.Controls.TextBlock.Text%2A>的<xref:System.Windows.Controls.TextBlock>使用的項目<xref:System.Windows.Controls.DockPanel.GetDock%2A>方法。 最後，範例會新增<xref:System.Windows.Controls.TextBlock>父系的項目<xref:System.Windows.Controls.DockPanel>， `dp1`。  
  
 [!code-csharp[DockPanelSetDock#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelSetDock/CSharp/DockPanel_SetDock.cs#1)]
 [!code-vb[DockPanelSetDock#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelSetDock/VisualBasic/DockPanel_SetDock.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.DockPanel.GetDock%2A>
- <xref:System.Windows.Controls.DockPanel.SetDock%2A>
- [面板概觀](panels-overview.md)
