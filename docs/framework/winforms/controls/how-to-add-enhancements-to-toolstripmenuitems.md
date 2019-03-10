---
title: HOW TO：新增 toolstripmenuitems 的功能的增強功能
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
ms.openlocfilehash: 68a926eba184d12d58e537d8db0a5baefb0fbe95
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57719321"
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a><span data-ttu-id="f3b18-102">HOW TO：新增 toolstripmenuitems 的功能的增強功能</span><span class="sxs-lookup"><span data-stu-id="f3b18-102">How to: Add Enhancements to ToolStripMenuItems</span></span>
<span data-ttu-id="f3b18-103">您可以增強的可用性<xref:System.Windows.Forms.MenuStrip>和<xref:System.Windows.Forms.ContextMenuStrip>控制項如下：</span><span class="sxs-lookup"><span data-stu-id="f3b18-103">You can enhance the usability of <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> controls in the following ways:</span></span>  
  
-   <span data-ttu-id="f3b18-104">新增指定一項功能開啟或關閉，例如沿著文書處理應用程式，邊界是否顯示尺規，或指出的檔案清單中的檔案正在顯示，例如上的核取記號**視窗**功能表。</span><span class="sxs-lookup"><span data-stu-id="f3b18-104">Add check marks to designate whether a feature is turned on or off, such as whether a ruler is displayed along the margin of a word-processing application, or to indicate which file in a list of files is being displayed, such as on a **Window** menu.</span></span>  
  
-   <span data-ttu-id="f3b18-105">新增以視覺方式表示功能表命令的映像。</span><span class="sxs-lookup"><span data-stu-id="f3b18-105">Add images that visually represent menu commands.</span></span>  
  
-   <span data-ttu-id="f3b18-106">顯示要執行命令提供替代滑鼠的鍵盤快速鍵。</span><span class="sxs-lookup"><span data-stu-id="f3b18-106">Display shortcut keys to provide a keyboard alternative to the mouse for performing commands.</span></span> <span data-ttu-id="f3b18-107">例如，按下 CTRL + C 會執行**複製**命令。</span><span class="sxs-lookup"><span data-stu-id="f3b18-107">For example, pressing CTRL+C performs the **Copy** command.</span></span>  
  
-   <span data-ttu-id="f3b18-108">顯示存取金鑰 功能表導覽提供替代滑鼠的鍵盤。</span><span class="sxs-lookup"><span data-stu-id="f3b18-108">Display access keys to provide a keyboard alternative to the mouse for menu navigation.</span></span> <span data-ttu-id="f3b18-109">例如，按下 ALT + F 會選擇**檔案**功能表。</span><span class="sxs-lookup"><span data-stu-id="f3b18-109">For example, pressing ALT+F chooses the **File** menu.</span></span>  
  
-   <span data-ttu-id="f3b18-110">顯示分組相關的命令，並讓功能表更容易閱讀的分隔線。</span><span class="sxs-lookup"><span data-stu-id="f3b18-110">Show separator bars to group related commands and make menus more readable.</span></span>  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a><span data-ttu-id="f3b18-111">若要顯示功能表命令上的核取記號</span><span class="sxs-lookup"><span data-stu-id="f3b18-111">To display a check mark on a menu command</span></span>  
  
-   <span data-ttu-id="f3b18-112">設定其<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="f3b18-112">Set its <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="f3b18-113">這也會設定<xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="f3b18-113">This also sets the <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> property to `true`.</span></span> <span data-ttu-id="f3b18-114">只有當您想要顯示為已核取，根據預設，不論是否選取的功能表命令，請使用此程序。</span><span class="sxs-lookup"><span data-stu-id="f3b18-114">Use this procedure only if you want the menu command to appear as checked by default, regardless of whether it is selected.</span></span>  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a><span data-ttu-id="f3b18-115">若要顯示 變更狀態時，使用每按一下核取記號</span><span class="sxs-lookup"><span data-stu-id="f3b18-115">To display a check mark that changes state with each click</span></span>  
  
