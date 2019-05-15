---
title: 作法：使用色彩矩陣設定影像中的 Alpha 值
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
ms.openlocfilehash: fd63380e04eeb4b7ec7ed7d59032309ea7446507
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593164"
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a>作法：使用色彩矩陣設定影像中的 Alpha 值
<xref:System.Drawing.Bitmap>類別 (繼承自<xref:System.Drawing.Image>類別) 和<xref:System.Drawing.Imaging.ImageAttributes>類別提供用於取得和設定像素值的功能。 您可以使用<xref:System.Drawing.Imaging.ImageAttributes>類別來修改 alpha 值的整個影像，或您可以呼叫<xref:System.Drawing.Bitmap.SetPixel%2A>方法<xref:System.Drawing.Bitmap>修改個別像素值的類別。  
  
## <a name="example"></a>範例  
 <xref:System.Drawing.Imaging.ImageAttributes>類別具有可供您在轉譯期間修改映像的屬性。 在下列範例中，<xref:System.Drawing.Imaging.ImageAttributes>物件用來將所有的 alpha 值設定為 80%的這些。 這是藉由初始化色彩矩陣，並設定的 alpha 縮放 0.8 矩陣中的值。 色彩矩陣的位址傳遞給<xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A>方法<xref:System.Drawing.Imaging.ImageAttributes>物件，而<xref:System.Drawing.Imaging.ImageAttributes>物件傳遞給<xref:System.Drawing.Graphics.DrawString%2A>方法<xref:System.Drawing.Graphics>物件。  
  
 在呈現期間，在點陣圖中的 alpha 值會轉換成原先的 80%。 這會導致混合與背景的影像。 下圖所示，點陣圖影像看起來透明;您所見，透過它的實心黑色線條。  
  
 ![使用矩陣 alpha 透明混色](./media/image2.png "image2")  
  
 其中是背景的白色部分上的映像，映像具有已混合與白色。 映像交點，黑色線條，映像會混合與黑色。  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。  
  
## <a name="see-also"></a>另請參閱

- [Windows Forms 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
- [Alpha 混色線條和填色](alpha-blending-lines-and-fills.md)
