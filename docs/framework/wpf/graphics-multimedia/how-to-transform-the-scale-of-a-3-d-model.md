---
title: "如何：轉換立體模型的比例 | Microsoft Docs"
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
  - "立體物件, 縮放比例"
  - "縮放比例, 立體物件"
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
caps.latest.revision: 3
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 3
---
# 如何：轉換立體模型的比例
這個範例顯示如何縮放 3\-D 物件。  若要縮放 3\-D 物件，請使用 <xref:System.Windows.Media.Media3D.ScaleTransform3D>。  <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>、<xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> 及 <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> 屬性會以您指定的因數調整項目的大小。  例如，如果 <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> 值為 1.5 則會將物件自動縮放成原始寬度的 150 %。  如果 <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> 值為 0.5 則會將物件壓縮為原始高度的 50 %。  下列程式碼顯示對 <xref:System.Windows.Media.Media3D.GeometryModel3D> 進行的 <xref:System.Windows.Media.Media3D.ScaleTransform3D> 轉換。  
  
 [!code-xml[3DGallery_snip#ScaleTransform3DExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## 範例  
 下列程式碼顯示整個範例。  
  
 [!code-xml[3DGallery_snip#ScaleTransform3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## 請參閱  
 [建立立體轉譯動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-3-d-translations.md)   
 [建立立體場景](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)   
 [立體圖形概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)