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
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a><span data-ttu-id="77840-102">如何：加強 ToolStripMenuItems 的功能</span><span class="sxs-lookup"><span data-stu-id="77840-102">How to: Add Enhancements to ToolStripMenuItems</span></span>
<span data-ttu-id="77840-103">您可以通過以下方式增強 和<xref:System.Windows.Forms.MenuStrip><xref:System.Windows.Forms.ContextMenuStrip>控制項的可用性：</span><span class="sxs-lookup"><span data-stu-id="77840-103">You can enhance the usability of <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> controls in the following ways:</span></span>  
  
- <span data-ttu-id="77840-104">添加核取記號以指定要素是打開還是關閉，例如尺規是沿文書處理應用程式的邊距顯示，還是指示顯示檔案清單中的檔，例如**視窗**功能表上的檔。</span><span class="sxs-lookup"><span data-stu-id="77840-104">Add check marks to designate whether a feature is turned on or off, such as whether a ruler is displayed along the margin of a word-processing application, or to indicate which file in a list of files is being displayed, such as on a **Window** menu.</span></span>  
  
- <span data-ttu-id="77840-105">添加視覺上表示功能表命令的圖像。</span><span class="sxs-lookup"><span data-stu-id="77840-105">Add images that visually represent menu commands.</span></span>  
  
- <span data-ttu-id="77840-106">顯示快速鍵，以提供用於執行命令的滑鼠的鍵盤替代方案。</span><span class="sxs-lookup"><span data-stu-id="77840-106">Display shortcut keys to provide a keyboard alternative to the mouse for performing commands.</span></span> <span data-ttu-id="77840-107">例如，按 CTRL_C 執行**複製**命令。</span><span class="sxs-lookup"><span data-stu-id="77840-107">For example, pressing CTRL+C performs the **Copy** command.</span></span>  
  
- <span data-ttu-id="77840-108">顯示便捷鍵，為功能表導航提供滑鼠的鍵盤替代方案。</span><span class="sxs-lookup"><span data-stu-id="77840-108">Display access keys to provide a keyboard alternative to the mouse for menu navigation.</span></span> <span data-ttu-id="77840-109">例如，按 ALT+F 選擇 **"檔**"功能表。</span><span class="sxs-lookup"><span data-stu-id="77840-109">For example, pressing ALT+F chooses the **File** menu.</span></span>  
  
- <span data-ttu-id="77840-110">顯示分隔線以對相關命令進行分組，並使功能表更具可讀性。</span><span class="sxs-lookup"><span data-stu-id="77840-110">Show separator bars to group related commands and make menus more readable.</span></span>  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a><span data-ttu-id="77840-111">在功能表命令上顯示核取記號</span><span class="sxs-lookup"><span data-stu-id="77840-111">To display a check mark on a menu command</span></span>  
  
- <span data-ttu-id="77840-112">將其<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>屬性設置為`true`。</span><span class="sxs-lookup"><span data-stu-id="77840-112">Set its <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="77840-113">這還將<xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A>屬性設置到`true`。</span><span class="sxs-lookup"><span data-stu-id="77840-113">This also sets the <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> property to `true`.</span></span> <span data-ttu-id="77840-114">僅當希望功能表命令預設顯示為選中時，才使用此過程，而不管是否選擇了該命令。</span><span class="sxs-lookup"><span data-stu-id="77840-114">Use this procedure only if you want the menu command to appear as checked by default, regardless of whether it is selected.</span></span>  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a><span data-ttu-id="77840-115">顯示每次按一下更改狀態的核取記號</span><span class="sxs-lookup"><span data-stu-id="77840-115">To display a check mark that changes state with each click</span></span>  
  
