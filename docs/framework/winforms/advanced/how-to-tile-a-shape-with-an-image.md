---
title: HOW TO：使用影像並排顯示圖案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- texture brushes [Windows Forms], tiling images with
- images [Windows Forms], filling shapes with
- shapes [Windows Forms], tiling with images
- bitmaps [Windows Forms], filling shapes with
ms.assetid: 6d407891-6e5c-4495-a546-3da5604e9fb8
ms.openlocfilehash: ad7b8737a63028e533cadfa6db56b063eb943f22
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221534"
---
# <a name="how-to-tile-a-shape-with-an-image"></a><span data-ttu-id="25973-102">HOW TO：使用影像並排顯示圖案</span><span class="sxs-lookup"><span data-stu-id="25973-102">How to: Tile a Shape with an Image</span></span>
<span data-ttu-id="25973-103">如同可以彼此討論 floor 旁邊放圖格，可以彼此相鄰放矩形的映像，來填滿 (tile) 圖形。</span><span class="sxs-lookup"><span data-stu-id="25973-103">Just as tiles can be placed next to each other to cover a floor, rectangular images can be placed next to each other to fill (tile) a shape.</span></span> <span data-ttu-id="25973-104">若要並排顯示圖案的內部，使用紋理筆刷。</span><span class="sxs-lookup"><span data-stu-id="25973-104">To tile the interior of a shape, use a texture brush.</span></span> <span data-ttu-id="25973-105">當您建構<xref:System.Drawing.TextureBrush>物件時，您將傳遞至建構函式的引數之一<xref:System.Drawing.Image>物件。</span><span class="sxs-lookup"><span data-stu-id="25973-105">When you construct a <xref:System.Drawing.TextureBrush> object, one of the arguments you pass to the constructor is an <xref:System.Drawing.Image> object.</span></span> <span data-ttu-id="25973-106">當您使用的材質筆刷來繪製圖形的內部時，圖形會填入此映像的重複副本。</span><span class="sxs-lookup"><span data-stu-id="25973-106">When you use the texture brush to paint the interior of a shape, the shape is filled with repeated copies of this image.</span></span>  
  
 <span data-ttu-id="25973-107">自動換行模式屬性<xref:System.Drawing.TextureBrush>物件可以決定如何將映像為導向重複矩形格線中。</span><span class="sxs-lookup"><span data-stu-id="25973-107">The wrap mode property of the <xref:System.Drawing.TextureBrush> object determines how the image is oriented as it is repeated in a rectangular grid.</span></span> <span data-ttu-id="25973-108">您可以進行所有的磚，在方格中有相同的方向，或您可從一個格線位置翻轉至下一個映像。</span><span class="sxs-lookup"><span data-stu-id="25973-108">You can make all the tiles in the grid have the same orientation, or you can make the image flip from one grid position to the next.</span></span> <span data-ttu-id="25973-109">翻轉為水平、 垂直或兩者。</span><span class="sxs-lookup"><span data-stu-id="25973-109">The flipping can be horizontal, vertical, or both.</span></span> <span data-ttu-id="25973-110">下列範例示範如何使用不同類型的翻轉並排顯示。</span><span class="sxs-lookup"><span data-stu-id="25973-110">The following examples demonstrate tiling with different types of flipping.</span></span>  
  
### <a name="to-tile-an-image"></a><span data-ttu-id="25973-111">若要並排顯示影像</span><span class="sxs-lookup"><span data-stu-id="25973-111">To tile an image</span></span>  
  
-   <span data-ttu-id="25973-112">此範例會使用下列的 75 × 75 映像，以並排顯示 200 × 200 的矩形。</span><span class="sxs-lookup"><span data-stu-id="25973-112">This example uses the following 75×75 image to tile a 200×200 rectangle.</span></span>  
  
 <span data-ttu-id="25973-113">![圖格 1](./media/tile1.gif "tile1")</span><span class="sxs-lookup"><span data-stu-id="25973-113">![Tile 1](./media/tile1.gif "tile1")</span></span>  
  
-   <span data-ttu-id="25973-114">下圖顯示矩形與影像如何並排顯示。</span><span class="sxs-lookup"><span data-stu-id="25973-114">The following illustration shows how the rectangle is tiled with the image.</span></span> <span data-ttu-id="25973-115">請注意，所有圖格都具有相同的方向;沒有開關。</span><span class="sxs-lookup"><span data-stu-id="25973-115">Note that all tiles have the same orientation; there is no flipping.</span></span>  
  
 <span data-ttu-id="25973-116">![圖格 2](./media/tile2.gif "tile2")</span><span class="sxs-lookup"><span data-stu-id="25973-116">![Tile 2](./media/tile2.gif "tile2")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingABrush#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#31)]  
  
