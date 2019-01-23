---
title: HOW TO：列舉 Visual 的繪圖內容
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: a3131b6c86b0f6a7aa79cca305b9c3b2496346f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561944"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a><span data-ttu-id="4d4ad-102">HOW TO：列舉 Visual 的繪圖內容</span><span class="sxs-lookup"><span data-stu-id="4d4ad-102">How to: Enumerate Drawing Content of a Visual</span></span>
<span data-ttu-id="4d4ad-103"><xref:System.Windows.Media.Drawing>物件提供列舉的內容的物件模型<xref:System.Windows.Media.Visual>。</span><span class="sxs-lookup"><span data-stu-id="4d4ad-103">The <xref:System.Windows.Media.Drawing> object provide an object model for enumerating the contents of a <xref:System.Windows.Media.Visual>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d4ad-104">範例</span><span class="sxs-lookup"><span data-stu-id="4d4ad-104">Example</span></span>  
 <span data-ttu-id="4d4ad-105">下列範例會使用<xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>方法來擷取<xref:System.Windows.Media.DrawingGroup>的值<xref:System.Windows.Media.Visual>並列舉它。</span><span class="sxs-lookup"><span data-stu-id="4d4ad-105">The following example uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method to retrieve the <xref:System.Windows.Media.DrawingGroup> value of a <xref:System.Windows.Media.Visual> and enumerate it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d4ad-106">當您要列舉的視覺效果內容時，您要擷取<xref:System.Windows.Media.Drawing>物件和不基礎表示法的轉譯資料作為向量圖形指示清單。</span><span class="sxs-lookup"><span data-stu-id="4d4ad-106">When you are enumerating the contents of the visual, you are retrieving <xref:System.Windows.Media.Drawing> objects, and not the underlying representation of the render data as a vector graphics instruction list.</span></span> <span data-ttu-id="4d4ad-107">如需詳細資訊，請參閱 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4d4ad-107">For more information, see [WPF Graphics Rendering Overview](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a><span data-ttu-id="4d4ad-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d4ad-108">See also</span></span>
- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [<span data-ttu-id="4d4ad-109">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="4d4ad-109">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="4d4ad-110">WPF 圖形轉譯概觀</span><span class="sxs-lookup"><span data-stu-id="4d4ad-110">WPF Graphics Rendering Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
