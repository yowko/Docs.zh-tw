---
title: HOW TO：設定狀態列面板的大小
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
ms.openlocfilehash: efd3074aaf018e7226c484061cbacb2eac0be820
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311899"
---
# <a name="how-to-set-the-size-of-status-bar-panels"></a><span data-ttu-id="2251d-102">HOW TO：設定狀態列面板的大小</span><span class="sxs-lookup"><span data-stu-id="2251d-102">How to: Set the Size of Status-Bar Panels</span></span>
> [!NOTE]
>  <span data-ttu-id="2251d-103"><xref:System.Windows.Forms.ToolStripStatusLabel> 控制項會取代 <xref:System.Windows.Forms.StatusBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.StatusBar> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="2251d-103">The <xref:System.Windows.Forms.ToolStripStatusLabel> control replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control; however, the <xref:System.Windows.Forms.StatusBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="2251d-104">每個執行個體<xref:System.Windows.Forms.StatusBarPanel>類別內[StatusBar 控制項](statusbar-control-windows-forms.md)控制項有許多動態屬性，以決定其寬度和調整大小行為，在執行階段。</span><span class="sxs-lookup"><span data-stu-id="2251d-104">Each instance of the <xref:System.Windows.Forms.StatusBarPanel> class within a [StatusBar Control](statusbar-control-windows-forms.md) control has a number of dynamic properties that determine its width and resize behavior at run time.</span></span>  
  
### <a name="to-set-the-size-of-a-panel"></a><span data-ttu-id="2251d-105">若要設定的面板大小</span><span class="sxs-lookup"><span data-stu-id="2251d-105">To set the size of a panel</span></span>  
  
1. <span data-ttu-id="2251d-106">在程序，設定<xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>， <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>，並<xref:System.Windows.Forms.StatusBarPanel.Width%2A>屬性 (或任何子集其中) 的狀態列面板使用其索引則是透過傳遞<xref:System.Windows.Forms.StatusBar.Panels%2A>屬性<xref:System.Windows.Forms.StatusBarPanel>集合。</span><span class="sxs-lookup"><span data-stu-id="2251d-106">In a procedure, set the <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>, <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>, and <xref:System.Windows.Forms.StatusBarPanel.Width%2A> properties (or any subset therein) for the status-bar panels using their index passed through the <xref:System.Windows.Forms.StatusBar.Panels%2A> property of the <xref:System.Windows.Forms.StatusBarPanel> collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2251d-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2251d-107">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="2251d-108">逐步解說：在執行階段更新狀態列資訊</span><span class="sxs-lookup"><span data-stu-id="2251d-108">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)
- [<span data-ttu-id="2251d-109">HOW TO：判斷在 Windows Forms StatusBar 控制項中按下了哪個面板</span><span class="sxs-lookup"><span data-stu-id="2251d-109">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [<span data-ttu-id="2251d-110">StatusBar 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="2251d-110">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)
