---
title: 操作說明：套用多重轉換至物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- grouping Transform objects [WPF]
- Transform objects [WPF], grouping
- graphics [WPF], grouping Transform objects
- TransformGroup [WPF]
ms.assetid: 98cd1921-12bc-4bf5-8193-529228fb7402
ms.openlocfilehash: 544d0a26f24e5ad4ed7e2e3cfa25f8e15d1be446
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452827"
---
# <a name="how-to-apply-multiple-transforms-to-an-object"></a>操作說明：套用多重轉換至物件
這個範例示範如何使用 <xref:System.Windows.Media.TransformGroup>，將兩個或多個 <xref:System.Windows.Media.Transform> 物件組成單一複合 <xref:System.Windows.Media.Transform>。  
  
## <a name="example"></a>範例  
 下列範例會使用 <xref:System.Windows.Media.TransformGroup>，將 <xref:System.Windows.Media.ScaleTransform> 和 <xref:System.Windows.Media.RotateTransform> 套用至 <xref:System.Windows.Controls.Button>。  
  
 [!code-xaml[Transforms_snip#MultipleTransformExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MultipleTransformExample.xaml#multipletransformexamplewholepage)]  
  
 [!code-csharp[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/MultipleTransformsExample.cs#multipletransformscodeexamplewholepage)]
 [!code-vb[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/MultipleTransformsExample.vb#multipletransformscodeexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Media.TransformGroup>
- [轉換概觀](transforms-overview.md)
- [2D 轉換範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)
