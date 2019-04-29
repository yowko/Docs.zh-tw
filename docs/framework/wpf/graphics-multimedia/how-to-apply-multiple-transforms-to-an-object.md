---
title: HOW TO：對物件套用多個轉換
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
ms.openlocfilehash: 26dcd4a64fc7aa2c3cb9cc599ceaef292efb1b6a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698924"
---
# <a name="how-to-apply-multiple-transforms-to-an-object"></a>HOW TO：對物件套用多個轉換
此範例示範如何使用<xref:System.Windows.Media.TransformGroup>兩個或多個群組<xref:System.Windows.Media.Transform>組成為單一複合物件<xref:System.Windows.Media.Transform>。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.TransformGroup>套用<xref:System.Windows.Media.ScaleTransform>並<xref:System.Windows.Media.RotateTransform>至<xref:System.Windows.Controls.Button>。  
  
 [!code-xaml[Transforms_snip#MultipleTransformExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MultipleTransformExample.xaml#multipletransformexamplewholepage)]  
  
 [!code-csharp[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/MultipleTransformsExample.cs#multipletransformscodeexamplewholepage)]
 [!code-vb[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/MultipleTransformsExample.vb#multipletransformscodeexamplewholepage)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Media.TransformGroup>
- [轉換概觀](transforms-overview.md)
- [2D 轉換範例](https://go.microsoft.com/fwlink/?LinkID=158252)
