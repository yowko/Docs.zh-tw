---
title: "操作說明：對 Visual 中的幾何進行點擊測試"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects comprising Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], visual objects comprising
ms.assetid: 8bf2643f-d7f9-4cb4-9ea6-5b893c23200d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ab125fe4031b5408eb202f21ce0fdf4314781f1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hit-test-geometry-in-a-visual"></a>操作說明：對 Visual 中的幾何進行點擊測試
這個範例示範如何在所組成的一或多個視覺物件上執行點擊的測試<xref:System.Windows.Media.Geometry>物件。  
  
## <a name="example"></a>範例  
 下列範例示範如何擷取<xref:System.Windows.Media.DrawingGroup>從使用的 visual 物件<xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>方法。 點擊的測試不會再對呈現內容的每個繪圖<xref:System.Windows.Media.DrawingGroup>來判斷點擊的幾何。  
  
> [!NOTE]
>  在大部分情況下，您會使用<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>方法，以判斷是否點相交的任何視覺效果呈現內容。  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 <xref:System.Windows.Media.Geometry.FillContains%2A>方法是多載的方法，可讓您藉由將指定進行點擊測試<xref:System.Windows.Point>或<xref:System.Windows.Media.Geometry>。 如果幾何是經過繪製，筆觸可延伸至填滿範圍外。 在此情況下，您可能想要呼叫<xref:System.Windows.Media.Geometry.StrokeContains%2A>除了<xref:System.Windows.Media.Geometry.FillContains%2A>。  
  
 您也可以提供<xref:System.Windows.Media.ToleranceType>用於目的貝茲扁平化。  
  
> [!NOTE]
>  這個範例不會將任何可能套用至幾何的轉換或裁剪列入考慮。 此外，這個範例無法搭配樣式化控制項運作，因為它不具備任何直接與其相關聯的圖案。  
  
## <a name="see-also"></a>另請參閱  
 [視覺分層中的點擊測試](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [使用幾何做為參數進行點擊測試](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-using-geometry-as-a-parameter.md)
