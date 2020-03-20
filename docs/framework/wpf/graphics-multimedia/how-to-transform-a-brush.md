---
title: 操作說明：轉換筆刷
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], rotating contents
- brushes [WPF], Transform property
- rotating contents of brushes [WPF]
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
ms.openlocfilehash: b4484e2fc1ae3e969b02b1d8f3ae4ab2a035558e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187330"
---
# <a name="how-to-transform-a-brush"></a>操作說明：轉換筆刷
此示例演示如何使用物件的兩個<xref:System.Windows.Media.Brush>轉換屬性：<xref:System.Windows.Media.Brush.RelativeTransform%2A>和<xref:System.Windows.Media.Brush.Transform%2A>轉換來轉換物件。  
  
 以下示例使用<xref:System.Windows.Media.RotateTransform>將 內容<xref:System.Windows.Media.ImageBrush>旋轉 45 度。  
  
 下圖顯示了<xref:System.Windows.Media.ImageBrush>無<xref:System.Windows.Media.RotateTransform>的 ，其中<xref:System.Windows.Media.RotateTransform>應用於<xref:System.Windows.Media.Brush.RelativeTransform%2A>屬性，並<xref:System.Windows.Media.RotateTransform>應用於 屬性。 <xref:System.Windows.Media.Brush.Transform%2A>  
  
 ![筆刷的 RelativeTransform 和 Transform 設定](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
## <a name="example"></a>範例  
 第一個示例將<xref:System.Windows.Media.RotateTransform>應用於<xref:System.Windows.Media.Brush.RelativeTransform%2A>的屬性<xref:System.Windows.Media.ImageBrush>。 物件的 和<xref:System.Windows.Media.RotateTransform.CenterX%2A><xref:System.Windows.Media.RotateTransform.CenterY%2A>屬性都設置為 0.5，這是此內容的中心點的相對座標。 <xref:System.Windows.Media.RotateTransform> 因此，<xref:System.Windows.Media.ImageBrush>內容圍繞其中心旋轉。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 第二個<xref:System.Windows.Media.RotateTransform><xref:System.Windows.Media.ImageBrush>示例還應用於但是，此示例使用 屬性<xref:System.Windows.Media.Brush.Transform%2A>而不是 屬性<xref:System.Windows.Media.Brush.RelativeTransform%2A>。  
  
 要圍繞其中心旋轉畫筆，該示例將<xref:System.Windows.Media.RotateTransform.CenterX%2A><xref:System.Windows.Media.RotateTransform.CenterY%2A><xref:System.Windows.Media.RotateTransform>物件的 和 屬性設置為絕對座標。 由於筆刷會繪製大小為 175 x 90 像素的矩形，矩形的中心點將會是 (87.5, 45)。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 有關<xref:System.Windows.Media.Brush.RelativeTransform%2A>和<xref:System.Windows.Media.Brush.Transform%2A>屬性工作方式的說明，請參閱[筆刷轉換概述](brush-transformation-overview.md)。  
  
 如需完整的範例，請參閱[筆刷範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)。 如需筆刷的詳細資訊，請參閱[使用純色和漸層繪製的概觀](painting-with-solid-colors-and-gradients-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- [筆刷轉換概觀](brush-transformation-overview.md)
- [使用純色和漸層繪製的概觀](painting-with-solid-colors-and-gradients-overview.md)
- [轉換概觀](transforms-overview.md)
