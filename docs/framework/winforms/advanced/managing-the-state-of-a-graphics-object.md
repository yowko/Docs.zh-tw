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
# <a name="managing-the-state-of-a-graphics-object"></a><span data-ttu-id="8de3d-102">管理圖形物件的狀態</span><span class="sxs-lookup"><span data-stu-id="8de3d-102">Managing the State of a Graphics Object</span></span>
<span data-ttu-id="8de3d-103">該<xref:System.Drawing.Graphics>課程是 GDI® 的核心。</span><span class="sxs-lookup"><span data-stu-id="8de3d-103">The <xref:System.Drawing.Graphics> class is at the heart of GDI+.</span></span> <span data-ttu-id="8de3d-104">要繪製任何內容，請獲取<xref:System.Drawing.Graphics>物件、設置其屬性並調用其方法<xref:System.Drawing.Graphics.DrawLine%2A>、、<xref:System.Drawing.Graphics.DrawString%2A><xref:System.Drawing.Graphics.DrawImage%2A>等。</span><span class="sxs-lookup"><span data-stu-id="8de3d-104">To draw anything, you obtain a <xref:System.Drawing.Graphics> object, set its properties, and call its methods <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>, and the like).</span></span>  
  
 <span data-ttu-id="8de3d-105">下面的示例調用<xref:System.Drawing.Graphics.DrawRectangle%2A><xref:System.Drawing.Graphics>物件的方法。</span><span class="sxs-lookup"><span data-stu-id="8de3d-105">The following example calls the <xref:System.Drawing.Graphics.DrawRectangle%2A> method of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="8de3d-106">傳遞給<xref:System.Drawing.Graphics.DrawRectangle%2A>方法的第一個參數是物件<xref:System.Drawing.Pen>。</span><span class="sxs-lookup"><span data-stu-id="8de3d-106">The first argument passed to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method is a <xref:System.Drawing.Pen> object.</span></span>  
  
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
  
## <a name="graphics-state"></a><span data-ttu-id="8de3d-107">圖形狀態</span><span class="sxs-lookup"><span data-stu-id="8de3d-107">Graphics State</span></span>  
 <span data-ttu-id="8de3d-108">物件<xref:System.Drawing.Graphics>的作用不僅僅是提供繪圖方法，如<xref:System.Drawing.Graphics.DrawLine%2A>和<xref:System.Drawing.Graphics.DrawRectangle%2A>。</span><span class="sxs-lookup"><span data-stu-id="8de3d-108">A <xref:System.Drawing.Graphics> object does more than provide drawing methods, such as <xref:System.Drawing.Graphics.DrawLine%2A> and <xref:System.Drawing.Graphics.DrawRectangle%2A>.</span></span> <span data-ttu-id="8de3d-109">物件<xref:System.Drawing.Graphics>還維護圖形狀態，可以分為以下幾類：</span><span class="sxs-lookup"><span data-stu-id="8de3d-109">A <xref:System.Drawing.Graphics> object also maintains graphics state, which can be divided into the following categories:</span></span>  
  
- <span data-ttu-id="8de3d-110">品質設置</span><span class="sxs-lookup"><span data-stu-id="8de3d-110">Quality settings</span></span>  
  
- <span data-ttu-id="8de3d-111">轉換</span><span class="sxs-lookup"><span data-stu-id="8de3d-111">Transformations</span></span>  
  
- <span data-ttu-id="8de3d-112">裁剪區域</span><span class="sxs-lookup"><span data-stu-id="8de3d-112">Clipping region</span></span>  
  
