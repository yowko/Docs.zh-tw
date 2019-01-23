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
ms.openlocfilehash: 197678cfdced1e17ad87f521a30c7103c49df4e4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624178"
---
# <a name="brushes-and-filled-shapes-in-gdi"></a>GDI+ 中的筆刷和填滿的形狀
封閉的形狀，例如矩形或橢圓形，是由外框和內部所組成。 使用畫筆繪製外框，並使用筆刷填滿內部。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供來填滿的封閉的形狀內部的筆刷的數個類別： <xref:System.Drawing.SolidBrush>， <xref:System.Drawing.Drawing2D.HatchBrush>， <xref:System.Drawing.TextureBrush>， <xref:System.Drawing.Drawing2D.LinearGradientBrush>，和<xref:System.Drawing.Drawing2D.PathGradientBrush>。 所有這些類別繼承自<xref:System.Drawing.Brush>類別。 下圖顯示使用實心筆刷填滿的矩形和橢圓形填滿影線筆刷。  
  
 ![填滿形狀](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art17.gif "Aboutgdip02_art17")  
  
## <a name="solid-brushes"></a>實心筆刷  
 若要填滿一個封閉的形狀 中，您需要的執行個體<xref:System.Drawing.Graphics>類別和<xref:System.Drawing.Brush>。 執行個體<xref:System.Drawing.Graphics>類別提供方法，例如<xref:System.Drawing.Graphics.FillRectangle%2A>並<xref:System.Drawing.Graphics.FillEllipse%2A>，和<xref:System.Drawing.Brush>儲存的填滿，例如色彩和模式的屬性。 <xref:System.Drawing.Brush>做為其中一個引數傳遞至填滿方法。 下列程式碼範例示範如何使用紅色純色填滿橢圓形。  
  
 [!code-csharp[LinesCurvesAndShapes#121](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
>  在上述範例中，筆刷是型別的<xref:System.Drawing.SolidBrush>，該項則繼承自<xref:System.Drawing.Brush>。  
  
## <a name="hatch-brushes"></a>筆刷  
 當您規劃筆刷填滿圖形時，請指定前景色彩、 背景色彩和影線樣式。 前景色彩是影線色彩。  
  
 [!code-csharp[LinesCurvesAndShapes#122](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供超過 50 的影線樣式;下圖所示的三個樣式如下<xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>， <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>，和<xref:System.Drawing.Drawing2D.HatchStyle.Cross>。  
  
 ![填滿形狀](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art18.gif "Aboutgdip02_art18")  
  
## <a name="texture-brushes"></a>紋理筆刷  
 使用紋理筆刷可以填滿形狀，以儲存在點陣圖中的模式。 例如，假設下列圖片會儲存在名為的磁碟檔案`MyTexture.bmp`。  
  
 ![填滿形狀](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art19.gif "Aboutgdip02_Art19")  
  
 下列程式碼範例示範如何藉由重複圖片儲存在填滿橢圓形`MyTexture.bmp`。  
  
 [!code-csharp[LinesCurvesAndShapes#123](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 下圖顯示實心的橢圓形。  
  
 ![填滿形狀](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art20.gif "AboutGdip02_Art20")  
  
## <a name="gradient-brushes"></a>漸層筆刷  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供的漸層筆刷的兩種類型： 線性和路徑。 若要變更逐漸，當您移動形狀之間水平、 垂直或對角線方式的色彩填滿圖形，您可以使用線性漸層筆刷。 下列程式碼範例示範如何使用變更從藍綠色當您從省略符號的左邊緣移至 右邊緣的水平漸層筆刷填滿橢圓形。  
  
 [!code-csharp[LinesCurvesAndShapes#124](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 下圖顯示實心的橢圓形。  
  
 ![填滿形狀](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art21.gif "AboutGdip02_Art21")  
  
 若要變更色彩，當您從邊緣，圖案的中心移動，可以設定路徑漸層筆刷。  
  
 ![填滿形狀](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art22.gif "AboutGdip02_Art22")  
  
 路徑漸層筆刷會很有彈性。 漸層筆刷，用來填滿每個頂點的三個不同色彩逐漸從紅色中心下列圖變更中的三角形。  
  
 ![填滿形狀](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art23.gif "AboutGdip02_Art23")  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>
- <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)
- [如何：Windows Form 上繪製實心的矩形](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-rectangle-on-a-windows-form.md)
- [如何：Windows Form 上繪製實心的橢圓形](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-ellipse-on-a-windows-form.md)
