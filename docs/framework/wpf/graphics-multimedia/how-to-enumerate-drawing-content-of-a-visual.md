---
title: "如何：列舉 Visual 的繪圖內容 | Microsoft Docs"
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
  - "列舉視覺項目的內容 [WPF]"
  - "擷取視覺項目的 DrawingGroup 值 [WPF]"
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
caps.latest.revision: 3
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 3
---
# 如何：列舉 Visual 的繪圖內容
<xref:System.Windows.Media.Drawing> 物件提供列舉 <xref:System.Windows.Media.Visual> 內容的物件模型。  
  
## 範例  
 下列範例使用 <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> 方法，擷取 <xref:System.Windows.Media.Visual> 的 <xref:System.Windows.Media.DrawingGroup> 值並加以列舉。  
  
> [!NOTE]
>  當您列舉視覺內容時，您會擷取 <xref:System.Windows.Media.Drawing> 物件，而不是擷取轉譯資料的基礎表示做為向量圖形指示清單。  如需詳細資訊，請參閱 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## 請參閱  
 <xref:System.Windows.Media.Drawing>   
 <xref:System.Windows.Media.DrawingGroup>   
 <xref:System.Windows.Media.VisualTreeHelper>   
 [繪圖物件概觀](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)   
 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)