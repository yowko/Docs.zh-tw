---
title: 如何：控制主要畫面格動畫執行時間
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], timing
- timing key-frame animation
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
ms.openlocfilehash: 8cfd2be0bbc526ed92a5fb1b558a5a41dc9c3113
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344740"
---
# <a name="how-to-control-key-frame-animation-timing"></a>如何：控制主要畫面格動畫執行時間

此示例演示如何控制關鍵幀動畫中關鍵幀的計時。 與其他動畫一樣，關鍵幀動畫具有屬性<xref:System.Windows.Media.Animation.Timeline.Duration%2A>。 除了指定動畫的持續時間外，還需要指定將該持續時間的哪一部分分配給其每個關鍵幀。 要指定時間，請為動畫中的每個關鍵<xref:System.Windows.Media.Animation.KeyTime>幀指定 a。

每個<xref:System.Windows.Media.Animation.KeyTime>關鍵幀指定關鍵幀何時結束（它不指定關鍵幀播放的時間長度）。 <xref:System.Windows.Media.Animation.KeyTime>您可以將 指定<xref:System.TimeSpan>為值、百分比或 或<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A><xref:System.Windows.Media.Animation.KeyTime.Paced%2A>特殊值。

## <a name="example"></a>範例

下面的示例使用<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>在螢幕上為矩形設置動畫。 關鍵幀的鍵時間設置的值<xref:System.TimeSpan>。

[!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
[!code-vb[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
[!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]

下圖顯示了何時達到每個關鍵幀的值。

![在 3、4 和 10 秒時到達各個主要畫面格](./media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")

下一個示例顯示相同的動畫，只不過關鍵幀的鍵時間設置的百分比值。

[!code-csharp[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
[!code-vb[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
[!code-xaml[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]

下圖顯示了何時達到每個關鍵幀的值。

![在 3、4 和 10 秒時到達各個主要畫面格](./media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")

下一個示例<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>使用關鍵時間值。

[!code-csharp[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
[!code-vb[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
[!code-xaml[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]

下圖顯示了何時達到每個關鍵幀的值。

![在 3.3、6.6 和 9.9 秒時到達各個主要畫面格](./media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")

最後一個示例<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>使用關鍵時間值。

[!code-csharp[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
[!code-vb[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
[!code-xaml[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]

下圖顯示了何時達到每個關鍵幀的值。

![在 0、5 和 10 秒時到達各個主要畫面格](./media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")

為簡單起見，此示例的代碼版本使用本地動畫，而不是分鏡腳本，因為只有單個動畫應用於單個屬性，但可以修改示例以改用分鏡腳本。 有關如何在代碼中聲明分鏡腳本的示例，請參閱[使用分鏡腳本對屬性進行動畫處理](how-to-animate-a-property-by-using-a-storyboard.md)。

如需完整的範例，請參閱[主要畫面格動畫範例](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)。 有關關鍵幀動畫的詳細資訊，請參閱[關鍵幀動畫概述](key-frame-animations-overview.md)。

## <a name="see-also"></a>另請參閱

- [主要畫面格動畫概觀](key-frame-animations-overview.md)
- [動畫概觀](animation-overview.md)
- [HOW TO 主題](animation-and-timing-how-to-topics.md)
