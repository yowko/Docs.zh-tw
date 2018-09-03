---
title: ContextMenu 概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ContextMenu
- ContextMenu controls [WPF], about ContextMenu controls
ms.assetid: 16909c42-799a-4561-91e0-7d69dcfeea91
ms.openlocfilehash: 54fd823594fba4500f35ed1d69720a3309e54a36
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43462446"
---
# <a name="contextmenu-overview"></a><span data-ttu-id="145a1-102">ContextMenu 概觀</span><span class="sxs-lookup"><span data-stu-id="145a1-102">ContextMenu Overview</span></span>
<span data-ttu-id="145a1-103"><xref:System.Windows.Controls.ContextMenu>類別代表使用特定內容公開功能的項目<xref:System.Windows.Controls.Menu>。</span><span class="sxs-lookup"><span data-stu-id="145a1-103">The <xref:System.Windows.Controls.ContextMenu> class represents the element that exposes functionality by using a context-specific <xref:System.Windows.Controls.Menu>.</span></span> <span data-ttu-id="145a1-104">一般而言，使用者會公開<xref:System.Windows.Controls.ContextMenu>在[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]以滑鼠右鍵按一下滑鼠按鈕。</span><span class="sxs-lookup"><span data-stu-id="145a1-104">Typically, a user exposes the <xref:System.Windows.Controls.ContextMenu> in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] by right-clicking the mouse button.</span></span> <span data-ttu-id="145a1-105">本主題將介紹<xref:System.Windows.Controls.ContextMenu>項目，並提供範例，示範如何將它用於[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]和程式碼。</span><span class="sxs-lookup"><span data-stu-id="145a1-105">This topic introduces the <xref:System.Windows.Controls.ContextMenu> element and provides examples of how to use it in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and code.</span></span>  
  
  
  
<a name="contextmenu_control"></a>   
## <a name="contextmenu-control"></a><span data-ttu-id="145a1-106">ContextMenu 控制項</span><span class="sxs-lookup"><span data-stu-id="145a1-106">ContextMenu Control</span></span>  
 <span data-ttu-id="145a1-107">A<xref:System.Windows.Controls.ContextMenu>附加至特定的控制項。</span><span class="sxs-lookup"><span data-stu-id="145a1-107">A <xref:System.Windows.Controls.ContextMenu> is attached to a specific control.</span></span> <span data-ttu-id="145a1-108"><xref:System.Windows.Controls.ContextMenu>元素可讓您指定命令或選項，例如與特定控制項相關聯的項目清單會向使用者<xref:System.Windows.Controls.Button>。</span><span class="sxs-lookup"><span data-stu-id="145a1-108">The <xref:System.Windows.Controls.ContextMenu> element enables you to present users with a list of items that specify commands or options that are associated with a particular control, for example, a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="145a1-109">使用者以滑鼠右鍵按一下控制項，即可顯示功能表。</span><span class="sxs-lookup"><span data-stu-id="145a1-109">Users right-click the control to make the menu appear.</span></span> <span data-ttu-id="145a1-110">一般而言，按一下<xref:System.Windows.Controls.MenuItem>開啟子功能表，或讓應用程式執行命令。</span><span class="sxs-lookup"><span data-stu-id="145a1-110">Typically, clicking a <xref:System.Windows.Controls.MenuItem> opens a submenu or causes an application to carry out a command.</span></span>  
  
