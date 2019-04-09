---
title: HOW TO：繪製自訂虛線
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], custom
- lines [Windows Forms], drawing
- lines [Windows Forms], dashed
ms.assetid: cd0ed96a-cce4-47b9-b58a-3bae2e3d1bee
ms.openlocfilehash: 8dc1ad41cf8067bea5b811ca126ad29f5a600f69
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109183"
---
# <a name="how-to-draw-a-custom-dashed-line"></a><span data-ttu-id="4d8ec-102">HOW TO：繪製自訂虛線</span><span class="sxs-lookup"><span data-stu-id="4d8ec-102">How to: Draw a Custom Dashed Line</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="4d8ec-103">提供數個虛線樣式中所列<xref:System.Drawing.Drawing2D.DashStyle>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="4d8ec-103">provides several dash styles that are listed in the <xref:System.Drawing.Drawing2D.DashStyle> enumeration.</span></span> <span data-ttu-id="4d8ec-104">如果這些標準的虛線樣式不符合您的需求，您可以建立自訂虛線圖樣。</span><span class="sxs-lookup"><span data-stu-id="4d8ec-104">If those standard dash styles do not suit your needs, you can create a custom dash pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d8ec-105">範例</span><span class="sxs-lookup"><span data-stu-id="4d8ec-105">Example</span></span>  
 <span data-ttu-id="4d8ec-106">若要繪製自訂短折線，陣列中放入虛線和間距的長度和指派的值的陣列<xref:System.Drawing.Pen.DashPattern%2A>屬性<xref:System.Drawing.Pen>物件。</span><span class="sxs-lookup"><span data-stu-id="4d8ec-106">To draw a custom dashed line, put the lengths of the dashes and spaces in an array and assign the array as the value of the <xref:System.Drawing.Pen.DashPattern%2A> property of a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="4d8ec-107">下列範例會繪製自訂短折線根據陣列`{5, 2, 15, 4}`。</span><span class="sxs-lookup"><span data-stu-id="4d8ec-107">The following example draws a custom dashed line based on the array `{5, 2, 15, 4}`.</span></span> <span data-ttu-id="4d8ec-108">如果您將陣列的項目乘以 5 的畫筆寬度時，您會收到`{25, 10, 75, 20}`。</span><span class="sxs-lookup"><span data-stu-id="4d8ec-108">If you multiply the elements of the array by the pen width of 5, you get `{25, 10, 75, 20}`.</span></span> <span data-ttu-id="4d8ec-109">顯示連字號替代的長度介於 25 和 75，之間和替代的長度介於 10 到 20 之間的空格。</span><span class="sxs-lookup"><span data-stu-id="4d8ec-109">The displayed dashes alternate in length between 25 and 75, and the spaces alternate in length between 10 and 20.</span></span>  
  
 <span data-ttu-id="4d8ec-110">下圖顯示產生的虛線。</span><span class="sxs-lookup"><span data-stu-id="4d8ec-110">The following illustration shows the resulting dashed line.</span></span> <span data-ttu-id="4d8ec-111">請注意，最終的 dash 必須是少於 25 個單位，以便在列可以在結束 （405，5）。</span><span class="sxs-lookup"><span data-stu-id="4d8ec-111">Note that the final dash has to be shorter than 25 units so that the line can end at (405, 5).</span></span>  
  
 <span data-ttu-id="4d8ec-112">![顯示一條虛線的圖例。](./media/how-to-draw-a-custom-dashed-line/dashed-line-illustration.gif "pens6")</span><span class="sxs-lookup"><span data-stu-id="4d8ec-112">![Illustration that shows a dashed line.](./media/how-to-draw-a-custom-dashed-line/dashed-line-illustration.gif "pens6")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.UsingAPen#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4d8ec-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="4d8ec-113">Compiling the Code</span></span>  
 <span data-ttu-id="4d8ec-114">建立 Windows 表單，並處理表單的<xref:System.Windows.Forms.Control.Paint>事件。</span><span class="sxs-lookup"><span data-stu-id="4d8ec-114">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="4d8ec-115">貼上上述程式碼到<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="4d8ec-115">Paste the preceding code into the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d8ec-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d8ec-116">See also</span></span>

- [<span data-ttu-id="4d8ec-117">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="4d8ec-117">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
