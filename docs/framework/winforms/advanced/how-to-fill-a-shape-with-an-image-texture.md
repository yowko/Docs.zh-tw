---
title: 如何：使用影像材質填滿圖案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using with brushes
- bitmaps [Windows Forms], using texture
- shapes [Windows Forms], filling with images
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
ms.openlocfilehash: c1eb090bebcced125193c1db16087b6165d27ff3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a>如何：使用影像材質填滿圖案
您也可以使用與紋理填入封閉的圖形<xref:System.Drawing.Image>類別和<xref:System.Drawing.TextureBrush>類別。  
  
## <a name="example"></a>範例  
 下列範例會填滿橢圓形使用的映像。 程式碼會建構<xref:System.Drawing.Image>物件，並接著會將該位址傳遞<xref:System.Drawing.Image>物件做為引數<xref:System.Drawing.TextureBrush.%23ctor%2A>建構函式。 第三個陳述式將映像，而第四個陳述式填滿橢圓形縮放影像的重複複本 %。  
  
 下列程式碼，<xref:System.Drawing.TextureBrush.Transform%2A>屬性包含它繪製前套用到影像的轉換。 假設原始的映像有 640 像素寬度和高度 480 像素。 轉換將影像縮小為 75 × 75 藉由設定水平和垂直縮放比例值。  
  
> [!NOTE]
>  在下列範例中，映像大小為 75 × 75，而橢圓形的大小為 150 × 250。 因為映像是小於它正在填滿的橢圓形，橢圓形會並排顯示與映像。 已達到並排方式映像會水平及垂直重複直到圖形的界限。 如需可並排顯示的詳細資訊，請參閱[如何： 並排顯示影像與圖案](../../../../docs/framework/winforms/advanced/how-to-tile-a-shape-with-an-image.md)。  
  
 [!code-csharp[System.Drawing.UsingABrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。  
  
## <a name="see-also"></a>另請參閱  
 [使用筆刷填滿形狀](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
