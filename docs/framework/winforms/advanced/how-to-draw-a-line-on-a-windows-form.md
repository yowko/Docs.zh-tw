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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074443"
---
# <a name="how-to-draw-a-line-on-a-windows-form"></a>HOW TO：在 Windows Form 上繪製線條
此範例會在表單上繪製一條線。 一般而言，當您在表單上繪製時，您處理表單的<xref:System.Windows.Forms.Control.Paint>事件並執行使用繪圖<xref:System.Windows.Forms.PaintEventArgs.Graphics%2A>屬性<xref:System.Windows.Forms.PaintEventArgs>，在此範例中所示  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Drawing.UsingAPen#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。  
  
## <a name="robust-programming"></a>穩固程式設計  
 您應該一律呼叫<xref:System.IDisposable.Dispose%2A>耗用系統資源，例如任何物件上<xref:System.Drawing.Pen>物件。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Graphics.DrawLine%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [圖形程式設計入門](getting-started-with-graphics-programming.md)
- [使用畫筆繪製線條和形狀](using-a-pen-to-draw-lines-and-shapes.md)
- [Windows Forms 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
