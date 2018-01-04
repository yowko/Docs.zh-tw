---
title: "如何：指定腳本動畫之間的傳遞行為"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Storyboards [WPF], handoff behavior between animations
- animation [WPF], handoff behavior between
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 21d4a39b9cbd2ee563edd22818630c18658e1d6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a><span data-ttu-id="2154c-102">如何：指定腳本動畫之間的傳遞行為</span><span class="sxs-lookup"><span data-stu-id="2154c-102">How to: Specify HandoffBehavior Between Storyboard Animations</span></span>
<span data-ttu-id="2154c-103">這個範例示範如何指定分鏡腳本動畫之間的遞移式行為。</span><span class="sxs-lookup"><span data-stu-id="2154c-103">This example shows how to specify handoff behavior between storyboard animations.</span></span> <span data-ttu-id="2154c-104"><xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>屬性<xref:System.Windows.Media.Animation.BeginStoryboard>指定新動畫已套用至屬性的現有與互動。</span><span class="sxs-lookup"><span data-stu-id="2154c-104">The <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> property of <xref:System.Windows.Media.Animation.BeginStoryboard> specifies how new animations interact with any existing ones that are already applied to a property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2154c-105">範例</span><span class="sxs-lookup"><span data-stu-id="2154c-105">Example</span></span>  
 <span data-ttu-id="2154c-106">下列範例會建立兩個按鈕放大滑鼠游標移到上面時，會變小，當資料指標移開。</span><span class="sxs-lookup"><span data-stu-id="2154c-106">The following example creates two buttons that enlarge when the mouse cursor moves over them and become smaller when the cursor moves away.</span></span> <span data-ttu-id="2154c-107">如果您將滑鼠移 按鈕，然後快速移除資料指標，第一個完成之前，將會套用第二個動畫。</span><span class="sxs-lookup"><span data-stu-id="2154c-107">If you mouse over a button and then quickly remove the cursor, the second animation will be applied before the first one is finished.</span></span> <span data-ttu-id="2154c-108">您可以看到之間的差異如下重疊的兩個動畫時<xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>值<xref:System.Windows.Media.Animation.HandoffBehavior.Compose>和<xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>。</span><span class="sxs-lookup"><span data-stu-id="2154c-108">It is when two animations overlap like this that you can see the difference between the <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> values of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> and <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.</span></span> <span data-ttu-id="2154c-109">值為<xref:System.Windows.Media.Animation.HandoffBehavior.Compose>結合造成平穩動畫時的值之間的重疊動畫<xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>使新的動畫，若要立即取代先前重疊的動畫。</span><span class="sxs-lookup"><span data-stu-id="2154c-109">A value of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> combines the overlapping animations causing a smoother transition between animations while a value of <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> causes the new animation to immediately replace the earlier overlapping animation.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="2154c-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="2154c-110">See Also</span></span>  
 <xref:System.Windows.Media.Animation.BeginStoryboard>  
 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>  
 [<span data-ttu-id="2154c-111">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="2154c-111">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="2154c-112">動畫和計時</span><span class="sxs-lookup"><span data-stu-id="2154c-112">Animation and Timing</span></span>](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="2154c-113">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="2154c-113">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
