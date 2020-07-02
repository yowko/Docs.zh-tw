---
title: 如何：在 Windows Form 上繪製實心矩形
description: 瞭解如何以程式設計方式在 Windows Form 上繪製填滿的矩形。 同時瞭解如何編譯您的程式碼。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Graphics.FillRectangle
helpviewer_keywords:
- drawing [Windows Forms], rectangles
- rectangles [Windows Forms], drawing
- drawing rectangles
ms.assetid: d656a93c-987d-4809-aafd-493fe17450f0
ms.openlocfilehash: 0ad8ec97000e29b2194a9eda713aa43d5557b44c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621635"
---
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a>如何：在 Windows Form 上繪製實心矩形
這個範例會在表單上繪製填滿的矩形。  
  
## <a name="example"></a>範例  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 您無法在事件處理常式中呼叫這個方法 <xref:System.Windows.Forms.Form.Load> 。 如果表單已調整大小或遮蔽另一個表單，則不會重新繪製所繪製的內容。 若要自動重新繪製您的內容，您應該覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法。  
  
## <a name="robust-programming"></a>穩固程式設計  
 您應該一律 <xref:System.IDisposable.Dispose%2A> 在取用系統資源的任何物件上呼叫，例如 <xref:System.Drawing.Brush> 和 <xref:System.Drawing.Graphics> 物件。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Graphics.FillRectangle%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [圖形程式設計入門](getting-started-with-graphics-programming.md)
- [Windows Form 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
- [使用畫筆繪製線條和形狀](using-a-pen-to-draw-lines-and-shapes.md)
- [GDI+ 中的筆刷和填滿的形狀](brushes-and-filled-shapes-in-gdi.md)
