---
title: HOW TO：使用色彩矩陣轉換單一色彩
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image colors [Windows Forms], transforming
- color matrices [Windows Forms], using
ms.assetid: 44df4556-a433-49c0-ac0f-9a12063a5860
ms.openlocfilehash: 9cff13cabb0cd496ee4e628664e4b92bd9e60808
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063725"
---
# <a name="how-to-use-a-color-matrix-to-transform-a-single-color"></a><span data-ttu-id="54ca6-102">HOW TO：使用色彩矩陣轉換單一色彩</span><span class="sxs-lookup"><span data-stu-id="54ca6-102">How to: Use a Color Matrix to Transform a Single Color</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="54ca6-103">提供<xref:System.Drawing.Image>和<xref:System.Drawing.Bitmap>來儲存及操作影像的類別。</span><span class="sxs-lookup"><span data-stu-id="54ca6-103">provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <span data-ttu-id="54ca6-104"><xref:System.Drawing.Image> 和<xref:System.Drawing.Bitmap>物件會儲存每個像素的色彩為 32 位元數字：8 位元用於紅色、 綠色、 藍色和 alpha 的每個。</span><span class="sxs-lookup"><span data-stu-id="54ca6-104"><xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> objects store the color of each pixel as a 32-bit number: 8 bits each for red, green, blue, and alpha.</span></span> <span data-ttu-id="54ca6-105">每四個元件是從 0 到 255，0 代表不含濃度，表示完整濃度 255 的數字。</span><span class="sxs-lookup"><span data-stu-id="54ca6-105">Each of the four components is a number from 0 through 255, with 0 representing no intensity and 255 representing full intensity.</span></span> <span data-ttu-id="54ca6-106">Alpha 元件指定色彩的透明度：0 是完全透明的而且完全不透明 255。</span><span class="sxs-lookup"><span data-stu-id="54ca6-106">The alpha component specifies the transparency of the color: 0 is fully transparent, and 255 is fully opaque.</span></span>  
  
 <span data-ttu-id="54ca6-107">色彩向量是表單 （紅色、 綠色、 藍色、 alpha） 的 4-tuple。</span><span class="sxs-lookup"><span data-stu-id="54ca6-107">A color vector is a 4-tuple of the form (red, green, blue, alpha).</span></span> <span data-ttu-id="54ca6-108">例如，色彩向量 （0，255，0，255） 表示不透明的色彩，含紅色或藍色，但有綠色的濃度。</span><span class="sxs-lookup"><span data-stu-id="54ca6-108">For example, the color vector (0, 255, 0, 255) represents an opaque color that has no red or blue, but has green at full intensity.</span></span>  
  
 <span data-ttu-id="54ca6-109">表示色彩的另一個慣例會將數字 1 用於完整濃度。</span><span class="sxs-lookup"><span data-stu-id="54ca6-109">Another convention for representing colors uses the number 1 for full intensity.</span></span> <span data-ttu-id="54ca6-110">使用這個慣例，會由向量 （0、 1、 0、 1） 表示前面段落中所述的色彩。</span><span class="sxs-lookup"><span data-stu-id="54ca6-110">Using that convention, the color described in the preceding paragraph would be represented by the vector (0, 1, 0, 1).</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="54ca6-111">會使用 1 慣例成完整濃度，當它執行色彩轉換。</span><span class="sxs-lookup"><span data-stu-id="54ca6-111">uses the convention of 1 as full intensity when it performs color transformations.</span></span>  
  
 <span data-ttu-id="54ca6-112">您可以套用色彩向量線性轉換 （旋轉、 縮放和 like） 乘以 4 × 4 矩陣色彩向量。</span><span class="sxs-lookup"><span data-stu-id="54ca6-112">You can apply linear transformations (rotation, scaling, and the like) to color vectors by multiplying the color vectors by a 4×4 matrix.</span></span> <span data-ttu-id="54ca6-113">不過，您無法使用 4 × 4 矩陣，以執行翻譯 （非線性）。</span><span class="sxs-lookup"><span data-stu-id="54ca6-113">However, you cannot use a 4×4 matrix to perform a translation (nonlinear).</span></span> <span data-ttu-id="54ca6-114">如果您將虛擬的第五個座標 （例如，數字 1） 加入每一個色彩向量時，您可以使用 5 × 5 矩陣来套用的線性轉換和轉譯的任意組合。</span><span class="sxs-lookup"><span data-stu-id="54ca6-114">If you add a dummy fifth coordinate (for example, the number 1) to each of the color vectors, you can use a 5×5 matrix to apply any combination of linear transformations and translations.</span></span> <span data-ttu-id="54ca6-115">轉換，其中包含後面接著翻譯的線性轉換稱為仿射轉換。</span><span class="sxs-lookup"><span data-stu-id="54ca6-115">A transformation consisting of a linear transformation followed by a translation is called an affine transformation.</span></span>  
  
 <span data-ttu-id="54ca6-116">例如，假設您想要開始色彩 （0.2，0.0、 0.4，1.0），並套用下列轉換：</span><span class="sxs-lookup"><span data-stu-id="54ca6-116">For example, suppose you want to start with the color (0.2, 0.0, 0.4, 1.0) and apply the following transformations:</span></span>  
  
1. <span data-ttu-id="54ca6-117">雙重紅色元件</span><span class="sxs-lookup"><span data-stu-id="54ca6-117">Double the red component</span></span>  
  
