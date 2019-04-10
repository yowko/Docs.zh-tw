---
title: HOW TO：觸發工具列按鈕的功能表事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], click event handlers
- ToolBar control [Windows Forms], coding button click events
- toolbars [Windows Forms], click event handlers
ms.assetid: 98374f70-993d-4ca4-89fb-48fea6ce5b45
ms.openlocfilehash: 0f5afde1cc0be772baff373c84c82f81df284b9b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303982"
---
# <a name="how-to-trigger-menu-events-for-toolbar-buttons"></a>HOW TO：觸發工具列按鈕的功能表事件
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> 控制項會取代 <xref:System.Windows.Forms.ToolBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ToolBar> 控制項，以提供回溯相容性及未來使用。  
  
 如果您的 Windows Form 功能<xref:System.Windows.Forms.ToolBar>控制項工具列按鈕，您會想要知道的按鈕使用者按。  
  
 在 <xref:System.Windows.Forms.ToolBar.ButtonClick>事件的<xref:System.Windows.Forms.ToolBar>控制項，您可以評估<xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A>屬性<xref:System.Windows.Forms.ToolBarButtonClickEventArgs>類別。 在下列範例中，會顯示訊息方塊，指出所按的按鈕。 如需詳細資訊，請參閱 <xref:System.Windows.Forms.MessageBox>。  
  
 下列範例假設<xref:System.Windows.Forms.ToolBar>控制項已經加入至 Windows 表單。  
  
### <a name="to-handle-the-click-event-on-a-toolbar"></a>處理工具列上的 Click 事件  
  
1. 在程序中，新增工具列按鈕以<xref:System.Windows.Forms.ToolBar>控制項。  
  
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
  
2. 新增事件處理常式<xref:System.Windows.Forms.ToolBar>控制項的<xref:System.Windows.Forms.ToolBar.ButtonClick>事件。 使用案例切換陳述式和<xref:System.Windows.Forms.ToolBarButtonClickEventArgs>類別，以判斷所按下工具列按鈕。 有鑑於此，會顯示適當的訊息方塊。  
  
    > [!NOTE]
    >  在此範例中，訊息方塊僅作為預留位置使用。 依需要新增要在按一下工具列按鈕時執行的其他程式碼。  
  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ToolBar>
- [HOW TO：將按鈕新增至 ToolBar 控制項](how-to-add-buttons-to-a-toolbar-control.md)
- [HOW TO：定義工具列按鈕的圖示](how-to-define-an-icon-for-a-toolbar-button.md)
- [ToolBar 控制項](toolbar-control-windows-forms.md)
