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
ms.openlocfilehash: ed129cd9487ba1416cd69b2e13f59747856cb598
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a>如何：使用色彩矩陣設定影像中的 Alpha 值
<xref:System.Drawing.Bitmap>類別 (繼承自<xref:System.Drawing.Image>類別) 和<xref:System.Drawing.Imaging.ImageAttributes>類別提供取得和設定像素值的功能。 您可以使用<xref:System.Drawing.Imaging.ImageAttributes>類別來修改 alpha 值整個影像，或您可以呼叫<xref:System.Drawing.Bitmap.SetPixel%2A>方法<xref:System.Drawing.Bitmap>類別以修改個別像素值。  
  
## <a name="example"></a>範例  
 <xref:System.Drawing.Imaging.ImageAttributes>類別具有可讓您在轉譯期間修改映像的屬性。 在下列範例中，<xref:System.Drawing.Imaging.ImageAttributes>物件用於設定所有 alpha 值的這些 80%。 這是初始化色彩矩陣和 alpha 縮放比例值為 0.8 矩陣中的設定。 色彩矩陣的位址傳遞給<xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A>方法<xref:System.Drawing.Imaging.ImageAttributes>物件，而<xref:System.Drawing.Imaging.ImageAttributes>物件傳遞至<xref:System.Drawing.Graphics.DrawString%2A>方法<xref:System.Drawing.Graphics>物件。  
  
 在呈現期間，在點陣圖的 alpha 值會轉換成原先的 80%。 這會導致混合與背景的影像。 如下圖所示，點陣圖影像看起來透明的;您可以查看透過它與實心黑色線條。  
  
 ![使用矩陣的 alpha 混色](../../../../docs/framework/winforms/advanced/media/image2.png "image2")  
  
 影像是白色背景的部分，其中具有與白色混合映像。 映像的黑色線條交點映像會與黑色混合。  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例設計用於搭配 Windows Form，且其需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。  
  
## <a name="see-also"></a>另請參閱  
 [Windows Forms 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Alpha 混色線條和填色](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
