---
title: HOW TO：將游標置放在 TextBox 控制項中文字的開頭或結尾
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- positioning cursor [WPF]
- TextBox control [WPF], positioning cursor
- cursor [WPF], positioning
ms.assetid: c771a0b8-c6b4-4240-aecd-a21d0ba51a2e
ms.openlocfilehash: 3d7da5daf09e06938b8366e0f5f98a599cae4571
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186221"
---
# <a name="how-to-position-the-cursor-at-the-beginning-or-end-of-text-in-a-textbox-control"></a><span data-ttu-id="6829b-102">HOW TO：將游標置放在 TextBox 控制項中文字的開頭或結尾</span><span class="sxs-lookup"><span data-stu-id="6829b-102">How to: Position the Cursor at the Beginning or End of Text in a TextBox Control</span></span>
<span data-ttu-id="6829b-103">此範例示範如何將資料指標的開頭或結尾的文字內容置於<xref:System.Windows.Controls.TextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="6829b-103">This example shows how to position the cursor at the beginning or end of the text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6829b-104">範例</span><span class="sxs-lookup"><span data-stu-id="6829b-104">Example</span></span>  
 <span data-ttu-id="6829b-105">下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]程式碼說明<xref:System.Windows.Controls.TextBox>控制，並將它指派名稱。</span><span class="sxs-lookup"><span data-stu-id="6829b-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a <xref:System.Windows.Controls.TextBox> control and assigns it a Name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MoveCursorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_movecursorxaml)]  
  
## <a name="example"></a><span data-ttu-id="6829b-106">範例</span><span class="sxs-lookup"><span data-stu-id="6829b-106">Example</span></span>  
 <span data-ttu-id="6829b-107">若要將游標放在內容的開頭<xref:System.Windows.Controls.TextBox>控制項，呼叫<xref:System.Windows.Controls.TextBox.Select%2A>方法並指定將選取範圍開始位置是 0，並選取項目長度為 0。</span><span class="sxs-lookup"><span data-stu-id="6829b-107">To position the cursor at the beginning of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position of 0, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToStart](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortostart)]
 [!code-vb[TextBox_MiscCode#_CursorToStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortostart)]  
  
## <a name="example"></a><span data-ttu-id="6829b-108">範例</span><span class="sxs-lookup"><span data-stu-id="6829b-108">Example</span></span>  
 <span data-ttu-id="6829b-109">將游標的內容結尾處<xref:System.Windows.Controls.TextBox>控制項，呼叫<xref:System.Windows.Controls.TextBox.Select%2A>方法並指定相等的長度的文字內容，並選取項目長度為 0 的選取範圍開始位置。</span><span class="sxs-lookup"><span data-stu-id="6829b-109">To position the cursor at the end of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position equal to the  length of the text content, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortoend)]
 [!code-vb[TextBox_MiscCode#_CursorToEnd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortoend)]  
  
## <a name="see-also"></a><span data-ttu-id="6829b-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6829b-110">See also</span></span>

- [<span data-ttu-id="6829b-111">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="6829b-111">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="6829b-112">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="6829b-112">RichTextBox Overview</span></span>](richtextbox-overview.md)
