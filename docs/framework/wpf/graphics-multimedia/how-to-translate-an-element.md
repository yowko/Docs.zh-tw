---
title: 操作說明：平移元素
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: ba6bda09a4ee189cdd1a32eed8f65b32d1a9abe4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187309"
---
# <a name="how-to-translate-an-element"></a><span data-ttu-id="9b49b-102">操作說明：平移元素</span><span class="sxs-lookup"><span data-stu-id="9b49b-102">How to: Translate an Element</span></span>
<span data-ttu-id="9b49b-103">此示例演示如何使用 轉換（移動）元素<xref:System.Windows.Media.TranslateTransform>。</span><span class="sxs-lookup"><span data-stu-id="9b49b-103">This example shows how to translate (move) an element by using a <xref:System.Windows.Media.TranslateTransform>.</span></span>  
  
 <span data-ttu-id="9b49b-104">該<xref:System.Windows.Media.TranslateTransform>類對於在不支援絕對位置的面板內移動元素特別有用。</span><span class="sxs-lookup"><span data-stu-id="9b49b-104">The <xref:System.Windows.Media.TranslateTransform> class is especially useful for moving elements inside panels that do not support absolute positioning.</span></span> <span data-ttu-id="9b49b-105">例如，<xref:System.Windows.Media.TranslateTransform>通過將 應用於元素的屬性<xref:System.Windows.UIElement.RenderTransform%2A>，可以在<xref:System.Windows.Controls.StackPanel>或<xref:System.Windows.Controls.DockPanel>中移動元素。</span><span class="sxs-lookup"><span data-stu-id="9b49b-105">For example, by applying a <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of an element, you can move an element within a <xref:System.Windows.Controls.StackPanel> or <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="9b49b-106">使用<xref:System.Windows.Media.TranslateTransform.X%2A>屬性<xref:System.Windows.Media.TranslateTransform>指定以圖元為單位的數量沿 X 軸移動元素。</span><span class="sxs-lookup"><span data-stu-id="9b49b-106">Use the <xref:System.Windows.Media.TranslateTransform.X%2A> property of the <xref:System.Windows.Media.TranslateTransform> to specify the amount, in pixels, to move the element along the x-axis.</span></span> <span data-ttu-id="9b49b-107">使用<xref:System.Windows.Media.TranslateTransform.Y%2A>屬性指定沿 y 軸移動元素的數量（以圖元為單位）。</span><span class="sxs-lookup"><span data-stu-id="9b49b-107">Use the <xref:System.Windows.Media.TranslateTransform.Y%2A> property to specify the amount, in pixels, to move the element along the y-axis.</span></span> <span data-ttu-id="9b49b-108">最後，將<xref:System.Windows.Media.TranslateTransform>應用<xref:System.Windows.UIElement.RenderTransform%2A>到 元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="9b49b-108">Finally, apply the <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="9b49b-109">下面的示例使用<xref:System.Windows.Media.TranslateTransform>將元素向右移動 50 圖元，向下移動 50 圖元。</span><span class="sxs-lookup"><span data-stu-id="9b49b-109">The following example uses a <xref:System.Windows.Media.TranslateTransform> to move an element 50 pixels to the right and 50 pixels down.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b49b-110">範例</span><span class="sxs-lookup"><span data-stu-id="9b49b-110">Example</span></span>  
 [!code-xaml[transformsSample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 <span data-ttu-id="9b49b-111">如需完整範例，請參閱 [2D 轉換範例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)。</span><span class="sxs-lookup"><span data-stu-id="9b49b-111">For the complete sample, see [2-D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b49b-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b49b-112">See also</span></span>

- [<span data-ttu-id="9b49b-113">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="9b49b-113">Transforms Overview</span></span>](transforms-overview.md)
