---
title: "GDI+ 中的筆刷和填滿的形狀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 01d7359499c858ad7c4f1da2fa24f18e801bb324
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="brushes-and-filled-shapes-in-gdi"></a>GDI+ 中的筆刷和填滿的形狀
封閉的圖形，例如矩形或橢圓形包含大綱和內部。 繪製外框畫筆和筆刷填滿內部。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]提供填滿內部的封閉圖形筆刷的數個類別： <xref:System.Drawing.SolidBrush>， <xref:System.Drawing.Drawing2D.HatchBrush>， <xref:System.Drawing.TextureBrush>， <xref:System.Drawing.Drawing2D.LinearGradientBrush>，和<xref:System.Drawing.Drawing2D.PathGradientBrush>。 所有這些類別繼承自<xref:System.Drawing.Brush>類別。 下圖顯示與實心筆刷填滿的矩形和橢圓形填滿影線筆刷。  
  
 ![填滿圖形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art17.gif "Aboutgdip02_art17")  
  
## <a name="solid-brushes"></a>純色筆刷  
 若要填滿封閉的圖形時，您需要的執行個體<xref:System.Drawing.Graphics>類別和<xref:System.Drawing.Brush>。 執行個體<xref:System.Drawing.Graphics>類別提供方法，例如<xref:System.Drawing.Graphics.FillRectangle%2A>和<xref:System.Drawing.Graphics.FillEllipse%2A>，而<xref:System.Drawing.Brush>儲存的填滿，例如色彩和模式的屬性。 <xref:System.Drawing.Brush>做為其中一個引數傳遞至填滿方法。 下列程式碼範例示範如何使用紅色純色填滿橢圓形。  
  
 [!code-csharp[LinesCurvesAndShapes#121](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#121)]
 [!code-vb[LinesCurvesAndShapes#121](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#121)]  
  
> [!NOTE]
>  在上述範例中，筆刷屬於型別<xref:System.Drawing.SolidBrush>，後者繼承自<xref:System.Drawing.Brush>。  
  
## <a name="hatch-brushes"></a>規劃筆刷  
 當您使用規劃筆刷填滿圖案時，您可以指定前景色彩、 背景色彩和影線樣式。 前景色彩是影線色彩。  
  
 [!code-csharp[LinesCurvesAndShapes#122](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#122)]
 [!code-vb[LinesCurvesAndShapes#122](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#122)]  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]提供超過 50 個影線樣式。下圖所示的三種樣式<xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>， <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>，和<xref:System.Drawing.Drawing2D.HatchStyle.Cross>。  
  
 ![填滿圖形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art18.gif "Aboutgdip02_art18")  
  
## <a name="texture-brushes"></a>紋理筆刷  
 使用紋理筆刷，您可以使用儲存在點陣圖中的模式填滿圖形。 例如，假設下列圖片會儲存在名為的磁碟檔案`MyTexture.bmp`。  
  
 ![填滿圖形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art19.gif "Aboutgdip02_Art19")  
  
 下列程式碼範例示範如何藉由重複圖片儲存在填滿橢圓形`MyTexture.bmp`。  
  
 [!code-csharp[LinesCurvesAndShapes#123](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#123)]
 [!code-vb[LinesCurvesAndShapes#123](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#123)]  
  
 下圖顯示實心的橢圓形。  
  
 ![填滿圖形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art20.gif "AboutGdip02_Art20")  
  
## <a name="gradient-brushes"></a>漸層筆刷  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]提供兩種漸層筆刷： 線性和路徑。 您可以使用線性漸層筆刷填滿圖形，以變更逐漸，當您移動形狀之間水平、 垂直或對角線的色彩。 下列程式碼範例示範如何使用當您移動距離左邊緣的橢圓形的右邊緣，變更從藍綠色水平漸層筆刷填滿橢圓形。  
  
 [!code-csharp[LinesCurvesAndShapes#124](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#124)]
 [!code-vb[LinesCurvesAndShapes#124](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#124)]  
  
 下圖顯示實心的橢圓形。  
  
 ![填滿圖形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art21.gif "AboutGdip02_Art21")  
  
 路徑漸層筆刷可以設定來變更色彩，當您從邊緣圖案的中心移動。  
  
 ![填滿圖形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art22.gif "AboutGdip02_Art22")  
  
 路徑漸層筆刷時相當有彈性。 漸層筆刷用來填滿至每個頂點的三種色彩逐漸從中央的紅色下列圖例變更的三角形。  
  
 ![填滿圖形](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art23.gif "AboutGdip02_Art23")  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.SolidBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.HatchBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.TextureBrush?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [操作說明：在 Windows Forms 上繪製實心矩形](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-rectangle-on-a-windows-form.md)  
 [操作說明：在 Windows Forms 上繪製實心橢圓形](../../../../docs/framework/winforms/advanced/how-to-draw-a-filled-ellipse-on-a-windows-form.md)
