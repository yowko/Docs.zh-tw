---
title: TextBlock 概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], TextBlock
- TextBlock control [WPF]
ms.assetid: 24720bca-341a-4b03-8a6b-7a678023b10a
ms.openlocfilehash: c18ca64a25f436c3ed2ccd9e04316e25bab00a66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556077"
---
# <a name="textblock-overview"></a><span data-ttu-id="39591-102">TextBlock 概觀</span><span class="sxs-lookup"><span data-stu-id="39591-102">TextBlock Overview</span></span>
<span data-ttu-id="39591-103"><xref:System.Windows.Controls.TextBlock>控制項提供有彈性的文字支援[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="39591-103">The <xref:System.Windows.Controls.TextBlock> control provides flexible text support for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span> <span data-ttu-id="39591-104">這個元素的主要目標是不需要超過一個段落文字的基本 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 案例。</span><span class="sxs-lookup"><span data-stu-id="39591-104">The element is targeted primarily toward basic [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenarios that do not require more than one paragraph of text.</span></span> <span data-ttu-id="39591-105">它支援一些屬性可讓簡報，精確地控制，例如<xref:System.Windows.Controls.TextBlock.FontFamily%2A>， <xref:System.Windows.Controls.TextBlock.FontSize%2A>， <xref:System.Windows.Controls.TextBlock.FontWeight%2A>， <xref:System.Windows.Controls.TextBlock.TextEffects%2A>，和<xref:System.Windows.Controls.TextBlock.TextWrapping%2A>。</span><span class="sxs-lookup"><span data-stu-id="39591-105">It supports a number of properties that enable precise control of presentation, such as <xref:System.Windows.Controls.TextBlock.FontFamily%2A>, <xref:System.Windows.Controls.TextBlock.FontSize%2A>, <xref:System.Windows.Controls.TextBlock.FontWeight%2A>, <xref:System.Windows.Controls.TextBlock.TextEffects%2A>, and <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>.</span></span> <span data-ttu-id="39591-106">文字內容可以使用加入<xref:System.Windows.Controls.TextBlock.Text%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="39591-106">Text content can be added using the <xref:System.Windows.Controls.TextBlock.Text%2A> property.</span></span> <span data-ttu-id="39591-107">在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中使用時，開始和結束標記之間的內容會以隱含方式加入為元素的文字。</span><span class="sxs-lookup"><span data-stu-id="39591-107">When used in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], content between the open and closing tag is implicitly added as the text of the element.</span></span>  
  
 <span data-ttu-id="39591-108">A<xref:System.Windows.Controls.TextBlock>項目可以具現化很簡單地使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="39591-108">A <xref:System.Windows.Controls.TextBlock> element can be instantiated very simply using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[TextBlockSnip_XAML#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip_XAML/CS/default.xaml#2)]  
  
 <span data-ttu-id="39591-109">同樣地，使用<xref:System.Windows.Controls.TextBlock>程式碼中的項目是相當簡單。</span><span class="sxs-lookup"><span data-stu-id="39591-109">Similarly, usage of the <xref:System.Windows.Controls.TextBlock> element in code is relatively simple.</span></span>  
  
 [!code-csharp[TextBlockSnip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip/CSharp/TextBlockSnips.cs#1)]
 [!code-vb[TextBlockSnip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBlockSnip/VisualBasic/TextBlockSnips.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="39591-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39591-110">See Also</span></span>  
 <xref:System.Windows.Controls.Label>
