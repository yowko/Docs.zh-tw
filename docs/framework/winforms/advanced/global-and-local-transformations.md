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
ms.openlocfilehash: fc23478cc4aaa51af3ff15bcc3c63590e7a8dcb2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54630875"
---
# <a name="global-and-local-transformations"></a><span data-ttu-id="616fe-102">全域和區域轉換</span><span class="sxs-lookup"><span data-stu-id="616fe-102">Global and Local Transformations</span></span>
<span data-ttu-id="616fe-103">「 全域 」 轉換這種轉換會套用至由繪製每個項目指定<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="616fe-103">A global transformation is a transformation that applies to every item drawn by a given <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="616fe-104">相較之下，「 本機 」 轉換是套用至特定的項目要繪製的轉換。</span><span class="sxs-lookup"><span data-stu-id="616fe-104">In contrast, a local transformation is a transformation that applies to a specific item to be drawn.</span></span>  
  
## <a name="global-transformations"></a><span data-ttu-id="616fe-105">全域的轉換</span><span class="sxs-lookup"><span data-stu-id="616fe-105">Global Transformations</span></span>  
 <span data-ttu-id="616fe-106">若要建立全域的轉換，建構<xref:System.Drawing.Graphics>物件，然後再操作其<xref:System.Drawing.Graphics.Transform%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="616fe-106">To create a global transformation, construct a <xref:System.Drawing.Graphics> object, and then manipulate its <xref:System.Drawing.Graphics.Transform%2A> property.</span></span> <span data-ttu-id="616fe-107"><xref:System.Drawing.Graphics.Transform%2A>屬性是<xref:System.Drawing.Drawing2D.Matrix>物件，因此它可以保留任何順序的仿射轉換。</span><span class="sxs-lookup"><span data-stu-id="616fe-107">The <xref:System.Drawing.Graphics.Transform%2A> property is a <xref:System.Drawing.Drawing2D.Matrix> object, so it can hold any sequence of affine transformations.</span></span> <span data-ttu-id="616fe-108">轉換儲存在<xref:System.Drawing.Graphics.Transform%2A>屬性稱為全局轉換。</span><span class="sxs-lookup"><span data-stu-id="616fe-108">The transformation stored in the <xref:System.Drawing.Graphics.Transform%2A> property is called the world transformation.</span></span> <span data-ttu-id="616fe-109"><xref:System.Drawing.Graphics>類別提供多種方法來建立複合的全局轉換： <xref:System.Drawing.Graphics.MultiplyTransform%2A>， <xref:System.Drawing.Graphics.RotateTransform%2A>， <xref:System.Drawing.Graphics.ScaleTransform%2A>，和<xref:System.Drawing.Graphics.TranslateTransform%2A>。</span><span class="sxs-lookup"><span data-stu-id="616fe-109">The <xref:System.Drawing.Graphics> class provides several methods for building up a composite world transformation: <xref:System.Drawing.Graphics.MultiplyTransform%2A>, <xref:System.Drawing.Graphics.RotateTransform%2A>, <xref:System.Drawing.Graphics.ScaleTransform%2A>, and <xref:System.Drawing.Graphics.TranslateTransform%2A>.</span></span> <span data-ttu-id="616fe-110">下列範例會繪製一個橢圓形兩次： 一次之前建立的自然變換和之後的一次。</span><span class="sxs-lookup"><span data-stu-id="616fe-110">The following example draws an ellipse twice: once before creating a world transformation and once after.</span></span> <span data-ttu-id="616fe-111">轉換第一次調整 y 方向的 0.5 倍然後平移 x 方向的 50 個單位，並再旋轉 30 度。</span><span class="sxs-lookup"><span data-stu-id="616fe-111">The transformation first scales by a factor of 0.5 in the y direction, then translates 50 units in the x direction, and then rotates 30 degrees.</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#21)]  
  
 <span data-ttu-id="616fe-112">下圖顯示參與轉換矩陣。</span><span class="sxs-lookup"><span data-stu-id="616fe-112">The following illustration shows the matrices involved in the transformation.</span></span>  
  
 <span data-ttu-id="616fe-113">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art14.gif "AboutGdip05_art14")</span><span class="sxs-lookup"><span data-stu-id="616fe-113">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art14.gif "AboutGdip05_art14")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="616fe-114">在上述範例中，省略符號會旋轉的座標系統中，工作區的左上角原點。</span><span class="sxs-lookup"><span data-stu-id="616fe-114">In the preceding example, the ellipse is rotated about the origin of the coordinate system, which is at the upper-left corner of the client area.</span></span> <span data-ttu-id="616fe-115">這會產生旋轉橢圓形繞著自己中心不同的結果。</span><span class="sxs-lookup"><span data-stu-id="616fe-115">This produces a different result than rotating the ellipse about its own center.</span></span>  
  
