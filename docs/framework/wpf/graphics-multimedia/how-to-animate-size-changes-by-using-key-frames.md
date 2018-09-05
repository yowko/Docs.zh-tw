---
title: 操作說明：使用主要畫面格建立大小變更的動畫
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 69845d1d75f81042bbeb20ee6b1015f5c2f53b81
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43672554"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a>操作說明：使用主要畫面格建立大小變更的動畫
這個範例示範如何使用主要畫面格建立大小變更的動畫。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>類別以動畫顯示<xref:System.Windows.Media.ArcSegment.Size%2A>屬性<xref:System.Windows.Media.ArcSegment>。 這個動畫會以下列方式使用三個主要畫面格：  
  
1.  在動畫的前半秒，期間使用的執行個體<xref:System.Windows.Media.Animation.LinearSizeKeyFrame>類別來逐漸增加弧線的大小。線性主要畫面格喜歡<xref:System.Windows.Media.Animation.LinearSizeKeyFrame>建立平滑的線性轉換值之間。  
  
2.  在下一步結尾半秒，使用的執行個體<xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>類別來突然增加弧線的大小。特定主要畫面格喜歡<xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>建立突然跳躍點之間的值，也就是，突然發生大小變更，而不是微量。  
  
3.  最後兩秒，透過使用的執行個體<xref:System.Windows.Media.Animation.SplineSizeKeyFrame>類別來增加弧線的大小。曲線主要畫面格喜歡<xref:System.Windows.Media.Animation.SplineSizeKeyFrame>變數之間建立轉換的值根據<xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A>屬性。 在此範例中，弧線的大小一開始會緩慢增加，然後在接近時間區段結尾時以指數方式增加。  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](https://go.microsoft.com/fwlink/?LinkID=160012)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.ArcSegment.Size%2A>  
 <xref:System.Windows.Media.ArcSegment>  
 <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>  
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [主要畫面格操作說明主題](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
