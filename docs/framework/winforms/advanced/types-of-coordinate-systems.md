---
title: "座標系統類型"
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: be89584ee8e7a82c405bf8664bfad18ced6d989a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="types-of-coordinate-systems"></a><span data-ttu-id="eae90-102">座標系統類型</span><span class="sxs-lookup"><span data-stu-id="eae90-102">Types of Coordinate Systems</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="eae90-103">會使用三種座標空間： world、 頁面和裝置。</span><span class="sxs-lookup"><span data-stu-id="eae90-103"> uses three coordinate spaces: world, page, and device.</span></span> <span data-ttu-id="eae90-104">全局座標是用來建立模型特定的圖形範圍的座標，您將傳遞至方法在.NET Framework 中的座標。</span><span class="sxs-lookup"><span data-stu-id="eae90-104">World coordinates are the coordinates used to model a particular graphic world and are the coordinates you pass to methods in the .NET Framework.</span></span> <span data-ttu-id="eae90-105">頁面座標是指繪圖介面，例如表單或控制項所使用的座標系統。</span><span class="sxs-lookup"><span data-stu-id="eae90-105">Page coordinates refer to the coordinate system used by a drawing surface, such as a form or control.</span></span> <span data-ttu-id="eae90-106">裝置座標是實體裝置，例如螢幕或紙張繪製所使用的座標。</span><span class="sxs-lookup"><span data-stu-id="eae90-106">Device coordinates are the coordinates used by the physical device being drawn on, such as a screen or sheet of paper.</span></span> <span data-ttu-id="eae90-107">當您進行的呼叫`myGraphics.DrawLine(myPen, 0, 0, 160, 80)`，傳遞至的點<xref:System.Drawing.Graphics.DrawLine%2A>方法-`(0, 0)`和`(160, 80)`— 中全局座標空間。</span><span class="sxs-lookup"><span data-stu-id="eae90-107">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, the points that you pass to the <xref:System.Drawing.Graphics.DrawLine%2A> method—`(0, 0)` and `(160, 80)`—are in the world coordinate space.</span></span> <span data-ttu-id="eae90-108">之前[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]可以在螢幕上繪製線條，通過一連串的轉換的座標。</span><span class="sxs-lookup"><span data-stu-id="eae90-108">Before [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] can draw the line on the screen, the coordinates pass through a sequence of transformations.</span></span> <span data-ttu-id="eae90-109">一個轉換，稱為全局轉換，將全局座標轉換為頁面座標和另一個轉換，稱為 「 頁面 」 轉換，將頁面座標轉換為裝置座標。</span><span class="sxs-lookup"><span data-stu-id="eae90-109">One transformation, called the world transformation, converts world coordinates to page coordinates, and another transformation, called the page transformation, converts page coordinates to device coordinates.</span></span>  
  
