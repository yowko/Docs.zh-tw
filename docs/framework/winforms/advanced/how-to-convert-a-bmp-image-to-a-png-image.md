---
title: HOW TO：將 BMP 影像轉換為 PNG 影像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BMP images [Windows Forms], converting to PNG
- image formats [Windows Forms], converting between
ms.assetid: 9d4a692d-73ac-4ce3-9e05-9ec321e8fbd6
ms.openlocfilehash: e11e2874853fb924b2da09f9fdc986873941f141
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676441"
---
# <a name="how-to-convert-a-bmp-image-to-a-png-image"></a><span data-ttu-id="d14e1-102">HOW TO：將 BMP 影像轉換為 PNG 影像</span><span class="sxs-lookup"><span data-stu-id="d14e1-102">How to: Convert a BMP image to a PNG image</span></span>
<span data-ttu-id="d14e1-103">有時候，您想要從一個影像檔案格式轉換成另一個。</span><span class="sxs-lookup"><span data-stu-id="d14e1-103">Oftentimes, you will want to convert from one image file format to another.</span></span> <span data-ttu-id="d14e1-104">藉由呼叫 <xref:System.Drawing.Image> 類別的 <xref:System.Drawing.Image.Save%2A> 方法，並指定 <xref:System.Drawing.Imaging.ImageFormat> 為所需的影像檔案格式，您可以輕鬆地執行這項轉換。</span><span class="sxs-lookup"><span data-stu-id="d14e1-104">You can do this conversion easily by calling the <xref:System.Drawing.Image.Save%2A> method of the <xref:System.Drawing.Image> class and specifying the <xref:System.Drawing.Imaging.ImageFormat> for the desired image file format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d14e1-105">範例</span><span class="sxs-lookup"><span data-stu-id="d14e1-105">Example</span></span>  
 <span data-ttu-id="d14e1-106">下列範例會從類型載入 BMP 影像，並將影像儲存成 PNG 格式。</span><span class="sxs-lookup"><span data-stu-id="d14e1-106">The following example loads a BMP image from a type, and saves the image in the PNG format.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d14e1-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="d14e1-107">Compiling the Code</span></span>  
 <span data-ttu-id="d14e1-108">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="d14e1-108">This example requires:</span></span>  
  
-   <span data-ttu-id="d14e1-109">Windows Form 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d14e1-109">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="d14e1-110">`System.Drawing.Imaging` 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="d14e1-110">A reference to the `System.Drawing.Imaging` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d14e1-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d14e1-111">See also</span></span>
- [<span data-ttu-id="d14e1-112">如何：列出已安裝的編碼器</span><span class="sxs-lookup"><span data-stu-id="d14e1-112">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)
- [<span data-ttu-id="d14e1-113">使用 Managed GDI+ 中的影像編碼器和解碼器</span><span class="sxs-lookup"><span data-stu-id="d14e1-113">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
- [<span data-ttu-id="d14e1-114">點陣圖類型</span><span class="sxs-lookup"><span data-stu-id="d14e1-114">Types of Bitmaps</span></span>](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)
