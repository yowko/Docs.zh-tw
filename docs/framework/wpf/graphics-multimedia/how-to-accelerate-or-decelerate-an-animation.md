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
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376243"
---
# <a name="how-to-accelerate-or-decelerate-an-animation"></a><span data-ttu-id="35ae9-102">HOW TO：動畫加速或減速</span><span class="sxs-lookup"><span data-stu-id="35ae9-102">How to: Accelerate or Decelerate an Animation</span></span>
<span data-ttu-id="35ae9-103">此範例示範如何讓動畫加速和減速經過一段時間。</span><span class="sxs-lookup"><span data-stu-id="35ae9-103">This example demonstrates how to make an animation accelerate and decelerate over time.</span></span> <span data-ttu-id="35ae9-104">在下列範例中，數個矩形有動畫效果所使用不同的動畫<xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A>和<xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A>設定。</span><span class="sxs-lookup"><span data-stu-id="35ae9-104">In the following example, several rectangles are animated by animations with different <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> and <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35ae9-105">範例</span><span class="sxs-lookup"><span data-stu-id="35ae9-105">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AccelDecelExample.xaml#1)]  
  
 <span data-ttu-id="35ae9-106">此範例中，已省略的程式碼。</span><span class="sxs-lookup"><span data-stu-id="35ae9-106">Code has been omitted from this example.</span></span> <span data-ttu-id="35ae9-107">完整的程式碼，請參閱 <<c0> [ 動畫計時行為 (C#)](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp)或是[動畫計時行為 (Visual Basic)](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic)。</c0></span><span class="sxs-lookup"><span data-stu-id="35ae9-107">For the complete code, see the [Animation Timing Behavior (C#)](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp) or [Animation Timing Behavior (Visual Basic)](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic).</span></span>
