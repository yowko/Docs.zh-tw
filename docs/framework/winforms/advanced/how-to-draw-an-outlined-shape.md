---
title: "如何：繪製外框形狀"
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
- cpp
f1_keywords: Graphics.DrawEllipse
helpviewer_keywords:
- ellipses [Windows Forms], drawing
- circles [Windows Forms], drawing
- drawing [Windows Forms], shapes
- circular shapes
- forms [Windows Forms], drawing circular shapes
- circles
- outlined shapes [Windows Forms], examples
- outlined shapes [Windows Forms], drawing
- drawing [Windows Forms], circular shapes
- shapes [Windows Forms], drawing
ms.assetid: f4f9214c-607e-407d-8cdd-6549f0278451
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eace68b646b3cdf75546527204bc41584ba64f85
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-an-outlined-shape"></a><span data-ttu-id="63416-102">如何：繪製外框形狀</span><span class="sxs-lookup"><span data-stu-id="63416-102">How to: Draw an Outlined Shape</span></span>
<span data-ttu-id="63416-103">這個範例會在表單上繪製含外框的橢圓形和矩形。</span><span class="sxs-lookup"><span data-stu-id="63416-103">This example draws outlined ellipses and rectangles on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63416-104">範例</span><span class="sxs-lookup"><span data-stu-id="63416-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#6)]
 [!code-csharp[System.Drawing.ConceptualHowTos#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#6)]
 [!code-vb[System.Drawing.ConceptualHowTos#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="63416-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="63416-105">Compiling the Code</span></span>  
 <span data-ttu-id="63416-106">您不能呼叫這個方法<xref:System.Windows.Forms.Form.Load>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="63416-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="63416-107">如果調整大小或遮蔽另一種形式的形式，將不會重新繪製內容。</span><span class="sxs-lookup"><span data-stu-id="63416-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="63416-108">若要讓您自動重新繪製的內容，您應該覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="63416-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="63416-109">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="63416-109">Robust Programming</span></span>  
 <span data-ttu-id="63416-110">您應該一律呼叫<xref:System.IDisposable.Dispose%2A>耗用系統資源，例如任何物件上<xref:System.Drawing.Pen>和<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="63416-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Pen> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63416-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="63416-111">See Also</span></span>  
 <xref:System.Drawing.Graphics.DrawEllipse%2A>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <xref:System.Drawing.Graphics.DrawRectangle%2A>  
 [<span data-ttu-id="63416-112">圖形程式設計入門</span><span class="sxs-lookup"><span data-stu-id="63416-112">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="63416-113">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="63416-113">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="63416-114">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="63416-114">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
