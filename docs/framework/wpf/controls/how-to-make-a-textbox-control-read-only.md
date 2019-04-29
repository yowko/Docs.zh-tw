---
title: HOW TO：將 TextBox 控制項設為唯讀
ms.date: 03/30/2017
helpviewer_keywords:
- read-only TextBox controls [WPF]
- TextBox control read-only
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
ms.openlocfilehash: 7f24458eb98bd669d59f15c49d1d9e3beb6833b1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770938"
---
# <a name="how-to-make-a-textbox-control-read-only"></a><span data-ttu-id="dd55a-102">HOW TO：將 TextBox 控制項設為唯讀</span><span class="sxs-lookup"><span data-stu-id="dd55a-102">How to: Make a TextBox Control Read-Only</span></span>
<span data-ttu-id="dd55a-103">此範例示範如何設定<xref:System.Windows.Controls.TextBox>控制項不允許使用者輸入或修改。</span><span class="sxs-lookup"><span data-stu-id="dd55a-103">This example shows how to configure a <xref:System.Windows.Controls.TextBox> control to not allow user input or modification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd55a-104">範例</span><span class="sxs-lookup"><span data-stu-id="dd55a-104">Example</span></span>  
 <span data-ttu-id="dd55a-105">若要防止使用者修改的內容<xref:System.Windows.Controls.TextBox>控制項，並設定<xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A>屬性設定為 **，則為 true**。</span><span class="sxs-lookup"><span data-stu-id="dd55a-105">To prevent users from modifying the contents of a <xref:System.Windows.Controls.TextBox> control, set the <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> attribute to **true**.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 <span data-ttu-id="dd55a-106"><xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A>屬性會影響僅供使用者輸入，它不會影響文字中設定[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]popis<xref:System.Windows.Controls.TextBox>控制項或設定以程式設計方式透過文字<xref:System.Windows.Controls.TextBox.Text%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="dd55a-106">The <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> attribute affects user input only; it does not affect text set in the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] description of a <xref:System.Windows.Controls.TextBox> control, or text set programmatically through the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span>  
  
 <span data-ttu-id="dd55a-107">預設值<xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A>已**false**。</span><span class="sxs-lookup"><span data-stu-id="dd55a-107">The default value of <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> is **false**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd55a-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd55a-108">See also</span></span>

- [<span data-ttu-id="dd55a-109">TextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="dd55a-109">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="dd55a-110">RichTextBox 概觀</span><span class="sxs-lookup"><span data-stu-id="dd55a-110">RichTextBox Overview</span></span>](richtextbox-overview.md)
