---
title: 建立多窗格使用者介面
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SplitContainer control [Windows Forms], examples
- ListView control [Windows Forms], examples
- RichTextBox control [Windows Forms], examples
- Panel control [Windows Forms], examples
- TreeView control [Windows Forms], examples
- Splitter control [Windows Forms], examples
ms.assetid: e79f6bcc-3740-4d1e-b46a-c5594d9b7327
ms.openlocfilehash: 4b168a6d566e20814d4403f90e157d80efe3bf12
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731332"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms"></a><span data-ttu-id="3c389-102">如何：利用 Windows Form 建立多窗格使用者介面</span><span class="sxs-lookup"><span data-stu-id="3c389-102">How to: Create a Multipane User Interface with Windows Forms</span></span>
<span data-ttu-id="3c389-103">在下列程式中，您將建立類似于 Microsoft Outlook 中所用的多窗格使用者介面，以及**資料夾**清單、[**訊息**] 窗格和 [**預覽**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="3c389-103">In the following procedure, you will create a multipane user interface that is similar to the one used in Microsoft Outlook, with a **Folder** list, a **Messages** pane, and a **Preview** pane.</span></span> <span data-ttu-id="3c389-104">這種安排是透過將控制項與表單停駐的方式來 chiefly。</span><span class="sxs-lookup"><span data-stu-id="3c389-104">This arrangement is achieved chiefly through docking controls with the form.</span></span>  
  
 <span data-ttu-id="3c389-105">當您停駐控制項時，您會決定控制項已固定的父容器邊緣。</span><span class="sxs-lookup"><span data-stu-id="3c389-105">When you dock a control, you determine which edge of the parent container a control is fastened to.</span></span> <span data-ttu-id="3c389-106">因此，如果您將 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle.Right>，控制項的右邊緣將停駐在其父控制項的右邊緣。</span><span class="sxs-lookup"><span data-stu-id="3c389-106">Thus, if you set the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Right>, the right edge of the control will be docked to the right edge of its parent control.</span></span> <span data-ttu-id="3c389-107">此外，控制項的停駐邊緣也會調整大小，以符合其容器控制項的邊緣。</span><span class="sxs-lookup"><span data-stu-id="3c389-107">Additionally, the docked edge of the control is resized to match that of its container control.</span></span> <span data-ttu-id="3c389-108">如需 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性如何運作的詳細資訊，請參閱[如何：將控制項停駐在 Windows Forms 上](how-to-dock-controls-on-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="3c389-108">For more information about how the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property works, see [How to: Dock Controls on Windows Forms](how-to-dock-controls-on-windows-forms.md).</span></span>  
  
 <span data-ttu-id="3c389-109">這個程式著重于在表單上排列 <xref:System.Windows.Forms.SplitContainer> 和其他控制項，而不是新增功能讓應用程式模擬 Microsoft Outlook。</span><span class="sxs-lookup"><span data-stu-id="3c389-109">This procedure focuses on arranging the <xref:System.Windows.Forms.SplitContainer> and the other controls on the form, not on adding functionality to make the application mimic Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="3c389-110">若要建立這個使用者介面，您可以將所有控制項放在 <xref:System.Windows.Forms.SplitContainer> 控制項內，其中包含左側面板中的 <xref:System.Windows.Forms.TreeView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="3c389-110">To create this user interface, you place all the controls within a <xref:System.Windows.Forms.SplitContainer> control, which contains a <xref:System.Windows.Forms.TreeView> control in the left-hand panel.</span></span> <span data-ttu-id="3c389-111"><xref:System.Windows.Forms.SplitContainer> 控制項的右面板中包含第二個 <xref:System.Windows.Forms.SplitContainer> 控制項，其中具有 <xref:System.Windows.Forms.RichTextBox> 控制項上方的 <xref:System.Windows.Forms.ListView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="3c389-111">The right-hand panel of the <xref:System.Windows.Forms.SplitContainer> control contains a second <xref:System.Windows.Forms.SplitContainer> control with a <xref:System.Windows.Forms.ListView> control above a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="3c389-112">這些 <xref:System.Windows.Forms.SplitContainer> 控制項可讓您在表單上進行其他控制項的獨立調整大小。</span><span class="sxs-lookup"><span data-stu-id="3c389-112">These <xref:System.Windows.Forms.SplitContainer> controls enable independent resizing of the other controls on the form.</span></span> <span data-ttu-id="3c389-113">您可以調整此程式中的技術，以製作您自己的自訂使用者介面。</span><span class="sxs-lookup"><span data-stu-id="3c389-113">You can adapt the techniques in this procedure to craft custom user interfaces of your own.</span></span>  
  
### <a name="to-create-an-outlook-style-user-interface-programmatically"></a><span data-ttu-id="3c389-114">以程式設計方式建立 Outlook 樣式的使用者介面</span><span class="sxs-lookup"><span data-stu-id="3c389-114">To create an Outlook-style user interface programmatically</span></span>  
  
1. <span data-ttu-id="3c389-115">在表單中，宣告組成使用者介面的每個控制項。</span><span class="sxs-lookup"><span data-stu-id="3c389-115">Within a form, declare each control that comprises your user interface.</span></span> <span data-ttu-id="3c389-116">在此範例中，使用 [<xref:System.Windows.Forms.TreeView>]、[<xref:System.Windows.Forms.ListView>]、[<xref:System.Windows.Forms.SplitContainer>] 和 [<xref:System.Windows.Forms.RichTextBox>] 控制項來模擬 Microsoft Outlook 使用者介面。</span><span class="sxs-lookup"><span data-stu-id="3c389-116">For this example, use the <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.SplitContainer>, and <xref:System.Windows.Forms.RichTextBox> controls to mimic the Microsoft Outlook user interface.</span></span>  
  
    ```vb  
    Private WithEvents treeView1 As System.Windows.Forms.TreeView  
    Private WithEvents listView1 As System.Windows.Forms.ListView  
    Private WithEvents richTextBox1 As System.Windows.Forms.RichTextBox  
    Private WithEvents splitContainer1 As _  
        System.Windows.Forms.SplitContainer  
    Private WithEvents splitContainer2 As _  
        System.Windows.Forms.SplitContainer  
    ```  
  
    ```csharp  
    private System.Windows.Forms.TreeView treeView1;  
    private System.Windows.Forms.ListView listView1;  
    private System.Windows.Forms.RichTextBox richTextBox1;  
    private System.Windows.Forms. SplitContainer splitContainer2;  
    private System.Windows.Forms. SplitContainer splitContainer1;  
    ```  
  
2. <span data-ttu-id="3c389-117">建立定義使用者介面的程式。</span><span class="sxs-lookup"><span data-stu-id="3c389-117">Create a procedure that defines your user interface.</span></span> <span data-ttu-id="3c389-118">下列程式碼會設定屬性，讓表單類似 Microsoft Outlook 中的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="3c389-118">The following code sets the properties so that the form will resemble the user interface in Microsoft Outlook.</span></span> <span data-ttu-id="3c389-119">不過，藉由使用其他控制項或以不同的方式將它們停駐，就像建立其他同樣有彈性的使用者介面一樣容易。</span><span class="sxs-lookup"><span data-stu-id="3c389-119">However, by using other controls or docking them differently, it is just as easy to create other user interfaces that are equally flexible.</span></span>  
  
    ```vb  
    Public Sub CreateOutlookUI()  
        ' Create an instance of each control being used.  
        Me.components = New System.ComponentModel.Container()  
        Me.treeView1 = New System.Windows.Forms.TreeView()  
        Me.listView1 = New System.Windows.Forms.ListView()  
        Me.richTextBox1 = New System.Windows.Forms.RichTextBox()  
        Me.splitContainer1 = New System.Windows.Forms.SplitContainer()  
        Me.splitContainer2= New System.Windows.Forms. SplitContainer()  
  
        ' Should you develop this into a working application,  
        ' use the AddHandler method to hook up event procedures here.  
  
        ' Set properties of TreeView control.  
        ' Use the With statement to avoid repetitive code.  
        With Me.treeView1  
            .Dock = System.Windows.Forms.DockStyle.Fill  
            .TabIndex = 0  
            .Nodes.Add("treeView")  
        End With  
  
    ' Set properties of ListView control.  
       With Me.listView1  
          .Dock = System.Windows.Forms.DockStyle.Top  
          .TabIndex = 2  
          .Items.Add("listView")  
       End With  
  
    ' Set properties of RichTextBox control.  
       With Me.richTextBox1  
          .Dock = System.Windows.Forms.DockStyle.Fill  
          .TabIndex = 3  
          .Text = "richTextBox1"  
       End With  
  
        ' Set properties of the first SplitContainer control.  
        With Me.splitContainer1  
            .Dock = System.Windows.Forms.DockStyle.Fill  
            .TabIndex = 1  
            .SplitterWidth = 4  
            .SplitterDistance = 150  
            .Orientation = Orientation.Horizontal  
            .Panel1.Controls.Add(Me.listView1)  
            .Panel2.Controls.Add(Me.richTextBox1)  
    End With  
  
        ' Set properties of the second SplitContainer control.  
        With Me.splitContainer2  
            .Dock = System.Windows.Forms.DockStyle.Fill  
            .TabIndex = 4  
            .SplitterWidth = 4  
            .SplitterDistance = 100  
            .Panel1.Controls.Add(Me.treeView1)  
            .Panel2.Controls.Add(Me.SplitContainer1)  
    End With  
  
    ' Add the main SplitContainer control to the form.  
        Me.Controls.Add(Me.splitContainer2)  
        Me.Text = "Intricate UI Example"  
    End Sub  
    ```  
  
    ```csharp  
    public void createOutlookUI()  
    {  
        // Create an instance of each control being used.  
        treeView1 = new System.Windows.Forms.TreeView();  
        listView1 = new System.Windows.Forms.ListView();  
        richTextBox1 = new System.Windows.Forms.RichTextBox();  
        splitContainer2 = new System.Windows.Forms.SplitContainer();  
        splitContainer1 = new System.Windows.Forms.SplitContainer();  
  
        // Insert code here to hook up event methods.  
  
        // Set properties of TreeView control.  
        treeView1.Dock = System.Windows.Forms.DockStyle.Fill;  
        treeView1.TabIndex = 0;  
        treeView1.Nodes.Add("treeView");  
  
        // Set properties of ListView control.  
        listView1.Dock = System.Windows.Forms.DockStyle.Top;  
        listView1.TabIndex = 2;  
        listView1.Items.Add("listView");  
  
        // Set properties of RichTextBox control.  
        richTextBox1.Dock = System.Windows.Forms.DockStyle.Fill;  
        richTextBox1.TabIndex = 3;  
        richTextBox1.Text = "richTextBox1";  
  
        // Set properties of first SplitContainer control.  
        splitContainer1.Dock = System.Windows.Forms.DockStyle.Fill;  
        splitContainer2.TabIndex = 1;  
        splitContainer2.SplitterWidth = 4;  
        splitContainer2.SplitterDistance = 150;  
        splitContainer2.Orientation = Orientation.Horizontal;  
        splitContainer2.Panel1.Controls.Add(this.listView1);  
        splitContainer2.Panel1.Controls.Add(this.richTextBox1);  
  
        // Set properties of second SplitContainer control.  
        splitContainer2.Dock = System.Windows.Forms.DockStyle.Fill;  
        splitContainer2.TabIndex = 4;  
        splitContainer2.SplitterWidth = 4;  
        splitContainer2.SplitterDistance = 100;  
        splitContainer2.Panel1.Controls.Add(this.treeView1);  
        splitContainer2.Panel1.Controls.Add(this.splitContainer1);  
  
        // Add the main SplitContainer control to the form.  
        this.Controls.Add(this.splitContainer2);  
        this.Text = "Intricate UI Example";  
    }  
    ```  
  
3. <span data-ttu-id="3c389-120">在 Visual Basic 中，將呼叫新增至您剛才在 `New()` 程式中建立的程式。</span><span class="sxs-lookup"><span data-stu-id="3c389-120">In Visual Basic, add a call to the procedure you just created in the `New()` procedure.</span></span> <span data-ttu-id="3c389-121">在 Visual C#中，將這行程式碼新增至表單類別的函式。</span><span class="sxs-lookup"><span data-stu-id="3c389-121">In Visual C#, add this line of code to the constructor for the form class.</span></span>  
  
    ```vb  
    ' Add this to the New procedure.  
    CreateOutlookUI()  
    ```  
  
    ```csharp  
    // Add this to the form class's constructor.  
    createOutlookUI();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3c389-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="3c389-122">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="3c389-123">SplitContainer 控制項</span><span class="sxs-lookup"><span data-stu-id="3c389-123">SplitContainer Control</span></span>](splitcontainer-control-windows-forms.md)
- [<span data-ttu-id="3c389-124">操作說明：使用設計工具，以 Windows Forms 建立多窗格使用者介面</span><span class="sxs-lookup"><span data-stu-id="3c389-124">How to: Create a Multipane User Interface with Windows Forms Using the Designer</span></span>](create-a-multipane-user-interface-with-wf-using-the-designer.md)