### <a name="quality-settings"></a><span data-ttu-id="8de3d-113">品質設置</span><span class="sxs-lookup"><span data-stu-id="8de3d-113">Quality Settings</span></span>  
 <span data-ttu-id="8de3d-114">物件<xref:System.Drawing.Graphics>具有多個屬性，這些屬性會影響所繪製的項的品質。</span><span class="sxs-lookup"><span data-stu-id="8de3d-114">A <xref:System.Drawing.Graphics> object has several properties that influence the quality of the items that are drawn.</span></span> <span data-ttu-id="8de3d-115">例如，<xref:System.Drawing.Graphics.TextRenderingHint%2A>可以將 屬性設置為指定應用於文本的反鋸齒類型（如果有）。</span><span class="sxs-lookup"><span data-stu-id="8de3d-115">For example, you can set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property to specify the type of antialiasing (if any) applied to text.</span></span> <span data-ttu-id="8de3d-116">影響品質<xref:System.Drawing.Graphics.SmoothingMode%2A>的其他屬性是 、<xref:System.Drawing.Graphics.CompositingMode%2A><xref:System.Drawing.Graphics.CompositingQuality%2A>和<xref:System.Drawing.Graphics.InterpolationMode%2A>。</span><span class="sxs-lookup"><span data-stu-id="8de3d-116">Other properties that influence quality are <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, and <xref:System.Drawing.Graphics.InterpolationMode%2A>.</span></span>  
  
 <span data-ttu-id="8de3d-117">下面的示例繪製兩個橢圓，一個設置為平滑模式<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>，另一個將平滑模式設置為 ： <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed></span><span class="sxs-lookup"><span data-stu-id="8de3d-117">The following example draws two ellipses, one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> and one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:</span></span>  
  
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
  
