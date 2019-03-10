---
title: HOW TO：繪製填滿材質的線條
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], texture
- drawing lines [Windows Forms], texture
ms.assetid: dc9118cc-f3c2-42e5-8173-f46d41d18fd5
ms.openlocfilehash: fd7a2aa2f6d930b0de29d8b8cbd3feacdb7a81e3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718593"
---
# <a name="how-to-draw-a-line-filled-with-a-texture"></a>HOW TO：繪製填滿材質的線條
而不是繪圖線，以使用純色，則可以繪製含有材質的線條。 若要繪製的直線和曲線滿材質，建立<xref:System.Drawing.TextureBrush>物件，並將其傳遞<xref:System.Drawing.TextureBrush>物件到<xref:System.Drawing.Pen.%23ctor%2A>建構函式。 點陣圖相關聯的材質筆刷用來 （不可見），圖格的平面與畫筆筆觸畫筆繪製線條或曲線時，當發現拼接材質的特定像素為單位。  
  
## <a name="example"></a>範例  
 下列範例會建立<xref:System.Drawing.Bitmap>檔案中的物件`Texture1.jpg`。 該點陣圖用來建構<xref:System.Drawing.TextureBrush>物件，而<xref:System.Drawing.TextureBrush>物件可用來建構<xref:System.Drawing.Pen>物件。 若要呼叫<xref:System.Drawing.Graphics.DrawImage%2A>繪製點陣圖，包含在其左上角 （0，0）。 若要在呼叫<xref:System.Drawing.Graphics.DrawEllipse%2A>使用<xref:System.Drawing.Pen>物件要繪製紋理的橢圓形。  
  
 下圖顯示點陣圖和紋理的橢圓形。  
  
 ![畫筆](./media/pens7.png "pens7")  
  
 [!code-csharp[System.Drawing.UsingAPen#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.UsingAPen#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 建立 Windows 表單，並處理表單的<xref:System.Windows.Forms.Control.Paint>事件。 貼上上述程式碼到<xref:System.Windows.Forms.Control.Paint>事件處理常式。 取代`Texture.jpg`您系統上有效的映像。  
  
## <a name="see-also"></a>另請參閱
- [使用畫筆繪製線條和形狀](using-a-pen-to-draw-lines-and-shapes.md)
- [Windows Forms 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
