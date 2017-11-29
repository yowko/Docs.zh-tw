---
title: "功能表概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 81611e7c5f509314b10e3188106870bdc67dfb0e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="menu-overview"></a><span data-ttu-id="81490-102">功能表概觀</span><span class="sxs-lookup"><span data-stu-id="81490-102">Menu Overview</span></span>
<span data-ttu-id="81490-103"><xref:System.Windows.Controls.Menu>類別可讓您組織命令和事件處理常式，以階層順序相關聯的項目。</span><span class="sxs-lookup"><span data-stu-id="81490-103">The <xref:System.Windows.Controls.Menu> class enables you to organize elements associated with commands and event handlers in a hierarchical order.</span></span> <span data-ttu-id="81490-104">每個<xref:System.Windows.Controls.Menu>項目包含集合<xref:System.Windows.Controls.MenuItem>項目。</span><span class="sxs-lookup"><span data-stu-id="81490-104">Each <xref:System.Windows.Controls.Menu> element contains a collection of <xref:System.Windows.Controls.MenuItem> elements.</span></span>  
  
  
<a name="menu_control"></a>   
## <a name="menu-control"></a><span data-ttu-id="81490-105">功能表控制項</span><span class="sxs-lookup"><span data-stu-id="81490-105">Menu Control</span></span>  
 <span data-ttu-id="81490-106"><xref:System.Windows.Controls.Menu>控制項呈現的項目，指定命令或應用程式的選項清單。</span><span class="sxs-lookup"><span data-stu-id="81490-106">The <xref:System.Windows.Controls.Menu> control presents a list of items that specify commands or options for an application.</span></span> <span data-ttu-id="81490-107">一般而言，按一下<xref:System.Windows.Controls.MenuItem>開啟子功能表，或是造成應用程式來執行命令。</span><span class="sxs-lookup"><span data-stu-id="81490-107">Typically, clicking a <xref:System.Windows.Controls.MenuItem> opens a submenu or causes an application to carry out a command.</span></span>  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a><span data-ttu-id="81490-108">建立功能表</span><span class="sxs-lookup"><span data-stu-id="81490-108">Creating Menus</span></span>  
 <span data-ttu-id="81490-109">下列範例會建立<xref:System.Windows.Controls.Menu>操作中的文字<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="81490-109">The following example creates a <xref:System.Windows.Controls.Menu> to manipulate text in a <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="81490-110"><xref:System.Windows.Controls.Menu>包含<xref:System.Windows.Controls.MenuItem>物件使用<xref:System.Windows.Controls.MenuItem.Command%2A>， <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>，和<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>屬性和<xref:System.Windows.Controls.MenuItem.Checked>， <xref:System.Windows.Controls.MenuItem.Unchecked>，和<xref:System.Windows.Controls.MenuItem.Click>事件。</span><span class="sxs-lookup"><span data-stu-id="81490-110">The <xref:System.Windows.Controls.Menu> contains <xref:System.Windows.Controls.MenuItem> objects that use the <xref:System.Windows.Controls.MenuItem.Command%2A>, <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>, and <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> properties and the <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>, and <xref:System.Windows.Controls.MenuItem.Click> events.</span></span>  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a><span data-ttu-id="81490-111">具有鍵盤快速鍵的 MenuItem</span><span class="sxs-lookup"><span data-stu-id="81490-111">MenuItems with Keyboard Shortcuts</span></span>  
 <span data-ttu-id="81490-112">鍵盤快速鍵是您可以用來叫用鍵盤輸入的字元組合<xref:System.Windows.Controls.Menu>命令。</span><span class="sxs-lookup"><span data-stu-id="81490-112">Keyboard shortcuts are character combinations that can be entered with the keyboard to invoke <xref:System.Windows.Controls.Menu> commands.</span></span> <span data-ttu-id="81490-113">例如，「複製」的快速鍵是 CTRL+C。</span><span class="sxs-lookup"><span data-stu-id="81490-113">For example, the shortcut for **Copy** is CTRL+C.</span></span> <span data-ttu-id="81490-114">有兩個屬性，若要使用鍵盤快速鍵與功能表項目-<xref:System.Windows.Controls.MenuItem.InputGestureText%2A>或<xref:System.Windows.Controls.MenuItem.Command%2A>。</span><span class="sxs-lookup"><span data-stu-id="81490-114">There are two properties to use with keyboard shortcuts and menu items —<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> or <xref:System.Windows.Controls.MenuItem.Command%2A>.</span></span>  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a><span data-ttu-id="81490-115">InputGestureText</span><span class="sxs-lookup"><span data-stu-id="81490-115">InputGestureText</span></span>  
 <span data-ttu-id="81490-116">下列範例示範如何使用<xref:System.Windows.Controls.MenuItem.InputGestureText%2A>要指派到的鍵盤快速鍵文字內容<xref:System.Windows.Controls.MenuItem>控制項。</span><span class="sxs-lookup"><span data-stu-id="81490-116">The following example shows how to use the <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> property to assign keyboard shortcut text to <xref:System.Windows.Controls.MenuItem> controls.</span></span> <span data-ttu-id="81490-117">這只會將鍵盤快速鍵放在功能表項目中。</span><span class="sxs-lookup"><span data-stu-id="81490-117">This only places the keyboard shortcut in the menu item.</span></span>  <span data-ttu-id="81490-118">不將關聯命令與<xref:System.Windows.Controls.MenuItem>。</span><span class="sxs-lookup"><span data-stu-id="81490-118">It does not associate the command with the <xref:System.Windows.Controls.MenuItem>.</span></span> <span data-ttu-id="81490-119">應用程式必須處理使用者的輸入，才能執行動作。</span><span class="sxs-lookup"><span data-stu-id="81490-119">The application must handle the user's input to carry out the action.</span></span>  
  
 [!code-xaml[MenuEvent#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a><span data-ttu-id="81490-120">命令</span><span class="sxs-lookup"><span data-stu-id="81490-120">Command</span></span>  
 <span data-ttu-id="81490-121">下列範例示範如何使用<xref:System.Windows.Controls.MenuItem.Command%2A>相關聯屬性**開啟**和**儲存**命令搭配<xref:System.Windows.Controls.MenuItem>控制項。</span><span class="sxs-lookup"><span data-stu-id="81490-121">The following example shows how to use the <xref:System.Windows.Controls.MenuItem.Command%2A> property to associate the **Open** and **Save** commands with <xref:System.Windows.Controls.MenuItem> controls.</span></span> <span data-ttu-id="81490-122">命令內容不只關聯的命令<xref:System.Windows.Controls.MenuItem>，但它也提供了使用較快速的輸入的動作文字。</span><span class="sxs-lookup"><span data-stu-id="81490-122">Not only does the command property associate a command with a <xref:System.Windows.Controls.MenuItem>, but it also supplies the input gesture text to use as a shortcut.</span></span>  
  
 [!code-xaml[MenuEvent#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 <span data-ttu-id="81490-123"><xref:System.Windows.Controls.MenuItem>類別也有<xref:System.Windows.Controls.MenuItem.CommandTarget%2A>屬性，指定命令的發生位置的項目。</span><span class="sxs-lookup"><span data-stu-id="81490-123">The <xref:System.Windows.Controls.MenuItem> class also has a <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> property, which specifies the element where the command occurs.</span></span> <span data-ttu-id="81490-124">如果<xref:System.Windows.Controls.MenuItem.CommandTarget%2A>未設定，具有鍵盤焦點的項目會在接收命令。</span><span class="sxs-lookup"><span data-stu-id="81490-124">If <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> is not set, the element that has keyboard focus receives the command.</span></span> <span data-ttu-id="81490-125">如需有關命令的詳細資訊，請參閱[命令概觀](../../../../docs/framework/wpf/advanced/commanding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="81490-125">For more information about commands, see [Commanding Overview](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span></span>  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a><span data-ttu-id="81490-126">功能表樣式設定</span><span class="sxs-lookup"><span data-stu-id="81490-126">Menu Styling</span></span>  
 <span data-ttu-id="81490-127">控制項的樣式，您可以利用大幅變更外觀和行為<xref:System.Windows.Controls.Menu>而不需要撰寫自訂控制項的控制項。</span><span class="sxs-lookup"><span data-stu-id="81490-127">With control styling, you can dramatically change the appearance and behavior of <xref:System.Windows.Controls.Menu> controls without having to write a custom control.</span></span> <span data-ttu-id="81490-128">除了設定視覺內容，您也可以套用<xref:System.Windows.Style>個別部分控制項的詳細資訊，變更行為的屬性，透過控制項的部分或將其他組件加入或變更控制項的配置。</span><span class="sxs-lookup"><span data-stu-id="81490-128">In addition to setting visual properties, you can also apply a <xref:System.Windows.Style> to individual parts of a control, change the behavior of parts of the control through properties, or add additional parts or change the layout of a control.</span></span> <span data-ttu-id="81490-129">下列範例將示範數個方法可以加入<xref:System.Windows.Style>至<xref:System.Windows.Controls.Menu>控制項。</span><span class="sxs-lookup"><span data-stu-id="81490-129">The following examples demonstrate several ways to add a <xref:System.Windows.Style> to a <xref:System.Windows.Controls.Menu> control.</span></span>  
  
 <span data-ttu-id="81490-130">第一個程式碼範例會定義<xref:System.Windows.Style>呼叫`Simple`，示範如何使用目前的系統設定，在您的風格。</span><span class="sxs-lookup"><span data-stu-id="81490-130">The first code example defines a <xref:System.Windows.Style> called `Simple` that shows how to use the current system settings in your style.</span></span> <span data-ttu-id="81490-131">此程式碼指派 `MenuHighlightBrush` 的色彩作為功能表的背景色彩，以及 `MenuTextBrush` 作為功能表的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="81490-131">The code assigns the color of the `MenuHighlightBrush` as the menu's background color and the `MenuTextBrush` as the menu's foreground color.</span></span> <span data-ttu-id="81490-132">請注意，您需使用資源索引鍵來指派筆刷。</span><span class="sxs-lookup"><span data-stu-id="81490-132">Notice that you use resource keys to assign the brushes.</span></span>  
  
 [!code-xaml[MenuStylesSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 <span data-ttu-id="81490-133">下列範例會使用<xref:System.Windows.Trigger>項目可讓您變更的外觀<xref:System.Windows.Controls.MenuItem>所發生的事件回應<xref:System.Windows.Controls.Menu>。</span><span class="sxs-lookup"><span data-stu-id="81490-133">The following sample uses <xref:System.Windows.Trigger> elements that enable you to change the appearance of a <xref:System.Windows.Controls.MenuItem> in response to events that occur on the <xref:System.Windows.Controls.Menu>.</span></span> <span data-ttu-id="81490-134">當您將滑鼠移<xref:System.Windows.Controls.Menu>的前景色彩和字型特性功能表項目的變更。</span><span class="sxs-lookup"><span data-stu-id="81490-134">When you move the mouse over the <xref:System.Windows.Controls.Menu>, the foreground color and the font characteristics of the menu items change.</span></span>  
  
 [!code-xaml[MenuStylesSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a><span data-ttu-id="81490-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81490-135">See Also</span></span>  
 [<span data-ttu-id="81490-136">WPF 控制項陳列庫範例</span><span class="sxs-lookup"><span data-stu-id="81490-136">WPF Controls Gallery Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160053)
