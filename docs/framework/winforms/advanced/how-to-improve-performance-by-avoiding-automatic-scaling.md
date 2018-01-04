---
title: "如何：避免自動縮放以提高效能"
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
- automatic scaling
- images [Windows Forms], improving performance
- images [Windows Forms], using without automatic scaling
- performance [Windows Forms], improving image
ms.assetid: 5fe2c95d-8653-4d55-bf0d-e5afa28f223b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f49fc4b1e59879b9ecc67295610187fa2e5e80d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-improve-performance-by-avoiding-automatic-scaling"></a><span data-ttu-id="15134-102">如何：避免自動縮放以提高效能</span><span class="sxs-lookup"><span data-stu-id="15134-102">How to: Improve Performance by Avoiding Automatic Scaling</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="15134-103">可能會自動隨著映像您繪製，反而會降低效能。</span><span class="sxs-lookup"><span data-stu-id="15134-103"> may automatically scale an image as you draw it, which would decrease performance.</span></span> <span data-ttu-id="15134-104">或者，您可以控制傳遞到目的地矩形的維度影像的縮放<xref:System.Drawing.Graphics.DrawImage%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="15134-104">Alternatively, you can control the scaling of the image by passing the dimensions of the destination rectangle to the <xref:System.Drawing.Graphics.DrawImage%2A> method.</span></span>  
  
 <span data-ttu-id="15134-105">例如，下列呼叫<xref:System.Drawing.Graphics.DrawImage%2A>方法指定的左上角 （50，30），但未指定目的地矩形。</span><span class="sxs-lookup"><span data-stu-id="15134-105">For example, the following call to the <xref:System.Drawing.Graphics.DrawImage%2A> method specifies an upper-left corner of (50, 30) but does not specify a destination rectangle.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#31)]  
  
 <span data-ttu-id="15134-106">雖然這是最簡單的版本<xref:System.Drawing.Graphics.DrawImage%2A>方法所需的引數數量不一定是最有效率。</span><span class="sxs-lookup"><span data-stu-id="15134-106">Although this is the easiest version of the <xref:System.Drawing.Graphics.DrawImage%2A> method in terms of the number of required arguments, it is not necessarily the most efficient.</span></span> <span data-ttu-id="15134-107">如果解析由[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)](通常是 96 dpi) 不同於儲存在解析<xref:System.Drawing.Image>物件，則<xref:System.Drawing.Graphics.DrawImage%2A>方法將縮放影像。</span><span class="sxs-lookup"><span data-stu-id="15134-107">If the resolution used by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] (usually 96 dots per inch) is different from the resolution stored in the <xref:System.Drawing.Image> object, then the <xref:System.Drawing.Graphics.DrawImage%2A> method will scale the image.</span></span> <span data-ttu-id="15134-108">例如，假設<xref:System.Drawing.Image>物件具有 216 像素為單位的寬度和水平解析度是預存的值為 72 dpi。</span><span class="sxs-lookup"><span data-stu-id="15134-108">For example, suppose an <xref:System.Drawing.Image> object has a width of 216 pixels and a stored horizontal resolution value of 72 dots per inch.</span></span> <span data-ttu-id="15134-109">因為 216/72 為 3， <xref:System.Drawing.Graphics.DrawImage%2A> ，使其具有 3 英吋的寬度解析度為 96 dpi 縮放影像。</span><span class="sxs-lookup"><span data-stu-id="15134-109">Because 216/72 is 3, <xref:System.Drawing.Graphics.DrawImage%2A> will scale the image so that it has a width of 3 inches at a resolution of 96 dots per inch.</span></span> <span data-ttu-id="15134-110">也就是說，<xref:System.Drawing.Graphics.DrawImage%2A>會顯示影像的寬度為 96 x 3 = 288，像素為單位。</span><span class="sxs-lookup"><span data-stu-id="15134-110">That is, <xref:System.Drawing.Graphics.DrawImage%2A> will display an image that has a width of 96x3 = 288 pixels.</span></span>  
  
 <span data-ttu-id="15134-111">即使您的螢幕解析度 96 dpi，從不同[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]將可能刻度影像好像螢幕解析度 96 dpi。</span><span class="sxs-lookup"><span data-stu-id="15134-111">Even if your screen resolution is different from 96 dots per inch, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] will probably scale the image as if the screen resolution were 96 dots per inch.</span></span> <span data-ttu-id="15134-112">這是因為[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<xref:System.Drawing.Graphics>物件都與裝置內容，以及當[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]螢幕解析度時，結果的裝置內容通常是 96，不論實際螢幕解析度的查詢。</span><span class="sxs-lookup"><span data-stu-id="15134-112">That is because a [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> object is associated with a device context, and when [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] queries the device context for the screen resolution, the result is usually 96, regardless of the actual screen resolution.</span></span> <span data-ttu-id="15134-113">您可以藉由指定目的地矩形中的自動調整，避免<xref:System.Drawing.Graphics.DrawImage%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="15134-113">You can avoid automatic scaling by specifying the destination rectangle in the <xref:System.Drawing.Graphics.DrawImage%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15134-114">範例</span><span class="sxs-lookup"><span data-stu-id="15134-114">Example</span></span>  
 <span data-ttu-id="15134-115">下列範例會繪製兩次相同的映像。</span><span class="sxs-lookup"><span data-stu-id="15134-115">The following example draws the same image twice.</span></span> <span data-ttu-id="15134-116">在第一個案例中，未指定目的地矩形的高度與寬度，並自動縮放影像。</span><span class="sxs-lookup"><span data-stu-id="15134-116">In the first case, the width and height of the destination rectangle are not specified, and the image is automatically scaled.</span></span> <span data-ttu-id="15134-117">在第二個案例中，寬度和目的地矩形的高度 （單位為像素為單位） 指定要做為原始影像的高度與寬度會相同。</span><span class="sxs-lookup"><span data-stu-id="15134-117">In the second case, the width and height (measured in pixels) of the destination rectangle are specified to be the same as the width and height of the original image.</span></span> <span data-ttu-id="15134-118">下圖顯示兩次呈現的影像。</span><span class="sxs-lookup"><span data-stu-id="15134-118">The following illustration shows the image rendered twice.</span></span>  
  
 <span data-ttu-id="15134-119">![調整紋理](../../../../docs/framework/winforms/advanced/media/csscaledtexture1.png "csscaledtexture1")</span><span class="sxs-lookup"><span data-stu-id="15134-119">![Scaled Texture](../../../../docs/framework/winforms/advanced/media/csscaledtexture1.png "csscaledtexture1")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#32)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="15134-120">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="15134-120">Compiling the Code</span></span>  
 <span data-ttu-id="15134-121">上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="15134-121">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="15134-122">取代 Texture.jpg 映像名稱和您系統為有效的路徑。</span><span class="sxs-lookup"><span data-stu-id="15134-122">Replace Texture.jpg with an image name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15134-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="15134-123">See Also</span></span>  
 [<span data-ttu-id="15134-124">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="15134-124">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="15134-125">使用影像、點陣圖、圖示和中繼檔</span><span class="sxs-lookup"><span data-stu-id="15134-125">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
