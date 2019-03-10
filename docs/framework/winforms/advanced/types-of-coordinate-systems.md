---
title: 座標系統類型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], page
- unit of measure
- world coordinate system
- page coordinate system
- page transformation
- device coordinate system
- world transformation
- coordinate systems
- transformations [Windows Forms], world
ms.assetid: c61ff50a-eb1d-4e6c-83cd-f7e9764cfa9f
ms.openlocfilehash: 42e8b5626cf30010f154e7c978708042c4e3369a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715850"
---
# <a name="types-of-coordinate-systems"></a><span data-ttu-id="9bd7e-102">座標系統類型</span><span class="sxs-lookup"><span data-stu-id="9bd7e-102">Types of Coordinate Systems</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="9bd7e-103">使用三個座標空間： 世界、 頁面和裝置。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-103">uses three coordinate spaces: world, page, and device.</span></span> <span data-ttu-id="9bd7e-104">全局座標是用來建立模型為特定圖形範圍的座標，您將傳遞給方法，在.NET Framework 中的座標。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-104">World coordinates are the coordinates used to model a particular graphic world and are the coordinates you pass to methods in the .NET Framework.</span></span> <span data-ttu-id="9bd7e-105">頁面座標是指繪圖介面，例如表單或控制項所使用的座標系統。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-105">Page coordinates refer to the coordinate system used by a drawing surface, such as a form or control.</span></span> <span data-ttu-id="9bd7e-106">裝置座標是實體裝置上，繪製到螢幕或紙張等所使用的座標。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-106">Device coordinates are the coordinates used by the physical device being drawn on, such as a screen or sheet of paper.</span></span> <span data-ttu-id="9bd7e-107">當您進行呼叫`myGraphics.DrawLine(myPen, 0, 0, 160, 80)`，您將傳遞至的點<xref:System.Drawing.Graphics.DrawLine%2A>方法 —`(0, 0)`和`(160, 80)`— 全局座標空間中。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-107">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, the points that you pass to the <xref:System.Drawing.Graphics.DrawLine%2A> method—`(0, 0)` and `(160, 80)`—are in the world coordinate space.</span></span> <span data-ttu-id="9bd7e-108">之前[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]可以在螢幕上繪製線條、 座標通過一連串的轉換。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-108">Before [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] can draw the line on the screen, the coordinates pass through a sequence of transformations.</span></span> <span data-ttu-id="9bd7e-109">一個轉換，稱為 「 世界 」 轉換中，將全局座標轉換成頁面座標，以及另一個轉換，稱為 「 頁面 」 轉換中，將轉換成頁面座標裝置座標。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-109">One transformation, called the world transformation, converts world coordinates to page coordinates, and another transformation, called the page transformation, converts page coordinates to device coordinates.</span></span>  
  
