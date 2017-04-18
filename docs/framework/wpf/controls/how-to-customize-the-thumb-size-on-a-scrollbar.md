---
title: "如何：自訂 ScrollBar 上捲動方塊的大小 | Microsoft Docs"
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
  - "自訂捲動方塊大小"
  - "ScrollBar 控制項"
  - "捲動方塊大小"
ms.assetid: fa32b866-5ca1-4e73-85e7-2ac64b80d194
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：自訂 ScrollBar 上捲動方塊的大小
本主題說明如何將 <xref:System.Windows.Controls.Primitives.ScrollBar> 的 <xref:System.Windows.Controls.Primitives.Thumb> 設為固定大小，以及如何為 <xref:System.Windows.Controls.Primitives.ScrollBar> 的 <xref:System.Windows.Controls.Primitives.Thumb> 指定最小大小。  
  
## 範例  
  
## 描述  
 下列範例將建立 <xref:System.Windows.Controls.Primitives.Thumb> 使用固定大小的 <xref:System.Windows.Controls.Primitives.ScrollBar>。  此範例會將 <xref:System.Windows.Controls.Primitives.Thumb> 的 <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> 屬性設為 <xref:System.Double.NaN>，並設定 <xref:System.Windows.Controls.Primitives.Thumb> 的高度。  若要建立 <xref:System.Windows.Controls.Primitives.Thumb> 使用固定寬度的水平 <xref:System.Windows.Controls.Primitives.ScrollBar>，請設定 <xref:System.Windows.Controls.Primitives.Thumb> 的寬度。  
  
## 程式碼  
 [!code-xml[ScrollBarCustomThumbSize#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#1)]  
  
## 描述  
 下列範例將建立 <xref:System.Windows.Controls.Primitives.Thumb> 使用最小大小的 <xref:System.Windows.Controls.Primitives.ScrollBar>。  此範例會設定 <xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A> 的值。  若要建立 <xref:System.Windows.Controls.Primitives.Thumb> 使用最小寬度的水平 <xref:System.Windows.Controls.Primitives.ScrollBar>，請設定 <xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A> 的寬度。  
  
## 程式碼  
 [!code-xml[ScrollBarCustomThumbSize#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#2)]  
  
## 請參閱  
 [ScrollBar 樣式和範本](../../../../docs/framework/wpf/controls/scrollbar-styles-and-templates.md)