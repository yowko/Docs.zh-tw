---
title: HOW TO：在 TextBox 使用自訂操作功能表
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [WPF], custom
- menus [WPF], custom
- custom context menus [WPF]
- TextBox control [WPF], custom content menus
ms.assetid: 842d3cd5-6fa0-4be4-8d90-6c7466213b1c
ms.openlocfilehash: b0507c6fa37f0f51f9e12ebe5f908c39c25b50d9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129411"
---
# <a name="how-to-use-a-custom-context-menu-with-a-textbox"></a><span data-ttu-id="9e094-102">HOW TO：在 TextBox 使用自訂操作功能表</span><span class="sxs-lookup"><span data-stu-id="9e094-102">How to: Use a Custom Context Menu with a TextBox</span></span>
<span data-ttu-id="9e094-103">此範例示範如何定義和實作簡單的自訂內容功能表<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="9e094-103">This example shows how to define and implement a simple custom context menu for a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e094-104">範例</span><span class="sxs-lookup"><span data-stu-id="9e094-104">Example</span></span>  
 <span data-ttu-id="9e094-105">下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]範例會定義<xref:System.Windows.Controls.TextBox>包含自訂內容功能表的控制項。</span><span class="sxs-lookup"><span data-stu-id="9e094-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example defines a <xref:System.Windows.Controls.TextBox> control that includes a custom context menu.</span></span>  
  
 <span data-ttu-id="9e094-106">使用所定義的操作功能表<xref:System.Windows.Controls.ContextMenu>項目。</span><span class="sxs-lookup"><span data-stu-id="9e094-106">The context menu is defined using a <xref:System.Windows.Controls.ContextMenu> element.</span></span>  <span data-ttu-id="9e094-107">快顯功能表本身包含的一系列<xref:System.Windows.Controls.MenuItem>項目和<xref:System.Windows.Controls.Separator>項目。</span><span class="sxs-lookup"><span data-stu-id="9e094-107">The context menu itself consists of a series of <xref:System.Windows.Controls.MenuItem> elements and <xref:System.Windows.Controls.Separator> elements.</span></span>  <span data-ttu-id="9e094-108">每個<xref:System.Windows.Controls.MenuItem>內容功能表項目定義命令<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>屬性會定義功能表命令，顯示的文字和<xref:System.Windows.Controls.MenuItem.Click>屬性會指定每個功能表項目處理常式方法。</span><span class="sxs-lookup"><span data-stu-id="9e094-108">Each <xref:System.Windows.Controls.MenuItem> element defines a command in the context menu; the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> attribute defines the display text for the menu command, and the <xref:System.Windows.Controls.MenuItem.Click> attribute specifies a handler method for each menu item.</span></span>  <span data-ttu-id="9e094-109"><xref:System.Windows.Controls.Separator>項目只會導致轉譯先前與後續的功能表項目之間的分隔列。</span><span class="sxs-lookup"><span data-stu-id="9e094-109">The <xref:System.Windows.Controls.Separator> element simply causes a separating line to be rendered between the previous and subsequent menu items.</span></span>  
  
 [!code-xaml[TextBox_ContextMenu#_TextBox_ContextMenuXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml#_textbox_contextmenuxaml)]  
  
## <a name="example"></a><span data-ttu-id="9e094-110">範例</span><span class="sxs-lookup"><span data-stu-id="9e094-110">Example</span></span>  
 <span data-ttu-id="9e094-111">下列範例示範實作程式碼，如先前的內容功能表定義，以及啟用和停用操作功能表的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9e094-111">The following example shows the implementation code for the preceding context menu definition, as well as the code that enables and disables the context menu.</span></span>  <span data-ttu-id="9e094-112"><xref:System.Windows.Controls.ContextMenu.Opened>事件用來動態啟用或停用特定的命令，根據目前的狀態<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="9e094-112">The <xref:System.Windows.Controls.ContextMenu.Opened> event is used to dynamically enable or disable certain commands depending on the current state of the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 <span data-ttu-id="9e094-113">若要還原預設的內容功能表，請使用<xref:System.Windows.DependencyObject.ClearValue%2A>方法，以清除的值<xref:System.Windows.FrameworkElement.ContextMenu%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="9e094-113">To restore the default context menu, use the <xref:System.Windows.DependencyObject.ClearValue%2A> method to clear the value of the <xref:System.Windows.FrameworkElement.ContextMenu%2A> property.</span></span>  <span data-ttu-id="9e094-114">若要完全停用操作功能表，請設定<xref:System.Windows.FrameworkElement.ContextMenu%2A>屬性設為 null 參考 (`Nothing` Visual Basic 中)。</span><span class="sxs-lookup"><span data-stu-id="9e094-114">To disable the context menu altogether, set the <xref:System.Windows.FrameworkElement.ContextMenu%2A> property to a null reference (`Nothing` in Visual Basic).</span></span>  
  
 [!code-csharp[TextBox_ContextMenu#_TextBox_ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml.cs#_textbox_contextmenu)]
 [!code-vb[TextBox_ContextMenu#_TextBox_ContextMenu](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_ContextMenu/VisualBasic/Window1.xaml.vb#_textbox_contextmenu)]  
  
## <a name="see-also"></a><span data-ttu-id="9e094-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e094-115">See also</span></span>

- [<span data-ttu-id="9e094-116">使用內容功能表的拼字檢查</span><span class="sxs-lookup"><span data-stu-id="9e094-116">Use Spell Checking with a Context Menu</span></span>](how-to-use-spell-checking-with-a-context-menu.md)
- [<span data-ttu-id="9e094-117">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="9e094-117">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="9e094-118">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="9e094-118">RichTextBox Overview</span></span>](richtextbox-overview.md)