## <a name="transforms-and-coordinate-systems"></a><span data-ttu-id="9bd7e-110">轉換和座標系統</span><span class="sxs-lookup"><span data-stu-id="9bd7e-110">Transforms and Coordinate Systems</span></span>  
 <span data-ttu-id="9bd7e-111">假設您想要使用的工作區，而不是左上角的主體中原點座標系統。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-111">Suppose you want to work with a coordinate system that has its origin in the body of the client area rather than the upper-left corner.</span></span> <span data-ttu-id="9bd7e-112">例如，假設您想要從工作區左邊緣的 100 像素且從工作區頂端的 50 個像素的原點。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-112">Say, for example, that you want the origin to be 100 pixels from the left edge of the client area and 50 pixels from the top of the client area.</span></span> <span data-ttu-id="9bd7e-113">下圖顯示這類的座標系統。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-113">The following illustration shows such a coordinate system.</span></span>  
  
 <span data-ttu-id="9bd7e-114">![座標系統](./media/aboutgdip05-art01.gif "AboutGdip05_art01")</span><span class="sxs-lookup"><span data-stu-id="9bd7e-114">![Coordinate System](./media/aboutgdip05-art01.gif "AboutGdip05_art01")</span></span>  
  
 <span data-ttu-id="9bd7e-115">當您建立呼叫`myGraphics.DrawLine(myPen, 0, 0, 160, 80)`，取得在下圖中顯示的列。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-115">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, you get the line shown in the following illustration.</span></span>  
  
 <span data-ttu-id="9bd7e-116">![Coordinate System](./media/aboutgdip05-art02.gif "AboutGdip05_art02")</span><span class="sxs-lookup"><span data-stu-id="9bd7e-116">![Coordinate System](./media/aboutgdip05-art02.gif "AboutGdip05_art02")</span></span>  
  
 <span data-ttu-id="9bd7e-117">您的企業中的三個座標空間的端點座標如下所示：</span><span class="sxs-lookup"><span data-stu-id="9bd7e-117">The coordinates of the endpoints of your line in the three coordinate spaces are as follows:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9bd7e-118">世界</span><span class="sxs-lookup"><span data-stu-id="9bd7e-118">World</span></span>|<span data-ttu-id="9bd7e-119">（0，0） 到 160 (80）</span><span class="sxs-lookup"><span data-stu-id="9bd7e-119">(0, 0) to (160, 80)</span></span>|  
