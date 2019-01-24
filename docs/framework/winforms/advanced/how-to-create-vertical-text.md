---
title: HOW TO：建立垂直文字
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
ms.openlocfilehash: 513d59c61d5195665928f6bb28d1d091b425c103
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573146"
---
# <a name="how-to-create-vertical-text"></a>HOW TO：建立垂直文字
您可以使用<xref:System.Drawing.StringFormat>物件來指定，垂直而非水平繪製文字。  
  
## <a name="example"></a>範例  
 下列範例會將值指派<xref:System.Drawing.StringFormatFlags.DirectionVertical>要<xref:System.Drawing.StringFormat.FormatFlags%2A>屬性<xref:System.Drawing.StringFormat>物件。 該<xref:System.Drawing.StringFormat>物件會傳遞給<xref:System.Drawing.Graphics.DrawString%2A>方法<xref:System.Drawing.Graphics>類別。 該值<xref:System.Drawing.StringFormatFlags.DirectionVertical>隸屬<xref:System.Drawing.StringFormatFlags>列舉型別。  
  
 下圖顯示垂直文字。  
  
 ![字型文字](../../../../docs/framework/winforms/advanced/media/csfontstext5.png "csfontstext5")  
  
 [!code-csharp[System.Drawing.FontsAndText#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e` ，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。  
  
## <a name="see-also"></a>另請參閱
- [如何：使用 GDI 繪製文字](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
