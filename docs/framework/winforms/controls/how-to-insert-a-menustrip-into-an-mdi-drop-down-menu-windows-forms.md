---
title: HOW TO：將 MenuStrip 插入至 MDI 下拉式功能表 (Windows Form)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], inserting
- MenuStrip control [Windows Forms], merging
- MDI [Windows Forms], merging menu items
ms.assetid: 0fad444e-26d9-49af-8860-044d9c10d608
ms.openlocfilehash: 1c0ee8c7029639d6911dbb80657ce03068223246
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147559"
---
# <a name="how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms"></a>HOW TO：將 MenuStrip 插入至 MDI 下拉式功能表 (Windows Form)
在某些應用程式中，多重文件介面 (MDI) 子視窗的類型可能與 MDI 父視窗不同。 例如，MDI 父視窗可能是試算表，而 MDI 子視窗可能是圖表。 在這種情況下，由於已啟動各種不同類型的 MDI 子視窗，因此您需要以 MDI 子視窗功能表的內容更新 MDI 父視窗功能表的內容。  
  
 使用下列程序<xref:System.Windows.Forms.Form.IsMdiContainer%2A>， <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>， <xref:System.Windows.Forms.MergeAction>，和<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>屬性，以從 MDI 子功能表中插入 MDI 父功能表的下拉式部分的功能表項目群組。 關閉 MDI 子視窗，是在 MDI 父視窗中移除插入的功能表項目。  
  
### <a name="to-insert-a-menustrip-into-an-mdi-drop-down-menu"></a>若要將 MenuStrip 插入至 MDI 下拉式功能表  
  
1.  建立表單，並將其 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 屬性設定為 `true`。  
  
2.  將 <xref:System.Windows.Forms.MenuStrip> 加入 `Form1`，並將 <xref:System.Windows.Forms.MenuStrip> 的 <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> 屬性設定為 `true`。  
  
3.  將最上層功能表項目，加入`Form1`<xref:System.Windows.Forms.MenuStrip>並將其<xref:System.Windows.Forms.Control.Text%2A>屬性設`&File`。  
  
4.  將三個的子功能表項目加入`&File`功能表項目和設定其<xref:System.Windows.Forms.ToolStripItem.Text%2A>屬性，以`&Open`， `&Import from`，和`E&xit`。  
  
5.  將兩個的子功能表項目加入`&Import from`子功能表項目和設定其<xref:System.Windows.Forms.ToolStripItem.Text%2A>屬性，以`&Word`和`&Excel`。  
  
6.  將表單加入專案，加入<xref:System.Windows.Forms.MenuStrip>至表單，並將<xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>屬性`Form2`<xref:System.Windows.Forms.MenuStrip>至`true`。  
  
7.  將最上層功能表項目，加入`Form2`<xref:System.Windows.Forms.MenuStrip>並將其<xref:System.Windows.Forms.ToolStripItem.Text%2A>屬性設`&File`。  
  
8.  將子功能表項目加入`&File`功能表`Form2`順序如下： <xref:System.Windows.Forms.ToolStripSeparator>， `&Save`， `Save and &Close`，和另一個<xref:System.Windows.Forms.ToolStripSeparator>。  
  
9. 設定<xref:System.Windows.Forms.MergeAction>並<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>屬性的`Form2`下表所示的功能表項目。  
  
    |Form2 功能表項目|MergeAction 值|MergeIndex 值|  
    |---------------------|-----------------------|----------------------|  
    |檔案|MatchOnly|-1|  
    |Separator|Insert|2|  
    |儲存|Insert|3|  
    |儲存並關閉|Insert|4|  
    |Separator|Insert|5|  
  
10. 建立事件處理常式<xref:System.Windows.Forms.Control.Click>事件的`&Open`<xref:System.Windows.Forms.ToolStripMenuItem>。  
  
11. 在事件處理常式中，插入類似下列程式碼範例的程式碼，以建立和顯示 `Form2` 的新執行個體，做為 `Form1` 的 MDI 子視窗。  
  
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
  
12. 將程式碼放在類似下列程式碼範例在`&Open`<xref:System.Windows.Forms.ToolStripMenuItem>註冊事件處理常式。  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   名為 `Form1` 和 `Form2` 的兩個 <xref:System.Windows.Forms.Form> 控制項。  
  
-   `Form1` 上名為 `menuStrip1` 的 <xref:System.Windows.Forms.MenuStrip> 控制項，以及 `Form2` 上名為 `menuStrip2` 的 <xref:System.Windows.Forms.MenuStrip> 控制項。  
  
-   <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。  
  
## <a name="see-also"></a>另請參閱

- [HOW TO：建立 MDI 父表單](../advanced/how-to-create-mdi-parent-forms.md)
- [HOW TO：建立 MDI 子表單](../advanced/how-to-create-mdi-child-forms.md)
- [MenuStrip 控制項概觀](menustrip-control-overview-windows-forms.md)
