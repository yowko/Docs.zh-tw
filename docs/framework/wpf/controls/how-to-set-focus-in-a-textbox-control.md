---
title: HOW TO：在 TextBox 控制項中設定焦點
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus [WPF], setting
- TextBox control [WPF], setting focus
ms.assetid: 24b61b45-dc2d-425e-9839-b017af7ab86f
ms.openlocfilehash: 1ab7fa5f5ce895d163e3db3dd020fee3f29b7153
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590704"
---
# <a name="how-to-set-focus-in-a-textbox-control"></a><span data-ttu-id="cf1e8-102">HOW TO：在 TextBox 控制項中設定焦點</span><span class="sxs-lookup"><span data-stu-id="cf1e8-102">How to: Set Focus in a TextBox Control</span></span>
<span data-ttu-id="cf1e8-103">此範例示範如何使用<xref:System.Windows.UIElement.Focus%2A>方法，以將焦點設定在<xref:System.Windows.Controls.TextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="cf1e8-103">This example shows how to use the <xref:System.Windows.UIElement.Focus%2A> method to set focus on a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf1e8-104">範例</span><span class="sxs-lookup"><span data-stu-id="cf1e8-104">Example</span></span>  
 <span data-ttu-id="cf1e8-105">下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]範例說明簡單<xref:System.Windows.Controls.TextBox>控制項，名為*tbFocusMe*</span><span class="sxs-lookup"><span data-stu-id="cf1e8-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example describes a simple <xref:System.Windows.Controls.TextBox> control named *tbFocusMe*</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxFocusXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxfocusxaml)]  
  
## <a name="example"></a><span data-ttu-id="cf1e8-106">範例</span><span class="sxs-lookup"><span data-stu-id="cf1e8-106">Example</span></span>  
 <span data-ttu-id="cf1e8-107">下列範例會呼叫<xref:System.Windows.UIElement.Focus%2A>方法，以將焦點設<xref:System.Windows.Controls.TextBox>具有名稱控制項*tbFocusMe*。</span><span class="sxs-lookup"><span data-stu-id="cf1e8-107">The following example calls the <xref:System.Windows.UIElement.Focus%2A> method to set the focus on the <xref:System.Windows.Controls.TextBox> control with the Name *tbFocusMe*.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_FocusTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_focustextbox)]
 [!code-vb[TextBox_MiscCode#_FocusTextBox](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_focustextbox)]  
  
## <a name="see-also"></a><span data-ttu-id="cf1e8-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf1e8-108">See also</span></span>
- <xref:System.Windows.UIElement.Focusable%2A>
- <xref:System.Windows.UIElement.IsFocused%2A>
- [<span data-ttu-id="cf1e8-109">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="cf1e8-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [<span data-ttu-id="cf1e8-110">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="cf1e8-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
