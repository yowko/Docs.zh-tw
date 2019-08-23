---
title: StatusBar 控制項 (Windows Form)
ms.date: 03/30/2017
helpviewer_keywords:
- StatusBar control [Windows Forms]
- status bars [Windows Forms], creating
ms.assetid: 6f543e27-cf78-4b7f-b4d0-6a8030155d48
ms.openlocfilehash: 72a93fc32715596efc7fb0f8b941e62f7019d06c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964413"
---
# <a name="statusbar-control-windows-forms"></a><span data-ttu-id="49034-102">StatusBar 控制項 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="49034-102">StatusBar Control (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="49034-103"><xref:System.Windows.Forms.ToolStripStatusLabel> 控制項會取代 <xref:System.Windows.Forms.StatusBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.StatusBar> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="49034-103">The <xref:System.Windows.Forms.ToolStripStatusLabel> control replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control; however, the <xref:System.Windows.Forms.StatusBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="49034-104">Windows Form <xref:System.Windows.Forms.StatusBar> 控制項在表單裡被當做區域來使用，通常會顯示在視窗底部，在其中應用程式可以顯示各種狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="49034-104">The Windows Forms <xref:System.Windows.Forms.StatusBar> control is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="49034-105"><xref:System.Windows.Forms.StatusBar>控制項可以有狀態列面板, 它們會顯示圖示以指示狀態, 或是動畫中表示進程正在運作的一系列圖示。例如, 表示正在儲存檔的 Microsoft Word。</span><span class="sxs-lookup"><span data-stu-id="49034-105"><xref:System.Windows.Forms.StatusBar> controls can have status-bar panels on them that display icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="49034-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="49034-106">In This Section</span></span>  
 [<span data-ttu-id="49034-107">StatusBar 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="49034-107">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)  
 <span data-ttu-id="49034-108">介紹<xref:System.Windows.Forms.StatusBar>控制項的一般概念, 可讓使用者查看具有焦點之控制項的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="49034-108">Introduces the general concepts of the <xref:System.Windows.Forms.StatusBar> control, which enables users to see relevant information for the control that has focus.</span></span>  
  
 [<span data-ttu-id="49034-109">如何：將面板新增至狀態列控制項</span><span class="sxs-lookup"><span data-stu-id="49034-109">How to: Add Panels to a StatusBar Control</span></span>](how-to-add-panels-to-a-statusbar-control.md)  
 <span data-ttu-id="49034-110">說明如何將可程式化的面板<xref:System.Windows.Forms.StatusBar>新增至控制項。</span><span class="sxs-lookup"><span data-stu-id="49034-110">Explains how to add programmable panels to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="49034-111">如何：判斷按一下 Windows Forms 狀態列控制項中的哪一個面板</span><span class="sxs-lookup"><span data-stu-id="49034-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)  
 <span data-ttu-id="49034-112">說明如何處理<xref:System.Windows.Forms.Control.Click>從控制項引發的<xref:System.Windows.Forms.StatusBar>事件。</span><span class="sxs-lookup"><span data-stu-id="49034-112">Explains how to handle <xref:System.Windows.Forms.Control.Click> events raised from the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="49034-113">如何：設定狀態列面板的大小</span><span class="sxs-lookup"><span data-stu-id="49034-113">How to: Set the Size of Status-Bar Panels</span></span>](how-to-set-the-size-of-status-bar-panels.md)  
 <span data-ttu-id="49034-114">提供可在執行時間控制狀態列面板之寬度和調整大小行為的屬性詳細資料。</span><span class="sxs-lookup"><span data-stu-id="49034-114">Gives details on the properties that control the width and resize behavior of status-bar panels at run time.</span></span>  
  
 [<span data-ttu-id="49034-115">逐步解說：在執行時間更新狀態列資訊</span><span class="sxs-lookup"><span data-stu-id="49034-115">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)  
 <span data-ttu-id="49034-116">說明如何以程式設計方式控制狀態列面板中的資料。</span><span class="sxs-lookup"><span data-stu-id="49034-116">Explains how to programmatically control the data within status-bar panels.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="49034-117">參考資料</span><span class="sxs-lookup"><span data-stu-id="49034-117">Reference</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <span data-ttu-id="49034-118">提供這個類別及其成員的相關參考資訊。</span><span class="sxs-lookup"><span data-stu-id="49034-118">Provides reference information on the class and its members.</span></span>  
  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <span data-ttu-id="49034-119">取代並將功能加入至<xref:System.Windows.Forms.StatusBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="49034-119">Replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="49034-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="49034-120">Related Sections</span></span>  
 [<span data-ttu-id="49034-121">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="49034-121">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="49034-122">提供 Windows Form 控制項的完整清單，以及其用法的資訊連結。</span><span class="sxs-lookup"><span data-stu-id="49034-122">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
