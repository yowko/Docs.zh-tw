---
title: 如何：使用 ScrollViewer 建立 Expander
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Expander
- ScrollViewer control [WPF], with Expander control
- Expander control [WPF], creating
- controls [WPF], ScrollViewer
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
ms.openlocfilehash: 6c014d4f6a12bfb58c2ae68f580f632c9478c82f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553058"
---
# <a name="how-to-create-an-expander-with-a-scrollviewer"></a><span data-ttu-id="19ce0-102">如何：使用 ScrollViewer 建立 Expander</span><span class="sxs-lookup"><span data-stu-id="19ce0-102">How to: Create an Expander with a ScrollViewer</span></span>
<span data-ttu-id="19ce0-103">這個範例示範如何建立<xref:System.Windows.Controls.Expander>包含複雜的內容，例如影像和文字控制項。</span><span class="sxs-lookup"><span data-stu-id="19ce0-103">This example shows how to create an <xref:System.Windows.Controls.Expander> control that contains complex content, such as an image and text.</span></span> <span data-ttu-id="19ce0-104">此範例也內含的之內容<xref:System.Windows.Controls.Expander>中<xref:System.Windows.Controls.ScrollViewer>控制項。</span><span class="sxs-lookup"><span data-stu-id="19ce0-104">The example also encloses the content of the <xref:System.Windows.Controls.Expander> in a <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19ce0-105">範例</span><span class="sxs-lookup"><span data-stu-id="19ce0-105">Example</span></span>  
 <span data-ttu-id="19ce0-106">下列範例示範如何建立<xref:System.Windows.Controls.Expander>。</span><span class="sxs-lookup"><span data-stu-id="19ce0-106">The following example shows how to create an <xref:System.Windows.Controls.Expander>.</span></span> <span data-ttu-id="19ce0-107">此範例會使用<xref:System.Windows.Controls.Primitives.BulletDecorator>控制項，包含影像和文字，以定義<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>。</span><span class="sxs-lookup"><span data-stu-id="19ce0-107">The example uses a <xref:System.Windows.Controls.Primitives.BulletDecorator> control, which contains an image and text, in order to define the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.</span></span> <span data-ttu-id="19ce0-108">A<xref:System.Windows.Controls.ScrollViewer>控制項提供一種方法捲動展開的內容。</span><span class="sxs-lookup"><span data-stu-id="19ce0-108">A <xref:System.Windows.Controls.ScrollViewer> control provides a method for scrolling the expanded content.</span></span>  
  
 <span data-ttu-id="19ce0-109">請注意，範例會設定<xref:System.Windows.FrameworkElement.Height%2A>屬性<xref:System.Windows.Controls.ScrollViewer>而不是內容。</span><span class="sxs-lookup"><span data-stu-id="19ce0-109">Note that the example sets the <xref:System.Windows.FrameworkElement.Height%2A> property on the <xref:System.Windows.Controls.ScrollViewer> instead of on the content.</span></span> <span data-ttu-id="19ce0-110">如果<xref:System.Windows.FrameworkElement.Height%2A>設定於內容，<xref:System.Windows.Controls.ScrollViewer>不允許使用者捲動內容。</span><span class="sxs-lookup"><span data-stu-id="19ce0-110">If the <xref:System.Windows.FrameworkElement.Height%2A> is set on the content, the <xref:System.Windows.Controls.ScrollViewer> does not allow the user to scroll the content.</span></span> <span data-ttu-id="19ce0-111"><xref:System.Windows.FrameworkElement.Width%2A>上設定屬性<xref:System.Windows.Controls.Expander>控制項與此設定適用於<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>和展開的內容。</span><span class="sxs-lookup"><span data-stu-id="19ce0-111">The <xref:System.Windows.FrameworkElement.Width%2A> property is set on the <xref:System.Windows.Controls.Expander> control and this setting applies to the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the expanded content.</span></span>  
  
 [!code-xaml[ExpanderRichContent#CreateExpander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## <a name="see-also"></a><span data-ttu-id="19ce0-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19ce0-112">See Also</span></span>  
 <xref:System.Windows.Controls.Expander>  
 [<span data-ttu-id="19ce0-113">Expander 概觀</span><span class="sxs-lookup"><span data-stu-id="19ce0-113">Expander Overview</span></span>](../../../../docs/framework/wpf/controls/expander-overview.md)  
 [<span data-ttu-id="19ce0-114">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="19ce0-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)