|<span data-ttu-id="9bd7e-120">頁面</span><span class="sxs-lookup"><span data-stu-id="9bd7e-120">Page</span></span>|<span data-ttu-id="9bd7e-121">（100，50） 到 （260、 130）</span><span class="sxs-lookup"><span data-stu-id="9bd7e-121">(100, 50) to (260, 130)</span></span>|  
|<span data-ttu-id="9bd7e-122">裝置</span><span class="sxs-lookup"><span data-stu-id="9bd7e-122">Device</span></span>|<span data-ttu-id="9bd7e-123">（100，50） 到 （260、 130）</span><span class="sxs-lookup"><span data-stu-id="9bd7e-123">(100, 50) to (260, 130)</span></span>|  
  
 <span data-ttu-id="9bd7e-124">請注意頁面座標空間的原點，左上角的 用戶端的區域。這一律會是大小寫。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-124">Note that the page coordinate space has its origin at the upper-left corner of the client area; this will always be the case.</span></span> <span data-ttu-id="9bd7e-125">也請注意，測量單位為像素，因為裝置座標畫面座標相同。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-125">Also note that because the unit of measure is the pixel, the device coordinates are the same as the page coordinates.</span></span> <span data-ttu-id="9bd7e-126">如果您將為測量單位為像素為單位 （例如英吋） 以外的項目時，裝置座標會不同於畫面座標。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-126">If you set the unit of measure to something other than pixels (for example, inches), then the device coordinates will be different from the page coordinates.</span></span>  
  
 <span data-ttu-id="9bd7e-127">全局轉換，可將全局座標對應成頁面座標，會保留在<xref:System.Drawing.Graphics.Transform%2A>屬性<xref:System.Drawing.Graphics>類別。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-127">The world transformation, which maps world coordinates to page coordinates, is held in the <xref:System.Drawing.Graphics.Transform%2A> property of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="9bd7e-128">在上述範例中，全局轉換是在 x 方向轉譯 100 單位並在 y 方向的 50 個單位。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-128">In the preceding example, the world transformation is a translation 100 units in the x direction and 50 units in the y direction.</span></span> <span data-ttu-id="9bd7e-129">下列範例會設定的自然變換<xref:System.Drawing.Graphics>物件，並會使用該<xref:System.Drawing.Graphics>物件来繪製在上圖中顯示的列：</span><span class="sxs-lookup"><span data-stu-id="9bd7e-129">The following example sets the world transformation of a <xref:System.Drawing.Graphics> object and then uses that <xref:System.Drawing.Graphics> object to draw the line shown in the preceding figure:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 <span data-ttu-id="9bd7e-130">「 頁面 」 轉換會將頁面座標對應至裝置座標。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-130">The page transformation maps page coordinates to device coordinates.</span></span> <span data-ttu-id="9bd7e-131"><xref:System.Drawing.Graphics>類別會提供<xref:System.Drawing.Graphics.PageUnit%2A>和<xref:System.Drawing.Graphics.PageScale%2A>操作 「 頁面 」 轉換的屬性。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-131">The <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.PageUnit%2A> and <xref:System.Drawing.Graphics.PageScale%2A> properties for manipulating the page transformation.</span></span> <span data-ttu-id="9bd7e-132"><xref:System.Drawing.Graphics>類別也會提供兩個唯讀屬性，<xref:System.Drawing.Graphics.DpiX%2A>和<xref:System.Drawing.Graphics.DpiY%2A>，檢查水平和垂直 dpi 為單位的顯示裝置。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-132">The <xref:System.Drawing.Graphics> class also provides two read-only properties, <xref:System.Drawing.Graphics.DpiX%2A> and <xref:System.Drawing.Graphics.DpiY%2A>, for examining the horizontal and vertical dots per inch of the display device.</span></span>  
  
 <span data-ttu-id="9bd7e-133">您可以使用<xref:System.Drawing.Graphics.PageUnit%2A>屬性<xref:System.Drawing.Graphics>類別，以指定的像素以外的量值單位。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-133">You can use the <xref:System.Drawing.Graphics.PageUnit%2A> property of the <xref:System.Drawing.Graphics> class to specify a unit of measure other than the pixel.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9bd7e-134">您無法設定<xref:System.Drawing.Graphics.PageUnit%2A>屬性設<xref:System.Drawing.GraphicsUnit.World>，因為這不是實體單位，並會導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-134">You cannot set the <xref:System.Drawing.Graphics.PageUnit%2A> property to <xref:System.Drawing.GraphicsUnit.World>, as this is not a physical unit and will cause an exception.</span></span>  
  
 <span data-ttu-id="9bd7e-135">下列範例會繪製線條，以從 （0，0） 到 （2，1），其中 （2，1） 的點是 2 英吋為單位向右再向下 1 英吋從點 （0，0）：</span><span class="sxs-lookup"><span data-stu-id="9bd7e-135">The following example draws a line from (0, 0) to (2, 1), where the point (2, 1) is 2 inches to the right and 1 inch down from the point (0, 0):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  <span data-ttu-id="9bd7e-136">如果您未指定畫筆寬度，當您建構您的畫筆時，上述範例會繪製為一英吋寬的線條。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-136">If you don't specify a pen width when you construct your pen, the preceding example will draw a line that is one inch wide.</span></span> <span data-ttu-id="9bd7e-137">您可以指定的第二個引數中的畫筆寬度<xref:System.Drawing.Pen>建構函式：</span><span class="sxs-lookup"><span data-stu-id="9bd7e-137">You can specify the pen width in the second argument to the <xref:System.Drawing.Pen> constructor:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 <span data-ttu-id="9bd7e-138">如果我們假設在顯示裝置，有 96 dpi 的水平方向和 96 dpi 為單位，在垂直方向，在上述範例中線條的端點會有下列的座標，三個座標空間中：</span><span class="sxs-lookup"><span data-stu-id="9bd7e-138">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9bd7e-139">世界</span><span class="sxs-lookup"><span data-stu-id="9bd7e-139">World</span></span>|<span data-ttu-id="9bd7e-140">（0，0） 到 （2，1）</span><span class="sxs-lookup"><span data-stu-id="9bd7e-140">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="9bd7e-141">頁面</span><span class="sxs-lookup"><span data-stu-id="9bd7e-141">Page</span></span>|<span data-ttu-id="9bd7e-142">（0，0） 到 （2，1）</span><span class="sxs-lookup"><span data-stu-id="9bd7e-142">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="9bd7e-143">裝置</span><span class="sxs-lookup"><span data-stu-id="9bd7e-143">Device</span></span>|<span data-ttu-id="9bd7e-144">(0，0，到 （192，96）</span><span class="sxs-lookup"><span data-stu-id="9bd7e-144">(0, 0, to (192, 96)</span></span>|  
  
 <span data-ttu-id="9bd7e-145">請注意，因為全局座標空間的原點位於左上角的 工作區時，畫面座標的全局座標相同。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-145">Note that because the origin of the world coordinate space is at the upper-left corner of the client area, the page coordinates are the same as the world coordinates.</span></span>  
  
 <span data-ttu-id="9bd7e-146">您可以結合的全局和頁面轉換，來達到各種不同的效果。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-146">You can combine the world and page transformations to achieve a variety of effects.</span></span> <span data-ttu-id="9bd7e-147">比方說，假設您想要做為測量單位為英吋為單位，而您想要為 2 英吋為單位從左邊緣的工作區和 1/2 英吋，從用戶端區域的頂端座標系統的原點。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-147">For example, suppose you want to use inches as the unit of measure and you want the origin of your coordinate system to be 2 inches from the left edge of the client area and 1/2 inch from the top of the client area.</span></span> <span data-ttu-id="9bd7e-148">下列範例會設定全局和頁面轉換<xref:System.Drawing.Graphics>物件，並再分別繪製一條從 （0，0） 到 （2，1）：</span><span class="sxs-lookup"><span data-stu-id="9bd7e-148">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object and then draws a line from (0, 0) to (2, 1):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 <span data-ttu-id="9bd7e-149">下圖顯示的行和座標系統。</span><span class="sxs-lookup"><span data-stu-id="9bd7e-149">The following illustration shows the line and coordinate system.</span></span>  
  
 <span data-ttu-id="9bd7e-150">![Coordinate System](./media/aboutgdip05-art03.gif "AboutGdip05_art03")</span><span class="sxs-lookup"><span data-stu-id="9bd7e-150">![Coordinate System](./media/aboutgdip05-art03.gif "AboutGdip05_art03")</span></span>  
  
 <span data-ttu-id="9bd7e-151">如果我們假設在顯示裝置，有 96 dpi 的水平方向和 96 dpi 為單位，在垂直方向，在上述範例中線條的端點會有下列的座標，三個座標空間中：</span><span class="sxs-lookup"><span data-stu-id="9bd7e-151">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9bd7e-152">世界</span><span class="sxs-lookup"><span data-stu-id="9bd7e-152">World</span></span>|<span data-ttu-id="9bd7e-153">（0，0） 到 （2，1）</span><span class="sxs-lookup"><span data-stu-id="9bd7e-153">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="9bd7e-154">頁面</span><span class="sxs-lookup"><span data-stu-id="9bd7e-154">Page</span></span>|<span data-ttu-id="9bd7e-155">（2，0.5） 到 （4，1.5）</span><span class="sxs-lookup"><span data-stu-id="9bd7e-155">(2, 0.5) to (4, 1.5)</span></span>|  
|<span data-ttu-id="9bd7e-156">裝置</span><span class="sxs-lookup"><span data-stu-id="9bd7e-156">Device</span></span>|<span data-ttu-id="9bd7e-157">（192，48） 到 （384，第 144）</span><span class="sxs-lookup"><span data-stu-id="9bd7e-157">(192, 48) to (384, 144)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9bd7e-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bd7e-158">See also</span></span>
- [<span data-ttu-id="9bd7e-159">座標系統和轉換</span><span class="sxs-lookup"><span data-stu-id="9bd7e-159">Coordinate Systems and Transformations</span></span>](coordinate-systems-and-transformations.md)
- [<span data-ttu-id="9bd7e-160">以矩陣來表示轉換</span><span class="sxs-lookup"><span data-stu-id="9bd7e-160">Matrix Representation of Transformations</span></span>](matrix-representation-of-transformations.md)
