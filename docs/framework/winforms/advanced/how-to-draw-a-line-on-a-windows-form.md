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
# <a name="how-to-draw-a-line-on-a-windows-form"></a>如何：在 Windows Form 上繪製線條
這個範例會在表單上繪製一條線。 一般而言，當您在表單上繪製時，會處理表單的 <xref:System.Windows.Forms.Control.Paint> 事件，並使用的屬性來執行繪圖 <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> <xref:System.Windows.Forms.PaintEventArgs> ，如下列範例所示  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Drawing.UsingAPen#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。  
  
## <a name="robust-programming"></a>穩固程式設計  
 您應該一律 <xref:System.IDisposable.Dispose%2A> 在取用系統資源的任何物件（例如物件）上呼叫 <xref:System.Drawing.Pen> 。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Graphics.DrawLine%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [圖形程式設計入門](getting-started-with-graphics-programming.md)
- [使用畫筆繪製線條和形狀](using-a-pen-to-draw-lines-and-shapes.md)
- [Windows Form 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
