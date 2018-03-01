---
title: "ProgressBar 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c5ca5fd908124b0f38643c7b2833ba591be3b980
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="progressbar-control-overview-windows-forms"></a><span data-ttu-id="37f4f-102">ProgressBar 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="37f4f-102">ProgressBar Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="37f4f-103"><xref:System.Windows.Forms.ToolStripProgressBar> 控制項會取代 <xref:System.Windows.Forms.ProgressBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ProgressBar> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="37f4f-103">The <xref:System.Windows.Forms.ToolStripProgressBar> control replaces and adds functionality to the <xref:System.Windows.Forms.ProgressBar> control; however, the <xref:System.Windows.Forms.ProgressBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="37f4f-104">Windows Form<xref:System.Windows.Forms.ProgressBar>控制項顯示適當的矩形排列在水平列數目，表示處理程序的進度。</span><span class="sxs-lookup"><span data-stu-id="37f4f-104">The Windows Forms <xref:System.Windows.Forms.ProgressBar> control indicates the progress of a process by displaying an appropriate number of rectangles arranged in a horizontal bar.</span></span> <span data-ttu-id="37f4f-105">處理程序完成時，會自動填入列。</span><span class="sxs-lookup"><span data-stu-id="37f4f-105">When the process is complete, the bar is filled.</span></span> <span data-ttu-id="37f4f-106">進度列通常用來讓使用者了解長等待處理序完成。比方說，當大型檔案載入時。</span><span class="sxs-lookup"><span data-stu-id="37f4f-106">Progress bars are commonly used to give the user an idea of how long to wait for a process to complete; for instance, when a large file is being loaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37f4f-107"><xref:System.Windows.Forms.ProgressBar>控制項可以只是水平方向表單上。</span><span class="sxs-lookup"><span data-stu-id="37f4f-107">The <xref:System.Windows.Forms.ProgressBar> control can only be oriented horizontally on the form.</span></span>  
  
