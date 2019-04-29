---
title: HOW TO：動畫加速或減速
ms.date: 03/30/2017
helpviewer_keywords:
- decelerating animation [WPF]
- accelerating animation [WPF]
- animation [WPF], accelerating
- animation [WPF], decelerating
ms.assetid: 4f383b2c-f94d-4a4e-9a06-f56f5dae95f9
ms.openlocfilehash: d4fcaf4a684c37590f27d603ef5cb2c86a6fb854
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762159"
---
# <a name="how-to-accelerate-or-decelerate-an-animation"></a>HOW TO：動畫加速或減速
此範例示範如何讓動畫加速和減速經過一段時間。 在下列範例中，數個矩形有動畫效果所使用不同的動畫<xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A>和<xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A>設定。  
  
## <a name="example"></a>範例  
 [!code-xaml[timingbehaviors_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AccelDecelExample.xaml#1)]  
  
 此範例中，已省略的程式碼。 完整的程式碼，請參閱 <<c0> [ 動畫計時行為 (C#)](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp)或是[動畫計時行為 (Visual Basic)](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic)。</c0>