2. <span data-ttu-id="54ca6-118">加上紅色、 綠色和藍色元件 0.2</span><span class="sxs-lookup"><span data-stu-id="54ca6-118">Add 0.2 to the red, green, and blue components</span></span>  
  
 <span data-ttu-id="54ca6-119">下列矩陣乘法會依列出的順序執行成對的轉換。</span><span class="sxs-lookup"><span data-stu-id="54ca6-119">The following matrix multiplication will perform the pair of transformations in the order listed.</span></span>  
  
 ![轉換矩陣乘法螢幕擷取畫面。](./media/how-to-use-a-color-matrix-to-transform-a-single-color/multiplication-color-matrix.gif)
  
 <span data-ttu-id="54ca6-121">色彩矩陣的項目編製索引 （以零為起始） 的資料列，然後資料行。</span><span class="sxs-lookup"><span data-stu-id="54ca6-121">The elements of a color matrix are indexed (zero-based) by row and then column.</span></span> <span data-ttu-id="54ca6-122">比方說，第五個資料列和第三個資料行的矩陣 M 中的項目被以 M [4] [2]。</span><span class="sxs-lookup"><span data-stu-id="54ca6-122">For example, the entry in the fifth row and third column of matrix M is denoted by M[4][2].</span></span>  
  
 <span data-ttu-id="54ca6-123">5 × 5 身分識別矩陣 （下圖所示） 具有對角線上的 1 和 0 的其他位置。</span><span class="sxs-lookup"><span data-stu-id="54ca6-123">The 5×5 identity matrix (shown in the following illustration) has 1s on the diagonal and 0s everywhere else.</span></span> <span data-ttu-id="54ca6-124">如果您將色彩向量乘以身分識別矩陣時，就不會變更色彩的向量。</span><span class="sxs-lookup"><span data-stu-id="54ca6-124">If you multiply a color vector by the identity matrix, the color vector does not change.</span></span> <span data-ttu-id="54ca6-125">便利的方式來形成 「 色彩 」 轉換的矩陣是以身分識別矩陣開始進行小幅變更會產生所需的轉換。</span><span class="sxs-lookup"><span data-stu-id="54ca6-125">A convenient way to form the matrix of a color transformation is to start with the identity matrix and make a small change that produces the desired transformation.</span></span>  
  
 ![螢幕擷取畫面 5 x 5 身分識別矩陣的色彩轉換。](./media/how-to-use-a-color-matrix-to-transform-a-single-color/5x5-identity-matrix-color-transformation.gif)  
  
 <span data-ttu-id="54ca6-127">矩陣和轉換的詳細討論，請參閱[座標系統和轉換](coordinate-systems-and-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="54ca6-127">For a more detailed discussion of matrices and transformations, see [Coordinate Systems and Transformations](coordinate-systems-and-transformations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="54ca6-128">範例</span><span class="sxs-lookup"><span data-stu-id="54ca6-128">Example</span></span>  
 <span data-ttu-id="54ca6-129">下列範例會為所有的一種色彩 （0.2，0.0、 0.4，1.0） 與先前段落中所述的轉換套用的映像。</span><span class="sxs-lookup"><span data-stu-id="54ca6-129">The following example takes an image that is all one color (0.2, 0.0, 0.4, 1.0) and applies the transformation described in the preceding paragraphs.</span></span>  
  
 <span data-ttu-id="54ca6-130">下圖顯示原始的映像，在左邊和轉換後的映像，在右邊。</span><span class="sxs-lookup"><span data-stu-id="54ca6-130">The following illustration shows the original image on the left and the transformed image on the right.</span></span>  
  
 ![在左邊和右邊粉色正方形紫色正方形。](./media/how-to-use-a-color-matrix-to-transform-a-single-color/color-transformation.png)  
  
 <span data-ttu-id="54ca6-132">下列範例中的程式碼會使用下列步驟執行的重新著色：</span><span class="sxs-lookup"><span data-stu-id="54ca6-132">The code in the following example uses the following steps to perform the recoloring:</span></span>  
  
1. <span data-ttu-id="54ca6-133">初始化<xref:System.Drawing.Imaging.ColorMatrix>物件。</span><span class="sxs-lookup"><span data-stu-id="54ca6-133">Initialize a <xref:System.Drawing.Imaging.ColorMatrix> object.</span></span>  
  
2. <span data-ttu-id="54ca6-134">建立<xref:System.Drawing.Imaging.ImageAttributes>物件，並傳遞<xref:System.Drawing.Imaging.ColorMatrix>物件<xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A>方法<xref:System.Drawing.Imaging.ImageAttributes>物件。</span><span class="sxs-lookup"><span data-stu-id="54ca6-134">Create an <xref:System.Drawing.Imaging.ImageAttributes> object and pass the <xref:System.Drawing.Imaging.ColorMatrix> object to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object.</span></span>  
  
3. <span data-ttu-id="54ca6-135">傳遞<xref:System.Drawing.Imaging.ImageAttributes>物件至<xref:System.Drawing.Graphics.DrawImage%2A>方法<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="54ca6-135">Pass the <xref:System.Drawing.Imaging.ImageAttributes> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.RecoloringImages#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="54ca6-136">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="54ca6-136">Compiling the Code</span></span>  
 <span data-ttu-id="54ca6-137">上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="54ca6-137">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54ca6-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54ca6-138">See also</span></span>

- [<span data-ttu-id="54ca6-139">為影像重新著色</span><span class="sxs-lookup"><span data-stu-id="54ca6-139">Recoloring Images</span></span>](recoloring-images.md)
- [<span data-ttu-id="54ca6-140">座標系統和轉換</span><span class="sxs-lookup"><span data-stu-id="54ca6-140">Coordinate Systems and Transformations</span></span>](coordinate-systems-and-transformations.md)
