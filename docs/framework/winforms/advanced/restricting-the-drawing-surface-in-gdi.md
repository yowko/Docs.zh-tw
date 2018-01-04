---
title: "限制 GDI+ 中的繪圖介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, clipping
- clipping [Windows Forms], using GDI+
- GDI+, restricting drawing surface
ms.assetid: 8b5f71d9-d2f0-4540-9c41-740f90fd4c26
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b7834c95959972e7264e1caa2cfc21b190341b21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="restricting-the-drawing-surface-in-gdi"></a><span data-ttu-id="68adc-102">限制 GDI+ 中的繪圖介面</span><span class="sxs-lookup"><span data-stu-id="68adc-102">Restricting the Drawing Surface in GDI+</span></span>
<span data-ttu-id="68adc-103">裁剪包括限制到特定矩形或區域的繪圖。</span><span class="sxs-lookup"><span data-stu-id="68adc-103">Clipping involves restricting drawing to a certain rectangle or region.</span></span> <span data-ttu-id="68adc-104">下圖顯示字串"Hello"裁剪為心形的區域。</span><span class="sxs-lookup"><span data-stu-id="68adc-104">The following illustration shows the string "Hello" clipped to a heart-shaped region.</span></span>  
  
 <span data-ttu-id="68adc-105">![受限制的繪圖介面](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art30.gif "AboutGdip02_Art30")</span><span class="sxs-lookup"><span data-stu-id="68adc-105">![Restricted Drawing Surface](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art30.gif "AboutGdip02_Art30")</span></span>  
  
## <a name="clipping-with-regions"></a><span data-ttu-id="68adc-106">裁剪區域</span><span class="sxs-lookup"><span data-stu-id="68adc-106">Clipping with Regions</span></span>  
 <span data-ttu-id="68adc-107">區域可用於建構從路徑，以及路徑可以包含外框的字串，因此您可以使用裁剪外框的文字。</span><span class="sxs-lookup"><span data-stu-id="68adc-107">Regions can be constructed from paths, and paths can contain the outlines of strings, so you can use outlined text for clipping.</span></span> <span data-ttu-id="68adc-108">下圖顯示的文字字串的內部同心橢圓形的一組。</span><span class="sxs-lookup"><span data-stu-id="68adc-108">The following illustration shows a set of concentric ellipses clipped to the interior of a string of text.</span></span>  
  
 <span data-ttu-id="68adc-109">![受限制的繪圖介面](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art31.gif "AboutGdip02_Art31")</span><span class="sxs-lookup"><span data-stu-id="68adc-109">![Restricted Drawing Surface](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art31.gif "AboutGdip02_Art31")</span></span>  
  
 <span data-ttu-id="68adc-110">若要繪製的裁剪，建立<xref:System.Drawing.Graphics>物件、 設定其<xref:System.Drawing.Graphics.Clip%2A>屬性，然後呼叫的繪圖的方法相同<xref:System.Drawing.Graphics>物件：</span><span class="sxs-lookup"><span data-stu-id="68adc-110">To draw with clipping, create a <xref:System.Drawing.Graphics> object, set its <xref:System.Drawing.Graphics.Clip%2A> property, and then call the drawing methods of that same <xref:System.Drawing.Graphics> object:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#91](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#91)]
 [!code-vb[LinesCurvesAndShapes#91](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#91)]  
  
## <a name="see-also"></a><span data-ttu-id="68adc-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="68adc-111">See Also</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Region?displayProperty=nameWithType>  
 [<span data-ttu-id="68adc-112">線條、曲線和形狀</span><span class="sxs-lookup"><span data-stu-id="68adc-112">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="68adc-113">使用區域</span><span class="sxs-lookup"><span data-stu-id="68adc-113">Using Regions</span></span>](../../../../docs/framework/winforms/advanced/using-regions.md)
