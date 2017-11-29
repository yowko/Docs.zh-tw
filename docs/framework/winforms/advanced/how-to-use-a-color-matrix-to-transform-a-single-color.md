---
title: "如何：使用色彩矩陣轉換單一色彩"
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
- image colors [Windows Forms], transforming
- color matrices [Windows Forms], using
ms.assetid: 44df4556-a433-49c0-ac0f-9a12063a5860
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 60da29b60d2b9b5b98c76a0a9c3ae73ac9142bbd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-color-matrix-to-transform-a-single-color"></a><span data-ttu-id="b52df-102">如何：使用色彩矩陣轉換單一色彩</span><span class="sxs-lookup"><span data-stu-id="b52df-102">How to: Use a Color Matrix to Transform a Single Color</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="b52df-103">提供<xref:System.Drawing.Image>和<xref:System.Drawing.Bitmap>類別來儲存和管理影像。</span><span class="sxs-lookup"><span data-stu-id="b52df-103"> provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <span data-ttu-id="b52df-104"><xref:System.Drawing.Image>和<xref:System.Drawing.Bitmap>物件會儲存每個像素色彩的 32 位元數字： 8 位元每個紅色、 綠色、 藍色及 alpha。</span><span class="sxs-lookup"><span data-stu-id="b52df-104"><xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> objects store the color of each pixel as a 32-bit number: 8 bits each for red, green, blue, and alpha.</span></span> <span data-ttu-id="b52df-105">四個元件的每一個都是從 0 到 255，0 代表不含濃度，代表完整的濃度 255 的數字。</span><span class="sxs-lookup"><span data-stu-id="b52df-105">Each of the four components is a number from 0 through 255, with 0 representing no intensity and 255 representing full intensity.</span></span> <span data-ttu-id="b52df-106">Alpha 元件指定色彩的透明度： 0 是完全透明，而 255 是完全不透明。</span><span class="sxs-lookup"><span data-stu-id="b52df-106">The alpha component specifies the transparency of the color: 0 is fully transparent, and 255 is fully opaque.</span></span>  
  
 <span data-ttu-id="b52df-107">色彩向量是紅色、 綠色、 藍色 （alpha） 格式的 4 tuple。</span><span class="sxs-lookup"><span data-stu-id="b52df-107">A color vector is a 4-tuple of the form (red, green, blue, alpha).</span></span> <span data-ttu-id="b52df-108">例如，色彩向量 （0，255，0，255） 代表不透明的色彩，含紅色或藍色，但有綠色的濃度。</span><span class="sxs-lookup"><span data-stu-id="b52df-108">For example, the color vector (0, 255, 0, 255) represents an opaque color that has no red or blue, but has green at full intensity.</span></span>  
  
 <span data-ttu-id="b52df-109">表示色彩的另一個慣例是使用數字 1 的完整的濃度。</span><span class="sxs-lookup"><span data-stu-id="b52df-109">Another convention for representing colors uses the number 1 for full intensity.</span></span> <span data-ttu-id="b52df-110">使用這個慣例，在上一段所述的色彩則表示向量 （0、 1、 0，1）。</span><span class="sxs-lookup"><span data-stu-id="b52df-110">Using that convention, the color described in the preceding paragraph would be represented by the vector (0, 1, 0, 1).</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="b52df-111">當它執行色彩轉換會使用 1 的慣例為完整的濃度。</span><span class="sxs-lookup"><span data-stu-id="b52df-111"> uses the convention of 1 as full intensity when it performs color transformations.</span></span>  
  
 <span data-ttu-id="b52df-112">您可以套用到色彩向量的線性轉換 （旋轉、 調整及 like） 乘以 4 × 4 矩陣的色彩向量。</span><span class="sxs-lookup"><span data-stu-id="b52df-112">You can apply linear transformations (rotation, scaling, and the like) to color vectors by multiplying the color vectors by a 4×4 matrix.</span></span> <span data-ttu-id="b52df-113">不過，您無法使用 4 × 4 矩陣，來執行 （「 非線性的 」） 的翻譯。</span><span class="sxs-lookup"><span data-stu-id="b52df-113">However, you cannot use a 4×4 matrix to perform a translation (nonlinear).</span></span> <span data-ttu-id="b52df-114">如果您將空的第五個座標 （例如，數字 1） 加入每一個色彩向量，您可以使用 5 × 5 矩陣來套用線性轉換和翻譯的任意組合。</span><span class="sxs-lookup"><span data-stu-id="b52df-114">If you add a dummy fifth coordinate (for example, the number 1) to each of the color vectors, you can use a 5×5 matrix to apply any combination of linear transformations and translations.</span></span> <span data-ttu-id="b52df-115">包含後面接著翻譯線性轉換稱為仿射轉換。</span><span class="sxs-lookup"><span data-stu-id="b52df-115">A transformation consisting of a linear transformation followed by a translation is called an affine transformation.</span></span>  
  
 <span data-ttu-id="b52df-116">例如，假設您想要使用的色彩 （0.2、 0.0、 0.4、 1.0） 啟動，並套用下列轉換：</span><span class="sxs-lookup"><span data-stu-id="b52df-116">For example, suppose you want to start with the color (0.2, 0.0, 0.4, 1.0) and apply the following transformations:</span></span>  
  
1.  <span data-ttu-id="b52df-117">Double 紅色的元件</span><span class="sxs-lookup"><span data-stu-id="b52df-117">Double the red component</span></span>  
  
