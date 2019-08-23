---
title: 作法：建立縮圖影像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thumbnail images [Windows Forms], creating
- images [Windows Forms], creating thumbnails
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
ms.openlocfilehash: 786a92d99f5e7a0c27f502efa9a5fe617ac4d4d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923745"
---
# <a name="how-to-create-thumbnail-images"></a><span data-ttu-id="f50e6-102">作法：建立縮圖影像</span><span class="sxs-lookup"><span data-stu-id="f50e6-102">How to: Create Thumbnail Images</span></span>
<span data-ttu-id="f50e6-103">縮圖影像是影像的小型版本。</span><span class="sxs-lookup"><span data-stu-id="f50e6-103">A thumbnail image is a small version of an image.</span></span> <span data-ttu-id="f50e6-104">您可以藉由呼叫<xref:System.Drawing.Image.GetThumbnailImage%2A> <xref:System.Drawing.Image>物件的方法來建立縮圖影像。</span><span class="sxs-lookup"><span data-stu-id="f50e6-104">You can create a thumbnail image by calling the <xref:System.Drawing.Image.GetThumbnailImage%2A> method of an <xref:System.Drawing.Image> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f50e6-105">範例</span><span class="sxs-lookup"><span data-stu-id="f50e6-105">Example</span></span>  
 <span data-ttu-id="f50e6-106">下列範例<xref:System.Drawing.Image>會從 JPG 檔案中建立物件。</span><span class="sxs-lookup"><span data-stu-id="f50e6-106">The following example constructs an <xref:System.Drawing.Image> object from a JPG file.</span></span> <span data-ttu-id="f50e6-107">原始影像的寬度為640圖元, 而高度為479圖元。</span><span class="sxs-lookup"><span data-stu-id="f50e6-107">The original image has a width of 640 pixels and a height of 479 pixels.</span></span> <span data-ttu-id="f50e6-108">程式碼會建立寬度為100圖元且高度為100圖元的縮圖影像。</span><span class="sxs-lookup"><span data-stu-id="f50e6-108">The code creates a thumbnail image that has a width of 100 pixels and a height of 100 pixels.</span></span>  
  
 <span data-ttu-id="f50e6-109">下圖顯示縮圖影像:</span><span class="sxs-lookup"><span data-stu-id="f50e6-109">The following illustration shows the thumbnail image:</span></span>  
  
 ![顯示輸出縮圖的螢幕擷取畫面。](./media/how-to-create-thumbnail-images/construct-thumbnail-image.png)  
  
> [!NOTE]
> <span data-ttu-id="f50e6-111">在此範例中, 回呼方法已宣告, 但從未使用過。</span><span class="sxs-lookup"><span data-stu-id="f50e6-111">In this example, a callback method is declared, but never used.</span></span> <span data-ttu-id="f50e6-112">這支援所有的 GDI + 版本。</span><span class="sxs-lookup"><span data-stu-id="f50e6-112">This supports all versions of GDI+.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f50e6-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="f50e6-113">Compiling the Code</span></span>  
 <span data-ttu-id="f50e6-114">上述範例是針對與 Windows Forms 搭配使用所設計, 而且它<xref:System.Windows.Forms.PaintEventArgs>需要`e`, 這<xref:System.Windows.Forms.Control.Paint>是事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="f50e6-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="f50e6-115">若要執行範例, 請遵循下列步驟:</span><span class="sxs-lookup"><span data-stu-id="f50e6-115">To run the example, follow these steps:</span></span>  
  
1. <span data-ttu-id="f50e6-116">新建 Windows Forms 應用程式</span><span class="sxs-lookup"><span data-stu-id="f50e6-116">Create a new Windows Forms application.</span></span>  
  
2. <span data-ttu-id="f50e6-117">將範例程式碼新增至表單。</span><span class="sxs-lookup"><span data-stu-id="f50e6-117">Add the example code to the form.</span></span>  
  
3. <span data-ttu-id="f50e6-118">建立表單<xref:System.Windows.Forms.Control.Paint>事件的處理常式</span><span class="sxs-lookup"><span data-stu-id="f50e6-118">Create a handler for the form's <xref:System.Windows.Forms.Control.Paint> event</span></span>  
  
4. <span data-ttu-id="f50e6-119">在處理常式中, `GetThumbnail`呼叫方法並傳遞給<xref:System.Windows.Forms.PaintEventArgs>。 `e` <xref:System.Windows.Forms.Control.Paint></span><span class="sxs-lookup"><span data-stu-id="f50e6-119">In the <xref:System.Windows.Forms.Control.Paint> handler, call the `GetThumbnail` method and pass `e` for <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
5. <span data-ttu-id="f50e6-120">尋找您要做為縮圖的影像檔案。</span><span class="sxs-lookup"><span data-stu-id="f50e6-120">Find an image file that you want to make a thumbnail of.</span></span>  
  
6. <span data-ttu-id="f50e6-121">`GetThumbnail`在方法中, 指定影像的路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="f50e6-121">In the `GetThumbnail` method, specify the path and file name to your image.</span></span>  
  
7. <span data-ttu-id="f50e6-122">按 F5 執行範例。</span><span class="sxs-lookup"><span data-stu-id="f50e6-122">Press F5 to run the example.</span></span>  
  
     <span data-ttu-id="f50e6-123">100 x 100 縮圖影像會出現在表單上。</span><span class="sxs-lookup"><span data-stu-id="f50e6-123">A 100 by 100 thumbnail image appears on the form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f50e6-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f50e6-124">See also</span></span>

- [<span data-ttu-id="f50e6-125">影像、點陣圖和中繼檔</span><span class="sxs-lookup"><span data-stu-id="f50e6-125">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="f50e6-126">使用影像、點陣圖、圖示和中繼檔</span><span class="sxs-lookup"><span data-stu-id="f50e6-126">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
