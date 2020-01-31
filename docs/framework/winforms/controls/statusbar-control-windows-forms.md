---
title: StatusBar 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- StatusBar control [Windows Forms]
- status bars [Windows Forms], creating
ms.assetid: 6f543e27-cf78-4b7f-b4d0-6a8030155d48
ms.openlocfilehash: 4d48cf497eeedcff6290dfa8ddecf38ce8ff7c63
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742858"
---
# <a name="statusbar-control-windows-forms"></a><span data-ttu-id="fa08b-102">StatusBar 控制項 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="fa08b-102">StatusBar Control (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="fa08b-103"><xref:System.Windows.Forms.ToolStripStatusLabel> 控制項會取代 <xref:System.Windows.Forms.StatusBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.StatusBar> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="fa08b-103">The <xref:System.Windows.Forms.ToolStripStatusLabel> control replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control; however, the <xref:System.Windows.Forms.StatusBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="fa08b-104">Windows Form <xref:System.Windows.Forms.StatusBar> 控制項在表單裡被當做區域來使用，通常會顯示在視窗底部，在其中應用程式可以顯示各種狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="fa08b-104">The Windows Forms <xref:System.Windows.Forms.StatusBar> control is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="fa08b-105"><xref:System.Windows.Forms.StatusBar> 控制項可以有狀態列面板，顯示圖示以指示狀態，或是動畫中表示進程正在運作的一系列圖示。例如，表示正在儲存檔的 Microsoft Word。</span><span class="sxs-lookup"><span data-stu-id="fa08b-105"><xref:System.Windows.Forms.StatusBar> controls can have status-bar panels on them that display icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fa08b-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="fa08b-106">In This Section</span></span>  
 [<span data-ttu-id="fa08b-107">StatusBar 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="fa08b-107">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)  
 <span data-ttu-id="fa08b-108">介紹 <xref:System.Windows.Forms.StatusBar> 控制項的一般概念，可讓使用者查看具有焦點之控制項的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fa08b-108">Introduces the general concepts of the <xref:System.Windows.Forms.StatusBar> control, which enables users to see relevant information for the control that has focus.</span></span>  
  
 [<span data-ttu-id="fa08b-109">操作說明：將面板新增至 StatusBar 控制項</span><span class="sxs-lookup"><span data-stu-id="fa08b-109">How to: Add Panels to a StatusBar Control</span></span>](how-to-add-panels-to-a-statusbar-control.md)  
 <span data-ttu-id="fa08b-110">說明如何將可程式化的面板新增至 <xref:System.Windows.Forms.StatusBar> 控制項。</span><span class="sxs-lookup"><span data-stu-id="fa08b-110">Explains how to add programmable panels to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="fa08b-111">操作說明：判斷在 Windows Forms StatusBar 控制項中按下的面板</span><span class="sxs-lookup"><span data-stu-id="fa08b-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)  
 <span data-ttu-id="fa08b-112">說明如何處理從 <xref:System.Windows.Forms.StatusBar> 控制項引發 <xref:System.Windows.Forms.Control.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="fa08b-112">Explains how to handle <xref:System.Windows.Forms.Control.Click> events raised from the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="fa08b-113">操作說明：設定狀態列面板的大小</span><span class="sxs-lookup"><span data-stu-id="fa08b-113">How to: Set the Size of Status-Bar Panels</span></span>](how-to-set-the-size-of-status-bar-panels.md)  
 <span data-ttu-id="fa08b-114">提供可在執行時間控制狀態列面板之寬度和調整大小行為的屬性詳細資料。</span><span class="sxs-lookup"><span data-stu-id="fa08b-114">Gives details on the properties that control the width and resize behavior of status-bar panels at run time.</span></span>  
  
 [<span data-ttu-id="fa08b-115">逐步解說：在執行階段更新狀態列資訊</span><span class="sxs-lookup"><span data-stu-id="fa08b-115">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)  
 <span data-ttu-id="fa08b-116">說明如何以程式設計方式控制狀態列面板中的資料。</span><span class="sxs-lookup"><span data-stu-id="fa08b-116">Explains how to programmatically control the data within status-bar panels.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fa08b-117">參考資料</span><span class="sxs-lookup"><span data-stu-id="fa08b-117">Reference</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <span data-ttu-id="fa08b-118">提供這個類別及其成員的相關參考資訊。</span><span class="sxs-lookup"><span data-stu-id="fa08b-118">Provides reference information on the class and its members.</span></span>  
  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <span data-ttu-id="fa08b-119">取代並加入 <xref:System.Windows.Forms.StatusBar> 控制項的功能。</span><span class="sxs-lookup"><span data-stu-id="fa08b-119">Replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fa08b-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="fa08b-120">Related Sections</span></span>  
 [<span data-ttu-id="fa08b-121">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="fa08b-121">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="fa08b-122">提供 Windows Form 控制項的完整清單，以及其用法的資訊連結。</span><span class="sxs-lookup"><span data-stu-id="fa08b-122">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
