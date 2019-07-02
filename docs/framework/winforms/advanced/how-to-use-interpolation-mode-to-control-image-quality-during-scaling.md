---
title: 作法：縮放期間使用插補模式控制影像品質
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interpolation mode [Windows Forms], controlling image quality
- images [Windows Forms], scaling
- images [Windows Forms], controlling quality
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
ms.openlocfilehash: ab0ff93b3ee26467c0de448efd31b698167f95c2
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505708"
---
# <a name="how-to-use-interpolation-mode-to-control-image-quality-during-scaling"></a><span data-ttu-id="e172f-102">HOW TO：縮放期間使用插補模式控制影像品質</span><span class="sxs-lookup"><span data-stu-id="e172f-102">How to: Use Interpolation Mode to Control Image Quality During Scaling</span></span>
<span data-ttu-id="e172f-103">插補模式<xref:System.Drawing.Graphics>物件影響的方式 GDI + （兩端之間自動縮放和壓縮） 的標尺映像。</span><span class="sxs-lookup"><span data-stu-id="e172f-103">The interpolation mode of a <xref:System.Drawing.Graphics> object influences the way GDI+ scales (stretches and shrinks) images.</span></span> <span data-ttu-id="e172f-104"><xref:System.Drawing.Drawing2D.InterpolationMode>列舉會定義數種插補模式，其中有些下列清單所示：</span><span class="sxs-lookup"><span data-stu-id="e172f-104">The <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration defines several interpolation modes, some of which are shown in the following list:</span></span>  
  
- <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>  
  
- <xref:System.Drawing.Drawing2D.InterpolationMode.Bilinear>  
  
- <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBilinear>  
  
- <xref:System.Drawing.Drawing2D.InterpolationMode.Bicubic>  
  
- <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>  
  
 <span data-ttu-id="e172f-105">要延展影像，原始的映像中的每個像素必須對應到較大的映像中的像素的群組。</span><span class="sxs-lookup"><span data-stu-id="e172f-105">To stretch an image, each pixel in the original image must be mapped to a group of pixels in the larger image.</span></span> <span data-ttu-id="e172f-106">若要壓縮映像，原始的映像中的像素的群組必須對應到較小的映像中的單一像素為單位。</span><span class="sxs-lookup"><span data-stu-id="e172f-106">To shrink an image, groups of pixels in the original image must be mapped to single pixels in the smaller image.</span></span> <span data-ttu-id="e172f-107">執行這些對應的演算法的效率會決定縮放的影像品質。</span><span class="sxs-lookup"><span data-stu-id="e172f-107">The effectiveness of the algorithms that perform these mappings determines the quality of a scaled image.</span></span> <span data-ttu-id="e172f-108">演算法會產生較高品質縮放的影像通常需要更多的處理時間。</span><span class="sxs-lookup"><span data-stu-id="e172f-108">Algorithms that produce higher-quality scaled images tend to require more processing time.</span></span> <span data-ttu-id="e172f-109">在上述清單中，<xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>是最低品質模式和<xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>是最高品質的模式。</span><span class="sxs-lookup"><span data-stu-id="e172f-109">In the preceding list, <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> is the lowest-quality mode and <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> is the highest-quality mode.</span></span>  
  
 <span data-ttu-id="e172f-110">若要設定的插補模式，將指派的成員<xref:System.Drawing.Drawing2D.InterpolationMode>列舉型別<xref:System.Drawing.Graphics.InterpolationMode%2A>屬性<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="e172f-110">To set the interpolation mode, assign one of the members of the <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration to the <xref:System.Drawing.Graphics.InterpolationMode%2A> property of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e172f-111">範例</span><span class="sxs-lookup"><span data-stu-id="e172f-111">Example</span></span>  
 <span data-ttu-id="e172f-112">下列範例會繪製影像，然後再壓縮具有三種不同的插補模式的映像。</span><span class="sxs-lookup"><span data-stu-id="e172f-112">The following example draws an image and then shrinks the image with three different interpolation modes.</span></span>  
  
 <span data-ttu-id="e172f-113">下圖顯示原始的映像和三個較小的影像。</span><span class="sxs-lookup"><span data-stu-id="e172f-113">The following illustration shows the original image and the three smaller images.</span></span>  
  
 ![如果螢幕擷取畫面顯示具有各種插補設定的影像。](./media/how-to-use-interpolation-mode-to-control-image-quality-during-scaling/varied-interpolation-settings.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e172f-115">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="e172f-115">Compiling the Code</span></span>  
 <span data-ttu-id="e172f-116">上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="e172f-116">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e172f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e172f-117">See also</span></span>

- [<span data-ttu-id="e172f-118">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="e172f-118">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="e172f-119">使用影像、點陣圖、圖示和中繼檔</span><span class="sxs-lookup"><span data-stu-id="e172f-119">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
