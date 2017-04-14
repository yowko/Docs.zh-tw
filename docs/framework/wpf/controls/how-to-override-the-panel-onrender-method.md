---
title: "如何：覆寫 Panel 的 OnRender 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "overriding OnRender method"
  - "Panel control, overriding OnRender method"
  - "OnRender method"
  - "controls, Panel, overriding OnRender method"
helpviewer_keywords: 
  - "OnRender 方法, 覆寫"
  - "覆寫 Panel 控制項的 OnRender 方法"
  - "Panel 控制項, 覆寫 OnRender 方法"
ms.assetid: 57397834-a085-4e36-90ab-416fad98f341
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：覆寫 Panel 的 OnRender 方法
本範例說明如何覆寫 <xref:System.Windows.Controls.Panel> 的 <xref:System.Windows.Controls.Panel.OnRender%2A> 方法，在版面配置項目中加入自訂圖形化效果。  
  
## 範例  
 使用 <xref:System.Windows.Controls.Panel.OnRender%2A> 方法，在呈現的面板項目中加入圖形化效果。  例如，您可以使用這個方法加入自訂框線或背景效果。  當做引數傳遞的 <xref:System.Windows.Media.DrawingContext> 物件，會提供繪製圖案、文字、影像或視訊的方法。  因此，這個方法對於自訂面板物件而言相當實用。  
  
 [!code-csharp[LightWeightCustomPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## 請參閱  
 <xref:System.Windows.Controls.Panel>   
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [自訂放射狀面板範例](http://go.microsoft.com/fwlink/?LinkID=159982)   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/panel-how-to-topics.md)