<a name="creating_contextmenus"></a>   
## <a name="creating-contextmenus"></a><span data-ttu-id="145a1-111">建立 ContextMenu</span><span class="sxs-lookup"><span data-stu-id="145a1-111">Creating ContextMenus</span></span>  
 <span data-ttu-id="145a1-112">下列範例示範如何建立<xref:System.Windows.Controls.ContextMenu>具有子功能表。</span><span class="sxs-lookup"><span data-stu-id="145a1-112">The following examples show how to create a <xref:System.Windows.Controls.ContextMenu> with submenus.</span></span> <span data-ttu-id="145a1-113"><xref:System.Windows.Controls.ContextMenu>控制項附加至按鈕控制項。</span><span class="sxs-lookup"><span data-stu-id="145a1-113">The <xref:System.Windows.Controls.ContextMenu> controls are attached to button controls.</span></span>  
  
 [!code-xaml[ContextMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## <a name="applying-styles-to-a-contextmenu"></a><span data-ttu-id="145a1-114">將樣式套用至 ContextMenu</span><span class="sxs-lookup"><span data-stu-id="145a1-114">Applying Styles to a ContextMenu</span></span>  
 <span data-ttu-id="145a1-115">使用控制項<xref:System.Windows.Style>，您可以大幅變更的外觀和行為<xref:System.Windows.Controls.ContextMenu>而不需要撰寫自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="145a1-115">By using a control <xref:System.Windows.Style>, you can dramatically change the appearance and behavior of a <xref:System.Windows.Controls.ContextMenu> without writing a custom control.</span></span> <span data-ttu-id="145a1-116">除了設定視覺屬性之外，您也可以套用樣式至控制項的組件。</span><span class="sxs-lookup"><span data-stu-id="145a1-116">In addition to setting visual properties, you can also apply styles to parts of a control.</span></span> <span data-ttu-id="145a1-117">例如，您可以藉由使用屬性，來變更控制項組件的行為或您可以將組件，加入或變更的版面配置<xref:System.Windows.Controls.ContextMenu>。</span><span class="sxs-lookup"><span data-stu-id="145a1-117">For example, you can change the behavior of parts of the control by using properties, or you can add parts to, or change the layout of, a <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="145a1-118">下列範例示範數種方式可以加入樣式以<xref:System.Windows.Controls.ContextMenu>控制項。</span><span class="sxs-lookup"><span data-stu-id="145a1-118">The following examples show several ways to add styles to <xref:System.Windows.Controls.ContextMenu> controls.</span></span>  
  
 <span data-ttu-id="145a1-119">第一個範例會定義稱為 `SimpleSysResources` 的樣式，它會顯示如何以您的樣式使用目前的系統設定。</span><span class="sxs-lookup"><span data-stu-id="145a1-119">The first example defines a style called `SimpleSysResources`, which shows how to use the current system settings in your style.</span></span> <span data-ttu-id="145a1-120">此範例將指派<xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A>做為<xref:System.Windows.Controls.Control.Background%2A>色彩並<xref:System.Windows.SystemColors.MenuTextBrushKey%2A>作為<xref:System.Windows.Controls.Control.Foreground%2A>色彩<xref:System.Windows.Controls.ContextMenu>。</span><span class="sxs-lookup"><span data-stu-id="145a1-120">The example assigns <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> as the <xref:System.Windows.Controls.Control.Background%2A> color and <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> as the <xref:System.Windows.Controls.Control.Foreground%2A> color of the <xref:System.Windows.Controls.ContextMenu>.</span></span>  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 <span data-ttu-id="145a1-121">下列範例會使用<xref:System.Windows.Trigger>項目，若要變更的外觀<xref:System.Windows.Controls.Menu>引發的事件回應<xref:System.Windows.Controls.ContextMenu>。</span><span class="sxs-lookup"><span data-stu-id="145a1-121">The following example uses the <xref:System.Windows.Trigger> element to change the appearance of a <xref:System.Windows.Controls.Menu> in response to events that are raised on the <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="145a1-122">當使用者將滑鼠移功能表的外觀<xref:System.Windows.Controls.ContextMenu>變更的項目。</span><span class="sxs-lookup"><span data-stu-id="145a1-122">When a user moves the mouse over the menu, the appearance of the <xref:System.Windows.Controls.ContextMenu> items changes.</span></span>  
  
```xaml  
<Style x:Key="Triggers" TargetType="{x:Type MenuItem}">  
  <Style.Triggers>  
    <Trigger Property="MenuItem.IsMouseOver" Value="true">  
      <Setter Property = "FontSize" Value="16"/>  
      <Setter Property = "FontStyle" Value="Italic"/>  
      <Setter Property = "Foreground" Value="Red"/>  
    </Trigger>  
  </Style.Triggers>  
</Style>  
```  
  
## <a name="see-also"></a><span data-ttu-id="145a1-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="145a1-123">See Also</span></span>  
 <xref:System.Windows.Controls.ContextMenu>  
 <xref:System.Windows.Style>  
 <xref:System.Windows.Controls.Menu>  
 <xref:System.Windows.Controls.MenuItem>  
 [<span data-ttu-id="145a1-124">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="145a1-124">ContextMenu</span></span>](../../../../docs/framework/wpf/controls/contextmenu.md)  
 [<span data-ttu-id="145a1-125">ContextMenu 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="145a1-125">ContextMenu Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/contextmenu-styles-and-templates.md)  
 [<span data-ttu-id="145a1-126">WPF 控制項陳列庫範例</span><span class="sxs-lookup"><span data-stu-id="145a1-126">WPF Controls Gallery Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160053)
