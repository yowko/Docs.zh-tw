---
title: HOW TO：旋轉、 反射和傾斜影像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], reflecting
- images [Windows Forms], rotating
- images [Windows Forms], skewing
ms.assetid: a3bf97eb-63ed-425a-ba07-dcc65efb567c
ms.openlocfilehash: 3e539f41667edb505269fe420396c79b68f34e8f
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711495"
---
# <a name="how-to-rotate-reflect-and-skew-images"></a><span data-ttu-id="9242c-102">HOW TO：旋轉、 反射和傾斜影像</span><span class="sxs-lookup"><span data-stu-id="9242c-102">How to: Rotate, Reflect, and Skew Images</span></span>
<span data-ttu-id="9242c-103">您可以旋轉、 反射和傾斜影像藉由指定之左上角、 右上方和左下角邊角原始映像的目的點。</span><span class="sxs-lookup"><span data-stu-id="9242c-103">You can rotate, reflect, and skew an image by specifying destination points for the upper-left, upper-right, and lower-left corners of the original image.</span></span> <span data-ttu-id="9242c-104">這三個目的點決定仿射轉換，原始的矩形映像會對應至平行四邊形。</span><span class="sxs-lookup"><span data-stu-id="9242c-104">The three destination points determine an affine transformation that maps the original rectangular image to a parallelogram.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9242c-105">範例</span><span class="sxs-lookup"><span data-stu-id="9242c-105">Example</span></span>  
 <span data-ttu-id="9242c-106">例如，假設原始的映像會在左上角的矩形 （0，0），在右上角 （100，0），並在左下角 （0，50）。</span><span class="sxs-lookup"><span data-stu-id="9242c-106">For example, suppose the original image is a rectangle with upper-left corner at (0, 0), upper-right corner at (100, 0), and lower-left corner at (0, 50).</span></span> <span data-ttu-id="9242c-107">現在假設您將這些對應三個點至目的地點，如下所示。</span><span class="sxs-lookup"><span data-stu-id="9242c-107">Now suppose you map those three points to destination points as follows.</span></span>  
  
|<span data-ttu-id="9242c-108">原始的點</span><span class="sxs-lookup"><span data-stu-id="9242c-108">Original point</span></span>|<span data-ttu-id="9242c-109">目的地點</span><span class="sxs-lookup"><span data-stu-id="9242c-109">Destination point</span></span>|  
|--------------------|-----------------------|  
|<span data-ttu-id="9242c-110">左上角 （0，0）</span><span class="sxs-lookup"><span data-stu-id="9242c-110">Upper-left (0, 0)</span></span>|<span data-ttu-id="9242c-111">(200, 20)</span><span class="sxs-lookup"><span data-stu-id="9242c-111">(200, 20)</span></span>|  
|<span data-ttu-id="9242c-112">右上方 （100，0）</span><span class="sxs-lookup"><span data-stu-id="9242c-112">Upper-right (100, 0)</span></span>|<span data-ttu-id="9242c-113">(110, 100)</span><span class="sxs-lookup"><span data-stu-id="9242c-113">(110, 100)</span></span>|  
|<span data-ttu-id="9242c-114">左下角 （0，50）</span><span class="sxs-lookup"><span data-stu-id="9242c-114">Lower-left (0, 50)</span></span>|<span data-ttu-id="9242c-115">(250, 30)</span><span class="sxs-lookup"><span data-stu-id="9242c-115">(250, 30)</span></span>|  
  
 <span data-ttu-id="9242c-116">下圖顯示原始的映像和對應的平行四邊形的映像。</span><span class="sxs-lookup"><span data-stu-id="9242c-116">The following illustration shows the original image and the image mapped to the parallelogram.</span></span> <span data-ttu-id="9242c-117">原始的映像具有已扭曲、 反映、 旋轉和轉譯。</span><span class="sxs-lookup"><span data-stu-id="9242c-117">The original image has been skewed, reflected, rotated, and translated.</span></span> <span data-ttu-id="9242c-118">原始的映像的上邊緣的 x 軸會對應到執行的那一行 （200，20） 和 （110，100）。</span><span class="sxs-lookup"><span data-stu-id="9242c-118">The x-axis along the top edge of the original image is mapped to the line that runs through (200, 20) and (110, 100).</span></span> <span data-ttu-id="9242c-119">原始的映像的左邊緣沿著 y 軸會對應到執行的那一行 （200，20） 和 250 (30）。</span><span class="sxs-lookup"><span data-stu-id="9242c-119">The y-axis along the left edge of the original image is mapped to the line that runs through (200, 20) and (250, 30).</span></span>  
  
 <span data-ttu-id="9242c-120">![等量分散](./media/stripes1.gif "Stripes1")</span><span class="sxs-lookup"><span data-stu-id="9242c-120">![Stripes](./media/stripes1.gif "Stripes1")</span></span>  
  
 <span data-ttu-id="9242c-121">下圖類似的轉換套用至相片的映像。</span><span class="sxs-lookup"><span data-stu-id="9242c-121">The following illustration shows a similar transformation applied to a photographic image.</span></span>  
  
 <span data-ttu-id="9242c-122">![轉換的 Climber](./media/transformedclimber.png "TransformedClimber")</span><span class="sxs-lookup"><span data-stu-id="9242c-122">![Transformed Climber](./media/transformedclimber.png "TransformedClimber")</span></span>  
  
 <span data-ttu-id="9242c-123">下圖類似的轉換套用至中繼檔。</span><span class="sxs-lookup"><span data-stu-id="9242c-123">The following illustration shows a similar transformation applied to a metafile.</span></span>  
  
 <span data-ttu-id="9242c-124">![轉換中繼檔](./media/transformedmetafile.png "TransformedMetafile")</span><span class="sxs-lookup"><span data-stu-id="9242c-124">![Transformed Metafile](./media/transformedmetafile.png "TransformedMetafile")</span></span>  
  
 <span data-ttu-id="9242c-125">下列範例會產生的第一個圖例中顯示的映像。</span><span class="sxs-lookup"><span data-stu-id="9242c-125">The following example produces the images shown in the first illustration.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.WorkingWithImages#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9242c-126">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="9242c-126">Compiling the Code</span></span>  
 <span data-ttu-id="9242c-127">上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="9242c-127">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="9242c-128">請務必取代`Stripes.bmp`適用於您的系統映像的路徑。</span><span class="sxs-lookup"><span data-stu-id="9242c-128">Make sure to replace `Stripes.bmp` with the path to an image that is valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9242c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9242c-129">See also</span></span>
- [<span data-ttu-id="9242c-130">使用影像、點陣圖、圖示和中繼檔</span><span class="sxs-lookup"><span data-stu-id="9242c-130">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
