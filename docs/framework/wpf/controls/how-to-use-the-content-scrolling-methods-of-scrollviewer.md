---
title: HOW TO：使用 ScrollViewer 的內容捲動方法
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IScrollInfo interface [WPF]
- scrolling methods [WPF]
- ScrollViewer control [WPF], scrolling methods
ms.assetid: 4708cc65-6510-45f8-82e6-30b0d3e30045
ms.openlocfilehash: 0f2ed1c0ac0d29a47ab98e0329ff161fd54daba6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547036"
---
# <a name="how-to-use-the-content-scrolling-methods-of-scrollviewer"></a><span data-ttu-id="0d41e-102">HOW TO：使用 ScrollViewer 的內容捲動方法</span><span class="sxs-lookup"><span data-stu-id="0d41e-102">How to: Use the Content-Scrolling Methods of ScrollViewer</span></span>
<span data-ttu-id="0d41e-103">此範例示範如何使用捲動方法<xref:System.Windows.Controls.ScrollViewer>項目。</span><span class="sxs-lookup"><span data-stu-id="0d41e-103">This example shows how to use the scrolling methods of the <xref:System.Windows.Controls.ScrollViewer> element.</span></span> <span data-ttu-id="0d41e-104">這些方法會提供累加捲動內容的列或頁面上，在<xref:System.Windows.Controls.ScrollViewer>。</span><span class="sxs-lookup"><span data-stu-id="0d41e-104">These methods provide incremental scrolling of content, either by line or by page, in a <xref:System.Windows.Controls.ScrollViewer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d41e-105">範例</span><span class="sxs-lookup"><span data-stu-id="0d41e-105">Example</span></span>  
 <span data-ttu-id="0d41e-106">下列範例會建立<xref:System.Windows.Controls.ScrollViewer>名為`sv1`，其中裝載子系<xref:System.Windows.Controls.TextBlock>項目。</span><span class="sxs-lookup"><span data-stu-id="0d41e-106">The following example creates a <xref:System.Windows.Controls.ScrollViewer> named `sv1`, which hosts a child <xref:System.Windows.Controls.TextBlock> element.</span></span> <span data-ttu-id="0d41e-107">因為<xref:System.Windows.Controls.TextBlock>大於父代<xref:System.Windows.Controls.ScrollViewer>，捲軸出現，以啟用捲動功能。</span><span class="sxs-lookup"><span data-stu-id="0d41e-107">Because the <xref:System.Windows.Controls.TextBlock> is larger than the parent <xref:System.Windows.Controls.ScrollViewer>, scroll bars appear in order to enable scrolling.</span></span> <span data-ttu-id="0d41e-108"><xref:System.Windows.Controls.Button> 在個別左側停駐項目代表各種捲動方法<xref:System.Windows.Controls.StackPanel>。</span><span class="sxs-lookup"><span data-stu-id="0d41e-108"><xref:System.Windows.Controls.Button> elements that represent the various scrolling methods are docked on the left in a separate <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="0d41e-109">每個<xref:System.Windows.Controls.Button>中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案會呼叫相關的自訂方法可控制捲動行為中的<xref:System.Windows.Controls.ScrollViewer>。</span><span class="sxs-lookup"><span data-stu-id="0d41e-109">Each <xref:System.Windows.Controls.Button> in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file calls a related custom method that controls scrolling behavior in <xref:System.Windows.Controls.ScrollViewer>.</span></span>  
  
 [!code-xaml[ScrollViewerMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="0d41e-110">下列範例會使用<xref:System.Windows.Controls.ScrollViewer.LineUp%2A>和<xref:System.Windows.Controls.ScrollViewer.LineDown%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="0d41e-110">The following example uses the <xref:System.Windows.Controls.ScrollViewer.LineUp%2A> and <xref:System.Windows.Controls.ScrollViewer.LineDown%2A> methods.</span></span>  
  
 [!code-csharp[ScrollViewerMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ScrollViewerMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewerMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="0d41e-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d41e-111">See also</span></span>
- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.StackPanel>
