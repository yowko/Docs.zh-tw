---
title: "如何：將載入、儲存和取消按鈕加入至 Windows Form BindingNavigator 控制項 | Microsoft Docs"
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
  - "控制項 [Windows Forms], 操作"
  - "BindingNavigator 控制項 [Windows Forms], 加入按鈕"
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：將載入、儲存和取消按鈕加入至 Windows Form BindingNavigator 控制項
<xref:System.Windows.Forms.BindingNavigator> 控制項是特殊用途的 <xref:System.Windows.Forms.ToolStrip> 控制項，是要用來巡覽及管理在表單上繫結至資料的控制項。  
  
 因為它是 <xref:System.Windows.Forms.ToolStrip> 控制項，所以可以輕易修改 <xref:System.Windows.Forms.BindingNavigator> 元件以包含使用者的其他或替代命令。  
  
 在下列程序中，<xref:System.Windows.Forms.TextBox> 控制項繫結至資料，並修改已加入至表單的 <xref:System.Windows.Forms.ToolStrip> 控制項以包含載入、儲存和取消按鈕。  
  
### 若要加入載入、儲存和取消按鈕至 BindingNavigator 元件  
  
1.  在表單中加入 <xref:System.Windows.Forms.TextBox> 控制項。  
  
2.  將它繫結至 <xref:System.Windows.Forms.BindingSource> \(此控制項繫結至資料來源\)。  在這個範例中，<xref:System.Windows.Forms.BindingSource> 繫結至資料庫。  
  
3.  在產生資料集和資料表配置器之後，將 <xref:System.Windows.Forms.BindingNavigator> 控制項拖曳至表單。  
  
4.  將 <xref:System.Windows.Forms.BindingNavigator> 控制項的 <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> 屬性設定為在表單上繫結至控制項的 <xref:System.Windows.Forms.BindingSource>。  
  
5.  選取 <xref:System.Windows.Forms.BindingNavigator> 控制項。  
  
6.  按一下智慧標籤圖像 \(![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\)，\[**BindingNavigator 工作**\] 對話方塊便會出現，然後選取 \[**編輯項目**\]。  
  
     \[**項目集合編輯器**\] 隨即出現。  
  
7.  在 \[**項目集合編輯器**\] 中，完成下列步驟：  
  
    1.  加入 <xref:System.Windows.Forms.ToolStripSeparator> 和三個 <xref:System.Windows.Forms.ToolStripButton> 項目，方法為選取適當的 <xref:System.Windows.Forms.ToolStripItem> 型別，然後按一下 \[**加入**\] 按鈕。  
  
    2.  將按鈕的 <xref:System.Windows.Forms.ToolStripItem.Name%2A> 屬性分別設定為  `` LoadButton、 `` SaveButton 和 `` CancelButton。  
  
    3.  將按鈕的 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性設定為 `` Load`、`Save 和 `` Cancel。  
  
    4.  將每個按鈕的 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> 屬性設定為  `` Text。  此外，您也可以將這個屬性設定為  `` Image `` 或 `` ImageAndText `` ，並且將影像設定為在 <xref:System.Windows.Forms.ToolStripItem.Image%2A> 屬性中顯示。  
  
    5.  按一下 \[**確定**\] 以關閉對話方塊。按鈕會加入至 <xref:System.Windows.Forms.ToolStrip>。  
  
8.  在表單上按一下滑鼠右鍵，並選擇 \[**檢視程式碼**\]。  
  
9. 在 \[程式碼編輯器\] 中，尋找將資料載入資料表配接器中的程式碼行。  當您在步驟 2 設定資料繫結時，就產生了這個程式碼。  程式碼應該類似下列：`TableAdapterName.Fill(DataSetName.TableName)`.  它最有可能在表單的 <xref:System.Windows.Forms.Form.Load> 事件中。  
  
10. 為您稍早建立的 `` \[**載入**\] `` <xref:System.Windows.Forms.ToolStripButton> 的 <xref:System.Windows.Forms.ToolStripItem.Click> 事件建立事件處理常式，然後將此資料載入程式碼移至這個事件處理常式中。  
  
     您的程式碼應該看起來如下：  
  
     \[Visual Basic\]  
  
    ```  
    Private Sub LoadButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles LoadButton.Click  
        TableAdapterName.Fill(DataSetName.TableName)  
    End Sub  
    ```  
  
     \[C\#\]  
  
    ```  
    private void LoadButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Fill(DataSetName.TableName);  
    }  
    ```  
  
11. 為您稍早建立的 \[**儲存**\]  `` <xref:System.Windows.Forms.ToolStripButton> 的 <xref:System.Windows.Forms.ToolStripItem.Click> 事件建立事件處理常式，並撰寫程式碼，以更新控制項繫結至的資料表中的資料。  
  
     \[Visual Basic\]  
  
    ```  
    Private Sub SaveButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles SaveButton.Click  
        TableAdapterName.Update(DataSetName.TableName)  
    End Sub  
    ```  
  
     \[C\#\]  
  
    ```  
    private void SaveButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Update(DataSetName.TableName);  
    }  
    ```  
  
    > [!NOTE]
    >  在某些情況中，<xref:System.Windows.Forms.BindingNavigator> 元件會已經擁有 ``  \[**儲存**\] 按鈕，但是 Windows Form 設計工具不會先產生任何程式碼。  在這個案例中，您可以在該按鈕的 <xref:System.Windows.Forms.ToolStripItem.Click> 事件處理常式中放入先前的程式碼，而非在 <xref:System.Windows.Forms.ToolStrip> 上建立全新的按鈕。  不過，根據預設會停用按鈕，所以您必須將按鈕的 <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> 屬性設定為 `true`，使按鈕能夠正常作用。  
  
12. 為您稍早建立的 `` \[**取消**\] `` <xref:System.Windows.Forms.ToolStripButton> 的 <xref:System.Windows.Forms.ToolStripItem.Click> 事件建立事件處理常式，並撰寫程式碼，以取消對顯示的資料錄所做的任何變更。  
  
     \[Visual Basic\]  
  
    ```  
    Private Sub CancelButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles CancelButton.Click  
        BindingSourceName.CancelEdit()  
    End Sub  
    ```  
  
     \[C\#\]  
  
    ```  
    private void CancelButton_Click(System.Object sender, System.EventArgs e)  
    {  
        BindingSourceName.CancelEdit();  
    }  
    ```  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> 方法符合資料列的範圍。  在巡覽至下一個資料錄之前檢視該個別資料錄，儲存您所做的任何變更。  
  
## 請參閱  
 <xref:System.Windows.Forms.BindingNavigator>   
 <xref:System.Windows.Forms.BindingSource>   
 <xref:System.Windows.Forms.ToolStrip>   
 [BindingNavigator 控制項](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)   
 [BindingSource 元件概觀](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)