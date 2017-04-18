---
title: "如何：轉譯項目 | Microsoft Docs"
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
  - "類別, TranslateTransform"
  - "圖形, 轉譯"
  - "TranslateTransform 類別"
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：轉譯項目
本範例說明如何使用 <xref:System.Windows.Media.TranslateTransform> 來轉譯 \(移動\) 項目。  
  
 在不支援絕對位置的面板內移動項目時，<xref:System.Windows.Media.TranslateTransform> 類別特別有幫助。  例如，藉由將 <xref:System.Windows.Media.TranslateTransform> 套用至項目的 <xref:System.Windows.UIElement.RenderTransform%2A> 屬性，您就可以在 <xref:System.Windows.Controls.StackPanel> 或 <xref:System.Windows.Controls.DockPanel> 內移動項目。  
  
 使用 <xref:System.Windows.Media.TranslateTransform> 的 <xref:System.Windows.Media.TranslateTransform.X%2A> 屬性，指定項目沿著 X 軸移動的量 \(以[像素](GTMT)為單位\)。  使用 <xref:System.Windows.Media.TranslateTransform.Y%2A> 屬性，來指定項目沿著 Y 軸移動的量 \(以像素為單位\)。  最後，將 <xref:System.Windows.Media.TranslateTransform> 套用至項目的 <xref:System.Windows.UIElement.RenderTransform%2A> 屬性。  
  
 下列範例使用 <xref:System.Windows.Media.TranslateTransform> 將項目向右移動 50 個[像素](GTMT)並向下移動 50 個像素。  
  
## 範例  
 [!code-xml[transformsSample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 如需完整範例，請參閱 [2D 轉換範例](http://go.microsoft.com/fwlink/?LinkID=158252) \(英文\)。  
  
## 請參閱  
 [轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)