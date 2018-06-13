---
title: 如何：自訂 ScrollBar 上捲動方塊的大小
ms.date: 03/30/2017
helpviewer_keywords:
- ScrollBar control [WPF]
- customizing thumb size [WPF]
- thumb size [WPF]
ms.assetid: fa32b866-5ca1-4e73-85e7-2ac64b80d194
ms.openlocfilehash: 689b73eb58cdfceb2ce5d4e76cbbc3d6c5af8967
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551800"
---
# <a name="how-to-customize-the-thumb-size-on-a-scrollbar"></a><span data-ttu-id="cc576-102">如何：自訂 ScrollBar 上捲動方塊的大小</span><span class="sxs-lookup"><span data-stu-id="cc576-102">How to: Customize the Thumb Size on a ScrollBar</span></span>
<span data-ttu-id="cc576-103">本主題說明如何設定<xref:System.Windows.Controls.Primitives.Thumb>的<xref:System.Windows.Controls.Primitives.ScrollBar>固定的大小，以及如何指定的最小大小<xref:System.Windows.Controls.Primitives.Thumb>的<xref:System.Windows.Controls.Primitives.ScrollBar>。</span><span class="sxs-lookup"><span data-stu-id="cc576-103">This topic explains how to set the <xref:System.Windows.Controls.Primitives.Thumb> of a <xref:System.Windows.Controls.Primitives.ScrollBar> to a fixed size and how to specify a minimum size for the <xref:System.Windows.Controls.Primitives.Thumb> of a <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc576-104">範例</span><span class="sxs-lookup"><span data-stu-id="cc576-104">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="cc576-105">描述</span><span class="sxs-lookup"><span data-stu-id="cc576-105">Description</span></span>  
 <span data-ttu-id="cc576-106">下列範例會建立<xref:System.Windows.Controls.Primitives.ScrollBar>具有<xref:System.Windows.Controls.Primitives.Thumb>具有固定大小。</span><span class="sxs-lookup"><span data-stu-id="cc576-106">The following example creates a <xref:System.Windows.Controls.Primitives.ScrollBar> that has a <xref:System.Windows.Controls.Primitives.Thumb> with a fixed size.</span></span> <span data-ttu-id="cc576-107">範例會設定<xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A>屬性<xref:System.Windows.Controls.Primitives.Thumb>至<xref:System.Double.NaN>和設定的高度<xref:System.Windows.Controls.Primitives.Thumb>。</span><span class="sxs-lookup"><span data-stu-id="cc576-107">The example sets the <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> property of the <xref:System.Windows.Controls.Primitives.Thumb> to <xref:System.Double.NaN> and sets the height of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  <span data-ttu-id="cc576-108">若要建立水平<xref:System.Windows.Controls.Primitives.ScrollBar>與<xref:System.Windows.Controls.Primitives.Thumb>固定的寬度時，設定寬度<xref:System.Windows.Controls.Primitives.Thumb>。</span><span class="sxs-lookup"><span data-stu-id="cc576-108">To create a horizontal <xref:System.Windows.Controls.Primitives.ScrollBar> with a <xref:System.Windows.Controls.Primitives.Thumb> that has a fixed width, set the width of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="cc576-109">程式碼</span><span class="sxs-lookup"><span data-stu-id="cc576-109">Code</span></span>  
 [!code-xaml[ScrollBarCustomThumbSize#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#1)]  
  
## <a name="description"></a><span data-ttu-id="cc576-110">描述</span><span class="sxs-lookup"><span data-stu-id="cc576-110">Description</span></span>  
 <span data-ttu-id="cc576-111">下列範例會建立<xref:System.Windows.Controls.Primitives.ScrollBar>具有<xref:System.Windows.Controls.Primitives.Thumb>具有最小大小。</span><span class="sxs-lookup"><span data-stu-id="cc576-111">The following example creates a <xref:System.Windows.Controls.Primitives.ScrollBar> that has a <xref:System.Windows.Controls.Primitives.Thumb> with a minimum size.</span></span> <span data-ttu-id="cc576-112">此範例設定的值<xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>。</span><span class="sxs-lookup"><span data-stu-id="cc576-112">The example sets the value of <xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>.</span></span> <span data-ttu-id="cc576-113">若要建立水平<xref:System.Windows.Controls.Primitives.ScrollBar>與<xref:System.Windows.Controls.Primitives.Thumb>最小寬度時，設定<xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>。</span><span class="sxs-lookup"><span data-stu-id="cc576-113">To create a horizontal <xref:System.Windows.Controls.Primitives.ScrollBar> with a <xref:System.Windows.Controls.Primitives.Thumb> that has a minimum width, set the <xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="cc576-114">程式碼</span><span class="sxs-lookup"><span data-stu-id="cc576-114">Code</span></span>  
 [!code-xaml[ScrollBarCustomThumbSize#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#2)]  
  
## <a name="see-also"></a><span data-ttu-id="cc576-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc576-115">See Also</span></span>  
 [<span data-ttu-id="cc576-116">ScrollBar 樣式和範本</span><span class="sxs-lookup"><span data-stu-id="cc576-116">ScrollBar Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/scrollbar-styles-and-templates.md)
