---
title: "如何：建立立體場景 | Microsoft Docs"
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
  - "立體場景"
  - "建立, 立體場景"
  - "場景, 3D"
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：建立立體場景
這個範例顯示如何建立看起來像是旋轉過之紙張的 3\-D 物件。  <xref:System.Windows.Controls.Viewport3D> 與下列元件用於建立這個範例的 3\-D 場景：  
  
-   使用 <xref:System.Windows.Media.Media3D.PerspectiveCamera> 建立鏡頭。  鏡頭會指定哪個部分的 3\-D 場景可以看得見。  
  
-   使用 <xref:System.Windows.Media.Media3D.GeometryModel3D> 的 <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> 屬性，建立網狀結構來指定 3\-D 物件的圖案 \(紙張\)。  
  
-   使用 <xref:System.Windows.Media.Media3D.GeometryModel3D> 的 <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> 屬性，指定物件表面上顯示的材質 \(在這個範例中是線形漸層\)。  
  
-   使用 <xref:System.Windows.Media.Media3D.DirectionalLight> 建立光源來照亮物件。  
  
## 範例  
 下列程式碼顯示如何在 XAML 中建立 3\-D 場景。  
  
 [!code-xml[3DGallery_snip#Basic3DShapeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## 範例  
 下列程式碼顯示如何在程序性程式碼中建立相同的 3\-D 場景。  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## 請參閱  
 [立體圖形概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)