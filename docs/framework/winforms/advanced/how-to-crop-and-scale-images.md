---
title: HOW TO：裁剪和縮放影像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], cropping
- images [Windows Forms], scaling
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
ms.openlocfilehash: 4257431881565f9160f45795111d374cc680dedd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189881"
---
# <a name="how-to-crop-and-scale-images"></a><span data-ttu-id="74e9c-102">HOW TO：裁剪和縮放影像</span><span class="sxs-lookup"><span data-stu-id="74e9c-102">How to: Crop and Scale Images</span></span>
<span data-ttu-id="74e9c-103"><xref:System.Drawing.Graphics>類別提供了幾個<xref:System.Drawing.Graphics.DrawImage%2A>方法，其中有些有可用來裁剪和縮放比例的映像的來源和目的地矩形參數。</span><span class="sxs-lookup"><span data-stu-id="74e9c-103">The <xref:System.Drawing.Graphics> class provides several <xref:System.Drawing.Graphics.DrawImage%2A> methods, some of which have source and destination rectangle parameters that you can use to crop and scale images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74e9c-104">範例</span><span class="sxs-lookup"><span data-stu-id="74e9c-104">Example</span></span>  
 <span data-ttu-id="74e9c-105">下列範例會建構<xref:System.Drawing.Image>從磁碟檔案 Apple.gif 的物件。</span><span class="sxs-lookup"><span data-stu-id="74e9c-105">The following example constructs an <xref:System.Drawing.Image> object from the disk file Apple.gif.</span></span> <span data-ttu-id="74e9c-106">程式碼會在其原始大小繪製整個 apple 映像。</span><span class="sxs-lookup"><span data-stu-id="74e9c-106">The code draws the entire apple image in its original size.</span></span> <span data-ttu-id="74e9c-107">程式碼會接著呼叫<xref:System.Drawing.Graphics.DrawImage%2A>方法的<xref:System.Drawing.Graphics>物件来繪製大於原始 apple 映像的目的地矩形的 apple 映像的一部分。</span><span class="sxs-lookup"><span data-stu-id="74e9c-107">The code then calls the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object to draw a portion of the apple image in a destination rectangle that is larger than the original apple image.</span></span>  
  
 <span data-ttu-id="74e9c-108"><xref:System.Drawing.Graphics.DrawImage%2A>方法會判斷哪一部分 apple，以繪製藉由查看來源矩形中，由第三個、 第四，第 5 個和第六個引數。</span><span class="sxs-lookup"><span data-stu-id="74e9c-108">The <xref:System.Drawing.Graphics.DrawImage%2A> method determines which portion of the apple to draw by looking at the source rectangle, which is specified by the third, fourth, fifth, and sixth arguments.</span></span> <span data-ttu-id="74e9c-109">在此情況下，apple 會裁剪成的寬度的 75%，且其高度的 75%。</span><span class="sxs-lookup"><span data-stu-id="74e9c-109">In this case, the apple is cropped to 75 percent of its width and 75 percent of its height.</span></span>  
  
 <span data-ttu-id="74e9c-110"><xref:System.Drawing.Graphics.DrawImage%2A>方法會判斷要繪製的裁剪後的 apple 的何處，以及這是要藉由查看目的地矩形的裁剪後的 apple 多大，第二個引數所指定。</span><span class="sxs-lookup"><span data-stu-id="74e9c-110">The <xref:System.Drawing.Graphics.DrawImage%2A> method determines where to draw the cropped apple and how big to make the cropped apple by looking at the destination rectangle, which is specified by the second argument.</span></span> <span data-ttu-id="74e9c-111">在此情況下，目的地矩形是更廣的 30%，而比原始影像高度的 30%。</span><span class="sxs-lookup"><span data-stu-id="74e9c-111">In this case, the destination rectangle is 30 percent wider and 30 percent taller than the original image.</span></span>  
  
 <span data-ttu-id="74e9c-112">下圖顯示原始的 apple，並調整裁剪 apple。</span><span class="sxs-lookup"><span data-stu-id="74e9c-112">The following illustration shows the original apple and the scaled, cropped apple.</span></span>  
  
 ![原始的映像和裁剪的相同映像的螢幕擷取畫面。](./media/how-to-crop-and-scale-images/original-image-cropped-image.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="74e9c-114">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="74e9c-114">Compiling the Code</span></span>  
 <span data-ttu-id="74e9c-115">上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="74e9c-115">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="74e9c-116">請務必取代`Apple.gif`映像檔案名稱與您系統為有效的路徑。</span><span class="sxs-lookup"><span data-stu-id="74e9c-116">Make sure to replace `Apple.gif` with an image file name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74e9c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74e9c-117">See also</span></span>

- [<span data-ttu-id="74e9c-118">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="74e9c-118">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="74e9c-119">使用影像、點陣圖、圖示和中繼檔</span><span class="sxs-lookup"><span data-stu-id="74e9c-119">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
