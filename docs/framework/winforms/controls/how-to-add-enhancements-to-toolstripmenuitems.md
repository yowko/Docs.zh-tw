---
title: 作法：將增強功能新增至 ToolStripMenuItems
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
ms.openlocfilehash: 9e95c3623bf9bad8395f586392a0557ad1cde880
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912576"
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a>HOW TO：將增強功能新增至 ToolStripMenuItems
您可以利用下列方式增強<xref:System.Windows.Forms.MenuStrip>和<xref:System.Windows.Forms.ContextMenuStrip>控制項的可用性:  
  
- 加入核取記號以指定是否開啟或關閉功能, 例如尺規是否會沿著文字處理應用程式的邊界顯示, 或表示要顯示的檔案清單中的哪個檔案, 例如在 [**視窗]** 功能表上。  
  
- 新增以視覺方式表示功能表命令的影像。  
  
- 顯示快速鍵, 以提供鍵盤替代滑鼠來執行命令。 例如, 按下 CTRL + C 會執行 [**複製**] 命令。  
  
- 顯示存取金鑰以提供鍵盤替代滑鼠來流覽功能表。 例如, 按 ALT + F 會選擇 [檔案] 功能表。  
  
- 顯示分隔線以將相關的命令分組, 並讓功能表更容易閱讀。  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a>若要在功能表命令上顯示核取記號  
  
- 將其<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>屬性設`true`為。  
  
     這也會將<xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A>屬性設定`true`為。 只有在您想要讓功能表命令預設顯示為 [已核取] 時 (不論是否已選取), 才使用此程式。  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a>顯示每次點擊時都變更狀態的核取記號  
  
- 將功能表命令的<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>屬性設定為。 `true`  
  
### <a name="to-add-an-image-to-a-menu-command"></a>將影像新增至功能表命令  
  
- 將功能表命令的<xref:System.Windows.Forms.ToolStripItem.Image%2A>屬性設定為映射的名稱。 如果此<xref:System.Windows.Forms.ToolStripItemDisplayStyle>功能表命令的屬性設定為<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>或<xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, 則無法顯示影像。  
  
> [!NOTE]
> 如果您選擇, 影像邊界也可以顯示核取記號。 此外, 您可以將影像<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>的屬性設定為`true`, 而且影像會在執行時間以陰影框線括住。  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a>若要顯示功能表命令的快速鍵  
  
- 將功能表命令<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>的屬性設為所需的鍵盤組合 (例如, CTRL + O 用於 [**開啟**] 功能表命令<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> ), 並將屬性設定為。 `true`  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a>若要顯示功能表命令的自訂快速鍵  
  
- 將功能表命令的<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A>屬性設為所需的鍵盤組合, 例如 CTRL + SHIFT + o, 而不是 SHIFT + CTRL + o, 然後<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>將屬性設定為。 `true`  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a>若要顯示功能表命令的存取金鑰  
  
- 當您設定<xref:System.Windows.Forms.ToolStripItem.Text%2A>功能表命令的屬性時, 請在您想要加上底線做為存取金鑰的字母前面輸入連字號 (&)。 例如, 輸入`&Open`做為功能表<xref:System.Windows.Forms.ToolStripItem.Text%2A>項的屬性, 將會產生顯示為 [ <u>O</u>畫筆] 的功能表命令。
  
     若要流覽至此功能表命令, 請按下 ALT 將焦點放<xref:System.Windows.Forms.MenuStrip>在, 然後按下功能表名稱的存取金鑰。 當功能表開啟並顯示具有存取金鑰的專案時, 您只需要按下存取金鑰, 即可選取功能表命令。  
  
> [!NOTE]
> 避免在相同的功能表系統中定義重複的存取金鑰, 例如定義 ALT + F 兩次。 無法保證重複存取金鑰的選取順序。  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a>若要在功能表命令之間顯示分隔線  
  
- 定義<xref:System.Windows.Forms.MenuStrip>和它將包含的專案之後, 請<xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A>使用或<xref:System.Windows.Forms.ToolStripItemCollection.Add%2A>方法, 依您想要的順序, <xref:System.Windows.Forms.ToolStripSeparator> <xref:System.Windows.Forms.MenuStrip>將功能表命令和控制項加入至。  
  
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
