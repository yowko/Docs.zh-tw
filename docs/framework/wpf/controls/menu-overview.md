---
title: 功能表概觀
ms.date: 03/30/2017
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
ms.openlocfilehash: 3d5cfba0734e684349f7d73b7242f4b69089b94d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124646"
---
# <a name="menu-overview"></a><span data-ttu-id="ea481-102">功能表概觀</span><span class="sxs-lookup"><span data-stu-id="ea481-102">Menu Overview</span></span>
<span data-ttu-id="ea481-103"><xref:System.Windows.Controls.Menu> 類別可讓您以階層順序組織與命令和事件處理常式相關聯的元素。</span><span class="sxs-lookup"><span data-stu-id="ea481-103">The <xref:System.Windows.Controls.Menu> class enables you to organize elements associated with commands and event handlers in a hierarchical order.</span></span> <span data-ttu-id="ea481-104">每個 <xref:System.Windows.Controls.Menu> 元素都包含 <xref:System.Windows.Controls.MenuItem> 元素的集合。</span><span class="sxs-lookup"><span data-stu-id="ea481-104">Each <xref:System.Windows.Controls.Menu> element contains a collection of <xref:System.Windows.Controls.MenuItem> elements.</span></span>  

<a name="menu_control"></a>   
## <a name="menu-control"></a><span data-ttu-id="ea481-105">功能表控制項</span><span class="sxs-lookup"><span data-stu-id="ea481-105">Menu Control</span></span>  
 <span data-ttu-id="ea481-106">[<xref:System.Windows.Controls.Menu>] 控制項會顯示指定應用程式之命令或選項的專案清單。</span><span class="sxs-lookup"><span data-stu-id="ea481-106">The <xref:System.Windows.Controls.Menu> control presents a list of items that specify commands or options for an application.</span></span> <span data-ttu-id="ea481-107">一般來說，按一下 <xref:System.Windows.Controls.MenuItem> 會開啟子功能表，或讓應用程式執行命令。</span><span class="sxs-lookup"><span data-stu-id="ea481-107">Typically, clicking a <xref:System.Windows.Controls.MenuItem> opens a submenu or causes an application to carry out a command.</span></span>  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a><span data-ttu-id="ea481-108">建立功能表</span><span class="sxs-lookup"><span data-stu-id="ea481-108">Creating Menus</span></span>  
 <span data-ttu-id="ea481-109">下列範例會建立 <xref:System.Windows.Controls.Menu> 來操作 <xref:System.Windows.Controls.TextBox>中的文字。</span><span class="sxs-lookup"><span data-stu-id="ea481-109">The following example creates a <xref:System.Windows.Controls.Menu> to manipulate text in a <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="ea481-110"><xref:System.Windows.Controls.Menu> 包含使用 <xref:System.Windows.Controls.MenuItem.Command%2A>、<xref:System.Windows.Controls.MenuItem.IsCheckable%2A>和 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> 屬性以及 <xref:System.Windows.Controls.MenuItem.Checked>、<xref:System.Windows.Controls.MenuItem.Unchecked>和 <xref:System.Windows.Controls.MenuItem.Click> 事件的 <xref:System.Windows.Controls.MenuItem> 物件。</span><span class="sxs-lookup"><span data-stu-id="ea481-110">The <xref:System.Windows.Controls.Menu> contains <xref:System.Windows.Controls.MenuItem> objects that use the <xref:System.Windows.Controls.MenuItem.Command%2A>, <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>, and <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> properties and the <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>, and <xref:System.Windows.Controls.MenuItem.Click> events.</span></span>  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a><span data-ttu-id="ea481-111">具有鍵盤快速鍵的 MenuItem</span><span class="sxs-lookup"><span data-stu-id="ea481-111">MenuItems with Keyboard Shortcuts</span></span>  
 <span data-ttu-id="ea481-112">鍵盤快速鍵是可以使用鍵盤輸入的字元組合，以叫用 <xref:System.Windows.Controls.Menu> 命令。</span><span class="sxs-lookup"><span data-stu-id="ea481-112">Keyboard shortcuts are character combinations that can be entered with the keyboard to invoke <xref:System.Windows.Controls.Menu> commands.</span></span> <span data-ttu-id="ea481-113">例如，「複製」的快速鍵是 CTRL+C。</span><span class="sxs-lookup"><span data-stu-id="ea481-113">For example, the shortcut for **Copy** is CTRL+C.</span></span> <span data-ttu-id="ea481-114">有兩個屬性可用於鍵盤快速鍵和功能表項目，<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> 或 <xref:System.Windows.Controls.MenuItem.Command%2A>。</span><span class="sxs-lookup"><span data-stu-id="ea481-114">There are two properties to use with keyboard shortcuts and menu items —<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> or <xref:System.Windows.Controls.MenuItem.Command%2A>.</span></span>  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a><span data-ttu-id="ea481-115">InputGestureText</span><span class="sxs-lookup"><span data-stu-id="ea481-115">InputGestureText</span></span>  
 <span data-ttu-id="ea481-116">下列範例顯示如何使用 <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> 屬性，將鍵盤快速鍵文字指派給 <xref:System.Windows.Controls.MenuItem> 控制項。</span><span class="sxs-lookup"><span data-stu-id="ea481-116">The following example shows how to use the <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> property to assign keyboard shortcut text to <xref:System.Windows.Controls.MenuItem> controls.</span></span> <span data-ttu-id="ea481-117">這只會將鍵盤快速鍵放在功能表項目中。</span><span class="sxs-lookup"><span data-stu-id="ea481-117">This only places the keyboard shortcut in the menu item.</span></span>  <span data-ttu-id="ea481-118">它不會將命令與 <xref:System.Windows.Controls.MenuItem>產生關聯。</span><span class="sxs-lookup"><span data-stu-id="ea481-118">It does not associate the command with the <xref:System.Windows.Controls.MenuItem>.</span></span> <span data-ttu-id="ea481-119">應用程式必須處理使用者的輸入，才能執行動作。</span><span class="sxs-lookup"><span data-stu-id="ea481-119">The application must handle the user's input to carry out the action.</span></span>  
  
 [!code-xaml[MenuEvent#6](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a><span data-ttu-id="ea481-120">命令</span><span class="sxs-lookup"><span data-stu-id="ea481-120">Command</span></span>  
 <span data-ttu-id="ea481-121">下列範例示範如何使用 [<xref:System.Windows.Controls.MenuItem.Command%2A>] 屬性，將 [**開啟**] 和 [**儲存**] 命令與 <xref:System.Windows.Controls.MenuItem> 控制項產生關聯。</span><span class="sxs-lookup"><span data-stu-id="ea481-121">The following example shows how to use the <xref:System.Windows.Controls.MenuItem.Command%2A> property to associate the **Open** and **Save** commands with <xref:System.Windows.Controls.MenuItem> controls.</span></span> <span data-ttu-id="ea481-122">命令屬性不僅會將命令與 <xref:System.Windows.Controls.MenuItem>產生關聯，還會提供輸入手勢文字做為快捷方式使用。</span><span class="sxs-lookup"><span data-stu-id="ea481-122">Not only does the command property associate a command with a <xref:System.Windows.Controls.MenuItem>, but it also supplies the input gesture text to use as a shortcut.</span></span>  
  
 [!code-xaml[MenuEvent#8](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 <span data-ttu-id="ea481-123"><xref:System.Windows.Controls.MenuItem> 類別也具有 <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> 屬性，它會指定命令發生所在的元素。</span><span class="sxs-lookup"><span data-stu-id="ea481-123">The <xref:System.Windows.Controls.MenuItem> class also has a <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> property, which specifies the element where the command occurs.</span></span> <span data-ttu-id="ea481-124">如果未設定 <xref:System.Windows.Controls.MenuItem.CommandTarget%2A>，則具有鍵盤焦點的元素會接收命令。</span><span class="sxs-lookup"><span data-stu-id="ea481-124">If <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> is not set, the element that has keyboard focus receives the command.</span></span> <span data-ttu-id="ea481-125">如需有關命令的詳細資訊，請參閱[命令概觀](../advanced/commanding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="ea481-125">For more information about commands, see [Commanding Overview](../advanced/commanding-overview.md).</span></span>  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a><span data-ttu-id="ea481-126">功能表樣式設定</span><span class="sxs-lookup"><span data-stu-id="ea481-126">Menu Styling</span></span>  
 <span data-ttu-id="ea481-127">使用控制項樣式，您可以大幅變更 <xref:System.Windows.Controls.Menu> 控制項的外觀和行為，而不需要撰寫自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="ea481-127">With control styling, you can dramatically change the appearance and behavior of <xref:System.Windows.Controls.Menu> controls without having to write a custom control.</span></span> <span data-ttu-id="ea481-128">除了設定視覺屬性之外，您也可以將 <xref:System.Windows.Style> 套用至控制項的個別部分、透過屬性變更控制項部分的行為，或加入其他元件或變更控制項的版面配置。</span><span class="sxs-lookup"><span data-stu-id="ea481-128">In addition to setting visual properties, you can also apply a <xref:System.Windows.Style> to individual parts of a control, change the behavior of parts of the control through properties, or add additional parts or change the layout of a control.</span></span> <span data-ttu-id="ea481-129">下列範例示範數種將 <xref:System.Windows.Style> 新增至 <xref:System.Windows.Controls.Menu> 控制項的方式。</span><span class="sxs-lookup"><span data-stu-id="ea481-129">The following examples demonstrate several ways to add a <xref:System.Windows.Style> to a <xref:System.Windows.Controls.Menu> control.</span></span>  
  
 <span data-ttu-id="ea481-130">第一個程式碼範例會定義稱為 `Simple` 的 <xref:System.Windows.Style>，以示範如何在樣式中使用目前的系統設定。</span><span class="sxs-lookup"><span data-stu-id="ea481-130">The first code example defines a <xref:System.Windows.Style> called `Simple` that shows how to use the current system settings in your style.</span></span> <span data-ttu-id="ea481-131">此程式碼指派 `MenuHighlightBrush` 的色彩作為功能表的背景色彩，以及 `MenuTextBrush` 作為功能表的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="ea481-131">The code assigns the color of the `MenuHighlightBrush` as the menu's background color and the `MenuTextBrush` as the menu's foreground color.</span></span> <span data-ttu-id="ea481-132">請注意，您需使用資源索引鍵來指派筆刷。</span><span class="sxs-lookup"><span data-stu-id="ea481-132">Notice that you use resource keys to assign the brushes.</span></span>  
  
 [!code-xaml[MenuStylesSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 <span data-ttu-id="ea481-133">下列範例會使用 <xref:System.Windows.Trigger> 元素，讓您變更 <xref:System.Windows.Controls.MenuItem> 的外觀，以回應發生在 <xref:System.Windows.Controls.Menu>上的事件。</span><span class="sxs-lookup"><span data-stu-id="ea481-133">The following sample uses <xref:System.Windows.Trigger> elements that enable you to change the appearance of a <xref:System.Windows.Controls.MenuItem> in response to events that occur on the <xref:System.Windows.Controls.Menu>.</span></span> <span data-ttu-id="ea481-134">當您將滑鼠游標移到 [<xref:System.Windows.Controls.Menu>] 上方時，功能表項目的前景色彩和字型特性也會變更。</span><span class="sxs-lookup"><span data-stu-id="ea481-134">When you move the mouse over the <xref:System.Windows.Controls.Menu>, the foreground color and the font characteristics of the menu items change.</span></span>  
  
 [!code-xaml[MenuStylesSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ea481-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea481-135">See also</span></span>

- [<span data-ttu-id="ea481-136">WPF 控制項陳列庫範例</span><span class="sxs-lookup"><span data-stu-id="ea481-136">WPF Controls Gallery Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
