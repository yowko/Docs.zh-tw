---
title: 如何：載入和顯示中繼檔
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
ms.openlocfilehash: 6c17e0b2d023ccf80b0d32301b7ee6765edcae9f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424808"
---
# <a name="how-to-load-and-display-metafiles"></a>如何：載入和顯示中繼檔
繼承自 <xref:System.Drawing.Image> 類別的 <xref:System.Drawing.Imaging.Metafile> 類別，提供了記錄、顯示和檢查向量影像的方法。  
  
## <a name="example"></a>範例  
 若要在螢幕上顯示向量影像（中繼檔），您需要 <xref:System.Drawing.Imaging.Metafile> 物件和 <xref:System.Drawing.Graphics> 物件。 將檔案（或資料流程）的名稱傳遞至 <xref:System.Drawing.Imaging.Metafile> 的函式。 建立 <xref:System.Drawing.Imaging.Metafile> 物件之後，請將該 <xref:System.Drawing.Imaging.Metafile> 物件傳遞至 <xref:System.Drawing.Graphics> 物件的 <xref:System.Drawing.Graphics.DrawImage%2A> 方法。  
  
 此範例會從 EMF （增強型中繼檔）檔案建立 <xref:System.Drawing.Imaging.Metafile> 物件，然後在上繪製影像，其左上角為（60，10）。  
  
 下圖顯示在指定位置繪製的中繼檔。  
  
 ![顯示影像位置的螢幕擷取畫面。](./media/how-to-load-and-display-metafiles/metafile-drawn-specified-location.png "imageposition2")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是針對與 Windows Forms 搭配使用所設計，而且需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。  
  
## <a name="see-also"></a>請參閱

- [使用影像、點陣圖、圖示和中繼檔](working-with-images-bitmaps-icons-and-metafiles.md)
