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
ms.openlocfilehash: 23d9374f1f46c4480079eb4ad5269a197a13a5bf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963883"
---
# <a name="types-of-coordinate-systems"></a><span data-ttu-id="71b01-102">座標系統類型</span><span class="sxs-lookup"><span data-stu-id="71b01-102">Types of Coordinate Systems</span></span>
<span data-ttu-id="71b01-103">GDI + 使用三個座標空間: [世界]、[頁面] 和 [裝置]。</span><span class="sxs-lookup"><span data-stu-id="71b01-103">GDI+ uses three coordinate spaces: world, page, and device.</span></span> <span data-ttu-id="71b01-104">全局座標是用來建立特定圖形世界模型的座標, 而且是您傳遞給 .NET Framework 中方法的座標。</span><span class="sxs-lookup"><span data-stu-id="71b01-104">World coordinates are the coordinates used to model a particular graphic world and are the coordinates you pass to methods in the .NET Framework.</span></span> <span data-ttu-id="71b01-105">頁面座標指的是繪圖介面所使用的座標系統, 例如表單或控制項。</span><span class="sxs-lookup"><span data-stu-id="71b01-105">Page coordinates refer to the coordinate system used by a drawing surface, such as a form or control.</span></span> <span data-ttu-id="71b01-106">裝置座標是用來繪製實體裝置的座標, 例如, 螢幕或紙張紙。</span><span class="sxs-lookup"><span data-stu-id="71b01-106">Device coordinates are the coordinates used by the physical device being drawn on, such as a screen or sheet of paper.</span></span> <span data-ttu-id="71b01-107">當您進行`myGraphics.DrawLine(myPen, 0, 0, 160, 80)`呼叫時, 您傳遞<xref:System.Drawing.Graphics.DrawLine%2A>給方法的點 (`(0, 0)`和`(160, 80)`) 會在全局座標空間中。</span><span class="sxs-lookup"><span data-stu-id="71b01-107">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, the points that you pass to the <xref:System.Drawing.Graphics.DrawLine%2A> method—`(0, 0)` and `(160, 80)`—are in the world coordinate space.</span></span> <span data-ttu-id="71b01-108">在 GDI + 可以繪製螢幕上的線條之前, 座標會傳遞一系列轉換。</span><span class="sxs-lookup"><span data-stu-id="71b01-108">Before GDI+ can draw the line on the screen, the coordinates pass through a sequence of transformations.</span></span> <span data-ttu-id="71b01-109">一個轉換 (稱為「世界」轉換) 會將全局座標轉換成頁面座標, 另一個轉換 (稱為「頁面」轉換) 會將頁面座標轉換成裝置座標。</span><span class="sxs-lookup"><span data-stu-id="71b01-109">One transformation, called the world transformation, converts world coordinates to page coordinates, and another transformation, called the page transformation, converts page coordinates to device coordinates.</span></span>  
  
