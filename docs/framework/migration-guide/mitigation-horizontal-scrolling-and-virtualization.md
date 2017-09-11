---
title: "風險降低：水平捲動和虛擬化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5bafd9b-a3b3-4f92-8241-2aad254fb1a9
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 40eaf185e9c0c60493e9a2e5428c58b7463789fe
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-horizontal-scrolling-and-virtualization"></a><span data-ttu-id="cd50d-102">風險降低：水平捲動和虛擬化</span><span class="sxs-lookup"><span data-stu-id="cd50d-102">Mitigation: Horizontal Scrolling and Virtualization</span></span>
<span data-ttu-id="cd50d-103">此變更會套用到以正交於主要捲動方向之方向執行自身的虛擬化的 <xref:System.Windows.Controls.ItemsControl>。</span><span class="sxs-lookup"><span data-stu-id="cd50d-103">This change applies to an <xref:System.Windows.Controls.ItemsControl> that does its own virtualization in the direction orthogonal to the main scrolling direction.</span></span> <span data-ttu-id="cd50d-104">(主要範例是 <xref:System.Windows.Controls.DataGrid.EnableColumnVirtualization%2A> 設定為 `true` 的 <xref:System.Windows.Controls.DataGrid> 控制項)。某些水平捲動作業的結果已變更，產生的結果更直覺，且更類似於可比較的垂直作業的結果。</span><span class="sxs-lookup"><span data-stu-id="cd50d-104">(The chief  example is a <xref:System.Windows.Controls.DataGrid> control with <xref:System.Windows.Controls.DataGrid.EnableColumnVirtualization%2A> set to `true`.)  The outcome of certain  horizontal scrolling operations has been changed to produce results that are more intuitive and more analogous to the results of comparable vertical operations.</span></span>  <span data-ttu-id="cd50d-105">具體的作業包括 [捲動至此處] 和 [右邊緣]，以使用以滑鼠右鍵按一下水平捲軸所取得之功能表中的名稱。</span><span class="sxs-lookup"><span data-stu-id="cd50d-105">The specific operations include **Scroll Here** and **Right Edge**, to use the names from the menu obtained by right-clicking a horizontal scrollbar.</span></span>  <span data-ttu-id="cd50d-106">這兩個都會計算候選位移並呼叫 <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset%2A?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="cd50d-106">Both of these compute a  candidate offset and call <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset%2A?displayProperty=fullName>.</span></span>  <span data-ttu-id="cd50d-107">捲動至新的位移後，「此處」或「右邊緣」的定義可能已變更，因為最近取消虛擬化的內容已變更 <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A?displayProperty=fullName> 的值。</span><span class="sxs-lookup"><span data-stu-id="cd50d-107">After scrolling to the new offset, the definition of "here" or "right edge" may have changed because newly de-virtualized content has changed the value of <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A?displayProperty=fullName>.</span></span>  
  
## <a name="description-of-the-change"></a><span data-ttu-id="cd50d-108">變更的描述</span><span class="sxs-lookup"><span data-stu-id="cd50d-108">Description of the change</span></span>  
 <span data-ttu-id="cd50d-109">在 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 之前，捲軸作業會直接使用候選位移，即使它可能已不再是「此處」或位於「右邊緣」。</span><span class="sxs-lookup"><span data-stu-id="cd50d-109">Prior to the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], the scroll operation simply uses the candidate offset, even though it may not be "here" or at the "right edge" any more.</span></span>  <span data-ttu-id="cd50d-110">這會導致類似捲動指標「反彈」的效果，以範例說明最為合適。</span><span class="sxs-lookup"><span data-stu-id="cd50d-110">This results in effects like "bouncing" the scroll thumb, best illustrated by example.</span></span>  <span data-ttu-id="cd50d-111">假設 <xref:System.Windows.Controls.DataGrid> 控制項的 <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A> 設為 1000，而 <xref:System.Windows.FrameworkElement.Width%2A> 設為 200。</span><span class="sxs-lookup"><span data-stu-id="cd50d-111">Suppose a <xref:System.Windows.Controls.DataGrid> control has <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A> set to 1000 and <xref:System.Windows.FrameworkElement.Width%2A> set to 200.</span></span>  <span data-ttu-id="cd50d-112">捲動到「右邊緣」會使用候選位移 1000 - 200 = 800。</span><span class="sxs-lookup"><span data-stu-id="cd50d-112">A scroll to "Right Edge" uses candidate offset  1000 - 200 = 800.</span></span>  <span data-ttu-id="cd50d-113">捲動到該位移時，新的資料行會取消虛擬化；假設它們非常寬，因此 <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A> 變更為 2000。</span><span class="sxs-lookup"><span data-stu-id="cd50d-113">While scrolling to that offset, new columns are de-virtualized; let's suppose they are very wide, so that the <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A> changes to 2000.</span></span>  <span data-ttu-id="cd50d-114">捲軸在 <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A>= 800 結束，而指標會反彈回到捲軸中央附近，精確來說是在 800/2000 等於 40% 的位置。</span><span class="sxs-lookup"><span data-stu-id="cd50d-114">The scroll ends with <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A>=800, and the thumb "bounces" back to near the middle of the scrollbar -- precisely at 800/2000 = 40%.</span></span>  
  
 <span data-ttu-id="cd50d-115">從 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 開始，發生這種情況時，會重新計算新的候選位移。</span><span class="sxs-lookup"><span data-stu-id="cd50d-115">Starting with the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], a new candidate offset is recomputed when this situation occurs.</span></span> <span data-ttu-id="cd50d-116">(這是垂直捲動目前運作的方式)。</span><span class="sxs-lookup"><span data-stu-id="cd50d-116">(This is how vertical scrolling works already.)</span></span>  
  
## <a name="impact"></a><span data-ttu-id="cd50d-117">影響</span><span class="sxs-lookup"><span data-stu-id="cd50d-117">Impact</span></span>  
 <span data-ttu-id="cd50d-118">此變更會為使用者產生更為可預測且直覺式的體驗，但它會影響依賴 <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A?displayProperty=fullName> 於水平捲動後 (無論是由使用者叫用或是明確呼叫 <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset%2A?displayProperty=fullName>) 之確切值的所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="cd50d-118">The change produces a more predictable and intuitive experience for the end user, but it could also affect any app that depends on the exact value of <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A?displayProperty=fullName> after a horizontal scroll, whether invoked by the end user or by an explicit call to <xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset%2A?displayProperty=fullName>.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="cd50d-119">緩和</span><span class="sxs-lookup"><span data-stu-id="cd50d-119">Mitigation</span></span>  
 <span data-ttu-id="cd50d-120">在因為取消虛擬化而可能變更 <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A> 的任何水平捲動之後，為 <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A?displayProperty=fullName> 使用預測值的應用程式應該改為擷取實際的值 (以及 <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A> 的值)。</span><span class="sxs-lookup"><span data-stu-id="cd50d-120">An app that uses a predicted value for <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A?displayProperty=fullName> should be changed to retrieve the actual value (and the value of <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A>) after any horizontal scroll that could change <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A> due to de-virtualization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd50d-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd50d-121">See Also</span></span>  
 [<span data-ttu-id="cd50d-122">執行階段變更</span><span class="sxs-lookup"><span data-stu-id="cd50d-122">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-2.md)

