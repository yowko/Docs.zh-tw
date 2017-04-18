---
title: "如何：指定自訂 Popup 的位置 | Microsoft Docs"
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
  - "Popup 控制項, 指定自訂位置"
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：指定自訂 Popup 的位置
本範例說明當 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 屬性設定為 <xref:System.Windows.Controls.Primitives.PlacementMode> 時，如何指定 <xref:System.Windows.Controls.Primitives.Popup> 控制項的自訂位置。  
  
## 範例  
 當 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 屬性設定為 <xref:System.Windows.Controls.Primitives.PlacementMode> 時，<xref:System.Windows.Controls.Primitives.Popup> 會呼叫 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> 委派的已定義執行個體。  這個委派會傳回一組相對於目標區域左上角和 <xref:System.Windows.Controls.Primitives.Popup> 左上角的可能點。  在提供最佳可視性的點上，會放置 <xref:System.Windows.Controls.Primitives.Popup>。  
  
 下列範例說明如何將 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 屬性設定為 <xref:System.Windows.Controls.Primitives.PlacementMode>，藉以定義 <xref:System.Windows.Controls.Primitives.Popup> 的位置。  它也說明如何建立並指派 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> 委派，以便放置 <xref:System.Windows.Controls.Primitives.Popup>。  回呼委派會傳回兩個 <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> 物件。  如果 <xref:System.Windows.Controls.Primitives.Popup> 在第一個位置上被畫面邊緣隱藏，就會將 <xref:System.Windows.Controls.Primitives.Popup> 放置在第二個位置上。  
  
 [!code-xml[PopupCustomPlacement#CustomPlacement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 如需完整範例，請參閱[快顯功能表位置範例](http://go.microsoft.com/fwlink/?LinkID=160032) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Controls.Primitives.Popup>   
 [快顯功能表概觀](../../../../docs/framework/wpf/controls/popup-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)