---
title: "如何：在 Windows Form 上繪製線條"
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
f1_keywords: Graphics.DrawLine
helpviewer_keywords:
- examples [Windows Forms], drawing lines on forms
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- drawing lines
ms.assetid: 55c1dbeb-75d0-430c-9814-a24b8971ad8c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 984cdaca14c354ca78118412911c69c282ddd1bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-line-on-a-windows-form"></a><span data-ttu-id="96f2a-102">如何：在 Windows Form 上繪製線條</span><span class="sxs-lookup"><span data-stu-id="96f2a-102">How to: Draw a Line on a Windows Form</span></span>
<span data-ttu-id="96f2a-103">這個範例會在表單上繪製一條線。</span><span class="sxs-lookup"><span data-stu-id="96f2a-103">This example draws a line on a form.</span></span> <span data-ttu-id="96f2a-104">通常，當您在表單上繪製時，您會處理表單的<xref:System.Windows.Forms.Control.Paint>事件，並執行繪圖使用<xref:System.Windows.Forms.PaintEventArgs.Graphics%2A>屬性<xref:System.Windows.Forms.PaintEventArgs>，在此範例所示</span><span class="sxs-lookup"><span data-stu-id="96f2a-104">Typically, when you draw on a form, you handle the form’s  <xref:System.Windows.Forms.Control.Paint> event and perform the drawing using the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.PaintEventArgs>, as shown in this example</span></span>  
  
## <a name="example"></a><span data-ttu-id="96f2a-105">範例</span><span class="sxs-lookup"><span data-stu-id="96f2a-105">Example</span></span>  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="96f2a-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="96f2a-106">Compiling the Code</span></span>  
 <span data-ttu-id="96f2a-107">上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="96f2a-107">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="96f2a-108">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="96f2a-108">Robust Programming</span></span>  
 <span data-ttu-id="96f2a-109">您應該一律呼叫<xref:System.IDisposable.Dispose%2A>耗用系統資源，例如任何物件上<xref:System.Drawing.Pen>物件。</span><span class="sxs-lookup"><span data-stu-id="96f2a-109">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Pen> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96f2a-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96f2a-110">See Also</span></span>  
 <xref:System.Drawing.Graphics.DrawLine%2A>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [<span data-ttu-id="96f2a-111">圖形程式設計入門</span><span class="sxs-lookup"><span data-stu-id="96f2a-111">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="96f2a-112">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="96f2a-112">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="96f2a-113">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="96f2a-113">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
