---
title: 限制 GDI+ 中的繪圖介面
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, clipping
- clipping [Windows Forms], using GDI+
- GDI+, restricting drawing surface
ms.assetid: 8b5f71d9-d2f0-4540-9c41-740f90fd4c26
ms.openlocfilehash: 3784c833098a5585c5cdc38014d5a9542daf39f2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583386"
---
# <a name="restricting-the-drawing-surface-in-gdi"></a><span data-ttu-id="c3449-102">限制 GDI+ 中的繪圖介面</span><span class="sxs-lookup"><span data-stu-id="c3449-102">Restricting the Drawing Surface in GDI+</span></span>
<span data-ttu-id="c3449-103">裁剪是指限制為特定的矩形或區域的繪製。</span><span class="sxs-lookup"><span data-stu-id="c3449-103">Clipping involves restricting drawing to a certain rectangle or region.</span></span> <span data-ttu-id="c3449-104">下圖顯示的字串"Hello"裁剪到心形區域。</span><span class="sxs-lookup"><span data-stu-id="c3449-104">The following illustration shows the string "Hello" clipped to a heart-shaped region.</span></span>  
  
 <span data-ttu-id="c3449-105">![受限制的繪圖介面](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art30.gif "AboutGdip02_Art30")</span><span class="sxs-lookup"><span data-stu-id="c3449-105">![Restricted Drawing Surface](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art30.gif "AboutGdip02_Art30")</span></span>  
  
## <a name="clipping-with-regions"></a><span data-ttu-id="c3449-106">使用區域的裁剪</span><span class="sxs-lookup"><span data-stu-id="c3449-106">Clipping with Regions</span></span>  
 <span data-ttu-id="c3449-107">區域可以建構從路徑，以及路徑可以包含字串的外框輪廓，因此您可以使用裁剪外框的文字。</span><span class="sxs-lookup"><span data-stu-id="c3449-107">Regions can be constructed from paths, and paths can contain the outlines of strings, so you can use outlined text for clipping.</span></span> <span data-ttu-id="c3449-108">下圖顯示一份同心橢圓形內部的文字字串。</span><span class="sxs-lookup"><span data-stu-id="c3449-108">The following illustration shows a set of concentric ellipses clipped to the interior of a string of text.</span></span>  
  
 <span data-ttu-id="c3449-109">![受限制的繪圖介面](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art31.gif "AboutGdip02_Art31")</span><span class="sxs-lookup"><span data-stu-id="c3449-109">![Restricted Drawing Surface](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art31.gif "AboutGdip02_Art31")</span></span>  
  
 <span data-ttu-id="c3449-110">若要繪製的裁剪，建立<xref:System.Drawing.Graphics>物件，將其<xref:System.Drawing.Graphics.Clip%2A>屬性，然後呼叫繪製方法的相同<xref:System.Drawing.Graphics>物件：</span><span class="sxs-lookup"><span data-stu-id="c3449-110">To draw with clipping, create a <xref:System.Drawing.Graphics> object, set its <xref:System.Drawing.Graphics.Clip%2A> property, and then call the drawing methods of that same <xref:System.Drawing.Graphics> object:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#91](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#91)]
 [!code-vb[LinesCurvesAndShapes#91](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#91)]  
  
## <a name="see-also"></a><span data-ttu-id="c3449-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3449-111">See also</span></span>
- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Region?displayProperty=nameWithType>
- [<span data-ttu-id="c3449-112">線條、曲線和形狀</span><span class="sxs-lookup"><span data-stu-id="c3449-112">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)
- [<span data-ttu-id="c3449-113">使用區域</span><span class="sxs-lookup"><span data-stu-id="c3449-113">Using Regions</span></span>](../../../../docs/framework/winforms/advanced/using-regions.md)
