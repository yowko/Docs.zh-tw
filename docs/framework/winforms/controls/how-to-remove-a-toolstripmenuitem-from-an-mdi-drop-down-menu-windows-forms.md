---
title: "如何：從 MDI 下拉式功能表移除 ToolStripMenuItem (Windows Form) | Microsoft Docs"
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
  - "MDI, 合併功能表項目"
  - "功能表項目, 從 MDI 下拉式功能表中移除"
  - "MenuStrip 控制項 [Windows Form], 合併"
  - "MenuStrip 控制項 [Windows Form], 移除"
ms.assetid: bdafe60d-82ee-45bc-97fe-eeefca6e54c1
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：從 MDI 下拉式功能表移除 ToolStripMenuItem (Windows Form)
在某些應用程式中，多重文件介面 \(MDI\) 子視窗的類型可能會與 MDI 父視窗不同。  例如，MDI 父視窗可能是試算表，而 MDI 子視窗則可能是圖表。  在此情形下，您要以 MDI 子視窗功能表的內容更新 MDI 父視窗功能表的內容，因為已啟動各種不同的 MDI 子視窗。  
  
 下列程序使用 <xref:System.Windows.Forms.Form.IsMdiContainer%2A>、<xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>、<xref:System.Windows.Forms.MergeAction> 和 <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> 屬性，將功能表項目從 MDI 父功能表的下拉式組件中移除。  關閉 MDI 子視窗，會將移除的功能表項目復原至 MDI 父功能表中。  
  
### 若要將 MenuStrip 從 MDI 下拉式功能表中移除  
  
1.  建立表單，並將其 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 屬性設定為 `true`。  
  
2.  加入 <xref:System.Windows.Forms.MenuStrip> 至 `Form1`，並將 <xref:System.Windows.Forms.MenuStrip> 的 <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> 屬性設定為 `true`。  
  
3.  新增最上層的功能表項目`Form1`<xref:System.Windows.Forms.MenuStrip> ，並設定其<xref:System.Windows.Forms.Control.Text%2A>屬性，以`&File`。  
  
4.  將三個子功能表項目加入至 `&File` 功能表項目，並將其 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性設為 `&Open`、`&Import from` 和 `E&xit`。  
  
5.  將兩個子功能表項目加入至 `&Import from` 子功能表項目，並將其 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性設為 `&Word` 和 `&Excel`。  
  
6.  將表單加入至專案、 新增<xref:System.Windows.Forms.MenuStrip>至表單及 「 <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>屬性的`Form2`<xref:System.Windows.Forms.MenuStrip>到`true`。  
  
7.  新增最上層的功能表項目`Form2`<xref:System.Windows.Forms.MenuStrip> ，並設定其<xref:System.Windows.Forms.ToolStripItem.Text%2A>屬性，以`&File`。  
  
8.  將 `&Import from` 子功能表項目加入至 `Form2` 的 `&File` 功能表並且將 `&Word` 子功能表項目加入至 `&File` 功能表。  
  
9. 請按照下表所示來設定 `Form2` 功能表項目的 <xref:System.Windows.Forms.MergeAction> 和 <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> 屬性。  
  
    |Form2 功能表項目|MergeAction 值|MergeIndex 值|  
    |-----------------|-------------------|------------------|  
    |檔案|MatchOnly|\-1|  
    |Import from|MatchOnly|\-1|  
    |Word|移除|\-1|  
  
10. 在`Form1`，建立事件處理常式的<xref:System.Windows.Forms.Control.Click>事件`&Open`<xref:System.Windows.Forms.ToolStripMenuItem>。  
  
11. 在事件處理常式中，插入類似下列程式碼範例的程式碼，以建立和顯示 `Form2` 的新執行個體，如同 `Form1` 的 MDI 子系：  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
  
    ```  
  
     \[C\#\]  
  
    ```  
    private void openToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
  
    ```  
  
12. 將程式碼類似下列的程式碼範例，在`&Open`<xref:System.Windows.Forms.ToolStripMenuItem>註冊事件處理常式。  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new _  
    System.EventHandler(this.openToolStripMenuItem_Click);  
  
    ```  
  
## 編譯程式碼  
 這個範例需要：  
  
-   命名為 `Form1` 和 `Form2` 的兩個 <xref:System.Windows.Forms.Form> 控制項。  
  
-   `Form1` 上名為 `menuStrip1` 的 <xref:System.Windows.Forms.MenuStrip> 控制項，以及 `Form2` 上名為 `menuStrip2` 的 <xref:System.Windows.Forms.MenuStrip> 控制項。  
  
-   <xref:System?displayProperty=fullName> 和 <xref:System.Windows.Forms?displayProperty=fullName> 組件的參考。  
  
## 請參閱  
 [如何：建立 MDI 父表單](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)   
 [如何：建立 MDI 子表單](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)   
 [MenuStrip 控制項概觀](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)