---
title: 如何：啟用 Windows Form RichTextBox 控制項的拖放作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], text boxes
- drag and drop [Windows Forms], richTextBox control
- text boxes [Windows Forms], drag-and-drop operations
- RichTextBox control [Windows Forms], drag-and-drop operations
ms.assetid: ca167d1c-2014-4cf0-96a0-20598470be3b
ms.openlocfilehash: 3adafd9b821dd9366a3ad5080154ab7eb5a2d2f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-drag-and-drop-operations-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="411cb-102">如何：啟用 Windows Form RichTextBox 控制項的拖放作業</span><span class="sxs-lookup"><span data-stu-id="411cb-102">How to: Enable Drag-and-Drop Operations with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="411cb-103">使用 Windows Forms <xref:System.Windows.Forms.RichTextBox> 控制項的拖放作業，可藉由處理 <xref:System.Windows.Forms.RichTextBox.DragEnter> 和 <xref:System.Windows.Forms.RichTextBox.DragDrop> 事件來完成。</span><span class="sxs-lookup"><span data-stu-id="411cb-103">Drag-and-drop operations with the Windows Forms <xref:System.Windows.Forms.RichTextBox> control are done by handling the <xref:System.Windows.Forms.RichTextBox.DragEnter> and <xref:System.Windows.Forms.RichTextBox.DragDrop> events.</span></span> <span data-ttu-id="411cb-104">因此，使用 <xref:System.Windows.Forms.RichTextBox> 控制項進行拖放作業相當簡單。</span><span class="sxs-lookup"><span data-stu-id="411cb-104">Thus, drag-and-drop operations are extremely simple with the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
### <a name="to-enable-drag-operations-in-a-richtextbox-control"></a><span data-ttu-id="411cb-105">在 RichTextBox 控制項中啟用拖曳作業</span><span class="sxs-lookup"><span data-stu-id="411cb-105">To enable drag operations in a RichTextBox control</span></span>  
  
1.  <span data-ttu-id="411cb-106">將 <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> 控制項的 <xref:System.Windows.Forms.RichTextBox> 屬性設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="411cb-106">Set the <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> property of the <xref:System.Windows.Forms.RichTextBox> control to `true`.</span></span>  
  
2.  <span data-ttu-id="411cb-107">在 <xref:System.Windows.Forms.RichTextBox.DragEnter> 事件的事件處理常式中撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="411cb-107">Write code in the event handler of the <xref:System.Windows.Forms.RichTextBox.DragEnter> event.</span></span> <span data-ttu-id="411cb-108">使用 `if` 陳述式，以確認拖曳中的資料是屬於可接受的類型 (在此例中為文字)。</span><span class="sxs-lookup"><span data-stu-id="411cb-108">Use an `if` statement to ensure that the data being dragged is of an acceptable type (in this case, text).</span></span> <span data-ttu-id="411cb-109"><xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> 屬性可以設定為 <xref:System.Windows.Forms.DragDropEffects> 列舉的任何值。</span><span class="sxs-lookup"><span data-stu-id="411cb-109">The <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> property can be set to any value of the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span>  
  
    ```vb  
    Private Sub RichTextBox1_DragEnter(ByVal sender As Object, _   
       ByVal e As System.Windows.Forms.DragEventArgs) _   
       Handles RichTextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
          e.Effect = DragDropEffects.Copy  
       Else  
          e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void richTextBox1_DragEnter(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))   
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    ```cpp  
    private:  
       void richTextBox1_DragEnter(System::Object ^  sender,  
          System::Windows::Forms::DragEventArgs ^  e)  
       {  
          if (e->Data->GetDataPresent(DataFormats::Text))  
             e->Effect = DragDropEffects::Copy;  
          else  
             e->Effect = DragDropEffects::None;  
       }  
    ```  
  
     <span data-ttu-id="411cb-110">(Visual C# 和[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="411cb-110">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.richTextBox1.DragEnter += new  
        System.Windows.Forms.DragEventHandler  
        (this.richTextBox1_DragEnter);  
    ```  
  
    ```cpp  
    this->richTextBox1->DragEnter += gcnew  
       System::Windows::Forms::DragEventHandler  
       (this, &Form1::richTextBox1_DragEnter);  
    ```  
  