## <a name="transforms-and-coordinate-systems"></a><span data-ttu-id="71b01-110">轉換和座標系統</span><span class="sxs-lookup"><span data-stu-id="71b01-110">Transforms and Coordinate Systems</span></span>  
 <span data-ttu-id="71b01-111">假設您想要使用座標系統, 其原點在工作區的主體中, 而不是左上角。</span><span class="sxs-lookup"><span data-stu-id="71b01-111">Suppose you want to work with a coordinate system that has its origin in the body of the client area rather than the upper-left corner.</span></span> <span data-ttu-id="71b01-112">比方說, 假設您希望原點是100圖元, 從工作區的左邊緣, 到工作區頂端50圖元。</span><span class="sxs-lookup"><span data-stu-id="71b01-112">Say, for example, that you want the origin to be 100 pixels from the left edge of the client area and 50 pixels from the top of the client area.</span></span> <span data-ttu-id="71b01-113">下圖顯示這類座標系統。</span><span class="sxs-lookup"><span data-stu-id="71b01-113">The following illustration shows such a coordinate system.</span></span>  
  
 <span data-ttu-id="71b01-114">![座標系統](./media/aboutgdip05-art01.gif "AboutGdip05_art01")</span><span class="sxs-lookup"><span data-stu-id="71b01-114">![Coordinate System](./media/aboutgdip05-art01.gif "AboutGdip05_art01")</span></span>  
  
 <span data-ttu-id="71b01-115">當您進行呼叫`myGraphics.DrawLine(myPen, 0, 0, 160, 80)`時, 您會看到下圖所示的那一行。</span><span class="sxs-lookup"><span data-stu-id="71b01-115">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, you get the line shown in the following illustration.</span></span>  
  
 <span data-ttu-id="71b01-116">![座標系統](./media/aboutgdip05-art02.gif "AboutGdip05_art02")</span><span class="sxs-lookup"><span data-stu-id="71b01-116">![Coordinate System](./media/aboutgdip05-art02.gif "AboutGdip05_art02")</span></span>  
  
 <span data-ttu-id="71b01-117">在三個座標空間中, 線條的端點座標如下所示:</span><span class="sxs-lookup"><span data-stu-id="71b01-117">The coordinates of the endpoints of your line in the three coordinate spaces are as follows:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="71b01-118">成為</span><span class="sxs-lookup"><span data-stu-id="71b01-118">World</span></span>|<span data-ttu-id="71b01-119">(0, 0) 到 (160, 80)</span><span class="sxs-lookup"><span data-stu-id="71b01-119">(0, 0) to (160, 80)</span></span>|  
