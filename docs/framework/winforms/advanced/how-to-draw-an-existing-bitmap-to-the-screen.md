---
title: "如何：將現有點陣圖描繪至螢幕"
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
- bitmaps [Windows Forms], displaying in Windows Forms
- bitmaps [Windows Forms], loading in Windows Forms applications
- images [Windows Forms], displaying on Windows Forms
ms.assetid: 5bc558d7-b326-4050-a834-b8600da0de95
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f435c397832e8f64b2bf911a59aae7578ffd3bdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-an-existing-bitmap-to-the-screen"></a><span data-ttu-id="583d7-102">如何：將現有點陣圖描繪至螢幕</span><span class="sxs-lookup"><span data-stu-id="583d7-102">How to: Draw an Existing Bitmap to the Screen</span></span>
<span data-ttu-id="583d7-103">您可以輕鬆地繪製現有映像，螢幕上。</span><span class="sxs-lookup"><span data-stu-id="583d7-103">You can easily draw an existing image on the screen.</span></span> <span data-ttu-id="583d7-104">您必須先建立<xref:System.Drawing.Bitmap>使用點陣圖建構函式之檔案名稱，物件<xref:System.Drawing.Bitmap.%23ctor%28System.String%29>。</span><span class="sxs-lookup"><span data-stu-id="583d7-104">First you need to create a <xref:System.Drawing.Bitmap> object by using the bitmap constructor that takes a file name, <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>.</span></span> <span data-ttu-id="583d7-105">這個建構函式接受數個不同的檔案格式，包括 BMP、 GIF、 JPEG、 PNG 和 TIFF 影像。</span><span class="sxs-lookup"><span data-stu-id="583d7-105">This constructor accepts images with several different file formats, including BMP, GIF, JPEG, PNG, and TIFF.</span></span> <span data-ttu-id="583d7-106">建立之後<xref:System.Drawing.Bitmap>物件，傳遞<xref:System.Drawing.Bitmap>物件<xref:System.Drawing.Graphics.DrawImage%2A>方法<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="583d7-106">After you have created the <xref:System.Drawing.Bitmap> object, pass that <xref:System.Drawing.Bitmap> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="583d7-107">範例</span><span class="sxs-lookup"><span data-stu-id="583d7-107">Example</span></span>  
 <span data-ttu-id="583d7-108">這個範例會建立<xref:System.Drawing.Bitmap>物件從 JPEG 檔案，然後繪製點陣圖的左上角在 60 (10）。</span><span class="sxs-lookup"><span data-stu-id="583d7-108">This example creates a <xref:System.Drawing.Bitmap> object from a JPEG file and then draws the bitmap with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="583d7-109">下圖顯示在指定的位置繪製的點陣圖。</span><span class="sxs-lookup"><span data-stu-id="583d7-109">The following illustration shows the bitmap drawn at the specified location.</span></span>  
  
 <span data-ttu-id="583d7-110">![影像位置](../../../../docs/framework/winforms/advanced/media/csimageposition1.png "csimageposition1")</span><span class="sxs-lookup"><span data-stu-id="583d7-110">![Image Position](../../../../docs/framework/winforms/advanced/media/csimageposition1.png "csimageposition1")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="583d7-111">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="583d7-111">Compiling the Code</span></span>  
 <span data-ttu-id="583d7-112">上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="583d7-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="583d7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="583d7-113">See Also</span></span>  
 [<span data-ttu-id="583d7-114">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="583d7-114">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="583d7-115">使用影像、點陣圖、圖示和中繼檔</span><span class="sxs-lookup"><span data-stu-id="583d7-115">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
