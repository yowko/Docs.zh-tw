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
ms.openlocfilehash: 61a79b9bbe101d7bf694240bdffdecee5187adf2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182326"
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a>如何：加強 ToolStripMenuItems 的功能
您可以通過以下方式增強 和<xref:System.Windows.Forms.MenuStrip><xref:System.Windows.Forms.ContextMenuStrip>控制項的可用性：  
  
- 添加核取記號以指定要素是打開還是關閉，例如尺規是沿文書處理應用程式的邊距顯示，還是指示顯示檔案清單中的檔，例如**視窗**功能表上的檔。  
  
- 添加視覺上表示功能表命令的圖像。  
  
- 顯示快速鍵，以提供用於執行命令的滑鼠的鍵盤替代方案。 例如，按 CTRL_C 執行**複製**命令。  
  
- 顯示便捷鍵，為功能表導航提供滑鼠的鍵盤替代方案。 例如，按 ALT+F 選擇 **"檔**"功能表。  
  
- 顯示分隔線以對相關命令進行分組，並使功能表更具可讀性。  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a>在功能表命令上顯示核取記號  
  
- 將其<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>屬性設置為`true`。  
  
     這還將<xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A>屬性設置到`true`。 僅當希望功能表命令預設顯示為選中時，才使用此過程，而不管是否選擇了該命令。  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a>顯示每次按一下更改狀態的核取記號  
  
- 將功能表命令的屬性<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>設置為`true`。  
  
### <a name="to-add-an-image-to-a-menu-command"></a>將圖像添加到功能表命令  
  
- 將功能表命令的屬性<xref:System.Windows.Forms.ToolStripItem.Image%2A>設置為圖像的名稱。 如果此<xref:System.Windows.Forms.ToolStripItemDisplayStyle>功能表命令的屬性設置為<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>或<xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>，則無法顯示圖像。  
  
> [!NOTE]
> 如果願意，圖像邊距也可以顯示核取記號。 此外，您可以將圖像<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>的屬性設置為`true`，並且圖像將在運行時以填充邊框出現在圖像周圍。  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a>顯示功能表命令的快速鍵  
  
- 將<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>功能表命令的屬性設置為所需的鍵盤組合，如 **"打開**"功能表命令的 CTRL_O，並將<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>該屬性設置為`true`。  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a>顯示功能表命令的自訂快速鍵  
  
- 將功能表命令的屬性<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A>設置為所需的鍵盤組合，如 CTRL_SHIFT_O 而不是 SHIFT_CTRL_O，並將<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>該屬性設置為`true`。  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a>顯示功能表命令的便捷鍵  
  
- 設置功能表命令的屬性<xref:System.Windows.Forms.ToolStripItem.Text%2A>時，在要作為便捷鍵底線的字母之前輸入一個 ampersand （&）。 例如，鍵入`&Open`作為功能表項目<xref:System.Windows.Forms.ToolStripItem.Text%2A>的屬性將導致功能表命令顯示為<u>O</u>筆。
  
     要導航到此功能表命令，請按 ALT 將焦點<xref:System.Windows.Forms.MenuStrip>放在 上，然後按功能表名稱的便捷鍵。 當功能表打開並顯示帶有便捷鍵的專案時，您只需按便捷鍵即選擇功能表命令。  
  
> [!NOTE]
> 避免定義重複的便捷鍵，例如在同一功能表系統中兩次定義 ALT+F。 無法保證重複訪問金鑰的選擇順序。  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a>在功能表命令之間顯示分隔符號  
  
- <xref:System.Windows.Forms.MenuStrip>定義及其將包含的專案後，使用<xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A>或<xref:System.Windows.Forms.ToolStripItemCollection.Add%2A>方法按所需順序將功能表命令和<xref:System.Windows.Forms.ToolStripSeparator>控制項添加到 。 <xref:System.Windows.Forms.MenuStrip>  
  
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

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [MenuStrip 控制項概觀](menustrip-control-overview-windows-forms.md)
