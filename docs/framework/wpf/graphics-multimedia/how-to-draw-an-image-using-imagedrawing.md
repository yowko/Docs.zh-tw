---
title: "如何：使用 ImageDrawing 繪製影像 | Microsoft Docs"
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
  - "類別, ImageDrawing"
  - "繪製, 影像"
  - "圖形, 描繪影像"
  - "ImageDrawing 類別"
  - "影像, 繪製"
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：使用 ImageDrawing 繪製影像
本範例顯示如何使用 <xref:System.Windows.Media.ImageDrawing> 繪製影像。  <xref:System.Windows.Media.ImageDrawing> 可以讓您使用 <xref:System.Windows.Media.DrawingBrush>、<xref:System.Windows.Media.DrawingImage> 或 <xref:System.Windows.Media.Visual> 來顯示 <xref:System.Windows.Media.ImageSource>。  若要繪製影像，您要建立 <xref:System.Windows.Media.ImageDrawing> 並設定其 <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=fullName> 和 <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=fullName> 屬性。  <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=fullName> 屬性指定要繪製的影像，而 <xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=fullName> 屬性則指定每個影像的位置和大小。  
  
## 範例  
 下列範例會使用 4 個 <xref:System.Windows.Media.ImageDrawing> 物件建立複合繪圖。  本範例會產生下列影像：  
  
 ![數個 DrawingImage 物件](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagedrawingexample.png "graphicsmm\_ImageDrawingExample")  
4 個 ImageDrawing 物件  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xml[DrawingMiscSnippets_snip#ImageDrawingExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 如需不使用 <xref:System.Windows.Media.ImageDrawing> 來顯示影像的簡單範例，請參閱 [使用 Image 項目](../../../../docs/framework/wpf/controls/how-to-use-the-image-element.md)。  
  
## 請參閱  
 <xref:System.Windows.Freezable.Freeze%2A>   
 <xref:System.Windows.Controls.Image>   
 [繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)   
 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)   
 [PresentationOptions:Freeze 屬性](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)