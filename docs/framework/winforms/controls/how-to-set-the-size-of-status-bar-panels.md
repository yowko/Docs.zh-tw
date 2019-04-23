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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311899"
---
# <a name="how-to-set-the-size-of-status-bar-panels"></a>HOW TO：設定狀態列面板的大小
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripStatusLabel> 控制項會取代 <xref:System.Windows.Forms.StatusBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.StatusBar> 控制項，以提供回溯相容性及未來使用。  
  
 每個執行個體<xref:System.Windows.Forms.StatusBarPanel>類別內[StatusBar 控制項](statusbar-control-windows-forms.md)控制項有許多動態屬性，以決定其寬度和調整大小行為，在執行階段。  
  
### <a name="to-set-the-size-of-a-panel"></a>若要設定的面板大小  
  
1. 在程序，設定<xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>， <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>，並<xref:System.Windows.Forms.StatusBarPanel.Width%2A>屬性 (或任何子集其中) 的狀態列面板使用其索引則是透過傳遞<xref:System.Windows.Forms.StatusBar.Panels%2A>屬性<xref:System.Windows.Forms.StatusBarPanel>集合。  
  
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
- [逐步解說：在執行階段更新狀態列資訊](walkthrough-updating-status-bar-information-at-run-time.md)
- [如何：判斷按下 Windows Forms StatusBar 控制項中的面板](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [StatusBar 控制項概觀](statusbar-control-overview-windows-forms.md)
