---
title: HOW TO：使用 IScrollInfo 介面捲動內容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ScrollViewer control [WPF], scrolling content
- scrolling content [WPF]
- IScrollInfo interface [WPF]
ms.assetid: d8700bef-a3f8-4c12-9de2-fc3b79f32cd3
ms.openlocfilehash: 145c58064b8557f9cb4730ec9272c354c7aa9c1b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378974"
---
# <a name="how-to-scroll-content-by-using-the-iscrollinfo-interface"></a><span data-ttu-id="baa60-102">HOW TO：使用 IScrollInfo 介面捲動內容</span><span class="sxs-lookup"><span data-stu-id="baa60-102">How to: Scroll Content by Using the IScrollInfo Interface</span></span>
<span data-ttu-id="baa60-103">此範例示範如何使用捲動內容<xref:System.Windows.Controls.Primitives.IScrollInfo>介面。</span><span class="sxs-lookup"><span data-stu-id="baa60-103">This example shows how to scroll content by using the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="baa60-104">範例</span><span class="sxs-lookup"><span data-stu-id="baa60-104">Example</span></span>  
 <span data-ttu-id="baa60-105">下列範例示範的功能<xref:System.Windows.Controls.Primitives.IScrollInfo>介面。</span><span class="sxs-lookup"><span data-stu-id="baa60-105">The following example demonstrates the features of the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.</span></span> <span data-ttu-id="baa60-106">此範例會建立<xref:System.Windows.Controls.StackPanel>中的項目[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，巢狀方式置於父代<xref:System.Windows.Controls.ScrollViewer>。</span><span class="sxs-lookup"><span data-stu-id="baa60-106">The example creates a <xref:System.Windows.Controls.StackPanel> element in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that is nested in a parent <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="baa60-107">子項目的<xref:System.Windows.Controls.StackPanel>可使用定義的方法以邏輯方式捲動<xref:System.Windows.Controls.Primitives.IScrollInfo>介面，並轉換成的執行個體<xref:System.Windows.Controls.StackPanel>(`sp1`) 程式碼中。</span><span class="sxs-lookup"><span data-stu-id="baa60-107">The child elements of the <xref:System.Windows.Controls.StackPanel> can be scrolled logically by using the methods defined by the <xref:System.Windows.Controls.Primitives.IScrollInfo> interface and cast to the instance of <xref:System.Windows.Controls.StackPanel> (`sp1`) in code.</span></span>  
  
 [!code-xaml[IScrollInfoMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="baa60-108">每個<xref:System.Windows.Controls.Button>中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案觸發程序的相關聯的自訂方法，控制捲動行為中的<xref:System.Windows.Controls.StackPanel>。</span><span class="sxs-lookup"><span data-stu-id="baa60-108">Each <xref:System.Windows.Controls.Button> in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file triggers an associated custom method that controls scrolling behavior in <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="baa60-109">下列範例示範如何使用<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A>並<xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>方法，它也以一般方式示範如何使用所有位置的方法，<xref:System.Windows.Controls.Primitives.IScrollInfo>類別定義。</span><span class="sxs-lookup"><span data-stu-id="baa60-109">The following example shows how to use the <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> and <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> methods; it also generically shows how to use all the positioning methods that the <xref:System.Windows.Controls.Primitives.IScrollInfo> class defines.</span></span>  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="baa60-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="baa60-110">See also</span></span>
- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- <xref:System.Windows.Controls.StackPanel>
- [<span data-ttu-id="baa60-111">ScrollViewer 概觀</span><span class="sxs-lookup"><span data-stu-id="baa60-111">ScrollViewer Overview</span></span>](scrollviewer-overview.md)
- [<span data-ttu-id="baa60-112">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="baa60-112">How-to Topics</span></span>](scrollviewer-how-to-topics.md)
- [<span data-ttu-id="baa60-113">面板概觀</span><span class="sxs-lookup"><span data-stu-id="baa60-113">Panels Overview</span></span>](panels-overview.md)