- <span data-ttu-id="77840-116">將功能表命令的屬性<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>設置為`true`。</span><span class="sxs-lookup"><span data-stu-id="77840-116">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true`.</span></span>  
  
### <a name="to-add-an-image-to-a-menu-command"></a><span data-ttu-id="77840-117">將圖像添加到功能表命令</span><span class="sxs-lookup"><span data-stu-id="77840-117">To add an image to a menu command</span></span>  
  
- <span data-ttu-id="77840-118">將功能表命令的屬性<xref:System.Windows.Forms.ToolStripItem.Image%2A>設置為圖像的名稱。</span><span class="sxs-lookup"><span data-stu-id="77840-118">Set the menu command's <xref:System.Windows.Forms.ToolStripItem.Image%2A> property to the name of the image.</span></span> <span data-ttu-id="77840-119">如果此<xref:System.Windows.Forms.ToolStripItemDisplayStyle>功能表命令的屬性設置為<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>或<xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>，則無法顯示圖像。</span><span class="sxs-lookup"><span data-stu-id="77840-119">If the <xref:System.Windows.Forms.ToolStripItemDisplayStyle> property of this menu command is set to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, the image cannot be displayed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77840-120">如果願意，圖像邊距也可以顯示核取記號。</span><span class="sxs-lookup"><span data-stu-id="77840-120">The image margin can also show a check mark if you so choose.</span></span> <span data-ttu-id="77840-121">此外，您可以將圖像<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>的屬性設置為`true`，並且圖像將在運行時以填充邊框出現在圖像周圍。</span><span class="sxs-lookup"><span data-stu-id="77840-121">Also, you can set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property of the image to `true`, and the image will appear with a hatched border around it at run time.</span></span>  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a><span data-ttu-id="77840-122">顯示功能表命令的快速鍵</span><span class="sxs-lookup"><span data-stu-id="77840-122">To display a shortcut key for a menu command</span></span>  
  
- <span data-ttu-id="77840-123">將<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>功能表命令的屬性設置為所需的鍵盤組合，如 **"打開**"功能表命令的 CTRL_O，並將<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>該屬性設置為`true`。</span><span class="sxs-lookup"><span data-stu-id="77840-123">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> property to the desired keyboard combination, such as CTRL+O for the **Open** menu command, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a><span data-ttu-id="77840-124">顯示功能表命令的自訂快速鍵</span><span class="sxs-lookup"><span data-stu-id="77840-124">To display custom shortcut keys for a menu command</span></span>  
  
- <span data-ttu-id="77840-125">將功能表命令的屬性<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A>設置為所需的鍵盤組合，如 CTRL_SHIFT_O 而不是 SHIFT_CTRL_O，並將<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>該屬性設置為`true`。</span><span class="sxs-lookup"><span data-stu-id="77840-125">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> property to the desired keyboard combination, such as CTRL+SHIFT+O rather than SHIFT+CTRL+O, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a><span data-ttu-id="77840-126">顯示功能表命令的便捷鍵</span><span class="sxs-lookup"><span data-stu-id="77840-126">To display an access key for a menu command</span></span>  
  
- <span data-ttu-id="77840-127">設置功能表命令的屬性<xref:System.Windows.Forms.ToolStripItem.Text%2A>時，在要作為便捷鍵底線的字母之前輸入一個 ampersand （&）。</span><span class="sxs-lookup"><span data-stu-id="77840-127">When you set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property for the menu command, enter an ampersand (&) before the letter you want to be underlined as the access key.</span></span> <span data-ttu-id="77840-128">例如，鍵入`&Open`作為功能表項目<xref:System.Windows.Forms.ToolStripItem.Text%2A>的屬性將導致功能表命令顯示為<u>O</u>筆。</span><span class="sxs-lookup"><span data-stu-id="77840-128">For example, typing `&Open` as the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of a menu item will result in a menu command that appears as <u>O</u>pen.</span></span>
  
     <span data-ttu-id="77840-129">要導航到此功能表命令，請按 ALT 將焦點<xref:System.Windows.Forms.MenuStrip>放在 上，然後按功能表名稱的便捷鍵。</span><span class="sxs-lookup"><span data-stu-id="77840-129">To navigate to this menu command, press ALT to give focus to the <xref:System.Windows.Forms.MenuStrip>, and press the access key of the menu name.</span></span> <span data-ttu-id="77840-130">當功能表打開並顯示帶有便捷鍵的專案時，您只需按便捷鍵即選擇功能表命令。</span><span class="sxs-lookup"><span data-stu-id="77840-130">When the menu opens and shows items with access keys, you only need to press the access key to select the menu command.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77840-131">避免定義重複的便捷鍵，例如在同一功能表系統中兩次定義 ALT+F。</span><span class="sxs-lookup"><span data-stu-id="77840-131">Avoid defining duplicate access keys, such as defining ALT+F twice in the same menu system.</span></span> <span data-ttu-id="77840-132">無法保證重複訪問金鑰的選擇順序。</span><span class="sxs-lookup"><span data-stu-id="77840-132">The selection order of duplicate access keys cannot be guaranteed.</span></span>  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a><span data-ttu-id="77840-133">在功能表命令之間顯示分隔符號</span><span class="sxs-lookup"><span data-stu-id="77840-133">To display a separator bar between menu commands</span></span>  
  
- <span data-ttu-id="77840-134"><xref:System.Windows.Forms.MenuStrip>定義及其將包含的專案後，使用<xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A>或<xref:System.Windows.Forms.ToolStripItemCollection.Add%2A>方法按所需順序將功能表命令和<xref:System.Windows.Forms.ToolStripSeparator>控制項添加到 。 <xref:System.Windows.Forms.MenuStrip></span><span class="sxs-lookup"><span data-stu-id="77840-134">After you define your <xref:System.Windows.Forms.MenuStrip> and the items it will contain, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> or <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add the menu commands and <xref:System.Windows.Forms.ToolStripSeparator> controls to the <xref:System.Windows.Forms.MenuStrip> in the order you want.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="77840-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77840-135">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="77840-136">MenuStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="77840-136">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
