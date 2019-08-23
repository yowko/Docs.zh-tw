---
title: 作法：設定狀態列面板的大小
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- StatusBar control [Windows Forms], panel size
- status bars [Windows Forms], setting panel size
- panels [Windows Forms], setting size in status bars
ms.assetid: a01bee43-d9eb-4954-84e6-45a93532d08d
ms.openlocfilehash: 4ba0f7f02b548a5d9ea1a99605a668f449b3e4a9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923631"
---
# <a name="how-to-set-the-size-of-status-bar-panels"></a><span data-ttu-id="1f63c-102">作法：設定狀態列面板的大小</span><span class="sxs-lookup"><span data-stu-id="1f63c-102">How to: Set the Size of Status-Bar Panels</span></span>
> [!NOTE]
> <span data-ttu-id="1f63c-103"><xref:System.Windows.Forms.ToolStripStatusLabel> 控制項會取代 <xref:System.Windows.Forms.StatusBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.StatusBar> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="1f63c-103">The <xref:System.Windows.Forms.ToolStripStatusLabel> control replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control; however, the <xref:System.Windows.Forms.StatusBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="1f63c-104">[狀態列控制項](statusbar-control-windows-forms.md)控制項內<xref:System.Windows.Forms.StatusBarPanel>類別的每個實例都有一些動態屬性, 可決定其在執行時間的寬度和調整大小行為。</span><span class="sxs-lookup"><span data-stu-id="1f63c-104">Each instance of the <xref:System.Windows.Forms.StatusBarPanel> class within a [StatusBar Control](statusbar-control-windows-forms.md) control has a number of dynamic properties that determine its width and resize behavior at run time.</span></span>  
  
### <a name="to-set-the-size-of-a-panel"></a><span data-ttu-id="1f63c-105">若要設定面板的大小</span><span class="sxs-lookup"><span data-stu-id="1f63c-105">To set the size of a panel</span></span>  
  
1. <span data-ttu-id="1f63c-106">在程式中, 使用透過<xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A> <xref:System.Windows.Forms.StatusBarPanel>集合<xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>的<xref:System.Windows.Forms.StatusBar.Panels%2A>屬性<xref:System.Windows.Forms.StatusBarPanel.Width%2A>傳遞的索引, 為狀態列面板設定、和屬性 (或其中的任何子集)。</span><span class="sxs-lookup"><span data-stu-id="1f63c-106">In a procedure, set the <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>, <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>, and <xref:System.Windows.Forms.StatusBarPanel.Width%2A> properties (or any subset therein) for the status-bar panels using their index passed through the <xref:System.Windows.Forms.StatusBar.Panels%2A> property of the <xref:System.Windows.Forms.StatusBarPanel> collection.</span></span>  
  
    ```vb  
    Public Sub SetStatusBarPanelSize()  
    ' Create panel and set text property.  
       StatusBar1.Panels.Add("One")  
    ' Set properties of panels.  
       StatusBar1.Panels(0).AutoSize = StatusBarPanelAutoSize.Spring  
       StatusBar1.Panels(0).Width = 200  
    ' Enable the StatusBar control to display panels.  
       StatusBar1.ShowPanels = True  
        End Sub  
    ```  
  
    ```csharp  
    public void SetStatusBarPanelSize()  
    {  
       // Create panel and set text property.  
       statusBar1.Panels.Add("One");  
       // Set properties of panels.  
       statusBar1.Panels[0].AutoSize = StatusBarPanelAutoSize.Spring;  
       statusBar1.Panels[0].Width = 200;  
       statusBar1.ShowPanels = true;  
    }  
    ```  
  
    ```cpp  
    public:  
       void SetStatusBarPanelSize()  
       {  
          // Create panel and set text property.  
          statusBar1->Panels->Add("One");  
          // Set properties of panels.  
          statusBar1->Panels[0]->AutoSize =  
             StatusBarPanelAutoSize::Spring;  
          statusBar1->Panels[0]->Width = 200;  
          statusBar1->ShowPanels = true;  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1f63c-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f63c-107">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="1f63c-108">逐步解說：在執行時間更新狀態列資訊</span><span class="sxs-lookup"><span data-stu-id="1f63c-108">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)
- [<span data-ttu-id="1f63c-109">如何：判斷按一下 Windows Forms 狀態列控制項中的哪一個面板</span><span class="sxs-lookup"><span data-stu-id="1f63c-109">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [<span data-ttu-id="1f63c-110">StatusBar 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="1f63c-110">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)
