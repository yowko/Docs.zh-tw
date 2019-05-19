---
title: HOW TO：建立線形漸層
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- linear gradients [Windows Forms], creating
- gradients [Windows Forms], creating linear
- colors [Windows Forms], creating linear gradients
- gradients
ms.assetid: 6c88e1cc-1217-4399-ac12-cb37592b9f01
ms.openlocfilehash: e55d27b454579268658192ae56daa52e0b28bb83
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65876048"
---
# <a name="how-to-create-a-linear-gradient"></a><span data-ttu-id="937b1-102">作法：建立線形漸層</span><span class="sxs-lookup"><span data-stu-id="937b1-102">How to: Create a Linear Gradient</span></span>
<span data-ttu-id="937b1-103">GDI + 提供水平、 垂直和對角線形漸層。</span><span class="sxs-lookup"><span data-stu-id="937b1-103">GDI+ provides horizontal, vertical, and diagonal linear gradients.</span></span> <span data-ttu-id="937b1-104">根據預設，線性漸層色彩一致變更。</span><span class="sxs-lookup"><span data-stu-id="937b1-104">By default, the color in a linear gradient changes uniformly.</span></span> <span data-ttu-id="937b1-105">不過，您可以自訂的線性漸層，以便的色彩會變更以非統一的方式。</span><span class="sxs-lookup"><span data-stu-id="937b1-105">However, you can customize a linear gradient so that the color changes in a non-uniform fashion.</span></span>  

> [!NOTE]
> <span data-ttu-id="937b1-106">這篇文章中的範例是呼叫從控制項的方法<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="937b1-106">The examples in this article are methods that are called from a control's <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  

<span data-ttu-id="937b1-107">下列範例填滿線條、 橢圓形和矩形，水平的線性漸層筆刷。</span><span class="sxs-lookup"><span data-stu-id="937b1-107">The following example fills a line, an ellipse, and a rectangle with a horizontal linear gradient brush.</span></span>  
  
<span data-ttu-id="937b1-108"><xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A>建構函式會收到四個引數： 兩個點和兩個色彩。</span><span class="sxs-lookup"><span data-stu-id="937b1-108">The <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> constructor receives four arguments: two points and two colors.</span></span> <span data-ttu-id="937b1-109">第一個點 （0，10） 相關聯的第一個色彩 （紅色），而第二點 （200，10） 的第二個色彩 （藍色） 與相關聯。</span><span class="sxs-lookup"><span data-stu-id="937b1-109">The first point (0, 10) is associated with the first color (red), and the second point (200, 10) is associated with the second color (blue).</span></span> <span data-ttu-id="937b1-110">如您所預期，從所繪製的線條 （0，10） 到 （200，10） 會逐漸從紅色變成藍色。</span><span class="sxs-lookup"><span data-stu-id="937b1-110">As you would expect, the line drawn from (0, 10) to (200, 10) changes gradually from red to blue.</span></span>  
  
 <span data-ttu-id="937b1-111">在點 （0，10） 和 200 （10） 的 10 個不重要。</span><span class="sxs-lookup"><span data-stu-id="937b1-111">The 10s in the points (0, 10) and (200, 10) are not important.</span></span> <span data-ttu-id="937b1-112">重要的是兩個點都有相同的第二個座標 — 它們連接的這條線是水平。</span><span class="sxs-lookup"><span data-stu-id="937b1-112">What is important is that the two points have the same second coordinate — the line connecting them is horizontal.</span></span> <span data-ttu-id="937b1-113">橢圓形和矩形也逐漸從紅色變成藍色，水平座標是從 0 到 200。</span><span class="sxs-lookup"><span data-stu-id="937b1-113">The ellipse and the rectangle also change gradually from red to blue as the horizontal coordinate goes from 0 to 200.</span></span>  
  
 <span data-ttu-id="937b1-114">下圖顯示線條、 橢圓形和矩形。</span><span class="sxs-lookup"><span data-stu-id="937b1-114">The following illustration shows the line, the ellipse, and the rectangle.</span></span> <span data-ttu-id="937b1-115">請注意，之色彩漸層會自行重複增加超過 200 時的水平座標。</span><span class="sxs-lookup"><span data-stu-id="937b1-115">Note that the color gradient repeats itself as the horizontal coordinate increases beyond 200.</span></span>  
  
 ![線條、 橢圓形和矩形填滿漸層色彩。](./media/how-to-create-a-linear-gradient/gradient-line-ellipse-rectangle.png)  
  