## <a name="transforms-and-coordinate-systems"></a><span data-ttu-id="eae90-110">轉換與座標系統</span><span class="sxs-lookup"><span data-stu-id="eae90-110">Transforms and Coordinate Systems</span></span>  
 <span data-ttu-id="eae90-111">假設您想要搭配使用的原點本文工作區，而不是左上角的座標系統。</span><span class="sxs-lookup"><span data-stu-id="eae90-111">Suppose you want to work with a coordinate system that has its origin in the body of the client area rather than the upper-left corner.</span></span> <span data-ttu-id="eae90-112">比方說，假設您想為 100 像素為單位，從工作區左邊緣和從用戶端區域的頂端 50 像素的原點。</span><span class="sxs-lookup"><span data-stu-id="eae90-112">Say, for example, that you want the origin to be 100 pixels from the left edge of the client area and 50 pixels from the top of the client area.</span></span> <span data-ttu-id="eae90-113">下圖顯示這類的座標系統。</span><span class="sxs-lookup"><span data-stu-id="eae90-113">The following illustration shows such a coordinate system.</span></span>  
  
 <span data-ttu-id="eae90-114">![座標系統](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art01.gif "AboutGdip05_art01")</span><span class="sxs-lookup"><span data-stu-id="eae90-114">![Coordinate System](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art01.gif "AboutGdip05_art01")</span></span>  
  
 <span data-ttu-id="eae90-115">當您建立呼叫`myGraphics.DrawLine(myPen, 0, 0, 160, 80)`，取得在下圖顯示的列。</span><span class="sxs-lookup"><span data-stu-id="eae90-115">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, you get the line shown in the following illustration.</span></span>  
  
 <span data-ttu-id="eae90-116">![座標系統](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art02.gif "AboutGdip05_art02")</span><span class="sxs-lookup"><span data-stu-id="eae90-116">![Coordinate System](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art02.gif "AboutGdip05_art02")</span></span>  
  
 <span data-ttu-id="eae90-117">三種座標空間中的程式行的結束點的座標如下所示：</span><span class="sxs-lookup"><span data-stu-id="eae90-117">The coordinates of the endpoints of your line in the three coordinate spaces are as follows:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eae90-118">世界</span><span class="sxs-lookup"><span data-stu-id="eae90-118">World</span></span>|<span data-ttu-id="eae90-119">（0，0） 到 160 (80）</span><span class="sxs-lookup"><span data-stu-id="eae90-119">(0, 0) to (160, 80)</span></span>|  
