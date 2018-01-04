---
title: "如何：以規劃圖樣填滿形狀"
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
- patterns [Windows Forms], adding to shapes
- shapes [Windows Forms], filling with patterns
- brushes [Windows Forms], using hatch brushes
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f44289b79812f2330639cc333727bd21b6ef4fe6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a><span data-ttu-id="44f64-102">如何：以規劃圖樣填滿形狀</span><span class="sxs-lookup"><span data-stu-id="44f64-102">How to: Fill a Shape with a Hatch Pattern</span></span>
<span data-ttu-id="44f64-103">從兩個色彩來進行規劃圖樣： 一個用於背景，一個背景上形成圖樣的程式碼行。</span><span class="sxs-lookup"><span data-stu-id="44f64-103">A hatch pattern is made from two colors: one for the background and one for the lines that form the pattern over the background.</span></span> <span data-ttu-id="44f64-104">若要規劃圖樣填滿封閉的圖形，請使用<xref:System.Drawing.Drawing2D.HatchBrush>物件。</span><span class="sxs-lookup"><span data-stu-id="44f64-104">To fill a closed shape with a hatch pattern, use a <xref:System.Drawing.Drawing2D.HatchBrush> object.</span></span> <span data-ttu-id="44f64-105">下列範例會示範如何以規劃圖樣填滿橢圓形：</span><span class="sxs-lookup"><span data-stu-id="44f64-105">The following example demonstrates how to fill an ellipse with a hatch pattern:</span></span>  
  
## <a name="example"></a><span data-ttu-id="44f64-106">範例</span><span class="sxs-lookup"><span data-stu-id="44f64-106">Example</span></span>  
 <span data-ttu-id="44f64-107"><xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A>建構函式接受三個引數： 影線樣式、 影線線條的色彩和背景的色彩。</span><span class="sxs-lookup"><span data-stu-id="44f64-107">The <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> constructor takes three arguments: the hatch style, the color of the hatch line, and the color of the background.</span></span> <span data-ttu-id="44f64-108">影線樣式引數可以是任何值<xref:System.Drawing.Drawing2D.HatchStyle>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="44f64-108">The hatch style argument can be any value from the <xref:System.Drawing.Drawing2D.HatchStyle> enumeration.</span></span> <span data-ttu-id="44f64-109">有多個五十個中的項目<xref:System.Drawing.Drawing2D.HatchStyle>列舉，其中幾個項目會顯示下面清單中：</span><span class="sxs-lookup"><span data-stu-id="44f64-109">There are more than fifty elements in the <xref:System.Drawing.Drawing2D.HatchStyle> enumeration; a few of those elements are shown in the following list:</span></span>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 <span data-ttu-id="44f64-110">下圖顯示實心的橢圓形。</span><span class="sxs-lookup"><span data-stu-id="44f64-110">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="44f64-111">![影線圖樣](../../../../docs/framework/winforms/advanced/media/hatch1.png "hatch1")</span><span class="sxs-lookup"><span data-stu-id="44f64-111">![Hatch Pattern](../../../../docs/framework/winforms/advanced/media/hatch1.png "hatch1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="44f64-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="44f64-112">Compiling the Code</span></span>  
 <span data-ttu-id="44f64-113">上述範例設計用於搭配 Windows Form，且其需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="44f64-113">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44f64-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="44f64-114">See Also</span></span>  
 [<span data-ttu-id="44f64-115">使用筆刷填滿形狀</span><span class="sxs-lookup"><span data-stu-id="44f64-115">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
