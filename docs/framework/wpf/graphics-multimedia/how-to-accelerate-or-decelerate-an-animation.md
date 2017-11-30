---
title: "如何：動畫加速或減速"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- decelerating animation [WPF]
- accelerating animation [WPF]
- animation [WPF], accelerating
- animation [WPF], decelerating
ms.assetid: 4f383b2c-f94d-4a4e-9a06-f56f5dae95f9
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f4820f312ca8d404123710321a9f45bff1545f10
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-accelerate-or-decelerate-an-animation"></a><span data-ttu-id="53503-102">如何：動畫加速或減速</span><span class="sxs-lookup"><span data-stu-id="53503-102">How to: Accelerate or Decelerate an Animation</span></span>
<span data-ttu-id="53503-103">此範例示範如何建立動畫加速及減速經過一段時間。</span><span class="sxs-lookup"><span data-stu-id="53503-103">This example demonstrates how to make an animation accelerate and decelerate over time.</span></span> <span data-ttu-id="53503-104">在下列範例中，數個矩形有動畫效果的動畫不同<xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A>和<xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A>設定。</span><span class="sxs-lookup"><span data-stu-id="53503-104">In the following example, several rectangles are animated by animations with different <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> and <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53503-105">範例</span><span class="sxs-lookup"><span data-stu-id="53503-105">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AccelDecelExample.xaml#1)]  
  
 <span data-ttu-id="53503-106">這個範例中省略了程式碼。</span><span class="sxs-lookup"><span data-stu-id="53503-106">Code has been omitted from this example.</span></span> <span data-ttu-id="53503-107">完整的程式碼，請參閱[動畫計時行為範例](http://go.microsoft.com/fwlink/?LinkID=159970)。</span><span class="sxs-lookup"><span data-stu-id="53503-107">For the complete code, see the [Animation Timing Behavior Sample](http://go.microsoft.com/fwlink/?LinkID=159970).</span></span>
