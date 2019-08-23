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
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a><span data-ttu-id="aa912-102">HOW TO：將增強功能新增至 ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="aa912-102">How to: Add Enhancements to ToolStripMenuItems</span></span>
<span data-ttu-id="aa912-103">您可以利用下列方式增強<xref:System.Windows.Forms.MenuStrip>和<xref:System.Windows.Forms.ContextMenuStrip>控制項的可用性:</span><span class="sxs-lookup"><span data-stu-id="aa912-103">You can enhance the usability of <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> controls in the following ways:</span></span>  
  
- <span data-ttu-id="aa912-104">加入核取記號以指定是否開啟或關閉功能, 例如尺規是否會沿著文字處理應用程式的邊界顯示, 或表示要顯示的檔案清單中的哪個檔案, 例如在 [**視窗]** 功能表上。</span><span class="sxs-lookup"><span data-stu-id="aa912-104">Add check marks to designate whether a feature is turned on or off, such as whether a ruler is displayed along the margin of a word-processing application, or to indicate which file in a list of files is being displayed, such as on a **Window** menu.</span></span>  
  
- <span data-ttu-id="aa912-105">新增以視覺方式表示功能表命令的影像。</span><span class="sxs-lookup"><span data-stu-id="aa912-105">Add images that visually represent menu commands.</span></span>  
  
- <span data-ttu-id="aa912-106">顯示快速鍵, 以提供鍵盤替代滑鼠來執行命令。</span><span class="sxs-lookup"><span data-stu-id="aa912-106">Display shortcut keys to provide a keyboard alternative to the mouse for performing commands.</span></span> <span data-ttu-id="aa912-107">例如, 按下 CTRL + C 會執行 [**複製**] 命令。</span><span class="sxs-lookup"><span data-stu-id="aa912-107">For example, pressing CTRL+C performs the **Copy** command.</span></span>  
  
- <span data-ttu-id="aa912-108">顯示存取金鑰以提供鍵盤替代滑鼠來流覽功能表。</span><span class="sxs-lookup"><span data-stu-id="aa912-108">Display access keys to provide a keyboard alternative to the mouse for menu navigation.</span></span> <span data-ttu-id="aa912-109">例如, 按 ALT + F 會選擇 [檔案] 功能表。</span><span class="sxs-lookup"><span data-stu-id="aa912-109">For example, pressing ALT+F chooses the **File** menu.</span></span>  
  
- <span data-ttu-id="aa912-110">顯示分隔線以將相關的命令分組, 並讓功能表更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="aa912-110">Show separator bars to group related commands and make menus more readable.</span></span>  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a><span data-ttu-id="aa912-111">若要在功能表命令上顯示核取記號</span><span class="sxs-lookup"><span data-stu-id="aa912-111">To display a check mark on a menu command</span></span>  
  
- <span data-ttu-id="aa912-112">將其<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>屬性設`true`為。</span><span class="sxs-lookup"><span data-stu-id="aa912-112">Set its <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property to `true`.</span></span>  
  
     <span data-ttu-id="aa912-113">這也會將<xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A>屬性設定`true`為。</span><span class="sxs-lookup"><span data-stu-id="aa912-113">This also sets the <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> property to `true`.</span></span> <span data-ttu-id="aa912-114">只有在您想要讓功能表命令預設顯示為 [已核取] 時 (不論是否已選取), 才使用此程式。</span><span class="sxs-lookup"><span data-stu-id="aa912-114">Use this procedure only if you want the menu command to appear as checked by default, regardless of whether it is selected.</span></span>  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a><span data-ttu-id="aa912-115">顯示每次點擊時都變更狀態的核取記號</span><span class="sxs-lookup"><span data-stu-id="aa912-115">To display a check mark that changes state with each click</span></span>  
  
