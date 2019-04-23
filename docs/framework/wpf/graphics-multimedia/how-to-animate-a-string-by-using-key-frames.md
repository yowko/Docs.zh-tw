---
title: HOW TO：使用主要畫面格建立字串的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: 4a37408ad90fda12a95e66c1b44018967b376837
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204168"
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a>HOW TO：使用主要畫面格建立字串的動畫
此範例示範如何以動畫顯示的字串，在此範例中是<xref:System.Windows.Controls.ContentControl.Content%2A>屬性<xref:System.Windows.Controls.Button>控制項，使用主要畫面格。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>類別以動畫顯示<xref:System.Windows.Controls.ContentControl.Content%2A>屬性<xref:System.Windows.Controls.Button>。  
  
 在此範例中的所有主要畫面格使用的執行個體<xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>類別，因為會使用主要畫面格建立字串動畫只能使用特定主要畫面格。 特定主要畫面格喜歡<xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>建立突然跳躍點之間的值，也就是，動畫的變更會快速發生，而不是微量。  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](https://go.microsoft.com/fwlink/?LinkID=160012)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.ContentControl.Content%2A>
- <xref:System.Windows.Controls.Button>
- <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>
- [主要畫面格動畫概觀](key-frame-animations-overview.md)
- [主要畫面格操作說明主題](key-frame-animation-how-to-topics.md)
