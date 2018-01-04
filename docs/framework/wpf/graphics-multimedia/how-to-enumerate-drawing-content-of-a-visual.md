---
title: "如何：列舉 Visual 的繪圖內容"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5c97926286076149a6eedf34bb70bbc76b2e0d8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a><span data-ttu-id="f7b62-102">如何：列舉 Visual 的繪圖內容</span><span class="sxs-lookup"><span data-stu-id="f7b62-102">How to: Enumerate Drawing Content of a Visual</span></span>
<span data-ttu-id="f7b62-103"><xref:System.Windows.Media.Drawing>物件提供列舉的內容物件模型<xref:System.Windows.Media.Visual>。</span><span class="sxs-lookup"><span data-stu-id="f7b62-103">The <xref:System.Windows.Media.Drawing> object provide an object model for enumerating the contents of a <xref:System.Windows.Media.Visual>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7b62-104">範例</span><span class="sxs-lookup"><span data-stu-id="f7b62-104">Example</span></span>  
 <span data-ttu-id="f7b62-105">下列範例會使用<xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>方法來擷取<xref:System.Windows.Media.DrawingGroup>值<xref:System.Windows.Media.Visual>和列舉它。</span><span class="sxs-lookup"><span data-stu-id="f7b62-105">The following example uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method to retrieve the <xref:System.Windows.Media.DrawingGroup> value of a <xref:System.Windows.Media.Visual> and enumerate it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7b62-106">當您要列舉的視覺效果的內容時，您會擷取<xref:System.Windows.Media.Drawing>物件和不基礎資料的表示法呈現為向量圖形指示清單。</span><span class="sxs-lookup"><span data-stu-id="f7b62-106">When you are enumerating the contents of the visual, you are retrieving <xref:System.Windows.Media.Drawing> objects, and not the underlying representation of the render data as a vector graphics instruction list.</span></span> <span data-ttu-id="f7b62-107">如需詳細資訊，請參閱 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f7b62-107">For more information, see [WPF Graphics Rendering Overview](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a><span data-ttu-id="f7b62-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="f7b62-108">See Also</span></span>  
 <xref:System.Windows.Media.Drawing>  
 <xref:System.Windows.Media.DrawingGroup>  
 <xref:System.Windows.Media.VisualTreeHelper>  
 [<span data-ttu-id="f7b62-109">繪圖物件概觀</span><span class="sxs-lookup"><span data-stu-id="f7b62-109">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="f7b62-110">WPF 圖形轉譯概觀</span><span class="sxs-lookup"><span data-stu-id="f7b62-110">WPF Graphics Rendering Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
