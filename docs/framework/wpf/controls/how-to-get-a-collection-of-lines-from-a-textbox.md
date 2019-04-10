---
title: HOW TO：從 TextBox 取得文字行集合
ms.date: 03/30/2017
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
ms.openlocfilehash: b7b2f1c2e071388635fb50b1e3573fd7f44334dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224633"
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a><span data-ttu-id="2b369-102">HOW TO：從 TextBox 取得文字行集合</span><span class="sxs-lookup"><span data-stu-id="2b369-102">How to: Get a Collection of Lines from a TextBox</span></span>
<span data-ttu-id="2b369-103">此範例示範如何取得從文字行集合<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="2b369-103">This example shows how to get a collection of lines of text from a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b369-104">範例</span><span class="sxs-lookup"><span data-stu-id="2b369-104">Example</span></span>  
 <span data-ttu-id="2b369-105">下列範例顯示簡單的方法採用<xref:System.Windows.Controls.TextBox>做為引數，並傳回<xref:System.Collections.Specialized.StringCollection>包含中的文字行**TextBox**。</span><span class="sxs-lookup"><span data-stu-id="2b369-105">The following example shows a simple method that takes a <xref:System.Windows.Controls.TextBox> as the argument, and returns a <xref:System.Collections.Specialized.StringCollection> containing the lines of text in the **TextBox**.</span></span>  <span data-ttu-id="2b369-106"><xref:System.Windows.Controls.TextBox.LineCount%2A>屬性用來判斷目前的行數**TextBox**，和<xref:System.Windows.Controls.TextBox.GetLineText%2A>方法可用來擷取每一行，並將它新增至之線條的集合。</span><span class="sxs-lookup"><span data-stu-id="2b369-106">The <xref:System.Windows.Controls.TextBox.LineCount%2A> property is used to determine how many lines are currently in the **TextBox**, and the <xref:System.Windows.Controls.TextBox.GetLineText%2A> method is then used to extract each line and add it to the collection of lines.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a><span data-ttu-id="2b369-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b369-107">See also</span></span>

- [<span data-ttu-id="2b369-108">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="2b369-108">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="2b369-109">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="2b369-109">RichTextBox Overview</span></span>](richtextbox-overview.md)
