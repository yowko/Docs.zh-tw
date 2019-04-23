---
title: HOW TO：平移元素
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: 9c1b873a89820e85efb99789f483c4832fb23cf7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59231184"
---
# <a name="how-to-translate-an-element"></a><span data-ttu-id="7d1df-102">HOW TO：平移元素</span><span class="sxs-lookup"><span data-stu-id="7d1df-102">How to: Translate an Element</span></span>
<span data-ttu-id="7d1df-103">此範例示範如何平移 （移動） 項目使用<xref:System.Windows.Media.TranslateTransform>。</span><span class="sxs-lookup"><span data-stu-id="7d1df-103">This example shows how to translate (move) an element by using a <xref:System.Windows.Media.TranslateTransform>.</span></span>  
  
 <span data-ttu-id="7d1df-104"><xref:System.Windows.Media.TranslateTransform>類別是特別適用於不支援絕對位置的面板內移動元素。</span><span class="sxs-lookup"><span data-stu-id="7d1df-104">The <xref:System.Windows.Media.TranslateTransform> class is especially useful for moving elements inside panels that do not support absolute positioning.</span></span> <span data-ttu-id="7d1df-105">例如，藉由套用<xref:System.Windows.Media.TranslateTransform>要<xref:System.Windows.UIElement.RenderTransform%2A>元素的屬性，您可以移動中的項目<xref:System.Windows.Controls.StackPanel>或<xref:System.Windows.Controls.DockPanel>。</span><span class="sxs-lookup"><span data-stu-id="7d1df-105">For example, by applying a <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of an element, you can move an element within a <xref:System.Windows.Controls.StackPanel> or <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="7d1df-106">使用<xref:System.Windows.Media.TranslateTransform.X%2A>屬性<xref:System.Windows.Media.TranslateTransform>來指定，單位為像素元素沿著 x 軸移動。</span><span class="sxs-lookup"><span data-stu-id="7d1df-106">Use the <xref:System.Windows.Media.TranslateTransform.X%2A> property of the <xref:System.Windows.Media.TranslateTransform> to specify the amount, in pixels, to move the element along the x-axis.</span></span> <span data-ttu-id="7d1df-107">使用<xref:System.Windows.Media.TranslateTransform.Y%2A>屬性來指定，單位為像素元素沿著 y 軸移動。</span><span class="sxs-lookup"><span data-stu-id="7d1df-107">Use the <xref:System.Windows.Media.TranslateTransform.Y%2A> property to specify the amount, in pixels, to move the element along the y-axis.</span></span> <span data-ttu-id="7d1df-108">最後，套用<xref:System.Windows.Media.TranslateTransform>至<xref:System.Windows.UIElement.RenderTransform%2A>項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="7d1df-108">Finally, apply the <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="7d1df-109">下列範例會使用<xref:System.Windows.Media.TranslateTransform>向下移元素 50 像素為右到 50 個像素。</span><span class="sxs-lookup"><span data-stu-id="7d1df-109">The following example uses a <xref:System.Windows.Media.TranslateTransform> to move an element 50 pixels to the right and 50 pixels down.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d1df-110">範例</span><span class="sxs-lookup"><span data-stu-id="7d1df-110">Example</span></span>  
 [!code-xaml[transformsSample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 <span data-ttu-id="7d1df-111">如需完整範例，請參閱 [2D 轉換範例](https://go.microsoft.com/fwlink/?LinkID=158252)。</span><span class="sxs-lookup"><span data-stu-id="7d1df-111">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d1df-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d1df-112">See also</span></span>

- [<span data-ttu-id="7d1df-113">轉換概觀</span><span class="sxs-lookup"><span data-stu-id="7d1df-113">Transforms Overview</span></span>](transforms-overview.md)