## <a name="to-use-horizontal-linear-gradients"></a><span data-ttu-id="937b1-117">若要使用水平的線性漸層</span><span class="sxs-lookup"><span data-stu-id="937b1-117">To use horizontal linear gradients</span></span>  
  
- <span data-ttu-id="937b1-118">傳入的不透明的紅色及不透明藍色分別做為第三個和第四個引數。</span><span class="sxs-lookup"><span data-stu-id="937b1-118">Pass in the opaque red and opaque blue as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 <span data-ttu-id="937b1-119">在上述範例中，，當您從水平座標 0 移到水平座標，為 200 的大小時色彩元件會以線性方式變更。</span><span class="sxs-lookup"><span data-stu-id="937b1-119">In the preceding example, the color components change linearly as you move from a horizontal coordinate of 0 to a horizontal coordinate of 200.</span></span> <span data-ttu-id="937b1-120">比方說，其第一個座標為偶數，介於 0 到 200 之間的點必須是介於 0 到 255 之間的中間的藍色元件。</span><span class="sxs-lookup"><span data-stu-id="937b1-120">For example, a point whose first coordinate is halfway between 0 and 200 will have a blue component that is halfway between 0 and 255.</span></span>  
  
 <span data-ttu-id="937b1-121">GDI + 可讓您調整色彩之間而異的漸層的一個邊緣的方式。</span><span class="sxs-lookup"><span data-stu-id="937b1-121">GDI+ allows you to adjust the way a color varies from one edge of a gradient to the other.</span></span> <span data-ttu-id="937b1-122">假設您想要建立從黑色變成紅色，根據下表的漸層筆刷。</span><span class="sxs-lookup"><span data-stu-id="937b1-122">Suppose you want to create a gradient brush that changes from black to red according to the following table.</span></span>  
  
