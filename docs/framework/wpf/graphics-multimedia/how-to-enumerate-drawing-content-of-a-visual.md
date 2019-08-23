---
title: 作法：列舉視覺物件的繪圖內容
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: 25aa0c3706005c1e16cedd7e06914db764545ebb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930075"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a><span data-ttu-id="3cc50-102">HOW TO：列舉視覺物件的繪圖內容</span><span class="sxs-lookup"><span data-stu-id="3cc50-102">How to: Enumerate Drawing Content of a Visual</span></span>
<span data-ttu-id="3cc50-103">物件提供用<xref:System.Windows.Media.Visual>來列舉內容的物件模型。 <xref:System.Windows.Media.Drawing></span><span class="sxs-lookup"><span data-stu-id="3cc50-103">The <xref:System.Windows.Media.Drawing> object provide an object model for enumerating the contents of a <xref:System.Windows.Media.Visual>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cc50-104">範例</span><span class="sxs-lookup"><span data-stu-id="3cc50-104">Example</span></span>  
 <span data-ttu-id="3cc50-105">下列範例會使用<xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>方法來<xref:System.Windows.Media.DrawingGroup>取出的值<xref:System.Windows.Media.Visual> , 並加以列舉。</span><span class="sxs-lookup"><span data-stu-id="3cc50-105">The following example uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method to retrieve the <xref:System.Windows.Media.DrawingGroup> value of a <xref:System.Windows.Media.Visual> and enumerate it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3cc50-106">當您列舉視覺效果的內容時, 您會抓取<xref:System.Windows.Media.Drawing>物件, 而不是以向量圖形指示清單的形式呈現資料的基礎標記法。</span><span class="sxs-lookup"><span data-stu-id="3cc50-106">When you are enumerating the contents of the visual, you are retrieving <xref:System.Windows.Media.Drawing> objects, and not the underlying representation of the render data as a vector graphics instruction list.</span></span> <span data-ttu-id="3cc50-107">如需詳細資訊，請參閱 [WPF 圖形轉譯概觀](wpf-graphics-rendering-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="3cc50-107">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a><span data-ttu-id="3cc50-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3cc50-108">See also</span></span>

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [<span data-ttu-id="3cc50-109">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="3cc50-109">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="3cc50-110">WPF 圖形轉譯概觀</span><span class="sxs-lookup"><span data-stu-id="3cc50-110">WPF Graphics Rendering Overview</span></span>](wpf-graphics-rendering-overview.md)
