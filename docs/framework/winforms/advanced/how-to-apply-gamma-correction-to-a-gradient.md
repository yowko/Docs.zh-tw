---
title: "如何：將 Gamma 修正套用至漸層"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- gradient brushes [Windows Forms], gamma correction
- gradients [Windows Forms], gamma correction
ms.assetid: da4690e7-5fac-4fd2-b3f0-5cb35c165b92
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6321894c86f340154bd37f50e81ea8a58a2e0896
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-gamma-correction-to-a-gradient"></a><span data-ttu-id="5fc69-102">如何：將 Gamma 修正套用至漸層</span><span class="sxs-lookup"><span data-stu-id="5fc69-102">How to: Apply Gamma Correction to a Gradient</span></span>
<span data-ttu-id="5fc69-103">您可以藉由設定筆刷的啟用線性漸層筆刷的 gamma 修正<xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="5fc69-103">You can enable gamma correction for a linear gradient brush by setting the brush's <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> property to `true`.</span></span> <span data-ttu-id="5fc69-104">您可以藉由設定停用 gamma 修正<xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A>屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="5fc69-104">You can disable gamma correction by setting the <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> property to `false`.</span></span> <span data-ttu-id="5fc69-105">預設為停用 gamma 修正。</span><span class="sxs-lookup"><span data-stu-id="5fc69-105">Gamma correction is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fc69-106">範例</span><span class="sxs-lookup"><span data-stu-id="5fc69-106">Example</span></span>  
 <span data-ttu-id="5fc69-107">範例會建立線形漸層筆刷，並使用該筆刷填滿兩個矩形。</span><span class="sxs-lookup"><span data-stu-id="5fc69-107">The example creates a linear gradient brush and uses that brush to fill two rectangles.</span></span> <span data-ttu-id="5fc69-108">Gamma 修正沒有填滿第一個矩形，第二個矩形會填入 gamma 修正。</span><span class="sxs-lookup"><span data-stu-id="5fc69-108">The first rectangle is filled without gamma correction, and the second rectangle is filled with gamma correction.</span></span>  
  
 <span data-ttu-id="5fc69-109">下圖顯示兩個填滿的矩形。</span><span class="sxs-lookup"><span data-stu-id="5fc69-109">The following illustration shows the two filled rectangles.</span></span> <span data-ttu-id="5fc69-110">最上層的矩形中，並沒有 gamma 修正顯示暗色，中間。</span><span class="sxs-lookup"><span data-stu-id="5fc69-110">The top rectangle, which does not have gamma correction, appears dark in the middle.</span></span> <span data-ttu-id="5fc69-111">下方的矩形，gamma 修正，其看似具有濃度較為一致。</span><span class="sxs-lookup"><span data-stu-id="5fc69-111">The bottom rectangle, which has gamma correction, appears to have more uniform intensity.</span></span>  
  
 <span data-ttu-id="5fc69-112">![漸層停駐](../../../../docs/framework/winforms/advanced/media/gammagradient1.png "gammagradient1")</span><span class="sxs-lookup"><span data-stu-id="5fc69-112">![Gradient](../../../../docs/framework/winforms/advanced/media/gammagradient1.png "gammagradient1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5fc69-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="5fc69-113">Compiling the Code</span></span>  
 <span data-ttu-id="5fc69-114">上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="5fc69-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fc69-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="5fc69-115">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush>  
 [<span data-ttu-id="5fc69-116">使用漸層筆刷填滿形狀</span><span class="sxs-lookup"><span data-stu-id="5fc69-116">Using a Gradient Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)
