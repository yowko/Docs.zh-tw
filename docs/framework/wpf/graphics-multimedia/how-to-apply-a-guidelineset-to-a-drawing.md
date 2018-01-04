---
title: "如何：對圖形套用 GuidelineSet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GuidelineSet property [WPF], applying to drawings
- graphics [WPF], GuidelineSet property
ms.assetid: 45f3e0b4-8820-45a7-b865-b8ea5b17b0c8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5cf689f8a7c475dbdda416297e28118d43bfdbff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-a-guidelineset-to-a-drawing"></a><span data-ttu-id="4fc65-102">如何：對圖形套用 GuidelineSet</span><span class="sxs-lookup"><span data-stu-id="4fc65-102">How to: Apply a GuidelineSet to a Drawing</span></span>
<span data-ttu-id="4fc65-103">這個範例示範如何套用<xref:System.Windows.Media.GuidelineSet>至<xref:System.Windows.Media.DrawingGroup>。</span><span class="sxs-lookup"><span data-stu-id="4fc65-103">This example shows how to apply a <xref:System.Windows.Media.GuidelineSet> to a <xref:System.Windows.Media.DrawingGroup>.</span></span>  
  
 <span data-ttu-id="4fc65-104"><xref:System.Windows.Media.DrawingGroup>類別是唯一的類型<xref:System.Windows.Media.Drawing>具有<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="4fc65-104">The <xref:System.Windows.Media.DrawingGroup> class is the only type of <xref:System.Windows.Media.Drawing> that has a <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> property.</span></span> <span data-ttu-id="4fc65-105">若要套用<xref:System.Windows.Media.GuidelineSet>至另一種<xref:System.Windows.Media.Drawing>，將它加入至<xref:System.Windows.Media.DrawingGroup>，然後套用<xref:System.Windows.Media.GuidelineSet>到您<xref:System.Windows.Media.DrawingGroup>。</span><span class="sxs-lookup"><span data-stu-id="4fc65-105">To apply a <xref:System.Windows.Media.GuidelineSet> to another type of <xref:System.Windows.Media.Drawing>, add it to a <xref:System.Windows.Media.DrawingGroup> and then apply the <xref:System.Windows.Media.GuidelineSet> to your <xref:System.Windows.Media.DrawingGroup>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fc65-106">範例</span><span class="sxs-lookup"><span data-stu-id="4fc65-106">Example</span></span>  
 <span data-ttu-id="4fc65-107">下列範例會建立兩個<xref:System.Windows.Media.DrawingGroup>幾乎完全相同; 唯一的差別是物件： 第二個<xref:System.Windows.Media.DrawingGroup>具有<xref:System.Windows.Media.GuidelineSet>第一個則沒有。</span><span class="sxs-lookup"><span data-stu-id="4fc65-107">The following example creates two <xref:System.Windows.Media.DrawingGroup> objects that are almost identical; the only difference is: the second <xref:System.Windows.Media.DrawingGroup> has a <xref:System.Windows.Media.GuidelineSet> and the first does not.</span></span>  
  
 <span data-ttu-id="4fc65-108">下圖顯示範例的輸出。</span><span class="sxs-lookup"><span data-stu-id="4fc65-108">The following illustration shows the output from the example.</span></span> <span data-ttu-id="4fc65-109">因為兩個之間的差異是呈現<xref:System.Windows.Media.DrawingGroup>物件太過精巧而、 放大的繪圖部分。</span><span class="sxs-lookup"><span data-stu-id="4fc65-109">Because the rendering difference between the two <xref:System.Windows.Media.DrawingGroup> objects is so subtle, portions of the drawings are enlarged.</span></span>  
  
 <span data-ttu-id="4fc65-110">![具有與不具 GuidelineSet 的 DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")</span><span class="sxs-lookup"><span data-stu-id="4fc65-110">![A DrawingGroup with and without a GuidelineSet](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupGuidelineSetExample.cs#graphicsmmdrawinggroupguidelinesetexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupGuidelineSetExample.xaml#graphicsmmdrawinggroupguidelinesetexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="4fc65-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="4fc65-111">See Also</span></span>  
 <xref:System.Windows.Media.DrawingGroup>  
 <xref:System.Windows.Media.GuidelineSet>  
 [<span data-ttu-id="4fc65-112">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="4fc65-112">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
