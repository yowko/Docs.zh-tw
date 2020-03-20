---
title: 功能表概觀
ms.date: 03/30/2017
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
ms.openlocfilehash: 53bc8f10e61b6e4e9e1f3b9a484340d9e2ec2a85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186966"
---
# <a name="menu-overview"></a><span data-ttu-id="4030e-102">功能表概觀</span><span class="sxs-lookup"><span data-stu-id="4030e-102">Menu Overview</span></span>
<span data-ttu-id="4030e-103">該<xref:System.Windows.Controls.Menu>類使您能夠按分層順序組織與命令和事件處理常式關聯的元素。</span><span class="sxs-lookup"><span data-stu-id="4030e-103">The <xref:System.Windows.Controls.Menu> class enables you to organize elements associated with commands and event handlers in a hierarchical order.</span></span> <span data-ttu-id="4030e-104">每個<xref:System.Windows.Controls.Menu>元素都包含元素的集合<xref:System.Windows.Controls.MenuItem>。</span><span class="sxs-lookup"><span data-stu-id="4030e-104">Each <xref:System.Windows.Controls.Menu> element contains a collection of <xref:System.Windows.Controls.MenuItem> elements.</span></span>  

<a name="menu_control"></a>
## <a name="menu-control"></a><span data-ttu-id="4030e-105">功能表控制項</span><span class="sxs-lookup"><span data-stu-id="4030e-105">Menu Control</span></span>  
 <span data-ttu-id="4030e-106">該<xref:System.Windows.Controls.Menu>控制項顯示指定應用程式的命令或選項的項清單。</span><span class="sxs-lookup"><span data-stu-id="4030e-106">The <xref:System.Windows.Controls.Menu> control presents a list of items that specify commands or options for an application.</span></span> <span data-ttu-id="4030e-107">通常，按一下<xref:System.Windows.Controls.MenuItem>將打開子功能表或導致應用程式執行命令。</span><span class="sxs-lookup"><span data-stu-id="4030e-107">Typically, clicking a <xref:System.Windows.Controls.MenuItem> opens a submenu or causes an application to carry out a command.</span></span>  
  
<a name="creating_menus"></a>
## <a name="creating-menus"></a><span data-ttu-id="4030e-108">建立功能表</span><span class="sxs-lookup"><span data-stu-id="4030e-108">Creating Menus</span></span>  
 <span data-ttu-id="4030e-109">下面的示例創建 一<xref:System.Windows.Controls.Menu>個 用於操作<xref:System.Windows.Controls.TextBox>中的文本。</span><span class="sxs-lookup"><span data-stu-id="4030e-109">The following example creates a <xref:System.Windows.Controls.Menu> to manipulate text in a <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="4030e-110"><xref:System.Windows.Controls.Menu>包含<xref:System.Windows.Controls.MenuItem>使用<xref:System.Windows.Controls.MenuItem.Command%2A>、<xref:System.Windows.Controls.MenuItem.IsCheckable%2A>和<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>屬性 以及<xref:System.Windows.Controls.MenuItem.Checked>和<xref:System.Windows.Controls.MenuItem.Unchecked>和<xref:System.Windows.Controls.MenuItem.Click>事件的物件。</span><span class="sxs-lookup"><span data-stu-id="4030e-110">The <xref:System.Windows.Controls.Menu> contains <xref:System.Windows.Controls.MenuItem> objects that use the <xref:System.Windows.Controls.MenuItem.Command%2A>, <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>, and <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> properties and the <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>, and <xref:System.Windows.Controls.MenuItem.Click> events.</span></span>  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>
