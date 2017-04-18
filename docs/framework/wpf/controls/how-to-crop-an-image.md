---
title: "如何：裁剪影像 | Microsoft Docs"
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
  - "類別, CroppedBitmap"
  - "CroppedBitmap 類別"
  - "裁剪影像"
  - "影像, 裁剪"
ms.assetid: c6bba109-c6e7-4cf8-bfe6-9cf8d01bb4fc
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：裁剪影像
本範例顯示如何使用 <xref:System.Windows.Media.Imaging.CroppedBitmap> 裁剪影像。  
  
 <xref:System.Windows.Media.Imaging.CroppedBitmap> 主要用於編碼影像的裁剪版本，以儲存到檔案中。  若要針對顯示目的裁剪影像，請參閱 [Create a Clip Region](http://msdn.microsoft.com/zh-tw/56e4bed6-78d7-4292-b917-d72d0b3e4376)主題。  
  
## 範例  
 下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 會定義以下範例內所使用的資源。  
  
 [!code-xml[imageelementexample#CroppedXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml1)]  
  
 下列範例使用 <xref:System.Windows.Media.Imaging.CroppedBitmap> 做為來源以建立影像。  
  
 [!code-xml[imageelementexample#CroppedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml2)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp1)]
 [!code-vb[imageelementexample#CroppedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp1)]  
  
 <xref:System.Windows.Media.Imaging.CroppedBitmap> 也可以用來做為另一個 <xref:System.Windows.Media.Imaging.CroppedBitmap> 的來源，鏈結裁剪作業。  請注意，<xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A> 使用的值是與來源裁剪點陣圖相關聯的，而非初始影像。  
  
 [!code-xml[imageelementexample#CroppedXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml3)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp2)]
 [!code-vb[imageelementexample#CroppedCSharp2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp2)]  
  
## 請參閱  
 [Create a Clip Region](http://msdn.microsoft.com/zh-tw/56e4bed6-78d7-4292-b917-d72d0b3e4376)