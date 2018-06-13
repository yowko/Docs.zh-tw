---
title: 如何：裁剪和縮放影像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], cropping
- images [Windows Forms], scaling
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
ms.openlocfilehash: d5acda50a1aa0f0cae6e77a748b011908fcc8c34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521634"
---
# <a name="how-to-crop-and-scale-images"></a><span data-ttu-id="1cea7-102">如何：裁剪和縮放影像</span><span class="sxs-lookup"><span data-stu-id="1cea7-102">How to: Crop and Scale Images</span></span>
<span data-ttu-id="1cea7-103"><xref:System.Drawing.Graphics>類別提供幾種<xref:System.Drawing.Graphics.DrawImage%2A>方法，其中有些具有來源和目的地矩形參數可用來裁剪和縮放影像。</span><span class="sxs-lookup"><span data-stu-id="1cea7-103">The <xref:System.Drawing.Graphics> class provides several <xref:System.Drawing.Graphics.DrawImage%2A> methods, some of which have source and destination rectangle parameters that you can use to crop and scale images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cea7-104">範例</span><span class="sxs-lookup"><span data-stu-id="1cea7-104">Example</span></span>  
 <span data-ttu-id="1cea7-105">下列範例會建構<xref:System.Drawing.Image>從磁碟檔案 Apple.gif 物件。</span><span class="sxs-lookup"><span data-stu-id="1cea7-105">The following example constructs an <xref:System.Drawing.Image> object from the disk file Apple.gif.</span></span> <span data-ttu-id="1cea7-106">程式碼會在其原始大小繪製整個 apple 映像。</span><span class="sxs-lookup"><span data-stu-id="1cea7-106">The code draws the entire apple image in its original size.</span></span> <span data-ttu-id="1cea7-107">然後程式碼會呼叫<xref:System.Drawing.Graphics.DrawImage%2A>方法<xref:System.Drawing.Graphics>apple 映像的一部分繪製大於原始 apple 映像的目的地矩形的物件。</span><span class="sxs-lookup"><span data-stu-id="1cea7-107">The code then calls the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object to draw a portion of the apple image in a destination rectangle that is larger than the original apple image.</span></span>  
  
 <span data-ttu-id="1cea7-108"><xref:System.Drawing.Graphics.DrawImage%2A>方法會判斷藉由查看來源矩形中，第四個，指定第三個、 第 5 個和第六個引數，讓 apple 的哪一部分。</span><span class="sxs-lookup"><span data-stu-id="1cea7-108">The <xref:System.Drawing.Graphics.DrawImage%2A> method determines which portion of the apple to draw by looking at the source rectangle, which is specified by the third, fourth, fifth, and sixth arguments.</span></span> <span data-ttu-id="1cea7-109">在此情況下，將 apple 裁剪成 75%的寬度和高度的 75%。</span><span class="sxs-lookup"><span data-stu-id="1cea7-109">In this case, the apple is cropped to 75 percent of its width and 75 percent of its height.</span></span>  
  
 <span data-ttu-id="1cea7-110"><xref:System.Drawing.Graphics.DrawImage%2A>方法會判斷繪製裁剪的 apple 位置和大小，以便進行裁剪的 apple 查看目的矩形，也就是第二個引數所指定。</span><span class="sxs-lookup"><span data-stu-id="1cea7-110">The <xref:System.Drawing.Graphics.DrawImage%2A> method determines where to draw the cropped apple and how big to make the cropped apple by looking at the destination rectangle, which is specified by the second argument.</span></span> <span data-ttu-id="1cea7-111">在此情況下，目的地矩形是較寬的 30%，而 30%高於原始映像。</span><span class="sxs-lookup"><span data-stu-id="1cea7-111">In this case, the destination rectangle is 30 percent wider and 30 percent taller than the original image.</span></span>  
  
 <span data-ttu-id="1cea7-112">下圖顯示原始 apple 和縮放裁剪 apple。</span><span class="sxs-lookup"><span data-stu-id="1cea7-112">The following illustration shows the original apple and the scaled, cropped apple.</span></span>  
  
 <span data-ttu-id="1cea7-113">![裁剪 & 縮放](../../../../docs/framework/winforms/advanced/media/cscropscale1.png "csCropScale1")</span><span class="sxs-lookup"><span data-stu-id="1cea7-113">![Crop & Scale](../../../../docs/framework/winforms/advanced/media/cscropscale1.png "csCropScale1")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1cea7-114">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1cea7-114">Compiling the Code</span></span>  
 <span data-ttu-id="1cea7-115">上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="1cea7-115">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="1cea7-116">請務必取代`Apple.gif`映像檔案名稱與您系統為有效的路徑。</span><span class="sxs-lookup"><span data-stu-id="1cea7-116">Make sure to replace `Apple.gif` with an image file name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cea7-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cea7-117">See Also</span></span>  
 [<span data-ttu-id="1cea7-118">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="1cea7-118">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="1cea7-119">使用影像、點陣圖、圖示和中繼檔</span><span class="sxs-lookup"><span data-stu-id="1cea7-119">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
