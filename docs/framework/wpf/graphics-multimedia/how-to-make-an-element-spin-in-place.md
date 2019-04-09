---
title: HOW TO：使元素就地旋轉
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: aca9bd577f2882e31e8d49abe5eeb5ade86f95f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110660"
---
# <a name="how-to-make-an-element-spin-in-place"></a>HOW TO：使元素就地旋轉
此範例示範如何讓組織使用的項目<xref:System.Windows.Media.RotateTransform>和<xref:System.Windows.Media.Animation.DoubleAnimation>。  
  
 下列範例會套用<xref:System.Windows.Media.RotateTransform>至<xref:System.Windows.UIElement.RenderTransform%2A>項目的屬性。 此範例會使用<xref:System.Windows.Media.Animation.DoubleAnimation>來建立動畫<xref:System.Windows.Media.RotateTransform.Angle%2A>的<xref:System.Windows.Media.RotateTransform>。 此範例會設定讓項目就地微調， <xref:System.Windows.UIElement.RenderTransformOrigin%2A> （0.5，0.5） 的點項目的屬性。  
  
## <a name="example"></a>範例  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 如需完整的範例中，包含更多轉換範例，請參閱[2d 轉換範例](https://go.microsoft.com/fwlink/?LinkID=158252)。  
  
## <a name="see-also"></a>另請參閱

- [動畫概觀](animation-overview.md)
- [轉換概觀](transforms-overview.md)
