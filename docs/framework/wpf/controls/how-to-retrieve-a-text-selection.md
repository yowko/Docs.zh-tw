---
title: HOW TO：擷取文字選取項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], retrieving
- TextBox control [WPF], retrieving text
- retrieving text [WPF]
ms.assetid: d5793172-1e11-4a39-9be0-73f336ed858d
ms.openlocfilehash: b7f0b9ee02a7ace717787fc8eeb6e15649829a49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770782"
---
# <a name="how-to-retrieve-a-text-selection"></a><span data-ttu-id="d7218-102">HOW TO：擷取文字選取項目</span><span class="sxs-lookup"><span data-stu-id="d7218-102">How to: Retrieve a Text Selection</span></span>
<span data-ttu-id="d7218-103">此範例示範使用一種方式<xref:System.Windows.Controls.TextBox.SelectedText%2A>屬性，以擷取使用者已在選取的文字<xref:System.Windows.Controls.TextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="d7218-103">This example shows one way to use the <xref:System.Windows.Controls.TextBox.SelectedText%2A> property to retrieve text that the user has selected in a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7218-104">範例</span><span class="sxs-lookup"><span data-stu-id="d7218-104">Example</span></span>  
 <span data-ttu-id="d7218-105">下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]範例顯示定義<xref:System.Windows.Controls.TextBox>控制項，其中包含一些文字，若要選取，並<xref:System.Windows.Controls.Button>以指定的控制項<xref:System.Windows.Controls.Button.OnClick%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="d7218-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example shows the definition of a <xref:System.Windows.Controls.TextBox> control that contains some text to select, and a <xref:System.Windows.Controls.Button> control with a specified <xref:System.Windows.Controls.Button.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="d7218-106">在此範例中，具有相關聯的按鈕<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件處理常式用來擷取文字選取範圍。</span><span class="sxs-lookup"><span data-stu-id="d7218-106">In this example, a button with an associated <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler is used to retrieve the text selection.</span></span> <span data-ttu-id="d7218-107">當使用者按一下按鈕，<xref:System.Windows.Controls.Button.OnClick%2A>方法在文字方塊中複製任何選取的文字轉換為字串。</span><span class="sxs-lookup"><span data-stu-id="d7218-107">When the user clicks the button, the <xref:System.Windows.Controls.Button.OnClick%2A> method copies any selected text in the textbox into a string.</span></span> <span data-ttu-id="d7218-108">特定情況下，所選取的文字擷取 （按鈕），以及與該選取項目 （複製字串的文字選取範圍） 中，所採取的動作可以輕鬆地修改以配合各種案例。</span><span class="sxs-lookup"><span data-stu-id="d7218-108">The particular circumstances by which the text selection is retrieved (clicking a button), as well as the action taken with that selection (copying the text selection to a string), can easily be modified to accommodate a wide variety of scenarios.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxSelectTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxselecttextxaml)]  
  
## <a name="example"></a><span data-ttu-id="d7218-109">範例</span><span class="sxs-lookup"><span data-stu-id="d7218-109">Example</span></span>  
 <span data-ttu-id="d7218-110">下列C#範例所示<xref:System.Windows.Controls.Button.OnClick%2A>中所定義的按鈕事件處理常式[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]此範例中。</span><span class="sxs-lookup"><span data-stu-id="d7218-110">The following C# example shows an <xref:System.Windows.Controls.Button.OnClick%2A> event handler for the button defined in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] for this example.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_SelectText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_selecttext)]
 [!code-vb[TextBox_MiscCode#_SelectText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_selecttext)]  
  
## <a name="see-also"></a><span data-ttu-id="d7218-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7218-111">See also</span></span>

- [<span data-ttu-id="d7218-112">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="d7218-112">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="d7218-113">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="d7218-113">RichTextBox Overview</span></span>](richtextbox-overview.md)
