---
title: HOW TO：指定腳本動畫之間的傳遞行為
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF], handoff behavior between animations
- animation [WPF], handoff behavior between
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
ms.openlocfilehash: 9a27c377e2993c1e67ada508071698a541cec660
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56305437"
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a><span data-ttu-id="993eb-102">HOW TO：指定腳本動畫之間的傳遞行為</span><span class="sxs-lookup"><span data-stu-id="993eb-102">How to: Specify HandoffBehavior Between Storyboard Animations</span></span>
<span data-ttu-id="993eb-103">此範例示範如何指定分鏡腳本動畫之間的遞移式行為。</span><span class="sxs-lookup"><span data-stu-id="993eb-103">This example shows how to specify handoff behavior between storyboard animations.</span></span> <span data-ttu-id="993eb-104"><xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>屬性<xref:System.Windows.Media.Animation.BeginStoryboard>指定新動畫已套用至屬性的任何現有的互動。</span><span class="sxs-lookup"><span data-stu-id="993eb-104">The <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> property of <xref:System.Windows.Media.Animation.BeginStoryboard> specifies how new animations interact with any existing ones that are already applied to a property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="993eb-105">範例</span><span class="sxs-lookup"><span data-stu-id="993eb-105">Example</span></span>  
 <span data-ttu-id="993eb-106">下列範例會建立兩個按鈕放大滑鼠游標移到上面時，會變小，當資料指標移開。</span><span class="sxs-lookup"><span data-stu-id="993eb-106">The following example creates two buttons that enlarge when the mouse cursor moves over them and become smaller when the cursor moves away.</span></span> <span data-ttu-id="993eb-107">如果您將滑鼠移的按鈕，並快速移除資料指標，第一個完成之前，將會套用第二個動畫。</span><span class="sxs-lookup"><span data-stu-id="993eb-107">If you mouse over a button and then quickly remove the cursor, the second animation will be applied before the first one is finished.</span></span> <span data-ttu-id="993eb-108">當兩個動畫重疊像這樣，您可以看到之間的差異<xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>的值<xref:System.Windows.Media.Animation.HandoffBehavior.Compose>和<xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>。</span><span class="sxs-lookup"><span data-stu-id="993eb-108">It is when two animations overlap like this that you can see the difference between the <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> values of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> and <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.</span></span> <span data-ttu-id="993eb-109">值為<xref:System.Windows.Media.Animation.HandoffBehavior.Compose>結合了重疊造成的值時的動畫之間順暢轉換的動畫<xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>使新動畫立即取代先前的重疊的動畫。</span><span class="sxs-lookup"><span data-stu-id="993eb-109">A value of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> combines the overlapping animations causing a smoother transition between animations while a value of <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> causes the new animation to immediately replace the earlier overlapping animation.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="993eb-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="993eb-110">See also</span></span>
- <xref:System.Windows.Media.Animation.BeginStoryboard>
- <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>
- [<span data-ttu-id="993eb-111">動畫概觀</span><span class="sxs-lookup"><span data-stu-id="993eb-111">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="993eb-112">動畫和計時</span><span class="sxs-lookup"><span data-stu-id="993eb-112">Animation and Timing</span></span>](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)
- [<span data-ttu-id="993eb-113">動畫和計時 how to 主題</span><span class="sxs-lookup"><span data-stu-id="993eb-113">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
