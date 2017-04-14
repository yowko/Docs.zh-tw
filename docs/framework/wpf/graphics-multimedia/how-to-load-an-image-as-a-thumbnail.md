---
title: "如何：將影像當做縮圖載入 | Microsoft Docs"
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
  - "影像, 載入為縮圖"
  - "將影像載入為縮圖"
  - "縮圖, 將影像載入為"
ms.assetid: 02e055a0-54df-499a-b8b6-ab6ff7535cff
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：將影像當做縮圖載入
下列範例顯示如何將 <xref:System.Windows.Controls.Image> 當做縮圖載入，以節省應用程式記憶體。  
  
## 範例  
 下列範例會在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中設定 <xref:System.Windows.Media.Imaging.BitmapImage> 的 <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> 屬性，以減少載入影像所需的記憶體。  
  
 [!code-xml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## 範例  
 下列範例會在程式碼中設定 <xref:System.Windows.Media.Imaging.BitmapImage> 的 <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> 屬性，以減少載入影像所需的記憶體。  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## 請參閱  
 [影像處理概觀](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)