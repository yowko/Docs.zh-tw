---
title: StatusBar 控制項 (Windows Form)
ms.date: 03/30/2017
helpviewer_keywords:
- StatusBar control [Windows Forms]
- status bars [Windows Forms], creating
ms.assetid: 6f543e27-cf78-4b7f-b4d0-6a8030155d48
ms.openlocfilehash: 9ef6bc125a641538e7fd2da4c17c5f25dfc62709
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009652"
---
# <a name="statusbar-control-windows-forms"></a><span data-ttu-id="9493c-102">StatusBar 控制項 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="9493c-102">StatusBar Control (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="9493c-103"><xref:System.Windows.Forms.ToolStripStatusLabel> 控制項會取代 <xref:System.Windows.Forms.StatusBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.StatusBar> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="9493c-103">The <xref:System.Windows.Forms.ToolStripStatusLabel> control replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control; however, the <xref:System.Windows.Forms.StatusBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="9493c-104">Windows Form <xref:System.Windows.Forms.StatusBar> 控制項在表單裡被當做區域來使用，通常會顯示在視窗底部，在其中應用程式可以顯示各種狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="9493c-104">The Windows Forms <xref:System.Windows.Forms.StatusBar> control is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="9493c-105"><xref:System.Windows.Forms.StatusBar> 可以在其上顯示的圖示指出狀態或一系列的動畫圖示，表示正在處理程序; 的狀態列面板控制項。比方說，指出 Microsoft Word 文件正在儲存。</span><span class="sxs-lookup"><span data-stu-id="9493c-105"><xref:System.Windows.Forms.StatusBar> controls can have status-bar panels on them that display icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9493c-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="9493c-106">In This Section</span></span>  
 [<span data-ttu-id="9493c-107">StatusBar 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="9493c-107">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)  
 <span data-ttu-id="9493c-108">導入的一般概念<xref:System.Windows.Forms.StatusBar>控制，可讓使用者看到具有焦點之控制項的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9493c-108">Introduces the general concepts of the <xref:System.Windows.Forms.StatusBar> control, which enables users to see relevant information for the control that has focus.</span></span>  
  
 [<span data-ttu-id="9493c-109">如何：將面板新增至 StatusBar 控制項</span><span class="sxs-lookup"><span data-stu-id="9493c-109">How to: Add Panels to a StatusBar Control</span></span>](how-to-add-panels-to-a-statusbar-control.md)  
 <span data-ttu-id="9493c-110">說明如何將可程式化的面板加入<xref:System.Windows.Forms.StatusBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="9493c-110">Explains how to add programmable panels to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="9493c-111">如何：判斷按下 Windows Forms StatusBar 控制項中的面板</span><span class="sxs-lookup"><span data-stu-id="9493c-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)  
 <span data-ttu-id="9493c-112">說明如何處理<xref:System.Windows.Forms.Control.Click>事件引發從<xref:System.Windows.Forms.StatusBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="9493c-112">Explains how to handle <xref:System.Windows.Forms.Control.Click> events raised from the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="9493c-113">如何：設定狀態列面板的大小</span><span class="sxs-lookup"><span data-stu-id="9493c-113">How to: Set the Size of Status-Bar Panels</span></span>](how-to-set-the-size-of-status-bar-panels.md)  
 <span data-ttu-id="9493c-114">提供控制項的寬度和調整大小行為的狀態列面板，在執行階段屬性的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="9493c-114">Gives details on the properties that control the width and resize behavior of status-bar panels at run time.</span></span>  
  
 [<span data-ttu-id="9493c-115">逐步解說：在執行階段更新狀態列資訊</span><span class="sxs-lookup"><span data-stu-id="9493c-115">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)  
 <span data-ttu-id="9493c-116">說明如何以程式設計方式控制狀態列面板內的資料。</span><span class="sxs-lookup"><span data-stu-id="9493c-116">Explains how to programmatically control the data within status-bar panels.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9493c-117">參考資料</span><span class="sxs-lookup"><span data-stu-id="9493c-117">Reference</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <span data-ttu-id="9493c-118">提供這個類別及其成員的相關參考資訊。</span><span class="sxs-lookup"><span data-stu-id="9493c-118">Provides reference information on the class and its members.</span></span>  
  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <span data-ttu-id="9493c-119">會取代並且將功能加入<xref:System.Windows.Forms.StatusBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="9493c-119">Replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9493c-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="9493c-120">Related Sections</span></span>  
 [<span data-ttu-id="9493c-121">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="9493c-121">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="9493c-122">提供 Windows Form 控制項的完整清單，以及其用法的資訊連結。</span><span class="sxs-lookup"><span data-stu-id="9493c-122">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
