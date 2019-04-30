---
title: HOW TO：使用畫筆繪製線條
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
ms.assetid: 0828c331-a438-4bdd-a4d6-3ef1e59e8795
ms.openlocfilehash: 8b4eb7684e15ffd5b0b528771490ba66f3b7bb45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954436"
---
# <a name="how-to-use-a-pen-to-draw-lines"></a>HOW TO：使用畫筆繪製線條
若要繪製線條，您需要<xref:System.Drawing.Graphics>物件和<xref:System.Drawing.Pen>物件。 <xref:System.Drawing.Graphics>物件會提供<xref:System.Drawing.Graphics.DrawLine%2A>方法，而<xref:System.Drawing.Pen>物件會儲存的行，例如色彩和寬度的功能。  
  
## <a name="example"></a>範例  
 下列範例會繪製中的行 20 (10） 到 （300，100）。 第一個陳述式會使用<xref:System.Drawing.Pen.%23ctor%2A>類別建構函式建立黑色的畫筆。 一個引數傳遞給<xref:System.Drawing.Pen.%23ctor%2A>建構函式<xref:System.Drawing.Color>物件以建立<xref:System.Drawing.Color.FromArgb%2A>方法。 值，用來建立<xref:System.Drawing.Color>物件 — （255，0，0，0），對應色彩的 alpha、 紅色、 綠色和藍色元件。 這些值會定義不透明的黑色畫筆。  
  
 [!code-csharp[System.Drawing.UsingAPen#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Pen>
- [使用畫筆繪製線條和形狀](using-a-pen-to-draw-lines-and-shapes.md)
- [GDI+ 中的畫筆、線條和矩形](pens-lines-and-rectangles-in-gdi.md)
