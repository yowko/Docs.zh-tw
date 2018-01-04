---
title: "如何：從 TextBox 取得線條集合"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12d32266bb901f6ce47d19d92d6f0785277aa7c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a><span data-ttu-id="d6f7e-102">如何：從 TextBox 取得線條集合</span><span class="sxs-lookup"><span data-stu-id="d6f7e-102">How to: Get a Collection of Lines from a TextBox</span></span>
<span data-ttu-id="d6f7e-103">這個範例示範如何取得集合中的文字行<xref:System.Windows.Controls.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="d6f7e-103">This example shows how to get a collection of lines of text from a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6f7e-104">範例</span><span class="sxs-lookup"><span data-stu-id="d6f7e-104">Example</span></span>  
 <span data-ttu-id="d6f7e-105">下列範例顯示簡單的方法採用<xref:System.Windows.Controls.TextBox>做為引數，並傳回<xref:System.Collections.Specialized.StringCollection>包含中的文字行**文字方塊**。</span><span class="sxs-lookup"><span data-stu-id="d6f7e-105">The following example shows a simple method that takes a <xref:System.Windows.Controls.TextBox> as the argument, and returns a <xref:System.Collections.Specialized.StringCollection> containing the lines of text in the **TextBox**.</span></span>  <span data-ttu-id="d6f7e-106"><xref:System.Windows.Controls.TextBox.LineCount%2A>屬性用來判斷目前有多少行**文字方塊**，而<xref:System.Windows.Controls.TextBox.GetLineText%2A>方法可用來擷取每一行，並將它加入至線條的集合。</span><span class="sxs-lookup"><span data-stu-id="d6f7e-106">The <xref:System.Windows.Controls.TextBox.LineCount%2A> property is used to determine how many lines are currently in the **TextBox**, and the <xref:System.Windows.Controls.TextBox.GetLineText%2A> method is then used to extract each line and add it to the collection of lines.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a><span data-ttu-id="d6f7e-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="d6f7e-107">See Also</span></span>  
 [<span data-ttu-id="d6f7e-108">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="d6f7e-108">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="d6f7e-109">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="d6f7e-109">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
