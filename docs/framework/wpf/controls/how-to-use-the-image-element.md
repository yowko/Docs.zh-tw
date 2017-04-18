---
title: "如何：使用 Image 項目 | Microsoft Docs"
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
  - "BitmapImage 類別"
  - "類別, BitmapImage"
  - "控制項, Image"
  - "Image 控制項"
  - "呈現影像"
ms.assetid: 5b92e74b-1b56-4756-ac64-d5e9e08d9854
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 如何：使用 Image 項目
本範例示範如何使用 <xref:System.Windows.Controls.Image> 項目，在應用程式中包含影像。  
  
## 範例  
 下列範例示範如何呈現寬度為 200 像素的影像。  這個[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 範例中使用了屬性 \(Attribute\) 語法和屬性 \(Property\) 標記語法來定義影像。  如需屬性 \(Attribute\) 語法和屬性 \(Property\) 語法的詳細資訊，請參閱[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。  <xref:System.Windows.Media.Imaging.BitmapImage> 是用來定義影像的來源資料，而且也針對屬性標記語法範例提供了明確的定義。  此外，<xref:System.Windows.Media.Imaging.BitmapImage> 的 <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> 也設定為與 <xref:System.Windows.Controls.Image> 的 <xref:System.Windows.FrameworkElement.Width%2A> 寬度相同。  這項設定的目的是為了以最少的記憶體容量來呈現影像。  
  
> [!NOTE]
>  一般來說，如果您想指定呈現影像的大小，只需要指定 <xref:System.Windows.FrameworkElement.Width%2A> 或 <xref:System.Windows.FrameworkElement.Height%2A>，但不能同時指定兩者。  如果您只指定其中一項，影像的[外觀比例](GTMT) \(Aspect Ratio\) 就會保持不變。  否則，影像可能會出現非預期的自動縮放 \(Stretch\) 或扭曲情形。  若要控制影像的自動縮放行為，請使用 <xref:System.Windows.Controls.Image.Stretch%2A> 和 <xref:System.Windows.Controls.Image.StretchDirection%2A> 屬性。  
  
> [!NOTE]
>  當您使用 <xref:System.Windows.FrameworkElement.Width%2A> 或 <xref:System.Windows.FrameworkElement.Height%2A> 指定影像的大小時，應該將 <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> 或 <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> 一併設定為相同的對應大小。  
  
 <xref:System.Windows.Controls.Image.Stretch%2A> 屬性決定了影像如何自動縮放以填滿影像項目。  如需詳細資訊，請參閱 <xref:System.Windows.Media.Stretch> 列舉。  
  
 [!code-xml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## 範例  
 下列範例顯示如何使用程式碼呈現 200 像素寬的影像。  
  
> [!NOTE]
>  <xref:System.Windows.Media.Imaging.BitmapImage> 屬性必須在 <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> 和 <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> 區塊中設定。  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## 請參閱  
 [影像處理概觀](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)