3.  <span data-ttu-id="411cb-111">撰寫程式碼來處理 <xref:System.Windows.Forms.RichTextBox.DragDrop> 事件。</span><span class="sxs-lookup"><span data-stu-id="411cb-111">Write code to handle the <xref:System.Windows.Forms.RichTextBox.DragDrop> event.</span></span> <span data-ttu-id="411cb-112">使用 <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> 方法來擷取正在拖曳的資料。</span><span class="sxs-lookup"><span data-stu-id="411cb-112">Use the <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> method to retrieve the data being dragged.</span></span>  
  
     <span data-ttu-id="411cb-113">在以下範例中，程式碼會將 <xref:System.Windows.Forms.RichTextBox.Text%2A> 控制項的 <xref:System.Windows.Forms.RichTextBox> 屬性設為等於正在拖曳的資料。</span><span class="sxs-lookup"><span data-stu-id="411cb-113">In the example below, the code sets the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control equal to the data being dragged.</span></span> <span data-ttu-id="411cb-114">如果 <xref:System.Windows.Forms.RichTextBox> 控制項中已有文字，拖曳的文字會插入在插入點。</span><span class="sxs-lookup"><span data-stu-id="411cb-114">If there is already text in the <xref:System.Windows.Forms.RichTextBox> control, the dragged text is inserted at the insertion point.</span></span>  
  
    ```vb  
    Private Sub RichTextBox1_DragDrop(ByVal sender As Object, _   
       ByVal e As System.Windows.Forms.DragEventArgs) _   
       Handles RichTextBox1.DragDrop  
       Dim i As Int16   
       Dim s As String  
  
       ' Get start position to drop the text.  
       i = RichTextBox1.SelectionStart  
       s = RichTextBox1.Text.Substring(i)  
       RichTextBox1.Text = RichTextBox1.Text.Substring(0, i)  
  
       ' Drop the text on to the RichTextBox.  
       RichTextBox1.Text = RichTextBox1.Text + _  
          e.Data.GetData(DataFormats.Text).ToString()  
       RichTextBox1.Text = RichTextBox1.Text + s  
    End Sub  
    ```  
  
    ```csharp  
    private void richTextBox1_DragDrop(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       int i;  
       String s;  
  
       // Get start position to drop the text.  
       i = richTextBox1.SelectionStart;  
       s = richTextBox1.Text.Substring(i);  
       richTextBox1.Text = richTextBox1.Text.Substring(0,i);  
  
       // Drop the text on to the RichTextBox.  
       richTextBox1.Text = richTextBox1.Text +   
          e.Data.GetData(DataFormats.Text).ToString();  
       richTextBox1.Text = richTextBox1.Text + s;  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void richTextBox1_DragDrop(System::Object ^  sender,  
          System::Windows::Forms::DragEventArgs ^  e)  
       {  
          int i;  
          String ^s;  
  
       // Get start position to drop the text.  
       i = richTextBox1->SelectionStart;  
       s = richTextBox1->Text->Substring(i);  
       richTextBox1->Text = richTextBox1->Text->Substring(0,i);  
  
       // Drop the text on to the RichTextBox.  
       String ^str = String::Concat(richTextBox1->Text, e->Data  
       ->GetData(DataFormats->Text)->ToString());   
       richTextBox1->Text = String::Concat(str, s);  
       }  
    ```  
  
     <span data-ttu-id="411cb-115">(Visual C# 和[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="411cb-115">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.richTextBox1.DragDrop += new  
        System.Windows.Forms.DragEventHandler  
        (this.richTextBox1_DragDrop);  
    ```  
  
    ```cpp  
    this->richTextBox1->DragDrop += gcnew   
       System::Windows::Forms::DragEventHandler  
       (this, &Form1::richTextBox1_DragDrop);  
    ```  
  
### <a name="to-test-the-drag-and-drop-functionality-in-your-application"></a><span data-ttu-id="411cb-116">測試應用程式中的拖放功能</span><span class="sxs-lookup"><span data-stu-id="411cb-116">To test the drag-and-drop functionality in your application</span></span>  
  
1.  <span data-ttu-id="411cb-117">儲存並建置您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="411cb-117">Save and build your application.</span></span> <span data-ttu-id="411cb-118">在執行時，執行 WordPad。</span><span class="sxs-lookup"><span data-stu-id="411cb-118">While it is running, run WordPad.</span></span>  
  
     <span data-ttu-id="411cb-119">WordPad 是由允許拖放作業之 Windows 所安裝的文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="411cb-119">WordPad is a text editor installed by Windows that allows drag-and-drop operations.</span></span> <span data-ttu-id="411cb-120">存取方式是按一下 [開始]  按鈕、選取 [執行] ，然後在 [執行] `WordPad`**對話方塊中的文字方塊中輸入** 並按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="411cb-120">It is accessible by clicking the **Start** button, selecting **Run**, typing `WordPad` in the text box of the **Run** dialog box, and then clicking **OK**.</span></span>  
  
2.  <span data-ttu-id="411cb-121">一旦開啟 WordPad，請於其中輸入文字的字串。</span><span class="sxs-lookup"><span data-stu-id="411cb-121">Once WordPad is open, type a string of text in it.</span></span> <span data-ttu-id="411cb-122">使用滑鼠、選取文字，然後再將選取的文字拖曳到 Windows 應用程式中的 <xref:System.Windows.Forms.RichTextBox> 控制項。</span><span class="sxs-lookup"><span data-stu-id="411cb-122">Using the mouse, select the text, and then drag the selected text over to the <xref:System.Windows.Forms.RichTextBox> control in your Windows application.</span></span>  
  
     <span data-ttu-id="411cb-123">請注意，當滑鼠指向 <xref:System.Windows.Forms.RichTextBox> 控制項 (然後因此引發 <xref:System.Windows.Forms.RichTextBox.DragEnter> 事件) 時，滑鼠指標會變更，且您可以將選取的文字放到 <xref:System.Windows.Forms.RichTextBox> 控制項。</span><span class="sxs-lookup"><span data-stu-id="411cb-123">Notice that when you point the mouse at the <xref:System.Windows.Forms.RichTextBox> control (and, consequently, raise the <xref:System.Windows.Forms.RichTextBox.DragEnter> event), the mouse pointer changes and you can drop the selected text into the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
     <span data-ttu-id="411cb-124">當您放開滑鼠按鈕時，會放下選取的文字 (也就是，會引發 <xref:System.Windows.Forms.RichTextBox.DragDrop> 事件)，並插入 <xref:System.Windows.Forms.RichTextBox> 控制項內。</span><span class="sxs-lookup"><span data-stu-id="411cb-124">When you release the mouse button, the selected text is dropped (that is, the <xref:System.Windows.Forms.RichTextBox.DragDrop> event is raised) and is inserted within the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="411cb-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="411cb-125">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="411cb-126">操作說明：在應用程式間執行拖放作業</span><span class="sxs-lookup"><span data-stu-id="411cb-126">How to: Perform Drag-and-Drop Operations Between Applications</span></span>](../../../../docs/framework/winforms/advanced/how-to-perform-drag-and-drop-operations-between-applications.md)  
 [<span data-ttu-id="411cb-127">RichTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="411cb-127">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="411cb-128">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="411cb-128">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
