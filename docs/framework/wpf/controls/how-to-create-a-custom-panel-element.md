---
title: "如何：建立自訂面板項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7e7cca5b6f7a0d5085e70c4ab6ac33ff83b75217
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-panel-element"></a>如何：建立自訂面板項目
## <a name="example"></a>範例  
 這個範例示範如何覆寫預設配置行為<xref:System.Windows.Controls.Panel>項目及建立自訂版面配置項目衍生自<xref:System.Windows.Controls.Panel>。  
  
 此範例會定義簡單的自訂<xref:System.Windows.Controls.Panel>項目稱為`PlotPanel`，其中放置子項目根據兩個硬式編碼 x 和 y 座標。 在此範例中，`x`和`y`都設定為`50`; 因此，所有子項目會都放置在該位置上的 x 和 y 軸。  
  
 若要實作自訂<xref:System.Windows.Controls.Panel>行為，此範例會使用<xref:System.Windows.FrameworkElement.MeasureOverride%2A>和<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>方法。 每個方法會傳回<xref:System.Windows.Size>定位和呈現子項目所需的資料。  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.Panel>  
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [建立自訂的內容換行面板範例](http://go.microsoft.com/fwlink/?LinkID=159979)
