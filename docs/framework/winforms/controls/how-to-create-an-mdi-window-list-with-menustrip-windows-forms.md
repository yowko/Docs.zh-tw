---
title: 如何：使用 MenuStrip 建立 MDI 視窗清單 (Windows Form)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
ms.openlocfilehash: c87ffadaef2842f10d40f6fd84eb1c70c6dfe37e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530818"
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a>如何：使用 MenuStrip 建立 MDI 視窗清單 (Windows Form)
使用多重文件介面 (MDI) 建立應用程式，可以開啟數個文件在相同的時間和複製並貼至另一份文件內容。  
  
 此程序會示範如何建立父視窗功能表上的所有作用中的子表單清單。  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a>若要在 MenuStrip 建立 MDI 視窗清單  
  
1.  建立表單，並將其 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 屬性設定為 `true`。  
  
2.  將 <xref:System.Windows.Forms.MenuStrip> 加入表單。  
  
3.  將兩個最上層功能表項目加入<xref:System.Windows.Forms.MenuStrip>並設定其<xref:System.Windows.Forms.Control.Text%2A>屬性`&File`和`&Window`。  
  
4.  將子功能表項目加入 `&File` 功能表項目，並將其 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 屬性設定為 `&Open`。  
  
5.  設定<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>屬性<xref:System.Windows.Forms.MenuStrip>至`&Window` <xref:System.Windows.Forms.ToolStripMenuItem>。  
  
6.  將表單加入專案，並加入您想要的控制項，例如另一個<xref:System.Windows.Forms.MenuStrip>。  
  
7.  為 `&New`<xref:System.Windows.Forms.ToolStripMenuItem> 的 <xref:System.Windows.Forms.Control.Click> 事件建立事件處理常式。  
  
8.  在事件處理常式中，插入類似下列的建立和顯示的新執行個體的程式碼`Form2`的 MDI 子系`Form1`。  
  
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
  
9. 將放在下列類似的程式碼`&New`<xref:System.Windows.Forms.ToolStripMenuItem>以註冊事件處理常式。  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   名為 `Form1` 和 `Form2` 的兩個 <xref:System.Windows.Forms.Form> 控制項。  
  
-   `Form1` 上名為 `menuStrip1` 的 <xref:System.Windows.Forms.MenuStrip> 控制項，以及 `Form2` 上名為 `menuStrip2` 的 <xref:System.Windows.Forms.MenuStrip> 控制項。  
  
-   <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。  
  
## <a name="see-also"></a>另請參閱  
 [操作說明：建立 MDI 父表單](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [操作說明：建立 MDI 子表單](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [MenuStrip 控制項](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
