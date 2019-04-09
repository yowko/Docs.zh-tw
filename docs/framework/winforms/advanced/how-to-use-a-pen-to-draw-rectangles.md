---
title: HOW TO：使用畫筆繪製矩形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- rectangles [Windows Forms], drawing
- pens [Windows Forms], drawing rectangles
ms.assetid: 54a7fa14-3ad8-4d64-b424-2a12005b250c
ms.openlocfilehash: 0e51a1e3a2d14754147dbd36f170127a7e978acd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074608"
---
# <a name="how-to-use-a-pen-to-draw-rectangles"></a>HOW TO：使用畫筆繪製矩形
若要繪製矩形，您需要<xref:System.Drawing.Graphics>物件和<xref:System.Drawing.Pen>物件。 <xref:System.Drawing.Graphics>物件會提供<xref:System.Drawing.Graphics.DrawRectangle%2A>方法，而<xref:System.Drawing.Pen>物件會儲存的行，例如色彩和寬度的功能。  
  
## <a name="example"></a>範例  
 下列範例會繪製在其左上角的矩形 （10，10）。 矩形的寬度為 100 且高度為 50。 第二個引數傳遞至<xref:System.Drawing.Pen.%23ctor%2A>建構函式表示畫筆寬度為 5 像素。  
  
 繪製矩形時，畫筆會集中在矩形的界限中。 矩形邊的畫筆寬度為 5，因為會繪製的 5 個像素 1 個像素寬、 這類會繪製在內部，繪製界限，2 個像素和 2 個像素會繪製在外部。 如需畫筆對齊方式的詳細資訊，請參閱[How to:設定畫筆寬度和對齊](how-to-set-pen-width-and-alignment.md)。  
  
 下圖顯示產生的矩形。 虛線顯示，其中會有已繪製矩形如果畫筆寬度有一個像素。 矩形左上角的放大的檢視顯示黑色粗線會置於這些點線。  
  
 ![顯示與黑色虛線繪製的矩形的螢幕擷取畫面。](./media/how-to-use-a-pen-to-draw-rectangles/drawn-rectangle-black-lines-dotted-lines.gif)  
  
 [!code-csharp[System.Drawing.UsingAPen#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs>`e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。  
  
## <a name="see-also"></a>另請參閱

- [使用畫筆繪製線條和形狀](using-a-pen-to-draw-lines-and-shapes.md)
