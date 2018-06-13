---
title: 如何：繪製不透明和半透明線條
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- transparency [Windows Forms], lines
- lines [Windows Forms], drawing alpha blended
- alpha blending [Windows Forms], drawing lines
ms.assetid: 8f2508af-f495-4223-b5cc-646cbbb520eb
ms.openlocfilehash: f6667b3ac5bbe5dd82198f7bf23047f01cd7350a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524218"
---
# <a name="how-to-draw-opaque-and-semitransparent-lines"></a><span data-ttu-id="b03d8-102">如何：繪製不透明和半透明線條</span><span class="sxs-lookup"><span data-stu-id="b03d8-102">How to: Draw Opaque and Semitransparent Lines</span></span>
<span data-ttu-id="b03d8-103">當您繪製一條線時，必須傳遞 <xref:System.Drawing.Pen> 物件至 <xref:System.Drawing.Graphics> 類別的 <xref:System.Drawing.Graphics.DrawLine%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="b03d8-103">When you draw a line, you must pass a <xref:System.Drawing.Pen> object to the <xref:System.Drawing.Graphics.DrawLine%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="b03d8-104"><xref:System.Drawing.Pen.%23ctor%2A> 建構函式的其中一個參數是 <xref:System.Drawing.Color> 物件。</span><span class="sxs-lookup"><span data-stu-id="b03d8-104">One of the parameters of the <xref:System.Drawing.Pen.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object.</span></span> <span data-ttu-id="b03d8-105">若要繪製不透明的線條，請將色彩的 Alpha 元件設為 255。</span><span class="sxs-lookup"><span data-stu-id="b03d8-105">To draw an opaque line, set the alpha component of the color to 255.</span></span> <span data-ttu-id="b03d8-106">若要繪製半透明線條，請將 Alpha 元件設為從 1 到 254 的任何值。</span><span class="sxs-lookup"><span data-stu-id="b03d8-106">To draw a semitransparent line, set the alpha component to any value from 1 through 254.</span></span>  
  
 <span data-ttu-id="b03d8-107">當您在背景上繪製半透明線條時，線條的色彩會與背景的色彩混合。</span><span class="sxs-lookup"><span data-stu-id="b03d8-107">When you draw a semitransparent line over a background, the color of the line is blended with the colors of the background.</span></span> <span data-ttu-id="b03d8-108">Alpha 元件指定如何混合線條和背景色彩；接近於 0 的 Alpha 值給予背景色彩較多的權重，而接近 255 的 Alpha 值給予線條色彩較多的權重。</span><span class="sxs-lookup"><span data-stu-id="b03d8-108">The alpha component specifies how the line and background colors are mixed; alpha values near 0 place more weight on the background colors, and alpha values near 255 place more weight on the line color.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b03d8-109">範例</span><span class="sxs-lookup"><span data-stu-id="b03d8-109">Example</span></span>  
 <span data-ttu-id="b03d8-110">下列範例會繪製點陣圖，然後繪製以該點陣圖做為背景的三條線。</span><span class="sxs-lookup"><span data-stu-id="b03d8-110">The following example draws a bitmap and then draws three lines that use the bitmap as a background.</span></span> <span data-ttu-id="b03d8-111">第一條線使用的 Alpha 元件為 255，所以是不透明的。</span><span class="sxs-lookup"><span data-stu-id="b03d8-111">The first line uses an alpha component of 255, so it is opaque.</span></span> <span data-ttu-id="b03d8-112">第二和第三條線使用的 Alpha 元件為 128，因此是半透明的；您可以透過線條看到背景影像。</span><span class="sxs-lookup"><span data-stu-id="b03d8-112">The second and third lines use an alpha component of 128, so they are semitransparent; you can see the background image through the lines.</span></span> <span data-ttu-id="b03d8-113">設定 <xref:System.Drawing.Graphics.CompositingQuality%2A> 屬性的陳述式會讓第三條線搭配 Gamma 修正進行混色。</span><span class="sxs-lookup"><span data-stu-id="b03d8-113">The statement that sets the <xref:System.Drawing.Graphics.CompositingQuality%2A> property causes the blending for the third line to be done in conjunction with gamma correction.</span></span>  
  
 <span data-ttu-id="b03d8-114">下圖顯示下列程式碼的輸出。</span><span class="sxs-lookup"><span data-stu-id="b03d8-114">The following illustration shows the output of the following code.</span></span>  
  
 <span data-ttu-id="b03d8-115">![不透明和半透明](../../../../docs/framework/winforms/advanced/media/compqualline.png "compqualline")</span><span class="sxs-lookup"><span data-stu-id="b03d8-115">![Opaque and Semitransparent](../../../../docs/framework/winforms/advanced/media/compqualline.png "compqualline")</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.AlphaBlending#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b03d8-116">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b03d8-116">Compiling the Code</span></span>  
 <span data-ttu-id="b03d8-117">上述範例設計用於搭配 Windows Form，且其需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="b03d8-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b03d8-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b03d8-118">See Also</span></span>  
 [<span data-ttu-id="b03d8-119">Alpha 混色線條和填色</span><span class="sxs-lookup"><span data-stu-id="b03d8-119">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)  
 [<span data-ttu-id="b03d8-120">操作說明：為控制項提供透明背景</span><span class="sxs-lookup"><span data-stu-id="b03d8-120">How to: Give Your Control a Transparent Background</span></span>](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 [<span data-ttu-id="b03d8-121">操作說明：使用不透明和半透明筆刷繪製</span><span class="sxs-lookup"><span data-stu-id="b03d8-121">How to: Draw with Opaque and Semitransparent Brushes</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-with-opaque-and-semitransparent-brushes.md)
