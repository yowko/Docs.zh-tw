---
title: "如何：套用多重轉換至物件 | Microsoft Docs"
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
  - "圖形, 群組 Transform 物件"
  - "群組 Transform 物件"
  - "Transform 物件, 群組"
  - "TransformGroup"
ms.assetid: 98cd1921-12bc-4bf5-8193-529228fb7402
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：套用多重轉換至物件
本範例說明如何使用 <xref:System.Windows.Media.TransformGroup>，將兩個或多個 <xref:System.Windows.Media.Transform> 物件群組至一個複合 <xref:System.Windows.Media.Transform> 中。  
  
## 範例  
 下列範例使用 <xref:System.Windows.Media.TransformGroup> 將 <xref:System.Windows.Media.ScaleTransform> 及 <xref:System.Windows.Media.RotateTransform> 套用至 <xref:System.Windows.Controls.Button> 中。  
  
 [!code-xml[Transforms_snip#MultipleTransformExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MultipleTransformExample.xaml#multipletransformexamplewholepage)]  
  
 [!code-csharp[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/MultipleTransformsExample.cs#multipletransformscodeexamplewholepage)]
 [!code-vb[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/MultipleTransformsExample.vb#multipletransformscodeexamplewholepage)]  
  
## 請參閱  
 <xref:System.Windows.UIElement.RenderTransform%2A>   
 <xref:System.Windows.Media.TransformGroup>   
 [轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)   
 [2D 轉換範例](http://go.microsoft.com/fwlink/?LinkID=158252)