---
title: "如何：對立體物件的前後套用材質 | Microsoft Docs"
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
  - "立體物件, 套用 Material 類別"
  - "類別, Material"
  - "Material 類別, 套用至立體物件的兩邊"
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：對立體物件的前後套用材質
下列範例顯示如何將 <xref:System.Windows.Media.Media3D.Material> 套用至立體物件的前後，並建立物件的動畫以顯示物件的兩邊。  <xref:System.Windows.Media.Media3D.GeometryModel3D> 的 <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> 屬性是用來將紅色 <xref:System.Windows.Media.Brush> 套用至物件的前面，而 <xref:System.Windows.Media.Media3D.GeometryModel3D> 的 <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> 屬性是用來將藍色 <xref:System.Windows.Media.Brush> 套用至物件的後面。  下列程式碼顯示如何將材質套用至物件：  
  
 [!code-xml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## 範例  
 下列程式碼顯示整個範例。  
  
 [!code-xml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## 請參閱  
 [建立立體場景](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)   
 [立體圖形概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)   
 [在立體場景中建立材質屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)   
 [將射出材質套用至立體物件](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-emissive-material-to-a-3-d-object.md)