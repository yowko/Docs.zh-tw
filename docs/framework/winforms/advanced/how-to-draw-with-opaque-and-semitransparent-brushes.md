---
title: HOW TO：使用不透明和半透明筆刷繪製
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- semi-transparent shapes [Windows Forms], drawing
- transparency [Windows Forms], semi-transparent shapes
- alpha blending [Windows Forms], brush
- brushes [Windows Forms], using semi-transparent
ms.assetid: a4f6f6b8-3bc8-440a-84af-d62ef0f8ff40
ms.openlocfilehash: a302b8bf978afcead5768fadeb6336c1ece986ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004119"
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a><span data-ttu-id="25f3b-102">HOW TO：使用不透明和半透明筆刷繪製</span><span class="sxs-lookup"><span data-stu-id="25f3b-102">How to: Draw with Opaque and Semitransparent Brushes</span></span>
<span data-ttu-id="25f3b-103">當您填滿形狀時，您必須傳遞 <xref:System.Drawing.Brush> 物件至 <xref:System.Drawing.Graphics> 類別的其中一種填滿方法。</span><span class="sxs-lookup"><span data-stu-id="25f3b-103">When you fill a shape, you must pass a <xref:System.Drawing.Brush> object to one of the fill methods of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="25f3b-104"><xref:System.Drawing.SolidBrush.%23ctor%2A> 建構函式的參數是 <xref:System.Drawing.Color> 物件。</span><span class="sxs-lookup"><span data-stu-id="25f3b-104">The one parameter of the <xref:System.Drawing.SolidBrush.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object.</span></span> <span data-ttu-id="25f3b-105">若要填滿不透明的圖形，請設定色彩的 Alpha 元件為 255。</span><span class="sxs-lookup"><span data-stu-id="25f3b-105">To fill an opaque shape, set the alpha component of the color to 255.</span></span> <span data-ttu-id="25f3b-106">若要填滿半透明的圖案，請設定 Alpha 元件為從 1 到 254 的任何值。</span><span class="sxs-lookup"><span data-stu-id="25f3b-106">To fill a semitransparent shape, set the alpha component to any value from 1 through 254.</span></span>  
  
 <span data-ttu-id="25f3b-107">當您填滿半透明的圖案時，圖案的色彩會與背景的色彩混合。</span><span class="sxs-lookup"><span data-stu-id="25f3b-107">When you fill a semitransparent shape, the color of the shape is blended with the colors of the background.</span></span> <span data-ttu-id="25f3b-108">Alpha 元件指定如何混合圖案和背景色彩；接近於 0 的 Alpha 值給予背景色彩較多的權重，而接近 255 的 Alpha 值給予圖形色彩較多的權重。</span><span class="sxs-lookup"><span data-stu-id="25f3b-108">The alpha component specifies how the shape and background colors are mixed; alpha values near 0 place more weight on the background colors, and alpha values near 255 place more weight on the shape color.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25f3b-109">範例</span><span class="sxs-lookup"><span data-stu-id="25f3b-109">Example</span></span>  
 <span data-ttu-id="25f3b-110">下列範例會繪製點陣圖，然後填滿重疊點陣圖的三個橢圓形。</span><span class="sxs-lookup"><span data-stu-id="25f3b-110">The following example draws a bitmap and then fills three ellipses that overlap the bitmap.</span></span> <span data-ttu-id="25f3b-111">第一個橢圓形使用的 Alpha 元件為 255，所以是不透明的。</span><span class="sxs-lookup"><span data-stu-id="25f3b-111">The first ellipse uses an alpha component of 255, so it is opaque.</span></span> <span data-ttu-id="25f3b-112">第二個和第三個橢圓形使用的 Alpha 元件為 128，因此是半透明的；您可以看到穿透橢圓形的背景影像。</span><span class="sxs-lookup"><span data-stu-id="25f3b-112">The second and third ellipses use an alpha component of 128, so they are semitransparent; you can see the background image through the ellipses.</span></span> <span data-ttu-id="25f3b-113">設定 <xref:System.Drawing.Graphics.CompositingQuality%2A> 屬性的呼叫會讓第三個橢圓形搭配 Gamma 修正進行混色。</span><span class="sxs-lookup"><span data-stu-id="25f3b-113">The call that sets the <xref:System.Drawing.Graphics.CompositingQuality%2A> property causes the blending for the third ellipse to be done in conjunction with gamma correction.</span></span>  

 [!code-csharp[System.Drawing.AlphaBlending#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  

 <span data-ttu-id="25f3b-114">下圖顯示下列程式碼的輸出：</span><span class="sxs-lookup"><span data-stu-id="25f3b-114">The following illustration shows the output of the following code:</span></span> 
  
 ![顯示圖例，不透明和半透明的輸出。](./media/how-to-draw-with-opaque-and-semitransparent-brushes/compositingquality-ellipse-semitransparent.png)  
  
## <a name="compiling-the-code"></a><span data-ttu-id="25f3b-116">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="25f3b-116">Compiling the Code</span></span>  
 <span data-ttu-id="25f3b-117">上述範例設計是為搭配 Windows Form 使用所設計，而且需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，這是 <xref:System.Windows.Forms.PaintEventHandler> 的參數。</span><span class="sxs-lookup"><span data-stu-id="25f3b-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25f3b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25f3b-118">See also</span></span>

- [<span data-ttu-id="25f3b-119">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="25f3b-119">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="25f3b-120">Alpha 混色線條和填色</span><span class="sxs-lookup"><span data-stu-id="25f3b-120">Alpha Blending Lines and Fills</span></span>](alpha-blending-lines-and-fills.md)
- [<span data-ttu-id="25f3b-121">如何：為控制項提供透明背景</span><span class="sxs-lookup"><span data-stu-id="25f3b-121">How to: Give Your Control a Transparent Background</span></span>](../controls/how-to-give-your-control-a-transparent-background.md)
- [<span data-ttu-id="25f3b-122">如何：繪製不透明和半透明線條</span><span class="sxs-lookup"><span data-stu-id="25f3b-122">How to: Draw Opaque and Semitransparent Lines</span></span>](how-to-draw-opaque-and-semitransparent-lines.md)
