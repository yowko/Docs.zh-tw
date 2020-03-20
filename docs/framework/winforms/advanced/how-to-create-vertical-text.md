---
title: 如何：建立垂直文字
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing vertical
- Windows Forms, drawing vertical text
- strings [Windows Forms], drawing vertical
- vertical text [Windows Forms], drawing
ms.assetid: 50c69046-4188-47d9-b949-cc2610ffd337
ms.openlocfilehash: 86401342625f593945b801f7619ef9ca9681317c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182553"
---
# <a name="how-to-create-vertical-text"></a>如何：建立垂直文字
可以使用<xref:System.Drawing.StringFormat>物件指定垂直而不是水準繪製文本。  
  
## <a name="example"></a>範例  
 下面的示例將該值<xref:System.Drawing.StringFormatFlags.DirectionVertical>分配給<xref:System.Drawing.StringFormat.FormatFlags%2A><xref:System.Drawing.StringFormat>物件的屬性。 該<xref:System.Drawing.StringFormat>物件傳遞給<xref:System.Drawing.Graphics.DrawString%2A><xref:System.Drawing.Graphics>類的方法。 該值<xref:System.Drawing.StringFormatFlags.DirectionVertical>是枚舉的成員<xref:System.Drawing.StringFormatFlags>。  
  
 下圖顯示了垂直文本：
  
 ![顯示垂直字體文本的圖形。](./media/how-to-create-vertical-text/vertical-font-text-graphic.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
- 前面的示例設計用於 Windows 表單，它要求<xref:System.Windows.Forms.PaintEventArgs>`e`. <xref:System.Windows.Forms.PaintEventHandler>  
  
## <a name="see-also"></a>另請參閱

- [如何：使用 GDI 繪製文字](how-to-draw-text-with-gdi.md)
