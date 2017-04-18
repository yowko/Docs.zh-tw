---
title: "如何：在事件發生時套用轉換至項目 | Microsoft Docs"
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
  - "圖形, 當做事件回應的轉換"
  - "LayoutTransform 屬性"
  - "屬性, LayoutTransform"
  - "屬性, RenderTransform"
  - "RenderTransform 屬性"
  - "當做事件回應的轉換"
ms.assetid: 71e4327e-ca57-444c-a3cf-09fb381491a0
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：在事件發生時套用轉換至項目
本範例說明如何在發生事件時套用 <xref:System.Windows.Media.ScaleTransform>。  此處顯示的概念與您用於套用其他類型之轉換的概念相同。  如需可用轉換類型的詳細資訊，請參閱 <xref:System.Windows.Media.Transform> 類別或[轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)。  
  
 您可以使用任何一種方法將轉換套用到項目：  
  
-   如果您*不想*轉換效果版面配置，請使用該項目的 <xref:System.Windows.UIElement.RenderTransform%2A> 屬性。  
  
-   如果您想轉換效果版面配置，請使用該項目的 <xref:System.Windows.FrameworkElement.LayoutTransform%2A> 屬性。  
  
 下列範例會透過將 <xref:System.Windows.Media.ScaleTransform> 套用至按鈕的 <xref:System.Windows.UIElement.RenderTransform%2A> 類別。  當滑鼠移過按鈕上時，<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>，且 <xref:System.Windows.Media.ScaleTransform> 的 <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> 屬性會設定為 `2`，這會讓按鈕變得較大。  當滑鼠從按鈕移開，<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>，且 <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> 設定為 `1`，這會讓按鈕變回正常大小。  
  
## 範例  
 [!code-xml[ButtonTransform#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## 請參閱  
 <xref:System.Windows.Media.Transform>   
 <xref:System.Windows.Media.ScaleTransform>   
 [轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)   
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)