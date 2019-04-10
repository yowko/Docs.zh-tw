---
title: HOW TO：從直線、曲線和形狀建立圖形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- figures [Windows Forms], creating from shapes
- figures [Windows Forms], creating from lines
ms.assetid: 82fd56c7-b443-4765-9b7c-62ce030656ec
ms.openlocfilehash: eeaf478375e08734b20d83b6f3c8030732495013
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224906"
---
# <a name="how-to-create-figures-from-lines-curves-and-shapes"></a><span data-ttu-id="ff388-102">HOW TO：從直線、曲線和形狀建立圖形</span><span class="sxs-lookup"><span data-stu-id="ff388-102">How to: Create Figures from Lines, Curves, and Shapes</span></span>
<span data-ttu-id="ff388-103">若要建立圖表，建構<xref:System.Drawing.Drawing2D.GraphicsPath>，然後呼叫方法，例如<xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>和<xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>，以新增至路徑的基本項目。</span><span class="sxs-lookup"><span data-stu-id="ff388-103">To create a figure, construct a <xref:System.Drawing.Drawing2D.GraphicsPath>, and then call methods, such as <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>, to add primitives to the path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff388-104">範例</span><span class="sxs-lookup"><span data-stu-id="ff388-104">Example</span></span>  
 <span data-ttu-id="ff388-105">下列程式碼範例會建立含有圖形的路徑：</span><span class="sxs-lookup"><span data-stu-id="ff388-105">The following code examples create paths that have figures:</span></span>  
  
-   <span data-ttu-id="ff388-106">第一個範例會建立包含單一圖形的路徑。</span><span class="sxs-lookup"><span data-stu-id="ff388-106">The first example creates a path that has a single figure.</span></span> <span data-ttu-id="ff388-107">此圖是由單一弧形所組成。弧線有的掃掠角度-180 度，也就是預設座標系統中的 逆時鐘方向。</span><span class="sxs-lookup"><span data-stu-id="ff388-107">The figure consists of a single arc. The arc has a sweep angle of –180 degrees, which is counterclockwise in the default coordinate system.</span></span>  
  
-   <span data-ttu-id="ff388-108">第二個範例會建立具有兩個圖形的路徑。</span><span class="sxs-lookup"><span data-stu-id="ff388-108">The second example creates a path that has two figures.</span></span> <span data-ttu-id="ff388-109">第一個圖形是後面接著行弧形。</span><span class="sxs-lookup"><span data-stu-id="ff388-109">The first figure is an arc followed by a line.</span></span> <span data-ttu-id="ff388-110">第二張圖是後面接著曲線，後面接著行。</span><span class="sxs-lookup"><span data-stu-id="ff388-110">The second figure is a line followed by a curve followed by a line.</span></span> <span data-ttu-id="ff388-111">第一個圖形會處於開啟狀態，而且第二張圖會關閉。</span><span class="sxs-lookup"><span data-stu-id="ff388-111">The first figure is left open, and the second figure is closed.</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#21)]  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#22)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ff388-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ff388-112">Compiling the Code</span></span>  
 <span data-ttu-id="ff388-113">先前的範例專為搭配 Windows Form 使用，而且它們需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="ff388-113">The previous examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff388-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff388-114">See also</span></span>

- <xref:System.Drawing.Drawing2D.GraphicsPath>
- [<span data-ttu-id="ff388-115">建構和繪製路徑</span><span class="sxs-lookup"><span data-stu-id="ff388-115">Constructing and Drawing Paths</span></span>](constructing-and-drawing-paths.md)
- [<span data-ttu-id="ff388-116">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="ff388-116">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
