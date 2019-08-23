---
title: StatusBar 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: bd58d4c70e3a3c88e57fe242957f669d1944fd71
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964428"
---
# <a name="statusbar-control-overview-windows-forms"></a><span data-ttu-id="b9b39-102">StatusBar 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="b9b39-102">StatusBar Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="b9b39-103"><xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBarPanel>和控制項會取代和加入和<xref:System.Windows.Forms.StatusBarPanel>控制項的功能; 不過, 如果您這樣做, 和控制項就會保留, 以提供回溯相容性及未來使用。 <xref:System.Windows.Forms.ToolStripStatusLabel> <xref:System.Windows.Forms.StatusStrip>決定.</span><span class="sxs-lookup"><span data-stu-id="b9b39-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="b9b39-104">[Windows Forms[狀態列] 控制項](statusbar-control-windows-forms.md)用於表單上作為區域, 通常會顯示在視窗底部, 應用程式可以在其中顯示各種類型的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="b9b39-104">The Windows Forms [StatusBar Control](statusbar-control-windows-forms.md) is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="b9b39-105"><xref:System.Windows.Forms.StatusBar>控制項可以有狀態列面板, 它們會顯示文字或圖示來表示狀態, 或是動畫中表示進程正在運作的一系列圖示。例如, 表示正在儲存檔的 Microsoft Word。</span><span class="sxs-lookup"><span data-stu-id="b9b39-105"><xref:System.Windows.Forms.StatusBar> controls can have status bar panels on them that display text or icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="using-the-statusbar-control"></a><span data-ttu-id="b9b39-106">使用狀態列控制項</span><span class="sxs-lookup"><span data-stu-id="b9b39-106">Using the StatusBar Control</span></span>  
 <span data-ttu-id="b9b39-107">當滑鼠變換超連結時, Internet Explorer 會使用狀態列來指出頁面的 URL;Microsoft Word 提供頁面位置、區段位置和編輯模式的資訊, 例如改寫和修訂追蹤;和 Visual Studio 會使用狀態列來提供內容相關資訊, 例如, 告訴您如何將可停駐的視窗操作為停駐或浮動。</span><span class="sxs-lookup"><span data-stu-id="b9b39-107">Internet Explorer uses a status bar to indicate the URL of a page when the mouse rolls over the hyperlink; Microsoft Word gives you information on page location, section location, and editing modes such as overtype and revision tracking; and Visual Studio uses the status bar to give context-sensitive information, such as telling you how to manipulate dockable windows as either docked or floating.</span></span>  
  
 <span data-ttu-id="b9b39-108">您可以將<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>屬性設定為`false` ( <xref:System.Windows.Forms.StatusBar.Text%2A>預設值), 並將狀態列的屬性設定為您要在狀態列中顯示的文字, 以在狀態列上顯示單一訊息。</span><span class="sxs-lookup"><span data-stu-id="b9b39-108">You can display a single message on the status bar by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `false` (the default) and setting the <xref:System.Windows.Forms.StatusBar.Text%2A> property of the status bar to the text you want to appear in the status bar.</span></span> <span data-ttu-id="b9b39-109">您<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>可以藉由將屬性設定為`true` <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>, 並使用的<xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A>方法, 將狀態列分割成面板, 以顯示一種以上的資訊。</span><span class="sxs-lookup"><span data-stu-id="b9b39-109">You can divide the status bar into panels to display more than one type of information by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true` and using the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> method of <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9b39-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9b39-110">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="b9b39-111">如何：判斷按一下 Windows Forms 狀態列控制項中的哪一個面板</span><span class="sxs-lookup"><span data-stu-id="b9b39-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
