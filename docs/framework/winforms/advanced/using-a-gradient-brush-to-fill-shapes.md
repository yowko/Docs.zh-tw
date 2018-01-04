---
title: "使用漸層筆刷填滿形狀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- brushes [Windows Forms], gradient brushes
- gradient brushes
- examples [Windows Forms], gradient brushes
ms.assetid: 2c6037b9-05bd-44c0-a22a-19584b722524
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a84a68f9082d00559938c2710b6574690fa6ab4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="using-a-gradient-brush-to-fill-shapes"></a><span data-ttu-id="104d9-102">使用漸層筆刷填滿形狀</span><span class="sxs-lookup"><span data-stu-id="104d9-102">Using a Gradient Brush to Fill Shapes</span></span>
<span data-ttu-id="104d9-103">您可以使用漸層筆刷填滿圖形的逐漸變更的色彩。</span><span class="sxs-lookup"><span data-stu-id="104d9-103">You can use a gradient brush to fill a shape with a gradually changing color.</span></span> <span data-ttu-id="104d9-104">例如，您可以使用水平漸層來填滿色彩逐漸變更在左邊緣圖案移右邊緣的形狀。</span><span class="sxs-lookup"><span data-stu-id="104d9-104">For example, you can use a horizontal gradient to fill a shape with color that changes gradually as you move from the left edge of the shape to the right edge.</span></span> <span data-ttu-id="104d9-105">假設有一個矩形，為黑色的左邊緣 （代表紅色、 綠色和藍色元件 0，0，0） 和右邊緣是紅色 （由 255，0，0）。</span><span class="sxs-lookup"><span data-stu-id="104d9-105">Imagine a rectangle with a left edge that is black (represented by red, green, and blue components 0, 0, 0) and a right edge that is red (represented by 255, 0, 0).</span></span> <span data-ttu-id="104d9-106">如果矩形是 256 像素寬，給定的像素的紅色元件將會大於其左側的像素的紅色元件。</span><span class="sxs-lookup"><span data-stu-id="104d9-106">If the rectangle is 256 pixels wide, the red component of a given pixel will be one greater than the red component of the pixel to its left.</span></span> <span data-ttu-id="104d9-107">資料列中最左邊的像素會有色彩元件 （0，0，0）、 第二個像素 （1，0，0），第三個像素的 （2，0，0），並依此類推，直到到達最右邊像素的色彩元件 （255，0，0）。</span><span class="sxs-lookup"><span data-stu-id="104d9-107">The leftmost pixel in a row has color components (0, 0, 0), the second pixel has (1, 0, 0), the third pixel has (2, 0, 0), and so on, until you get to the rightmost pixel, which has color components (255, 0, 0).</span></span> <span data-ttu-id="104d9-108">這些插補的色彩值便會產生之色彩漸層。</span><span class="sxs-lookup"><span data-stu-id="104d9-108">These interpolated color values make up the color gradient.</span></span>  
  
 <span data-ttu-id="104d9-109">當您移動水平、 垂直，或指定斜線平行色彩變更線形漸層。</span><span class="sxs-lookup"><span data-stu-id="104d9-109">A linear gradient changes color as you move horizontally, vertically, or parallel to a specified slanted line.</span></span> <span data-ttu-id="104d9-110">路徑漸層變更色彩，當您移動需內部和路徑的界限。</span><span class="sxs-lookup"><span data-stu-id="104d9-110">A path gradient changes color as you move about the interior and boundary of a path.</span></span> <span data-ttu-id="104d9-111">您可以自訂路徑漸層來達到各種不同的效果。</span><span class="sxs-lookup"><span data-stu-id="104d9-111">You can customize path gradients to achieve a wide variety of effects.</span></span>  
  
 <span data-ttu-id="104d9-112">下圖顯示以線性漸層筆刷填滿的矩形和橢圓形填入路徑漸層筆刷。</span><span class="sxs-lookup"><span data-stu-id="104d9-112">The following illustration shows a rectangle filled with a linear gradient brush and an ellipse filled with a path gradient brush.</span></span>  
  
 <span data-ttu-id="104d9-113">![漸層停駐](../../../../docs/framework/winforms/advanced/media/gradient2.png "gradient2")</span><span class="sxs-lookup"><span data-stu-id="104d9-113">![Gradient](../../../../docs/framework/winforms/advanced/media/gradient2.png "gradient2")</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="104d9-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="104d9-114">In This Section</span></span>  
 [<span data-ttu-id="104d9-115">操作說明：建立線性漸層</span><span class="sxs-lookup"><span data-stu-id="104d9-115">How to: Create a Linear Gradient</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-linear-gradient.md)  
 <span data-ttu-id="104d9-116">示範如何建立線形漸層停駐 using<xref:System.Drawing.Drawing2D.LinearGradientBrush>類別。</span><span class="sxs-lookup"><span data-stu-id="104d9-116">Shows how to create a linear gradient using the <xref:System.Drawing.Drawing2D.LinearGradientBrush> class.</span></span>  
  
 [<span data-ttu-id="104d9-117">操作說明：建立路徑漸層</span><span class="sxs-lookup"><span data-stu-id="104d9-117">How to: Create a Path Gradient</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-path-gradient.md)  
 <span data-ttu-id="104d9-118">描述如何建立路徑漸層停駐 using<xref:System.Drawing.Drawing2D.PathGradientBrush>類別。</span><span class="sxs-lookup"><span data-stu-id="104d9-118">Describes how to create a path gradient using the <xref:System.Drawing.Drawing2D.PathGradientBrush> class.</span></span>  
  
 [<span data-ttu-id="104d9-119">操作說明：將 Gamma 修正套用至漸層</span><span class="sxs-lookup"><span data-stu-id="104d9-119">How to: Apply Gamma Correction to a Gradient</span></span>](../../../../docs/framework/winforms/advanced/how-to-apply-gamma-correction-to-a-gradient.md)  
 <span data-ttu-id="104d9-120">說明如何使用漸層筆刷的 gamma 修正。</span><span class="sxs-lookup"><span data-stu-id="104d9-120">Explains how to use gamma correction with a gradient brush.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="104d9-121">參考資料</span><span class="sxs-lookup"><span data-stu-id="104d9-121">Reference</span></span>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 <span data-ttu-id="104d9-122">包含這個類別的描述，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="104d9-122">Contains a description of this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Drawing2D.PathGradientBrush?displayProperty=nameWithType>  
 <span data-ttu-id="104d9-123">包含這個類別的描述，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="104d9-123">Contains a description of this class and has links to all of its members.</span></span>
