---
title: "StatusBar 控制項 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- StatusBar control [Windows Forms]
- status bars [Windows Forms], creating
ms.assetid: 6f543e27-cf78-4b7f-b4d0-6a8030155d48
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 945d9a658dd3d75dd0edb9f4eaca78334ee4d652
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="statusbar-control-windows-forms"></a><span data-ttu-id="812fc-102">StatusBar 控制項 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="812fc-102">StatusBar Control (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="812fc-103"><xref:System.Windows.Forms.ToolStripStatusLabel> 控制項會取代 <xref:System.Windows.Forms.StatusBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.StatusBar> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="812fc-103">The <xref:System.Windows.Forms.ToolStripStatusLabel> control replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control; however, the <xref:System.Windows.Forms.StatusBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="812fc-104">Windows Form <xref:System.Windows.Forms.StatusBar> 控制項在表單裡被當做區域來使用，通常會顯示在視窗底部，在其中應用程式可以顯示各種狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="812fc-104">The Windows Forms <xref:System.Windows.Forms.StatusBar> control is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="812fc-105"><xref:System.Windows.Forms.StatusBar>控制項可以有顯示圖示，表示狀態或一系列的動畫圖示，以指出程序運作; 的狀態列面板上例如，指出此問題的 Microsoft Word 文件正在儲存。</span><span class="sxs-lookup"><span data-stu-id="812fc-105"><xref:System.Windows.Forms.StatusBar> controls can have status-bar panels on them that display icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="812fc-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="812fc-106">In This Section</span></span>  
 [<span data-ttu-id="812fc-107">StatusBar 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="812fc-107">StatusBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)  
 <span data-ttu-id="812fc-108">導入的一般概念<xref:System.Windows.Forms.StatusBar>控制項，讓使用者查看具有焦點的控制項的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="812fc-108">Introduces the general concepts of the <xref:System.Windows.Forms.StatusBar> control, which enables users to see relevant information for the control that has focus.</span></span>  
  
 [<span data-ttu-id="812fc-109">操作說明：將面板新增至 StatusBar 控制項</span><span class="sxs-lookup"><span data-stu-id="812fc-109">How to: Add Panels to a StatusBar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)  
 <span data-ttu-id="812fc-110">說明如何將可程式化的面板加入<xref:System.Windows.Forms.StatusBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="812fc-110">Explains how to add programmable panels to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="812fc-111">操作說明：判斷在 Windows Forms StatusBar 控制項中按下的面板</span><span class="sxs-lookup"><span data-stu-id="812fc-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)  
 <span data-ttu-id="812fc-112">說明如何處理<xref:System.Windows.Forms.Control.Click>事件引發從<xref:System.Windows.Forms.StatusBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="812fc-112">Explains how to handle <xref:System.Windows.Forms.Control.Click> events raised from the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
 [<span data-ttu-id="812fc-113">操作說明：設定狀態列面板的大小</span><span class="sxs-lookup"><span data-stu-id="812fc-113">How to: Set the Size of Status-Bar Panels</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-size-of-status-bar-panels.md)  
 <span data-ttu-id="812fc-114">詳細的屬性來控制寬度，並在執行階段調整大小行為的狀態列面板。</span><span class="sxs-lookup"><span data-stu-id="812fc-114">Gives details on the properties that control the width and resize behavior of status-bar panels at run time.</span></span>  
  
 [<span data-ttu-id="812fc-115">逐步解說：在執行階段更新狀態列資訊</span><span class="sxs-lookup"><span data-stu-id="812fc-115">Walkthrough: Updating Status Bar Information at Run Time</span></span>](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)  
 <span data-ttu-id="812fc-116">說明如何以程式設計方式控制狀態列面板內的資料。</span><span class="sxs-lookup"><span data-stu-id="812fc-116">Explains how to programmatically control the data within status-bar panels.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="812fc-117">參考資料</span><span class="sxs-lookup"><span data-stu-id="812fc-117">Reference</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <span data-ttu-id="812fc-118">提供這個類別及其成員的相關參考資訊。</span><span class="sxs-lookup"><span data-stu-id="812fc-118">Provides reference information on the class and its members.</span></span>  
  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <span data-ttu-id="812fc-119">取代，並將功能加入<xref:System.Windows.Forms.StatusBar>控制項。</span><span class="sxs-lookup"><span data-stu-id="812fc-119">Replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="812fc-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="812fc-120">Related Sections</span></span>  
 [<span data-ttu-id="812fc-121">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="812fc-121">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="812fc-122">提供 Windows Form 控制項的完整清單，以及其用法的資訊連結。</span><span class="sxs-lookup"><span data-stu-id="812fc-122">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
