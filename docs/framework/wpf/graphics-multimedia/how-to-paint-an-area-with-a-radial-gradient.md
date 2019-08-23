---
title: 作法：使用放射狀漸層繪製區域
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
ms.openlocfilehash: 5762ef1a1526ba6f004917c8a947e35ce731c86d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916105"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a>HOW TO：使用放射狀漸層繪製區域
這個範例示範如何使用<xref:System.Windows.Media.RadialGradientBrush>類別, 以放射狀漸層繪製區域。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.RadialGradientBrush>來繪製具有放射漸層的矩形, 而星形漸層會從黃色轉換成紅色到藍色, 以綠色顯示。  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 下圖顯示上述範例中的漸層。 漸層的停駐點已反白顯示。  
  
 ![放射狀漸層中的漸層停駐點](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")  
  
> [!NOTE]
> 本主題中的範例會使用預設的座標系統來設定控制點。 預設座標系統是相對於周框方塊:0 表示週框方塊的 0%，1 表示週框方塊的 100%。 您可以藉由將<xref:System.Windows.Media.GradientBrush.MappingMode%2A>屬性設定為值<xref:System.Windows.Media.BrushMappingMode.Absolute>來變更此座標系統。 絕對座標系統不會相對於週框方塊。 值會直接在本機空間中解譯。  
  
 如需<xref:System.Windows.Media.RadialGradientBrush>其他範例, 請參閱[筆刷範例](https://go.microsoft.com/fwlink/?LinkID=159973)。 如需漸層和其他類型之筆刷的詳細資訊, 請參閱[使用純色和漸層繪製的色彩](painting-with-solid-colors-and-gradients-overview.md)。
