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
# <a name="how-to-set-the-size-of-status-bar-panels"></a>作法：設定狀態列面板的大小
> [!NOTE]
> <xref:System.Windows.Forms.ToolStripStatusLabel> 控制項會取代 <xref:System.Windows.Forms.StatusBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.StatusBar> 控制項，以提供回溯相容性及未來使用。  
  
 [狀態列控制項](statusbar-control-windows-forms.md)控制項內<xref:System.Windows.Forms.StatusBarPanel>類別的每個實例都有一些動態屬性, 可決定其在執行時間的寬度和調整大小行為。  
  
### <a name="to-set-the-size-of-a-panel"></a>若要設定面板的大小  
  
1. 在程式中, 使用透過<xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A> <xref:System.Windows.Forms.StatusBarPanel>集合<xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>的<xref:System.Windows.Forms.StatusBar.Panels%2A>屬性<xref:System.Windows.Forms.StatusBarPanel.Width%2A>傳遞的索引, 為狀態列面板設定、和屬性 (或其中的任何子集)。  
  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [逐步解說：在執行時間更新狀態列資訊](walkthrough-updating-status-bar-information-at-run-time.md)
- [如何：判斷按一下 Windows Forms 狀態列控制項中的哪一個面板](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [StatusBar 控制項概觀](statusbar-control-overview-windows-forms.md)