|<span data-ttu-id="eae90-120">頁面</span><span class="sxs-lookup"><span data-stu-id="eae90-120">Page</span></span>|<span data-ttu-id="eae90-121">（100，50） 到 （260、 130）</span><span class="sxs-lookup"><span data-stu-id="eae90-121">(100, 50) to (260, 130)</span></span>|  
|<span data-ttu-id="eae90-122">裝置</span><span class="sxs-lookup"><span data-stu-id="eae90-122">Device</span></span>|<span data-ttu-id="eae90-123">（100，50） 到 （260、 130）</span><span class="sxs-lookup"><span data-stu-id="eae90-123">(100, 50) to (260, 130)</span></span>|  
  
 <span data-ttu-id="eae90-124">請注意，畫面座標空間原點左上角的 用戶端的區域。一律是這樣的情況。</span><span class="sxs-lookup"><span data-stu-id="eae90-124">Note that the page coordinate space has its origin at the upper-left corner of the client area; this will always be the case.</span></span> <span data-ttu-id="eae90-125">也請注意，因為量值的單位為像素，裝置座標畫面座標相同。</span><span class="sxs-lookup"><span data-stu-id="eae90-125">Also note that because the unit of measure is the pixel, the device coordinates are the same as the page coordinates.</span></span> <span data-ttu-id="eae90-126">如果您設定的度量單位為像素為單位 （例如英吋） 以外的項目，則裝置座標會不同於畫面座標。</span><span class="sxs-lookup"><span data-stu-id="eae90-126">If you set the unit of measure to something other than pixels (for example, inches), then the device coordinates will be different from the page coordinates.</span></span>  
  
 <span data-ttu-id="eae90-127">全局轉換，以將全局座標對應頁面座標，保存在<xref:System.Drawing.Graphics.Transform%2A>屬性<xref:System.Drawing.Graphics>類別。</span><span class="sxs-lookup"><span data-stu-id="eae90-127">The world transformation, which maps world coordinates to page coordinates, is held in the <xref:System.Drawing.Graphics.Transform%2A> property of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="eae90-128">在上述範例中，自然變換是 x 方向的 100 個轉譯單位和 50 個單位，在 y 方向。</span><span class="sxs-lookup"><span data-stu-id="eae90-128">In the preceding example, the world transformation is a translation 100 units in the x direction and 50 units in the y direction.</span></span> <span data-ttu-id="eae90-129">下列範例會設定的自然變換<xref:System.Drawing.Graphics>物件，並會使用該<xref:System.Drawing.Graphics>物件来繪製在上圖中顯示的列：</span><span class="sxs-lookup"><span data-stu-id="eae90-129">The following example sets the world transformation of a <xref:System.Drawing.Graphics> object and then uses that <xref:System.Drawing.Graphics> object to draw the line shown in the preceding figure:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 <span data-ttu-id="eae90-130">頁面轉換會將頁面座標對應至裝置座標。</span><span class="sxs-lookup"><span data-stu-id="eae90-130">The page transformation maps page coordinates to device coordinates.</span></span> <span data-ttu-id="eae90-131"><xref:System.Drawing.Graphics>類別提供<xref:System.Drawing.Graphics.PageUnit%2A>和<xref:System.Drawing.Graphics.PageScale%2A>管理畫面轉換的屬性。</span><span class="sxs-lookup"><span data-stu-id="eae90-131">The <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.PageUnit%2A> and <xref:System.Drawing.Graphics.PageScale%2A> properties for manipulating the page transformation.</span></span> <span data-ttu-id="eae90-132"><xref:System.Drawing.Graphics>類別也提供兩個唯讀屬性，<xref:System.Drawing.Graphics.DpiX%2A>和<xref:System.Drawing.Graphics.DpiY%2A>，檢查水平和垂直 dpi 顯示裝置。</span><span class="sxs-lookup"><span data-stu-id="eae90-132">The <xref:System.Drawing.Graphics> class also provides two read-only properties, <xref:System.Drawing.Graphics.DpiX%2A> and <xref:System.Drawing.Graphics.DpiY%2A>, for examining the horizontal and vertical dots per inch of the display device.</span></span>  
  
 <span data-ttu-id="eae90-133">您可以使用<xref:System.Drawing.Graphics.PageUnit%2A>屬性<xref:System.Drawing.Graphics>類別，以指定的像素以外的測量單位。</span><span class="sxs-lookup"><span data-stu-id="eae90-133">You can use the <xref:System.Drawing.Graphics.PageUnit%2A> property of the <xref:System.Drawing.Graphics> class to specify a unit of measure other than the pixel.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eae90-134">您不能設定<xref:System.Drawing.Graphics.PageUnit%2A>屬性<xref:System.Drawing.GraphicsUnit.World>，因為這不是實體裝置，並會導致例外狀況。</span><span class="sxs-lookup"><span data-stu-id="eae90-134">You cannot set the <xref:System.Drawing.Graphics.PageUnit%2A> property to <xref:System.Drawing.GraphicsUnit.World>, as this is not a physical unit and will cause an exception.</span></span>  
  
 <span data-ttu-id="eae90-135">下列範例會繪製線條，以從 （0，0） 到 （2，1），其中的點 （2，1） 是 2 英吋，向右和向下 1 英吋從點 （0，0）：</span><span class="sxs-lookup"><span data-stu-id="eae90-135">The following example draws a line from (0, 0) to (2, 1), where the point (2, 1) is 2 inches to the right and 1 inch down from the point (0, 0):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  <span data-ttu-id="eae90-136">如果您未指定畫筆寬度，當您建構您的畫筆時，上述範例中，會繪製為一英吋寬的線條。</span><span class="sxs-lookup"><span data-stu-id="eae90-136">If you don't specify a pen width when you construct your pen, the preceding example will draw a line that is one inch wide.</span></span> <span data-ttu-id="eae90-137">您可以指定的第二個引數中的畫筆寬度<xref:System.Drawing.Pen>建構函式：</span><span class="sxs-lookup"><span data-stu-id="eae90-137">You can specify the pen width in the second argument to the <xref:System.Drawing.Pen> constructor:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 <span data-ttu-id="eae90-138">如果我們假設顯示裝置，具有 96 dpi 的水平方向與 96 dpi 在垂直方向，在上述範例中線條的端點會有下列座標在三個座標空間：</span><span class="sxs-lookup"><span data-stu-id="eae90-138">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eae90-139">世界</span><span class="sxs-lookup"><span data-stu-id="eae90-139">World</span></span>|<span data-ttu-id="eae90-140">（0，0） 到 （2，1）</span><span class="sxs-lookup"><span data-stu-id="eae90-140">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="eae90-141">頁面</span><span class="sxs-lookup"><span data-stu-id="eae90-141">Page</span></span>|<span data-ttu-id="eae90-142">（0，0） 到 （2，1）</span><span class="sxs-lookup"><span data-stu-id="eae90-142">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="eae90-143">裝置</span><span class="sxs-lookup"><span data-stu-id="eae90-143">Device</span></span>|<span data-ttu-id="eae90-144">(0，0，以 192 (96）</span><span class="sxs-lookup"><span data-stu-id="eae90-144">(0, 0, to (192, 96)</span></span>|  
  
 <span data-ttu-id="eae90-145">請注意，因為全局座標空間的原點位於左上角的用戶端區域時，畫面座標全局座標相同。</span><span class="sxs-lookup"><span data-stu-id="eae90-145">Note that because the origin of the world coordinate space is at the upper-left corner of the client area, the page coordinates are the same as the world coordinates.</span></span>  
  
 <span data-ttu-id="eae90-146">您可以結合全局和頁面轉換，以達成各種不同的效果。</span><span class="sxs-lookup"><span data-stu-id="eae90-146">You can combine the world and page transformations to achieve a variety of effects.</span></span> <span data-ttu-id="eae90-147">例如，假設您想要使用的測量單位為英吋，而您想從左邊緣起 2 英吋的 1/2 英吋，從用戶端區域的頂端與工作區座標系統的原點。</span><span class="sxs-lookup"><span data-stu-id="eae90-147">For example, suppose you want to use inches as the unit of measure and you want the origin of your coordinate system to be 2 inches from the left edge of the client area and 1/2 inch from the top of the client area.</span></span> <span data-ttu-id="eae90-148">下列範例會設定全局和頁面轉換<xref:System.Drawing.Graphics>物件，並再繪製的直線 （0，0） 到 （2，1）：</span><span class="sxs-lookup"><span data-stu-id="eae90-148">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object and then draws a line from (0, 0) to (2, 1):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 <span data-ttu-id="eae90-149">下圖顯示的行和座標系統。</span><span class="sxs-lookup"><span data-stu-id="eae90-149">The following illustration shows the line and coordinate system.</span></span>  
  
 <span data-ttu-id="eae90-150">![座標系統](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art03.gif "AboutGdip05_art03")</span><span class="sxs-lookup"><span data-stu-id="eae90-150">![Coordinate System](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art03.gif "AboutGdip05_art03")</span></span>  
  
 <span data-ttu-id="eae90-151">如果我們假設顯示裝置，具有 96 dpi 的水平方向與 96 dpi 在垂直方向，在上述範例中線條的端點會有下列座標在三個座標空間：</span><span class="sxs-lookup"><span data-stu-id="eae90-151">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eae90-152">世界</span><span class="sxs-lookup"><span data-stu-id="eae90-152">World</span></span>|<span data-ttu-id="eae90-153">（0，0） 到 （2，1）</span><span class="sxs-lookup"><span data-stu-id="eae90-153">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="eae90-154">頁面</span><span class="sxs-lookup"><span data-stu-id="eae90-154">Page</span></span>|<span data-ttu-id="eae90-155">（2，0.5） 到 （4，1.5）</span><span class="sxs-lookup"><span data-stu-id="eae90-155">(2, 0.5) to (4, 1.5)</span></span>|  
|<span data-ttu-id="eae90-156">裝置</span><span class="sxs-lookup"><span data-stu-id="eae90-156">Device</span></span>|<span data-ttu-id="eae90-157">（192，48） 到 （384、 144）</span><span class="sxs-lookup"><span data-stu-id="eae90-157">(192, 48) to (384, 144)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eae90-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eae90-158">See Also</span></span>  
 [<span data-ttu-id="eae90-159">座標系統和轉換</span><span class="sxs-lookup"><span data-stu-id="eae90-159">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [<span data-ttu-id="eae90-160">以矩陣來表示轉換</span><span class="sxs-lookup"><span data-stu-id="eae90-160">Matrix Representation of Transformations</span></span>](../../../../docs/framework/winforms/advanced/matrix-representation-of-transformations.md)
