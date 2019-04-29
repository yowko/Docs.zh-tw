---
title: HOW TO：將 [載入]、[儲存] 和 [取消] 按鈕新增至 Windows Forms BindingNavigator 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: 4d5cc91ca8bf71b2d5893f591652d777041e1a4d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757364"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>HOW TO：將 [載入]、[儲存] 和 [取消] 按鈕新增至 Windows Forms BindingNavigator 控制項
<xref:System.Windows.Forms.BindingNavigator>控制項是特殊用途<xref:System.Windows.Forms.ToolStrip>適用於瀏覽和操作您的表單上繫結至資料的控制項的控制項。  
  
 因為它是<xref:System.Windows.Forms.ToolStrip>控制項，<xref:System.Windows.Forms.BindingNavigator>元件可以輕鬆地修改以包含使用者的額外或其他命令。  
  
 在下列程序中，<xref:System.Windows.Forms.TextBox>控制項繫結至資料，而<xref:System.Windows.Forms.ToolStrip>控制項加入至表單，會修改成包含載入、 儲存和取消按鈕。  
  
### <a name="to-add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>若要將載入、 儲存，和 [取消] 按鈕至 BindingNavigator 元件  
  
1. 新增 <xref:System.Windows.Forms.TextBox> 控制項至表單。  
  
2. 繫結到<xref:System.Windows.Forms.BindingSource>，它會繫結至資料來源。 此範例中，針對<xref:System.Windows.Forms.BindingSource>繫結至資料庫。  
  
3. 產生資料集和資料表配接器之後，請將<xref:System.Windows.Forms.BindingNavigator>控制項加入表單。  
  
4. 設定<xref:System.Windows.Forms.BindingNavigator>控制項的<xref:System.Windows.Forms.BindingNavigator.BindingSource%2A>屬性設<xref:System.Windows.Forms.BindingSource>繫結至控制項在表單上。  
  
5. 選取 <xref:System.Windows.Forms.BindingNavigator> 控制項。  
  
6. 按一下智慧標籤圖像 (![智慧標籤圖像](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 因此**BindingNavigator 工作** 對話方塊隨即出現，並選取**編輯項目**.  
  
     **項目集合編輯器**隨即出現。  
  
7. 在 **項目集合編輯器**，完成下列步驟：  
  
    1. 新增<xref:System.Windows.Forms.ToolStripSeparator>和三個<xref:System.Windows.Forms.ToolStripButton>藉由選取適當類型的項目<xref:System.Windows.Forms.ToolStripItem>，然後按一下**新增** 按鈕。  
  
    2. 設定<xref:System.Windows.Forms.ToolStripItem.Name%2A> 按鈕的屬性**LoadButton**， **SaveButton**，和**CancelButton**分別。  
  
    3. 設定<xref:System.Windows.Forms.ToolStripItem.Text%2A> 按鈕的屬性**負載**，**儲存**，和**取消**。  
  
    4. 設定<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> 按鈕的每個屬性**文字**。 或者，您可以設定此屬性，**映像**或是**ImageAndText**，並設定要顯示在影像<xref:System.Windows.Forms.ToolStripItem.Image%2A>屬性。  
  
    5. 按一下 **確定**以關閉對話方塊。按鈕會新增至<xref:System.Windows.Forms.ToolStrip>。  
  
8. 以滑鼠右鍵按一下表單，然後選擇 **檢視程式碼**。  
  
9. 在程式碼編輯器中，找到資料載入資料表配接器的程式碼的行。 當您設定在步驟 2 中的資料繫結時，所產生此程式碼。 程式碼應該類似下面的： `TableAdapterName.Fill(DataSetName.TableName)`。 它會最可能會出現在表單的<xref:System.Windows.Forms.Form.Load>事件。  
  
10. 建立事件處理常式<xref:System.Windows.Forms.ToolStripItem.Click>事件的**負載**<xref:System.Windows.Forms.ToolStripButton>您稍早建立，並將此資料載入程式碼移到它。  
  
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
  
11. 建立事件處理常式<xref:System.Windows.Forms.ToolStripItem.Click>事件的**儲存**<xref:System.Windows.Forms.ToolStripButton>您在稍早所建立，並撰寫程式碼來更新資料表控制項中的資料繫結至。  
  
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
    > 在某些情況下，<xref:System.Windows.Forms.BindingNavigator>元件已經**儲存** 按鈕，但沒有程式碼將產生的 Windows Form 設計工具。 在此情況下，您可以將上述程式碼中的放<xref:System.Windows.Forms.ToolStripItem.Click>該按鈕，而不是建立全新的按鈕上的事件處理常式<xref:System.Windows.Forms.ToolStrip>。 不過，按鈕預設會停用，因此您必須設定<xref:System.Windows.Forms.ToolBarButton.Enabled%2A>屬性的按鈕`true`正確有按鈕函式。
  
12. 建立事件處理常式<xref:System.Windows.Forms.ToolStripItem.Click>事件的**取消**<xref:System.Windows.Forms.ToolStripButton>您稍早建立，並撰寫程式碼來取消資料記錄顯示的任何變更。  
  
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
    >  <xref:System.Windows.Forms.BindingSource.CancelEdit%2A>方法的範圍為資料的資料列。 儲存您在檢視該個別記錄之前瀏覽至下一筆記錄時所做的任何變更。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [BindingNavigator 控制項](bindingnavigator-control-windows-forms.md)
- [BindingSource 元件概觀](bindingsource-component-overview.md)
