---
title: "如何：觸發工具列按鈕的功能表事件 | Microsoft Docs"
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
  - "範例 [Windows Form], 工具列"
  - "ToolBar 控制項 [Windows Form], Click 事件處理常式"
  - "ToolBar 控制項 [Windows Form], 程式碼按鈕 Click 事件"
  - "工具列 [Windows Form], Click 事件處理常式"
ms.assetid: 98374f70-993d-4ca4-89fb-48fea6ce5b45
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：觸發工具列按鈕的功能表事件
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> 控制項會取代 <xref:System.Windows.Forms.ToolBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ToolBar> 控制項，以提供回溯相容性及未來使用。  
  
 如果您的 Windows Form 具備內含幾個工具列按鈕的 <xref:System.Windows.Forms.ToolBar> 控制項，您會需要知道使用者按的是哪一個按鈕。  
  
 在 <xref:System.Windows.Forms.ToolBar> 控制項的 <xref:System.Windows.Forms.ToolBar.ButtonClick> 事件中，您可以評估 <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> 類別的 <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> 屬性。  下列範例會顯示訊息方塊，指示所按的按鈕是哪一個。  如需詳細資訊，請參閱 [MessageBox 類別](frlrfSystemWindowsFormsMessageBoxClassTopic)。  
  
 下面的範例假設已將 <xref:System.Windows.Forms.ToolBar> 控制項加入至 Windows Form。  
  
### 若要處理工具列上的 Click 事件  
  
1.  在程序中，將工具列按鈕加入至 <xref:System.Windows.Forms.ToolBar> 控制項。  
  
    ```vb  
    Public Sub ToolBarConfig()  
    ' Instantiate the toolbar buttons, set their Text properties  
    ' and add them to the ToolBar control.  
       ToolBar1.Buttons.Add(New ToolBarButton("One"))  
       ToolBar1.Buttons.Add(New ToolBarButton("Two"))  
       ToolBar1.Buttons.Add(New ToolBarButton("Three"))  
    ' Add the event handler delegate.  
       AddHandler ToolBar1.ButtonClick, AddressOf Me.ToolBar1_ButtonClick  
    End Sub  
  
    ```  
  
    ```csharp  
    public void ToolBarConfig()   
    {  
       toolBar1.Buttons.Add(new ToolBarButton("One"));  
       toolBar1.Buttons.Add(new ToolBarButton("Two"));  
       toolBar1.Buttons.Add(new ToolBarButton("Three"));  
  
       toolBar1.ButtonClick +=   
          new ToolBarButtonClickEventHandler(this.toolBar1_ButtonClick);  
    }  
  
    ```  
  
    ```cpp  
    public:  
       void ToolBarConfig()  
       {  
          toolBar1->Buttons->Add(gcnew ToolBarButton("One"));  
          toolBar1->Buttons->Add(gcnew ToolBarButton("Two"));  
          toolBar1->Buttons->Add(gcnew ToolBarButton("Three"));  
  
          toolBar1->ButtonClick +=   
             gcnew ToolBarButtonClickEventHandler(this,  
             &Form1::toolBar1_ButtonClick);  
       }  
    ```  
  
2.  為 <xref:System.Windows.Forms.ToolBar> 控制項的 <xref:System.Windows.Forms.ToolBar.ButtonClick> 事件加入事件處理常式。  使用 case switching 陳述式和 <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> 類別來判斷所按的工具列按鈕是哪一個。  根據結果顯示適當的訊息方塊。  
  
    > [!NOTE]
    >  訊息方塊在這個範例中只是當做預留位置使用。  請依需要加入按下工具列按鈕時要執行的其他程式碼。  
  
    ```vb  
    Protected Sub ToolBar1_ButtonClick(ByVal sender As Object, _  
    ByVal e As ToolBarButtonClickEventArgs)  
    ' Evaluate the Button property of the ToolBarButtonClickEventArgs  
    ' to determine which button was clicked.  
       Select Case ToolBar1.Buttons.IndexOf(e.Button)  
         Case 0  
           MessageBox.Show("First toolbar button clicked")  
         Case 1  
           MessageBox.Show("Second toolbar button clicked")  
         Case 2  
           MessageBox.Show("Third toolbar button clicked")  
       End Select  
    End Sub  
  
    ```  
  
    ```csharp  
    protected void toolBar1_ButtonClick(object sender,  
    ToolBarButtonClickEventArgs e)  
    {  
       // Evaluate the Button property of the ToolBarButtonClickEventArgs  
       // to determine which button was clicked.  
       switch (toolBar1.Buttons.IndexOf(e.Button))  
       {  
          case 0 :  
             MessageBox.Show("First toolbar button clicked");  
             break;  
          case 1 :  
             MessageBox.Show("Second toolbar button clicked");  
             break;  
          case 2 :  
             MessageBox.Show("Third toolbar button clicked");  
             break;  
       }  
    }  
  
    ```  
  
    ```cpp  
    protected:  
       void toolBar1_ButtonClick(System::Object ^ sender,  
          ToolBarButtonClickEventArgs ^ e)  
       {  
         // Evaluate the Button property of the ToolBarButtonClickEventArgs  
         // to determine which button was clicked.  
          switch (toolBar1->Buttons->IndexOf(e->Button))  
          {  
             case 0 :  
                MessageBox::Show("First toolbar button clicked");  
                break;  
             case 1 :  
                MessageBox::Show("Second toolbar button clicked");  
                break;  
             case 2 :  
                MessageBox::Show("Third toolbar button clicked");  
                break;  
          }  
       }  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.ToolBar>   
 [如何：將按鈕加入至 ToolBar 控制項](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)   
 [如何：定義工具列按鈕的圖示](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)   
 [ToolBar 控制項](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)