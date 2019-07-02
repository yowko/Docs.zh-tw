---
title: HOW TO：避免自動縮放以提高效能
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- automatic scaling
- images [Windows Forms], improving performance
- images [Windows Forms], using without automatic scaling
- performance [Windows Forms], improving image
ms.assetid: 5fe2c95d-8653-4d55-bf0d-e5afa28f223b
ms.openlocfilehash: dd1a1545dce33de1ce11938db8495ebf311dadda
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506213"
---
# <a name="how-to-improve-performance-by-avoiding-automatic-scaling"></a>作法：避免自動縮放以提高效能
GDI + 可能會自動調整映像方式而定，反而會降低效能。 或者，您可以控制傳遞到目的地矩形的維度影像的縮放<xref:System.Drawing.Graphics.DrawImage%2A>方法。  
  
 例如，下列呼叫來<xref:System.Drawing.Graphics.DrawImage%2A>方法指定的左上角 （50、 30），但未指定目的地矩形。  
  
 [!code-csharp[System.Drawing.WorkingWithImages#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.WorkingWithImages#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#31)]  
  
 雖然這是最簡單版本<xref:System.Drawing.Graphics.DrawImage%2A>方法所需的引數數目不一定是最有效率的作法。 如果使用 GDI + (通常是 96 dpi 為單位) 的解決方法是從儲存在解析度不同<xref:System.Drawing.Image>物件，則<xref:System.Drawing.Graphics.DrawImage%2A>方法將會調整映像。 例如，假設<xref:System.Drawing.Image>物件具有 216 像素寬度] 和 [預存的水平解析度值為 72 dpi 為單位。 因為 216/72 為 3，<xref:System.Drawing.Graphics.DrawImage%2A>會調整映像，使其具有寬度 3 英吋為 96 dpi 的解析度。 也就是<xref:System.Drawing.Graphics.DrawImage%2A>會顯示影像的寬度為 96 x 3 = 288 則像素為單位。  
  
 即使您的螢幕解析度是 96 dpi，GDI + 會可能縮放影像，好像螢幕解析度 96 dpi 為單位。 這是因為 GDI +<xref:System.Drawing.Graphics>物件與裝置內容相關聯，而且當 GDI + 查詢的螢幕解析度的裝置內容時，結果通常是 96，不論實際螢幕解析度。 您可以藉由指定目的地矩形的自動調整來避免<xref:System.Drawing.Graphics.DrawImage%2A>方法。  
  
## <a name="example"></a>範例  
 下列範例會繪製兩次相同的映像。 在第一個案例中，未指定目的地矩形的高度與寬度，並將映像會自動調整。 在第二個案例中，會依照相同成為原始影像的高度與寬度會指定寬度和目的地矩形的高度 （單位為像素為單位）。 下圖顯示兩次呈現的影像：  
  
 ![如果螢幕擷取畫面顯示調整的紋理的影像。](./media/how-to-improve-performance-by-avoiding-automatic-scaling/two-scaled-texture-images.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.WorkingWithImages#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#32)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。 Texture.jpg 取代映像名稱和您系統為有效的路徑。  
  
## <a name="see-also"></a>另請參閱

- [影像、點陣圖和中繼檔](images-bitmaps-and-metafiles.md)
- [使用影像、點陣圖、圖示和中繼檔](working-with-images-bitmaps-icons-and-metafiles.md)
