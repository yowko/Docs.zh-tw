---
title: HOW TO：套用多重轉換至物件
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
ms.openlocfilehash: 19fc87f04ca111f1fd0b6d7a4784fd96b464eb22
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363646"
---
# <a name="how-to-apply-multiple-transforms-to-an-object"></a>HOW TO：套用多重轉換至物件
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
