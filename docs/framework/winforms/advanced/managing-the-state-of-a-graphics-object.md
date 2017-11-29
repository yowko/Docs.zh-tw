---
title: "管理圖形物件的狀態"
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
- graphics [Windows Forms], managing state
- graphics [Windows Forms], clipping
ms.assetid: 6207cad1-7a34-4bd6-bfc1-db823ca7a73e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 438243d16d8031d99e27993cadb44fd58bbec0b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="managing-the-state-of-a-graphics-object"></a>管理圖形物件的狀態
<xref:System.Drawing.Graphics>類別的核心是[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]。 若要繪製的任何項目，您取得<xref:System.Drawing.Graphics>物件、 設定其屬性，並呼叫其方法<xref:System.Drawing.Graphics.DrawLine%2A>， <xref:System.Drawing.Graphics.DrawImage%2A>， <xref:System.Drawing.Graphics.DrawString%2A>，等等)。  
  
 下列範例會呼叫<xref:System.Drawing.Graphics.DrawRectangle%2A>方法<xref:System.Drawing.Graphics>物件。 第一個引數傳遞至<xref:System.Drawing.Graphics.DrawRectangle%2A>方法<xref:System.Drawing.Pen>物件。  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Blue) ' Opaque blue  
graphics.DrawRectangle(pen, 10, 10, 200, 100)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Blue);  // Opaque blue  
graphics.DrawRectangle(pen, 10, 10, 200, 100);  
```  
  
## <a name="graphics-state"></a>圖形狀態  
 A<xref:System.Drawing.Graphics>物件沒有多個提供繪圖方法，例如<xref:System.Drawing.Graphics.DrawLine%2A>和<xref:System.Drawing.Graphics.DrawRectangle%2A>。 A<xref:System.Drawing.Graphics>物件也會維護圖形狀態，可以分為下列類別：  
  
-   品質設定  
  
-   轉換  
  
-   裁剪區域  
  
### <a name="quality-settings"></a>品質設定  
 A<xref:System.Drawing.Graphics>物件有好幾個屬性會影響的項目所繪製的品質。 例如，您可以設定<xref:System.Drawing.Graphics.TextRenderingHint%2A>屬性來指定套用至文字消除鋸齒 （如果有的話） 的型別。 品質會影響其他屬性則<xref:System.Drawing.Graphics.SmoothingMode%2A>， <xref:System.Drawing.Graphics.CompositingMode%2A>， <xref:System.Drawing.Graphics.CompositingQuality%2A>，和<xref:System.Drawing.Graphics.InterpolationMode%2A>。  
  
 下列範例會繪製平滑模式設定為使用其中一個的兩個橢圓形<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>，以及平滑化模式設為另一個<xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Blue)  
  
graphics.SmoothingMode = SmoothingMode.AntiAlias  
graphics.DrawEllipse(pen, 0, 0, 200, 100)  
graphics.SmoothingMode = SmoothingMode.HighSpeed  
graphics.DrawEllipse(pen, 0, 150, 200, 100)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Blue);  
  
graphics.SmoothingMode = SmoothingMode.AntiAlias;  
graphics.DrawEllipse(pen, 0, 0, 200, 100);  
graphics.SmoothingMode = SmoothingMode.HighSpeed;  
graphics.DrawEllipse(pen, 0, 150, 200, 100);  
```  
  
