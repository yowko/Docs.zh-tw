---
title: 如何：將 MenuStrip 附加至 MDI 父視窗 (Windows Form)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], appending
- MDI [Windows Forms], merging menu items
ms.assetid: ab70c936-b452-4653-b417-17be57bb795b
ms.openlocfilehash: 048add340a81856cd30482c52c93c76bbf6181f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529551"
---
# <a name="how-to-append-a-menustrip-to-an-mdi-parent-window-windows-forms"></a>如何：將 MenuStrip 附加至 MDI 父視窗 (Windows Form)
在某些應用程式中，多重文件介面 (MDI) 子視窗的類型可能與 MDI 父視窗不同。 例如，MDI 父視窗可能是試算表，而 MDI 子視窗可能是圖表。 在這種情況下，由於已啟動各種不同類型的 MDI 子視窗，因此您需要以 MDI 子視窗功能表的內容更新 MDI 父視窗功能表的內容。  
  
 下列程序使用 <xref:System.Windows.Forms.Form.IsMdiContainer%2A>、<xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>、<xref:System.Windows.Forms.MergeAction> 和 <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> 屬性，將 MDI 子功能表附加至 MDI 父功能表。 關閉 MDI 子視窗會將附加的功能表從 MDI 父視窗中移除。  
  
 另請參閱[多重文件介面 (MDI) 應用程式](http://msdn.microsoft.com/library/xyhh2e7e\(v=vs.110\))。  
  
### <a name="to-append-a-menu-item-to-an-mdi-parent"></a>將功能表項目附加至 MDI 父視窗  
  
1.  建立表單，並將其 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 屬性設定為 `true`。  
  
2.  將 <xref:System.Windows.Forms.MenuStrip> 加入 `Form1`，並將 <xref:System.Windows.Forms.MenuStrip> 的 <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> 屬性設定為 `true`。  
  
3.  將 `Form1`<xref:System.Windows.Forms.MenuStrip> 的 <xref:System.Windows.Forms.ToolStripItem.Visible%2A> 屬性設定為 `false`。  
  
4.  將最上層功能表項目加入 `Form1`<xref:System.Windows.Forms.MenuStrip>，並將其 <xref:System.Windows.Forms.Control.Text%2A> 屬性設定為 `&File`。  
  
5.  將子功能表項目加入 `&File` 功能表項目，並將其 <xref:System.Windows.Forms.Form.Text%2A> 屬性設定為 `&Open`。  
  
6.  將表單加入專案，將 <xref:System.Windows.Forms.MenuStrip> 加入表單，並將 `Form2`<xref:System.Windows.Forms.MenuStrip> 的 <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> 屬性設定為 `true`。  
  
7.  將最上層功能表項目加入 `Form2`<xref:System.Windows.Forms.MenuStrip>，並將其 <xref:System.Windows.Forms.Form.Text%2A> 屬性設定為 `&Special`。  
  
8.  將兩個子功能表項目加入 `&Special` 功能表項目，並將其 <xref:System.Windows.Forms.Form.Text%2A> 屬性分別設定為 `Command&1` 和 `Command&2`。  
  
9. 將 `&Special`、`Command&1` 和 `Command&2` 功能表項目的 <xref:System.Windows.Forms.MergeAction> 屬性設定為 <xref:System.Windows.Forms.MergeAction.Append>。  
  
10. 為 `&New`<xref:System.Windows.Forms.ToolStripMenuItem> 的 <xref:System.Windows.Forms.Control.Click> 事件建立事件處理常式。  
  
11. 在事件處理常式中，插入類似下列程式碼範例的程式碼，以建立和顯示 `Form2` 的新執行個體，做為 `Form1` 的 MDI 子視窗。  
  
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
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   名為 `Form1` 和 `Form2` 的兩個 <xref:System.Windows.Forms.Form> 控制項。  
  
-   `Form1` 上名為 `menuStrip1` 的 <xref:System.Windows.Forms.MenuStrip> 控制項，以及 `Form2` 上名為 `menuStrip2` 的 <xref:System.Windows.Forms.MenuStrip> 控制項。  
  
-   <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。
