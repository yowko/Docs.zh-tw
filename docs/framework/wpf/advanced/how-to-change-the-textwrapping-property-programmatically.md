---
title: HOW TO：以程式設計方式變更 TextWrapping 屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], changing TextWrapping property programmatically
- TextWrapping property [WPF], changing programmatically
ms.assetid: 30d25554-4c82-4df9-a8d6-35683a4a13bb
ms.openlocfilehash: 6cf0993d0433e03a3c19bb59bf3621672e164b43
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640221"
---
# <a name="how-to-change-the-textwrapping-property-programmatically"></a><span data-ttu-id="b245d-102">HOW TO：以程式設計方式變更 TextWrapping 屬性</span><span class="sxs-lookup"><span data-stu-id="b245d-102">How to: Change the TextWrapping Property Programmatically</span></span>
## <a name="example"></a><span data-ttu-id="b245d-103">範例</span><span class="sxs-lookup"><span data-stu-id="b245d-103">Example</span></span>  
 <span data-ttu-id="b245d-104">下列程式碼範例示範如何變更的值<xref:System.Windows.Controls.TextBlock.TextWrapping%2A>屬性以程式設計的方式。</span><span class="sxs-lookup"><span data-stu-id="b245d-104">The following code example shows how to change the value of the <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> property programmatically.</span></span>  
  
 <span data-ttu-id="b245d-105">三個<xref:System.Windows.Controls.Button>項目會放在<xref:System.Windows.Controls.StackPanel>中的項目[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b245d-105">Three <xref:System.Windows.Controls.Button> elements are placed within a <xref:System.Windows.Controls.StackPanel> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="b245d-106">每個<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件<xref:System.Windows.Controls.Button>與程式碼中的事件處理常式對應。</span><span class="sxs-lookup"><span data-stu-id="b245d-106">Each <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event for a <xref:System.Windows.Controls.Button> corresponds with an event handler in the code.</span></span> <span data-ttu-id="b245d-107">事件處理常式使用同名<xref:System.Windows.Controls.TextBlock.TextWrapping%2A>值將會套用到`txt2`按下按鈕。</span><span class="sxs-lookup"><span data-stu-id="b245d-107">The event handlers use the same name as the <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> value they will apply to `txt2` when the button is clicked.</span></span> <span data-ttu-id="b245d-108">此外中的文字`txt1`(<xref:System.Windows.Controls.TextBlock>不會顯示在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) 會更新以反映屬性中的變更。</span><span class="sxs-lookup"><span data-stu-id="b245d-108">Also, the text in `txt1` (a <xref:System.Windows.Controls.TextBlock> not shown in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) is updated to reflect the change in the property.</span></span>  
  
 [!code-xaml[TextWrapProperty#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml#1)]  
  
 [!code-csharp[TextWrapProperty#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextWrapProperty/CSharp/Window1.xaml.cs#2)]
 [!code-vb[TextWrapProperty#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="b245d-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b245d-109">See also</span></span>
- <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>
- <xref:System.Windows.TextWrapping>
