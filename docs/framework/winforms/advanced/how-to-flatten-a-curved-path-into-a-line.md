---
title: 如何：將曲線路徑簡維為線條
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
ms.openlocfilehash: a3a8467dc5906a88911672316bb0f2ed3607d3a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521199"
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a><span data-ttu-id="9e061-102">如何：將曲線路徑簡維為線條</span><span class="sxs-lookup"><span data-stu-id="9e061-102">How to: Flatten a Curved Path into a Line</span></span>
<span data-ttu-id="9e061-103">A<xref:System.Drawing.Drawing2D.GraphicsPath>物件會儲存一連串的線路與貝茲曲線。</span><span class="sxs-lookup"><span data-stu-id="9e061-103">A <xref:System.Drawing.Drawing2D.GraphicsPath> object stores a sequence of lines and Bézier splines.</span></span> <span data-ttu-id="9e061-104">您可以加入幾種類型的曲線 （省略符號、 弧線、 曲線） 的路徑，但之前儲存的路徑中，將會轉換成貝茲曲線的每個曲線。</span><span class="sxs-lookup"><span data-stu-id="9e061-104">You can add several types of curves (ellipses, arcs, cardinal splines) to a path, but each curve is converted to a Bézier spline before it is stored in the path.</span></span> <span data-ttu-id="9e061-105">簡維路徑包含將在路徑中的每個貝茲曲線轉換成一系列直線。</span><span class="sxs-lookup"><span data-stu-id="9e061-105">Flattening a path consists of converting each Bézier spline in the path to a sequence of straight lines.</span></span> <span data-ttu-id="9e061-106">下圖顯示路徑之前和之後扁平化。</span><span class="sxs-lookup"><span data-stu-id="9e061-106">The following illustration shows a path before and after flattening.</span></span>  
  
 <span data-ttu-id="9e061-107">![直線和曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")</span><span class="sxs-lookup"><span data-stu-id="9e061-107">![Straight Lines and Curves](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")</span></span>  
  
### <a name="to-flatten-a-path"></a><span data-ttu-id="9e061-108">壓平合併路徑</span><span class="sxs-lookup"><span data-stu-id="9e061-108">To Flatten a Path</span></span>  
  
-   <span data-ttu-id="9e061-109">呼叫<xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A>方法<xref:System.Drawing.Drawing2D.GraphicsPath>物件。</span><span class="sxs-lookup"><span data-stu-id="9e061-109">call the <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> method of a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="9e061-110"><xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A>方法會接收指定的原始路徑簡維的路徑之間的最大距離為扁平引數。</span><span class="sxs-lookup"><span data-stu-id="9e061-110">The <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A> method receives a flatness argument that specifies the maximum distance between the flattened path and the original path.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e061-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e061-111">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 [<span data-ttu-id="9e061-112">線條、曲線和形狀</span><span class="sxs-lookup"><span data-stu-id="9e061-112">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="9e061-113">建構和繪製路徑</span><span class="sxs-lookup"><span data-stu-id="9e061-113">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
