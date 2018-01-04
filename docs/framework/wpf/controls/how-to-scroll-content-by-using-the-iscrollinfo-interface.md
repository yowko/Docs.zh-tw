---
title: "如何：使用 IScrollInfo 介面捲動內容"
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
- ScrollViewer control [WPF], scrolling content
- scrolling content [WPF]
- IScrollInfo interface [WPF]
ms.assetid: d8700bef-a3f8-4c12-9de2-fc3b79f32cd3
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae6d9439ad76258105d615960bd05ecf458eb613
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-scroll-content-by-using-the-iscrollinfo-interface"></a><span data-ttu-id="9b650-102">如何：使用 IScrollInfo 介面捲動內容</span><span class="sxs-lookup"><span data-stu-id="9b650-102">How to: Scroll Content by Using the IScrollInfo Interface</span></span>
<span data-ttu-id="9b650-103">這個範例示範如何使用捲動內容<xref:System.Windows.Controls.Primitives.IScrollInfo>介面。</span><span class="sxs-lookup"><span data-stu-id="9b650-103">This example shows how to scroll content by using the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b650-104">範例</span><span class="sxs-lookup"><span data-stu-id="9b650-104">Example</span></span>  
 <span data-ttu-id="9b650-105">下列範例示範的功能<xref:System.Windows.Controls.Primitives.IScrollInfo>介面。</span><span class="sxs-lookup"><span data-stu-id="9b650-105">The following example demonstrates the features of the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.</span></span> <span data-ttu-id="9b650-106">此範例會建立<xref:System.Windows.Controls.StackPanel>中的項目[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]父系中的巢狀<xref:System.Windows.Controls.ScrollViewer>。</span><span class="sxs-lookup"><span data-stu-id="9b650-106">The example creates a <xref:System.Windows.Controls.StackPanel> element in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that is nested in a parent <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="9b650-107">子項目的<xref:System.Windows.Controls.StackPanel>可使用所定義之方法以邏輯方式捲動<xref:System.Windows.Controls.Primitives.IScrollInfo>介面，並轉換成執行個體<xref:System.Windows.Controls.StackPanel>(`sp1`) 程式碼中。</span><span class="sxs-lookup"><span data-stu-id="9b650-107">The child elements of the <xref:System.Windows.Controls.StackPanel> can be scrolled logically by using the methods defined by the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface and cast to the instance of <xref:System.Windows.Controls.StackPanel> (`sp1`) in code.</span></span>  
  
 [!code-xaml[IScrollInfoMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="9b650-108">每個<xref:System.Windows.Controls.Button>中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案觸發程序的相關聯的自訂方法，控制捲動行為中的<xref:System.Windows.Controls.StackPanel>。</span><span class="sxs-lookup"><span data-stu-id="9b650-108">Each <xref:System.Windows.Controls.Button> in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file triggers an associated custom method that controls scrolling behavior in <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="9b650-109">下列範例示範如何使用<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A>和<xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>方法; 它通常也會示範如何使用所有定位的方法，<xref:System.Windows.Controls.Primitives.IScrollInfo>類別定義。</span><span class="sxs-lookup"><span data-stu-id="9b650-109">The following example shows how to use the <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> and <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> methods; it also generically shows how to use all the positioning methods that the <xref:System.Windows.Controls.Primitives.IScrollInfo> class defines.</span></span>  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="9b650-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="9b650-110">See Also</span></span>  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>  
 <xref:System.Windows.Controls.StackPanel>  
 [<span data-ttu-id="9b650-111">ScrollViewer 概觀</span><span class="sxs-lookup"><span data-stu-id="9b650-111">ScrollViewer Overview</span></span>](../../../../docs/framework/wpf/controls/scrollviewer-overview.md)  
 [<span data-ttu-id="9b650-112">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="9b650-112">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/scrollviewer-how-to-topics.md)  
 [<span data-ttu-id="9b650-113">面板概觀</span><span class="sxs-lookup"><span data-stu-id="9b650-113">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
