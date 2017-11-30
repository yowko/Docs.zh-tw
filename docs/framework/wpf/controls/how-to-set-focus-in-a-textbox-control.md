---
title: "如何：在 TextBox 控制項中設定焦點"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus [WPF], setting
- TextBox control [WPF], setting focus
ms.assetid: 24b61b45-dc2d-425e-9839-b017af7ab86f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a2c25f9dbc05ac9d5c14eb794236613b49f8240e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-focus-in-a-textbox-control"></a><span data-ttu-id="1927a-102">如何：在 TextBox 控制項中設定焦點</span><span class="sxs-lookup"><span data-stu-id="1927a-102">How to: Set Focus in a TextBox Control</span></span>
<span data-ttu-id="1927a-103">這個範例示範如何使用<xref:System.Windows.UIElement.Focus%2A>方法，以將焦點設在<xref:System.Windows.Controls.TextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="1927a-103">This example shows how to use the <xref:System.Windows.UIElement.Focus%2A> method to set focus on a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1927a-104">範例</span><span class="sxs-lookup"><span data-stu-id="1927a-104">Example</span></span>  
 <span data-ttu-id="1927a-105">下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]範例說明簡單<xref:System.Windows.Controls.TextBox>控制項，名為*tbFocusMe*</span><span class="sxs-lookup"><span data-stu-id="1927a-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example describes a simple <xref:System.Windows.Controls.TextBox> control named *tbFocusMe*</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxFocusXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxfocusxaml)]  
  
## <a name="example"></a><span data-ttu-id="1927a-106">範例</span><span class="sxs-lookup"><span data-stu-id="1927a-106">Example</span></span>  
 <span data-ttu-id="1927a-107">下列範例會呼叫<xref:System.Windows.UIElement.Focus%2A>方法，以將焦點設<xref:System.Windows.Controls.TextBox>控制項名稱*tbFocusMe*。</span><span class="sxs-lookup"><span data-stu-id="1927a-107">The following example calls the <xref:System.Windows.UIElement.Focus%2A> method to set the focus on the <xref:System.Windows.Controls.TextBox> control with the Name *tbFocusMe*.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_FocusTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_focustextbox)]
 [!code-vb[TextBox_MiscCode#_FocusTextBox](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_focustextbox)]  
  
## <a name="see-also"></a><span data-ttu-id="1927a-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1927a-108">See Also</span></span>  
 <xref:System.Windows.UIElement.Focusable%2A>  
 <xref:System.Windows.UIElement.IsFocused%2A>  
 [<span data-ttu-id="1927a-109">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="1927a-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="1927a-110">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="1927a-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
