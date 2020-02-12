---
title: 如何：建立 BorderThickness 值的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF], animating changes to
- animation [WPF], changes to border thickness
ms.assetid: fd021978-f74b-4e7b-a7f7-3987dcad9e0f
ms.openlocfilehash: 4533ce6f2a1fe7243267ee8d638e2ad0a4f9cf3a
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124659"
---
# <a name="how-to-animate-a-borderthickness-value"></a>如何：建立 BorderThickness 值的動畫
這個範例示範如何使用 <xref:System.Windows.Media.Animation.ThicknessAnimation> 類別，以動畫顯示框線粗細的變更。  
  
## <a name="example"></a>範例  
 下列範例會使用 <xref:System.Windows.Media.Animation.ThicknessAnimation>以動畫呈現框線的粗細。 此範例使用 <xref:System.Windows.Controls.Border>的 <xref:System.Windows.Controls.Border.BorderThickness%2A> 屬性。  
  
 [!code-csharp[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/ThicknessAnimationExample.cs#thicknessanimationwholepage)]
 [!code-vb[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/ThicknessAnimationExample.vb#thicknessanimationwholepage)]  
  
 如需完整範例，請參閱[動畫範例庫](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Animation.ThicknessAnimation>
- <xref:System.Windows.Controls.Border.BorderThickness%2A>
- <xref:System.Windows.Controls.Border>
- [動畫概觀](../graphics-multimedia/animation-overview.md)
- [動畫和計時 how to 主題](../graphics-multimedia/animation-and-timing-how-to-topics.md)
- [使用主要畫面格建立框線粗細的動畫](../graphics-multimedia/how-to-animate-the-thickness-of-a-border-by-using-key-frames.md)
