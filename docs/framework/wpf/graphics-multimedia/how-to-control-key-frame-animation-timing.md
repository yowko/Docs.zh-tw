---
title: "如何：控制主要畫面格動畫執行時間"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], timing
- timing key-fram animation
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3bc3566cf25282749a09c5f2372cd1c81e3ce881
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-key-frame-animation-timing"></a>如何：控制主要畫面格動畫執行時間
這個範例示範如何控制內主要畫面格動畫主要畫面格的時機。 如同其他動畫主要畫面格動畫具有<xref:System.Windows.Media.Animation.Timeline.Duration%2A>屬性。 除了指定動畫的持續時間，您需要指定該期間的哪個部分會分配給每個主要畫面格。 若要配置的時間，您指定<xref:System.Windows.Media.Animation.KeyTime>動畫中的每一個主要畫面格。  
  
 <xref:System.Windows.Media.Animation.KeyTime> （其並未指定主要畫面格播放的時間長度） 的主要畫面格結束時，指定每一個主要畫面格。 您可以指定<xref:System.Windows.Media.Animation.KeyTime>為<xref:System.TimeSpan>值，以百分比表示，或做為<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>或<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>特殊值。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>要在螢幕上繪製矩形。 設定主要畫面格的關鍵時間<xref:System.TimeSpan>值。  
  
 [!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
 [!code-vb[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
 [!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]  
  
 下圖顯示時到達各個主要畫面格的值。  
  
 ![在 3、 4 和 10 秒時到達各個索引鍵值](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")  
  
 下一個範例會顯示完全相同，不同之處在於主要畫面格的關鍵時間設定百分比值的動畫。  
  
 [!code-csharp[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
 [!code-vb[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
 [!code-xaml[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]  
  
 下圖顯示時到達各個主要畫面格的值。  
  
 ![在 3、 4 和 10 秒時到達各個索引鍵值](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")  
  
 下一個範例會使用<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>索引鍵時間值。  
  
 [!code-csharp[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
 [!code-vb[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
 [!code-xaml[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]  
  
 下圖顯示時到達各個主要畫面格的值。  
  
 ![索引鍵值在 3.3、 6.6 和 9.9 秒到達](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")  
  
 最後一個範例會使用<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>索引鍵時間值。  
  
 [!code-csharp[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
 [!code-vb[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
 [!code-xaml[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]  
  
 下圖顯示時到達各個主要畫面格的值。  
  
 ![在 0、 5 和 10 秒時到達各個索引鍵值](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")  
  
 為了簡單起見，程式碼版本，此範例使用本機動畫，並不分鏡腳本，因為單一動畫套用至單一屬性，但這些範例可能修改改為使用分鏡腳本。 如需顯示如何宣告在程式碼中的分鏡腳本範例，請參閱[使用分鏡腳本建立屬性的動畫](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)。  
  
 如需完整的範例，請參閱[主要畫面格動畫範例](http://go.microsoft.com/fwlink/?LinkID=160012)。 如需主要畫面格動畫的詳細資訊，請參閱[主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 [主要畫面格動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [操作說明主題](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
