---
title: HOW TO：裁剪和縮放影像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], cropping
- images [Windows Forms], scaling
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
ms.openlocfilehash: ff0567dca0fd86736e02a9dd827ec15df8bf2df8
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654493"
---
# <a name="how-to-crop-and-scale-images"></a>HOW TO：裁剪和縮放影像
<xref:System.Drawing.Graphics>類別提供了幾個<xref:System.Drawing.Graphics.DrawImage%2A>方法，其中有些有可用來裁剪和縮放比例的映像的來源和目的地矩形參數。  
  
## <a name="example"></a>範例  
 下列範例會建構<xref:System.Drawing.Image>從磁碟檔案 Apple.gif 的物件。 程式碼會在其原始大小繪製整個 apple 映像。 程式碼會接著呼叫<xref:System.Drawing.Graphics.DrawImage%2A>方法的<xref:System.Drawing.Graphics>物件来繪製大於原始 apple 映像的目的地矩形的 apple 映像的一部分。  
  
 <xref:System.Drawing.Graphics.DrawImage%2A>方法會判斷哪一部分 apple，以繪製藉由查看來源矩形中，由第三個、 第四，第 5 個和第六個引數。 在此情況下，apple 會裁剪成的寬度的 75%，且其高度的 75%。  
  
 <xref:System.Drawing.Graphics.DrawImage%2A>方法會判斷要繪製的裁剪後的 apple 的何處，以及這是要藉由查看目的地矩形的裁剪後的 apple 多大，第二個引數所指定。 在此情況下，目的地矩形是更廣的 30%，而比原始影像高度的 30%。  
  
 下圖顯示原始的 apple，並調整裁剪 apple。  
  
 ![原始的映像和裁剪的相同映像的螢幕擷取畫面。](./media/how-to-crop-and-scale-images/original-image-cropped-image.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。 請務必取代`Apple.gif`映像檔案名稱與您系統為有效的路徑。  
  
## <a name="see-also"></a>另請參閱
- [影像、點陣圖和中繼檔](images-bitmaps-and-metafiles.md)
- [使用影像、點陣圖、圖示和中繼檔](working-with-images-bitmaps-icons-and-metafiles.md)
