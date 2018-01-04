---
title: "操作說明：使用主要畫面格建立大小變更的動畫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 30ee897efd01712bf4313da87e1050c5a16e4523
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a>操作說明：使用主要畫面格建立大小變更的動畫
這個範例示範如何使用主要畫面格建立大小變更的動畫。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>類別以動畫方式顯示<xref:System.Windows.Media.ArcSegment.Size%2A>屬性<xref:System.Windows.Media.ArcSegment>。 這個動畫會以下列方式使用三個主要畫面格：  
  
1.  在第一個半秒數的動畫，會使用的執行個體<xref:System.Windows.Media.Animation.LinearSizeKeyFrame>類別來逐漸增加弧線的大小。線性的主要畫面格喜歡<xref:System.Windows.Media.Animation.LinearSizeKeyFrame>建立值之間的平順地線性轉換。  
  
2.  在下一個結尾半秒，使用的執行個體<xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>類別突然增加弧線的大小。獨立的主要畫面格喜歡<xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>建立突然跳躍點之間的值，也就是，大小變更突然出現，並不會出現細微。  
  
3.  在最後的兩秒，使用 執行個體<xref:System.Windows.Media.Animation.SplineSizeKeyFrame>弧線的大小增加的類別。曲線主要畫面格喜歡<xref:System.Windows.Media.Animation.SplineSizeKeyFrame>建立變數的值根據值之間轉換<xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A>屬性。 在此範例中，弧線的大小一開始會緩慢增加，然後在接近時間區段結尾時以指數方式增加。  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.ArcSegment.Size%2A>  
 <xref:System.Windows.Media.ArcSegment>  
 <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>  
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [主要畫面格操作說明主題](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
