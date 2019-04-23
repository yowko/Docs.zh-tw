---
title: HOW TO：使用影線圖樣填滿形狀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- patterns [Windows Forms], adding to shapes
- shapes [Windows Forms], filling with patterns
- brushes [Windows Forms], using hatch brushes
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
ms.openlocfilehash: f5399c4151b335090f4b93be041375b8c2781afa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59118114"
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a><span data-ttu-id="034e4-102">HOW TO：使用影線圖樣填滿形狀</span><span class="sxs-lookup"><span data-stu-id="034e4-102">How to: Fill a Shape with a Hatch Pattern</span></span>
<span data-ttu-id="034e4-103">從兩個色彩來進行以規劃圖樣： 一個用於背景，一個在背景上形成模式的程式碼行。</span><span class="sxs-lookup"><span data-stu-id="034e4-103">A hatch pattern is made from two colors: one for the background and one for the lines that form the pattern over the background.</span></span> <span data-ttu-id="034e4-104">若要以規劃圖樣填滿一個封閉的形狀，請使用<xref:System.Drawing.Drawing2D.HatchBrush>物件。</span><span class="sxs-lookup"><span data-stu-id="034e4-104">To fill a closed shape with a hatch pattern, use a <xref:System.Drawing.Drawing2D.HatchBrush> object.</span></span> <span data-ttu-id="034e4-105">下列範例示範如何使用以規劃圖樣填滿橢圓形：</span><span class="sxs-lookup"><span data-stu-id="034e4-105">The following example demonstrates how to fill an ellipse with a hatch pattern:</span></span>  
  
## <a name="example"></a><span data-ttu-id="034e4-106">範例</span><span class="sxs-lookup"><span data-stu-id="034e4-106">Example</span></span>  
 <span data-ttu-id="034e4-107"><xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A>建構函式接受三個引數： 影線樣式、 規劃線條、 色彩和背景的色彩。</span><span class="sxs-lookup"><span data-stu-id="034e4-107">The <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> constructor takes three arguments: the hatch style, the color of the hatch line, and the color of the background.</span></span> <span data-ttu-id="034e4-108">影線樣式引數可以是任何值<xref:System.Drawing.Drawing2D.HatchStyle>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="034e4-108">The hatch style argument can be any value from the <xref:System.Drawing.Drawing2D.HatchStyle> enumeration.</span></span> <span data-ttu-id="034e4-109">有 50 位以上的項目中<xref:System.Drawing.Drawing2D.HatchStyle>列舉型別，其中幾個項目會顯示下面清單中：</span><span class="sxs-lookup"><span data-stu-id="034e4-109">There are more than fifty elements in the <xref:System.Drawing.Drawing2D.HatchStyle> enumeration; a few of those elements are shown in the following list:</span></span>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 <span data-ttu-id="034e4-110">下圖顯示實心的橢圓形。</span><span class="sxs-lookup"><span data-stu-id="034e4-110">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="034e4-111">![影線圖樣](./media/hatch1.png "hatch1")</span><span class="sxs-lookup"><span data-stu-id="034e4-111">![Hatch Pattern](./media/hatch1.png "hatch1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="034e4-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="034e4-112">Compiling the Code</span></span>  
 <span data-ttu-id="034e4-113">上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="034e4-113">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="034e4-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="034e4-114">See also</span></span>

- [<span data-ttu-id="034e4-115">使用筆刷填滿形狀</span><span class="sxs-lookup"><span data-stu-id="034e4-115">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
