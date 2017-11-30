---
title: "如何：將載入、儲存和取消按鈕加入至 Windows Form BindingNavigator 控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4bc4f53c404e3767b9f98ca5ab46b19db31f9c6e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>如何：將載入、儲存和取消按鈕加入至 Windows Form BindingNavigator 控制項
<xref:System.Windows.Forms.BindingNavigator>控制項是特殊用途<xref:System.Windows.Forms.ToolStrip>適用於巡覽及操作控制項在表單上的繫結至資料的控制項。  
  
 因為它是<xref:System.Windows.Forms.ToolStrip>控制項，<xref:System.Windows.Forms.BindingNavigator>元件可以輕鬆地修改為包含使用者的其他或替代式命令。  
  
 在下列程序中，<xref:System.Windows.Forms.TextBox>控制項所繫結至資料，而<xref:System.Windows.Forms.ToolStrip>控制項加入至表單，會修改成包含載入、 儲存和取消按鈕。  
  
### <a name="to-add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>若要將載入、 儲存和取消按鈕 BindingNavigator 元件  
  
1.  新增 <xref:System.Windows.Forms.TextBox> 控制項至表單。  
  
2.  繫結至<xref:System.Windows.Forms.BindingSource>，它繫結至資料來源。 例如，<xref:System.Windows.Forms.BindingSource>繫結至資料庫。  
  
3.  產生資料集和資料表配接器之後，請將<xref:System.Windows.Forms.BindingNavigator>控制項加入表單。  
  
4.  設定<xref:System.Windows.Forms.BindingNavigator>控制項的<xref:System.Windows.Forms.BindingNavigator.BindingSource%2A>屬性<xref:System.Windows.Forms.BindingSource>繫結至控制項在表單上。  
  
5.  選取 <xref:System.Windows.Forms.BindingNavigator> 控制項。  
  
6.  按一下智慧標籤圖像 (![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 因此**BindingNavigator 工作**對話方塊出現，並選取**編輯項目**.  
  
     **項目集合編輯器**隨即出現。  
  
7.  在**項目集合編輯器**，完成下列步驟：  
  
    1.  新增<xref:System.Windows.Forms.ToolStripSeparator>和三個<xref:System.Windows.Forms.ToolStripButton>選取適當類型的項目<xref:System.Windows.Forms.ToolStripItem>按一下**新增** 按鈕。  
  
    2.  設定<xref:System.Windows.Forms.ToolStripItem.Name%2A> 按鈕的屬性**LoadButton**，**SaveButton**，和**CancelButton**分別。  
  
    3.  設定<xref:System.Windows.Forms.ToolStripItem.Text%2A> 按鈕的屬性**負載**`,` **儲存**，和**取消**。  
  
    4.  設定<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>屬性每個按鈕，**文字**。 或者，您可以將此屬性設定為**映像**或**ImageAndText**並設定要顯示在影像<xref:System.Windows.Forms.ToolStripItem.Image%2A>屬性。  
  
    5.  按一下**確定**以關閉對話方塊。若要加入按鈕<xref:System.Windows.Forms.ToolStrip>。  
  
8.  以滑鼠右鍵按一下表單，然後選擇 **檢視程式碼**。  
  
9. 在程式碼編輯器中，找到資料載入資料表配接器的程式碼的行。 您可以設定在步驟 2 中的資料繫結時，所產生此程式碼。 程式碼應該類似下列： `TableAdapterName.Fill(DataSetName.TableName)`。 將會使用最可能會出現在表單的<xref:System.Windows.Forms.Form.Load>事件。  
  
10. 建立事件處理常式<xref:System.Windows.Forms.ToolStripItem.Click>事件**負載**<xref:System.Windows.Forms.ToolStripButton>您先前建立並將此資料載入程式碼移到它。  
  
     您的程式碼現在看起來應該如下所示：  
  
    ```vb  
    Private Sub LoadButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles LoadButton.Click  
        TableAdapterName.Fill(DataSetName.TableName)  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Fill(DataSetName.TableName);  
    }  
    ```  
  
11. 建立事件處理常式<xref:System.Windows.Forms.ToolStripItem.Click>事件**儲存**<xref:System.Windows.Forms.ToolStripButton>您先前建立並撰寫程式碼來更新資料表控制項中的資料繫結至。  
  
    ```vb  
    Private Sub SaveButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles SaveButton.Click  
        TableAdapterName.Update(DataSetName.TableName)  
    End Sub  
    ```  
  
    ```csharp  
    private void SaveButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Update(DataSetName.TableName);  
    }  
    ```  
  
    > [!NOTE]
    >  在某些情況下，<xref:System.Windows.Forms.BindingNavigator>元件已經**儲存** 按鈕，但沒有程式碼會產生的 Windows Form 設計工具。 在此情況下，您可以在其中放置在上述程式碼<xref:System.Windows.Forms.ToolStripItem.Click>該按鈕，而不建立全新的按鈕上的事件處理常式<xref:System.Windows.Forms.ToolStrip>。 不過，按鈕預設會停用，因此您必須設定<xref:System.Windows.Forms.ToolBarButton.Enabled%2A>按鈕的屬性`true`正確具有按鈕函式。  
  
12. 建立事件處理常式<xref:System.Windows.Forms.ToolStripItem.Click>事件**取消**<xref:System.Windows.Forms.ToolStripButton>您先前建立並撰寫程式碼來取消任何顯示的資料記錄的變更。  
  
    ```vb  
    Private Sub CancelButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles CancelButton.Click  
        BindingSourceName.CancelEdit()  
    End Sub  
    ```  
  
    ```csharp  
    private void CancelButton_Click(System.Object sender, System.EventArgs e)  
    {  
        BindingSourceName.CancelEdit();  
    }  
    ```  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.BindingSource.CancelEdit%2A>方法的範圍為資料列。 儲存您在檢視該個別記錄之前瀏覽至下一筆記錄時所做的變更。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.ToolStrip>  
 [BindingNavigator 控制項](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [BindingSource 元件概觀](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)
