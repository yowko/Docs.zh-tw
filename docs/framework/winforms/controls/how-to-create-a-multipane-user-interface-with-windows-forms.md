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
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms"></a>如何：利用 Windows Form 建立多窗格使用者介面
在下列程式中，您將建立類似于 Microsoft Outlook 中所用的多窗格使用者介面，以及**資料夾**清單、[**訊息**] 窗格和 [**預覽**] 窗格。 這種安排是透過將控制項與表單停駐的方式來 chiefly。  
  
 當您停駐控制項時，您會決定控制項已固定的父容器邊緣。 因此，如果您將 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性設定為 <xref:System.Windows.Forms.DockStyle.Right>，控制項的右邊緣將停駐在其父控制項的右邊緣。 此外，控制項的停駐邊緣也會調整大小，以符合其容器控制項的邊緣。 如需 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性如何運作的詳細資訊，請參閱[如何：將控制項停駐在 Windows Forms 上](how-to-dock-controls-on-windows-forms.md)。  
  
 這個程式著重于在表單上排列 <xref:System.Windows.Forms.SplitContainer> 和其他控制項，而不是新增功能讓應用程式模擬 Microsoft Outlook。  
  
 若要建立這個使用者介面，您可以將所有控制項放在 <xref:System.Windows.Forms.SplitContainer> 控制項內，其中包含左側面板中的 <xref:System.Windows.Forms.TreeView> 控制項。 <xref:System.Windows.Forms.SplitContainer> 控制項的右面板中包含第二個 <xref:System.Windows.Forms.SplitContainer> 控制項，其中具有 <xref:System.Windows.Forms.RichTextBox> 控制項上方的 <xref:System.Windows.Forms.ListView> 控制項。 這些 <xref:System.Windows.Forms.SplitContainer> 控制項可讓您在表單上進行其他控制項的獨立調整大小。 您可以調整此程式中的技術，以製作您自己的自訂使用者介面。  
  
### <a name="to-create-an-outlook-style-user-interface-programmatically"></a>以程式設計方式建立 Outlook 樣式的使用者介面  
  
1. 在表單中，宣告組成使用者介面的每個控制項。 在此範例中，使用 [<xref:System.Windows.Forms.TreeView>]、[<xref:System.Windows.Forms.ListView>]、[<xref:System.Windows.Forms.SplitContainer>] 和 [<xref:System.Windows.Forms.RichTextBox>] 控制項來模擬 Microsoft Outlook 使用者介面。  
  
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
  
2. 建立定義使用者介面的程式。 下列程式碼會設定屬性，讓表單類似 Microsoft Outlook 中的使用者介面。 不過，藉由使用其他控制項或以不同的方式將它們停駐，就像建立其他同樣有彈性的使用者介面一樣容易。  
  
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
  
3. 在 Visual Basic 中，將呼叫新增至您剛才在 `New()` 程式中建立的程式。 在 Visual C#中，將這行程式碼新增至表單類別的函式。  
  
    ```vb  
    ' Add this to the New procedure.  
    CreateOutlookUI()  
    ```  
  
    ```csharp  
    // Add this to the form class's constructor.  
    createOutlookUI();  
    ```  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer 控制項](splitcontainer-control-windows-forms.md)
- [操作說明：使用設計工具，以 Windows Forms 建立多窗格使用者介面](create-a-multipane-user-interface-with-wf-using-the-designer.md)
