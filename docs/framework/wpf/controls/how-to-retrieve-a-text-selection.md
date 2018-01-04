---
title: "如何：擷取文字選取項目"
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
- text [WPF], retrieving
- TextBox control [WPF], retrieving text
- retrieving text [WPF]
ms.assetid: d5793172-1e11-4a39-9be0-73f336ed858d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32be79811de4b8056449c2c6d6c53eca8cc063f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-a-text-selection"></a><span data-ttu-id="4139c-102">如何：擷取文字選取項目</span><span class="sxs-lookup"><span data-stu-id="4139c-102">How to: Retrieve a Text Selection</span></span>
<span data-ttu-id="4139c-103">這個範例會示範一個方式來使用<xref:System.Windows.Controls.TextBox.SelectedText%2A>屬性，以擷取使用者在選取的文字<xref:System.Windows.Controls.TextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="4139c-103">This example shows one way to use the <xref:System.Windows.Controls.TextBox.SelectedText%2A> property to retrieve text that the user has selected in a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4139c-104">範例</span><span class="sxs-lookup"><span data-stu-id="4139c-104">Example</span></span>  
 <span data-ttu-id="4139c-105">下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]範例會示範定義<xref:System.Windows.Controls.TextBox>控制項，其中包含一些文字，若要選取，而<xref:System.Windows.Controls.Button>與指定的控制項<xref:System.Windows.Controls.Button.OnClick%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="4139c-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example shows the definition of a <xref:System.Windows.Controls.TextBox> control that contains some text to select, and a <xref:System.Windows.Controls.Button> control with a specified <xref:System.Windows.Controls.Button.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="4139c-106">在此範例中，具有相關聯的按鈕<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件處理常式用來擷取文字選取範圍。</span><span class="sxs-lookup"><span data-stu-id="4139c-106">In this example, a button with an associated <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler is used to retrieve the text selection.</span></span> <span data-ttu-id="4139c-107">當使用者按一下按鈕，<xref:System.Windows.Controls.Button.OnClick%2A>方法在文字方塊中選取的文字複製成字串。</span><span class="sxs-lookup"><span data-stu-id="4139c-107">When the user clicks the button, the <xref:System.Windows.Controls.Button.OnClick%2A> method copies any selected text in the textbox into a string.</span></span> <span data-ttu-id="4139c-108">特定情況下，根據的文字選取範圍會擷取 （按一下按鈕），以及與該選取項目 （複製為字串的文字選取範圍） 中，所採取的動作可以輕鬆地修改以容納各種案例。</span><span class="sxs-lookup"><span data-stu-id="4139c-108">The particular circumstances by which the text selection is retrieved (clicking a button), as well as the action taken with that selection (copying the text selection to a string), can easily be modified to accommodate a wide variety of scenarios.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxSelectTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxselecttextxaml)]  
  
## <a name="example"></a><span data-ttu-id="4139c-109">範例</span><span class="sxs-lookup"><span data-stu-id="4139c-109">Example</span></span>  
 <span data-ttu-id="4139c-110">下列[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)]範例所示<xref:System.Windows.Controls.Button.OnClick%2A>按鈕中所定義的事件處理常式[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]此範例中。</span><span class="sxs-lookup"><span data-stu-id="4139c-110">The following [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] example shows an <xref:System.Windows.Controls.Button.OnClick%2A> event handler for the button defined in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] for this example.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_SelectText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_selecttext)]
 [!code-vb[TextBox_MiscCode#_SelectText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_selecttext)]  
  
## <a name="see-also"></a><span data-ttu-id="4139c-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="4139c-111">See Also</span></span>  
 [<span data-ttu-id="4139c-112">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="4139c-112">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="4139c-113">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="4139c-113">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
