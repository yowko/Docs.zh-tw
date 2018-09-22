---
title: 如何：動畫加速或減速
ms.date: 03/30/2017
helpviewer_keywords:
- decelerating animation [WPF]
- accelerating animation [WPF]
- animation [WPF], accelerating
- animation [WPF], decelerating
ms.assetid: 4f383b2c-f94d-4a4e-9a06-f56f5dae95f9
ms.openlocfilehash: b1649f27fc8ff850516eef2086dbce732915406b
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46562713"
---
# <a name="how-to-accelerate-or-decelerate-an-animation"></a>如何：動畫加速或減速
此範例示範如何讓動畫加速和減速經過一段時間。 在下列範例中，數個矩形有動畫效果所使用不同的動畫<xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A>和<xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A>設定。  
  
## <a name="example"></a>範例  
 [!code-xaml[timingbehaviors_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AccelDecelExample.xaml#1)]  
  
 此範例中，已省略的程式碼。 完整的程式碼，請參閱 <<c0> [ 動畫計時行為範例](https://go.microsoft.com/fwlink/?LinkID=159970)。