-   <span data-ttu-id="f3b18-116">將功能表命令的<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="f3b18-116">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true`.</span></span>  
  
### <a name="to-add-an-image-to-a-menu-command"></a><span data-ttu-id="f3b18-117">若要將影像加入功能表命令</span><span class="sxs-lookup"><span data-stu-id="f3b18-117">To add an image to a menu command</span></span>  
  
-   <span data-ttu-id="f3b18-118">將功能表命令的<xref:System.Windows.Forms.ToolStripItem.Image%2A>映像名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="f3b18-118">Set the menu command's <xref:System.Windows.Forms.ToolStripItem.Image%2A> property to the name of the image.</span></span> <span data-ttu-id="f3b18-119">如果<xref:System.Windows.Forms.ToolStripItemDisplayStyle>這個功能表命令的屬性設定為<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>或<xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>，無法顯示影像。</span><span class="sxs-lookup"><span data-stu-id="f3b18-119">If the <xref:System.Windows.Forms.ToolStripItemDisplayStyle> property of this menu command is set to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, the image cannot be displayed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3b18-120">影像邊界也可以顯示勾號，是否您選擇如此。</span><span class="sxs-lookup"><span data-stu-id="f3b18-120">The image margin can also show a check mark if you so choose.</span></span> <span data-ttu-id="f3b18-121">此外，您可以設定<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>映像，以屬性`true`，並具有其周圍的陰影框線呈現的影像，就將它在執行階段。</span><span class="sxs-lookup"><span data-stu-id="f3b18-121">Also, you can set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property of the image to `true`, and the image will appear with a hatched border around it at run time.</span></span>  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a><span data-ttu-id="f3b18-122">若要顯示的功能表命令的快速鍵</span><span class="sxs-lookup"><span data-stu-id="f3b18-122">To display a shortcut key for a menu command</span></span>  
  
-   <span data-ttu-id="f3b18-123">將功能表命令的<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>屬性所需要的鍵盤組合，例如 CTRL + O**開啟**功能表命令，以及組<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="f3b18-123">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> property to the desired keyboard combination, such as CTRL+O for the **Open** menu command, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a><span data-ttu-id="f3b18-124">若要顯示的功能表命令的自訂快速鍵</span><span class="sxs-lookup"><span data-stu-id="f3b18-124">To display custom shortcut keys for a menu command</span></span>  
  
-   <span data-ttu-id="f3b18-125">將功能表命令的<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A>屬性所需要的鍵盤組合，例如 CTRL + SHIFT + O，而非 SHIFT + CTRL + O，以及組<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="f3b18-125">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> property to the desired keyboard combination, such as CTRL+SHIFT+O rather than SHIFT+CTRL+O, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a><span data-ttu-id="f3b18-126">若要顯示的功能表命令的存取金鑰</span><span class="sxs-lookup"><span data-stu-id="f3b18-126">To display an access key for a menu command</span></span>  
  
-   <span data-ttu-id="f3b18-127">當您將設定<xref:System.Windows.Forms.ToolStripItem.Text%2A>屬性功能表命令，請輸入連字號 (&) 您想要作為便捷鍵加上底線的字母前面。</span><span class="sxs-lookup"><span data-stu-id="f3b18-127">When you set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property for the menu command, enter an ampersand (&) before the letter you want to be underlined as the access key.</span></span> <span data-ttu-id="f3b18-128">例如，輸入`&Open`作為<xref:System.Windows.Forms.ToolStripItem.Text%2A>功能表項目的屬性會顯示為功能表命令<u>O</u>畫筆。</span><span class="sxs-lookup"><span data-stu-id="f3b18-128">For example, typing `&Open` as the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of a menu item will result in a menu command that appears as <u>O</u>pen.</span></span>
  
     <span data-ttu-id="f3b18-129">瀏覽至這個功能表命令、 按下 ALT 以焦點轉給<xref:System.Windows.Forms.MenuStrip>，然後按 的功能表名稱的存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="f3b18-129">To navigate to this menu command, press ALT to give focus to the <xref:System.Windows.Forms.MenuStrip>, and press the access key of the menu name.</span></span> <span data-ttu-id="f3b18-130">當功能表會隨即開啟，並顯示具有便捷鍵的項目時，您只需要按下便捷鍵以選取功能表命令。</span><span class="sxs-lookup"><span data-stu-id="f3b18-130">When the menu opens and shows items with access keys, you only need to press the access key to select the menu command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3b18-131">應避免定義重複的便捷鍵，例如定義相同的功能表系統中的兩倍的 ALT + F。</span><span class="sxs-lookup"><span data-stu-id="f3b18-131">Avoid defining duplicate access keys, such as defining ALT+F twice in the same menu system.</span></span> <span data-ttu-id="f3b18-132">重複的便捷鍵的選取項目順序，將無法保證。</span><span class="sxs-lookup"><span data-stu-id="f3b18-132">The selection order of duplicate access keys cannot be guaranteed.</span></span>  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a><span data-ttu-id="f3b18-133">若要顯示功能表命令之間的分隔線</span><span class="sxs-lookup"><span data-stu-id="f3b18-133">To display a separator bar between menu commands</span></span>  
  
-   <span data-ttu-id="f3b18-134">定義之後您<xref:System.Windows.Forms.MenuStrip>和項目會包含使用<xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A>或是<xref:System.Windows.Forms.ToolStripItemCollection.Add%2A>方法來加入功能表命令和<xref:System.Windows.Forms.ToolStripSeparator>控制項新增至<xref:System.Windows.Forms.MenuStrip>您想要的順序。</span><span class="sxs-lookup"><span data-stu-id="f3b18-134">After you define your <xref:System.Windows.Forms.MenuStrip> and the items it will contain, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> or <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add the menu commands and <xref:System.Windows.Forms.ToolStripSeparator> controls to the <xref:System.Windows.Forms.MenuStrip> in the order you want.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f3b18-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3b18-135">See also</span></span>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="f3b18-136">MenuStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="f3b18-136">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
