---
title: 如何：使用色彩矩陣設定影像中的 Alpha 值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using color matrices for semi-transparent
- transparency [Windows Forms], color matrices
- matrices [Windows Forms], alpha values
- bitmaps [Windows Forms], using color matrices for semi-transparent
ms.assetid: a27121e6-f7e9-4c09-84e2-f05aa9d2a1bb
ms.openlocfilehash: 73e820845d040856a0ae367da8b9371ad6afa142
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423719"
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a><span data-ttu-id="95293-102">如何：使用色彩矩陣設定影像中的 Alpha 值</span><span class="sxs-lookup"><span data-stu-id="95293-102">How to: Use a Color Matrix to Set Alpha Values in Images</span></span>
<span data-ttu-id="95293-103"><xref:System.Drawing.Bitmap> 類別（繼承自 <xref:System.Drawing.Image> 類別）和 <xref:System.Drawing.Imaging.ImageAttributes> 類別提供用來取得和設定圖元值的功能。</span><span class="sxs-lookup"><span data-stu-id="95293-103">The <xref:System.Drawing.Bitmap> class (which inherits from the <xref:System.Drawing.Image> class) and the <xref:System.Drawing.Imaging.ImageAttributes> class provide functionality for getting and setting pixel values.</span></span> <span data-ttu-id="95293-104">您可以使用 <xref:System.Drawing.Imaging.ImageAttributes> 類別來修改整個影像的 Alpha 值，也可以呼叫 <xref:System.Drawing.Bitmap> 類別的 <xref:System.Drawing.Bitmap.SetPixel%2A> 方法來修改個別的圖元值。</span><span class="sxs-lookup"><span data-stu-id="95293-104">You can use the <xref:System.Drawing.Imaging.ImageAttributes> class to modify the alpha values for an entire image, or you can call the <xref:System.Drawing.Bitmap.SetPixel%2A> method of the <xref:System.Drawing.Bitmap> class to modify individual pixel values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95293-105">範例</span><span class="sxs-lookup"><span data-stu-id="95293-105">Example</span></span>  
 <span data-ttu-id="95293-106"><xref:System.Drawing.Imaging.ImageAttributes> 類別有許多屬性，可讓您在呈現期間用來修改影像。</span><span class="sxs-lookup"><span data-stu-id="95293-106">The <xref:System.Drawing.Imaging.ImageAttributes> class has many properties that you can use to modify images during rendering.</span></span> <span data-ttu-id="95293-107">在下列範例中，會使用 <xref:System.Drawing.Imaging.ImageAttributes> 物件，將所有 Alpha 值設定為其過去的80%。</span><span class="sxs-lookup"><span data-stu-id="95293-107">In the following example, an <xref:System.Drawing.Imaging.ImageAttributes> object is used to set all the alpha values to 80 percent of what they were.</span></span> <span data-ttu-id="95293-108">這是藉由初始化色彩矩陣，並將矩陣中的 Alpha 縮放值設定為0.8 來完成。</span><span class="sxs-lookup"><span data-stu-id="95293-108">This is done by initializing a color matrix and setting the alpha scaling value in the matrix to 0.8.</span></span> <span data-ttu-id="95293-109">色彩矩陣的位址會傳遞至 <xref:System.Drawing.Imaging.ImageAttributes> 物件的 <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> 方法，而 <xref:System.Drawing.Imaging.ImageAttributes> 物件會傳遞至 <xref:System.Drawing.Graphics> 物件的 <xref:System.Drawing.Graphics.DrawString%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="95293-109">The address of the color matrix is passed to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object, and the <xref:System.Drawing.Imaging.ImageAttributes> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="95293-110">在轉譯期間，點陣圖中的 Alpha 值會轉換成其過去的80%。</span><span class="sxs-lookup"><span data-stu-id="95293-110">During rendering, the alpha values in the bitmap are converted to 80 percent of what they were.</span></span> <span data-ttu-id="95293-111">這會產生與背景混合的影像。</span><span class="sxs-lookup"><span data-stu-id="95293-111">This results in an image that is blended with the background.</span></span> <span data-ttu-id="95293-112">如下圖所示，點陣圖影像看起來是透明的;您可以透過它來查看實心黑色線。</span><span class="sxs-lookup"><span data-stu-id="95293-112">As the following illustration shows, the bitmap image looks transparent; you can see the solid black line through it.</span></span>  
  
 <span data-ttu-id="95293-113">![使用矩陣的 Alpha 混合螢幕擷取畫面。](./media/how-to-use-a-color-matrix-to-set-alpha-values-in-images/alpha-blending-matrix.png "image2）")</span><span class="sxs-lookup"><span data-stu-id="95293-113">![Screenshot of alpha blending using a matrix.](./media/how-to-use-a-color-matrix-to-set-alpha-values-in-images/alpha-blending-matrix.png "image2")</span></span>  
  
 <span data-ttu-id="95293-114">當影像在背景的白色部分上方時，影像就會與白色色彩混合。</span><span class="sxs-lookup"><span data-stu-id="95293-114">Where the image is over the white portion of the background, the image has been blended with the color white.</span></span> <span data-ttu-id="95293-115">影像與黑色線條相交時，影像會以黑色進行混合。</span><span class="sxs-lookup"><span data-stu-id="95293-115">Where the image crosses the black line, the image is blended with the color black.</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="95293-116">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="95293-116">Compiling the Code</span></span>  
 <span data-ttu-id="95293-117">先前的範例是針對與 Windows Forms 搭配使用所設計，而且需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.PaintEventHandler>的參數。</span><span class="sxs-lookup"><span data-stu-id="95293-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95293-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="95293-118">See also</span></span>

- [<span data-ttu-id="95293-119">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="95293-119">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="95293-120">Alpha 混色線條和填色</span><span class="sxs-lookup"><span data-stu-id="95293-120">Alpha Blending Lines and Fills</span></span>](alpha-blending-lines-and-fills.md)
