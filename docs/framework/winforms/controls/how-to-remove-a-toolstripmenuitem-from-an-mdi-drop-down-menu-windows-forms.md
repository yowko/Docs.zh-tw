---
title: HOW TO：從 MDI 下拉式功能表 (Windows Form) 移除 ToolStripMenuItem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], removing from MDI drop-down menus
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], removing
- MDI [Windows Forms], merging menu items
ms.assetid: bdafe60d-82ee-45bc-97fe-eeefca6e54c1
ms.openlocfilehash: 7c84d260783e3a511b5ef6a651c71f1ee55acffe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913155"
---
# <a name="how-to-remove-a-toolstripmenuitem-from-an-mdi-drop-down-menu-windows-forms"></a>HOW TO：從 MDI 下拉式功能表 (Windows Form) 移除 ToolStripMenuItem
在某些應用程式中，多重文件介面 (MDI) 子視窗的類型可能與 MDI 父視窗不同。 例如，MDI 父視窗可能是試算表，而 MDI 子視窗可能是圖表。 在這種情況下，由於已啟動各種不同類型的 MDI 子視窗，因此您需要以 MDI 子視窗功能表的內容更新 MDI 父視窗功能表的內容。  
  
 使用下列程序<xref:System.Windows.Forms.Form.IsMdiContainer%2A>， <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>， <xref:System.Windows.Forms.MergeAction>，和<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>移除功能表項目，從 MDI 父功能表的下拉式部分的屬性。 關閉 MDI 子視窗還原已移除的功能表項目至 MDI 父功能表。  
  
### <a name="to-remove-a-menustrip-from-an-mdi-drop-down-menu"></a>若要從 MDI 下拉式功能表移除 MenuStrip  
  
1. 建立表單，並將其 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 屬性設定為 `true`。  
  
2. 將 <xref:System.Windows.Forms.MenuStrip> 加入 `Form1`，並將 <xref:System.Windows.Forms.MenuStrip> 的 <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> 屬性設定為 `true`。  
  
3. 將最上層功能表項目加入 `Form1`<xref:System.Windows.Forms.MenuStrip>，並將其 <xref:System.Windows.Forms.Control.Text%2A> 屬性設定為 `&File`。  
  
4. 將三個的子功能表項目加入`&File`功能表項目和設定其<xref:System.Windows.Forms.ToolStripItem.Text%2A>屬性，以`&Open`， `&Import from`，和`E&xit`。  
  
5. 將兩個的子功能表項目加入`&Import from`子功能表項目和設定其<xref:System.Windows.Forms.ToolStripItem.Text%2A>屬性，以`&Word`和`&Excel`。  
  
6. 將表單加入專案，將 <xref:System.Windows.Forms.MenuStrip> 加入表單，並將 `Form2`<xref:System.Windows.Forms.MenuStrip> 的 <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> 屬性設定為 `true`。  
  
7. 將最上層功能表項目加入 `Form2`<xref:System.Windows.Forms.MenuStrip>，並將其 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性設定為 `&File`。  
  
8. 新增`&Import from`子功能表項目`&File`功能表`Form2`，並新增`&Word` 子功能表項目`&File`功能表。  
  
9. 設定<xref:System.Windows.Forms.MergeAction>並<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>屬性的`Form2`下表所示的功能表項目。  
  
    |Form2 功能表項目|MergeAction 值|MergeIndex 值|  
    |---------------------|-----------------------|----------------------|  
    |檔案|MatchOnly|-1|  
    |從匯入|MatchOnly|-1|  
    |字組|移除|-1|  
  
10. 在  `Form1`，建立事件處理常式<xref:System.Windows.Forms.Control.Click>事件`&Open` <xref:System.Windows.Forms.ToolStripMenuItem>。  
  
11. 在事件處理常式中，插入類似下列的程式碼範例，以建立及顯示的新執行個體的程式碼`Form2`做為 MDI 子系的`Form1`:  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
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
  
12. 將類似下列程式碼範例的程式碼放入 `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> 之中，以註冊事件處理常式。  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new _  
    System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   名為 `Form1` 和 `Form2` 的兩個 <xref:System.Windows.Forms.Form> 控制項。  
  
-   `Form1` 上名為 `menuStrip1` 的 <xref:System.Windows.Forms.MenuStrip> 控制項，以及 `Form2` 上名為 `menuStrip2` 的 <xref:System.Windows.Forms.MenuStrip> 控制項。  
  
-   <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。  
  
## <a name="see-also"></a>另請參閱

- [如何：建立 MDI 父表單](../advanced/how-to-create-mdi-parent-forms.md)
- [如何：建立 MDI 子表單](../advanced/how-to-create-mdi-child-forms.md)
- [MenuStrip 控制項概觀](menustrip-control-overview-windows-forms.md)
