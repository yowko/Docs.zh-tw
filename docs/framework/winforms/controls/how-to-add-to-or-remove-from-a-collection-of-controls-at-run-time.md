---
title: 作法：在執行階段於控制項集合中新增或移除
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- run time [Windows Forms], removing controls
- controls [Windows Forms], adding using collections
- controls collections
- collections [Windows Forms], adding items
- run time [Windows Forms], adding controls
- controls [Windows Forms], removing using collections
ms.assetid: 771bf895-3d5f-469b-a324-3528f343657e
ms.openlocfilehash: 87ad4c957ac5b99438684d398a0c5ad7d126c406
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925036"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a>HOW TO：在執行階段於控制項集合中新增或移除
應用程式開發的一般工作, 是將控制項加入至表單上的任何容器控制項, 並從中移除<xref:System.Windows.Forms.Panel>控制項<xref:System.Windows.Forms.GroupBox> (例如或控制項, 甚至是表單本身)。 在設計階段，可以將控制項直接拖曳至面板或群組方塊。 在執行階段，這些控制項會維護 `Controls` 集合，以便持續追蹤有哪些控制項置於其上。  
  
> [!NOTE]
> 下列程式碼範例適用於任何可維護內含控制項集合的控制項。  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a>以程式設計方式將控制項新增至集合  
  
1. 建立要新增之控制項的執行個體。  
  
2. 設定新控制項的屬性。  
  
3. 將控制項新增至父控制項的 `Controls` 集合。  
  
     下列程式碼範例顯示如何建立<xref:System.Windows.Forms.Button>控制項的實例。 它需要具有<xref:System.Windows.Forms.Panel>控制項的表單, 而且所`NewPanelButton_Click`建立之按鈕的事件處理方法已經存在。  
  
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
       // below is used as an example. Substitute the appropriate event  
       // handler for your application.  
       this.newPanelButton.Click += new System.EventHandler(this. NewPanelButton_Click);  
    }  
    ```  
  
### <a name="to-remove-controls-from-a-collection-programmatically"></a>以程式設計方式移除集合中的控制項  
  
1. 移除事件的事件處理常式。 在 Visual Basic 中, 使用[RemoveHandler 語句](../../../visual-basic/language-reference/statements/removehandler-statement.md)關鍵字;在C#中, 使用[-= 運算子](../../../csharp/language-reference/operators/subtraction-operator.md)。  
  
2. 使用 `Remove` 方法，從面板的 `Controls` 集合中刪除所需控制項。  
  
3. <xref:System.Windows.Forms.Control.Dispose%2A>呼叫方法以釋放控制項所使用的所有資源。  
  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Panel>
- [Panel 控制項](panel-control-windows-forms.md)
