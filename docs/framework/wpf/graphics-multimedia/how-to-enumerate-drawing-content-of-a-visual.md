---
title: HOW TO：列舉視覺物件的繪圖內容
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: 4f0afc1075fe66c7f154fcef3cd883709db55316
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108000"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a><span data-ttu-id="35ed6-102">HOW TO：列舉視覺物件的繪圖內容</span><span class="sxs-lookup"><span data-stu-id="35ed6-102">How to: Enumerate Drawing Content of a Visual</span></span>
<span data-ttu-id="35ed6-103"><xref:System.Windows.Media.Drawing>物件提供列舉的內容的物件模型<xref:System.Windows.Media.Visual>。</span><span class="sxs-lookup"><span data-stu-id="35ed6-103">The <xref:System.Windows.Media.Drawing> object provide an object model for enumerating the contents of a <xref:System.Windows.Media.Visual>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35ed6-104">範例</span><span class="sxs-lookup"><span data-stu-id="35ed6-104">Example</span></span>  
 <span data-ttu-id="35ed6-105">下列範例會使用<xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>方法來擷取<xref:System.Windows.Media.DrawingGroup>的值<xref:System.Windows.Media.Visual>並列舉它。</span><span class="sxs-lookup"><span data-stu-id="35ed6-105">The following example uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method to retrieve the <xref:System.Windows.Media.DrawingGroup> value of a <xref:System.Windows.Media.Visual> and enumerate it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35ed6-106">當您要列舉的視覺效果內容時，您要擷取<xref:System.Windows.Media.Drawing>物件和不基礎表示法的轉譯資料作為向量圖形指示清單。</span><span class="sxs-lookup"><span data-stu-id="35ed6-106">When you are enumerating the contents of the visual, you are retrieving <xref:System.Windows.Media.Drawing> objects, and not the underlying representation of the render data as a vector graphics instruction list.</span></span> <span data-ttu-id="35ed6-107">如需詳細資訊，請參閱 [WPF 圖形轉譯概觀](wpf-graphics-rendering-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="35ed6-107">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a><span data-ttu-id="35ed6-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35ed6-108">See also</span></span>

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [<span data-ttu-id="35ed6-109">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="35ed6-109">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="35ed6-110">WPF 圖形轉譯概觀</span><span class="sxs-lookup"><span data-stu-id="35ed6-110">WPF Graphics Rendering Overview</span></span>](wpf-graphics-rendering-overview.md)
