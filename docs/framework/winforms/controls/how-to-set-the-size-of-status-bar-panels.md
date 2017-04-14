---
title: "如何：設定狀態列面板的大小 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "面板, 在狀態列中設定大小"
  - "狀態列, 設定面板大小"
  - "StatusBar 控制項 [Windows Form], 面板大小"
ms.assetid: a01bee43-d9eb-4954-84e6-45a93532d08d
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：設定狀態列面板的大小
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripStatusLabel> 控制項會取代 <xref:System.Windows.Forms.StatusBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.StatusBar> 控制項，以提供回溯相容性及未來使用。  
  
 [StatusBar 控制項](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) 控制項內 <xref:System.Windows.Forms.StatusBarPanel> 類別的每個執行個體都有許多動態屬性，這些屬性決定了該控制項在執行階段中的寬度及調整大小行為。  
  
### 若要設定面板的大小  
  
1.  在程序中，使用透過 <xref:System.Windows.Forms.StatusBarPanel> 集合的 <xref:System.Windows.Forms.StatusBar.Panels%2A> 屬性傳遞的索引，來設定狀態列面板的 <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>、<xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A> 和 <xref:System.Windows.Forms.StatusBarPanel.Width%2A> 屬性 \(或各屬性的任何子集\)。  
  
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
  
## 請參閱  
 <xref:System.Windows.Forms.StatusBar>   
 <xref:System.Windows.Forms.ToolStripStatusLabel>   
 [逐步解說：在執行階段更新狀態列資訊](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)   
 [如何：判斷在 Windows Form StatusBar 控制項中按下的面板](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)   
 [StatusBar 控制項概觀](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)