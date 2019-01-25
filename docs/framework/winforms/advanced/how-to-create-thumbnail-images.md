---
title: HOW TO：建立縮圖影像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thumbnail images [Windows Forms], creating
- images [Windows Forms], creating thumbnails
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
ms.openlocfilehash: fd5e0b5341a712f25f9d41670f9b3ede5414dda4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497007"
---
# <a name="how-to-create-thumbnail-images"></a><span data-ttu-id="ec892-102">HOW TO：建立縮圖影像</span><span class="sxs-lookup"><span data-stu-id="ec892-102">How to: Create Thumbnail Images</span></span>
<span data-ttu-id="ec892-103">縮圖的影像是影像的縮小版本。</span><span class="sxs-lookup"><span data-stu-id="ec892-103">A thumbnail image is a small version of an image.</span></span> <span data-ttu-id="ec892-104">您可以藉由呼叫建立縮圖影像<xref:System.Drawing.Image.GetThumbnailImage%2A>方法的<xref:System.Drawing.Image>物件。</span><span class="sxs-lookup"><span data-stu-id="ec892-104">You can create a thumbnail image by calling the <xref:System.Drawing.Image.GetThumbnailImage%2A> method of an <xref:System.Drawing.Image> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec892-105">範例</span><span class="sxs-lookup"><span data-stu-id="ec892-105">Example</span></span>  
 <span data-ttu-id="ec892-106">下列範例會建構<xref:System.Drawing.Image>JPG 檔案中的物件。</span><span class="sxs-lookup"><span data-stu-id="ec892-106">The following example constructs an <xref:System.Drawing.Image> object from a JPG file.</span></span> <span data-ttu-id="ec892-107">原始的映像有 640 像素的寬度和高度為 479 個像素。</span><span class="sxs-lookup"><span data-stu-id="ec892-107">The original image has a width of 640 pixels and a height of 479 pixels.</span></span> <span data-ttu-id="ec892-108">程式碼會建立具有 100 像素的寬度和高度為 100 像素的縮圖影像。</span><span class="sxs-lookup"><span data-stu-id="ec892-108">The code creates a thumbnail image that has a width of 100 pixels and a height of 100 pixels.</span></span>  
  
 <span data-ttu-id="ec892-109">下圖顯示的縮圖影像。</span><span class="sxs-lookup"><span data-stu-id="ec892-109">The following illustration shows the thumbnail image.</span></span>  
  
 <span data-ttu-id="ec892-110">![縮圖影像](../../../../docs/framework/winforms/advanced/media/thumbnail1.png "Thumbnail1")</span><span class="sxs-lookup"><span data-stu-id="ec892-110">![Thumbnail Image](../../../../docs/framework/winforms/advanced/media/thumbnail1.png "Thumbnail1")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ec892-111">在此範例中，回呼方法已宣告但從未使用。</span><span class="sxs-lookup"><span data-stu-id="ec892-111">In this example, a callback method is declared, but never used.</span></span> <span data-ttu-id="ec892-112">這可支援所有版本的 GDI +。</span><span class="sxs-lookup"><span data-stu-id="ec892-112">This supports all versions of GDI+.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ec892-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ec892-113">Compiling the Code</span></span>  
 <span data-ttu-id="ec892-114">上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="ec892-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="ec892-115">若要執行此範例，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="ec892-115">To run the example, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ec892-116">新建 Windows Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="ec892-116">Create a new Windows Forms application.</span></span>  
  
2.  <span data-ttu-id="ec892-117">將範例程式碼加入至表單。</span><span class="sxs-lookup"><span data-stu-id="ec892-117">Add the example code to the form.</span></span>  
  
3.  <span data-ttu-id="ec892-118">建立表單的處理常式<xref:System.Windows.Forms.Control.Paint>事件</span><span class="sxs-lookup"><span data-stu-id="ec892-118">Create a handler for the form's <xref:System.Windows.Forms.Control.Paint> event</span></span>  
  
4.  <span data-ttu-id="ec892-119">在 <xref:System.Windows.Forms.Control.Paint>處理常式中，呼叫`GetThumbnail`方法並傳遞`e`如<xref:System.Windows.Forms.PaintEventArgs>。</span><span class="sxs-lookup"><span data-stu-id="ec892-119">In the <xref:System.Windows.Forms.Control.Paint> handler, call the `GetThumbnail` method and pass `e` for <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
5.  <span data-ttu-id="ec892-120">尋找您想要的縮圖的影像檔。</span><span class="sxs-lookup"><span data-stu-id="ec892-120">Find an image file that you want to make a thumbnail of.</span></span>  
  
6.  <span data-ttu-id="ec892-121">在 `GetThumbnail`方法指定的路徑和檔案加入至映像的名稱。</span><span class="sxs-lookup"><span data-stu-id="ec892-121">In the `GetThumbnail` method, specify the path and file name to your image.</span></span>  
  
7.  <span data-ttu-id="ec892-122">按 F5 執行範例。</span><span class="sxs-lookup"><span data-stu-id="ec892-122">Press F5 to run the example.</span></span>  
  
     <span data-ttu-id="ec892-123">100 x 100 的縮圖影像會出現在表單上。</span><span class="sxs-lookup"><span data-stu-id="ec892-123">A 100 by 100 thumbnail image appears on the form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec892-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec892-124">See also</span></span>
- [<span data-ttu-id="ec892-125">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="ec892-125">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="ec892-126">使用影像、點陣圖、圖示和中繼檔</span><span class="sxs-lookup"><span data-stu-id="ec892-126">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
