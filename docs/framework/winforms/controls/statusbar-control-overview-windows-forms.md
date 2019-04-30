---
title: StatusBar 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: 5fdefa7d7e7c7ef543f677be7beb61dfee54e077
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009681"
---
# <a name="statusbar-control-overview-windows-forms"></a><span data-ttu-id="b7226-102">StatusBar 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="b7226-102">StatusBar Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="b7226-103"><xref:System.Windows.Forms.StatusStrip>及<xref:System.Windows.Forms.ToolStripStatusLabel>控制項會取代及新增功能<xref:System.Windows.Forms.StatusBar>並<xref:System.Windows.Forms.StatusBarPanel>控制項，不過，<xref:System.Windows.Forms.StatusBar>和<xref:System.Windows.Forms.StatusBarPanel>控制項保留回溯相容性和未來使用，如果您選擇。</span><span class="sxs-lookup"><span data-stu-id="b7226-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="b7226-104">Windows Forms [StatusBar 控制項](statusbar-control-windows-forms.md)可在表單區域的區域，通常會顯示在視窗中，以何種應用程式可以顯示各種狀態資訊的底部。</span><span class="sxs-lookup"><span data-stu-id="b7226-104">The Windows Forms [StatusBar Control](statusbar-control-windows-forms.md) is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="b7226-105"><xref:System.Windows.Forms.StatusBar> 控制項可以有狀態列面板上顯示的文字或圖示以表示狀態或一系列的動畫表示正在處理程序; 的圖示比方說，[!INCLUDE[ofprword](../../../../includes/ofprword-md.md)]表示正在儲存文件。</span><span class="sxs-lookup"><span data-stu-id="b7226-105"><xref:System.Windows.Forms.StatusBar> controls can have status bar panels on them that display text or icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] indicating that the document is being saved.</span></span>  
  
## <a name="using-the-statusbar-control"></a><span data-ttu-id="b7226-106">使用 StatusBar 控制項</span><span class="sxs-lookup"><span data-stu-id="b7226-106">Using the StatusBar Control</span></span>  
 <span data-ttu-id="b7226-107">Internet Explorer 使用狀態列來表示頁面的 URL，當滑鼠跨過超連結;[!INCLUDE[ofprword](../../../../includes/ofprword-md.md)]提供您資訊所在位置、 區段的位置，以及編輯模式，例如取代和修訂追蹤; 和 Visual Studio 的 [狀態] 列則會提供內容相關的資訊，例如告訴您如何操作可停駐視窗使用為停駐或浮動。</span><span class="sxs-lookup"><span data-stu-id="b7226-107">Internet Explorer uses a status bar to indicate the URL of a page when the mouse rolls over the hyperlink; [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] gives you information on page location, section location, and editing modes such as overtype and revision tracking; and Visual Studio uses the status bar to give context-sensitive information, such as telling you how to manipulate dockable windows as either docked or floating.</span></span>  
  
 <span data-ttu-id="b7226-108">您可以在狀態列上顯示的單一訊息，藉由設定<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>屬性，以`false`（預設值） 和設定<xref:System.Windows.Forms.StatusBar.Text%2A>狀態列以您想要出現在狀態列中文字的屬性。</span><span class="sxs-lookup"><span data-stu-id="b7226-108">You can display a single message on the status bar by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `false` (the default) and setting the <xref:System.Windows.Forms.StatusBar.Text%2A> property of the status bar to the text you want to appear in the status bar.</span></span> <span data-ttu-id="b7226-109">您可以將 [狀態] 列分成面板，以藉由設定顯示多個類型的資訊<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>屬性，以`true`並使用<xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A>方法<xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>。</span><span class="sxs-lookup"><span data-stu-id="b7226-109">You can divide the status bar into panels to display more than one type of information by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true` and using the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> method of <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7226-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7226-110">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="b7226-111">如何：判斷按下 Windows Forms StatusBar 控制項中的面板</span><span class="sxs-lookup"><span data-stu-id="b7226-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
