---
title: "如何：建立 FrameworkElement 大小的動畫 | Microsoft Docs"
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
  - "動畫, FrameworkElement 大小"
  - "FrameworkElement, 建立大小動畫"
ms.assetid: d4cd5a13-c20d-4a6f-a2ba-14f2c9ce4cef
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：建立 FrameworkElement 大小的動畫
若要建立 <xref:System.Windows.FrameworkElement> 大小的動畫，您可以建立其 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 屬性的動畫，或使用動畫的 <xref:System.Windows.Media.ScaleTransform>。  
  
 下列範例會使用這兩種方式建立兩個按鈕的大小動畫。  一個按鈕的大小調整是藉由建立其 <xref:System.Windows.FrameworkElement.Width%2A> 屬性的動畫，而另一個按鈕的大小調整是藉由建立 <xref:System.Windows.Media.ScaleTransform> 的動畫套用到其 <xref:System.Windows.UIElement.RenderTransform%2A> 屬性。  每個按鈕都包含一些文字。  一開始，顯示在兩個按鈕中的文字都相同，但隨著調整按鈕的大小，第二個按鈕中的文字會扭曲。  
  
## 範例  
 [!code-xml[transformanimations_snip#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/AnimatingSizeExample.xaml#1)]  
  
 轉換項目時，整個項目和其內容都會轉換。  當您直接更改項目的大小時，如第一個按鈕的情況，項目的內容不會調整大小，除非它們的大小和位置是由其父項目大小所決定。  
  
 藉由套用動畫轉換至其 <xref:System.Windows.UIElement.RenderTransform%2A> 屬性來建立項目大小的動畫，比直接建立其 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 動畫的效能來得佳，因為 <xref:System.Windows.UIElement.RenderTransform%2A> 屬性不會觸發配置傳遞。  
  
 如需動畫屬性的詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  如需轉換的詳細資訊，請參閱[轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)。