### <a name="to-flip-an-image-horizontally-while-tiling"></a><span data-ttu-id="25973-117">若要翻轉並排顯示時的水平影像</span><span class="sxs-lookup"><span data-stu-id="25973-117">To flip an image horizontally while tiling</span></span>  
  
-   <span data-ttu-id="25973-118">此範例會使用相同的 75 × 75 映像，以填滿 200 × 200 的矩形。</span><span class="sxs-lookup"><span data-stu-id="25973-118">This example uses the same 75×75 image to fill a 200×200 rectangle.</span></span> <span data-ttu-id="25973-119">自動換行模式設定為水平翻轉影像。</span><span class="sxs-lookup"><span data-stu-id="25973-119">The wrap mode is set to flip the image horizontally.</span></span> <span data-ttu-id="25973-120">下圖顯示矩形與影像如何並排顯示。</span><span class="sxs-lookup"><span data-stu-id="25973-120">The following illustration shows how the rectangle is tiled with the image.</span></span> <span data-ttu-id="25973-121">請注意，當從一個圖格移至指定的資料列中的下一步 時，會水平翻轉影像。</span><span class="sxs-lookup"><span data-stu-id="25973-121">Note that as you move from one tile to the next in a given row, the image is flipped horizontally.</span></span>  
  
 <span data-ttu-id="25973-122">![圖格 3](./media/tile3.gif "tile3")</span><span class="sxs-lookup"><span data-stu-id="25973-122">![Tile 3](./media/tile3.gif "tile3")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.UsingABrush#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#32)]  
  
### <a name="to-flip-an-image-vertically-while-tiling"></a><span data-ttu-id="25973-123">若要翻轉垂直在並排顯示時的映像</span><span class="sxs-lookup"><span data-stu-id="25973-123">To flip an image vertically while tiling</span></span>  
  
-   <span data-ttu-id="25973-124">此範例會使用相同的 75 × 75 映像，以填滿 200 × 200 的矩形。</span><span class="sxs-lookup"><span data-stu-id="25973-124">This example uses the same 75×75 image to fill a 200×200 rectangle.</span></span> <span data-ttu-id="25973-125">自動換行模式設定為垂直翻轉影像。</span><span class="sxs-lookup"><span data-stu-id="25973-125">The wrap mode is set to flip the image vertically.</span></span>  
  
     [!code-csharp[System.Drawing.UsingABrush#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#33)]
     [!code-vb[System.Drawing.UsingABrush#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#33)]  
  
### <a name="to-flip-an-image-horizontally-and-vertically-while-tiling"></a><span data-ttu-id="25973-126">若要在並排顯示時水平及垂直翻轉影像</span><span class="sxs-lookup"><span data-stu-id="25973-126">To flip an image horizontally and vertically while tiling</span></span>  
  
-   <span data-ttu-id="25973-127">此範例會使用相同的 75 × 75 映像，以並排顯示 200 × 200 的矩形。</span><span class="sxs-lookup"><span data-stu-id="25973-127">This example uses the same 75×75 image to tile a 200×200 rectangle.</span></span> <span data-ttu-id="25973-128">自動換行模式設定為以水平和垂直翻轉影像。</span><span class="sxs-lookup"><span data-stu-id="25973-128">The wrap mode is set to flip the image both horizontally and vertically.</span></span> <span data-ttu-id="25973-129">下圖顯示矩形的影像如何並排顯示。</span><span class="sxs-lookup"><span data-stu-id="25973-129">The following illustration shows how the rectangle is tiled by the image.</span></span> <span data-ttu-id="25973-130">請注意，您從一個圖格移至下一步 指定的資料列中，水平翻轉影像，並當從一個圖格移至指定的資料行中的下一步 時，要以垂直方式翻轉影像。</span><span class="sxs-lookup"><span data-stu-id="25973-130">Note that as you move from one tile to the next in a given row, the image is flipped horizontally, and as you move from one tile to the next in a given column, the image is flipped vertically.</span></span>  
  
 <span data-ttu-id="25973-131">![圖格 5](./media/tile5.gif "tile5")</span><span class="sxs-lookup"><span data-stu-id="25973-131">![Tile 5](./media/tile5.gif "tile5")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.UsingABrush#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="25973-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25973-132">See also</span></span>

- [<span data-ttu-id="25973-133">使用筆刷填滿形狀</span><span class="sxs-lookup"><span data-stu-id="25973-133">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
