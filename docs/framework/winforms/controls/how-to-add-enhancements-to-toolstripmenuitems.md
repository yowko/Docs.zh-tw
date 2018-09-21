---
title: 如何：加強 ToolStripMenuItems 的功能
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- commands [Windows Forms], grouping on menus
- check marks [Windows Forms], adding to menus
- ToolStripMenuItems [Windows Forms], displaying access keys
- menus [Windows Forms], grouping commands
- menu items [Windows Forms], displaying shortcut keys
- ToolStripMenuItems
- separators [Windows Forms], displaying on menus
- menu items [Windows Forms], showing separators
- menu items [Windows Forms], adding check marks
- ToolStripMenuItems [Windows Forms], adding check marks
- menu items [Windows Forms], adding images
- ToolStripSeparators [Windows Forms], displaying on MenuStrips
- menu items [Windows Forms], displaying access keys
- ToolStripMenuItems [Windows Forms], displaying shortcut keys
- ToolStripMenuItems [Windows Forms], adding images
- keyboard shortcuts [Windows Forms], displaying on menus
- images [Windows Forms], adding to menus
- ToolStripMenuItems [Windows Forms], showing separator bars
ms.assetid: aa5f19bb-b545-4378-bfa6-36ba592f0d7c
ms.openlocfilehash: eb55796480bea896383da479fe23a5d8967a52e3
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46529111"
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a>如何：加強 ToolStripMenuItems 的功能
您可以增強的可用性<xref:System.Windows.Forms.MenuStrip>和<xref:System.Windows.Forms.ContextMenuStrip>控制項如下：  
  
-   新增指定一項功能開啟或關閉，例如沿著文書處理應用程式，邊界是否顯示尺規，或指出的檔案清單中的檔案正在顯示，例如上的核取記號**視窗**功能表。  
  
-   新增以視覺方式表示功能表命令的映像。  
  
-   顯示要執行命令提供替代滑鼠的鍵盤快速鍵。 例如，按下 CTRL + C 會執行**複製**命令。  
  
-   顯示存取金鑰 功能表導覽提供替代滑鼠的鍵盤。 例如，按下 ALT + F 會選擇**檔案**功能表。  
  
-   顯示分組相關的命令，並讓功能表更容易閱讀的分隔線。  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a>若要顯示功能表命令上的核取記號  
  
-   設定其<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>屬性設`true`。  
  
     這也會設定<xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A>屬性設`true`。 只有當您想要顯示為已核取，根據預設，不論是否選取的功能表命令，請使用此程序。  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a>若要顯示 變更狀態時，使用每按一下核取記號  
  
-   將功能表命令的<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>屬性設`true`。  
  
### <a name="to-add-an-image-to-a-menu-command"></a>若要將影像加入功能表命令  
  
-   將功能表命令的<xref:System.Windows.Forms.ToolStripItem.Image%2A>映像名稱的屬性。 如果<xref:System.Windows.Forms.ToolStripItemDisplayStyle>這個功能表命令的屬性設定為<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>或<xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>，無法顯示影像。  
  
> [!NOTE]
>  影像邊界也可以顯示勾號，是否您選擇如此。 此外，您可以設定<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>映像，以屬性`true`，並具有其周圍的陰影框線呈現的影像，就將它在執行階段。  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a>若要顯示的功能表命令的快速鍵  
  
-   將功能表命令的<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>屬性所需要的鍵盤組合，例如 CTRL + O**開啟**功能表命令，以及組<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>屬性設`true`。  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a>若要顯示的功能表命令的自訂快速鍵  
  
-   將功能表命令的<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A>屬性所需要的鍵盤組合，例如 CTRL + SHIFT + O，而非 SHIFT + CTRL + O，以及組<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>屬性設`true`。  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a>若要顯示的功能表命令的存取金鑰  
  
-   當您將設定<xref:System.Windows.Forms.ToolStripItem.Text%2A>屬性功能表命令，請輸入連字號 (&) 您想要作為便捷鍵加上底線的字母前面。 例如，輸入`&Open`作為<xref:System.Windows.Forms.ToolStripItem.Text%2A>功能表項目的屬性會顯示為功能表命令<u>O</u>畫筆。
  
     瀏覽至這個功能表命令、 按下 ALT 以焦點轉給<xref:System.Windows.Forms.MenuStrip>，然後按 的功能表名稱的存取金鑰。 當功能表會隨即開啟，並顯示具有便捷鍵的項目時，您只需要按下便捷鍵以選取功能表命令。  
  
> [!NOTE]
>  應避免定義重複的便捷鍵，例如定義相同的功能表系統中的兩倍的 ALT + F。 重複的便捷鍵的選取項目順序，將無法保證。  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a>若要顯示功能表命令之間的分隔線  
  
-   定義之後您<xref:System.Windows.Forms.MenuStrip>和項目會包含使用<xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A>或是<xref:System.Windows.Forms.ToolStripItemCollection.Add%2A>方法來加入功能表命令和<xref:System.Windows.Forms.ToolStripSeparator>控制項新增至<xref:System.Windows.Forms.MenuStrip>您想要的順序。  
  
    ```vb  
    ' This code adds a top-level File menu to the MenuStrip.  
    Me.menuStrip1.Items.Add(New ToolStripMenuItem() _  
    {Me.fileToolStripMenuItem})  
  
    ' This code adds the New and Open menu commands, a separator bar,   
    ' and the Save and Exit menu commands to the top-level File menu,   
    ' in that order.  
    Me.fileToolStripMenuItem.DropDownItems.AddRange(New _  
    ToolStripMenuItem() {Me.newToolStripMenuItem, _  
    Me.openToolStripMenuItem, Me.toolStripSeparator1, _  
    Me.saveToolStripMenuItem, Me.exitToolStripMenuItem})  
    ```  
  
    ```csharp  
    // This code adds a top-level File menu to the MenuStrip.  
    this.menuStrip1.Items.Add(new ToolStripItem[]_  
    {this.fileToolStripMenuItem});  
  
    // This code adds the New and Open menu commands, a separator bar,   
    // and the Save and Exit menu commands to the top-level File menu,   
    // in that order.  
    this.fileToolStripMenuItem.DropDownItems.AddRange(new _  
    ToolStripItem[] {  
    this.newToolStripMenuItem,  
    this.openToolStripMenuItem,  
    this.toolStripSeparator1,  
    this.saveToolStripMenuItem,  
    this.exitToolStripMenuItem});  
    ```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [MenuStrip 控制項概觀](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
