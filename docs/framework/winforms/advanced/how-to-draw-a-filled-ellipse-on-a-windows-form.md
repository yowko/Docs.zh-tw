---
title: "如何：在 Windows Form 上繪製實心橢圓形"
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
f1_keywords: Graphics.FillEllipse
helpviewer_keywords:
- ellipses [Windows Forms], drawing
- circles [Windows Forms], drawing
- circular shapes
- drawing [Windows Forms], ellipses
- shapes [Windows Forms], drawing
- forms [Windows Forms], drawing ellipses
ms.assetid: 781db806-950d-4c5b-b022-493f7fd0c4a8
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ad3297d1db29ec7310922dddf1caf57558a1505a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-filled-ellipse-on-a-windows-form"></a><span data-ttu-id="8784f-102">如何：在 Windows Form 上繪製實心橢圓形</span><span class="sxs-lookup"><span data-stu-id="8784f-102">How to: Draw a Filled Ellipse on a Windows Form</span></span>
<span data-ttu-id="8784f-103">這個範例會在表單上繪製實心的橢圓形。</span><span class="sxs-lookup"><span data-stu-id="8784f-103">This example draws a filled ellipse on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8784f-104">範例</span><span class="sxs-lookup"><span data-stu-id="8784f-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8784f-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="8784f-105">Compiling the Code</span></span>  
 <span data-ttu-id="8784f-106">您不能呼叫這個方法<xref:System.Windows.Forms.Form.Load>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="8784f-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="8784f-107">如果調整大小或遮蔽另一種形式的形式，將不會重新繪製內容。</span><span class="sxs-lookup"><span data-stu-id="8784f-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="8784f-108">若要讓您自動重新繪製的內容，您應該覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="8784f-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8784f-109">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="8784f-109">Robust Programming</span></span>  
 <span data-ttu-id="8784f-110">您應該一律呼叫<xref:System.IDisposable.Dispose%2A>耗用系統資源，例如任何物件上<xref:System.Drawing.Brush>和<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="8784f-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Brush> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8784f-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8784f-111">See Also</span></span>  
 [<span data-ttu-id="8784f-112">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="8784f-112">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="8784f-113">圖形程式設計入門</span><span class="sxs-lookup"><span data-stu-id="8784f-113">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="8784f-114">Alpha 混色線條和填色</span><span class="sxs-lookup"><span data-stu-id="8784f-114">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)  
 [<span data-ttu-id="8784f-115">使用筆刷填滿形狀</span><span class="sxs-lookup"><span data-stu-id="8784f-115">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
