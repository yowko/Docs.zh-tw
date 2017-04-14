---
title: "如何：使用放射狀漸層繪製區域 | Microsoft Docs"
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
  - "筆刷, 使用放射狀漸層繪製"
  - "繪圖, 使用放射狀漸層"
  - "放射狀漸層, 繪製方式"
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：使用放射狀漸層繪製區域
本範例示範如何使用 <xref:System.Windows.Media.RadialGradientBrush> 類別以放射狀漸層繪製區域。  
  
## 範例  
 下列範例使用 <xref:System.Windows.Media.RadialGradientBrush> 繪製具有放射狀漸層的矩形，其漸層效果是從黃色變成紅色，再變成藍色，最後變成淡黃綠色。  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 下圖顯示前述範例的漸層效果。  圖中特別標出漸層的停駐點。  
  
 ![放射狀漸層中的漸層停駐點](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk\_graphicsmm\_4gradientstops\_rg")  
  
> [!NOTE]
>  本主題中的範例會使用預設座標系統設定控制點。  預設座標系統與週框方塊有關：0 表示週框方塊的 0%，而 1 表示週框方塊的 100%。  您可以藉由將 <xref:System.Windows.Media.GradientBrush.MappingMode%2A> 屬性設為值 <xref:System.Windows.Media.BrushMappingMode>，變更這個座標系統。  絕對座標系統不會相對於週框方塊。  值會直接在本機空間中解譯。  
  
 如需其他 <xref:System.Windows.Media.RadialGradientBrush> 範例，請參閱[筆刷範例](http://go.microsoft.com/fwlink/?LinkID=159973) \(英文\)。  如需漸層和其他筆刷類型的詳細資訊，請參閱[使用純色和漸層繪製的概觀](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)。