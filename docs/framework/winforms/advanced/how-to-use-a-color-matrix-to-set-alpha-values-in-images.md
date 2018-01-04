---
title: "如何：使用色彩矩陣設定影像中的 Alpha 值"
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
- images [Windows Forms], using color matrices for semi-transparent
- transparency [Windows Forms], color matrices
- matrices [Windows Forms], alpha values
- bitmaps [Windows Forms], using color matrices for semi-transparent
ms.assetid: a27121e6-f7e9-4c09-84e2-f05aa9d2a1bb
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5dde9417782e4404237a995364d65058f023c3e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a><span data-ttu-id="64340-102">如何：使用色彩矩陣設定影像中的 Alpha 值</span><span class="sxs-lookup"><span data-stu-id="64340-102">How to: Use a Color Matrix to Set Alpha Values in Images</span></span>
<span data-ttu-id="64340-103"><xref:System.Drawing.Bitmap>類別 (繼承自<xref:System.Drawing.Image>類別) 和<xref:System.Drawing.Imaging.ImageAttributes>類別提供取得和設定像素值的功能。</span><span class="sxs-lookup"><span data-stu-id="64340-103">The <xref:System.Drawing.Bitmap> class (which inherits from the <xref:System.Drawing.Image> class) and the <xref:System.Drawing.Imaging.ImageAttributes> class provide functionality for getting and setting pixel values.</span></span> <span data-ttu-id="64340-104">您可以使用<xref:System.Drawing.Imaging.ImageAttributes>類別來修改 alpha 值整個影像，或您可以呼叫<xref:System.Drawing.Bitmap.SetPixel%2A>方法<xref:System.Drawing.Bitmap>類別以修改個別像素值。</span><span class="sxs-lookup"><span data-stu-id="64340-104">You can use the <xref:System.Drawing.Imaging.ImageAttributes> class to modify the alpha values for an entire image, or you can call the <xref:System.Drawing.Bitmap.SetPixel%2A> method of the <xref:System.Drawing.Bitmap> class to modify individual pixel values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64340-105">範例</span><span class="sxs-lookup"><span data-stu-id="64340-105">Example</span></span>  
 <span data-ttu-id="64340-106"><xref:System.Drawing.Imaging.ImageAttributes>類別具有可讓您在轉譯期間修改映像的屬性。</span><span class="sxs-lookup"><span data-stu-id="64340-106">The <xref:System.Drawing.Imaging.ImageAttributes> class has many properties that you can use to modify images during rendering.</span></span> <span data-ttu-id="64340-107">在下列範例中，<xref:System.Drawing.Imaging.ImageAttributes>物件用於設定所有 alpha 值的這些 80%。</span><span class="sxs-lookup"><span data-stu-id="64340-107">In the following example, an <xref:System.Drawing.Imaging.ImageAttributes> object is used to set all the alpha values to 80 percent of what they were.</span></span> <span data-ttu-id="64340-108">這是初始化色彩矩陣和 alpha 縮放比例值為 0.8 矩陣中的設定。</span><span class="sxs-lookup"><span data-stu-id="64340-108">This is done by initializing a color matrix and setting the alpha scaling value in the matrix to 0.8.</span></span> <span data-ttu-id="64340-109">色彩矩陣的位址傳遞給<xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A>方法<xref:System.Drawing.Imaging.ImageAttributes>物件，而<xref:System.Drawing.Imaging.ImageAttributes>物件傳遞至<xref:System.Drawing.Graphics.DrawString%2A>方法<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="64340-109">The address of the color matrix is passed to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object, and the <xref:System.Drawing.Imaging.ImageAttributes> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="64340-110">在呈現期間，在點陣圖的 alpha 值會轉換成原先的 80%。</span><span class="sxs-lookup"><span data-stu-id="64340-110">During rendering, the alpha values in the bitmap are converted to 80 percent of what they were.</span></span> <span data-ttu-id="64340-111">這會導致混合與背景的影像。</span><span class="sxs-lookup"><span data-stu-id="64340-111">This results in an image that is blended with the background.</span></span> <span data-ttu-id="64340-112">如下圖所示，點陣圖影像看起來透明的;您可以查看透過它與實心黑色線條。</span><span class="sxs-lookup"><span data-stu-id="64340-112">As the following illustration shows, the bitmap image looks transparent; you can see the solid black line through it.</span></span>  
  
 <span data-ttu-id="64340-113">![使用矩陣的 alpha 混色](../../../../docs/framework/winforms/advanced/media/image2.png "image2")</span><span class="sxs-lookup"><span data-stu-id="64340-113">![Alpha Blending Using a Matrix](../../../../docs/framework/winforms/advanced/media/image2.png "image2")</span></span>  
  
 <span data-ttu-id="64340-114">影像是白色背景的部分，其中具有與白色混合映像。</span><span class="sxs-lookup"><span data-stu-id="64340-114">Where the image is over the white portion of the background, the image has been blended with the color white.</span></span> <span data-ttu-id="64340-115">映像的黑色線條交點映像會與黑色混合。</span><span class="sxs-lookup"><span data-stu-id="64340-115">Where the image crosses the black line, the image is blended with the color black.</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="64340-116">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="64340-116">Compiling the Code</span></span>  
 <span data-ttu-id="64340-117">上述範例設計用於搭配 Windows Form，且其需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="64340-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64340-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="64340-118">See Also</span></span>  
 [<span data-ttu-id="64340-119">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="64340-119">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="64340-120">Alpha 混色線條和填色</span><span class="sxs-lookup"><span data-stu-id="64340-120">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
