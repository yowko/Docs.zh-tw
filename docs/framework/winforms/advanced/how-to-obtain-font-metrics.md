---
title: 作法：取得字型度量資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], obtaining metrics
- font metrics [Windows Forms], obtaining
ms.assetid: ff7c0616-67f7-4fa2-84ee-b8d642f2b09b
ms.openlocfilehash: 7d7ad92199bb8a8f01290066f8ae023a14c2f9ce
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307429"
---
# <a name="how-to-obtain-font-metrics"></a>作法：取得字型度量資訊
<xref:System.Drawing.FontFamily>類別提供下列方法，擷取各種度量，針對特定的系列樣式組合：  
  
- <xref:System.Drawing.FontFamily.GetEmHeight%2A>([Fontstyle])  
  
- <xref:System.Drawing.FontFamily.GetCellAscent%2A>([Fontstyle])  
  
- <xref:System.Drawing.FontFamily.GetCellDescent%2A>([Fontstyle])  
  
- <xref:System.Drawing.FontFamily.GetLineSpacing%2A>([Fontstyle])  
  
 這些方法所傳回的值為字型設計單位，因此它們是獨立的大小和單位的特定<xref:System.Drawing.Font>物件。  
  
 下圖顯示各種計量：
  
 ![圖例字型度量資訊: （堆疊），下降，以及行距。](./media/how-to-obtain-font-metrics/various-font-metrics.png)  
  
## <a name="example"></a>範例  
 下列範例會顯示規則的樣式，新細明體字型家族的計量。 程式碼也會建立<xref:System.Drawing.Font>具有大小為 16 像素，並顯示該特定的計量 （以像素為單位） （根據新細明體系列） 的物件<xref:System.Drawing.Font>物件。  
  
 下圖顯示的範例程式碼的輸出：
  
 ![新細明體字型度量資訊的範例程式碼輸出。](./media/how-to-obtain-font-metrics/example-output-code-arial-font.png)  
  
 請注意上圖中的前兩行。 <xref:System.Drawing.Font>物件傳回的大小為 16，而<xref:System.Drawing.FontFamily>物件傳回 em 高度 2,048。 這兩個數字 （16 及 2,048） 是字型設計單位和單位 （在此案例的像素） 之間進行轉換的關鍵<xref:System.Drawing.Font>物件。  
  
 例如，您可以將轉換 ascent 設計單位為像素，如下所示：  
  
 ![顯示從設計單位轉換為像素為單位的公式](./media/how-to-obtain-font-metrics/convert-font-units-example.png)  
  
 下列程式碼文字垂直定位 splittunneling<xref:System.Drawing.PointF.Y%2A>資料成員<xref:System.Drawing.PointF>物件。 Y 座標會隨著增加`font.Height`針對每個新的一行文字。 <xref:System.Drawing.Font.Height%2A>的屬性<xref:System.Drawing.Font>物件傳回該特定的行距 （單位為像素）<xref:System.Drawing.Font>物件。 在此範例中，數字傳回<xref:System.Drawing.Font.Height%2A>為 19。 請注意，這是由行距度量轉換為像素 （無條件進位到整數） 的數字相同。  
  
 請注意，（也稱為大小或 em 大小） 其 em 高度不上升和下降的總和。 上升和下降的總和會呼叫儲存格的高度。 儲存格的高度減去內部的前置字元等於其 em 高度。 儲存格的高度加上外部前置字元等於行距。  
  
 [!code-csharp[System.Drawing.FontsAndText#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.FontsAndText#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。  
  
## <a name="see-also"></a>另請參閱

- [Windows Forms 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
- [使用字型和文字](using-fonts-and-text.md)
