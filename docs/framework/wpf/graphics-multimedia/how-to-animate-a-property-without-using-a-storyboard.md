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
ms.openlocfilehash: 71711c0392576930e97986078ec5926ff6ca9813
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963015"
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a>作法：不使用分鏡腳本而建立屬性的動畫
這個範例示範將動畫套用至屬性的一種方式, 而不<xref:System.Windows.Media.Animation.Storyboard>使用。  
  
> [!NOTE]
> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中無法使用此功能。 如需以動畫顯示 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中屬性的詳細資訊，請參閱[使用分鏡腳本建立屬性的動畫](how-to-animate-a-property-by-using-a-storyboard.md)。  
  
 若要將本機動畫套用至屬性, 請使用<xref:System.Windows.UIElement.BeginAnimation%2A>方法。 這個方法會採用兩個參數<xref:System.Windows.DependencyProperty> :, 指定要建立動畫的屬性, 以及要套用至該屬性的動畫。  
  
## <a name="example"></a>範例  
 下列範例示範如何以動畫顯示的寬度和背景色彩<xref:System.Windows.Controls.Button>。  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 命名空間中的各種動畫類別<xref:System.Windows.Media.Animation>都存在, 以動畫顯示不同類型的屬性。 如需將屬性顯示為動畫的詳細資訊，請參閱[動畫概觀](animation-overview.md)。 如需相依性屬性 (這些範例所示的內容類型) 和其功能的詳細資訊，請參閱[相依性屬性概觀](../advanced/dependency-properties-overview.md)。  
  
 還有其他方式可建立動畫, 而<xref:System.Windows.Media.Animation.Storyboard>不使用物件。如需詳細資訊, 請參閱[屬性動畫技術總覽](property-animation-techniques-overview.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Animation.Storyboard>
- [屬性動畫技術概觀](property-animation-techniques-overview.md)
- [動畫概觀](animation-overview.md)
