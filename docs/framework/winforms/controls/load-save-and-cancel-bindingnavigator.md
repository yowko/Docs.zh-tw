---
title: 將 [載入]、[儲存] 和 [取消] 按鈕新增至 BindingNavigator 控制項
description: 瞭解如何將 [載入]、[儲存] 和 [取消] 按鈕新增至 Windows Forms BindingNavigator 控制項。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: d4db91b8cfaf2df253d0c4cf5d8a66e9157d4986
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173415"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>如何：將載入、儲存和取消按鈕加入至 Windows Form BindingNavigator 控制項

<xref:System.Windows.Forms.BindingNavigator>控制項是一個特殊用途的 <xref:System.Windows.Forms.ToolStrip> 控制項，用於導覽和操作表單上系結至資料的控制項。

因為它是 <xref:System.Windows.Forms.ToolStrip> 控制項，所以 <xref:System.Windows.Forms.BindingNavigator> 可以輕鬆地修改元件以包含使用者的其他或替代命令。

在下列程式中，控制項系結 <xref:System.Windows.Forms.TextBox> 至資料，而 <xref:System.Windows.Forms.ToolStrip> 新增至表單的控制項則會修改為包含 [載入]、[儲存] 和 [取消] 按鈕。

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>將 [載入]、[儲存] 和 [取消] 按鈕新增至 BindingNavigator 元件

1. 在 Visual Studio 中，將 <xref:System.Windows.Forms.TextBox> 控制項新增至表單。

2. 將它系結至系結 <xref:System.Windows.Forms.BindingSource> 至資料來源的。 在此範例中， <xref:System.Windows.Forms.BindingSource> 會系結至資料庫。

3. 產生資料集和資料表介面卡之後，將 <xref:System.Windows.Forms.BindingNavigator> 控制項拖曳至表單。

4. 在系結 <xref:System.Windows.Forms.BindingNavigator> <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> <xref:System.Windows.Forms.BindingSource> 至控制項的表單上，將控制項的屬性設定為。

5. 選取 <xref:System.Windows.Forms.BindingNavigator> 控制項。

6. 按一下 [設計工具動作] 圖像 (![ 小型黑色箭號 ](./media/designer-actions-glyph.gif)) 讓 [ **BindingNavigator**工作] 對話方塊出現，然後選取 [**編輯專案**]。

     [**專案集合編輯器**] 隨即出現。

7. 在 [**專案集合編輯器**] 中，完成下列步驟：

    1. <xref:System.Windows.Forms.ToolStripSeparator> <xref:System.Windows.Forms.ToolStripButton> 選取適當的類型 <xref:System.Windows.Forms.ToolStripItem> ，然後按一下 [**新增**] 按鈕，以新增 a 和三個專案。

    2. 將 <xref:System.Windows.Forms.ToolStripItem.Name%2A> 按鈕的屬性分別設定為**LoadButton**、 **SaveButton**和**CancelButton**。

    3. 將 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 按鈕的屬性設定為 [**載入**]、[**儲存**] 和 [**取消**]。

    4. 將 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> 每個按鈕的屬性設為 [**文字**]。 或者，您可以將此屬性設定為**Image**或**ImageAndText**，並設定要在屬性中顯示的影像 <xref:System.Windows.Forms.ToolStripItem.Image%2A> 。

    5. 按一下 [確定]  關閉對話方塊。 這些按鈕會新增至 <xref:System.Windows.Forms.ToolStrip> 。

8. 以滑鼠右鍵按一下表單，然後選擇 [ **View Code**]。

9. 在 [程式碼編輯器] 中，尋找將資料載入資料表介面卡的程式程式碼。 當您在步驟2中設定資料系結時，就會產生此程式碼。 程式碼應如下所示： `TableAdapterName.Fill(DataSetName.TableName)` 。 這很可能會在表單的 <xref:System.Windows.Forms.Form.Load> 事件中。

10. 針對 <xref:System.Windows.Forms.ToolStripItem.Click> 您稍早建立之**負載**的事件建立事件處理常式 <xref:System.Windows.Forms.ToolStripButton> ，並將此資料載入程式碼移至其中。

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

11. 針對 <xref:System.Windows.Forms.ToolStripItem.Click> 您稍早建立之**儲存**的事件建立事件處理常式 <xref:System.Windows.Forms.ToolStripButton> ，並撰寫程式碼以更新控制項所系結之資料表中的資料。

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
    > 在某些情況下， <xref:System.Windows.Forms.BindingNavigator> 元件已經有 [**儲存**] 按鈕，但 Windows Form 設計工具未產生任何程式碼。 在這種情況下，您可以將上述程式碼放在 <xref:System.Windows.Forms.ToolStripItem.Click> 該按鈕的事件處理常式中，而不是在上建立全新的按鈕 <xref:System.Windows.Forms.ToolStrip> 。 不過，按鈕預設為停用，因此您必須將按鈕的 <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> 屬性設定為， `true` 才能讓按鈕正常運作。

12. 針對您稍早建立的取消事件建立事件處理常式 <xref:System.Windows.Forms.ToolStripItem.Click> **Cancel** <xref:System.Windows.Forms.ToolStripButton> ，然後撰寫程式碼以取消對所顯示資料記錄所做的任何變更。

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
    > <xref:System.Windows.Forms.BindingSource.CancelEdit%2A>方法的範圍是資料列。 在流覽至下一個記錄之前，請先儲存您在查看該個別記錄時所做的任何變更。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [BindingNavigator 控制項](bindingnavigator-control-windows-forms.md)
- [BindingSource 元件概觀](bindingsource-component-overview.md)
