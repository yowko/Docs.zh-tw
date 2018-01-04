---
title: "如何：使用影像並排顯示圖案"
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
- texture brushes [Windows Forms], tiling images with
- images [Windows Forms], filling shapes with
- shapes [Windows Forms], tiling with images
- bitmaps [Windows Forms], filling shapes with
ms.assetid: 6d407891-6e5c-4495-a546-3da5604e9fb8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d8726322e9443042b76c28e7b4b22ebc51c871bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-tile-a-shape-with-an-image"></a><span data-ttu-id="83780-102">如何：使用影像並排顯示圖案</span><span class="sxs-lookup"><span data-stu-id="83780-102">How to: Tile a Shape with an Image</span></span>
<span data-ttu-id="83780-103">磚可以放在相鄰涵蓋樓層，如同可以相鄰放置矩形的映像，填滿 （磚） 圖形。</span><span class="sxs-lookup"><span data-stu-id="83780-103">Just as tiles can be placed next to each other to cover a floor, rectangular images can be placed next to each other to fill (tile) a shape.</span></span> <span data-ttu-id="83780-104">若要並排顯示圖案的內部，使用紋理筆刷。</span><span class="sxs-lookup"><span data-stu-id="83780-104">To tile the interior of a shape, use a texture brush.</span></span> <span data-ttu-id="83780-105">當您建構<xref:System.Drawing.TextureBrush>物件，其中您傳遞給建構函式的引數為<xref:System.Drawing.Image>物件。</span><span class="sxs-lookup"><span data-stu-id="83780-105">When you construct a <xref:System.Drawing.TextureBrush> object, one of the arguments you pass to the constructor is an <xref:System.Drawing.Image> object.</span></span> <span data-ttu-id="83780-106">當您使用的材質筆刷繪製圖形內部時，此映像的重複複本填滿的圖案。</span><span class="sxs-lookup"><span data-stu-id="83780-106">When you use the texture brush to paint the interior of a shape, the shape is filled with repeated copies of this image.</span></span>  
  
 <span data-ttu-id="83780-107">自動換行模式屬性的<xref:System.Drawing.TextureBrush>物件決定如何將映像導向矩形格線中重複時。</span><span class="sxs-lookup"><span data-stu-id="83780-107">The wrap mode property of the <xref:System.Drawing.TextureBrush> object determines how the image is oriented as it is repeated in a rectangular grid.</span></span> <span data-ttu-id="83780-108">您可以進行所有的磚，在方格中有相同的方向，或您可以進行映像從一個格線位置翻轉到下一步。</span><span class="sxs-lookup"><span data-stu-id="83780-108">You can make all the tiles in the grid have the same orientation, or you can make the image flip from one grid position to the next.</span></span> <span data-ttu-id="83780-109">翻轉可以水平、 垂直或兩者。</span><span class="sxs-lookup"><span data-stu-id="83780-109">The flipping can be horizontal, vertical, or both.</span></span> <span data-ttu-id="83780-110">下列範例示範使用不同的開關來並排顯示。</span><span class="sxs-lookup"><span data-stu-id="83780-110">The following examples demonstrate tiling with different types of flipping.</span></span>  
  
### <a name="to-tile-an-image"></a><span data-ttu-id="83780-111">若要並排顯示影像</span><span class="sxs-lookup"><span data-stu-id="83780-111">To tile an image</span></span>  
  
-   <span data-ttu-id="83780-112">這個範例會使用下列 75 × 75 映像來並排顯示 200 × 200 的矩形。</span><span class="sxs-lookup"><span data-stu-id="83780-112">This example uses the following 75×75 image to tile a 200×200 rectangle.</span></span>  
  
 <span data-ttu-id="83780-113">![菾拏 1](../../../../docs/framework/winforms/advanced/media/tile1.gif "tile1")</span><span class="sxs-lookup"><span data-stu-id="83780-113">![Tile 1](../../../../docs/framework/winforms/advanced/media/tile1.gif "tile1")</span></span>  
  
-   <span data-ttu-id="83780-114">下圖顯示如何與影像並排顯示矩形。</span><span class="sxs-lookup"><span data-stu-id="83780-114">The following illustration shows how the rectangle is tiled with the image.</span></span> <span data-ttu-id="83780-115">請注意，所有圖格都具有相同的方向。沒有任何翻轉。</span><span class="sxs-lookup"><span data-stu-id="83780-115">Note that all tiles have the same orientation; there is no flipping.</span></span>  
  
 <span data-ttu-id="83780-116">![磚 2](../../../../docs/framework/winforms/advanced/media/tile2.gif "tile2")</span><span class="sxs-lookup"><span data-stu-id="83780-116">![Tile 2](../../../../docs/framework/winforms/advanced/media/tile2.gif "tile2")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingABrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#31)]  
  
