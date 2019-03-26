---
title: HOW TO：使用複合模式控制 Alpha 混色
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- alpha blending [Windows Forms], compositing
- colors [Windows Forms], blending
- colors [Windows Forms], controlling transparency
ms.assetid: f331df2d-b395-4b0a-95be-24fec8c9bbb5
ms.openlocfilehash: 1a5cf23890cd6183d92e33ec4e24f87c226e8ec3
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2019
ms.locfileid: "58462860"
---
# <a name="how-to-use-compositing-mode-to-control-alpha-blending"></a><span data-ttu-id="4dae4-102">HOW TO：使用複合模式控制 Alpha 混色</span><span class="sxs-lookup"><span data-stu-id="4dae4-102">How to: Use Compositing Mode to Control Alpha Blending</span></span>
<span data-ttu-id="4dae4-103">可能有您想来建立一個幕外的點陣圖，具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="4dae4-103">There may be times when you want to create an off-screen bitmap that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="4dae4-104">色彩必須是小於 255 的 alpha 值。</span><span class="sxs-lookup"><span data-stu-id="4dae4-104">Colors have alpha values that are less than 255.</span></span>  
  
-   <span data-ttu-id="4dae4-105">色彩不 alpha 混色彼此，當您在建立點陣圖。</span><span class="sxs-lookup"><span data-stu-id="4dae4-105">Colors are not alpha blended with each other as you create the bitmap.</span></span>  
  
-   <span data-ttu-id="4dae4-106">當您顯示完成的點陣圖時，點陣圖中的色彩會是 alpha 混色與顯示裝置上的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="4dae4-106">When you display the finished bitmap, colors in the bitmap are alpha blended with the background colors on the display device.</span></span>  
  
 <span data-ttu-id="4dae4-107">若要建立這種點陣圖，建構空白<xref:System.Drawing.Bitmap>物件，然後再建構<xref:System.Drawing.Graphics>物件會根據該點陣圖。</span><span class="sxs-lookup"><span data-stu-id="4dae4-107">To create such a bitmap, construct a blank <xref:System.Drawing.Bitmap> object, and then construct a <xref:System.Drawing.Graphics> object based on that bitmap.</span></span> <span data-ttu-id="4dae4-108">設定的複合 （compositing） 模式<xref:System.Drawing.Graphics>物件至<xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="4dae4-108">Set the compositing mode of the <xref:System.Drawing.Graphics> object to <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4dae4-109">範例</span><span class="sxs-lookup"><span data-stu-id="4dae4-109">Example</span></span>  
 <span data-ttu-id="4dae4-110">下列範例會建立<xref:System.Drawing.Graphics>物件根據<xref:System.Drawing.Bitmap>物件。</span><span class="sxs-lookup"><span data-stu-id="4dae4-110">The following example creates a <xref:System.Drawing.Graphics> object based on a <xref:System.Drawing.Bitmap> object.</span></span> <span data-ttu-id="4dae4-111">此程式碼使用<xref:System.Drawing.Graphics>物件以及兩個半透明筆刷 (alpha = 160) 來繪製點陣圖。</span><span class="sxs-lookup"><span data-stu-id="4dae4-111">The code uses the <xref:System.Drawing.Graphics> object along with two semitransparent brushes (alpha = 160) to paint on the bitmap.</span></span> <span data-ttu-id="4dae4-112">紅色的橢圓形和綠色橢圓形使用半透明筆刷，會填滿的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4dae4-112">The code fills a red ellipse and a green ellipse using the semitransparent brushes.</span></span> <span data-ttu-id="4dae4-113">綠色的橢圓形重疊紅色的省略符號，但因為綠色不會以紅色混合的複合 （compositing） 模式<xref:System.Drawing.Graphics>物件設定為<xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>。</span><span class="sxs-lookup"><span data-stu-id="4dae4-113">The green ellipse overlaps the red ellipse, but the green is not blended with the red because the compositing mode of the <xref:System.Drawing.Graphics> object is set to <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>.</span></span>  
  
 <span data-ttu-id="4dae4-114">程式碼會繪製點陣圖在螢幕上兩次： 彩色背景上白色背景上一次，一次。</span><span class="sxs-lookup"><span data-stu-id="4dae4-114">The code draws the bitmap on the screen twice: once on a white background and once on a multicolored background.</span></span> <span data-ttu-id="4dae4-115">屬於兩個橢圓形的點陣圖中像素會有的 alpha 元件為 160，因此橢圓形會混合與在螢幕上的背景色彩。</span><span class="sxs-lookup"><span data-stu-id="4dae4-115">The pixels in the bitmap that are part of the two ellipses have an alpha component of 160, so the ellipses are blended with the background colors on the screen.</span></span>  
  
 <span data-ttu-id="4dae4-116">下圖顯示程式碼範例的輸出。</span><span class="sxs-lookup"><span data-stu-id="4dae4-116">The following illustration shows the output of the code example.</span></span> <span data-ttu-id="4dae4-117">請注意混合與背景，在省略符號，但它們不能彼此。</span><span class="sxs-lookup"><span data-stu-id="4dae4-117">Note that the ellipses are blended with the background, but they are not blended with each other.</span></span>  
  
 ![圖表顯示省略符號與背景，不互相混合。](./media/how-to-use-compositing-mode-to-control-alpha-blending/ellipses-blended-background.png)  
  
 <span data-ttu-id="4dae4-119">在程式碼範例包含此陳述式：</span><span class="sxs-lookup"><span data-stu-id="4dae4-119">The code example contains this statement:</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.AlphaBlending#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#41)]  
  
 <span data-ttu-id="4dae4-120">如果您想要混合彼此以及與背景的省略符號，請將陳述式變更如下：</span><span class="sxs-lookup"><span data-stu-id="4dae4-120">If you want the ellipses to be blended with each other as well as with the background, change that statement to the following:</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.AlphaBlending#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#42)]  
  
 <span data-ttu-id="4dae4-121">下圖顯示修改過的程式碼的輸出。</span><span class="sxs-lookup"><span data-stu-id="4dae4-121">The following illustration shows the output of the revised code.</span></span>  
  
 ![此圖顯示省略符號混合在一起，並具有背景。](./media/how-to-use-compositing-mode-to-control-alpha-blending/blend-ellipses-background.png)  
  
 [!code-csharp[System.Drawing.AlphaBlending#43](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#43)]
 [!code-vb[System.Drawing.AlphaBlending#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#43)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4dae4-123">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="4dae4-123">Compiling the Code</span></span>  
 <span data-ttu-id="4dae4-124">上述範例設計是為搭配 Windows Form 使用所設計，而且需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，這是 <xref:System.Windows.Forms.PaintEventHandler> 的參數。</span><span class="sxs-lookup"><span data-stu-id="4dae4-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dae4-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4dae4-125">See also</span></span>
- <xref:System.Drawing.Color.FromArgb%2A>
- [<span data-ttu-id="4dae4-126">Alpha 混色線條和填色</span><span class="sxs-lookup"><span data-stu-id="4dae4-126">Alpha Blending Lines and Fills</span></span>](alpha-blending-lines-and-fills.md)
