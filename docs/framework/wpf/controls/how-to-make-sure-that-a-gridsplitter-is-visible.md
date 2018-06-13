---
title: 如何：確保 GridSplitter 是可見的
ms.date: 03/30/2017
helpviewer_keywords:
- GridSplitter control [WPF], ensuring visibility of
ms.assetid: 0a62a964-89c8-48f0-9023-5df721a8cf47
ms.openlocfilehash: 926df118bfd8e7ab3d1f0c953d0b6debafd59073
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554816"
---
# <a name="how-to-make-sure-that-a-gridsplitter-is-visible"></a><span data-ttu-id="a556c-102">如何：確保 GridSplitter 是可見的</span><span class="sxs-lookup"><span data-stu-id="a556c-102">How to: Make Sure That a GridSplitter Is Visible</span></span>
<span data-ttu-id="a556c-103">這個範例示範如何確定<xref:System.Windows.Controls.GridSplitter>中的其他控制項並未隱藏控制項<xref:System.Windows.Controls.Grid>。</span><span class="sxs-lookup"><span data-stu-id="a556c-103">This example shows how to make sure a <xref:System.Windows.Controls.GridSplitter> control is not hidden by the other controls in a <xref:System.Windows.Controls.Grid>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a556c-104">範例</span><span class="sxs-lookup"><span data-stu-id="a556c-104">Example</span></span>  
 <span data-ttu-id="a556c-105"><xref:System.Windows.Controls.Panel.Children%2A>的<xref:System.Windows.Controls.Grid>控制項以它們在標記或程式碼中定義的順序轉譯。</span><span class="sxs-lookup"><span data-stu-id="a556c-105">The <xref:System.Windows.Controls.Panel.Children%2A> of a <xref:System.Windows.Controls.Grid> control are rendered in the order that they are defined in markup or code.</span></span> <span data-ttu-id="a556c-106"><xref:System.Windows.Controls.GridSplitter> 如果您沒有定義輸出為中的最後一個項目，可以由其他控制項隱藏控制項<xref:System.Windows.Controls.Panel.Children%2A>集合，或若您授與其他控制更高層<xref:System.Windows.Controls.Panel.ZIndexProperty>。</span><span class="sxs-lookup"><span data-stu-id="a556c-106"><xref:System.Windows.Controls.GridSplitter> controls can be hidden by other controls if you do not define them as the last elements in the <xref:System.Windows.Controls.Panel.Children%2A> collection or if you give other controls a higher <xref:System.Windows.Controls.Panel.ZIndexProperty>.</span></span>  
  
 <span data-ttu-id="a556c-107">若要避免隱藏<xref:System.Windows.Controls.GridSplitter>控制項，執行下列其中一項。</span><span class="sxs-lookup"><span data-stu-id="a556c-107">To prevent hidden <xref:System.Windows.Controls.GridSplitter> controls, do one of the following.</span></span>  
  
-   <span data-ttu-id="a556c-108">請確定<xref:System.Windows.Controls.GridSplitter>控制項是最後<xref:System.Windows.Controls.Panel.Children%2A>加入<xref:System.Windows.Controls.Grid>。</span><span class="sxs-lookup"><span data-stu-id="a556c-108">Make sure that <xref:System.Windows.Controls.GridSplitter> controls are the last <xref:System.Windows.Controls.Panel.Children%2A> added to the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="a556c-109">下列範例所示<xref:System.Windows.Controls.GridSplitter>中的最後一個項目為<xref:System.Windows.Controls.Panel.Children%2A>集合<xref:System.Windows.Controls.Grid>。</span><span class="sxs-lookup"><span data-stu-id="a556c-109">The following example shows the <xref:System.Windows.Controls.GridSplitter> as the last element in the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.Grid>.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterLastChild](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterlastchild)]  
  
-   <span data-ttu-id="a556c-110">設定<xref:System.Windows.Controls.Panel.ZIndexProperty>上<xref:System.Windows.Controls.GridSplitter>高於的控制項，否則會隱藏起來。</span><span class="sxs-lookup"><span data-stu-id="a556c-110">Set the <xref:System.Windows.Controls.Panel.ZIndexProperty> on the <xref:System.Windows.Controls.GridSplitter> to be higher than a control that would otherwise hide it.</span></span> <span data-ttu-id="a556c-111">下列範例會提供<xref:System.Windows.Controls.GridSplitter>控制更高層<xref:System.Windows.Controls.Panel.ZIndexProperty>比<xref:System.Windows.Controls.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="a556c-111">The following example gives the <xref:System.Windows.Controls.GridSplitter> control a higher <xref:System.Windows.Controls.Panel.ZIndexProperty> than the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterZIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterzindex)]  
  
-   <span data-ttu-id="a556c-112">否則會隱藏在控制項上設定邊界<xref:System.Windows.Controls.GridSplitter>以便<xref:System.Windows.Controls.GridSplitter>公開。</span><span class="sxs-lookup"><span data-stu-id="a556c-112">Set margins on the control that would otherwise hide the <xref:System.Windows.Controls.GridSplitter> so that the <xref:System.Windows.Controls.GridSplitter> is exposed.</span></span> <span data-ttu-id="a556c-113">下列範例會設定邊界上的控制項，否則會覆疊和隱藏<xref:System.Windows.Controls.GridSplitter>。</span><span class="sxs-lookup"><span data-stu-id="a556c-113">The following example sets margins on a control that would otherwise overlay and hide the <xref:System.Windows.Controls.GridSplitter>.</span></span>  
  
 [!code-xaml[GridSplitterSnips#GridSplitterMargin](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplittermargin)]  
  
## <a name="see-also"></a><span data-ttu-id="a556c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a556c-114">See Also</span></span>  
 <xref:System.Windows.Controls.GridSplitter>  
 [<span data-ttu-id="a556c-115">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="a556c-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)
