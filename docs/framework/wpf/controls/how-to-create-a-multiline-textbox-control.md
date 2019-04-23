---
title: HOW TO：建立多行 TextBox 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: 29fb4c9498fe163c36e71680242d3ef8cf98c089
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181164"
---
# <a name="how-to-create-a-multiline-textbox-control"></a><span data-ttu-id="e433c-102">HOW TO：建立多行 TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="e433c-102">How to: Create a Multiline TextBox Control</span></span>
<span data-ttu-id="e433c-103">此範例示範如何使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]來定義<xref:System.Windows.Controls.TextBox>會自動擴展以容納多行文字的控制項。</span><span class="sxs-lookup"><span data-stu-id="e433c-103">This example shows how to use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to define a <xref:System.Windows.Controls.TextBox> control that will automatically expand to accommodate multiple lines of text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e433c-104">範例</span><span class="sxs-lookup"><span data-stu-id="e433c-104">Example</span></span>  
 <span data-ttu-id="e433c-105">設定<xref:System.Windows.Controls.TextBox.TextWrapping%2A>屬性設定為**包裝**會導致輸入的文字自動換行至新行時的邊緣<xref:System.Windows.Controls.TextBox>達到控制項時，會自動展開<xref:System.Windows.Controls.TextBox>控制項以容納新的一行，如果必要。</span><span class="sxs-lookup"><span data-stu-id="e433c-105">Setting the <xref:System.Windows.Controls.TextBox.TextWrapping%2A> attribute to **Wrap** will cause entered text to wrap to a new line when the edge of the <xref:System.Windows.Controls.TextBox> control is reached, automatically expanding the <xref:System.Windows.Controls.TextBox> control to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="e433c-106">設定<xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A>屬性設定為 **，則為 true** RETURN 鍵按下時，會自動再次展開要插入新行<xref:System.Windows.Controls.TextBox>以容納新的一行，如有必要。</span><span class="sxs-lookup"><span data-stu-id="e433c-106">Setting the <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> attribute to **true** causes a new line to be inserted when the RETURN key is pressed, once again automatically expanding the <xref:System.Windows.Controls.TextBox> to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="e433c-107"><xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>屬性新增至的捲軸<xref:System.Windows.Controls.TextBox>，如此的內容<xref:System.Windows.Controls.TextBox>捲動如果<xref:System.Windows.Controls.TextBox>擴充框架或視窗的大小超過。</span><span class="sxs-lookup"><span data-stu-id="e433c-107">The <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> attribute adds a scroll bar to the <xref:System.Windows.Controls.TextBox>, so that the contents of the <xref:System.Windows.Controls.TextBox> can be scrolled through if the <xref:System.Windows.Controls.TextBox> expands beyond the size of the frame or window that encloses it.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="e433c-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e433c-108">See also</span></span>

- <xref:System.Windows.TextWrapping>
- [<span data-ttu-id="e433c-109">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="e433c-109">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="e433c-110">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="e433c-110">RichTextBox Overview</span></span>](richtextbox-overview.md)