### <a name="transformations"></a><span data-ttu-id="8de3d-118">轉換</span><span class="sxs-lookup"><span data-stu-id="8de3d-118">Transformations</span></span>  
 <span data-ttu-id="8de3d-119">物件<xref:System.Drawing.Graphics>維護應用於該<xref:System.Drawing.Graphics>物件繪製的所有項的兩個轉換（世界和頁面）。</span><span class="sxs-lookup"><span data-stu-id="8de3d-119">A <xref:System.Drawing.Graphics> object maintains two transformations (world and page) that are applied to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="8de3d-120">任何仿冒變換都可以儲存在世界變換中。</span><span class="sxs-lookup"><span data-stu-id="8de3d-120">Any affine transformation can be stored in the world transformation.</span></span> <span data-ttu-id="8de3d-121">仿法變換包括縮放、旋轉、反射、傾斜和平移。</span><span class="sxs-lookup"><span data-stu-id="8de3d-121">Affine transformations include scaling, rotating, reflecting, skewing, and translating.</span></span> <span data-ttu-id="8de3d-122">頁面轉換可用於縮放和更改單位（例如，圖元到英寸）。</span><span class="sxs-lookup"><span data-stu-id="8de3d-122">The page transformation can be used for scaling and for changing units (for example, pixels to inches).</span></span> <span data-ttu-id="8de3d-123">有關詳細資訊，請參閱[坐標系和變換](coordinate-systems-and-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="8de3d-123">For more information, see [Coordinate Systems and Transformations](coordinate-systems-and-transformations.md).</span></span>  
  
 <span data-ttu-id="8de3d-124">下面的示例設置<xref:System.Drawing.Graphics>物件的世界和頁面轉換。</span><span class="sxs-lookup"><span data-stu-id="8de3d-124">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="8de3d-125">世界轉型設置為 30 度旋轉。</span><span class="sxs-lookup"><span data-stu-id="8de3d-125">The world transformation is set to a 30-degree rotation.</span></span> <span data-ttu-id="8de3d-126">設置頁面變換，以便傳遞給第二<xref:System.Drawing.Graphics.DrawEllipse%2A>個座標將被視為毫米而不是圖元。</span><span class="sxs-lookup"><span data-stu-id="8de3d-126">The page transformation is set so that the coordinates passed to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> will be treated as millimeters instead of pixels.</span></span> <span data-ttu-id="8de3d-127">代碼對<xref:System.Drawing.Graphics.DrawEllipse%2A>該方法進行兩個相同的調用。</span><span class="sxs-lookup"><span data-stu-id="8de3d-127">The code makes two identical calls to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method.</span></span> <span data-ttu-id="8de3d-128">世界轉換應用於第一個<xref:System.Drawing.Graphics.DrawEllipse%2A>調用，並且兩個轉換（世界和頁面）都應用於第二個<xref:System.Drawing.Graphics.DrawEllipse%2A>調用。</span><span class="sxs-lookup"><span data-stu-id="8de3d-128">The world transformation is applied to the first <xref:System.Drawing.Graphics.DrawEllipse%2A> call, and both transformations (world and page) are applied to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> call.</span></span>  
  
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
  
 <span data-ttu-id="8de3d-129">下圖顯示了兩個橢圓。</span><span class="sxs-lookup"><span data-stu-id="8de3d-129">The following illustration shows the two ellipses.</span></span> <span data-ttu-id="8de3d-130">請注意，30 度旋轉是關於坐標系的原點（工作區的左上角），而不是橢圓的中心。</span><span class="sxs-lookup"><span data-stu-id="8de3d-130">Note that the 30-degree rotation is about the origin of the coordinate system (upper-left corner of the client area), not about the centers of the ellipses.</span></span> <span data-ttu-id="8de3d-131">另請注意，筆寬度 1 表示第一個橢圓的 1 圖元，第二個橢圓的筆寬度為 1 毫米。</span><span class="sxs-lookup"><span data-stu-id="8de3d-131">Also note that the pen width of 1 means 1 pixel for the first ellipse and 1 millimeter for the second ellipse.</span></span>  
  
 ![顯示兩個橢圓的插圖：旋轉和筆寬度。](./media/managing-the-state-of-a-graphics-object/set-rotation-pen-width-drawellipse-method.png)  
  
### <a name="clipping-region"></a><span data-ttu-id="8de3d-133">裁剪區域</span><span class="sxs-lookup"><span data-stu-id="8de3d-133">Clipping Region</span></span>  
 <span data-ttu-id="8de3d-134">物件<xref:System.Drawing.Graphics>維護一個裁剪區域，該區域適用于該<xref:System.Drawing.Graphics>物件繪製的所有專案。</span><span class="sxs-lookup"><span data-stu-id="8de3d-134">A <xref:System.Drawing.Graphics> object maintains a clipping region that applies to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="8de3d-135">您可以通過調用<xref:System.Drawing.Graphics.SetClip%2A>方法來設置裁剪區域。</span><span class="sxs-lookup"><span data-stu-id="8de3d-135">You can set the clipping region by calling the <xref:System.Drawing.Graphics.SetClip%2A> method.</span></span>  
  
 <span data-ttu-id="8de3d-136">下面的示例通過形成兩個矩形的合併來創建一個加形區域。</span><span class="sxs-lookup"><span data-stu-id="8de3d-136">The following example creates a plus-shaped region by forming the union of two rectangles.</span></span> <span data-ttu-id="8de3d-137">該區域被指定為<xref:System.Drawing.Graphics>物件的裁剪區域。</span><span class="sxs-lookup"><span data-stu-id="8de3d-137">That region is designated as the clipping region of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="8de3d-138">然後，代碼繪製兩行，這些行僅限於裁剪區域的內部。</span><span class="sxs-lookup"><span data-stu-id="8de3d-138">Then the code draws two lines that are restricted to the interior of the clipping region.</span></span>  
  
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
  
 <span data-ttu-id="8de3d-139">下圖顯示了剪切的線條：</span><span class="sxs-lookup"><span data-stu-id="8de3d-139">The following illustration shows the clipped lines:</span></span>  
  
 ![顯示有限剪輯區域的圖表。](./media/managing-the-state-of-a-graphics-object/set-clipping-region-setclip-method.png)  
  
## <a name="see-also"></a><span data-ttu-id="8de3d-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8de3d-141">See also</span></span>

- [<span data-ttu-id="8de3d-142">Windows Form 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="8de3d-142">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="8de3d-143">使用巢狀圖形容器</span><span class="sxs-lookup"><span data-stu-id="8de3d-143">Using Nested Graphics Containers</span></span>](using-nested-graphics-containers.md)