## <a name="local-transformations"></a><span data-ttu-id="616fe-116">區域轉換</span><span class="sxs-lookup"><span data-stu-id="616fe-116">Local Transformations</span></span>  
 <span data-ttu-id="616fe-117">局部的轉換套用至特定的項目要繪製。</span><span class="sxs-lookup"><span data-stu-id="616fe-117">A local transformation applies to a specific item to be drawn.</span></span> <span data-ttu-id="616fe-118">例如，<xref:System.Drawing.Drawing2D.GraphicsPath>物件具有<xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A>方法，可讓您將資料點，該路徑的轉換。</span><span class="sxs-lookup"><span data-stu-id="616fe-118">For example, a <xref:System.Drawing.Drawing2D.GraphicsPath> object has a <xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A> method that allows you to transform the data points of that path.</span></span> <span data-ttu-id="616fe-119">下列範例會繪製任何轉換的矩形和旋轉轉換的路徑。</span><span class="sxs-lookup"><span data-stu-id="616fe-119">The following example draws a rectangle with no transformation and a path with a rotation transformation.</span></span> <span data-ttu-id="616fe-120">（假設沒有任何全局轉換）。</span><span class="sxs-lookup"><span data-stu-id="616fe-120">(Assume that there is no world transformation.)</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#22)]  
  
 <span data-ttu-id="616fe-121">您可以結合自然變換和區域轉換來達成各種不同的結果。</span><span class="sxs-lookup"><span data-stu-id="616fe-121">You can combine the world transformation with local transformations to achieve a variety of results.</span></span> <span data-ttu-id="616fe-122">例如，您可以使用全局轉換到修改座標系統，並使用本機的轉換，旋轉和縮放新的座標系統上所繪製的物件。</span><span class="sxs-lookup"><span data-stu-id="616fe-122">For example, you can use the world transformation to revise the coordinate system and use local transformations to rotate and scale objects drawn on the new coordinate system.</span></span>  
  
 <span data-ttu-id="616fe-123">假設您想要具有其原始 200 像素為單位從工作區左邊緣和工作區頂端的 150 個像素座標系統。</span><span class="sxs-lookup"><span data-stu-id="616fe-123">Suppose you want a coordinate system that has its origin 200 pixels from the left edge of the client area and 150 pixels from the top of the client area.</span></span> <span data-ttu-id="616fe-124">此外，假設您想要的像素，與 x 軸指向右側和 y 軸向上的測量單位。</span><span class="sxs-lookup"><span data-stu-id="616fe-124">Furthermore, assume that you want the unit of measure to be the pixel, with the x-axis pointing to the right and the y-axis pointing up.</span></span> <span data-ttu-id="616fe-125">預設座標系統中將有 y 軸指向下方，因此您必須執行反映在水平軸。</span><span class="sxs-lookup"><span data-stu-id="616fe-125">The default coordinate system has the y-axis pointing down, so you need to perform a reflection across the horizontal axis.</span></span> <span data-ttu-id="616fe-126">下圖顯示此類反射的矩陣。</span><span class="sxs-lookup"><span data-stu-id="616fe-126">The following illustration shows the matrix of such a reflection.</span></span>  
  
 <span data-ttu-id="616fe-127">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art15.gif "AboutGdip05_art15")</span><span class="sxs-lookup"><span data-stu-id="616fe-127">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art15.gif "AboutGdip05_art15")</span></span>  
  
 <span data-ttu-id="616fe-128">接下來，假設您要執行轉譯的 200 個單位向右和向下的 150 單位。</span><span class="sxs-lookup"><span data-stu-id="616fe-128">Next, assume you need to perform a translation 200 units to the right and 150 units down.</span></span>  
  
 <span data-ttu-id="616fe-129">下列範例會建立所設定的自然變換剛描述的座標系統<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="616fe-129">The following example establishes the coordinate system just described by setting the world transformation of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#23)]  
  
 <span data-ttu-id="616fe-130">下列程式碼 （放在前述範例中的結尾） 會建立單一的新的座標系統的原始位置左下方角矩形組成的路徑。</span><span class="sxs-lookup"><span data-stu-id="616fe-130">The following code (placed at the end of the preceding example) creates a path that consists of a single rectangle with its lower-left corner at the origin of the new coordinate system.</span></span> <span data-ttu-id="616fe-131">矩形填滿一次搭配任何本機的轉換與一次本機的轉換。</span><span class="sxs-lookup"><span data-stu-id="616fe-131">The rectangle is filled once with no local transformation and once with a local transformation.</span></span> <span data-ttu-id="616fe-132">「 本機 」 轉換包含水平調整，後面接著 30 度旋轉的 2 倍。</span><span class="sxs-lookup"><span data-stu-id="616fe-132">The local transformation consists of a horizontal scaling by a factor of 2 followed by a 30-degree rotation.</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#24)]
 [!code-vb[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#24)]  
  
 <span data-ttu-id="616fe-133">下圖顯示新的座標系統和兩個矩形。</span><span class="sxs-lookup"><span data-stu-id="616fe-133">The following illustration shows the new coordinate system and the two rectangles.</span></span>  
  
 <span data-ttu-id="616fe-134">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art16.gif "AboutGdip05_art16")</span><span class="sxs-lookup"><span data-stu-id="616fe-134">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art16.gif "AboutGdip05_art16")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="616fe-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="616fe-135">See also</span></span>
- [<span data-ttu-id="616fe-136">座標系統和轉換</span><span class="sxs-lookup"><span data-stu-id="616fe-136">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)
- [<span data-ttu-id="616fe-137">使用 Managed GDI+ 中的轉換</span><span class="sxs-lookup"><span data-stu-id="616fe-137">Using Transformations in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
