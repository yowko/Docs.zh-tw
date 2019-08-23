---
title: 全域和區域轉換
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- matrices [Windows Forms], using transformations
- transformations [Windows Forms], global
- transformations [Windows Forms], local
ms.assetid: b601d66d-d572-4f11-9d2e-92f0dc8893f3
ms.openlocfilehash: f62efb31e95b0797272997fadbc28459579a0de0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955194"
---
# <a name="global-and-local-transformations"></a><span data-ttu-id="4c582-102">全域和區域轉換</span><span class="sxs-lookup"><span data-stu-id="4c582-102">Global and Local Transformations</span></span>
<span data-ttu-id="4c582-103">全域轉換是一種轉換, 適用于指定<xref:System.Drawing.Graphics>物件所繪製的每個專案。</span><span class="sxs-lookup"><span data-stu-id="4c582-103">A global transformation is a transformation that applies to every item drawn by a given <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="4c582-104">相反地, 「局部轉換」是一種轉換, 適用于要繪製的特定專案。</span><span class="sxs-lookup"><span data-stu-id="4c582-104">In contrast, a local transformation is a transformation that applies to a specific item to be drawn.</span></span>  
  
## <a name="global-transformations"></a><span data-ttu-id="4c582-105">全域轉換</span><span class="sxs-lookup"><span data-stu-id="4c582-105">Global Transformations</span></span>  
 <span data-ttu-id="4c582-106">若要建立全域轉換, 請先<xref:System.Drawing.Graphics>建立物件, 然後再操控<xref:System.Drawing.Graphics.Transform%2A>其屬性。</span><span class="sxs-lookup"><span data-stu-id="4c582-106">To create a global transformation, construct a <xref:System.Drawing.Graphics> object, and then manipulate its <xref:System.Drawing.Graphics.Transform%2A> property.</span></span> <span data-ttu-id="4c582-107"><xref:System.Drawing.Graphics.Transform%2A> 屬性<xref:System.Drawing.Drawing2D.Matrix>是物件, 因此可以保留任何一系列的仿射轉換。</span><span class="sxs-lookup"><span data-stu-id="4c582-107">The <xref:System.Drawing.Graphics.Transform%2A> property is a <xref:System.Drawing.Drawing2D.Matrix> object, so it can hold any sequence of affine transformations.</span></span> <span data-ttu-id="4c582-108">儲存在<xref:System.Drawing.Graphics.Transform%2A>屬性中的轉換稱為「世界轉換」。</span><span class="sxs-lookup"><span data-stu-id="4c582-108">The transformation stored in the <xref:System.Drawing.Graphics.Transform%2A> property is called the world transformation.</span></span> <span data-ttu-id="4c582-109"><xref:System.Drawing.Graphics.RotateTransform%2A> <xref:System.Drawing.Graphics.MultiplyTransform%2A> <xref:System.Drawing.Graphics.TranslateTransform%2A> <xref:System.Drawing.Graphics.ScaleTransform%2A>類別提供數種方法來建立複合世界轉換:、、和。 <xref:System.Drawing.Graphics></span><span class="sxs-lookup"><span data-stu-id="4c582-109">The <xref:System.Drawing.Graphics> class provides several methods for building up a composite world transformation: <xref:System.Drawing.Graphics.MultiplyTransform%2A>, <xref:System.Drawing.Graphics.RotateTransform%2A>, <xref:System.Drawing.Graphics.ScaleTransform%2A>, and <xref:System.Drawing.Graphics.TranslateTransform%2A>.</span></span> <span data-ttu-id="4c582-110">下列範例會繪製一個橢圓形兩次: 一次是在建立世界轉換之後, 一次在之後。</span><span class="sxs-lookup"><span data-stu-id="4c582-110">The following example draws an ellipse twice: once before creating a world transformation and once after.</span></span> <span data-ttu-id="4c582-111">轉換會先依 y 方向調整為0.5 因數, 然後在 x 方向轉譯50單位, 然後旋轉30度。</span><span class="sxs-lookup"><span data-stu-id="4c582-111">The transformation first scales by a factor of 0.5 in the y direction, then translates 50 units in the x direction, and then rotates 30 degrees.</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.CoordinateSystems#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#21)]  
  
 <span data-ttu-id="4c582-112">下圖顯示轉換所涉及的矩陣。</span><span class="sxs-lookup"><span data-stu-id="4c582-112">The following illustration shows the matrices involved in the transformation.</span></span>  
  
 <span data-ttu-id="4c582-113">![Transformations](./media/aboutgdip05-art14.gif "AboutGdip05_art14")</span><span class="sxs-lookup"><span data-stu-id="4c582-113">![Transformations](./media/aboutgdip05-art14.gif "AboutGdip05_art14")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4c582-114">在上述範例中, 橢圓形會繞過座標系統的原點, 位於工作區的左上角。</span><span class="sxs-lookup"><span data-stu-id="4c582-114">In the preceding example, the ellipse is rotated about the origin of the coordinate system, which is at the upper-left corner of the client area.</span></span> <span data-ttu-id="4c582-115">這會產生不同的結果, 而不是旋轉其本身中心的橢圓形。</span><span class="sxs-lookup"><span data-stu-id="4c582-115">This produces a different result than rotating the ellipse about its own center.</span></span>  
  
