---
title: 如何：建立多行 TextBox 控制項
description: 瞭解如何使用 XAML 來定義 TextBox 控制項，以擴充以容納 Windows Presentation Foundation 應用程式中的多行文字。
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: 0a88d4d768884df135afddb491431650b9ba2d24
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166248"
---
# <a name="how-to-create-a-multiline-textbox-control"></a><span data-ttu-id="eaa05-103">如何：建立多行 TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="eaa05-103">How to: Create a Multiline TextBox Control</span></span>
<span data-ttu-id="eaa05-104">這個範例示範如何使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 來定義 <xref:System.Windows.Controls.TextBox> 會自動展開以容納多行文字的控制項。</span><span class="sxs-lookup"><span data-stu-id="eaa05-104">This example shows how to use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to define a <xref:System.Windows.Controls.TextBox> control that will automatically expand to accommodate multiple lines of text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eaa05-105">範例</span><span class="sxs-lookup"><span data-stu-id="eaa05-105">Example</span></span>  
 <span data-ttu-id="eaa05-106">將 <xref:System.Windows.Controls.TextBox.TextWrapping%2A> 屬性設定為**wrap**會使輸入的文字在到達控制項的邊緣時換行，以在 <xref:System.Windows.Controls.TextBox> 必要時自動展開 <xref:System.Windows.Controls.TextBox> 控制項以包含新行的空間。</span><span class="sxs-lookup"><span data-stu-id="eaa05-106">Setting the <xref:System.Windows.Controls.TextBox.TextWrapping%2A> attribute to **Wrap** will cause entered text to wrap to a new line when the edge of the <xref:System.Windows.Controls.TextBox> control is reached, automatically expanding the <xref:System.Windows.Controls.TextBox> control to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="eaa05-107">將 <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> 屬性設定為**true**時，會在按下 RETURN 鍵時插入新的行，再次自動展開 <xref:System.Windows.Controls.TextBox> 以包含新行的空間（如有需要）。</span><span class="sxs-lookup"><span data-stu-id="eaa05-107">Setting the <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> attribute to **true** causes a new line to be inserted when the RETURN key is pressed, once again automatically expanding the <xref:System.Windows.Controls.TextBox> to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="eaa05-108"><xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>屬性會將捲軸加入至 <xref:System.Windows.Controls.TextBox> ，因此， <xref:System.Windows.Controls.TextBox> 如果展開的內容 <xref:System.Windows.Controls.TextBox> 超出環繞其範圍的框架或視窗大小，就可以滾動到。</span><span class="sxs-lookup"><span data-stu-id="eaa05-108">The <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> attribute adds a scroll bar to the <xref:System.Windows.Controls.TextBox>, so that the contents of the <xref:System.Windows.Controls.TextBox> can be scrolled through if the <xref:System.Windows.Controls.TextBox> expands beyond the size of the frame or window that encloses it.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="eaa05-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eaa05-109">See also</span></span>

- <xref:System.Windows.TextWrapping>
- [<span data-ttu-id="eaa05-110">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="eaa05-110">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="eaa05-111">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="eaa05-111">RichTextBox Overview</span></span>](richtextbox-overview.md)
