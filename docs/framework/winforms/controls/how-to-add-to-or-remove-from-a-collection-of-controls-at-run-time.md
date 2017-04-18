---
title: "如何：在執行階段時從控制項集合加入或移除 | Microsoft Docs"
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
  - "集合, 加入項目"
  - "控制項 [Windows Form], 使用集合加入"
  - "控制項 [Windows Form], 使用集合移除"
  - "控制項集合"
  - "執行階段, 加入控制項"
  - "執行階段, 移除控制項"
ms.assetid: 771bf895-3d5f-469b-a324-3528f343657e
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：在執行階段時從控制項集合加入或移除
應用程式開發中常見的工作是，在表單的任何容器控制項 \(例如 <xref:System.Windows.Forms.Panel> 或 <xref:System.Windows.Forms.GroupBox> 控制項，甚至是表單本身\) 中加入和移除控制項。  在設計階段中，可以將控制項直接拖曳到面板或群組方塊上。  在執行階段中，這些控制項會維護 `Controls` 集合，該集合會記錄有哪些控制項置於其上。  
  
> [!NOTE]
>  下列程式碼範例適用於任何維護其所包含之控制項集合的控制項。  
  
### 若要以程式設計的方式將控制項加入集合中  
  
1.  建立要加入之控制項的執行個體。  
  
2.  設定新控制項的屬性。  
  
3.  將控制項加入至父控制項的 `Controls` 集合中。  
  
     下列程式碼範例說明如何建立 <xref:System.Windows.Forms.Button> 控制項的執行個體。  它要求表單必須具有 <xref:System.Windows.Forms.Panel> 控制項，而且已具有正在建立之按鈕的事件處理方法 `NewPanelButton_Click`。  
  
    ```vb  
    Public NewPanelButton As New Button()  
  
    Public Sub AddNewControl()  
       ' The Add method will accept as a parameter any object that derives  
       ' from the Control class. In this case, it is a Button control.  
       Panel1.Controls.Add(NewPanelButton)  
       ' The event handler indicated for the Click event in the code   
       ' below is used as an example. Substite the appropriate event  
       ' handler for your application.  
       AddHandler NewPanelButton.Click, AddressOf NewPanelButton_Click  
    End Sub  
  
    ```  
  
    ```csharp  
    public Button newPanelButton = new Button();  
  
    public void addNewControl()  
    {   
       // The Add method will accept as a parameter any object that derives  
       // from the Control class. In this case, it is a Button control.  
       panel1.Controls.Add(newPanelButton);  
       // The event handler indicated for the Click event in the code   
       // below is used as an example. Substite the appropriate event  
       // handler for your application.  
       this.newPanelButton.Click += new System.EventHandler(this. NewPanelButton_Click);  
    }  
    ```  
  
### 若要以程式設計的方式從集合移除控制項  
  
1.  從事件移除事件處理常式。  在 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 中，請使用 [RemoveHandler Statement](../../../../ocs/visual-basic/language-reference/statements/removehandler-statement.md) 關鍵字，在 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 中，則是使用 [\-\= 運算子](../Topic/-=%20Operator%20\(C%23%20Reference\)2.md)。  
  
2.  使用 `Remove` 方法，從面板的 `Controls` 集合刪除想要刪除的控制項。  
  
3.  呼叫 <xref:System.Windows.Forms.Control.Dispose%2A> 方法，來釋放控制項使用的所有資源。  
  
    ```vb  
    Public Sub RemoveControl()  
    ' NOTE: The code below uses the instance of   
    ' the button (NewPanelButton) from the previous example.  
       If Panel1.Controls.Contains(NewPanelButton) Then  
          RemoveHandler NewPanelButton.Click, AddressOf _   
             NewPanelButton_Click  
          Panel1.Controls.Remove(NewPanelButton)  
          NewPanelButton.Dispose()  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void removeControl(object sender, System.EventArgs e)  
    {  
    // NOTE: The code below uses the instance of   
    // the button (newPanelButton) from the previous example.  
       if(panel1.Controls.Contains(newPanelButton))  
       {  
          this.newPanelButton.Click -= new System.EventHandler(this.   
             NewPanelButton_Click);  
          panel1.Controls.Remove(newPanelButton);  
          newPanelButton.Dispose();  
       }  
    }  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.Panel>   
 [Panel 控制項](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)