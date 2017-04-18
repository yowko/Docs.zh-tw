---
title: "如何：使用 MenuStrip 建立 MDI 視窗清單 (Windows Form) | Microsoft Docs"
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
  - "MDI, 建立視窗清單"
  - "MenuStrip 控制項 [Windows Form], 建立視窗清單"
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：使用 MenuStrip 建立 MDI 視窗清單 (Windows Form)
請使用多重文件介面 \(MDI\) 建立應用程式，此應用程式可同時開啟數個文件，並且可複製某一文件的內容並將它貼入另一個文件。  
  
 這個程序顯示如何建立父視窗功能表上所有現用子表單的清單。  
  
### 若要建立 MenuStrip 上的 MDI 視窗清單  
  
1.  建立表單，並將其 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 屬性設定為 `true`。  
  
2.  將 <xref:System.Windows.Forms.MenuStrip> 加入表單中。  
  
3.  將最上層的兩個功能表項目加入至 <xref:System.Windows.Forms.MenuStrip> 中，並將其 <xref:System.Windows.Forms.Control.Text%2A> 屬性設定為 `&File` 和 `&Window`。  
  
4.  將子功能表項目加入至 `&File` 功能表項目，並將該項目的 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性設定為 `&Open`。  
  
5.  Set the <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> property of the <xref:System.Windows.Forms.MenuStrip> to the `&Window`<xref:System.Windows.Forms.ToolStripMenuItem>.  
  
6.  將表單加入至專案，並且在其中加入您想要的控制項，例如另一個 <xref:System.Windows.Forms.MenuStrip>。  
  
7.  建立事件處理常式的<xref:System.Windows.Forms.Control.Click>事件`&New`<xref:System.Windows.Forms.ToolStripMenuItem>。  
  
8.  在事件處理常式中，插入類似以下的程式碼，藉此建立和顯示 `Form2` 的新執行個體，如同 `Form1` 的 MDI 子系：  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As _  
    System.Object, ByVal e As System.EventArgs) Handles _  
    openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
  
    ```  
  
     \[C\#\]  
  
    ```  
    private void newToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
  
    ```  
  
9. 將像下列的程式碼置於`&New`<xref:System.Windows.Forms.ToolStripMenuItem>註冊事件處理常式。  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
  
    ```  
  
## 編譯程式碼  
 這個範例需要：  
  
-   命名為 `Form1` 和 `Form2` 的兩個 <xref:System.Windows.Forms.Form> 控制項。  
  
-   `Form1` 上名為 `menuStrip1` 的 <xref:System.Windows.Forms.MenuStrip> 控制項，以及 `Form2` 上名為 `menuStrip2` 的 <xref:System.Windows.Forms.MenuStrip> 控制項。  
  
-   <xref:System?displayProperty=fullName> 和 <xref:System.Windows.Forms?displayProperty=fullName> 組件的參考。  
  
## 請參閱  
 [如何：建立 MDI 父表單](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)   
 [如何：建立 MDI 子表單](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)   
 [MenuStrip 控制項](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)