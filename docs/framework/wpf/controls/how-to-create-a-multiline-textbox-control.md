---
title: 如何：建立多行 TextBox 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: 9f4c9e637b686c82b4ec8a4a5d6d3a78d46f97c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553283"
---
# <a name="how-to-create-a-multiline-textbox-control"></a><span data-ttu-id="a8f6a-102">如何：建立多行 TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="a8f6a-102">How to: Create a Multiline TextBox Control</span></span>
<span data-ttu-id="a8f6a-103">這個範例示範如何使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]定義<xref:System.Windows.Controls.TextBox>會自動擴展以容納多行文字的控制項。</span><span class="sxs-lookup"><span data-stu-id="a8f6a-103">This example shows how to use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to define a <xref:System.Windows.Controls.TextBox> control that will automatically expand to accommodate multiple lines of text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8f6a-104">範例</span><span class="sxs-lookup"><span data-stu-id="a8f6a-104">Example</span></span>  
 <span data-ttu-id="a8f6a-105">設定<xref:System.Windows.Controls.TextBox.TextWrapping%2A>屬性**包裝**會導致輸入的文字換行至新行時的邊緣<xref:System.Windows.Controls.TextBox>達到控制項時，自動展開<xref:System.Windows.Controls.TextBox>以包含新行的空間，如果控制項必要的。</span><span class="sxs-lookup"><span data-stu-id="a8f6a-105">Setting the <xref:System.Windows.Controls.TextBox.TextWrapping%2A> attribute to **Wrap** will cause entered text to wrap to a new line when the edge of the <xref:System.Windows.Controls.TextBox> control is reached, automatically expanding the <xref:System.Windows.Controls.TextBox> control to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="a8f6a-106">設定<xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A>屬性**true**導致 RETURN 鍵按下時，再次自動展開要插入新行<xref:System.Windows.Controls.TextBox>來視需要加入新行的空間。</span><span class="sxs-lookup"><span data-stu-id="a8f6a-106">Setting the <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> attribute to **true** causes a new line to be inserted when the RETURN key is pressed, once again automatically expanding the <xref:System.Windows.Controls.TextBox> to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="a8f6a-107"><xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>屬性新增至捲軸<xref:System.Windows.Controls.TextBox>，如此的內容<xref:System.Windows.Controls.TextBox>可以捲動，即透過如果<xref:System.Windows.Controls.TextBox>展開超過框架或將它關閉的視窗。</span><span class="sxs-lookup"><span data-stu-id="a8f6a-107">The <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> attribute adds a scroll bar to the <xref:System.Windows.Controls.TextBox>, so that the contents of the <xref:System.Windows.Controls.TextBox> can be scrolled through if the <xref:System.Windows.Controls.TextBox> expands beyond the size of the frame or window that encloses it.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="a8f6a-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8f6a-108">See Also</span></span>  
 <xref:System.Windows.TextWrapping>  
 [<span data-ttu-id="a8f6a-109">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="a8f6a-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="a8f6a-110">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="a8f6a-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
