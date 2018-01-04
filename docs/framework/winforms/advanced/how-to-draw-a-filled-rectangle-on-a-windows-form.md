---
title: "如何：在 Windows Form 上繪製實心矩形"
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
f1_keywords: Graphics.FillRectangle
helpviewer_keywords:
- drawing [Windows Forms], rectangles
- rectangles [Windows Forms], drawing
- drawing rectangles
ms.assetid: d656a93c-987d-4809-aafd-493fe17450f0
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 17d143c0c265fea876d084ebc21663d93553fe9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a><span data-ttu-id="a5f4c-102">如何：在 Windows Form 上繪製實心矩形</span><span class="sxs-lookup"><span data-stu-id="a5f4c-102">How to: Draw a Filled Rectangle on a Windows Form</span></span>
<span data-ttu-id="a5f4c-103">這個範例會在表單上繪製實心的矩形。</span><span class="sxs-lookup"><span data-stu-id="a5f4c-103">This example draws a filled rectangle on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5f4c-104">範例</span><span class="sxs-lookup"><span data-stu-id="a5f4c-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a5f4c-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="a5f4c-105">Compiling the Code</span></span>  
 <span data-ttu-id="a5f4c-106">您不能呼叫這個方法<xref:System.Windows.Forms.Form.Load>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="a5f4c-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="a5f4c-107">如果調整大小或遮蔽另一種形式的形式，將不會重新繪製內容。</span><span class="sxs-lookup"><span data-stu-id="a5f4c-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="a5f4c-108">若要讓您自動重新繪製的內容，您應該覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="a5f4c-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a5f4c-109">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="a5f4c-109">Robust Programming</span></span>  
 <span data-ttu-id="a5f4c-110">您應該一律呼叫<xref:System.IDisposable.Dispose%2A>耗用系統資源，例如任何物件上<xref:System.Drawing.Brush>和<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="a5f4c-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Brush> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5f4c-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="a5f4c-111">See Also</span></span>  
 <xref:System.Drawing.Graphics.FillRectangle%2A>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [<span data-ttu-id="a5f4c-112">圖形程式設計入門</span><span class="sxs-lookup"><span data-stu-id="a5f4c-112">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="a5f4c-113">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="a5f4c-113">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="a5f4c-114">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="a5f4c-114">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="a5f4c-115">GDI+ 中的筆刷和填滿的形狀</span><span class="sxs-lookup"><span data-stu-id="a5f4c-115">Brushes and Filled Shapes in GDI+</span></span>](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)
