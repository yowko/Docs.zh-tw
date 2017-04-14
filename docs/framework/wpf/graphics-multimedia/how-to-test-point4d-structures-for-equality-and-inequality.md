---
title: "如何：測試 Point4D 結構是否相等和不相等 | Microsoft Docs"
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
  - "相等, 測試 Point4D 結構"
  - "不等於, 測試 Point4D 結構"
  - "Point4D 結構, 測試是否相等"
  - "Point4D 結構, 測試是否不相等"
  - "測試, Point4D 結構是否相等"
  - "測試, Point4D 結構是否不相等"
ms.assetid: e004a67e-db7f-4af8-a31f-e6b2a44ccf34
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：測試 Point4D 結構是否相等和不相等
本範例顯示如何測試 <xref:System.Windows.Media.Media3D.Point4D> 結構是否相等和不相等。  
  
 下列程式碼說明如何使用 <xref:System.Windows.Media.Media3D.Point4D> 等號比較方法，測試 <xref:System.Windows.Media.Media3D.Point4D> 結構是否相等和不相等。  <xref:System.Windows.Media.Media3D.Point4D> 結構的相等測試，是使用多載相等 \(`==`\) 運算子來比較是否相等，再使用多載不相等 \(`!=`\) 運算子來比較是否不相等，最後使用靜態 <xref:System.Windows.Media.Media3D.Point4D.Equals%2A> 方法，檢查 <xref:System.Windows.Media.Media3D.Point3D> 結構和 <xref:System.Windows.Media.Media3D.Point4D> 結構是否相等。  
  
## 範例  
 [!code-csharp[3DGallery_procedural_snip#Point4DEqualityExample_csharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Misc3DOperationsExample.cs#point4dequalityexample_csharp)]  
  
## 請參閱  
 <xref:System.Windows.Media.Media3D.Point4D.op_Equality%2A>   
 <xref:System.Windows.Media.Media3D.Point4D.op_Inequality%2A>   
 <xref:System.Windows.Media.Media3D.Point4D.Equals%2A>