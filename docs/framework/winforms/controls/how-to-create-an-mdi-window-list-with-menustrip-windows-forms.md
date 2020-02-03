---
title: 如何：使用 MenuStrip 建立 MDI 視窗清單
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
ms.openlocfilehash: f013c3df2ab5783a22fe2c34402dc53a328cafa2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731016"
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a>如何：使用 MenuStrip 建立 MDI 視窗清單 (Windows Form)
使用多重文件介面（MDI）來建立可同時開啟多份檔的應用程式，並將內容從一份檔案複製並貼到另一份檔。  
  
 此程式說明如何在父系的 [視窗] 功能表上建立所有作用中子表單的清單。  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a>在 MenuStrip 上建立 MDI 視窗清單  
  
1. 建立表單，並將其 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 屬性設定為 `true`。  
  
2. 將 <xref:System.Windows.Forms.MenuStrip> 加入表單。  
  
3. 將兩個最上層功能表項目加入至 <xref:System.Windows.Forms.MenuStrip>，並將其 <xref:System.Windows.Forms.Control.Text%2A> 屬性設定為 [`&File`] 和 [`&Window`]。  
  
4. 將子功能表項目加入 `&File` 功能表項目，並將其 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性設定為 `&Open`。  
  
5. 將 <xref:System.Windows.Forms.MenuStrip> 的 <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> 屬性設定為 `&Window`<xref:System.Windows.Forms.ToolStripMenuItem>。  
  
6. 將表單新增至專案，並新增您想要的控制項，例如另一個 <xref:System.Windows.Forms.MenuStrip>。  
  
7. 為 <xref:System.Windows.Forms.Control.Click>`&New` 的 <xref:System.Windows.Forms.ToolStripMenuItem> 事件建立事件處理常式。  
  
8. 在事件處理常式中，插入與下列類似的程式碼，以建立和顯示 `Form2` 的新實例，做為 `Form1`的 MDI 子系。  
  
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
  
    ```csharp  
    private void newToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
9. 在 `&New`<xref:System.Windows.Forms.ToolStripMenuItem> 中放置類似下列的程式碼，以註冊事件處理常式。  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- 名為 <xref:System.Windows.Forms.Form> 和 `Form1` 的兩個 `Form2` 控制項。  
  
- <xref:System.Windows.Forms.MenuStrip> 上名為 `Form1` 的 `menuStrip1` 控制項，以及 <xref:System.Windows.Forms.MenuStrip> 上名為 `Form2` 的 `menuStrip2` 控制項。  
  
- <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。  
  
## <a name="see-also"></a>另請參閱

- [操作說明：建立 MDI 父表單](../advanced/how-to-create-mdi-parent-forms.md)
- [操作說明：建立 MDI 子表單](../advanced/how-to-create-mdi-child-forms.md)
- [MenuStrip 控制項](menustrip-control-windows-forms.md)
