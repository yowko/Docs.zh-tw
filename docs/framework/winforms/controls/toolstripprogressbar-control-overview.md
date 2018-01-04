---
title: "ToolStripProgressBar 控制項概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ToolStripProgressBar
helpviewer_keywords:
- toolbars [Windows Forms], progress bars
- progress controls [Windows Forms]
- ToolStripProgressBar control [Windows Forms], about ToolStripProgressBar control
ms.assetid: ec3ab522-5fe4-4b4d-a551-bc19e84f4774
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ee73d87a65e9febed6ebd5ad981dcd548fc2404
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="toolstripprogressbar-control-overview"></a><span data-ttu-id="4632f-102">ToolStripProgressBar 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="4632f-102">ToolStripProgressBar Control Overview</span></span>
<span data-ttu-id="4632f-103"><xref:System.Windows.Forms.ToolStripProgressBar>結合浮動定位和所有的轉譯功能<xref:System.Windows.Forms.ToolStrip>其一般的程序追蹤功能使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="4632f-103">The <xref:System.Windows.Forms.ToolStripProgressBar> combines the rafting and rendering functionality of all <xref:System.Windows.Forms.ToolStrip> controls with its typical process-tracking functionality.</span></span> <span data-ttu-id="4632f-104">A<xref:System.Windows.Forms.ToolStripProgressBar>最通常由<xref:System.Windows.Forms.StatusStrip>，且較不頻繁的<xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="4632f-104">A <xref:System.Windows.Forms.ToolStripProgressBar> is most usually hosted by <xref:System.Windows.Forms.StatusStrip>, and less frequently by a <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
 <span data-ttu-id="4632f-105">雖然<xref:System.Windows.Forms.ToolStripProgressBar>取代，並將功能加入至較舊的版本中的控制項<xref:System.Windows.Forms.ToolStripProgressBar>如果想要保留以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="4632f-105">Although <xref:System.Windows.Forms.ToolStripProgressBar> replaces and adds functionality to the control in previous versions, <xref:System.Windows.Forms.ToolStripProgressBar> is retained for both backward compatibility and future use if desired.</span></span>  
  
### <a name="important-toolstripprogressbar-members"></a><span data-ttu-id="4632f-106">重要 ToolStripProgressBar 成員</span><span class="sxs-lookup"><span data-stu-id="4632f-106">Important ToolStripProgressBar Members</span></span>  
  
|<span data-ttu-id="4632f-107">名稱</span><span class="sxs-lookup"><span data-stu-id="4632f-107">Name</span></span>|<span data-ttu-id="4632f-108">描述</span><span class="sxs-lookup"><span data-stu-id="4632f-108">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripProgressBar.MarqueeAnimationSpeed%2A>|<span data-ttu-id="4632f-109">取得或設定值，表示每個之間的延遲<xref:System.Windows.Forms.ProgressBarStyle.Marquee>顯示更新，以毫秒為單位。</span><span class="sxs-lookup"><span data-stu-id="4632f-109">Gets or sets a value representing the delay between each <xref:System.Windows.Forms.ProgressBarStyle.Marquee> display update, in milliseconds.</span></span>|  
|<xref:System.Windows.Forms.ProgressBar.Maximum%2A>|<span data-ttu-id="4632f-110">取得或設定定義這個範圍的上限<xref:System.Windows.Forms.ToolStripProgressBar>。</span><span class="sxs-lookup"><span data-stu-id="4632f-110">Gets or sets the upper bound of the range that is defined for this <xref:System.Windows.Forms.ToolStripProgressBar>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar.Minimum%2A>|<span data-ttu-id="4632f-111">取得或設定定義這個範圍的下限<xref:System.Windows.Forms.ToolStripProgressBar>。</span><span class="sxs-lookup"><span data-stu-id="4632f-111">Gets or sets the lower bound of the range that is defined for this <xref:System.Windows.Forms.ToolStripProgressBar>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar.Style%2A>|<span data-ttu-id="4632f-112">取得或設定樣式<xref:System.Windows.Forms.ToolStripProgressBar>用來顯示作業的進度。</span><span class="sxs-lookup"><span data-stu-id="4632f-112">Gets or sets the style that the <xref:System.Windows.Forms.ToolStripProgressBar> uses to display the progress of an operation.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar.Value%2A>|<span data-ttu-id="4632f-113">取得或設定目前的值<xref:System.Windows.Forms.ToolStripProgressBar>。</span><span class="sxs-lookup"><span data-stu-id="4632f-113">Gets or sets the current value of the <xref:System.Windows.Forms.ToolStripProgressBar>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar.PerformStep%2A>|<span data-ttu-id="4632f-114">進度列的目前位置前移數量<xref:System.Windows.Forms.ToolStripProgressBar.Step%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="4632f-114">Advances the current position of the progress bar by the amount of the <xref:System.Windows.Forms.ToolStripProgressBar.Step%2A> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4632f-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="4632f-115">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripProgressBar>
