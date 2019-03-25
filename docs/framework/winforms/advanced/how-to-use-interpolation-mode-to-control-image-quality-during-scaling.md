---
title: HOW TO：在調整期間使用插補法模式控制影像品質
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interpolation mode [Windows Forms], controlling image quality
- images [Windows Forms], scaling
- images [Windows Forms], controlling quality
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
ms.openlocfilehash: 93430f521904d9d38ba98f4055480583fd650114
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410364"
---
# <a name="how-to-use-interpolation-mode-to-control-image-quality-during-scaling"></a><span data-ttu-id="60b15-102">HOW TO：在調整期間使用插補法模式控制影像品質</span><span class="sxs-lookup"><span data-stu-id="60b15-102">How to: Use Interpolation Mode to Control Image Quality During Scaling</span></span>
<span data-ttu-id="60b15-103">插補模式<xref:System.Drawing.Graphics>物件會影響方式[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]標尺 （兩端之間自動縮放和壓縮） 映像。</span><span class="sxs-lookup"><span data-stu-id="60b15-103">The interpolation mode of a <xref:System.Drawing.Graphics> object influences the way [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] scales (stretches and shrinks) images.</span></span> <span data-ttu-id="60b15-104"><xref:System.Drawing.Drawing2D.InterpolationMode>列舉會定義數種插補模式，其中有些下列清單所示：</span><span class="sxs-lookup"><span data-stu-id="60b15-104">The <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration defines several interpolation modes, some of which are shown in the following list:</span></span>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bicubic>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>  
  
 <span data-ttu-id="60b15-105">要延展影像，原始的映像中的每個像素必須對應到較大的映像中的像素的群組。</span><span class="sxs-lookup"><span data-stu-id="60b15-105">To stretch an image, each pixel in the original image must be mapped to a group of pixels in the larger image.</span></span> <span data-ttu-id="60b15-106">若要壓縮映像，原始的映像中的像素的群組必須對應到較小的映像中的單一像素為單位。</span><span class="sxs-lookup"><span data-stu-id="60b15-106">To shrink an image, groups of pixels in the original image must be mapped to single pixels in the smaller image.</span></span> <span data-ttu-id="60b15-107">執行這些對應的演算法的效率會決定縮放的影像品質。</span><span class="sxs-lookup"><span data-stu-id="60b15-107">The effectiveness of the algorithms that perform these mappings determines the quality of a scaled image.</span></span> <span data-ttu-id="60b15-108">演算法會產生較高品質縮放的影像通常需要更多的處理時間。</span><span class="sxs-lookup"><span data-stu-id="60b15-108">Algorithms that produce higher-quality scaled images tend to require more processing time.</span></span> <span data-ttu-id="60b15-109">在上述清單中，<xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>是最低品質模式和<xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>是最高品質的模式。</span><span class="sxs-lookup"><span data-stu-id="60b15-109">In the preceding list, <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> is the lowest-quality mode and <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> is the highest-quality mode.</span></span>  
  
 <span data-ttu-id="60b15-110">若要設定的插補模式，將指派的成員<xref:System.Drawing.Drawing2D.InterpolationMode>列舉型別<xref:System.Drawing.Graphics.InterpolationMode%2A>屬性<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="60b15-110">To set the interpolation mode, assign one of the members of the <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration to the <xref:System.Drawing.Graphics.InterpolationMode%2A> property of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60b15-111">範例</span><span class="sxs-lookup"><span data-stu-id="60b15-111">Example</span></span>  
 <span data-ttu-id="60b15-112">下列範例會繪製影像，然後再壓縮具有三種不同的插補模式的映像。</span><span class="sxs-lookup"><span data-stu-id="60b15-112">The following example draws an image and then shrinks the image with three different interpolation modes.</span></span>  
  
 <span data-ttu-id="60b15-113">下圖顯示原始的映像和三個較小的影像。</span><span class="sxs-lookup"><span data-stu-id="60b15-113">The following illustration shows the original image and the three smaller images.</span></span>  
  
 ![如果螢幕擷取畫面顯示具有各種插補設定的影像。](./media/how-to-use-interpolation-mode-to-control-image-quality-during-scaling/varied-interpolation-settings.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="60b15-115">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="60b15-115">Compiling the Code</span></span>  
 <span data-ttu-id="60b15-116">上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="60b15-116">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60b15-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60b15-117">See also</span></span>
- [<span data-ttu-id="60b15-118">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="60b15-118">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="60b15-119">使用影像、點陣圖、圖示和中繼檔</span><span class="sxs-lookup"><span data-stu-id="60b15-119">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
