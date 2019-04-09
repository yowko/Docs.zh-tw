---
title: HOW TO：將現有點陣圖描繪至螢幕
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], displaying in Windows Forms
- bitmaps [Windows Forms], loading in Windows Forms applications
- images [Windows Forms], displaying on Windows Forms
ms.assetid: 5bc558d7-b326-4050-a834-b8600da0de95
ms.openlocfilehash: 90511adf9caffe7952e270d6fe32dd85162a29d7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089162"
---
# <a name="how-to-draw-an-existing-bitmap-to-the-screen"></a>HOW TO：將現有點陣圖描繪至螢幕
您可以輕鬆地繪製現有的映像，在螢幕上。 您必須先建立<xref:System.Drawing.Bitmap>物件使用點陣圖建構函式接受檔案名稱， <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>。 這個建構函式會接受映像，包含數個不同的檔案格式，包括 BMP、 GIF、 JPEG、 PNG 和 TIFF。 建立之後<xref:System.Drawing.Bitmap>物件，傳遞<xref:System.Drawing.Bitmap>物件<xref:System.Drawing.Graphics.DrawImage%2A>方法<xref:System.Drawing.Graphics>物件。  
  
## <a name="example"></a>範例  
 這個範例會建立<xref:System.Drawing.Bitmap>JPEG 檔案中的物件，然後繪製以其左上角，在點陣圖 （60，10）。  
  
 下圖顯示在指定的位置繪製的點陣圖：  
  
 ![如果螢幕擷取畫面顯示在指定位置的影像。](./media/how-to-draw-an-existing-bitmap-to-the-screen/bitmap-specified-position.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.WorkingWithImages#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。  
  
## <a name="see-also"></a>另請參閱

- [Windows Form 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
- [使用影像、點陣圖、圖示和中繼檔](working-with-images-bitmaps-icons-and-metafiles.md)
