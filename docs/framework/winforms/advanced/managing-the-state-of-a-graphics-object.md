---
title: 管理圖形物件的狀態
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], managing state
- graphics [Windows Forms], clipping
ms.assetid: 6207cad1-7a34-4bd6-bfc1-db823ca7a73e
ms.openlocfilehash: d1e7e6eac775ca779fb68605adcc9bc2b9915e49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182459"
---
# <a name="managing-the-state-of-a-graphics-object"></a>管理圖形物件的狀態
該<xref:System.Drawing.Graphics>課程是 GDI® 的核心。 要繪製任何內容，請獲取<xref:System.Drawing.Graphics>物件、設置其屬性並調用其方法<xref:System.Drawing.Graphics.DrawLine%2A>、、<xref:System.Drawing.Graphics.DrawString%2A><xref:System.Drawing.Graphics.DrawImage%2A>等。  
  
 下面的示例調用<xref:System.Drawing.Graphics.DrawRectangle%2A><xref:System.Drawing.Graphics>物件的方法。 傳遞給<xref:System.Drawing.Graphics.DrawRectangle%2A>方法的第一個參數是物件<xref:System.Drawing.Pen>。  
  
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
 物件<xref:System.Drawing.Graphics>的作用不僅僅是提供繪圖方法，如<xref:System.Drawing.Graphics.DrawLine%2A>和<xref:System.Drawing.Graphics.DrawRectangle%2A>。 物件<xref:System.Drawing.Graphics>還維護圖形狀態，可以分為以下幾類：  
  
- 品質設置  
  
- 轉換  
  
- 裁剪區域  
  
### <a name="quality-settings"></a>品質設置  
 物件<xref:System.Drawing.Graphics>具有多個屬性，這些屬性會影響所繪製的項的品質。 例如，<xref:System.Drawing.Graphics.TextRenderingHint%2A>可以將 屬性設置為指定應用於文本的反鋸齒類型（如果有）。 影響品質<xref:System.Drawing.Graphics.SmoothingMode%2A>的其他屬性是 、<xref:System.Drawing.Graphics.CompositingMode%2A><xref:System.Drawing.Graphics.CompositingQuality%2A>和<xref:System.Drawing.Graphics.InterpolationMode%2A>。  
  
 下面的示例繪製兩個橢圓，一個設置為平滑模式<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>，另一個將平滑模式設置為 ： <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>  
  
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
 物件<xref:System.Drawing.Graphics>維護應用於該<xref:System.Drawing.Graphics>物件繪製的所有項的兩個轉換（世界和頁面）。 任何仿冒變換都可以儲存在世界變換中。 仿法變換包括縮放、旋轉、反射、傾斜和平移。 頁面轉換可用於縮放和更改單位（例如，圖元到英寸）。 有關詳細資訊，請參閱[坐標系和變換](coordinate-systems-and-transformations.md)。  
  
 下面的示例設置<xref:System.Drawing.Graphics>物件的世界和頁面轉換。 世界轉型設置為 30 度旋轉。 設置頁面變換，以便傳遞給第二<xref:System.Drawing.Graphics.DrawEllipse%2A>個座標將被視為毫米而不是圖元。 代碼對<xref:System.Drawing.Graphics.DrawEllipse%2A>該方法進行兩個相同的調用。 世界轉換應用於第一個<xref:System.Drawing.Graphics.DrawEllipse%2A>調用，並且兩個轉換（世界和頁面）都應用於第二個<xref:System.Drawing.Graphics.DrawEllipse%2A>調用。  
  
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
  
 下圖顯示了兩個橢圓。 請注意，30 度旋轉是關於坐標系的原點（工作區的左上角），而不是橢圓的中心。 另請注意，筆寬度 1 表示第一個橢圓的 1 圖元，第二個橢圓的筆寬度為 1 毫米。  
  
 ![顯示兩個橢圓的插圖：旋轉和筆寬度。](./media/managing-the-state-of-a-graphics-object/set-rotation-pen-width-drawellipse-method.png)  
  
### <a name="clipping-region"></a>裁剪區域  
 物件<xref:System.Drawing.Graphics>維護一個裁剪區域，該區域適用于該<xref:System.Drawing.Graphics>物件繪製的所有專案。 您可以通過調用<xref:System.Drawing.Graphics.SetClip%2A>方法來設置裁剪區域。  
  
 下面的示例通過形成兩個矩形的合併來創建一個加形區域。 該區域被指定為<xref:System.Drawing.Graphics>物件的裁剪區域。 然後，代碼繪製兩行，這些行僅限於裁剪區域的內部。  
  
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
  
 下圖顯示了剪切的線條：  
  
 ![顯示有限剪輯區域的圖表。](./media/managing-the-state-of-a-graphics-object/set-clipping-region-setclip-method.png)  
  
## <a name="see-also"></a>另請參閱

- [Windows Form 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
- [使用巢狀圖形容器](using-nested-graphics-containers.md)
