---
title: "如何：建立 MDI 子表單 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "子表單"
  - "MDI, 建立表單"
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# 如何：建立 MDI 子表單
MDI 子表單是[多重文件介面 \(MDI\) 應用程式](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)的基本項目，也是使用者互動的中心所在。  
  
 在下列程序中，您將建立顯示 <xref:System.Windows.Forms.RichTextBox> 控制項的 MDI 子表單，這和大多數文書處理應用程式類似。  以其他控制項 \(例如 <xref:System.Windows.Forms.DataGridView> 控制項\) 或混合控制項來取代 <xref:System.Windows.Forms> 控制項，可讓您建立各種可能的 MDI 子視窗 \(甚至是 MDI 應用程式\)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選取 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 建立 MDI 子表單  
  
1.  建立新的 Windows Form 專案。  在表單的 \[屬性\] 視窗中，將其 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 屬性設定為 `true`，並將其 `WindowsState` 屬性設定為 `Maximized`。  
  
     如此即可將表單指定為子視窗的 MDI 容器。  
  
2.  將 <xref:System.Windows.Forms.MenuStrip> 控制項從 \[`Toolbox`\] 拖曳至表單。  將其 `Text` 屬性設定為 \[檔案\]。  
  
3.  按一下 \[項目\] 屬性旁的省略符號 \(...\)，然後按一下 \[加入\] 加入兩個子工具區域功能表項目。  將這些項目的 `Text` 屬性設定為 \[新增\] 和 \[視窗\]。  
  
4.  在 \[方案總管\] 中，以滑鼠右鍵按一下專案，指向 \[加入\]，然後選取 \[加入新項目\]。  
  
5.  在 \[加入新項目\] 對話方塊中，從 \[範本\] 窗格選取 \[Windows Form\] \(在 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 中\) 或 \[Windows Form 應用程式 \(.NET\)\] \(在 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)] 中\)。  在 \[名稱\] 方塊中，將表單命名為 Form2。  按一下 \[開啟\] 按鈕，將表單加入專案。  
  
    > [!NOTE]
    >  您在這個步驟中所建立的 MDI 子表單是標準的 Windows Form。  因此，它具有 <xref:System.Windows.Forms.Form.Opacity%2A> 屬性，可讓您控制表單的透明度。  然而，<xref:System.Windows.Forms.Form.Opacity%2A> 屬性是專為最上層視窗而設計的。  請勿搭配 MDI 子表單使用這個屬性，這樣做可能會發生繪製問題。  
  
     這個表單將是您的 MDI 子表單範本。  
  
     此時會開啟 \[Windows Form 設計工具\]，並顯示 Form2。  
  
6.  將 RichTextBox 控制項從 \[工具箱\] 拖曳至表單。  
  
7.  在 \[屬性\] 視窗中，將 `Anchor` 屬性設定為 \[Top, Left\]，並將 `Dock` 屬性設定為 \[填滿\]。  
  
     如此一來，<xref:System.Windows.Forms.RichTextBox> 控制項就會完全填滿 MDI 子表單區域，即使表單大小重新調整過亦可。  
  
8.  按兩下 \[新增\] 功能表項目，為它建立 <xref:System.Windows.Forms.Control.Click> 事件處理常式。  
  
9. 插入與以下類似的程式碼，如此即可在使用者按一下 \[新增\] 功能表項目時建立新的 MDI 子表單。  
  
    > [!NOTE]
    >  在下列範例中，事件處理常式會處理 `MenuItem2` 的 <xref:System.Windows.Forms.Control.Click> 事件。  請注意，視應用程式架構的細節而定，\[新增\] 功能表項目可能不是 `MenuItem2`。  
  
    ```vb  
    Protected Sub MDIChildNew_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MenuItem2.Click  
       Dim NewMDIChild As New Form2()  
       'Set the Parent Form of the Child window.  
       NewMDIChild.MdiParent = Me  
       'Display the new form.  
       NewMDIChild.Show()  
    End Sub  
  
    ```  
  
    ```csharp  
    protected void MDIChildNew_Click(object sender, System.EventArgs e){  
       Form2 newMDIChild = new Form2();  
       // Set the Parent Form of the Child window.  
       newMDIChild.MdiParent = this;  
       // Display the new form.  
       newMDIChild.Show();  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void menuItem2_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          Form2^ newMDIChild = gcnew Form2();  
          // Set the Parent Form of the Child window.  
          newMDIChild->MdiParent = this;  
          // Display the new form.  
          newMDIChild->Show();  
       }  
    ```  
  
     在 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)] 中，將下列 `#include` 指示詞加入 Form1.h 上方：  
  
    ```cpp  
    #include "Form2.h"  
    ```  
  
10. 在 \[屬性\] 視窗頂端的下拉式清單中，選取對應到 \[檔案\] 功能表區域的功能表區域，並將 <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> 屬性設定為 Window <xref:System.Windows.Forms.ToolStripMenuItem>。  
  
     這會讓 \[視窗\] 功能表維護一份已開啟 MDI 子視窗的清單，並在作用中的子視窗旁顯示核取記號。  
  
11. 按 F5 執行應用程式。  您可以從 \[檔案\] 功能表選取 \[新增\]，以建立新的 MDI 子表單，並在 \[視窗\] 功能表項目中追蹤這些子表單。  
  
    > [!NOTE]
    >  在 <xref:System.Windows.Forms.MainMenu> 元件 \(這個元件通常具有功能表項目的功能表結構\) 的 MDI 父表單中，開啟同樣具有 <xref:System.Windows.Forms.MainMenu> 元件 \(這個元件通常具有功能表項目的功能表結構\) 的 MDI 子表單時，如果您已設定 <xref:System.Windows.Forms.MenuItem.MergeType%2A> 屬性 \(並選擇性地設定 <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> 屬性\)，則功能表項目會自動合併。  將上述兩個 <xref:System.Windows.Forms.MainMenu> 的 <xref:System.Windows.Forms.MenuItem.MergeType%2A> 屬性和子表單的所有功能表項目設定為 <xref:System.Windows.Forms.MenuMerge>。  接著再設定 <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> 屬性，如此一來，來自兩個功能表的功能表項目即可依指定順序出現。  再者，請記住，在關閉 MDI 父表單時，每個 MDI 子表單都會在 MDI 父表單的 <xref:System.Windows.Forms.Form.Closing> 事件引發前，先引發 <xref:System.Windows.Forms.Form.Closing> 事件。  只取消 MDI 子表單的 <xref:System.Windows.Forms.Form.Closing> 事件並無法避免引發 MDI 父表單的 <xref:System.Windows.Forms.Form.Closing> 事件；不過，MDI 父表單之 <xref:System.Windows.Forms.Form.Closing> 事件的 <xref:System.ComponentModel.CancelEventArgs> 引數現在會設定為 `true`。  您可以將 <xref:System.ComponentModel.CancelEventArgs> 引數設定為 `false`，以強制關閉 MDI 父表單和所有 MDI 子表單。  
  
## 請參閱  
 [多重文件介面 \(MDI\) 應用程式](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)   
 [如何：建立 MDI 父表單](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)   
 [如何：決定作用中的 MDI 子系](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)   
 [如何：傳送資料至作用中的 MDI 子系](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)   
 [如何：安排 MDI 子表單](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)