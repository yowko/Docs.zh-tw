---
title: "如何：同步搜尋時鐘"
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
- clocks [WPF], seeking synchronously
- seeking clocks synchronously [WPF]
ms.assetid: e5b7529b-b7d0-40d2-9e1d-fa4b5e736e96
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90611e0b18e58e4c24b44e7c87cba56e4b0b01ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-seek-a-clock-synchronously"></a><span data-ttu-id="8dd74-102">如何：同步搜尋時鐘</span><span class="sxs-lookup"><span data-stu-id="8dd74-102">How to: Seek a Clock Synchronously</span></span>
<span data-ttu-id="8dd74-103">使用<xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A>来搜尋的特定點的時鐘同步的方法。</span><span class="sxs-lookup"><span data-stu-id="8dd74-103">Use the <xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A> method to seek a clock to a specific point synchronously.</span></span> <span data-ttu-id="8dd74-104">下列範例示範<xref:System.Windows.Media.Animation.ClockController.Seek%2A>和<xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A>方法<xref:System.Windows.Media.Animation.ClockController>。</span><span class="sxs-lookup"><span data-stu-id="8dd74-104">The following example demonstrates both the <xref:System.Windows.Media.Animation.ClockController.Seek%2A> and <xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A> methods of a <xref:System.Windows.Media.Animation.ClockController>.</span></span>  
  
 <span data-ttu-id="8dd74-105">這個範例示範如何搜尋<xref:System.Windows.Media.Animation.Clock>; 如需範例示範如何搜尋分鏡腳本，請參閱[分鏡腳本以同步方式搜尋](../../../../docs/framework/wpf/graphics-multimedia/how-to-seek-a-storyboard-synchronously.md)。</span><span class="sxs-lookup"><span data-stu-id="8dd74-105">This example shows how to seek a <xref:System.Windows.Media.Animation.Clock>; for an example showing how to seek a storyboard, see [Seek a Storyboard Synchronously](../../../../docs/framework/wpf/graphics-multimedia/how-to-seek-a-storyboard-synchronously.md) .</span></span>  
  
## <a name="example"></a><span data-ttu-id="8dd74-106">範例</span><span class="sxs-lookup"><span data-stu-id="8dd74-106">Example</span></span>  
 [!code-csharp[ClockController_procedural_snip#ClockControllerSeekExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClockController_procedural_snip/CSharp/SeekAlignedToLastTickExample.cs#clockcontrollerseekexample)]
 [!code-vb[ClockController_procedural_snip#ClockControllerSeekExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClockController_procedural_snip/visualbasic/seekalignedtolasttickexample.vb#clockcontrollerseekexample)]
