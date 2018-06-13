---
title: 如何：使用純色填滿形狀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], adding to shapes
- shapes [Windows Forms], filling
ms.assetid: 06088b31-bac9-4ef3-9ebe-06c2c764d6df
ms.openlocfilehash: 7f719417a6a1226d7dc4d600518711ba31920a6c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521319"
---
# <a name="how-to-fill-a-shape-with-a-solid-color"></a><span data-ttu-id="ff34d-102">如何：使用純色填滿形狀</span><span class="sxs-lookup"><span data-stu-id="ff34d-102">How to: Fill a Shape with a Solid Color</span></span>
<span data-ttu-id="ff34d-103">若要利用純色填滿圖形時，建立<xref:System.Drawing.SolidBrush>物件，並再將其傳遞<xref:System.Drawing.SolidBrush>物件做為其中一個填滿方法的引數為<xref:System.Drawing.Graphics>類別。</span><span class="sxs-lookup"><span data-stu-id="ff34d-103">To fill a shape with a solid color, create a <xref:System.Drawing.SolidBrush> object, and then pass that <xref:System.Drawing.SolidBrush> object as an argument to one of the fill methods of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="ff34d-104">下列範例會示範如何使用紅色的色彩填滿橢圓形。</span><span class="sxs-lookup"><span data-stu-id="ff34d-104">The following example shows how to fill an ellipse with the color red.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff34d-105">範例</span><span class="sxs-lookup"><span data-stu-id="ff34d-105">Example</span></span>  
 <span data-ttu-id="ff34d-106">下列程式碼，<xref:System.Drawing.SolidBrush.%23ctor%2A>建構函式接受<xref:System.Drawing.Color>物件做為其唯一的引數。</span><span class="sxs-lookup"><span data-stu-id="ff34d-106">In the following code, the <xref:System.Drawing.SolidBrush.%23ctor%2A> constructor takes a <xref:System.Drawing.Color> object as its only argument.</span></span> <span data-ttu-id="ff34d-107">使用的值<xref:System.Drawing.Color.FromArgb%2A>方法來表示色彩的 alpha、 紅色、 綠色和藍色元件。</span><span class="sxs-lookup"><span data-stu-id="ff34d-107">The values used by the <xref:System.Drawing.Color.FromArgb%2A> method represent the alpha, red, green, and blue components of the color.</span></span> <span data-ttu-id="ff34d-108">每個這些值必須是 0 到 255 範圍內。</span><span class="sxs-lookup"><span data-stu-id="ff34d-108">Each of these values must be in the range 0 through 255.</span></span> <span data-ttu-id="ff34d-109">第一個 255 表示的色彩就是完全不透明，而第二個 255 表示紅色元件的濃度。</span><span class="sxs-lookup"><span data-stu-id="ff34d-109">The first 255 indicates that the color is fully opaque, and the second 255 indicates that the red component is at full intensity.</span></span> <span data-ttu-id="ff34d-110">兩個零表示綠色和藍色元件同時具有 0 的濃度。</span><span class="sxs-lookup"><span data-stu-id="ff34d-110">The two zeros indicate that the green and blue components both have an intensity of 0.</span></span>  
  
 <span data-ttu-id="ff34d-111">四個數字 （0，0，100，60） 傳遞至<xref:System.Drawing.Graphics.FillEllipse%2A>方法指定的位置和大小的橢圓形之周框。</span><span class="sxs-lookup"><span data-stu-id="ff34d-111">The four numbers (0, 0, 100, 60) passed to the <xref:System.Drawing.Graphics.FillEllipse%2A> method specify the location and size of the bounding rectangle for the ellipse.</span></span> <span data-ttu-id="ff34d-112">矩形的左上角 （0，0） 為 100，寬度和高度為 60。</span><span class="sxs-lookup"><span data-stu-id="ff34d-112">The rectangle has an upper-left corner of (0, 0), a width of 100, and a height of 60.</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingABrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ff34d-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ff34d-113">Compiling the Code</span></span>  
 <span data-ttu-id="ff34d-114">上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="ff34d-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff34d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff34d-115">See Also</span></span>  
 [<span data-ttu-id="ff34d-116">使用筆刷填滿形狀</span><span class="sxs-lookup"><span data-stu-id="ff34d-116">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