## <a name="local-transformations"></a><span data-ttu-id="4c582-116">本機轉換</span><span class="sxs-lookup"><span data-stu-id="4c582-116">Local Transformations</span></span>  
 <span data-ttu-id="4c582-117">本機轉換會套用至要繪製的特定專案。</span><span class="sxs-lookup"><span data-stu-id="4c582-117">A local transformation applies to a specific item to be drawn.</span></span> <span data-ttu-id="4c582-118">例如, <xref:System.Drawing.Drawing2D.GraphicsPath>物件<xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A>的方法可讓您轉換該路徑的資料點。</span><span class="sxs-lookup"><span data-stu-id="4c582-118">For example, a <xref:System.Drawing.Drawing2D.GraphicsPath> object has a <xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A> method that allows you to transform the data points of that path.</span></span> <span data-ttu-id="4c582-119">下列範例會繪製沒有轉換的矩形, 以及具有旋轉轉換的路徑。</span><span class="sxs-lookup"><span data-stu-id="4c582-119">The following example draws a rectangle with no transformation and a path with a rotation transformation.</span></span> <span data-ttu-id="4c582-120">(假設沒有任何世界轉換)。</span><span class="sxs-lookup"><span data-stu-id="4c582-120">(Assume that there is no world transformation.)</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.CoordinateSystems#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#22)]  
  
 <span data-ttu-id="4c582-121">您可以結合「世界」轉換與「本機」轉換來達到各種不同的結果。</span><span class="sxs-lookup"><span data-stu-id="4c582-121">You can combine the world transformation with local transformations to achieve a variety of results.</span></span> <span data-ttu-id="4c582-122">例如, 您可以使用「世界」轉換來修改座標系統, 並使用「區域」轉換來旋轉和縮放在新座標系統上繪製的物件。</span><span class="sxs-lookup"><span data-stu-id="4c582-122">For example, you can use the world transformation to revise the coordinate system and use local transformations to rotate and scale objects drawn on the new coordinate system.</span></span>  
  
 <span data-ttu-id="4c582-123">假設您想要一個座標系統, 其原點為200圖元, 從工作區的左邊緣到工作區的頂端150圖元。</span><span class="sxs-lookup"><span data-stu-id="4c582-123">Suppose you want a coordinate system that has its origin 200 pixels from the left edge of the client area and 150 pixels from the top of the client area.</span></span> <span data-ttu-id="4c582-124">此外, 假設您希望測量單位是圖元, 而 X 軸指向右側, 而 y 軸指向上方。</span><span class="sxs-lookup"><span data-stu-id="4c582-124">Furthermore, assume that you want the unit of measure to be the pixel, with the x-axis pointing to the right and the y-axis pointing up.</span></span> <span data-ttu-id="4c582-125">預設座標系統會將 y 軸指向下方, 因此您需要跨水準軸執行反映。</span><span class="sxs-lookup"><span data-stu-id="4c582-125">The default coordinate system has the y-axis pointing down, so you need to perform a reflection across the horizontal axis.</span></span> <span data-ttu-id="4c582-126">下圖顯示這類反映的矩陣。</span><span class="sxs-lookup"><span data-stu-id="4c582-126">The following illustration shows the matrix of such a reflection.</span></span>  
  
 <span data-ttu-id="4c582-127">![Transformations](./media/aboutgdip05-art15.gif "AboutGdip05_art15")</span><span class="sxs-lookup"><span data-stu-id="4c582-127">![Transformations](./media/aboutgdip05-art15.gif "AboutGdip05_art15")</span></span>  
  
 <span data-ttu-id="4c582-128">接下來, 假設您需要向右和150個單位執行轉譯200單位。</span><span class="sxs-lookup"><span data-stu-id="4c582-128">Next, assume you need to perform a translation 200 units to the right and 150 units down.</span></span>  
  
 <span data-ttu-id="4c582-129">下列範例會藉由設定<xref:System.Drawing.Graphics>物件的世界轉換, 建立剛才描述的座標系統。</span><span class="sxs-lookup"><span data-stu-id="4c582-129">The following example establishes the coordinate system just described by setting the world transformation of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.CoordinateSystems#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#23)]  
  
 <span data-ttu-id="4c582-130">下列程式碼 (放在上述範例的結尾) 會建立一個路徑, 其中包含一個矩形, 其左下角位於新座標系統的原點。</span><span class="sxs-lookup"><span data-stu-id="4c582-130">The following code (placed at the end of the preceding example) creates a path that consists of a single rectangle with its lower-left corner at the origin of the new coordinate system.</span></span> <span data-ttu-id="4c582-131">矩形會填入一次, 但不含本機轉換, 一次是使用本機轉換。</span><span class="sxs-lookup"><span data-stu-id="4c582-131">The rectangle is filled once with no local transformation and once with a local transformation.</span></span> <span data-ttu-id="4c582-132">「局部」轉換是由一因數2的水準調整組成, 後面接著30度的旋轉。</span><span class="sxs-lookup"><span data-stu-id="4c582-132">The local transformation consists of a horizontal scaling by a factor of 2 followed by a 30-degree rotation.</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#24](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#24)]
 [!code-vb[System.Drawing.CoordinateSystems#24](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#24)]  
  
 <span data-ttu-id="4c582-133">下圖顯示新的座標系統和兩個矩形。</span><span class="sxs-lookup"><span data-stu-id="4c582-133">The following illustration shows the new coordinate system and the two rectangles.</span></span>  
  
 <span data-ttu-id="4c582-134">![Transformations](./media/aboutgdip05-art16.gif "AboutGdip05_art16")</span><span class="sxs-lookup"><span data-stu-id="4c582-134">![Transformations](./media/aboutgdip05-art16.gif "AboutGdip05_art16")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c582-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c582-135">See also</span></span>

- [<span data-ttu-id="4c582-136">座標系統和轉換</span><span class="sxs-lookup"><span data-stu-id="4c582-136">Coordinate Systems and Transformations</span></span>](coordinate-systems-and-transformations.md)
- [<span data-ttu-id="4c582-137">使用 Managed GDI+ 中的轉換</span><span class="sxs-lookup"><span data-stu-id="4c582-137">Using Transformations in Managed GDI+</span></span>](using-transformations-in-managed-gdi.md)
