---
title: Alpha 混色線條和填色
ms.date: 03/30/2017
helpviewer_keywords:
- lines [Windows Forms], adding transparency
- examples [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with lines
- alpha blending
- lines [Windows Forms], alpha blending
- fills [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with fills
- shapes [Windows Forms], adding transparency
ms.assetid: 5440f48c-3ac9-44c3-b170-c1c110bdbab8
ms.openlocfilehash: f58fa2d105492c6c72d3d6906c3c35f89130fe91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517682"
---
# <a name="alpha-blending-lines-and-fills"></a><span data-ttu-id="20e3e-102">Alpha 混色線條和填色</span><span class="sxs-lookup"><span data-stu-id="20e3e-102">Alpha Blending Lines and Fills</span></span>
<span data-ttu-id="20e3e-103">在[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，色彩是與 8 位元每個 alpha、 紅、 綠和藍 32 位元值。</span><span class="sxs-lookup"><span data-stu-id="20e3e-103">In [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], a color is a 32-bit value with 8 bits each for alpha, red, green, and blue.</span></span> <span data-ttu-id="20e3e-104">Alpha 值表示色彩的透明度，以背景色彩的色彩會混合的範圍。</span><span class="sxs-lookup"><span data-stu-id="20e3e-104">The alpha value indicates the transparency of the color — the extent to which the color is blended with the background color.</span></span> <span data-ttu-id="20e3e-105">從 0 到 255，其中 0 代表完全透明的色彩，到 255 的 alpha 值範圍表示完全不透明的色彩。</span><span class="sxs-lookup"><span data-stu-id="20e3e-105">Alpha values range from 0 through 255, where 0 represents a fully transparent color, and 255 represents a fully opaque color.</span></span>  
  
 <span data-ttu-id="20e3e-106">Alpha 混色是像素 x 像素的混合，其來源和背景的色彩資料。</span><span class="sxs-lookup"><span data-stu-id="20e3e-106">Alpha blending is a pixel-by-pixel blending of source and background color data.</span></span> <span data-ttu-id="20e3e-107">每個指定的來源色彩的三個元件 （紅色、 綠色、 藍色） 會混合使用對應元件的背景色彩，根據下列公式：</span><span class="sxs-lookup"><span data-stu-id="20e3e-107">Each of the three components (red, green, blue) of a given source color is blended with the corresponding component of the background color according to the following formula:</span></span>  
  
 <span data-ttu-id="20e3e-108">displayColor = sourceColor × alpha / 255 + backgroundColor × (255-alpha) / 255</span><span class="sxs-lookup"><span data-stu-id="20e3e-108">displayColor = sourceColor × alpha / 255 + backgroundColor × (255 – alpha) / 255</span></span>  
  
 <span data-ttu-id="20e3e-109">例如，假設來源色彩的紅色元件是 150，而背景色彩的紅色元件為 100。</span><span class="sxs-lookup"><span data-stu-id="20e3e-109">For example, suppose the red component of the source color is 150 and the red component of the background color is 100.</span></span> <span data-ttu-id="20e3e-110">如果 alpha 值是 200，產生色彩的紅色元件的計算方式如下：</span><span class="sxs-lookup"><span data-stu-id="20e3e-110">If the alpha value is 200, the red component of the resultant color is calculated as follows:</span></span>  
  
 <span data-ttu-id="20e3e-111">150 × 200 / 255 + 100 × (255 – 200) / 255 = 139</span><span class="sxs-lookup"><span data-stu-id="20e3e-111">150 × 200 / 255 + 100 × (255 – 200) / 255 = 139</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="20e3e-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="20e3e-112">In This Section</span></span>  
 [<span data-ttu-id="20e3e-113">操作說明：繪製不透明和半透明線條</span><span class="sxs-lookup"><span data-stu-id="20e3e-113">How to: Draw Opaque and Semitransparent Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)  
 <span data-ttu-id="20e3e-114">示範如何繪製 alpha 混色線條。</span><span class="sxs-lookup"><span data-stu-id="20e3e-114">Shows how to draw alpha-blended lines.</span></span>  
  
 [<span data-ttu-id="20e3e-115">操作說明：使用不透明和半透明筆刷繪製</span><span class="sxs-lookup"><span data-stu-id="20e3e-115">How to: Draw with Opaque and Semitransparent Brushes</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-with-opaque-and-semitransparent-brushes.md)  
 <span data-ttu-id="20e3e-116">說明如何 alpha-blend 的筆刷。</span><span class="sxs-lookup"><span data-stu-id="20e3e-116">Explains how to alpha-blend with brushes.</span></span>  
  
 [<span data-ttu-id="20e3e-117">操作說明：使用複合模式控制 Alpha 混色</span><span class="sxs-lookup"><span data-stu-id="20e3e-117">How to: Use Compositing Mode to Control Alpha Blending</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-compositing-mode-to-control-alpha-blending.md)  
 <span data-ttu-id="20e3e-118">描述如何控制 alpha 混色使用<xref:System.Drawing.Drawing2D.CompositingMode>。</span><span class="sxs-lookup"><span data-stu-id="20e3e-118">Describes how to control alpha blending using <xref:System.Drawing.Drawing2D.CompositingMode>.</span></span>  
  
 [<span data-ttu-id="20e3e-119">操作說明：使用色彩矩陣設定影像中的 Alpha 值</span><span class="sxs-lookup"><span data-stu-id="20e3e-119">How to: Use a Color Matrix to Set Alpha Values in Images</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-color-matrix-to-set-alpha-values-in-images.md)  
 <span data-ttu-id="20e3e-120">說明如何使用<xref:System.Drawing.Imaging.ColorMatrix>物件來控制 alpha 混色。</span><span class="sxs-lookup"><span data-stu-id="20e3e-120">Explains how to use a <xref:System.Drawing.Imaging.ColorMatrix> object to control alpha blending.</span></span>
