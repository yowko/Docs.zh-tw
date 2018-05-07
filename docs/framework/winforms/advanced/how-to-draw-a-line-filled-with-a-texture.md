---
title: 如何：繪製填滿材質的線條
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], texture
- drawing lines [Windows Forms], texture
ms.assetid: dc9118cc-f3c2-42e5-8173-f46d41d18fd5
ms.openlocfilehash: 1895c752340d8d764205b5a32b9af0861303841a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-a-line-filled-with-a-texture"></a>如何：繪製填滿材質的線條
而不是繪製線條，以利用純色，您可以繪製材質的線條。 若要繪製的直線和曲線的紋理，建立<xref:System.Drawing.TextureBrush>物件，並將其傳遞<xref:System.Drawing.TextureBrush>物件<xref:System.Drawing.Pen.%23ctor%2A>建構函式。 紋理筆刷與關聯的點陣圖用於磚平面 （不可見），並畫筆筆觸時畫筆繪製線條或曲線時，發現並排紋理的特定像素為單位。  
  
## <a name="example"></a>範例  
 下列範例會建立<xref:System.Drawing.Bitmap>物件從檔案`Texture1.jpg`。 該點陣圖用來建構<xref:System.Drawing.TextureBrush>物件，而<xref:System.Drawing.TextureBrush>物件用來建構<xref:System.Drawing.Pen>物件。 若要呼叫<xref:System.Drawing.Graphics.DrawImage%2A>繪製點陣圖，以在其左上角 （0，0）。 若要呼叫<xref:System.Drawing.Graphics.DrawEllipse%2A>使用<xref:System.Drawing.Pen>物件要繪製的材質的橢圓形。  
  
 下圖顯示點陣圖和紋理的橢圓形。  
  
 ![畫筆](../../../../docs/framework/winforms/advanced/media/pens7.png "pens7")  
  
 [!code-csharp[System.Drawing.UsingAPen#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.UsingAPen#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 建立 Windows 表單，並處理表單的<xref:System.Windows.Forms.Control.Paint>事件。 貼上上述程式碼到<xref:System.Windows.Forms.Control.Paint>事件處理常式。 取代`Texture.jpg`您系統上有效的映像。  
  
## <a name="see-also"></a>另請參閱  
 [使用畫筆繪製線條和形狀](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [Windows Forms 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
