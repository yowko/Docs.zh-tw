---
title: 操作說明：平移元素
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: 0089f294c54662d1ea4929ec25c08464072cbdde
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561934"
---
# <a name="how-to-translate-an-element"></a><span data-ttu-id="b9502-102">操作說明：平移元素</span><span class="sxs-lookup"><span data-stu-id="b9502-102">How to: Translate an Element</span></span>
<span data-ttu-id="b9502-103">這個範例示範如何平移 （移動） 項目使用<xref:System.Windows.Media.TranslateTransform>。</span><span class="sxs-lookup"><span data-stu-id="b9502-103">This example shows how to translate (move) an element by using a <xref:System.Windows.Media.TranslateTransform>.</span></span>  
  
 <span data-ttu-id="b9502-104"><xref:System.Windows.Media.TranslateTransform>類別是特別適用於移動面板不支援絕對定位的項目。</span><span class="sxs-lookup"><span data-stu-id="b9502-104">The <xref:System.Windows.Media.TranslateTransform> class is especially useful for moving elements inside panels that do not support absolute positioning.</span></span> <span data-ttu-id="b9502-105">例如，藉由套用<xref:System.Windows.Media.TranslateTransform>至<xref:System.Windows.UIElement.RenderTransform%2A>某個項目的屬性，您可以移動中的項目<xref:System.Windows.Controls.StackPanel>或<xref:System.Windows.Controls.DockPanel>。</span><span class="sxs-lookup"><span data-stu-id="b9502-105">For example, by applying a <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of an element, you can move an element within a <xref:System.Windows.Controls.StackPanel> or <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="b9502-106">使用<xref:System.Windows.Media.TranslateTransform.X%2A>屬性<xref:System.Windows.Media.TranslateTransform>指定像素為單位，若要移動的項目沿著 x 軸單位的數量。</span><span class="sxs-lookup"><span data-stu-id="b9502-106">Use the <xref:System.Windows.Media.TranslateTransform.X%2A> property of the <xref:System.Windows.Media.TranslateTransform> to specify the amount, in pixels, to move the element along the x-axis.</span></span> <span data-ttu-id="b9502-107">使用<xref:System.Windows.Media.TranslateTransform.Y%2A>屬性，以像素為單位，若要移動的項目沿著 y 軸指定單位的數量。</span><span class="sxs-lookup"><span data-stu-id="b9502-107">Use the <xref:System.Windows.Media.TranslateTransform.Y%2A> property to specify the amount, in pixels, to move the element along the y-axis.</span></span> <span data-ttu-id="b9502-108">最後，套用<xref:System.Windows.Media.TranslateTransform>至<xref:System.Windows.UIElement.RenderTransform%2A>元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="b9502-108">Finally, apply the <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="b9502-109">下列範例會使用<xref:System.Windows.Media.TranslateTransform>即可向下移動項目 50 像素為 50 和右邊的像素。</span><span class="sxs-lookup"><span data-stu-id="b9502-109">The following example uses a <xref:System.Windows.Media.TranslateTransform> to move an element 50 pixels to the right and 50 pixels down.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9502-110">範例</span><span class="sxs-lookup"><span data-stu-id="b9502-110">Example</span></span>  
 [!code-xaml[transformsSample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 <span data-ttu-id="b9502-111">如需完整範例，請參閱 [2D 轉換範例](http://go.microsoft.com/fwlink/?LinkID=158252)。</span><span class="sxs-lookup"><span data-stu-id="b9502-111">For the complete sample, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9502-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9502-112">See Also</span></span>  
 [<span data-ttu-id="b9502-113">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="b9502-113">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
