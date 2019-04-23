---
title: HOW TO：不使用分鏡腳本而建立屬性的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- non-Storyboard animation
- local animation [WPF]
- animation [WPF], non-Storyboard (local)
ms.assetid: d411db70-4df7-487d-82bc-95a7c1b2e7f8
ms.openlocfilehash: 93609cdeb4d879cbec0f90096e4fa2c131a2ec5e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091703"
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a>HOW TO：不使用分鏡腳本而建立屬性的動畫
此範例示範套用至屬性的動畫，而不使用的一種方法<xref:System.Windows.Media.Animation.Storyboard>。  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中無法使用此功能。 如需以動畫顯示 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中屬性的詳細資訊，請參閱[使用分鏡腳本建立屬性的動畫](how-to-animate-a-property-by-using-a-storyboard.md)。  
  
 若要將本機動畫套用至屬性，使用<xref:System.Windows.UIElement.BeginAnimation%2A>方法。 這個方法會採用兩個參數：<xref:System.Windows.DependencyProperty>可指定的屬性，以動畫顯示，以及要套用到該屬性的動畫。  
  
## <a name="example"></a>範例  
 下列範例示範如何以動畫顯示的寬度和背景色彩<xref:System.Windows.Controls.Button>。  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 中的動畫類別的各種<xref:System.Windows.Media.Animation>命名空間存在以動畫顯示不同類型的屬性。 如需將屬性顯示為動畫的詳細資訊，請參閱[動畫概觀](animation-overview.md)。 如需相依性屬性 (這些範例所示的內容類型) 和其功能的詳細資訊，請參閱[相依性屬性概觀](../advanced/dependency-properties-overview.md)。  
  
 還有其他方式，而不使用動畫<xref:System.Windows.Media.Animation.Storyboard>物件; 如需詳細資訊，請參閱[屬性動畫技術概觀](property-animation-techniques-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Animation.Storyboard>
- [屬性動畫技術概觀](property-animation-techniques-overview.md)
- [動畫概觀](animation-overview.md)
