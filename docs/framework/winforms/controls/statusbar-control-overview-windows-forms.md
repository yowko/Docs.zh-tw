---
title: StatusBar 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: 6dd5b45b38ec4fb04d9a53a1648cfe6e5a5b9f20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535125"
---
# <a name="statusbar-control-overview-windows-forms"></a><span data-ttu-id="89081-102">StatusBar 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="89081-102">StatusBar Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="89081-103"><xref:System.Windows.Forms.StatusStrip>和<xref:System.Windows.Forms.ToolStripStatusLabel>控制項取代，並將功能加入至<xref:System.Windows.Forms.StatusBar>和<xref:System.Windows.Forms.StatusBarPanel>控制項，不過，<xref:System.Windows.Forms.StatusBar>和<xref:System.Windows.Forms.StatusBarPanel>控制項是被保留為回溯相容性及未來使用，如果您選擇。</span><span class="sxs-lookup"><span data-stu-id="89081-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="89081-104">Windows Form [StatusBar 控制項](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md)可在表單區域的區域，通常會顯示在視窗中，在其中應用程式可以顯示各種狀態資訊的底部。</span><span class="sxs-lookup"><span data-stu-id="89081-104">The Windows Forms [StatusBar Control](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="89081-105"><xref:System.Windows.Forms.StatusBar> 控制項可以有狀態列面板上顯示文字或圖示以表示狀態或一系列的動畫圖示，以指出程序可以運作。例如，[!INCLUDE[ofprword](../../../../includes/ofprword-md.md)]表示正在儲存文件。</span><span class="sxs-lookup"><span data-stu-id="89081-105"><xref:System.Windows.Forms.StatusBar> controls can have status bar panels on them that display text or icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] indicating that the document is being saved.</span></span>  
  
## <a name="using-the-statusbar-control"></a><span data-ttu-id="89081-106">使用 StatusBar 控制項</span><span class="sxs-lookup"><span data-stu-id="89081-106">Using the StatusBar Control</span></span>  
 <span data-ttu-id="89081-107">Internet Explorer 使用狀態列表示網頁的 URL，當滑鼠彙總超連結。[!INCLUDE[ofprword](../../../../includes/ofprword-md.md)]提供您資訊頁面的位置、 區段位置，以及編輯模式，例如取代和追蹤修訂; 和 Visual Studio 會使用狀態列讓內容相關資訊，例如告訴您如何管理可停駐視窗為停駐或浮動。</span><span class="sxs-lookup"><span data-stu-id="89081-107">Internet Explorer uses a status bar to indicate the URL of a page when the mouse rolls over the hyperlink; [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] gives you information on page location, section location, and editing modes such as overtype and revision tracking; and Visual Studio uses the status bar to give context-sensitive information, such as telling you how to manipulate dockable windows as either docked or floating.</span></span>  
  
 <span data-ttu-id="89081-108">您可以藉由設定 [狀態] 列上顯示單一訊息<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>屬性`false`（預設值） 和設定<xref:System.Windows.Forms.StatusBar.Text%2A>至您想要顯示在狀態列中文字的 [狀態] 列的屬性。</span><span class="sxs-lookup"><span data-stu-id="89081-108">You can display a single message on the status bar by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `false` (the default) and setting the <xref:System.Windows.Forms.StatusBar.Text%2A> property of the status bar to the text you want to appear in the status bar.</span></span> <span data-ttu-id="89081-109">[狀態] 列分成面板，以顯示多種類型的資訊，藉由設定<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>屬性`true`和使用<xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A>方法<xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>。</span><span class="sxs-lookup"><span data-stu-id="89081-109">You can divide the status bar into panels to display more than one type of information by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true` and using the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> method of <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89081-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89081-110">See Also</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [<span data-ttu-id="89081-111">操作說明：判斷在 Windows Forms StatusBar 控制項中按下的面板</span><span class="sxs-lookup"><span data-stu-id="89081-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)
