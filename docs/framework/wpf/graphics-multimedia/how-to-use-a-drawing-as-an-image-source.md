---
title: "如何：將圖形當做影像來源使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "繪圖, 做為影像來源"
  - "圖形, 繪圖, 做為影像來源"
  - "影像來源, 繪圖"
ms.assetid: dcf71c7b-9e86-4b8e-8e39-0d0ce0389ef4
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：將圖形當做影像來源使用
這個範例顯示如何使用 <xref:System.Windows.Media.Drawing> 做為 <xref:System.Windows.Controls.Image> 控制項的 <xref:System.Windows.Controls.Image.Source%2A>。  若要以 <xref:System.Windows.Controls.Image> 控制項顯示 <xref:System.Windows.Media.Drawing>，請使用 <xref:System.Windows.Media.DrawingImage> 做為 <xref:System.Windows.Controls.Image> 控制項的 <xref:System.Windows.Controls.Image.Source%2A>，並將 <xref:System.Windows.Media.DrawingImage> 物件的 <xref:System.Windows.Media.DrawingImage.Drawing%2A?displayProperty=fullName> 屬性設定為您要顯示的繪圖。  
  
## 範例  
 下列範例使用 <xref:System.Windows.Media.DrawingImage> 和 <xref:System.Windows.Controls.Image> 控制項來顯示 <xref:System.Windows.Media.GeometryDrawing>。  這個範例會產生下列輸出：  
  
 ![兩個橢圓形的 GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.png "graphicsmm\_geodraw")  
DrawingImage  
  
 [!code-csharp[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingImageExample.cs#drawingimageexamplewholepage)]
 [!code-xml[DrawingMiscSnippets_snip#DrawingImageExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingImageExample.xaml#drawingimageexamplewholepage)]  
  
## 請參閱  
 <xref:System.Windows.Freezable.Freeze%2A>   
 [使用 ImageDrawing 繪製影像](../../../../docs/framework/wpf/graphics-multimedia/how-to-draw-an-image-using-imagedrawing.md)   
 [繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)   
 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [PresentationOptions:Freeze 屬性](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)