### <a name="transformations"></a>轉換  
 A<xref:System.Drawing.Graphics>物件會維護兩個 （全局和頁面） 的轉換會套用至所有項目，來繪製<xref:System.Drawing.Graphics>物件。 任何仿射轉換可以儲存在全局轉換中。 仿射轉換包括縮放、 旋轉、 反射、 扭曲，和轉譯。 可用於頁面轉換，縮放比例和變更單位 （例如，像素為單位為英吋）。 如需詳細資訊，請參閱[座標系統和轉換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)。  
  
 下列範例會設定全局和頁面轉換<xref:System.Drawing.Graphics>物件。 全局轉換設定為 30 度旋轉。 頁面轉換設定讓座標傳遞至第二個<xref:System.Drawing.Graphics.DrawEllipse%2A>會被視為公釐為單位，而不是像素為單位。 程式碼，使兩個相同呼叫<xref:System.Drawing.Graphics.DrawEllipse%2A>方法。 全局轉換會套用至第一個<xref:System.Drawing.Graphics.DrawEllipse%2A>呼叫或這兩種轉換 （全局和頁面） 會套用到第二個<xref:System.Drawing.Graphics.DrawEllipse%2A>呼叫。  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Red)  
  
graphics.ResetTransform()  
graphics.RotateTransform(30) ' world transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50)  
graphics.PageUnit = GraphicsUnit.Millimeter ' page transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Red);   
  
graphics.ResetTransform();  
graphics.RotateTransform(30);                    // world transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50);  
graphics.PageUnit = GraphicsUnit.Millimeter;     // page transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50);  
```  
  
 下圖顯示兩個橢圓形。 請注意，30 度旋轉 （用戶端區域的左上角） 座標系統的原點，而非橢圓形的中心。 也請注意畫筆寬度為 1，表示第二個橢圓形的 1 個像素的第一個橢圓形和 1 公釐。  
  
 ![橢圓形](../../../../docs/framework/winforms/advanced/media/csgraphicsascon1.png "csgraphicsascon1")  
  
### <a name="clipping-region"></a>裁剪區域  
 A<xref:System.Drawing.Graphics>物件會維護適用於所有的項目繪製的裁剪區域<xref:System.Drawing.Graphics>物件。 您可以藉由呼叫設定的裁剪區域<xref:System.Drawing.Graphics.SetClip%2A>方法。  
  
 下列範例會建立所形成聯集兩個矩形的加號形狀的區域。 該區域指定的裁剪區域為<xref:System.Drawing.Graphics>物件。 然後程式碼繪製兩行，僅限於裁剪區域的內部。  
  
```vb  
Dim graphics As Graphics = e.Graphics  
  
' Opaque red, width 5  
Dim pen As New Pen(Color.Red, 5)  
  
' Opaque aqua  
Dim brush As New SolidBrush(Color.FromArgb(255, 180, 255, 255))  
  
' Create a plus-shaped region by forming the union of two rectangles.  
Dim [region] As New [Region](New Rectangle(50, 0, 50, 150))  
[region].Union(New Rectangle(0, 50, 150, 50))  
graphics.FillRegion(brush, [region])  
  
' Set the clipping region.  
graphics.SetClip([region], CombineMode.Replace)  
  
' Draw two clipped lines.  
graphics.DrawLine(pen, 0, 30, 150, 160)  
graphics.DrawLine(pen, 40, 20, 190, 150)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
  
// Opaque red, width 5  
Pen pen = new Pen(Color.Red, 5);    
  
// Opaque aqua  
SolidBrush brush = new SolidBrush(Color.FromArgb(255, 180, 255, 255));    
  
// Create a plus-shaped region by forming the union of two rectangles.  
Region region = new Region(new Rectangle(50, 0, 50, 150));  
region.Union(new Rectangle(0, 50, 150, 50));  
graphics.FillRegion(brush, region);  
  
// Set the clipping region.  
graphics.SetClip(region, CombineMode.Replace);  
  
// Draw two clipped lines.  
graphics.DrawLine(pen, 0, 30, 150, 160);  
graphics.DrawLine(pen, 40, 20, 190, 150);  
```  
  
 下圖顯示裁剪的線條。  
  
 ![有限的裁剪區域](../../../../docs/framework/winforms/advanced/media/graphicsascon2.png "graphicsascon2")  
  
## <a name="see-also"></a>另請參閱  
 [Windows Forms 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [使用巢狀圖形容器](../../../../docs/framework/winforms/advanced/using-nested-graphics-containers.md)
