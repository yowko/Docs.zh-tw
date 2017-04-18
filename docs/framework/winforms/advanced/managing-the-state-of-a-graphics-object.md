---
title: "管理圖形物件的狀態 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "圖形, 裁剪"
  - "圖形, 管理狀態"
ms.assetid: 6207cad1-7a34-4bd6-bfc1-db823ca7a73e
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 管理圖形物件的狀態
<xref:System.Drawing.Graphics> 類別是 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 的核心。  若要繪製任何項目，請您取得 <xref:System.Drawing.Graphics> 物件、設定其屬性，並呼叫它的方法 <xref:System.Drawing.Graphics.DrawLine%2A>、<xref:System.Drawing.Graphics.DrawImage%2A>、<xref:System.Drawing.Graphics.DrawString%2A> 等等。  
  
 下列範例呼叫 <xref:System.Drawing.Graphics> 物件的 <xref:System.Drawing.Graphics.DrawRectangle%2A> 方法。  傳遞至 <xref:System.Drawing.Graphics.DrawRectangle%2A> 方法的第一個引數是 <xref:System.Drawing.Pen> 物件。  
  
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
  
## 圖形狀態  
 <xref:System.Drawing.Graphics> 物件不僅提供繪圖方法，例如 <xref:System.Drawing.Graphics.DrawLine%2A> 和 <xref:System.Drawing.Graphics.DrawRectangle%2A>。  <xref:System.Drawing.Graphics> 物件也會保留圖形狀態，圖形狀態可分為下列幾個分類：  
  
-   品質設定  
  
-   轉換  
  
-   裁剪區域  
  
### 品質設定  
 <xref:System.Drawing.Graphics> 物件具有幾個會影響繪製項目品質的屬性。  例如，您可以設定 <xref:System.Drawing.Graphics.TextRenderingHint%2A> 屬性，以指定套用至文字的反鋸齒類型 \(如果有的話\)。  其他影響品質的屬性還有 <xref:System.Drawing.Graphics.SmoothingMode%2A>、<xref:System.Drawing.Graphics.CompositingMode%2A>、<xref:System.Drawing.Graphics.CompositingQuality%2A> 和 <xref:System.Drawing.Graphics.InterpolationMode%2A>。  
  
 下列範例繪製兩個橢圓形，其中一個的平滑化模式設定為 <xref:System.Drawing.Drawing2D.SmoothingMode>，而另一個的平滑化模式則設定為 <xref:System.Drawing.Drawing2D.SmoothingMode>：  
  
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
  
### 轉換  
 <xref:System.Drawing.Graphics> 物件保留了兩種轉換 \(全局和畫面\)，由此 <xref:System.Drawing.Graphics> 物件繪製的所有項目將會套用這兩種轉換。  任何仿射轉換都可以儲存在全局轉換中。  仿射轉換包括縮放、旋轉、反射、傾斜和轉換。  畫面轉換可用來縮放和變更單位 \(例如，將像素變成英吋\)。  如需詳細資訊，請參閱[座標系統和轉換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)。  
  
 下列範例設定 <xref:System.Drawing.Graphics> 物件的全局轉換和畫面轉換。  全局轉換設定為 30 度旋轉。  而畫面轉換則設定為將傳遞至第二個 <xref:System.Drawing.Graphics.DrawEllipse%2A> 的座標單位當成公釐，而非像素。  程式碼會進行兩次完全相同的 <xref:System.Drawing.Graphics.DrawEllipse%2A> 方法呼叫。  第一個 <xref:System.Drawing.Graphics.DrawEllipse%2A> 呼叫套用全局轉換，第二個 <xref:System.Drawing.Graphics.DrawEllipse%2A> 呼叫則是同時套用兩種轉換 \(全局和畫面\)。  
  
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
  
 下圖顯示的是兩個橢圓形。  請注意，30 度旋轉的中心是座標系統的原點 \(工作區的左上角\)，而非橢圓形的中心。  也請注意，畫筆寬度 1 在第一個橢圓形中代表 1 個像素，在第二個橢圓形中則代表 1 公釐。  
  
 ![橢圓形](../../../../docs/framework/winforms/advanced/media/csgraphicsascon1.png "csgraphicsascon1")  
  
### 裁剪區域  
 <xref:System.Drawing.Graphics> 物件保留了一個裁剪區域，由此 <xref:System.Drawing.Graphics> 物件繪製的所有項目將會套用此裁剪區域。  您可以藉由呼叫 <xref:System.Drawing.Graphics.SetClip%2A> 方法來設定裁剪區域。  
  
 下列範例會藉由形成兩個矩形的聯集，來建立加號形狀的區域。  該區域指定為 <xref:System.Drawing.Graphics> 物件的裁剪區域。  然後程式碼會繪製兩條限定在裁剪區域內部的線條。  
  
```vb  
Dim graphics As Graphics = e.Graphics  
  
' Opaque red, width 5  
Dim pen As New Pen(Color.Red, 5)  
  
' Opaque aqua  
Dim brush As New SolidBrush(Color.FromArgb(255, 180, 255, 255))  
  
' Create a plus-shaped region by forming the union of two rectangles.  
Dim [region] As New [Region](../../../../amples/snippets/visualbasic/VS_Snippets_Wpf/ToolBarOrient_snip/visualbasic/toolbargraphics/new.bmp Rectangle(50, 0, 50, 150))  
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
  
 下圖顯示的是裁剪的線條。  
  
 ![有限的裁剪區域](../../../../docs/framework/winforms/advanced/media/graphicsascon2.png "graphicsascon2")  
  
## 請參閱  
 [Windows Form 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [使用巢狀圖形容器](../../../../docs/framework/winforms/advanced/using-nested-graphics-containers.md)