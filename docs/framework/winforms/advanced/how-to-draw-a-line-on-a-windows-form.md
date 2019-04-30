---
title: HOW TO：在 Windows Form 上繪製線條
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- Graphics.DrawLine
helpviewer_keywords:
- examples [Windows Forms], drawing lines on forms
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- drawing lines
ms.assetid: 55c1dbeb-75d0-430c-9814-a24b8971ad8c
ms.openlocfilehash: aab04b9236175cedd154b817db5a6f6450503105
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004155"
---
# <a name="how-to-draw-a-line-on-a-windows-form"></a><span data-ttu-id="4eb88-102">HOW TO：在 Windows Form 上繪製線條</span><span class="sxs-lookup"><span data-stu-id="4eb88-102">How to: Draw a Line on a Windows Form</span></span>
<span data-ttu-id="4eb88-103">此範例會在表單上繪製一條線。</span><span class="sxs-lookup"><span data-stu-id="4eb88-103">This example draws a line on a form.</span></span> <span data-ttu-id="4eb88-104">一般而言，當您在表單上繪製時，您處理表單的<xref:System.Windows.Forms.Control.Paint>事件並執行使用繪圖<xref:System.Windows.Forms.PaintEventArgs.Graphics%2A>屬性<xref:System.Windows.Forms.PaintEventArgs>，在此範例中所示</span><span class="sxs-lookup"><span data-stu-id="4eb88-104">Typically, when you draw on a form, you handle the form’s  <xref:System.Windows.Forms.Control.Paint> event and perform the drawing using the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.PaintEventArgs>, as shown in this example</span></span>  
  
## <a name="example"></a><span data-ttu-id="4eb88-105">範例</span><span class="sxs-lookup"><span data-stu-id="4eb88-105">Example</span></span>  
 [!code-csharp[System.Drawing.UsingAPen#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4eb88-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="4eb88-106">Compiling the Code</span></span>  
 <span data-ttu-id="4eb88-107">上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="4eb88-107">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="4eb88-108">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="4eb88-108">Robust Programming</span></span>  
 <span data-ttu-id="4eb88-109">您應該一律呼叫<xref:System.IDisposable.Dispose%2A>耗用系統資源，例如任何物件上<xref:System.Drawing.Pen>物件。</span><span class="sxs-lookup"><span data-stu-id="4eb88-109">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Pen> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eb88-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4eb88-110">See also</span></span>

- <xref:System.Drawing.Graphics.DrawLine%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="4eb88-111">圖形程式設計入門</span><span class="sxs-lookup"><span data-stu-id="4eb88-111">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="4eb88-112">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="4eb88-112">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="4eb88-113">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="4eb88-113">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
