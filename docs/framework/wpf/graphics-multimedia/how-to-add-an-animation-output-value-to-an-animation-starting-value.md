---
title: HOW TO：將動畫輸出值加到動畫啟動值
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
ms.openlocfilehash: 945675d03a280e2394fdb0eab27c0978dc7cc320
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102605"
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a>HOW TO：將動畫輸出值加到動畫啟動值
此範例示範如何將動畫輸出值加入至動畫的起始值。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A>屬性會指定是否要加入至動畫的屬性的起始值 （基底值） 的動畫的輸出值。 您可以使用<xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A>具有最基本的動畫和大部分的主要畫面格動畫屬性。 如需詳細資訊，請參閱 <<c0> [ 動畫概觀](animation-overview.md)並[主要畫面格動畫概觀](key-frame-animations-overview.md)。  
  
 下列範例示範使用的效果<xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType>具有屬性<xref:System.Windows.Media.Animation.DoubleAnimation>並使用<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType>屬性與<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>。  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a>另請參閱

- [在重複循環期間累加動畫值](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [動畫概觀](animation-overview.md)
- [主要畫面格動畫概觀](key-frame-animations-overview.md)
- [動畫和計時 how to 主題](animation-and-timing-how-to-topics.md)