2.  <span data-ttu-id="b52df-118">0.2 加入紅色、 綠色和藍色元件</span><span class="sxs-lookup"><span data-stu-id="b52df-118">Add 0.2 to the red, green, and blue components</span></span>  
  
 <span data-ttu-id="b52df-119">下列的矩陣乘法會列出的順序執行成對的轉換。</span><span class="sxs-lookup"><span data-stu-id="b52df-119">The following matrix multiplication will perform the pair of transformations in the order listed.</span></span>  
  
 <span data-ttu-id="b52df-120">![重新著色，以便](../../../../docs/framework/winforms/advanced/media/recoloring01.gif "recoloring01")</span><span class="sxs-lookup"><span data-stu-id="b52df-120">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring01.gif "recoloring01")</span></span>  
  
 <span data-ttu-id="b52df-121">色彩矩陣的項目會依照資料列和資料行索引 （以零為起始）。</span><span class="sxs-lookup"><span data-stu-id="b52df-121">The elements of a color matrix are indexed (zero-based) by row and then column.</span></span> <span data-ttu-id="b52df-122">例如，由 M [4] [2] 表示第五個資料列和第三個資料行的矩陣 M 中的項目。</span><span class="sxs-lookup"><span data-stu-id="b52df-122">For example, the entry in the fifth row and third column of matrix M is denoted by M[4][2].</span></span>  
  
 <span data-ttu-id="b52df-123">5 × 5 身分識別矩陣 （如圖所示） 具有對角線上的 1 和 0 其他位置。</span><span class="sxs-lookup"><span data-stu-id="b52df-123">The 5×5 identity matrix (shown in the following illustration) has 1s on the diagonal and 0s everywhere else.</span></span> <span data-ttu-id="b52df-124">如果您將色彩向量乘以矩陣時，就不會變更色彩向量。</span><span class="sxs-lookup"><span data-stu-id="b52df-124">If you multiply a color vector by the identity matrix, the color vector does not change.</span></span> <span data-ttu-id="b52df-125">便利的方式，以形成色彩轉換的矩陣是單位矩陣以開頭，並且進行小幅變更產生所需的轉換。</span><span class="sxs-lookup"><span data-stu-id="b52df-125">A convenient way to form the matrix of a color transformation is to start with the identity matrix and make a small change that produces the desired transformation.</span></span>  
  
 <span data-ttu-id="b52df-126">![重新著色，以便](../../../../docs/framework/winforms/advanced/media/recoloring02.gif "recoloring02")</span><span class="sxs-lookup"><span data-stu-id="b52df-126">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring02.gif "recoloring02")</span></span>  
  
 <span data-ttu-id="b52df-127">矩陣和轉換的更詳細討論，請參閱[座標系統和轉換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="b52df-127">For a more detailed discussion of matrices and transformations, see [Coordinate Systems and Transformations](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b52df-128">範例</span><span class="sxs-lookup"><span data-stu-id="b52df-128">Example</span></span>  
 <span data-ttu-id="b52df-129">下列範例會為所有的一種色彩 （0.2、 0.0、 0.4、 1.0） 與前面段落中所述的轉換套用的映像。</span><span class="sxs-lookup"><span data-stu-id="b52df-129">The following example takes an image that is all one color (0.2, 0.0, 0.4, 1.0) and applies the transformation described in the preceding paragraphs.</span></span>  
  
 <span data-ttu-id="b52df-130">下圖顯示在右側的原始左側映像，而且已轉換的映像。</span><span class="sxs-lookup"><span data-stu-id="b52df-130">The following illustration shows the original image on the left and the transformed image on the right.</span></span>  
  
 <span data-ttu-id="b52df-131">![色彩](../../../../docs/framework/winforms/advanced/media/colortrans1.png "colortrans1")</span><span class="sxs-lookup"><span data-stu-id="b52df-131">![Colors](../../../../docs/framework/winforms/advanced/media/colortrans1.png "colortrans1")</span></span>  
  
 <span data-ttu-id="b52df-132">下列範例中的程式碼會使用下列步驟執行重新著色，以便：</span><span class="sxs-lookup"><span data-stu-id="b52df-132">The code in the following example uses the following steps to perform the recoloring:</span></span>  
  
1.  <span data-ttu-id="b52df-133">初始化<xref:System.Drawing.Imaging.ColorMatrix>物件。</span><span class="sxs-lookup"><span data-stu-id="b52df-133">Initialize a <xref:System.Drawing.Imaging.ColorMatrix> object.</span></span>  
  
2.  <span data-ttu-id="b52df-134">建立<xref:System.Drawing.Imaging.ImageAttributes>物件，並傳遞<xref:System.Drawing.Imaging.ColorMatrix>物件<xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A>方法<xref:System.Drawing.Imaging.ImageAttributes>物件。</span><span class="sxs-lookup"><span data-stu-id="b52df-134">Create an <xref:System.Drawing.Imaging.ImageAttributes> object and pass the <xref:System.Drawing.Imaging.ColorMatrix> object to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object.</span></span>  
  
3.  <span data-ttu-id="b52df-135">傳遞<xref:System.Drawing.Imaging.ImageAttributes>物件<xref:System.Drawing.Graphics.DrawImage%2A>方法<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="b52df-135">Pass the <xref:System.Drawing.Imaging.ImageAttributes> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.RecoloringImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b52df-136">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b52df-136">Compiling the Code</span></span>  
 <span data-ttu-id="b52df-137">上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="b52df-137">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b52df-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b52df-138">See Also</span></span>  
 [<span data-ttu-id="b52df-139">為影像重新著色</span><span class="sxs-lookup"><span data-stu-id="b52df-139">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 [<span data-ttu-id="b52df-140">座標系統和轉換</span><span class="sxs-lookup"><span data-stu-id="b52df-140">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)