|<span data-ttu-id="71b01-120">頁面</span><span class="sxs-lookup"><span data-stu-id="71b01-120">Page</span></span>|<span data-ttu-id="71b01-121">(100, 50) 到 (260, 130)</span><span class="sxs-lookup"><span data-stu-id="71b01-121">(100, 50) to (260, 130)</span></span>|  
|<span data-ttu-id="71b01-122">裝置</span><span class="sxs-lookup"><span data-stu-id="71b01-122">Device</span></span>|<span data-ttu-id="71b01-123">(100, 50) 到 (260, 130)</span><span class="sxs-lookup"><span data-stu-id="71b01-123">(100, 50) to (260, 130)</span></span>|  
  
 <span data-ttu-id="71b01-124">請注意, 頁面座標空間的原點在工作區的左上角;這一律會是這種情況。</span><span class="sxs-lookup"><span data-stu-id="71b01-124">Note that the page coordinate space has its origin at the upper-left corner of the client area; this will always be the case.</span></span> <span data-ttu-id="71b01-125">另請注意, 因為測量單位是圖元, 所以裝置座標與頁面座標相同。</span><span class="sxs-lookup"><span data-stu-id="71b01-125">Also note that because the unit of measure is the pixel, the device coordinates are the same as the page coordinates.</span></span> <span data-ttu-id="71b01-126">如果您將測量單位設定為圖元以外的值 (例如, 英寸), 則裝置座標會與頁面座標不同。</span><span class="sxs-lookup"><span data-stu-id="71b01-126">If you set the unit of measure to something other than pixels (for example, inches), then the device coordinates will be different from the page coordinates.</span></span>  
  
 <span data-ttu-id="71b01-127">將全局座標對應至頁面座標的「世界」轉換會保留在<xref:System.Drawing.Graphics.Transform%2A> <xref:System.Drawing.Graphics>類別的屬性中。</span><span class="sxs-lookup"><span data-stu-id="71b01-127">The world transformation, which maps world coordinates to page coordinates, is held in the <xref:System.Drawing.Graphics.Transform%2A> property of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="71b01-128">在上述範例中, 世界轉換是 x 方向的轉譯100單位和 y 方向的50單位。</span><span class="sxs-lookup"><span data-stu-id="71b01-128">In the preceding example, the world transformation is a translation 100 units in the x direction and 50 units in the y direction.</span></span> <span data-ttu-id="71b01-129">下列範例會設定<xref:System.Drawing.Graphics>物件的世界轉換, 然後使用該<xref:System.Drawing.Graphics>物件繪製如上圖所示的線條:</span><span class="sxs-lookup"><span data-stu-id="71b01-129">The following example sets the world transformation of a <xref:System.Drawing.Graphics> object and then uses that <xref:System.Drawing.Graphics> object to draw the line shown in the preceding figure:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 <span data-ttu-id="71b01-130">頁面轉換會將頁面座標對應至裝置座標。</span><span class="sxs-lookup"><span data-stu-id="71b01-130">The page transformation maps page coordinates to device coordinates.</span></span> <span data-ttu-id="71b01-131"><xref:System.Drawing.Graphics>類別提供和<xref:System.Drawing.Graphics.PageScale%2A>屬性, 用於動作頁面轉換。 <xref:System.Drawing.Graphics.PageUnit%2A></span><span class="sxs-lookup"><span data-stu-id="71b01-131">The <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.PageUnit%2A> and <xref:System.Drawing.Graphics.PageScale%2A> properties for manipulating the page transformation.</span></span> <span data-ttu-id="71b01-132">類別也提供兩個唯讀<xref:System.Drawing.Graphics.DpiX%2A>屬性和<xref:System.Drawing.Graphics.DpiY%2A>, 以檢查顯示裝置的每英寸水準和垂直點。 <xref:System.Drawing.Graphics></span><span class="sxs-lookup"><span data-stu-id="71b01-132">The <xref:System.Drawing.Graphics> class also provides two read-only properties, <xref:System.Drawing.Graphics.DpiX%2A> and <xref:System.Drawing.Graphics.DpiY%2A>, for examining the horizontal and vertical dots per inch of the display device.</span></span>  
  
 <span data-ttu-id="71b01-133">您可以使用<xref:System.Drawing.Graphics.PageUnit%2A> <xref:System.Drawing.Graphics>類別的屬性來指定圖元以外的量值單位。</span><span class="sxs-lookup"><span data-stu-id="71b01-133">You can use the <xref:System.Drawing.Graphics.PageUnit%2A> property of the <xref:System.Drawing.Graphics> class to specify a unit of measure other than the pixel.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71b01-134">您無法將<xref:System.Drawing.Graphics.PageUnit%2A>屬性設定為<xref:System.Drawing.GraphicsUnit.World>, 因為這不是實體單位, 而且會造成例外狀況。</span><span class="sxs-lookup"><span data-stu-id="71b01-134">You cannot set the <xref:System.Drawing.Graphics.PageUnit%2A> property to <xref:System.Drawing.GraphicsUnit.World>, as this is not a physical unit and will cause an exception.</span></span>  
  
 <span data-ttu-id="71b01-135">下列範例會繪製從 (0, 0) 到 (2, 1) 的線條, 其中的點 (2, 1) 從點到右, 1 英寸向下 (0, 0):</span><span class="sxs-lookup"><span data-stu-id="71b01-135">The following example draws a line from (0, 0) to (2, 1), where the point (2, 1) is 2 inches to the right and 1 inch down from the point (0, 0):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
