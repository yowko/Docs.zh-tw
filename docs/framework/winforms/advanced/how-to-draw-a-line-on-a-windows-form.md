---
title: 如何：在 Windows Form 上繪製線條
description: 瞭解如何藉由處理繪製事件，在表單上繪製線條，然後使用 PaintEventArgs 的 Graphics 屬性來執行繪製。
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
ms.openlocfilehash: c8e92dc265c63413275561d0e2e3aa820eaec724
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621622"
---
# <a name="how-to-draw-a-line-on-a-windows-form"></a><span data-ttu-id="9ce09-103">如何：在 Windows Form 上繪製線條</span><span class="sxs-lookup"><span data-stu-id="9ce09-103">How to: Draw a Line on a Windows Form</span></span>
<span data-ttu-id="9ce09-104">這個範例會在表單上繪製一條線。</span><span class="sxs-lookup"><span data-stu-id="9ce09-104">This example draws a line on a form.</span></span> <span data-ttu-id="9ce09-105">一般而言，當您在表單上繪製時，會處理表單的 <xref:System.Windows.Forms.Control.Paint> 事件，並使用的屬性來執行繪圖 <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> <xref:System.Windows.Forms.PaintEventArgs> ，如下列範例所示</span><span class="sxs-lookup"><span data-stu-id="9ce09-105">Typically, when you draw on a form, you handle the form’s  <xref:System.Windows.Forms.Control.Paint> event and perform the drawing using the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.PaintEventArgs>, as shown in this example</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ce09-106">範例</span><span class="sxs-lookup"><span data-stu-id="9ce09-106">Example</span></span>  
 [!code-csharp[System.Drawing.UsingAPen#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9ce09-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="9ce09-107">Compiling the Code</span></span>  
 <span data-ttu-id="9ce09-108">上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。</span><span class="sxs-lookup"><span data-stu-id="9ce09-108">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9ce09-109">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="9ce09-109">Robust Programming</span></span>  
 <span data-ttu-id="9ce09-110">您應該一律 <xref:System.IDisposable.Dispose%2A> 在取用系統資源的任何物件（例如物件）上呼叫 <xref:System.Drawing.Pen> 。</span><span class="sxs-lookup"><span data-stu-id="9ce09-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Pen> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ce09-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ce09-111">See also</span></span>

- <xref:System.Drawing.Graphics.DrawLine%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="9ce09-112">圖形程式設計入門</span><span class="sxs-lookup"><span data-stu-id="9ce09-112">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="9ce09-113">使用畫筆繪製線條和形狀</span><span class="sxs-lookup"><span data-stu-id="9ce09-113">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="9ce09-114">Windows Form 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="9ce09-114">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