## <a name="key-properties-and-methods"></a><span data-ttu-id="37f4f-108">索引鍵屬性和方法</span><span class="sxs-lookup"><span data-stu-id="37f4f-108">Key Properties and Methods</span></span>  
 <span data-ttu-id="37f4f-109">索引鍵屬性<xref:System.Windows.Forms.ProgressBar>控制是<xref:System.Windows.Forms.ProgressBar.Value%2A>， <xref:System.Windows.Forms.ProgressBar.Minimum%2A>，和<xref:System.Windows.Forms.ProgressBar.Maximum%2A>。</span><span class="sxs-lookup"><span data-stu-id="37f4f-109">The key properties of the <xref:System.Windows.Forms.ProgressBar> control are <xref:System.Windows.Forms.ProgressBar.Value%2A>, <xref:System.Windows.Forms.ProgressBar.Minimum%2A>, and <xref:System.Windows.Forms.ProgressBar.Maximum%2A>.</span></span> <span data-ttu-id="37f4f-110"><xref:System.Windows.Forms.ProgressBar.Minimum%2A>和<xref:System.Windows.Forms.ProgressBar.Maximum%2A>設定可以顯示進度列的最大和最小值的屬性。</span><span class="sxs-lookup"><span data-stu-id="37f4f-110">The <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> properties set the maximum and minimum values the progress bar can display.</span></span> <span data-ttu-id="37f4f-111"><xref:System.Windows.Forms.ProgressBar.Value%2A>屬性代表已完成此作業的進度。</span><span class="sxs-lookup"><span data-stu-id="37f4f-111">The <xref:System.Windows.Forms.ProgressBar.Value%2A> property represents the progress that has been made toward completing the operation.</span></span> <span data-ttu-id="37f4f-112">因為控制項中顯示的列由區塊組成，值會顯示由<xref:System.Windows.Forms.ProgressBar>控制項只近似<xref:System.Windows.Forms.ProgressBar.Value%2A>屬性的目前值。</span><span class="sxs-lookup"><span data-stu-id="37f4f-112">Because the bar displayed in the control is composed of blocks, the value displayed by the <xref:System.Windows.Forms.ProgressBar> control only approximates the <xref:System.Windows.Forms.ProgressBar.Value%2A> property's current value.</span></span> <span data-ttu-id="37f4f-113">根據大小<xref:System.Windows.Forms.ProgressBar>控制項，<xref:System.Windows.Forms.ProgressBar.Value%2A>屬性會決定何時顯示下一個區塊。</span><span class="sxs-lookup"><span data-stu-id="37f4f-113">Based on the size of the <xref:System.Windows.Forms.ProgressBar> control, the <xref:System.Windows.Forms.ProgressBar.Value%2A> property determines when to display the next block.</span></span>  
  
 <span data-ttu-id="37f4f-114">更新目前的進度值的最常見方式是撰寫程式碼來設定<xref:System.Windows.Forms.ProgressBar.Value%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="37f4f-114">The most common way to update the current progress value is to write code to set the <xref:System.Windows.Forms.ProgressBar.Value%2A> property.</span></span> <span data-ttu-id="37f4f-115">在載入的大型檔案的範例中，您可能設定的檔案，以 kb 為單位的大小的最大值。</span><span class="sxs-lookup"><span data-stu-id="37f4f-115">In the example of loading a large file, you might set the maximum to the size of the file in kilobytes.</span></span> <span data-ttu-id="37f4f-116">比方說，如果<xref:System.Windows.Forms.ProgressBar.Maximum%2A>屬性設定為 100，<xref:System.Windows.Forms.ProgressBar.Minimum%2A>屬性設為 10，和<xref:System.Windows.Forms.ProgressBar.Value%2A>屬性設定為 50，將會顯示 5 的矩形。</span><span class="sxs-lookup"><span data-stu-id="37f4f-116">For example, if the <xref:System.Windows.Forms.ProgressBar.Maximum%2A> property is set to 100, the <xref:System.Windows.Forms.ProgressBar.Minimum%2A> property is set to 10, and the <xref:System.Windows.Forms.ProgressBar.Value%2A> property is set to 50, 5 rectangles will be displayed.</span></span> <span data-ttu-id="37f4f-117">這是數量的可顯示的一半。</span><span class="sxs-lookup"><span data-stu-id="37f4f-117">This is half of the number that can be displayed.</span></span>  
  
 <span data-ttu-id="37f4f-118">不過，還有其他方式修改顯示的值<xref:System.Windows.Forms.ProgressBar>控制項，除了設定<xref:System.Windows.Forms.ProgressBar.Value%2A>直接屬性。</span><span class="sxs-lookup"><span data-stu-id="37f4f-118">However, there are other ways to modify the value displayed by the <xref:System.Windows.Forms.ProgressBar> control, aside from setting the <xref:System.Windows.Forms.ProgressBar.Value%2A> property directly.</span></span> <span data-ttu-id="37f4f-119"><xref:System.Windows.Forms.ProgressBar.Step%2A>屬性可以用來指定要遞增的值<xref:System.Windows.Forms.ProgressBar.Value%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="37f4f-119">The <xref:System.Windows.Forms.ProgressBar.Step%2A> property can be used to specify a value to increment the <xref:System.Windows.Forms.ProgressBar.Value%2A> property by.</span></span> <span data-ttu-id="37f4f-120">然後，呼叫<xref:System.Windows.Forms.ProgressBar.PerformStep%2A>方法將遞增的值。</span><span class="sxs-lookup"><span data-stu-id="37f4f-120">Then, calling the <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> method will increment the value.</span></span> <span data-ttu-id="37f4f-121">若要變化的遞增值，您可以使用<xref:System.Windows.Forms.ProgressBar.Increment%2A>方法並指定用來遞增值<xref:System.Windows.Forms.ProgressBar.Value%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="37f4f-121">To vary the increment value, you can use the <xref:System.Windows.Forms.ProgressBar.Increment%2A> method and specify a value with which to increment the <xref:System.Windows.Forms.ProgressBar.Value%2A> property.</span></span>  
  
 <span data-ttu-id="37f4f-122">另一個控制項，以圖形方式通知使用者有關目前的動作是<xref:System.Windows.Forms.StatusBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="37f4f-122">Another control that graphically informs the user about a current action is the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="37f4f-123"><xref:System.Windows.Forms.StatusStrip>和<xref:System.Windows.Forms.ToolStripStatusLabel>控制項取代，並將功能加入至<xref:System.Windows.Forms.StatusBar>和<xref:System.Windows.Forms.StatusBarPanel>控制項，不過，<xref:System.Windows.Forms.StatusBar>和<xref:System.Windows.Forms.StatusBarPanel>控制項是被保留為回溯相容性及未來使用，如果您選擇。</span><span class="sxs-lookup"><span data-stu-id="37f4f-123">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37f4f-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="37f4f-124">See Also</span></span>  
 <xref:System.Windows.Forms.ProgressBar>  
 [<span data-ttu-id="37f4f-125">ProgressBar 控制項</span><span class="sxs-lookup"><span data-stu-id="37f4f-125">ProgressBar Control</span></span>](../../../../docs/framework/winforms/controls/progressbar-control-windows-forms.md)
