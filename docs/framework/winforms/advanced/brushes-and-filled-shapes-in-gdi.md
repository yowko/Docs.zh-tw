---
title: GDI+ 中的筆刷和填滿的形狀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [Windows Forms], GDI+
- filled shapes [Windows Forms], GDI+
- shapes [Windows Forms], GDI+
- GDI+, brushes
- GDI+, filled shapes
- gradient brushes
- brushes [Windows Forms], gradient
ms.assetid: e863e2a7-0294-4130-99b6-f1ea3201e7cd
ms.openlocfilehash: 45ef0b5920e43300e047d363149ea10a7833477b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912236"
---
# <a name="brushes-and-filled-shapes-in-gdi"></a>GDI+ 中的筆刷和填滿的形狀
「封閉」圖形 (例如矩形或橢圓形) 包含外框和內部。 外框會以畫筆繪製, 而內部則會填滿筆刷。 Gdi + 提供數筆刷類別來填滿封閉圖形的<xref:System.Drawing.SolidBrush>內部<xref:System.Drawing.Drawing2D.HatchBrush>: <xref:System.Drawing.TextureBrush>、 <xref:System.Drawing.Drawing2D.LinearGradientBrush>、、 <xref:System.Drawing.Drawing2D.PathGradientBrush>和。 所有這些類別都是<xref:System.Drawing.Brush>繼承自類別。 下圖顯示填滿實心筆刷的矩形, 以及填滿影線筆刷的橢圓形。  
  
 ![填滿的圖案](./media/aboutgdip02-art17.gif "Aboutgdip02_art17")  
  
## <a name="solid-brushes"></a>實心筆刷  
 若要填滿封閉圖形, 您需要<xref:System.Drawing.Graphics>類別的實例<xref:System.Drawing.Brush>和。 <xref:System.Drawing.Graphics>類別的實例會提供方法 ( <xref:System.Drawing.Graphics.FillRectangle%2A>例如和<xref:System.Drawing.Graphics.FillEllipse%2A>), 並<xref:System.Drawing.Brush>儲存填滿的屬性 (例如色彩和模式)。 <xref:System.Drawing.Brush>會當做其中一個引數傳遞至 fill 方法。 下列程式碼範例示範如何以純色紅色填滿橢圓形。  
  
 [!code-csharp[LinesCurvesAndShapes#121](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
> 在上述範例中, 筆刷的類型<xref:System.Drawing.SolidBrush>為, 其繼承自。 <xref:System.Drawing.Brush>  
  
## <a name="hatch-brushes"></a>影線筆刷  
 當您填滿具有影線筆刷的圖形時, 您可以指定前景色彩、背景色彩和影線樣式。 前景色彩是影線的色彩。  
  
 [!code-csharp[LinesCurvesAndShapes#122](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 GDI + 提供超過50的影線樣式;下圖所示的三種樣式為<xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>、 <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>和<xref:System.Drawing.Drawing2D.HatchStyle.Cross>。  
  
 ![填滿的圖案](./media/aboutgdip02-art18.gif "Aboutgdip02_art18")  
  
## <a name="texture-brushes"></a>材質筆刷  
 使用材質筆刷時, 您可以使用儲存在點陣圖中的模式來填滿圖形。 例如, 假設下圖儲存在名為`MyTexture.bmp`的磁片檔案中。  
  
 ![填滿的圖形](./media/aboutgdip02-art19.gif "Aboutgdip02_Art19")  
  
 下列程式碼範例示範如何透過重複儲存在中`MyTexture.bmp`的圖片來填滿橢圓形。  
  
 [!code-csharp[LinesCurvesAndShapes#123](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 下圖顯示已填滿的橢圓形。  
  
 ![填滿的圖形](./media/aboutgdip02-art20.gif "AboutGdip02_Art20")  
  
## <a name="gradient-brushes"></a>漸層筆刷  
 GDI + 提供兩種漸層筆刷: 線性和路徑。 您可以使用線性漸層筆刷, 將色彩變更為水準、垂直或對角線地在圖形上移動時, 逐漸變化。 下列程式碼範例示範如何使用水準漸層筆刷來填滿橢圓形, 這會在您從橢圓形的左邊緣移至右邊緣時, 從藍色變更為綠色。  
  
 [!code-csharp[LinesCurvesAndShapes#124](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 下圖顯示已填滿的橢圓形。  
  
 ![填滿的圖形](./media/aboutgdip02-art21.gif "AboutGdip02_Art21")  
  
 您可以設定路徑漸層筆刷, 以便在您從圖形的中央往邊緣移動時變更色彩。  
  
 ![填滿的圖形](./media/aboutgdip02-art22.gif "AboutGdip02_Art22")  
  
 路徑漸層筆刷相當有彈性。 在下圖中用來填滿三角形的漸層筆刷, 會從中央的紅色逐漸變更為頂點上的三種不同色彩。  
  
 ![填滿的圖形](./media/aboutgdip02-art23.gif "AboutGdip02_Art23")  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>
- <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [線條、曲線和形狀](lines-curves-and-shapes.md)
- [如何：在 Windows Form 上繪製實心矩形](how-to-draw-a-filled-rectangle-on-a-windows-form.md)
- [如何：在 Windows Form 上繪製實心橢圓形](how-to-draw-a-filled-ellipse-on-a-windows-form.md)
