---
title: HOW TO：載入和顯示中繼檔
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
ms.openlocfilehash: d0835d7f2c5ffea44f22661a765ab16b1d0130c5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619554"
---
# <a name="how-to-load-and-display-metafiles"></a><span data-ttu-id="c5935-102">HOW TO：載入和顯示中繼檔</span><span class="sxs-lookup"><span data-stu-id="c5935-102">How to: Load and Display Metafiles</span></span>
<span data-ttu-id="c5935-103"><xref:System.Drawing.Imaging.Metafile>類別，繼承自<xref:System.Drawing.Image>類別中，提供記錄、 顯示及檢查向量影像的方法。</span><span class="sxs-lookup"><span data-stu-id="c5935-103">The <xref:System.Drawing.Imaging.Metafile> class, which inherits from the <xref:System.Drawing.Image> class, provides methods for recording, displaying, and examining vector images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5935-104">範例</span><span class="sxs-lookup"><span data-stu-id="c5935-104">Example</span></span>  
 <span data-ttu-id="c5935-105">若要在螢幕上顯示為向量影像 （中繼檔），您需要<xref:System.Drawing.Imaging.Metafile>物件和<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="c5935-105">To display a vector image (metafile) on the screen, you need a <xref:System.Drawing.Imaging.Metafile> object and a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="c5935-106">將檔案 （或資料流） 的名稱傳遞給<xref:System.Drawing.Imaging.Metafile>建構函式。</span><span class="sxs-lookup"><span data-stu-id="c5935-106">Pass the name of a file (or a stream) to a <xref:System.Drawing.Imaging.Metafile> constructor.</span></span> <span data-ttu-id="c5935-107">建立之後<xref:System.Drawing.Imaging.Metafile>物件，傳遞<xref:System.Drawing.Imaging.Metafile>物件<xref:System.Drawing.Graphics.DrawImage%2A>方法<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="c5935-107">After you have created a <xref:System.Drawing.Imaging.Metafile> object, pass that <xref:System.Drawing.Imaging.Metafile> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="c5935-108">此範例會建立<xref:System.Drawing.Imaging.Metafile>EMF （增強型中繼檔） 檔案中的物件，然後繪製在其左上角的映像 （60，10）。</span><span class="sxs-lookup"><span data-stu-id="c5935-108">The example creates a <xref:System.Drawing.Imaging.Metafile> object from an EMF (enhanced metafile) file and then draws the image with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="c5935-109">下圖顯示中繼檔繪製在指定的位置。</span><span class="sxs-lookup"><span data-stu-id="c5935-109">The following illustration shows the metafile drawn at the specified location.</span></span>  
  
 <span data-ttu-id="c5935-110">![映像位置](../../../../docs/framework/winforms/advanced/media/imageposition2.png "imageposition2")</span><span class="sxs-lookup"><span data-stu-id="c5935-110">![Image Position](../../../../docs/framework/winforms/advanced/media/imageposition2.png "imageposition2")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c5935-111">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="c5935-111">Compiling the Code</span></span>  
 <span data-ttu-id="c5935-112">上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="c5935-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5935-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5935-113">See also</span></span>
- [<span data-ttu-id="c5935-114">使用影像、點陣圖、圖示和中繼檔</span><span class="sxs-lookup"><span data-stu-id="c5935-114">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
