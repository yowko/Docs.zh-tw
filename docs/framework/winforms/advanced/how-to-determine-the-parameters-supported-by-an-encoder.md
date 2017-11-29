---
title: "如何：判斷編碼器所支援的參數"
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
helpviewer_keywords: encoder parameters [Windows Forms], determining supported
ms.assetid: f47ae459-e3ce-4d41-a140-2f6c6aea3f44
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e041434e9ace24618dbdc45341a0e8468721c3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-the-parameters-supported-by-an-encoder"></a><span data-ttu-id="92ffa-102">如何：判斷編碼器所支援的參數</span><span class="sxs-lookup"><span data-stu-id="92ffa-102">How to: Determine the Parameters Supported by an Encoder</span></span>
<span data-ttu-id="92ffa-103">您可以調整影像的參數，例如品質和壓縮層級，但您必須知道所指定之影像編碼器支援的參數。</span><span class="sxs-lookup"><span data-stu-id="92ffa-103">You can adjust image parameters, such as quality and compression level, but you must know which parameters are supported by a given image encoder.</span></span> <span data-ttu-id="92ffa-104"><xref:System.Drawing.Image>類別提供<xref:System.Drawing.Image.GetEncoderParameterList%2A>方法，以便決定映像所支援的參數為特定的編碼器。</span><span class="sxs-lookup"><span data-stu-id="92ffa-104">The <xref:System.Drawing.Image> class provides the <xref:System.Drawing.Image.GetEncoderParameterList%2A> method so that you can determine which image parameters are supported for a particular encoder.</span></span> <span data-ttu-id="92ffa-105">您可以指定編碼器使用的 GUID。</span><span class="sxs-lookup"><span data-stu-id="92ffa-105">You specify the encoder with a GUID.</span></span> <span data-ttu-id="92ffa-106"><xref:System.Drawing.Image.GetEncoderParameterList%2A>方法傳回的陣列<xref:System.Drawing.Imaging.EncoderParameter>物件。</span><span class="sxs-lookup"><span data-stu-id="92ffa-106">The <xref:System.Drawing.Image.GetEncoderParameterList%2A> method returns an array of <xref:System.Drawing.Imaging.EncoderParameter> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92ffa-107">範例</span><span class="sxs-lookup"><span data-stu-id="92ffa-107">Example</span></span>  
 <span data-ttu-id="92ffa-108">下列範例程式碼輸出 JPEG 編碼器支援的參數。</span><span class="sxs-lookup"><span data-stu-id="92ffa-108">The following example code outputs the supported parameters for the JPEG encoder.</span></span> <span data-ttu-id="92ffa-109">使用參數類別目錄清單中相關聯的 Guid<xref:System.Drawing.Imaging.Encoder>類別概觀來決定每個參數類別。</span><span class="sxs-lookup"><span data-stu-id="92ffa-109">Use the list of parameter categories and associated GUIDs in the <xref:System.Drawing.Imaging.Encoder> class overview to determine the category for each parameter.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#3)]
 [!code-vb[UsingImageEncodersDecoders#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="92ffa-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="92ffa-110">Compiling the Code</span></span>  
 <span data-ttu-id="92ffa-111">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="92ffa-111">This example requires:</span></span>  
  
-   <span data-ttu-id="92ffa-112">Windows Form 應用程式。</span><span class="sxs-lookup"><span data-stu-id="92ffa-112">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="92ffa-113">A <xref:System.Windows.Forms.PaintEventArgs>，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="92ffa-113">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92ffa-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92ffa-114">See Also</span></span>  
 [<span data-ttu-id="92ffa-115">操作說明：列出已安裝的編碼器</span><span class="sxs-lookup"><span data-stu-id="92ffa-115">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [<span data-ttu-id="92ffa-116">點陣圖類型</span><span class="sxs-lookup"><span data-stu-id="92ffa-116">Types of Bitmaps</span></span>](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)  
 [<span data-ttu-id="92ffa-117">使用 Managed GDI+ 中的影像編碼器和解碼器</span><span class="sxs-lookup"><span data-stu-id="92ffa-117">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
