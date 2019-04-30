---
title: HOW TO：使用 From、To 和 By 控制動畫
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
ms.openlocfilehash: 56522ee5bd4391e43c261558b2fa622234c9ea3b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008781"
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a>HOW TO：使用 From、To 和 By 控制動畫
「 From/To/By"或 「 基本動畫 」 會建立兩個目標值之間的轉換 (請參閱[動畫概觀](animation-overview.md)不同類型動畫的簡介)。 若要設定基本動畫目標值時，使用其<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>， <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>，和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性。  下表摘要說明如何<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>， <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>，和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性可能會一起或分開來決定動畫的目標值。  
  
|指定的屬性|產生的行為|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|動畫會從所指定的值<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性要繪製之屬性的基底值或上一個動畫輸出值，根據上一個動畫的設定方式。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 和 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|動畫會從所指定的值<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性所指定的值為<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 和 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|動畫會從所指定的值<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>屬性設為值的總和所指定<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|從動畫的屬性的基底值的動畫進展或上一個動畫輸出值所指定的值來<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|動畫會從要繪製之屬性的基底值或上一個動畫輸出值，該值與所指定之值的總和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>屬性。|  
  
> [!NOTE]
>  未設定兩者<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>屬性和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>上相同的動畫屬性。  
  
 若要使用其他插補方法，或建立兩個以上的目標值之間的動畫，請使用主要畫面格動畫。 請參閱[主要畫面格動畫概觀](key-frame-animations-overview.md)如需詳細資訊。  
  
 將多個動畫套用至單一屬性的相關資訊，請參閱[主要畫面格動畫概觀](key-frame-animations-overview.md)。  
  
 下列範例顯示的設定不同的效果<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>， <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>，和<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>動畫的屬性。  
  
## <a name="example"></a>範例  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>另請參閱

- [動畫概觀](animation-overview.md)
- [主要畫面格動畫概觀](key-frame-animations-overview.md)
- [From、To 和 By 動畫目標值範例](https://go.microsoft.com/fwlink/?LinkID=159988)
