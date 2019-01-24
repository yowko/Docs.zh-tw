---
title: HOW TO：建立自訂面板項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
ms.openlocfilehash: 93d9ebacda8c753ab5a4446999e1aa86828a2b9e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621928"
---
# <a name="how-to-create-a-custom-panel-element"></a>HOW TO：建立自訂面板項目
## <a name="example"></a>範例  
 此範例示範如何覆寫預設版面配置行為<xref:System.Windows.Controls.Panel>項目，並建立自訂的版面配置項目衍生自<xref:System.Windows.Controls.Panel>。  
  
 此範例會定義簡單的自訂<xref:System.Windows.Controls.Panel>項目稱為`PlotPanel`，其中放置子項目根據兩個硬式編碼 x 和 y 座標。 在此範例中，`x`並`y`都設為`50`; 因此，所有子項目都位於此位置的 x 和 y 軸。  
  
 若要實作自訂<xref:System.Windows.Controls.Panel>行為，此範例會使用<xref:System.Windows.FrameworkElement.MeasureOverride%2A>和<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>方法。 每個方法會傳回<xref:System.Windows.Size>定位和呈現子項目所需的資料。  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Controls.Panel>
- [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)
- [建立自訂的內容換行面板範例](https://go.microsoft.com/fwlink/?LinkID=159979)