|<span data-ttu-id="937b1-123">水平座標</span><span class="sxs-lookup"><span data-stu-id="937b1-123">Horizontal coordinate</span></span>|<span data-ttu-id="937b1-124">RGB 元件</span><span class="sxs-lookup"><span data-stu-id="937b1-124">RGB components</span></span>|  
|---------------------------|--------------------|  
|<span data-ttu-id="937b1-125">0</span><span class="sxs-lookup"><span data-stu-id="937b1-125">0</span></span>|<span data-ttu-id="937b1-126">(0, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="937b1-126">(0, 0, 0)</span></span>|  
|<span data-ttu-id="937b1-127">40</span><span class="sxs-lookup"><span data-stu-id="937b1-127">40</span></span>|<span data-ttu-id="937b1-128">(128, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="937b1-128">(128, 0, 0)</span></span>|  
|<span data-ttu-id="937b1-129">200</span><span class="sxs-lookup"><span data-stu-id="937b1-129">200</span></span>|<span data-ttu-id="937b1-130">(255, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="937b1-130">(255, 0, 0)</span></span>|  
  
 <span data-ttu-id="937b1-131">請注意，紅色元件在半強度時的水平座標是僅有百分之 20 的從 0 到 200 個的方式。</span><span class="sxs-lookup"><span data-stu-id="937b1-131">Note that the red component is at half intensity when the horizontal coordinate is only 20 percent of the way from 0 to 200.</span></span>  
  
 <span data-ttu-id="937b1-132">下列範例會設定<xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A?displayProperty=nameWithType>三個相對的位置與相關三個相對強度屬性。</span><span class="sxs-lookup"><span data-stu-id="937b1-132">The following example sets the <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A?displayProperty=nameWithType> property to associate three relative intensities with three relative positions.</span></span> <span data-ttu-id="937b1-133">如同上表中，為 0.5 的相對強度是 0.2 的相對位置相關聯。</span><span class="sxs-lookup"><span data-stu-id="937b1-133">As in the preceding table, a relative intensity of 0.5 is associated with a relative position of 0.2.</span></span> <span data-ttu-id="937b1-134">橢圓形和漸層筆刷的矩形，會填滿的程式碼。</span><span class="sxs-lookup"><span data-stu-id="937b1-134">The code fills an ellipse and a rectangle with the gradient brush.</span></span>  
  
 <span data-ttu-id="937b1-135">下圖顯示產生的橢圓形和矩形。</span><span class="sxs-lookup"><span data-stu-id="937b1-135">The following illustration shows the resulting ellipse and rectangle.</span></span>  
  
 ![橢圓形和矩形填滿水平的色彩漸層。](./media/how-to-create-a-linear-gradient/gradient-ellipse-rectangle.png)  

## <a name="to-customize-linear-gradients"></a><span data-ttu-id="937b1-137">若要自訂線性漸層</span><span class="sxs-lookup"><span data-stu-id="937b1-137">To customize linear gradients</span></span>  
  
- <span data-ttu-id="937b1-138">傳入的不透明黑色及不透明的紅色分別做為第三個和第四個引數。</span><span class="sxs-lookup"><span data-stu-id="937b1-138">Pass in the opaque black and opaque red as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 <span data-ttu-id="937b1-139">在上述範例中的漸層已水平;也就是，色彩會逐漸當您移動任何水平對齊。</span><span class="sxs-lookup"><span data-stu-id="937b1-139">The gradients in the preceding examples have been horizontal; that is, the color changes gradually as you move along any horizontal line.</span></span> <span data-ttu-id="937b1-140">您也可以定義垂直漸層和對角線的漸層。</span><span class="sxs-lookup"><span data-stu-id="937b1-140">You can also define vertical gradients and diagonal gradients.</span></span>  
  
 <span data-ttu-id="937b1-141">下列範例會將點 （0，0） 和 （200，100） 傳遞給<xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A>建構函式。</span><span class="sxs-lookup"><span data-stu-id="937b1-141">The following example passes the points (0, 0) and (200, 100) to a <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> constructor.</span></span> <span data-ttu-id="937b1-142">藍色相關聯 （0，0） 和相關聯的綠色 （200，100）。</span><span class="sxs-lookup"><span data-stu-id="937b1-142">The color blue is associated with (0, 0), and the color green is associated with (200, 100).</span></span> <span data-ttu-id="937b1-143">（包含畫筆寬度為 10） 的線條和 ellipse 會以線性漸層筆刷填滿。</span><span class="sxs-lookup"><span data-stu-id="937b1-143">A line (with pen width 10) and an ellipse are filled with the linear gradient brush.</span></span>  
  
 <span data-ttu-id="937b1-144">下圖顯示的一行，並省略符號。</span><span class="sxs-lookup"><span data-stu-id="937b1-144">The following illustration shows the line and the ellipse.</span></span> <span data-ttu-id="937b1-145">請注意，在 ellipse 變更色彩逐漸沿著任何移動線是兩點的直線通過 （0，0） 和 （200，100）。</span><span class="sxs-lookup"><span data-stu-id="937b1-145">Note that the color in the ellipse changes gradually as you move along any line that is parallel to the line passing through (0, 0) and (200, 100).</span></span>  
  
 ![線條和橢圓形以對角線的色彩漸層填滿。](./media/how-to-create-a-linear-gradient/gradient-line-ellipse.png)  
  
## <a name="to-create-diagonal-linear-gradients"></a><span data-ttu-id="937b1-147">若要建立對角線的線性漸層</span><span class="sxs-lookup"><span data-stu-id="937b1-147">To create diagonal linear gradients</span></span>  
  
- <span data-ttu-id="937b1-148">傳入的不透明的藍色及不透明綠色分別做為第三個和第四個引數。</span><span class="sxs-lookup"><span data-stu-id="937b1-148">Pass in the opaque blue and opaque green as the third and fourth argument, respectively.</span></span>  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="937b1-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="937b1-149">See also</span></span>

- [<span data-ttu-id="937b1-150">使用漸層筆刷填滿形狀</span><span class="sxs-lookup"><span data-stu-id="937b1-150">Using a Gradient Brush to Fill Shapes</span></span>](using-a-gradient-brush-to-fill-shapes.md)
- [<span data-ttu-id="937b1-151">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="937b1-151">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
