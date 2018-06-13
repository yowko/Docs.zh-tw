---
title: 圖形介面的結構
ms.date: 03/30/2017
helpviewer_keywords:
- GDI+, using managed interface
- graphics [Windows Forms], class structure
ms.assetid: 010a1e46-656b-40a1-8d5d-87aa05ee1243
ms.openlocfilehash: 625bd5818d58fd659af69d4985d629f055123e54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525898"
---
# <a name="structure-of-the-graphics-interface"></a>圖形介面的結構
Managed 的類別介面，以[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]包含約 60 類別、 50 的列舉型別，以及 8 結構。 <xref:System.Drawing.Graphics>類別的核心是[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]功能; 它是實際繪製線條、 曲線、 圖形、 影像和文字的類別。  
  
## <a name="important-classes"></a>重要類別  
 搭配運作的許多類別<xref:System.Drawing.Graphics>類別。 例如，<xref:System.Drawing.Graphics.DrawLine%2A>方法會接收<xref:System.Drawing.Pen>物件，其中包含要繪製線條的屬性 （色彩、 寬度、 虛線樣式等等）。 <xref:System.Drawing.Graphics.FillRectangle%2A>方法可以接收的指標<xref:System.Drawing.Drawing2D.LinearGradientBrush>物件，可搭配<xref:System.Drawing.Graphics>使用逐漸變更的色彩填滿之矩形的物件。 <xref:System.Drawing.Font> 和<xref:System.Drawing.StringFormat>物件影響方式<xref:System.Drawing.Graphics>物件上繪製的文字。 A<xref:System.Drawing.Drawing2D.Matrix>物件可儲存及操作的自然變換<xref:System.Drawing.Graphics>物件，用來旋轉和調整其規模，翻轉影像。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供數種結構 (例如， <xref:System.Drawing.Rectangle>， <xref:System.Drawing.Point>，和<xref:System.Drawing.Size>) 用來組織圖形資料。 此外，某些類別是服務主要是為結構化的資料類型。 例如，<xref:System.Drawing.Imaging.BitmapData>類別是 helper<xref:System.Drawing.Bitmap>類別，而<xref:System.Drawing.Drawing2D.PathData>類別是 helper<xref:System.Drawing.Drawing2D.GraphicsPath>類別。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 定義數個列舉型別，這是集合相關的常數。 例如，<xref:System.Drawing.Drawing2D.LineJoin>列舉包含的項目<xref:System.Drawing.Drawing2D.LineJoin.Bevel>， <xref:System.Drawing.Drawing2D.LineJoin.Miter>，和<xref:System.Drawing.Drawing2D.LineJoin.Round>，它會指定可用於聯結兩個線條的樣式。  
  
## <a name="see-also"></a>另請參閱  
 [圖形概觀](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 [關於 GDI+ Managed 程式碼](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 [使用 Managed 圖形類別](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
