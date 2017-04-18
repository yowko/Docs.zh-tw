---
title: "如何：將 MenuStrip 插入至 MDI 下拉式功能表 (Windows Form) | Microsoft Docs"
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
  - "MenuStrip 控制項 [Windows Form], 插入"
  - "MenuStrip 控制項 [Windows Form], 合併"
ms.assetid: 0fad444e-26d9-49af-8860-044d9c10d608
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：將 MenuStrip 插入至 MDI 下拉式功能表 (Windows Form)
在某些應用程式中，多重文件介面 \(MDI\) 子視窗的類型可能會與 MDI 父視窗不同。  例如，MDI 父視窗可能是試算表，而 MDI 子視窗則可能是圖表。  在此情形下，您要以 MDI 子視窗功能表的內容更新 MDI 父視窗功能表的內容，因為已啟動各種不同的 MDI 子視窗。  
  
 以下程序使用 <xref:System.Windows.Forms.Form.IsMdiContainer%2A>、<xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>、<xref:System.Windows.Forms.MergeAction> 和 <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> 屬性，將來自 MDI 子功能表的功能表項目群組插入至 MDI 父功能表的下拉式組件中。  關閉 MDI 子視窗，會使插入的功能表項目從 MDI 父視窗中移除。  
  
### 若要將 MenuStrip 插入至 MDI 下拉式功能表  
  
1.  建立表單，並將其 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 屬性設定為 `true`。  
  
2.  加入 <xref:System.Windows.Forms.MenuStrip> 至 `Form1`，並將 <xref:System.Windows.Forms.MenuStrip> 的 <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> 屬性設定為 `true`。  
  
3.  將最上層的功能表項目加入至 `Form1` <xref:System.Windows.Forms.MenuStrip> 中，並將該項目的 <xref:System.Windows.Forms.Control.Text%2A> 屬性設為 `&File`。  
  
4.  將三個子功能表項目加入至 `&File` 功能表項目，並將其 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性設為 `&Open`、`&Import from` 和 `E&xit`。  
  
5.  將兩個子功能表項目加入至 `&Import from` 子功能表項目，並將其 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性設為 `&Word` 和 `&Excel`。  
  
6.  將表單加入至專案，並將 <xref:System.Windows.Forms.MenuStrip> 加入至表單，然後將 `Form2` <xref:System.Windows.Forms.MenuStrip> 的 <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> 屬性設定為 `true`。  
  
7.  將最上層的功能表項目加入至 `Form2` <xref:System.Windows.Forms.MenuStrip> 中，並將該項目的 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性設定為 `&File`。  
  
8.  請依下列順序將子功能表加入至 `Form2` 的 `&File` 功能表中：<xref:System.Windows.Forms.ToolStripSeparator>、`&Save`、`&Close` `and Save` 以及另外一個 <xref:System.Windows.Forms.ToolStripSeparator>。  
  
9. 請按照下表所示來設定 `Form2` 功能表項目的 <xref:System.Windows.Forms.MergeAction> 和 <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> 屬性。  
  
    |Form2 功能表項目|MergeAction 值|MergeIndex 值|  
    |-----------------|-------------------|------------------|  
    |檔案|MatchOnly|\-1|  
    |Separator|Insert|2|  
    |Save|Insert|3|  
    |儲存後關閉|Insert|4|  
    |Separator|Insert|5|  
  
10. 為 `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> 的 <xref:System.Windows.Forms.Control.Click> 事件建立事件處理常式。  
  
11. 在事件處理常式中，插入類似下列程式碼範例的程式碼，以建立和顯示 `Form2` 的新執行個體，做為 `Form1` 的 MDI 子系：  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
  
    ```  
  
    ```csharp  
    private void openToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
  
    ```  
  
12. 將類似下列程式碼範例的程式碼放入 `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> 之中，以註冊事件處理常式。  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
  
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