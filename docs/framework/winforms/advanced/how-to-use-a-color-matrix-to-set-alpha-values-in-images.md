---
title: 如何：使用色彩矩陣設定影像中的 Alpha 值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using color matrices for semi-transparent
- transparency [Windows Forms], color matrices
- matrices [Windows Forms], alpha values
- bitmaps [Windows Forms], using color matrices for semi-transparent
ms.assetid: a27121e6-f7e9-4c09-84e2-f05aa9d2a1bb
ms.openlocfilehash: 73e820845d040856a0ae367da8b9371ad6afa142
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423719"
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a>如何：使用色彩矩陣設定影像中的 Alpha 值
<xref:System.Drawing.Bitmap> 類別（繼承自 <xref:System.Drawing.Image> 類別）和 <xref:System.Drawing.Imaging.ImageAttributes> 類別提供用來取得和設定圖元值的功能。 您可以使用 <xref:System.Drawing.Imaging.ImageAttributes> 類別來修改整個影像的 Alpha 值，也可以呼叫 <xref:System.Drawing.Bitmap> 類別的 <xref:System.Drawing.Bitmap.SetPixel%2A> 方法來修改個別的圖元值。  
  
## <a name="example"></a>範例  
 <xref:System.Drawing.Imaging.ImageAttributes> 類別有許多屬性，可讓您在呈現期間用來修改影像。 在下列範例中，會使用 <xref:System.Drawing.Imaging.ImageAttributes> 物件，將所有 Alpha 值設定為其過去的80%。 這是藉由初始化色彩矩陣，並將矩陣中的 Alpha 縮放值設定為0.8 來完成。 色彩矩陣的位址會傳遞至 <xref:System.Drawing.Imaging.ImageAttributes> 物件的 <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> 方法，而 <xref:System.Drawing.Imaging.ImageAttributes> 物件會傳遞至 <xref:System.Drawing.Graphics> 物件的 <xref:System.Drawing.Graphics.DrawString%2A> 方法。  
  
 在轉譯期間，點陣圖中的 Alpha 值會轉換成其過去的80%。 這會產生與背景混合的影像。 如下圖所示，點陣圖影像看起來是透明的;您可以透過它來查看實心黑色線。  
  
 ![使用矩陣的 Alpha 混合螢幕擷取畫面。](./media/how-to-use-a-color-matrix-to-set-alpha-values-in-images/alpha-blending-matrix.png "image2）")  
  
 當影像在背景的白色部分上方時，影像就會與白色色彩混合。 影像與黑色線條相交時，影像會以黑色進行混合。  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 先前的範例是針對與 Windows Forms 搭配使用所設計，而且需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.PaintEventHandler>的參數。  
  
## <a name="see-also"></a>請參閱

- [Windows Forms 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
- [Alpha 混色線條和填色](alpha-blending-lines-and-fills.md)
