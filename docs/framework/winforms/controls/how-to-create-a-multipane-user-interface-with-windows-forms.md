---
title: 逐步解說：利用 Windows Form 建立多窗格使用者介面
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
ms.openlocfilehash: 4e243191b83149f17f4970150d784dcd7d014b22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532079"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms"></a>逐步解說：利用 Windows Form 建立多窗格使用者介面
在下列程序中，您將建立類似搭配使用 Microsoft Outlook 中的多窗格使用者介面**資料夾** 清單中，**訊息** 窗格中，與**預覽**窗格。 這種排列方式被達成透過停駐控制項的表單來達成。  
  
 將控制項停駐，您決定哪一個父容器的邊緣控制項視窗固定至。 因此，如果您設定<xref:System.Windows.Forms.SplitContainer.Dock%2A>屬性<xref:System.Windows.Forms.DockStyle.Right>，控制項的右邊緣會停駐於其父控制項的右邊緣。 此外，停駐控制項的邊緣會調整大小以符合其容器控制項。 如需有關如何<xref:System.Windows.Forms.SplitContainer.Dock%2A>屬性雖然有效，請參閱[How to： 在 Windows Form 上的停駐控制項](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)。  
  
 此程序著重於排列<xref:System.Windows.Forms.SplitContainer>和其他控制項在表單上，而非新增功能，讓模擬 Microsoft Outlook 應用程式。  
  
 若要建立此使用者介面，您將放內的所有控制項<xref:System.Windows.Forms.SplitContainer>控制項，其中包含<xref:System.Windows.Forms.TreeView>左側面板中的控制項。 右手邊的面板<xref:System.Windows.Forms.SplitContainer>控制項包含第二個<xref:System.Windows.Forms.SplitContainer>用來控制<xref:System.Windows.Forms.ListView>上述控制項<xref:System.Windows.Forms.RichTextBox>控制項。 這些<xref:System.Windows.Forms.SplitContainer>控制項可讓獨立調整表單上其他控制項的大小。 您可以調整此程序以您自己的特殊功能的自訂使用者介面中的技術。  
  
### <a name="to-create-an-outlook-style-user-interface-programmatically"></a>若要以程式設計方式建立的 Outlook 樣式使用者介面  
  
1.  在表單中，宣告每個包含您的使用者介面的控制項。 此範例中，使用<xref:System.Windows.Forms.TreeView>， <xref:System.Windows.Forms.ListView>， <xref:System.Windows.Forms.SplitContainer>，和<xref:System.Windows.Forms.RichTextBox>控制項，以模擬 Microsoft Outlook 的使用者介面。  
  
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
  
2.  建立您的使用者介面會定義程序。 下列程式碼設定的屬性，讓表單將類似於 Microsoft Outlook 中的使用者介面。 不過，藉由使用其他控制項，或停駐它們以不同的方式，它也一樣簡單來建立其他使用者介面一樣具有彈性。  
  
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
  
3.  在 Visual Basic 中，加入至您在建立程序呼叫`New()`程序。 在 Visual C# 中，將這行程式碼加入表單類別的建構函式。  
  
    ```vb  
    ' Add this to the New procedure.  
    CreateOutlookUI()  
    ```  
  
    ```csharp  
    // Add this to the form class's constructor.  
    createOutlookUI();  
    ```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.SplitContainer>  
 [SplitContainer 控制項](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)  
 [操作說明：使用設計工具，以 Windows Forms 建立多窗格使用者介面](../../../../docs/framework/winforms/controls/create-a-multipane-user-interface-with-wf-using-the-designer.md)
