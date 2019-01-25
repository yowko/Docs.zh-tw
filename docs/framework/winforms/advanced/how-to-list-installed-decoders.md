---
title: HOW TO：列出已安裝的解碼器
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image decoders [Windows Forms], listing
ms.assetid: 11417191-8c95-40ca-8024-779e61706fb6
ms.openlocfilehash: 3d24eadca23aa6da4a8557cc2db3189b6e232e78
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54605195"
---
# <a name="how-to-list-installed-decoders"></a><span data-ttu-id="e0fd1-102">HOW TO：列出已安裝的解碼器</span><span class="sxs-lookup"><span data-stu-id="e0fd1-102">How to: List Installed Decoders</span></span>
<span data-ttu-id="e0fd1-103">若要列出可用的電腦上，影像解碼器，來判斷您的應用程式是否可以讀取特定影像檔案格式。</span><span class="sxs-lookup"><span data-stu-id="e0fd1-103">You may want to list the image decoders available on a computer, to determine whether your application can read a particular image file format.</span></span> <span data-ttu-id="e0fd1-104"><xref:System.Drawing.Imaging.ImageCodecInfo>類別提供<xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A>靜態方法，如此您就可以判斷哪一個映像會提供解碼器。</span><span class="sxs-lookup"><span data-stu-id="e0fd1-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> static methods so that you can determine which image decoders are available.</span></span> <span data-ttu-id="e0fd1-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> 傳回的陣列<xref:System.Drawing.Imaging.ImageCodecInfo>物件。</span><span class="sxs-lookup"><span data-stu-id="e0fd1-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0fd1-106">範例</span><span class="sxs-lookup"><span data-stu-id="e0fd1-106">Example</span></span>  
 <span data-ttu-id="e0fd1-107">下列程式碼範例會輸出一份已安裝的解碼器和其屬性值。</span><span class="sxs-lookup"><span data-stu-id="e0fd1-107">The following code example outputs the list of installed decoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e0fd1-108">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="e0fd1-108">Compiling the Code</span></span>  
 <span data-ttu-id="e0fd1-109">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="e0fd1-109">This example requires:</span></span>  
  
-   <span data-ttu-id="e0fd1-110">Windows Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e0fd1-110">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="e0fd1-111">A <xref:System.Windows.Forms.PaintEventArgs>，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="e0fd1-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0fd1-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0fd1-112">See also</span></span>
- [<span data-ttu-id="e0fd1-113">如何：列出已安裝的編碼器</span><span class="sxs-lookup"><span data-stu-id="e0fd1-113">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)
- [<span data-ttu-id="e0fd1-114">使用 Managed GDI+ 中的影像編碼器和解碼器</span><span class="sxs-lookup"><span data-stu-id="e0fd1-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