- <span data-ttu-id="aa912-116">將功能表命令的<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>屬性設定為。 `true`</span><span class="sxs-lookup"><span data-stu-id="aa912-116">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true`.</span></span>  
  
### <a name="to-add-an-image-to-a-menu-command"></a><span data-ttu-id="aa912-117">將影像新增至功能表命令</span><span class="sxs-lookup"><span data-stu-id="aa912-117">To add an image to a menu command</span></span>  
  
- <span data-ttu-id="aa912-118">將功能表命令的<xref:System.Windows.Forms.ToolStripItem.Image%2A>屬性設定為映射的名稱。</span><span class="sxs-lookup"><span data-stu-id="aa912-118">Set the menu command's <xref:System.Windows.Forms.ToolStripItem.Image%2A> property to the name of the image.</span></span> <span data-ttu-id="aa912-119">如果此<xref:System.Windows.Forms.ToolStripItemDisplayStyle>功能表命令的屬性設定為<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>或<xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, 則無法顯示影像。</span><span class="sxs-lookup"><span data-stu-id="aa912-119">If the <xref:System.Windows.Forms.ToolStripItemDisplayStyle> property of this menu command is set to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>, the image cannot be displayed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa912-120">如果您選擇, 影像邊界也可以顯示核取記號。</span><span class="sxs-lookup"><span data-stu-id="aa912-120">The image margin can also show a check mark if you so choose.</span></span> <span data-ttu-id="aa912-121">此外, 您可以將影像<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>的屬性設定為`true`, 而且影像會在執行時間以陰影框線括住。</span><span class="sxs-lookup"><span data-stu-id="aa912-121">Also, you can set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property of the image to `true`, and the image will appear with a hatched border around it at run time.</span></span>  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a><span data-ttu-id="aa912-122">若要顯示功能表命令的快速鍵</span><span class="sxs-lookup"><span data-stu-id="aa912-122">To display a shortcut key for a menu command</span></span>  
  
- <span data-ttu-id="aa912-123">將功能表命令<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>的屬性設為所需的鍵盤組合 (例如, CTRL + O 用於 [**開啟**] 功能表命令<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> ), 並將屬性設定為。 `true`</span><span class="sxs-lookup"><span data-stu-id="aa912-123">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> property to the desired keyboard combination, such as CTRL+O for the **Open** menu command, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a><span data-ttu-id="aa912-124">若要顯示功能表命令的自訂快速鍵</span><span class="sxs-lookup"><span data-stu-id="aa912-124">To display custom shortcut keys for a menu command</span></span>  
  
- <span data-ttu-id="aa912-125">將功能表命令的<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A>屬性設為所需的鍵盤組合, 例如 CTRL + SHIFT + o, 而不是 SHIFT + CTRL + o, 然後<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>將屬性設定為。 `true`</span><span class="sxs-lookup"><span data-stu-id="aa912-125">Set the menu command's <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> property to the desired keyboard combination, such as CTRL+SHIFT+O rather than SHIFT+CTRL+O, and set the <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> property to `true`.</span></span>  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a><span data-ttu-id="aa912-126">若要顯示功能表命令的存取金鑰</span><span class="sxs-lookup"><span data-stu-id="aa912-126">To display an access key for a menu command</span></span>  
  
- <span data-ttu-id="aa912-127">當您設定<xref:System.Windows.Forms.ToolStripItem.Text%2A>功能表命令的屬性時, 請在您想要加上底線做為存取金鑰的字母前面輸入連字號 (&)。</span><span class="sxs-lookup"><span data-stu-id="aa912-127">When you set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property for the menu command, enter an ampersand (&) before the letter you want to be underlined as the access key.</span></span> <span data-ttu-id="aa912-128">例如, 輸入`&Open`做為功能表<xref:System.Windows.Forms.ToolStripItem.Text%2A>項的屬性, 將會產生顯示為 [ <u>O</u>畫筆] 的功能表命令。</span><span class="sxs-lookup"><span data-stu-id="aa912-128">For example, typing `&Open` as the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of a menu item will result in a menu command that appears as <u>O</u>pen.</span></span>
  
     <span data-ttu-id="aa912-129">若要流覽至此功能表命令, 請按下 ALT 將焦點放<xref:System.Windows.Forms.MenuStrip>在, 然後按下功能表名稱的存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="aa912-129">To navigate to this menu command, press ALT to give focus to the <xref:System.Windows.Forms.MenuStrip>, and press the access key of the menu name.</span></span> <span data-ttu-id="aa912-130">當功能表開啟並顯示具有存取金鑰的專案時, 您只需要按下存取金鑰, 即可選取功能表命令。</span><span class="sxs-lookup"><span data-stu-id="aa912-130">When the menu opens and shows items with access keys, you only need to press the access key to select the menu command.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa912-131">避免在相同的功能表系統中定義重複的存取金鑰, 例如定義 ALT + F 兩次。</span><span class="sxs-lookup"><span data-stu-id="aa912-131">Avoid defining duplicate access keys, such as defining ALT+F twice in the same menu system.</span></span> <span data-ttu-id="aa912-132">無法保證重複存取金鑰的選取順序。</span><span class="sxs-lookup"><span data-stu-id="aa912-132">The selection order of duplicate access keys cannot be guaranteed.</span></span>  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a><span data-ttu-id="aa912-133">若要在功能表命令之間顯示分隔線</span><span class="sxs-lookup"><span data-stu-id="aa912-133">To display a separator bar between menu commands</span></span>  
  
- <span data-ttu-id="aa912-134">定義<xref:System.Windows.Forms.MenuStrip>和它將包含的專案之後, 請<xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A>使用或<xref:System.Windows.Forms.ToolStripItemCollection.Add%2A>方法, 依您想要的順序, <xref:System.Windows.Forms.ToolStripSeparator> <xref:System.Windows.Forms.MenuStrip>將功能表命令和控制項加入至。</span><span class="sxs-lookup"><span data-stu-id="aa912-134">After you define your <xref:System.Windows.Forms.MenuStrip> and the items it will contain, use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> or <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add the menu commands and <xref:System.Windows.Forms.ToolStripSeparator> controls to the <xref:System.Windows.Forms.MenuStrip> in the order you want.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aa912-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa912-135">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="aa912-136">MenuStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="aa912-136">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
