---
title: HOW TO：聯結線條
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- miter line join style
- bevel line join style
- line join
- drawing [Windows Forms], joining lines
- GraphicsPath object
- round line join style
- lines [Windows Forms], joining
- graphics [Windows Forms], joining lines
ms.assetid: 9fc480c2-3c75-4fd1-8ab5-296a99e820e2
ms.openlocfilehash: 445d7f12f57137c6b06a074eeaf0574eb027a723
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174911"
---
# <a name="how-to-join-lines"></a><span data-ttu-id="9b1d3-102">HOW TO：聯結線條</span><span class="sxs-lookup"><span data-stu-id="9b1d3-102">How to: Join Lines</span></span>
<span data-ttu-id="9b1d3-103">線條聯結是指的常見區域由其結束符合或重疊的兩行所構成。</span><span class="sxs-lookup"><span data-stu-id="9b1d3-103">A line join is the common area that is formed by two lines whose ends meet or overlap.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="9b1d3-104">提供三個線條聯結樣式： 儀表、 斜面，和捨入。</span><span class="sxs-lookup"><span data-stu-id="9b1d3-104">provides three line join styles: miter, bevel, and round.</span></span> <span data-ttu-id="9b1d3-105">線條聯結樣式是屬性<xref:System.Drawing.Pen>類別。</span><span class="sxs-lookup"><span data-stu-id="9b1d3-105">Line join style is a property of the <xref:System.Drawing.Pen> class.</span></span> <span data-ttu-id="9b1d3-106">當您指定的線條聯結樣式<xref:System.Drawing.Pen>物件，將會聯結樣式套用到所有連接的直線，任何<xref:System.Drawing.Drawing2D.GraphicsPath>使用該畫筆繪製的物件。</span><span class="sxs-lookup"><span data-stu-id="9b1d3-106">When you specify a line join style for a <xref:System.Drawing.Pen> object, that join style will be applied to all the connected lines in any <xref:System.Drawing.Drawing2D.GraphicsPath> object drawn using that pen.</span></span>  
  
 <span data-ttu-id="9b1d3-107">下圖顯示斜面的線條聯結範例的結果。</span><span class="sxs-lookup"><span data-stu-id="9b1d3-107">The following illustration shows the results of the beveled line join example.</span></span>  
  
 ![顯示圖例，線條的聯結。](./media/how-to-join-lines/joined-beveled-lines.gif)  
  
## <a name="example"></a><span data-ttu-id="9b1d3-109">範例</span><span class="sxs-lookup"><span data-stu-id="9b1d3-109">Example</span></span>  
 <span data-ttu-id="9b1d3-110">您可以使用來指定線條聯結樣式<xref:System.Drawing.Pen.LineJoin%2A>屬性<xref:System.Drawing.Pen>類別。</span><span class="sxs-lookup"><span data-stu-id="9b1d3-110">You can specify the line join style by using the <xref:System.Drawing.Pen.LineJoin%2A> property of the <xref:System.Drawing.Pen> class.</span></span> <span data-ttu-id="9b1d3-111">此範例示範斜切的線之間的聯結的水平線和垂直線。</span><span class="sxs-lookup"><span data-stu-id="9b1d3-111">The example demonstrates a beveled line join between a horizontal line and a vertical line.</span></span> <span data-ttu-id="9b1d3-112">下列程式碼的值<xref:System.Drawing.Drawing2D.LineJoin.Bevel>指派給<xref:System.Drawing.Pen.LineJoin%2A>屬性是成員的<xref:System.Drawing.Drawing2D.LineJoin>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="9b1d3-112">In the following code, the value <xref:System.Drawing.Drawing2D.LineJoin.Bevel> assigned to the <xref:System.Drawing.Pen.LineJoin%2A> property is a member of the <xref:System.Drawing.Drawing2D.LineJoin> enumeration.</span></span> <span data-ttu-id="9b1d3-113">其他成員<xref:System.Drawing.Drawing2D.LineJoin>列舉型別都<xref:System.Drawing.Drawing2D.LineJoin.Miter>和<xref:System.Drawing.Drawing2D.LineJoin.Round>。</span><span class="sxs-lookup"><span data-stu-id="9b1d3-113">The other members of the <xref:System.Drawing.Drawing2D.LineJoin> enumeration are <xref:System.Drawing.Drawing2D.LineJoin.Miter> and <xref:System.Drawing.Drawing2D.LineJoin.Round>.</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9b1d3-114">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="9b1d3-114">Compiling the Code</span></span>  
 <span data-ttu-id="9b1d3-115">上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="9b1d3-115">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b1d3-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b1d3-116">See also</span></span>

- [<span data-ttu-id="9b1d3-117">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="9b1d3-117">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
