---
title: "如何：列出已安裝的編碼器"
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
- image codecs [Windows Forms], listing
- image encoders [Windows Forms], listing
ms.assetid: 49e8e4e9-7a67-42d9-86bf-08821cdc282e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ec3ce7d2d933226162664826764c818eacf97afc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-list-installed-encoders"></a><span data-ttu-id="e034b-102">如何：列出已安裝的編碼器</span><span class="sxs-lookup"><span data-stu-id="e034b-102">How to: List Installed Encoders</span></span>
<span data-ttu-id="e034b-103">若要列出影像轉碼器的電腦上，可用來判斷您的應用程式是否可以將儲存至特定的影像檔案格式。</span><span class="sxs-lookup"><span data-stu-id="e034b-103">You may want to list the image encoders available on a computer, to determine whether your application can save to a particular image file format.</span></span> <span data-ttu-id="e034b-104"><xref:System.Drawing.Imaging.ImageCodecInfo>類別提供<xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A>靜態方法，如此您就可以判斷哪一個映像編碼器可用。</span><span class="sxs-lookup"><span data-stu-id="e034b-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> static methods so that you can determine which image encoders are available.</span></span> <span data-ttu-id="e034b-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A>傳回的陣列<xref:System.Drawing.Imaging.ImageCodecInfo>物件。</span><span class="sxs-lookup"><span data-stu-id="e034b-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e034b-106">範例</span><span class="sxs-lookup"><span data-stu-id="e034b-106">Example</span></span>  
 <span data-ttu-id="e034b-107">下列程式碼範例會輸出之已安裝的編碼器清單和其屬性值。</span><span class="sxs-lookup"><span data-stu-id="e034b-107">The following code example outputs the list of installed encoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#1)]
 [!code-vb[UsingImageEncodersDecoders#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e034b-108">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="e034b-108">Compiling the Code</span></span>  
 <span data-ttu-id="e034b-109">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="e034b-109">This example requires:</span></span>  
  
-   <span data-ttu-id="e034b-110">Windows Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e034b-110">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="e034b-111">A <xref:System.Windows.Forms.PaintEventArgs>，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="e034b-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e034b-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="e034b-112">See Also</span></span>  
 [<span data-ttu-id="e034b-113">操作說明：列出已安裝的解碼器</span><span class="sxs-lookup"><span data-stu-id="e034b-113">How to: List Installed Decoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 [<span data-ttu-id="e034b-114">使用 Managed GDI+ 中的影像編碼器和解碼器</span><span class="sxs-lookup"><span data-stu-id="e034b-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