### <a name="to-flip-an-image-horizontally-while-tiling"></a><span data-ttu-id="83780-117">若要翻轉並排顯示時的水平影像</span><span class="sxs-lookup"><span data-stu-id="83780-117">To flip an image horizontally while tiling</span></span>  
  
-   <span data-ttu-id="83780-118">這個範例會使用相同 75 × 75 影像以填滿 200 × 200 的矩形。</span><span class="sxs-lookup"><span data-stu-id="83780-118">This example uses the same 75×75 image to fill a 200×200 rectangle.</span></span> <span data-ttu-id="83780-119">換行模式設定為水平翻轉影像。</span><span class="sxs-lookup"><span data-stu-id="83780-119">The wrap mode is set to flip the image horizontally.</span></span> <span data-ttu-id="83780-120">下圖顯示如何與影像並排顯示矩形。</span><span class="sxs-lookup"><span data-stu-id="83780-120">The following illustration shows how the rectangle is tiled with the image.</span></span> <span data-ttu-id="83780-121">請注意，當您從一個磚移至給定的資料列在下一步，水平翻轉影像。</span><span class="sxs-lookup"><span data-stu-id="83780-121">Note that as you move from one tile to the next in a given row, the image is flipped horizontally.</span></span>  
  
 <span data-ttu-id="83780-122">![磚 3](../../../../docs/framework/winforms/advanced/media/tile3.gif "tile3")</span><span class="sxs-lookup"><span data-stu-id="83780-122">![Tile 3](../../../../docs/framework/winforms/advanced/media/tile3.gif "tile3")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.UsingABrush#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#32)]  
  
### <a name="to-flip-an-image-vertically-while-tiling"></a><span data-ttu-id="83780-123">若要翻轉垂直在並排顯示時的映像</span><span class="sxs-lookup"><span data-stu-id="83780-123">To flip an image vertically while tiling</span></span>  
  
-   <span data-ttu-id="83780-124">這個範例會使用相同 75 × 75 影像以填滿 200 × 200 的矩形。</span><span class="sxs-lookup"><span data-stu-id="83780-124">This example uses the same 75×75 image to fill a 200×200 rectangle.</span></span> <span data-ttu-id="83780-125">換行模式設定為垂直翻轉影像。</span><span class="sxs-lookup"><span data-stu-id="83780-125">The wrap mode is set to flip the image vertically.</span></span>  
  
     [!code-csharp[System.Drawing.UsingABrush#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#33)]
     [!code-vb[System.Drawing.UsingABrush#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#33)]  
  
### <a name="to-flip-an-image-horizontally-and-vertically-while-tiling"></a><span data-ttu-id="83780-126">若要在並排顯示時水平及垂直翻轉影像</span><span class="sxs-lookup"><span data-stu-id="83780-126">To flip an image horizontally and vertically while tiling</span></span>  
  
-   <span data-ttu-id="83780-127">這個範例會使用相同的 75 × 75 映像來並排顯示 200 × 200 的矩形。</span><span class="sxs-lookup"><span data-stu-id="83780-127">This example uses the same 75×75 image to tile a 200×200 rectangle.</span></span> <span data-ttu-id="83780-128">換行模式設定為水平及垂直翻轉影像。</span><span class="sxs-lookup"><span data-stu-id="83780-128">The wrap mode is set to flip the image both horizontally and vertically.</span></span> <span data-ttu-id="83780-129">下圖顯示矩形影像如何並排顯示。</span><span class="sxs-lookup"><span data-stu-id="83780-129">The following illustration shows how the rectangle is tiled by the image.</span></span> <span data-ttu-id="83780-130">請注意，當您從一個磚移動到給定的資料列中的下一個水平翻轉影像，當您從一個磚移動到給定的資料行中的下，垂直翻轉影像。</span><span class="sxs-lookup"><span data-stu-id="83780-130">Note that as you move from one tile to the next in a given row, the image is flipped horizontally, and as you move from one tile to the next in a given column, the image is flipped vertically.</span></span>  
  
 <span data-ttu-id="83780-131">![磚 5](../../../../docs/framework/winforms/advanced/media/tile5.gif "tile5")</span><span class="sxs-lookup"><span data-stu-id="83780-131">![Tile 5](../../../../docs/framework/winforms/advanced/media/tile5.gif "tile5")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.UsingABrush#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="83780-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="83780-132">See Also</span></span>  
 [<span data-ttu-id="83780-133">使用筆刷填滿形狀</span><span class="sxs-lookup"><span data-stu-id="83780-133">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
