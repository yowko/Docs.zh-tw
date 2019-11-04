---
title: 如何：工具列上的樣式控制項
ms.date: 03/30/2017
helpviewer_keywords:
- styling controls on toolbar [WPF]
- toolbars [WPF]
- customizing controls on toolbar [WPF]
ms.assetid: ba6ae056-d6a9-4c24-90f8-467ab0bc0b1a
ms.openlocfilehash: 78b9fc505c3c9045a0ca16ddaa1361c90bcc896a
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459414"
---
# <a name="how-to-style-controls-on-a-toolbar"></a><span data-ttu-id="c27da-102">如何：工具列上的樣式控制項</span><span class="sxs-lookup"><span data-stu-id="c27da-102">How to: Style Controls on a ToolBar</span></span>
<span data-ttu-id="c27da-103"><xref:System.Windows.Controls.ToolBar> 會定義 <xref:System.Windows.ResourceKey> 物件，以便在 <xref:System.Windows.Controls.ToolBar>內指定控制項的樣式。</span><span class="sxs-lookup"><span data-stu-id="c27da-103">The <xref:System.Windows.Controls.ToolBar> defines <xref:System.Windows.ResourceKey> objects to specify the style of controls within the <xref:System.Windows.Controls.ToolBar>.</span></span>  <span data-ttu-id="c27da-104">若要在 <xref:System.Windows.Controls.ToolBar>中設定控制項的樣式，請將樣式的 `x:key` 屬性設為 <xref:System.Windows.Controls.ToolBar>中定義的 <xref:System.Windows.ResourceKey>。</span><span class="sxs-lookup"><span data-stu-id="c27da-104">To style a control in a <xref:System.Windows.Controls.ToolBar>, set the `x:key` attribute of the style to a <xref:System.Windows.ResourceKey> defined in <xref:System.Windows.Controls.ToolBar>.</span></span>  
  
 <span data-ttu-id="c27da-105"><xref:System.Windows.Controls.ToolBar> 會定義下列 <xref:System.Windows.ResourceKey> 物件：</span><span class="sxs-lookup"><span data-stu-id="c27da-105">The <xref:System.Windows.Controls.ToolBar> defines the following <xref:System.Windows.ResourceKey> objects:</span></span>  
  
- <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.CheckBoxStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.MenuStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.RadioButtonStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.SeparatorStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.TextBoxStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.ToggleButtonStyleKey%2A>  
  
## <a name="example"></a><span data-ttu-id="c27da-106">範例</span><span class="sxs-lookup"><span data-stu-id="c27da-106">Example</span></span>  
 <span data-ttu-id="c27da-107">下列範例會定義 <xref:System.Windows.Controls.ToolBar>內控制項的樣式。</span><span class="sxs-lookup"><span data-stu-id="c27da-107">The following example defines styles for the controls within a <xref:System.Windows.Controls.ToolBar>.</span></span>  
  
 [!code-xaml[ToolBar_snip#ToolBarAllStyles](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbarallstyles)]  
[!code-xaml[ToolBar_snip#ToolBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbar)]  
  
## <a name="see-also"></a><span data-ttu-id="c27da-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="c27da-108">See also</span></span>

- [<span data-ttu-id="c27da-109">設定樣式和範本</span><span class="sxs-lookup"><span data-stu-id="c27da-109">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
