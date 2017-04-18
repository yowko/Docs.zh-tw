---
title: "如何：在立體場景中建立材質屬性的動畫 | Microsoft Docs"
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
  - "立體場景, 建立材質屬性動畫"
  - "動畫, 立體場景中的材質屬性"
  - "材質屬性, 在立體場景中建立動畫"
ms.assetid: 229fd6eb-7401-4992-b0c9-8b28de230c0f
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：在立體場景中建立材質屬性的動畫
這個範例顯示如何以[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]模型套用之 <xref:System.Windows.Media.Media3D.Material> 的 <xref:System.Windows.Media.Brush.Opacity%2A> 屬性建立動畫。  
  
 下列程式碼範例會定義 <xref:System.Windows.Media.LinearGradientBrush> 做為 <xref:System.Windows.Media.Media3D.Material> 套用至 3D 物件。  
  
 [!code-xml[Animation3DGallery_snip#AnimateMaterialExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline1)]  
  
 下列程式碼範例會使用這個 <xref:System.Windows.Media.LinearGradientBrush> 的 <xref:System.Windows.Media.Brush.Opacity%2A> 屬性建立動畫。  
  
 [!code-xml[Animation3DGallery_snip#AnimateMaterialExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline2)]  
  
## 範例  
 下列程式碼顯示整個範例。  
  
 [!code-xml[Animation3DGallery_snip#AnimateMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexamplewholepage)]  
  
## 請參閱  
 [建立立體場景](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)   
 [立體圖形概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)