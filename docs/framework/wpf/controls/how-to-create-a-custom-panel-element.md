---
title: "如何：建立自訂面板項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "自訂 Panel 項目"
  - "Panel 控制項"
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：建立自訂面板項目
## 範例  
 本範例說明如何覆寫 <xref:System.Windows.Controls.Panel> 項目的預設版面配置行為，並建立衍生自 <xref:System.Windows.Controls.Panel> 的自訂版面配置項目。  
  
 此範例會定義一個名為 `PlotPanel` 的簡單自訂 <xref:System.Windows.Controls.Panel> 項目，這個項目會根據兩個硬式編碼的 X 和 Y 座標放置子項目的位置。  在這個範例中，`x` 和 `y` 都設為 `50`，因此，所有子項目都會放在 X 和 Y 軸上的該位置。  
  
 為實作自訂 <xref:System.Windows.Controls.Panel> 行為，此範例使用 <xref:System.Windows.FrameworkElement.MeasureOverride%2A> 和 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> 方法。  每個方法會傳回放置和呈現子項目所需的 <xref:System.Windows.Size> 資料。  
  
 [!code-cpp[PlotPanel#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## 請參閱  
 <xref:System.Windows.Controls.Panel>   
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [建立自訂內容換行面板範例](http://go.microsoft.com/fwlink/?LinkID=159979)