## <a name="menuitems-with-keyboard-shortcuts"></a><span data-ttu-id="4030e-111">具有鍵盤快速鍵的 MenuItem</span><span class="sxs-lookup"><span data-stu-id="4030e-111">MenuItems with Keyboard Shortcuts</span></span>  
 <span data-ttu-id="4030e-112">鍵盤快速鍵是可以使用鍵盤輸入以調用<xref:System.Windows.Controls.Menu>命令的字元組合。</span><span class="sxs-lookup"><span data-stu-id="4030e-112">Keyboard shortcuts are character combinations that can be entered with the keyboard to invoke <xref:System.Windows.Controls.Menu> commands.</span></span> <span data-ttu-id="4030e-113">例如，「複製」\*\*\*\* 的快速鍵是 CTRL+C。</span><span class="sxs-lookup"><span data-stu-id="4030e-113">For example, the shortcut for **Copy** is CTRL+C.</span></span> <span data-ttu-id="4030e-114">有兩個屬性可用於鍵盤快速鍵和功能表項目 -<xref:System.Windows.Controls.MenuItem.InputGestureText%2A>或<xref:System.Windows.Controls.MenuItem.Command%2A>。</span><span class="sxs-lookup"><span data-stu-id="4030e-114">There are two properties to use with keyboard shortcuts and menu items —<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> or <xref:System.Windows.Controls.MenuItem.Command%2A>.</span></span>  
  
