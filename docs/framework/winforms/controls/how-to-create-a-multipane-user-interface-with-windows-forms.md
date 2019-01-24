---
title: HOW TO：利用 Windows Form 建立多窗格使用者介面
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
ms.openlocfilehash: 1f7ba0ab7f0701fe39c3cefb979b9226eeeddffe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531404"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms"></a><span data-ttu-id="dea73-102">HOW TO：利用 Windows Form 建立多窗格使用者介面</span><span class="sxs-lookup"><span data-stu-id="dea73-102">How to: Create a Multipane User Interface with Windows Forms</span></span>
<span data-ttu-id="dea73-103">在下列程序中，您將建立類似於使用 Microsoft Outlook 中所使用的多窗格使用者介面**資料夾** 清單中，**訊息**窗格中，和**預覽**  窗格。</span><span class="sxs-lookup"><span data-stu-id="dea73-103">In the following procedure, you will create a multipane user interface that is similar to the one used in Microsoft Outlook, with a **Folder** list, a **Messages** pane, and a **Preview** pane.</span></span> <span data-ttu-id="dea73-104">這種排列方式是主要透過停駐控制項的表單來達成的。</span><span class="sxs-lookup"><span data-stu-id="dea73-104">This arrangement is achieved chiefly through docking controls with the form.</span></span>  
  
 <span data-ttu-id="dea73-105">當您將控制項停駐時，您決定父容器的邊緣控制項固定至。</span><span class="sxs-lookup"><span data-stu-id="dea73-105">When you dock a control, you determine which edge of the parent container a control is fastened to.</span></span> <span data-ttu-id="dea73-106">因此，如果您設定<xref:System.Windows.Forms.SplitContainer.Dock%2A>屬性設<xref:System.Windows.Forms.DockStyle.Right>，右邊緣的控制項所停駐到其父控制項的右邊緣。</span><span class="sxs-lookup"><span data-stu-id="dea73-106">Thus, if you set the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Right>, the right edge of the control will be docked to the right edge of its parent control.</span></span> <span data-ttu-id="dea73-107">此外，停駐控制項的邊緣會調整大小以符合其容器控制項。</span><span class="sxs-lookup"><span data-stu-id="dea73-107">Additionally, the docked edge of the control is resized to match that of its container control.</span></span> <span data-ttu-id="dea73-108">如需有關如何<xref:System.Windows.Forms.SplitContainer.Dock%2A>屬性雖然有效，請參閱[How to:停駐在 Windows Forms 上的控制項](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="dea73-108">For more information about how the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property works, see [How to: Dock Controls on Windows Forms](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md).</span></span>  
  
 <span data-ttu-id="dea73-109">此程序著重於排列<xref:System.Windows.Forms.SplitContainer>和其他控制項在表單上，而不加入讓模仿 Microsoft Outlook 應用程式的功能。</span><span class="sxs-lookup"><span data-stu-id="dea73-109">This procedure focuses on arranging the <xref:System.Windows.Forms.SplitContainer> and the other controls on the form, not on adding functionality to make the application mimic Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="dea73-110">若要建立此使用者介面，您會放置內的所有控制項<xref:System.Windows.Forms.SplitContainer>控制項，包含<xref:System.Windows.Forms.TreeView>左面板中的控制項。</span><span class="sxs-lookup"><span data-stu-id="dea73-110">To create this user interface, you place all the controls within a <xref:System.Windows.Forms.SplitContainer> control, which contains a <xref:System.Windows.Forms.TreeView> control in the left-hand panel.</span></span> <span data-ttu-id="dea73-111">右側面板中的<xref:System.Windows.Forms.SplitContainer>控制項包含第二個<xref:System.Windows.Forms.SplitContainer>控制項取代<xref:System.Windows.Forms.ListView>控制上述<xref:System.Windows.Forms.RichTextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="dea73-111">The right-hand panel of the <xref:System.Windows.Forms.SplitContainer> control contains a second <xref:System.Windows.Forms.SplitContainer> control with a <xref:System.Windows.Forms.ListView> control above a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="dea73-112">這些<xref:System.Windows.Forms.SplitContainer>控制項可讓您獨立調整大小的表單上的其他控制項。</span><span class="sxs-lookup"><span data-stu-id="dea73-112">These <xref:System.Windows.Forms.SplitContainer> controls enable independent resizing of the other controls on the form.</span></span> <span data-ttu-id="dea73-113">您可以調整此程序來製作您自己的自訂使用者介面中的技術。</span><span class="sxs-lookup"><span data-stu-id="dea73-113">You can adapt the techniques in this procedure to craft custom user interfaces of your own.</span></span>  
  
### <a name="to-create-an-outlook-style-user-interface-programmatically"></a><span data-ttu-id="dea73-114">若要以程式設計方式建立的 Outlook 樣式使用者介面</span><span class="sxs-lookup"><span data-stu-id="dea73-114">To create an Outlook-style user interface programmatically</span></span>  
  
1.  <span data-ttu-id="dea73-115">在表單中，宣告每個包含您的使用者介面的控制項。</span><span class="sxs-lookup"><span data-stu-id="dea73-115">Within a form, declare each control that comprises your user interface.</span></span> <span data-ttu-id="dea73-116">此範例中，使用<xref:System.Windows.Forms.TreeView>， <xref:System.Windows.Forms.ListView>， <xref:System.Windows.Forms.SplitContainer>，和<xref:System.Windows.Forms.RichTextBox>為了模仿 Microsoft Outlook 使用者介面的控制項。</span><span class="sxs-lookup"><span data-stu-id="dea73-116">For this example, use the <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.SplitContainer>, and <xref:System.Windows.Forms.RichTextBox> controls to mimic the Microsoft Outlook user interface.</span></span>  
  
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
  
2.  <span data-ttu-id="dea73-117">建立您的使用者介面會定義程序。</span><span class="sxs-lookup"><span data-stu-id="dea73-117">Create a procedure that defines your user interface.</span></span> <span data-ttu-id="dea73-118">下列程式碼設定的屬性，使表單看起來將類似 Microsoft Outlook 中的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="dea73-118">The following code sets the properties so that the form will resemble the user interface in Microsoft Outlook.</span></span> <span data-ttu-id="dea73-119">不過，藉由使用其他控制項，或停駐它們以不同的方式，它是一樣的容易建立一樣具有彈性的其他使用者介面。</span><span class="sxs-lookup"><span data-stu-id="dea73-119">However, by using other controls or docking them differently, it is just as easy to create other user interfaces that are equally flexible.</span></span>  
  
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
  
3.  <span data-ttu-id="dea73-120">在 Visual Basic 中，新增您在建立程序的呼叫`New()`程序。</span><span class="sxs-lookup"><span data-stu-id="dea73-120">In Visual Basic, add a call to the procedure you just created in the `New()` procedure.</span></span> <span data-ttu-id="dea73-121">在視覺效果C#，將這行程式碼新增至表單類別的建構函式。</span><span class="sxs-lookup"><span data-stu-id="dea73-121">In Visual C#, add this line of code to the constructor for the form class.</span></span>  
  
    ```vb  
    ' Add this to the New procedure.  
    CreateOutlookUI()  
    ```  
  
    ```csharp  
    // Add this to the form class's constructor.  
    createOutlookUI();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="dea73-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dea73-122">See also</span></span>
- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="dea73-123">SplitContainer 控制項</span><span class="sxs-lookup"><span data-stu-id="dea73-123">SplitContainer Control</span></span>](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
- [<span data-ttu-id="dea73-124">如何：使用設計工具的 Windows form 建立多窗格使用者介面</span><span class="sxs-lookup"><span data-stu-id="dea73-124">How to: Create a Multipane User Interface with Windows Forms Using the Designer</span></span>](../../../../docs/framework/winforms/controls/create-a-multipane-user-interface-with-wf-using-the-designer.md)
