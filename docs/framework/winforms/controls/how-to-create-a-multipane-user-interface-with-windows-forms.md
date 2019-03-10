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
ms.openlocfilehash: 4db424b27af09dcb7def0051fba070fe9ccf0491
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721966"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms"></a>HOW TO：利用 Windows Form 建立多窗格使用者介面
在下列程序中，您將建立類似於使用 Microsoft Outlook 中所使用的多窗格使用者介面**資料夾** 清單中，**訊息**窗格中，和**預覽**  窗格。 這種排列方式是主要透過停駐控制項的表單來達成的。  
  
 當您將控制項停駐時，您決定父容器的邊緣控制項固定至。 因此，如果您設定<xref:System.Windows.Forms.SplitContainer.Dock%2A>屬性設<xref:System.Windows.Forms.DockStyle.Right>，右邊緣的控制項所停駐到其父控制項的右邊緣。 此外，停駐控制項的邊緣會調整大小以符合其容器控制項。 如需有關如何<xref:System.Windows.Forms.SplitContainer.Dock%2A>屬性雖然有效，請參閱[How to:停駐在 Windows Forms 上的控制項](how-to-dock-controls-on-windows-forms.md)。  
  
 此程序著重於排列<xref:System.Windows.Forms.SplitContainer>和其他控制項在表單上，而不加入讓模仿 Microsoft Outlook 應用程式的功能。  
  
 若要建立此使用者介面，您會放置內的所有控制項<xref:System.Windows.Forms.SplitContainer>控制項，包含<xref:System.Windows.Forms.TreeView>左面板中的控制項。 右側面板中的<xref:System.Windows.Forms.SplitContainer>控制項包含第二個<xref:System.Windows.Forms.SplitContainer>控制項取代<xref:System.Windows.Forms.ListView>控制上述<xref:System.Windows.Forms.RichTextBox>控制項。 這些<xref:System.Windows.Forms.SplitContainer>控制項可讓您獨立調整大小的表單上的其他控制項。 您可以調整此程序來製作您自己的自訂使用者介面中的技術。  
  
### <a name="to-create-an-outlook-style-user-interface-programmatically"></a>若要以程式設計方式建立的 Outlook 樣式使用者介面  
  
1.  在表單中，宣告每個包含您的使用者介面的控制項。 此範例中，使用<xref:System.Windows.Forms.TreeView>， <xref:System.Windows.Forms.ListView>， <xref:System.Windows.Forms.SplitContainer>，和<xref:System.Windows.Forms.RichTextBox>為了模仿 Microsoft Outlook 使用者介面的控制項。  
  
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
  
2.  建立您的使用者介面會定義程序。 下列程式碼設定的屬性，使表單看起來將類似 Microsoft Outlook 中的使用者介面。 不過，藉由使用其他控制項，或停駐它們以不同的方式，它是一樣的容易建立一樣具有彈性的其他使用者介面。  
  
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
  
3.  在 Visual Basic 中，新增您在建立程序的呼叫`New()`程序。 在視覺效果C#，將這行程式碼新增至表單類別的建構函式。  
  
    ```vb  
    ' Add this to the New procedure.  
    CreateOutlookUI()  
    ```  
  
    ```csharp  
    // Add this to the form class's constructor.  
    createOutlookUI();  
    ```  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer 控制項](splitcontainer-control-windows-forms.md)
- [如何：使用設計工具的 Windows form 建立多窗格使用者介面](create-a-multipane-user-interface-with-wf-using-the-designer.md)