> <span data-ttu-id="71b01-136">如果您在建立畫筆時未指定畫筆寬度, 上述範例會繪製一條寬度為一英寸寬的線條。</span><span class="sxs-lookup"><span data-stu-id="71b01-136">If you don't specify a pen width when you construct your pen, the preceding example will draw a line that is one inch wide.</span></span> <span data-ttu-id="71b01-137">您可以在函式的第二個引數<xref:System.Drawing.Pen>中指定畫筆寬度:</span><span class="sxs-lookup"><span data-stu-id="71b01-137">You can specify the pen width in the second argument to the <xref:System.Drawing.Pen> constructor:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 <span data-ttu-id="71b01-138">假設顯示裝置的水準方向有96個點, 以及垂直方向的每英寸96個點, 則上述範例中的線條端點在三個座標空間中具有下列座標:</span><span class="sxs-lookup"><span data-stu-id="71b01-138">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="71b01-139">成為</span><span class="sxs-lookup"><span data-stu-id="71b01-139">World</span></span>|<span data-ttu-id="71b01-140">(0, 0) 到 (2, 1)</span><span class="sxs-lookup"><span data-stu-id="71b01-140">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="71b01-141">頁面</span><span class="sxs-lookup"><span data-stu-id="71b01-141">Page</span></span>|<span data-ttu-id="71b01-142">(0, 0) 到 (2, 1)</span><span class="sxs-lookup"><span data-stu-id="71b01-142">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="71b01-143">裝置</span><span class="sxs-lookup"><span data-stu-id="71b01-143">Device</span></span>|<span data-ttu-id="71b01-144">(0, 0, 至 (192, 96)</span><span class="sxs-lookup"><span data-stu-id="71b01-144">(0, 0, to (192, 96)</span></span>|  
  
 <span data-ttu-id="71b01-145">請注意, 因為全局座標空間的原點是在工作區的左上角, 所以頁面座標與全局座標相同。</span><span class="sxs-lookup"><span data-stu-id="71b01-145">Note that because the origin of the world coordinate space is at the upper-left corner of the client area, the page coordinates are the same as the world coordinates.</span></span>  
  
 <span data-ttu-id="71b01-146">您可以結合世界和頁面轉換來達到各種效果。</span><span class="sxs-lookup"><span data-stu-id="71b01-146">You can combine the world and page transformations to achieve a variety of effects.</span></span> <span data-ttu-id="71b01-147">例如, 假設您想要使用英寸做為測量單位, 而您想要座標系統的原點是2英寸, 從工作區的左邊緣到1/2 英寸, 從工作區的頂端開始。</span><span class="sxs-lookup"><span data-stu-id="71b01-147">For example, suppose you want to use inches as the unit of measure and you want the origin of your coordinate system to be 2 inches from the left edge of the client area and 1/2 inch from the top of the client area.</span></span> <span data-ttu-id="71b01-148">下列範例會設定<xref:System.Drawing.Graphics>物件的世界和頁面轉換, 然後繪製從 (0, 0) 到 (2, 1) 的線條:</span><span class="sxs-lookup"><span data-stu-id="71b01-148">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object and then draws a line from (0, 0) to (2, 1):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 <span data-ttu-id="71b01-149">下圖顯示線條和座標系統。</span><span class="sxs-lookup"><span data-stu-id="71b01-149">The following illustration shows the line and coordinate system.</span></span>  
  
 <span data-ttu-id="71b01-150">![座標系統](./media/aboutgdip05-art03.gif "AboutGdip05_art03")</span><span class="sxs-lookup"><span data-stu-id="71b01-150">![Coordinate System](./media/aboutgdip05-art03.gif "AboutGdip05_art03")</span></span>  
  
 <span data-ttu-id="71b01-151">假設顯示裝置的水準方向有96個點, 以及垂直方向的每英寸96個點, 則上述範例中的線條端點在三個座標空間中具有下列座標:</span><span class="sxs-lookup"><span data-stu-id="71b01-151">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="71b01-152">成為</span><span class="sxs-lookup"><span data-stu-id="71b01-152">World</span></span>|<span data-ttu-id="71b01-153">(0, 0) 到 (2, 1)</span><span class="sxs-lookup"><span data-stu-id="71b01-153">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="71b01-154">頁面</span><span class="sxs-lookup"><span data-stu-id="71b01-154">Page</span></span>|<span data-ttu-id="71b01-155">(2, 0.5) 至 (4, 1.5)</span><span class="sxs-lookup"><span data-stu-id="71b01-155">(2, 0.5) to (4, 1.5)</span></span>|  
|<span data-ttu-id="71b01-156">裝置</span><span class="sxs-lookup"><span data-stu-id="71b01-156">Device</span></span>|<span data-ttu-id="71b01-157">(192, 48) 到 (384, 144)</span><span class="sxs-lookup"><span data-stu-id="71b01-157">(192, 48) to (384, 144)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="71b01-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71b01-158">See also</span></span>

- [<span data-ttu-id="71b01-159">座標系統和轉換</span><span class="sxs-lookup"><span data-stu-id="71b01-159">Coordinate Systems and Transformations</span></span>](coordinate-systems-and-transformations.md)
- [<span data-ttu-id="71b01-160">以矩陣來表示轉換</span><span class="sxs-lookup"><span data-stu-id="71b01-160">Matrix Representation of Transformations</span></span>](matrix-representation-of-transformations.md)
