---
title: HOW TO：建立 BorderThickness 值的動畫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF], animating changes to
- animation [WPF], changes to border thickness
ms.assetid: fd021978-f74b-4e7b-a7f7-3987dcad9e0f
ms.openlocfilehash: 4f38895f58e1a41a8a66b31a116e94f5b02492f7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368934"
---
# <a name="how-to-animate-a-borderthickness-value"></a>HOW TO：建立 BorderThickness 值的動畫
此範例示範如何建立變更框線粗細的動畫使用<xref:System.Windows.Media.Animation.ThicknessAnimation>類別。  
  
## <a name="example"></a>範例  
 下列範例會建立框線粗細的動畫使用<xref:System.Windows.Media.Animation.ThicknessAnimation>。 此範例會使用<xref:System.Windows.Controls.Border.BorderThickness%2A>屬性<xref:System.Windows.Controls.Border>。  
  
 [!code-csharp[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/ThicknessAnimationExample.cs#thicknessanimationwholepage)]
 [!code-vb[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/ThicknessAnimationExample.vb#thicknessanimationwholepage)]  
  
 如需完整的範例，請參閱[動畫範例圖庫](https://go.microsoft.com/fwlink/?LinkID=159969)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Media.Animation.ThicknessAnimation>
- <xref:System.Windows.Controls.Border.BorderThickness%2A>
- <xref:System.Windows.Controls.Border>
- [動畫概觀](../graphics-multimedia/animation-overview.md)
- [動畫和計時 how to 主題](../graphics-multimedia/animation-and-timing-how-to-topics.md)
- [使用主要畫面格建立框線粗細的動畫](../graphics-multimedia/how-to-animate-the-thickness-of-a-border-by-using-key-frames.md)
