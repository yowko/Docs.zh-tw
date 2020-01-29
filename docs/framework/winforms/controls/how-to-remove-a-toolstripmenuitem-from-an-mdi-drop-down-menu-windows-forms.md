---
title: 如何：從 MDI 下拉式功能表移除 ToolStripMenuItem
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
ms.openlocfilehash: 3198195cf0991734826508aa65818505bf2038c8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735847"
---
# <a name="how-to-remove-a-toolstripmenuitem-from-an-mdi-drop-down-menu-windows-forms"></a>如何：從 MDI 下拉式功能表移除 ToolStripMenuItem (Windows Form)
在某些應用程式中，多重文件介面 (MDI) 子視窗的類型可能與 MDI 父視窗不同。 例如，MDI 父視窗可能是試算表，而 MDI 子視窗可能是圖表。 在這種情況下，由於已啟動各種不同類型的 MDI 子視窗，因此您需要以 MDI 子視窗功能表的內容更新 MDI 父視窗功能表的內容。  
  
 下列程式會使用 [<xref:System.Windows.Forms.Form.IsMdiContainer%2A>]、[<xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>]、[<xref:System.Windows.Forms.MergeAction>] 和 [<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>] 屬性，從 MDI 父功能表的下拉式部分移除功能表項目。 關閉 MDI 子視窗會將已移除的功能表項目還原至 MDI 父功能表。  
  
### <a name="to-remove-a-menustrip-from-an-mdi-drop-down-menu"></a>若要從 MDI 下拉式功能表移除 MenuStrip  
  
1. 建立表單，並將其 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 屬性設定為 `true`。  
  
2. 將 <xref:System.Windows.Forms.MenuStrip> 加入 `Form1`，並將 <xref:System.Windows.Forms.MenuStrip> 的 <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> 屬性設定為 `true`。  
  
3. 將最上層功能表項目加入 `Form1`<xref:System.Windows.Forms.MenuStrip>，並將其 <xref:System.Windows.Forms.Control.Text%2A> 屬性設定為 `&File`。  
  
4. 將三個子功能表項目目新增至 [`&File`] 功能表項目，並將其 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性設定為 [`&Open`]、[`&Import from`] 和 [`E&xit`]。  
  
5. 將兩個子功能表項目目新增至 [`&Import from`] 子功能表專案，並將其 [<xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性] 設定為 `&Word` 和 `&Excel`。  
  
6. 將表單加入專案，將 <xref:System.Windows.Forms.MenuStrip> 加入表單，並將 `Form2`<xref:System.Windows.Forms.MenuStrip> 的 <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> 屬性設定為 `true`。  
  
7. 將最上層功能表項目加入 `Form2`<xref:System.Windows.Forms.MenuStrip>，並將其 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性設定為 `&File`。  
  
8. 將 `&Import from` 子功能表專案新增至 `Form2`的 [`&File`] 功能表，並將 [`&Word`] 子功能表專案新增至 [`&File`] 功能表。  
  
9. 設定 `Form2` 功能表項目的 <xref:System.Windows.Forms.MergeAction> 和 <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> 屬性，如下表所示。  
  
    |Form2 功能表項目|MergeAction 值|MergeIndex 值|  
    |---------------------|-----------------------|----------------------|  
    |File|MatchOnly|-1|  
    |從  匯入|MatchOnly|-1|  
    |Word|Remove|-1|  
  
10. 在 `Form1`中，為 `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>的 <xref:System.Windows.Forms.Control.Click> 事件建立事件處理常式。  
  
11. 在事件處理常式中，插入類似下列程式碼範例的程式碼，以建立和顯示 `Form2` 的新實例，做為 `Form1`的 MDI 子系：  
  
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
  
- 名為 `Form1` 和 `Form2` 的兩個 <xref:System.Windows.Forms.Form> 控制項。  
  
- `Form1` 上名為 `menuStrip1` 的 <xref:System.Windows.Forms.MenuStrip> 控制項，以及 `Form2` 上名為 `menuStrip2` 的 <xref:System.Windows.Forms.MenuStrip> 控制項。  
  
- <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。  
  
## <a name="see-also"></a>請參閱

- [操作說明：建立 MDI 父表單](../advanced/how-to-create-mdi-parent-forms.md)
- [操作說明：建立 MDI 子表單](../advanced/how-to-create-mdi-child-forms.md)
- [MenuStrip 控制項概觀](menustrip-control-overview-windows-forms.md)