<a name="menus_inputgesturetext"></a>
### <a name="inputgesturetext"></a><span data-ttu-id="4030e-115">InputGestureText</span><span class="sxs-lookup"><span data-stu-id="4030e-115">InputGestureText</span></span>  
 <span data-ttu-id="4030e-116">下面的示例演示如何使用 屬性<xref:System.Windows.Controls.MenuItem.InputGestureText%2A>將鍵盤快捷文本分配給<xref:System.Windows.Controls.MenuItem>控制項。</span><span class="sxs-lookup"><span data-stu-id="4030e-116">The following example shows how to use the <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> property to assign keyboard shortcut text to <xref:System.Windows.Controls.MenuItem> controls.</span></span> <span data-ttu-id="4030e-117">這只會將鍵盤快速鍵放在功能表項目中。</span><span class="sxs-lookup"><span data-stu-id="4030e-117">This only places the keyboard shortcut in the menu item.</span></span>  <span data-ttu-id="4030e-118">它不將命令與 相關聯<xref:System.Windows.Controls.MenuItem>。</span><span class="sxs-lookup"><span data-stu-id="4030e-118">It does not associate the command with the <xref:System.Windows.Controls.MenuItem>.</span></span> <span data-ttu-id="4030e-119">應用程式必須處理使用者的輸入，才能執行動作。</span><span class="sxs-lookup"><span data-stu-id="4030e-119">The application must handle the user's input to carry out the action.</span></span>  
  
 [!code-xaml[MenuEvent#6](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>
### <a name="command"></a><span data-ttu-id="4030e-120">Command</span><span class="sxs-lookup"><span data-stu-id="4030e-120">Command</span></span>  
 <span data-ttu-id="4030e-121">下面的示例<xref:System.Windows.Controls.MenuItem.Command%2A>演示如何使用 屬性將 **"打開**"和"**保存"** 命令與<xref:System.Windows.Controls.MenuItem>控制項相關聯。</span><span class="sxs-lookup"><span data-stu-id="4030e-121">The following example shows how to use the <xref:System.Windows.Controls.MenuItem.Command%2A> property to associate the **Open** and **Save** commands with <xref:System.Windows.Controls.MenuItem> controls.</span></span> <span data-ttu-id="4030e-122">命令屬性不僅將命令與<xref:System.Windows.Controls.MenuItem>相關聯，而且還提供用作快捷方式的輸入手勢文本。</span><span class="sxs-lookup"><span data-stu-id="4030e-122">Not only does the command property associate a command with a <xref:System.Windows.Controls.MenuItem>, but it also supplies the input gesture text to use as a shortcut.</span></span>  
  
 [!code-xaml[MenuEvent#8](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 <span data-ttu-id="4030e-123">類<xref:System.Windows.Controls.MenuItem>還具有一個<xref:System.Windows.Controls.MenuItem.CommandTarget%2A>屬性，該屬性指定發生命令的元素。</span><span class="sxs-lookup"><span data-stu-id="4030e-123">The <xref:System.Windows.Controls.MenuItem> class also has a <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> property, which specifies the element where the command occurs.</span></span> <span data-ttu-id="4030e-124">如果未<xref:System.Windows.Controls.MenuItem.CommandTarget%2A>設置，具有鍵盤焦點的元素將接收該命令。</span><span class="sxs-lookup"><span data-stu-id="4030e-124">If <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> is not set, the element that has keyboard focus receives the command.</span></span> <span data-ttu-id="4030e-125">如需有關命令的詳細資訊，請參閱[命令概觀](../advanced/commanding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4030e-125">For more information about commands, see [Commanding Overview](../advanced/commanding-overview.md).</span></span>  
  
<a name="menu_styling"></a>
## <a name="menu-styling"></a><span data-ttu-id="4030e-126">功能表樣式設定</span><span class="sxs-lookup"><span data-stu-id="4030e-126">Menu Styling</span></span>  
 <span data-ttu-id="4030e-127">使用控制項樣式，您可以顯著更改<xref:System.Windows.Controls.Menu>控制項的外觀和行為，而無需編寫自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="4030e-127">With control styling, you can dramatically change the appearance and behavior of <xref:System.Windows.Controls.Menu> controls without having to write a custom control.</span></span> <span data-ttu-id="4030e-128">除了設置可視屬性外，還可以<xref:System.Windows.Style>將 應用於控制項的各個部分、通過屬性更改控制項各部分的行為、添加其他部分或更改控制項的佈局。</span><span class="sxs-lookup"><span data-stu-id="4030e-128">In addition to setting visual properties, you can also apply a <xref:System.Windows.Style> to individual parts of a control, change the behavior of parts of the control through properties, or add additional parts or change the layout of a control.</span></span> <span data-ttu-id="4030e-129">以下示例演示了向<xref:System.Windows.Style><xref:System.Windows.Controls.Menu>控制項添加 的幾種方法。</span><span class="sxs-lookup"><span data-stu-id="4030e-129">The following examples demonstrate several ways to add a <xref:System.Windows.Style> to a <xref:System.Windows.Controls.Menu> control.</span></span>  
  
 <span data-ttu-id="4030e-130">第一個代碼示例定義一<xref:System.Windows.Style>個`Simple`調用，該調用示例演示如何在樣式中使用當前系統設置。</span><span class="sxs-lookup"><span data-stu-id="4030e-130">The first code example defines a <xref:System.Windows.Style> called `Simple` that shows how to use the current system settings in your style.</span></span> <span data-ttu-id="4030e-131">此程式碼指派 `MenuHighlightBrush` 的色彩作為功能表的背景色彩，以及 `MenuTextBrush` 作為功能表的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="4030e-131">The code assigns the color of the `MenuHighlightBrush` as the menu's background color and the `MenuTextBrush` as the menu's foreground color.</span></span> <span data-ttu-id="4030e-132">請注意，您需使用資源索引鍵來指派筆刷。</span><span class="sxs-lookup"><span data-stu-id="4030e-132">Notice that you use resource keys to assign the brushes.</span></span>  
  
 [!code-xaml[MenuStylesSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 <span data-ttu-id="4030e-133">以下示例使用<xref:System.Windows.Trigger>元素，以便更改 的外觀<xref:System.Windows.Controls.MenuItem>以回應 在 上發生的事件。 <xref:System.Windows.Controls.Menu></span><span class="sxs-lookup"><span data-stu-id="4030e-133">The following sample uses <xref:System.Windows.Trigger> elements that enable you to change the appearance of a <xref:System.Windows.Controls.MenuItem> in response to events that occur on the <xref:System.Windows.Controls.Menu>.</span></span> <span data-ttu-id="4030e-134">將滑鼠移到 上<xref:System.Windows.Controls.Menu>時，功能表項目的前景顏色和字體特徵將發生變化。</span><span class="sxs-lookup"><span data-stu-id="4030e-134">When you move the mouse over the <xref:System.Windows.Controls.Menu>, the foreground color and the font characteristics of the menu items change.</span></span>  
  
 [!code-xaml[MenuStylesSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a><span data-ttu-id="4030e-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4030e-135">See also</span></span>

- [<span data-ttu-id="4030e-136">WPF 控制項陳列庫範例</span><span class="sxs-lookup"><span data-stu-id="4030e-136">WPF Controls Gallery Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
