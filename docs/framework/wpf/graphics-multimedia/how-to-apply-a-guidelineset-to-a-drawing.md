---
title: "如何：對圖形套用 GuidelineSet | Microsoft Docs"
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
  - "圖形 [WPF], GuidelineSet 屬性"
  - "GuidelineSet 屬性, 套用到繪圖"
ms.assetid: 45f3e0b4-8820-45a7-b865-b8ea5b17b0c8
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：對圖形套用 GuidelineSet
本範例說明如何將 <xref:System.Windows.Media.GuidelineSet> 套用到 <xref:System.Windows.Media.DrawingGroup>。  
  
 <xref:System.Windows.Media.DrawingGroup> 類別是唯一有 <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> 屬性的一個 <xref:System.Windows.Media.Drawing>。  若要將 <xref:System.Windows.Media.GuidelineSet> 套用到另一種 <xref:System.Windows.Media.Drawing>，請將它加入到 <xref:System.Windows.Media.DrawingGroup>，然後再將 <xref:System.Windows.Media.GuidelineSet> 套用到您的 <xref:System.Windows.Media.DrawingGroup>。  
  
## 範例  
 下列範例會建立兩個幾乎相同的 <xref:System.Windows.Media.DrawingGroup> 物件，唯一的差別在於第二個 <xref:System.Windows.Media.DrawingGroup> 有 <xref:System.Windows.Media.GuidelineSet>，而第一個沒有。  
  
 下圖顯示的是範例的輸出。  由於兩個 <xref:System.Windows.Media.DrawingGroup> 物件所呈現的差異極小，因此將繪圖的一部分放大顯示。  
  
 ![具有與不具 GuidelineSet 的 DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm\_drawinggroup\_guidelineset")  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupGuidelineSetExample.cs#graphicsmmdrawinggroupguidelinesetexamplewholepage)]
 [!code-xml[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupGuidelineSetExample.xaml#graphicsmmdrawinggroupguidelinesetexamplewholepage)]  
  
## 請參閱  
 <xref:System.Windows.Media.DrawingGroup>   
 <xref:System.Windows.Media.GuidelineSet>   
 [繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)