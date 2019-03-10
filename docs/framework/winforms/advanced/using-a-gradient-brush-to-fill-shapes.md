---
title: 使用漸層筆刷填滿形狀
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [Windows Forms], gradient brushes
- gradient brushes
- examples [Windows Forms], gradient brushes
ms.assetid: 2c6037b9-05bd-44c0-a22a-19584b722524
ms.openlocfilehash: 5771aaabd283d71f5fa6934f86a1c24a57f38dca
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704384"
---
# <a name="using-a-gradient-brush-to-fill-shapes"></a><span data-ttu-id="807a7-102">使用漸層筆刷填滿形狀</span><span class="sxs-lookup"><span data-stu-id="807a7-102">Using a Gradient Brush to Fill Shapes</span></span>
<span data-ttu-id="807a7-103">您可以使用漸層筆刷填滿圖形，以逐漸變更色彩。</span><span class="sxs-lookup"><span data-stu-id="807a7-103">You can use a gradient brush to fill a shape with a gradually changing color.</span></span> <span data-ttu-id="807a7-104">例如，您可以使用水平漸層來填滿色彩，當您從圖形的左邊緣移至 右邊緣會逐漸變更形狀。</span><span class="sxs-lookup"><span data-stu-id="807a7-104">For example, you can use a horizontal gradient to fill a shape with color that changes gradually as you move from the left edge of the shape to the right edge.</span></span> <span data-ttu-id="807a7-105">假設有一個矩形，為黑色的左邊緣 （以紅色、 綠色和藍色元件 0，0，0） 和右邊緣是 red （由 255，0，0）。</span><span class="sxs-lookup"><span data-stu-id="807a7-105">Imagine a rectangle with a left edge that is black (represented by red, green, and blue components 0, 0, 0) and a right edge that is red (represented by 255, 0, 0).</span></span> <span data-ttu-id="807a7-106">如果矩形是 256 像素寬，給定的像素的紅色元件將會大於其左邊的像素的紅色元件。</span><span class="sxs-lookup"><span data-stu-id="807a7-106">If the rectangle is 256 pixels wide, the red component of a given pixel will be one greater than the red component of the pixel to its left.</span></span> <span data-ttu-id="807a7-107">資料列中最左邊的像素色彩元件 （0，0，0）、 第二個像素具有 （1，0，0），第三個像素的 （2，0，0），並依此類推，直到到達最右邊像素的色彩元件 （255，0，0）。</span><span class="sxs-lookup"><span data-stu-id="807a7-107">The leftmost pixel in a row has color components (0, 0, 0), the second pixel has (1, 0, 0), the third pixel has (2, 0, 0), and so on, until you get to the rightmost pixel, which has color components (255, 0, 0).</span></span> <span data-ttu-id="807a7-108">這些內插補點的色彩值會產生之色彩漸層。</span><span class="sxs-lookup"><span data-stu-id="807a7-108">These interpolated color values make up the color gradient.</span></span>  
  
 <span data-ttu-id="807a7-109">當您移動水平、 垂直，或指定斜線平行線形漸層會變更色彩。</span><span class="sxs-lookup"><span data-stu-id="807a7-109">A linear gradient changes color as you move horizontally, vertically, or parallel to a specified slanted line.</span></span> <span data-ttu-id="807a7-110">當您移動相關的內部和路徑的邊界色彩變更路徑漸層。</span><span class="sxs-lookup"><span data-stu-id="807a7-110">A path gradient changes color as you move about the interior and boundary of a path.</span></span> <span data-ttu-id="807a7-111">您可以自訂路徑漸層來達到各種不同的效果。</span><span class="sxs-lookup"><span data-stu-id="807a7-111">You can customize path gradients to achieve a wide variety of effects.</span></span>  
  
 <span data-ttu-id="807a7-112">下圖顯示以線性漸層筆刷填滿的矩形和橢圓形填入路徑漸層筆刷。</span><span class="sxs-lookup"><span data-stu-id="807a7-112">The following illustration shows a rectangle filled with a linear gradient brush and an ellipse filled with a path gradient brush.</span></span>  
  
 <span data-ttu-id="807a7-113">![漸層停駐](./media/gradient2.png "gradient2")</span><span class="sxs-lookup"><span data-stu-id="807a7-113">![Gradient](./media/gradient2.png "gradient2")</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="807a7-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="807a7-114">In This Section</span></span>  
 [<span data-ttu-id="807a7-115">如何：建立線形漸層</span><span class="sxs-lookup"><span data-stu-id="807a7-115">How to: Create a Linear Gradient</span></span>](how-to-create-a-linear-gradient.md)  
 <span data-ttu-id="807a7-116">示範如何使用下列方法建立線性漸層停駐<xref:System.Drawing.Drawing2D.LinearGradientBrush>類別。</span><span class="sxs-lookup"><span data-stu-id="807a7-116">Shows how to create a linear gradient using the <xref:System.Drawing.Drawing2D.LinearGradientBrush> class.</span></span>  
  
 [<span data-ttu-id="807a7-117">如何：建立路徑漸層</span><span class="sxs-lookup"><span data-stu-id="807a7-117">How to: Create a Path Gradient</span></span>](how-to-create-a-path-gradient.md)  
 <span data-ttu-id="807a7-118">描述如何建立路徑漸層停駐 using<xref:System.Drawing.Drawing2D.PathGradientBrush>類別。</span><span class="sxs-lookup"><span data-stu-id="807a7-118">Describes how to create a path gradient using the <xref:System.Drawing.Drawing2D.PathGradientBrush> class.</span></span>  
  
 [<span data-ttu-id="807a7-119">如何：將 Gamma 修正套用至漸層</span><span class="sxs-lookup"><span data-stu-id="807a7-119">How to: Apply Gamma Correction to a Gradient</span></span>](how-to-apply-gamma-correction-to-a-gradient.md)  
 <span data-ttu-id="807a7-120">說明如何使用漸層筆刷的 gamma 修正。</span><span class="sxs-lookup"><span data-stu-id="807a7-120">Explains how to use gamma correction with a gradient brush.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="807a7-121">參考資料</span><span class="sxs-lookup"><span data-stu-id="807a7-121">Reference</span></span>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 <span data-ttu-id="807a7-122">包含描述此類別並且連結到其所有成員。</span><span class="sxs-lookup"><span data-stu-id="807a7-122">Contains a description of this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Drawing2D.PathGradientBrush?displayProperty=nameWithType>  
 <span data-ttu-id="807a7-123">包含描述此類別並且連結到其所有成員。</span><span class="sxs-lookup"><span data-stu-id="807a7-123">Contains a description of this class and has links to all of its members.</span></span>
