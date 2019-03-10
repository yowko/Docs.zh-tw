---
title: HOW TO：列出已安裝的編碼器
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image encoders [Windows Forms], listing
ms.assetid: 49e8e4e9-7a67-42d9-86bf-08821cdc282e
ms.openlocfilehash: 492930b7d8a47db478c8fa0f282cb5f491e144ac
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708453"
---
# <a name="how-to-list-installed-encoders"></a><span data-ttu-id="9cad4-102">HOW TO：列出已安裝的編碼器</span><span class="sxs-lookup"><span data-stu-id="9cad4-102">How to: List Installed Encoders</span></span>
<span data-ttu-id="9cad4-103">若要列出可用的電腦上，影像編碼器，以判斷是否能省下您的應用程式特定的影像檔案格式。</span><span class="sxs-lookup"><span data-stu-id="9cad4-103">You may want to list the image encoders available on a computer, to determine whether your application can save to a particular image file format.</span></span> <span data-ttu-id="9cad4-104"><xref:System.Drawing.Imaging.ImageCodecInfo>類別提供<xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A>靜態方法，讓您可以判斷哪一個映像編碼器可用。</span><span class="sxs-lookup"><span data-stu-id="9cad4-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> static methods so that you can determine which image encoders are available.</span></span> <span data-ttu-id="9cad4-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> 傳回的陣列<xref:System.Drawing.Imaging.ImageCodecInfo>物件。</span><span class="sxs-lookup"><span data-stu-id="9cad4-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cad4-106">範例</span><span class="sxs-lookup"><span data-stu-id="9cad4-106">Example</span></span>  
 <span data-ttu-id="9cad4-107">下列程式碼範例會輸出已安裝的編碼器的清單和其屬性值。</span><span class="sxs-lookup"><span data-stu-id="9cad4-107">The following code example outputs the list of installed encoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#1](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#1)]
 [!code-vb[UsingImageEncodersDecoders#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9cad4-108">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="9cad4-108">Compiling the Code</span></span>  
 <span data-ttu-id="9cad4-109">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="9cad4-109">This example requires:</span></span>  
  
-   <span data-ttu-id="9cad4-110">Windows Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9cad4-110">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="9cad4-111">A <xref:System.Windows.Forms.PaintEventArgs>，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="9cad4-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cad4-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cad4-112">See also</span></span>
- [<span data-ttu-id="9cad4-113">如何：列出已安裝的解碼器</span><span class="sxs-lookup"><span data-stu-id="9cad4-113">How to: List Installed Decoders</span></span>](how-to-list-installed-decoders.md)
- [<span data-ttu-id="9cad4-114">使用 Managed GDI+ 中的影像編碼器和解碼器</span><span class="sxs-lookup"><span data-stu-id="9cad4-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](using-image-encoders-and-decoders-in-managed-gdi.md)
