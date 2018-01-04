---
title: "操作說明：將游標放置在 TextBox 控制項中文字的開頭或結尾"
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
- positioning cursor [WPF]
- TextBox control [WPF], positioning cursor
- cursor [WPF], positioning
ms.assetid: c771a0b8-c6b4-4240-aecd-a21d0ba51a2e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: df30adf232ad782999d8bdf52b1946f84785f98d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-position-the-cursor-at-the-beginning-or-end-of-text-in-a-textbox-control"></a><span data-ttu-id="938b7-102">操作說明：將游標放置在 TextBox 控制項中文字的開頭或結尾</span><span class="sxs-lookup"><span data-stu-id="938b7-102">How to: Position the Cursor at the Beginning or End of Text in a TextBox Control</span></span>
<span data-ttu-id="938b7-103">此範例示範如何將資料指標的開頭或結尾的文字內容置於<xref:System.Windows.Controls.TextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="938b7-103">This example shows how to position the cursor at the beginning or end of the text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="938b7-104">範例</span><span class="sxs-lookup"><span data-stu-id="938b7-104">Example</span></span>  
 <span data-ttu-id="938b7-105">下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]程式碼說明<xref:System.Windows.Controls.TextBox>控制，並將其指派的名稱。</span><span class="sxs-lookup"><span data-stu-id="938b7-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a <xref:System.Windows.Controls.TextBox> control and assigns it a Name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MoveCursorXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_movecursorxaml)]  
  
## <a name="example"></a><span data-ttu-id="938b7-106">範例</span><span class="sxs-lookup"><span data-stu-id="938b7-106">Example</span></span>  
 <span data-ttu-id="938b7-107">若要將游標放在內容的開頭<xref:System.Windows.Controls.TextBox>控制，請呼叫<xref:System.Windows.Controls.TextBox.Select%2A>方法並指定選取範圍開始位置是 0，並選取項目長度為 0。</span><span class="sxs-lookup"><span data-stu-id="938b7-107">To position the cursor at the beginning of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position of 0, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortostart)]
 [!code-vb[TextBox_MiscCode#_CursorToStart](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortostart)]  
  
## <a name="example"></a><span data-ttu-id="938b7-108">範例</span><span class="sxs-lookup"><span data-stu-id="938b7-108">Example</span></span>  
 <span data-ttu-id="938b7-109">內容的結尾將資料指標置於<xref:System.Windows.Controls.TextBox>控制，請呼叫<xref:System.Windows.Controls.TextBox.Select%2A>方法並指定在選取範圍開始位置等於文字內容的長度，然後選取項目長度為 0。</span><span class="sxs-lookup"><span data-stu-id="938b7-109">To position the cursor at the end of the contents of a <xref:System.Windows.Controls.TextBox> control, call the <xref:System.Windows.Controls.TextBox.Select%2A> method and specify the selection start position equal to the  length of the text content, and a selection length of 0.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_CursorToEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_cursortoend)]
 [!code-vb[TextBox_MiscCode#_CursorToEnd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_cursortoend)]  
  
## <a name="see-also"></a><span data-ttu-id="938b7-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="938b7-110">See Also</span></span>  
 [<span data-ttu-id="938b7-111">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="938b7-111">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="938b7-112">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="938b7-112">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
