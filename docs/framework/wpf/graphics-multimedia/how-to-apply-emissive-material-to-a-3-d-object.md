---
title: "如何：將射出材質套用至立體物件 | Microsoft Docs"
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
  - "立體物件, 套用 EmissiveMaterial"
  - "EmissiveMaterial, 套用至立體物件"
ms.assetid: fd442cc2-5adc-487a-ba70-e45ed54bb3b4
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：將射出材質套用至立體物件
下列範例說明如何使用 <xref:System.Windows.Media.Media3D.EmissiveMaterial> 將色彩新增至現有的「材質」，成為 EmissiveMaterial 的筆刷色彩。  下列程式碼顯示套用了 <xref:System.Windows.Media.Media3D.DiffuseMaterial> 和 <xref:System.Windows.Media.Media3D.EmissiveMaterial> 的組合，以便在 DiffuseMaterial 的外觀中加入藍色。  
  
 [!code-xml[3DGallery_snip#EmmisiveMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emmisivematerialanimationexampleinline1)]  
  
 在程序性程式碼中：  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexampleinline1)]  
  
## 範例  
 下列程式碼會以 XAML 顯示完整範例。  
  
 [!code-xml[3DGallery_snip#EmissiveMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/EmissiveMaterialExample.xaml#emissivematerialexamplewholepage)]  
  
## 範例  
 以下為程序性程式碼的完整範例。  
  
 [!code-csharp[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/EmissiveMaterialExample.cs#emissivematerialcodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#EmissiveMaterialCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/emissivematerialexample.vb#emissivematerialcodeexamplewholepage)]  
  
## 請參閱  
 [建立立體場景](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)   
 [立體圖形概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)   
 [在立體場景中建立材質屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)   
 [對立體物件的前後套用材質](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-material-to-the-front-and-back-of-a-3-d-object.md)