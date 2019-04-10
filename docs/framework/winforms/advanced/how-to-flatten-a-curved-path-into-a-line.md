---
title: HOW TO：將曲線路徑壓平合併為線條
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
ms.openlocfilehash: a151b4244e14d3704fd5fa1c55de92211981232f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215153"
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a><span data-ttu-id="ca34b-102">HOW TO：將曲線路徑壓平合併為線條</span><span class="sxs-lookup"><span data-stu-id="ca34b-102">How to: Flatten a Curved Path into a Line</span></span>
<span data-ttu-id="ca34b-103">A<xref:System.Drawing.Drawing2D.GraphicsPath>物件會儲存一串線和貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="ca34b-103">A <xref:System.Drawing.Drawing2D.GraphicsPath> object stores a sequence of lines and Bézier splines.</span></span> <span data-ttu-id="ca34b-104">您可以將數種類型的曲線 （省略符號，弧線，基線曲線） 加入路徑，但之前它會儲存在路徑中的每條曲線轉換成貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="ca34b-104">You can add several types of curves (ellipses, arcs, cardinal splines) to a path, but each curve is converted to a Bézier spline before it is stored in the path.</span></span> <span data-ttu-id="ca34b-105">壓平合併的路徑將每個路徑中的貝茲曲線轉換成一連串的直線，線條所組成。</span><span class="sxs-lookup"><span data-stu-id="ca34b-105">Flattening a path consists of converting each Bézier spline in the path to a sequence of straight lines.</span></span> <span data-ttu-id="ca34b-106">壓平合併的前後，如下圖所顯示的路徑。</span><span class="sxs-lookup"><span data-stu-id="ca34b-106">The following illustration shows a path before and after flattening.</span></span>  
  
 <span data-ttu-id="ca34b-107">![直線和曲線](./media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")</span><span class="sxs-lookup"><span data-stu-id="ca34b-107">![Straight Lines and Curves](./media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")</span></span>  
  
### <a name="to-flatten-a-path"></a><span data-ttu-id="ca34b-108">若要壓平合併的路徑</span><span class="sxs-lookup"><span data-stu-id="ca34b-108">To Flatten a Path</span></span>  
  
-   <span data-ttu-id="ca34b-109">呼叫<xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A>方法的<xref:System.Drawing.Drawing2D.GraphicsPath>物件。</span><span class="sxs-lookup"><span data-stu-id="ca34b-109">call the <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> method of a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="ca34b-110"><xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A>方法會接收指定的扁平化的路徑與原始路徑之間的最大距離的扁平引數。</span><span class="sxs-lookup"><span data-stu-id="ca34b-110">The <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> method receives a flatness argument that specifies the maximum distance between the flattened path and the original path.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca34b-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca34b-111">See also</span></span>

- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- [<span data-ttu-id="ca34b-112">線條、曲線和形狀</span><span class="sxs-lookup"><span data-stu-id="ca34b-112">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="ca34b-113">建構和繪製路徑</span><span class="sxs-lookup"><span data-stu-id="ca34b-113">Constructing and Drawing Paths</span></span>](constructing-and-drawing-paths.md)
