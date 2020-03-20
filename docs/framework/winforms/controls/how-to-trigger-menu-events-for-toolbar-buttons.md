---
title: 如何：觸發工具列按鈕的功能表事件
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
ms.openlocfilehash: 99db077b41a59fe9263f7283b58b8c31959c7c79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182082"
---
# <a name="how-to-trigger-menu-events-for-toolbar-buttons"></a><span data-ttu-id="76bb4-102">如何：觸發工具列按鈕的功能表事件</span><span class="sxs-lookup"><span data-stu-id="76bb4-102">How to: Trigger Menu Events for Toolbar Buttons</span></span>
> [!NOTE]
> <span data-ttu-id="76bb4-103"><xref:System.Windows.Forms.ToolStrip> 控制項會取代 <xref:System.Windows.Forms.ToolBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ToolBar> 控制項，以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="76bb4-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="76bb4-104">如果您的 Windows 表單具有<xref:System.Windows.Forms.ToolBar>帶有工具列按鈕的控制項，您將想知道使用者按一下哪個按鈕。</span><span class="sxs-lookup"><span data-stu-id="76bb4-104">If your Windows Form features a <xref:System.Windows.Forms.ToolBar> control with toolbar buttons, you will want to know which button the user clicks.</span></span>  
  
 <span data-ttu-id="76bb4-105">在<xref:System.Windows.Forms.ToolBar.ButtonClick><xref:System.Windows.Forms.ToolBar>控制項的事件中，可以評估<xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A><xref:System.Windows.Forms.ToolBarButtonClickEventArgs>類的屬性。</span><span class="sxs-lookup"><span data-stu-id="76bb4-105">On the <xref:System.Windows.Forms.ToolBar.ButtonClick> event of the <xref:System.Windows.Forms.ToolBar> control, you can evaluate the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> property of the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> class.</span></span> <span data-ttu-id="76bb4-106">在下列範例中，會顯示訊息方塊，指出所按的按鈕。</span><span class="sxs-lookup"><span data-stu-id="76bb4-106">In the example below, a message box is shown, indicating which button was clicked.</span></span> <span data-ttu-id="76bb4-107">如需詳細資訊，請參閱<xref:System.Windows.Forms.MessageBox>。</span><span class="sxs-lookup"><span data-stu-id="76bb4-107">For details, see <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="76bb4-108">下面的示例假定控制項<xref:System.Windows.Forms.ToolBar>已添加到 Windows 表單中。</span><span class="sxs-lookup"><span data-stu-id="76bb4-108">The example below assumes a <xref:System.Windows.Forms.ToolBar> control has been added to a Windows Form.</span></span>  
  
### <a name="to-handle-the-click-event-on-a-toolbar"></a><span data-ttu-id="76bb4-109">處理工具列上的 Click 事件</span><span class="sxs-lookup"><span data-stu-id="76bb4-109">To handle the Click event on a toolbar</span></span>  
  
1. <span data-ttu-id="76bb4-110">在此過程中，向<xref:System.Windows.Forms.ToolBar>控制項添加工具列按鈕。</span><span class="sxs-lookup"><span data-stu-id="76bb4-110">In a procedure, add toolbar buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
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
  
2. <span data-ttu-id="76bb4-111">為<xref:System.Windows.Forms.ToolBar>控制項<xref:System.Windows.Forms.ToolBar.ButtonClick>的事件添加事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="76bb4-111">Add an event handler for the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ButtonClick> event.</span></span> <span data-ttu-id="76bb4-112">使用大小寫切換語句和<xref:System.Windows.Forms.ToolBarButtonClickEventArgs>類確定按一下的工具列按鈕。</span><span class="sxs-lookup"><span data-stu-id="76bb4-112">Use a case switching statement and the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> class to determine the toolbar button that was clicked.</span></span> <span data-ttu-id="76bb4-113">有鑑於此，會顯示適當的訊息方塊。</span><span class="sxs-lookup"><span data-stu-id="76bb4-113">Based on this, show an appropriate message box.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="76bb4-114">在此範例中，訊息方塊僅作為預留位置使用。</span><span class="sxs-lookup"><span data-stu-id="76bb4-114">A message box is being used solely as a placeholder in this example.</span></span> <span data-ttu-id="76bb4-115">依需要新增要在按一下工具列按鈕時執行的其他程式碼。</span><span class="sxs-lookup"><span data-stu-id="76bb4-115">Feel free to add other code to execute when the toolbar buttons are clicked.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="76bb4-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76bb4-116">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="76bb4-117">如何：將按鈕新增至 ToolBar 控制項</span><span class="sxs-lookup"><span data-stu-id="76bb4-117">How to: Add Buttons to a ToolBar Control</span></span>](how-to-add-buttons-to-a-toolbar-control.md)
- [<span data-ttu-id="76bb4-118">如何：定義工具列按鈕的圖示</span><span class="sxs-lookup"><span data-stu-id="76bb4-118">How to: Define an Icon for a ToolBar Button</span></span>](how-to-define-an-icon-for-a-toolbar-button.md)
- [<span data-ttu-id="76bb4-119">ToolBar 控制項</span><span class="sxs-lookup"><span data-stu-id="76bb4-119">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
