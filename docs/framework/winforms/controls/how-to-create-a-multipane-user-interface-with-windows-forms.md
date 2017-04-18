---
title: "逐步解說：利用 Windows Form 建立多窗格使用者介面 | Microsoft Docs"
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
  - "ListView 控制項 [Windows Form], 範例"
  - "Panel 控制項 [Windows Form], 範例"
  - "RichTextBox 控制項 [Windows Form], 範例"
  - "SplitContainer 控制項 [Windows Form], 範例"
  - "Splitter 控制項 [Windows Form], 範例"
  - "TreeView 控制項 [Windows Form], 範例"
ms.assetid: e79f6bcc-3740-4d1e-b46a-c5594d9b7327
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# 逐步解說：利用 Windows Form 建立多窗格使用者介面
在下列程序中，您將建立一個多窗格使用者介面，它和 Microsoft Outlook 中的使用者介面類似，具有 \[**資料夾**\] 清單、\[**訊息**\] 窗格，以及 \[**預覽**\] 窗格。  這個排列主要是透過停駐控制項和表單來達成。  
  
 當停駐控制項時，您決定控制項應該貼近父容器 \(Container\) 的哪一個邊緣。  因此，如果您設定 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性為 <xref:System.Windows.Forms.DockStyle>，則控制項的右邊緣將停駐在其父控制項的右邊緣。  此外，控制項的停駐邊緣會調整大小以符合其容器控制項的邊緣。  如需 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性如何運作的詳細資訊，請參閱 [如何：將控制項停駐在 Windows Form 上](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)。  
  
 這個程序集中焦點於排列 <xref:System.Windows.Forms.SplitContainer> 和其他在表單上的控制項，並非加入功能來讓應用程式模仿 Microsoft Outlook。  
  
 若要建立這個使用者介面，將所有控制項置於 <xref:System.Windows.Forms.SplitContainer> 控制項中 \(包含在左邊面板中的 <xref:System.Windows.Forms.TreeView> 控制項\)。  <xref:System.Windows.Forms.SplitContainer> 控制項的右邊面板包含第二個 <xref:System.Windows.Forms.SplitContainer> 控制項和 <xref:System.Windows.Forms.ListView> 控制項 \(位於 <xref:System.Windows.Forms.RichTextBox> 控制項之上\)。  這些 <xref:System.Windows.Forms.SplitContainer> 控制項可讓您單獨的調整表單上其他控制項的大小。  您可以修改以下程序的方法來建立您自己的自訂使用者介面。  
  
### 若要以程式設計方式建立 Outlook 樣式的使用者介面  
  
1.  在表單中，宣告每個含有使用者介面的控制項。  就這個範例而言，使用 <xref:System.Windows.Forms.TreeView>、<xref:System.Windows.Forms.ListView>、<xref:System.Windows.Forms.SplitContainer> 和 <xref:System.Windows.Forms.RichTextBox> 控制項來模仿 Microsoft Outlook 使用者介面。  
  
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
  
2.  建立定義使用者介面的程序。  下列程式碼會設定屬性，使得表單能夠與 Microsoft Outlook 中的使用者介面類似。  不過，只要使用其他控制項或以不同方式停駐它們，就能夠建立其他一樣具有彈性的使用者介面。  
  
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
  
3.  在 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 中，加入呼叫至您在 `New()` 程序剛剛建立的程序。  在 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 中，將下面這行程式碼加入到表單類別的建構函式。  
  
    ```vb  
    ' Add this to the New procedure.  
    CreateOutlookUI()  
  
    ```  
  
    ```csharp  
    // Add this to the form class's constructor.  
    createOutlookUI();  
  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.SplitContainer>   
 [SplitContainer 控制項](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)   
 [如何：使用設計工具，以 Windows Form 建立多窗格使用者介面](../../../../docs/framework/winforms/controls/create-a-multipane-user-interface-with-wf-using-the-designer.md)