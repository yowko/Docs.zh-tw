---
title: HOW TO：將 Gamma 修正套用至漸層
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- gradient brushes [Windows Forms], gamma correction
- gradients [Windows Forms], gamma correction
ms.assetid: da4690e7-5fac-4fd2-b3f0-5cb35c165b92
ms.openlocfilehash: 7290b7901714e9b71bda3f85f930f5331b8fd4ab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077325"
---
# <a name="how-to-apply-gamma-correction-to-a-gradient"></a><span data-ttu-id="c89af-102">HOW TO：將 Gamma 修正套用至漸層</span><span class="sxs-lookup"><span data-stu-id="c89af-102">How to: Apply Gamma Correction to a Gradient</span></span>
<span data-ttu-id="c89af-103">您可以藉由設定筆刷的線性漸層筆刷的 gamma 修正<xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="c89af-103">You can enable gamma correction for a linear gradient brush by setting the brush's <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> property to `true`.</span></span> <span data-ttu-id="c89af-104">您可以設定連線，停用 gamma 修正<xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A>屬性設`false`。</span><span class="sxs-lookup"><span data-stu-id="c89af-104">You can disable gamma correction by setting the <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> property to `false`.</span></span> <span data-ttu-id="c89af-105">預設會停用 gamma 修正。</span><span class="sxs-lookup"><span data-stu-id="c89af-105">Gamma correction is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c89af-106">範例</span><span class="sxs-lookup"><span data-stu-id="c89af-106">Example</span></span>  
 <span data-ttu-id="c89af-107">範例會建立線形漸層筆刷，並使用以填滿兩個矩形的筆刷。</span><span class="sxs-lookup"><span data-stu-id="c89af-107">The example creates a linear gradient brush and uses that brush to fill two rectangles.</span></span> <span data-ttu-id="c89af-108">Gamma 修正沒有填滿第一個矩形，第二個矩形填滿的 gamma 修正。</span><span class="sxs-lookup"><span data-stu-id="c89af-108">The first rectangle is filled without gamma correction, and the second rectangle is filled with gamma correction.</span></span>  
  
 <span data-ttu-id="c89af-109">下圖顯示兩個填滿的矩形。</span><span class="sxs-lookup"><span data-stu-id="c89af-109">The following illustration shows the two filled rectangles.</span></span> <span data-ttu-id="c89af-110">最上方的矩形，並沒有 gamma 修正，會在中間項目出現深。</span><span class="sxs-lookup"><span data-stu-id="c89af-110">The top rectangle, which does not have gamma correction, appears dark in the middle.</span></span> <span data-ttu-id="c89af-111">下方的矩形，其具有 gamma 修正，似乎有多個統一的濃度。</span><span class="sxs-lookup"><span data-stu-id="c89af-111">The bottom rectangle, which has gamma correction, appears to have more uniform intensity.</span></span>  
  
 <span data-ttu-id="c89af-112">![漸層停駐](./media/gammagradient1.png "gammagradient1")</span><span class="sxs-lookup"><span data-stu-id="c89af-112">![Gradient](./media/gammagradient1.png "gammagradient1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c89af-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="c89af-113">Compiling the Code</span></span>  
 <span data-ttu-id="c89af-114">上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="c89af-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c89af-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c89af-115">See also</span></span>

- <xref:System.Drawing.Drawing2D.LinearGradientBrush>
- [<span data-ttu-id="c89af-116">使用漸層筆刷填滿形狀</span><span class="sxs-lookup"><span data-stu-id="c89af-116">Using a Gradient Brush to Fill Shapes</span></span>](using-a-gradient-brush-to-fill-shapes.md)
