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
ms.openlocfilehash: fc961b59dabc2f7f123b792e7e45a4ff3b535fc1
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717618"
---
# <a name="managing-the-state-of-a-graphics-object"></a><span data-ttu-id="36cb4-102">管理圖形物件的狀態</span><span class="sxs-lookup"><span data-stu-id="36cb4-102">Managing the State of a Graphics Object</span></span>
<span data-ttu-id="36cb4-103"><xref:System.Drawing.Graphics>類別的核心是[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="36cb4-103">The <xref:System.Drawing.Graphics> class is at the heart of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="36cb4-104">若要繪製的任何項目，取得<xref:System.Drawing.Graphics>物件、 設定其屬性，並呼叫其方法<xref:System.Drawing.Graphics.DrawLine%2A>， <xref:System.Drawing.Graphics.DrawImage%2A>， <xref:System.Drawing.Graphics.DrawString%2A>，等等)。</span><span class="sxs-lookup"><span data-stu-id="36cb4-104">To draw anything, you obtain a <xref:System.Drawing.Graphics> object, set its properties, and call its methods <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>, and the like).</span></span>  
  
 <span data-ttu-id="36cb4-105">下列範例會呼叫<xref:System.Drawing.Graphics.DrawRectangle%2A>方法的<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="36cb4-105">The following example calls the <xref:System.Drawing.Graphics.DrawRectangle%2A> method of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="36cb4-106">第一個引數傳遞給<xref:System.Drawing.Graphics.DrawRectangle%2A>方法是<xref:System.Drawing.Pen>物件。</span><span class="sxs-lookup"><span data-stu-id="36cb4-106">The first argument passed to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method is a <xref:System.Drawing.Pen> object.</span></span>  
  
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
  
## <a name="graphics-state"></a><span data-ttu-id="36cb4-107">圖形狀態</span><span class="sxs-lookup"><span data-stu-id="36cb4-107">Graphics State</span></span>  
 <span data-ttu-id="36cb4-108">A<xref:System.Drawing.Graphics>物件沒有多個提供繪製方法，例如<xref:System.Drawing.Graphics.DrawLine%2A>和<xref:System.Drawing.Graphics.DrawRectangle%2A>。</span><span class="sxs-lookup"><span data-stu-id="36cb4-108">A <xref:System.Drawing.Graphics> object does more than provide drawing methods, such as <xref:System.Drawing.Graphics.DrawLine%2A> and <xref:System.Drawing.Graphics.DrawRectangle%2A>.</span></span> <span data-ttu-id="36cb4-109">A<xref:System.Drawing.Graphics>物件也會維護圖形狀態，可分成下列類別：</span><span class="sxs-lookup"><span data-stu-id="36cb4-109">A <xref:System.Drawing.Graphics> object also maintains graphics state, which can be divided into the following categories:</span></span>  
  
-   <span data-ttu-id="36cb4-110">品質設定</span><span class="sxs-lookup"><span data-stu-id="36cb4-110">Quality settings</span></span>  
  
-   <span data-ttu-id="36cb4-111">轉換</span><span class="sxs-lookup"><span data-stu-id="36cb4-111">Transformations</span></span>  
  
-   <span data-ttu-id="36cb4-112">裁剪區域</span><span class="sxs-lookup"><span data-stu-id="36cb4-112">Clipping region</span></span>  
  
### <a name="quality-settings"></a><span data-ttu-id="36cb4-113">品質設定</span><span class="sxs-lookup"><span data-stu-id="36cb4-113">Quality Settings</span></span>  
 <span data-ttu-id="36cb4-114">A<xref:System.Drawing.Graphics>物件有數個屬性會影響所繪製項目的品質。</span><span class="sxs-lookup"><span data-stu-id="36cb4-114">A <xref:System.Drawing.Graphics> object has several properties that influence the quality of the items that are drawn.</span></span> <span data-ttu-id="36cb4-115">例如，您可以設定<xref:System.Drawing.Graphics.TextRenderingHint%2A>屬性可指定對文字套用消除鋸齒 （如果有的話） 的類型。</span><span class="sxs-lookup"><span data-stu-id="36cb4-115">For example, you can set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property to specify the type of antialiasing (if any) applied to text.</span></span> <span data-ttu-id="36cb4-116">品質會影響其他屬性都<xref:System.Drawing.Graphics.SmoothingMode%2A>， <xref:System.Drawing.Graphics.CompositingMode%2A>， <xref:System.Drawing.Graphics.CompositingQuality%2A>，和<xref:System.Drawing.Graphics.InterpolationMode%2A>。</span><span class="sxs-lookup"><span data-stu-id="36cb4-116">Other properties that influence quality are <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, and <xref:System.Drawing.Graphics.InterpolationMode%2A>.</span></span>  
  
 <span data-ttu-id="36cb4-117">下列範例會繪製平滑的模式設定為其中一個的兩個橢圓形<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>部署，一個用於平滑模式設定為<xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:</span><span class="sxs-lookup"><span data-stu-id="36cb4-117">The following example draws two ellipses, one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> and one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:</span></span>  
  
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
  
### <a name="transformations"></a><span data-ttu-id="36cb4-118">轉換</span><span class="sxs-lookup"><span data-stu-id="36cb4-118">Transformations</span></span>  
 <span data-ttu-id="36cb4-119">A<xref:System.Drawing.Graphics>物件會維護套用至所有項目所繪製的兩個轉換 （全局和頁面）<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="36cb4-119">A <xref:System.Drawing.Graphics> object maintains two transformations (world and page) that are applied to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="36cb4-120">任何仿射轉換可以儲存在全局轉換。</span><span class="sxs-lookup"><span data-stu-id="36cb4-120">Any affine transformation can be stored in the world transformation.</span></span> <span data-ttu-id="36cb4-121">仿射轉換包括縮放、 旋轉、 反射、 扭曲，和轉譯。</span><span class="sxs-lookup"><span data-stu-id="36cb4-121">Affine transformations include scaling, rotating, reflecting, skewing, and translating.</span></span> <span data-ttu-id="36cb4-122">可用於頁面轉換，調整和變更單位 （例如，像素為單位為英吋）。</span><span class="sxs-lookup"><span data-stu-id="36cb4-122">The page transformation can be used for scaling and for changing units (for example, pixels to inches).</span></span> <span data-ttu-id="36cb4-123">如需詳細資訊，請參閱 <<c0> [ 座標系統和轉換](coordinate-systems-and-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="36cb4-123">For more information, see [Coordinate Systems and Transformations](coordinate-systems-and-transformations.md).</span></span>  
  
 <span data-ttu-id="36cb4-124">下列範例會設定全局和頁面轉換<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="36cb4-124">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="36cb4-125">全局轉換設定為 30 度的旋轉。</span><span class="sxs-lookup"><span data-stu-id="36cb4-125">The world transformation is set to a 30-degree rotation.</span></span> <span data-ttu-id="36cb4-126">「 頁面 」 轉換會設定以便座標傳遞給第二個<xref:System.Drawing.Graphics.DrawEllipse%2A>會被視為公釐為單位，而不是像素為單位。</span><span class="sxs-lookup"><span data-stu-id="36cb4-126">The page transformation is set so that the coordinates passed to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> will be treated as millimeters instead of pixels.</span></span> <span data-ttu-id="36cb4-127">程式碼會建立兩個相同呼叫<xref:System.Drawing.Graphics.DrawEllipse%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="36cb4-127">The code makes two identical calls to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method.</span></span> <span data-ttu-id="36cb4-128">全局轉換會套用至第一個<xref:System.Drawing.Graphics.DrawEllipse%2A>呼叫時，並 （全局和頁面） 這兩種轉換會套用至第二個<xref:System.Drawing.Graphics.DrawEllipse%2A>呼叫。</span><span class="sxs-lookup"><span data-stu-id="36cb4-128">The world transformation is applied to the first <xref:System.Drawing.Graphics.DrawEllipse%2A> call, and both transformations (world and page) are applied to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> call.</span></span>  
  
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
  
 <span data-ttu-id="36cb4-129">下圖顯示兩個橢圓形。</span><span class="sxs-lookup"><span data-stu-id="36cb4-129">The following illustration shows the two ellipses.</span></span> <span data-ttu-id="36cb4-130">請注意，30 度旋轉的座標系統 （用戶端區域的左上角） 原點，不需橢圓形的中心。</span><span class="sxs-lookup"><span data-stu-id="36cb4-130">Note that the 30-degree rotation is about the origin of the coordinate system (upper-left corner of the client area), not about the centers of the ellipses.</span></span> <span data-ttu-id="36cb4-131">也請注意畫筆寬度為 1，表示第二個橢圓形的 1 個像素的第一個橢圓形和 1 公釐。</span><span class="sxs-lookup"><span data-stu-id="36cb4-131">Also note that the pen width of 1 means 1 pixel for the first ellipse and 1 millimeter for the second ellipse.</span></span>  
  
 <span data-ttu-id="36cb4-132">![橢圓形](./media/csgraphicsascon1.png "csgraphicsascon1")</span><span class="sxs-lookup"><span data-stu-id="36cb4-132">![Ovals](./media/csgraphicsascon1.png "csgraphicsascon1")</span></span>  
  
### <a name="clipping-region"></a><span data-ttu-id="36cb4-133">裁剪區域</span><span class="sxs-lookup"><span data-stu-id="36cb4-133">Clipping Region</span></span>  
 <span data-ttu-id="36cb4-134">A<xref:System.Drawing.Graphics>物件會維護適用於所有的項目所繪製的裁剪區域<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="36cb4-134">A <xref:System.Drawing.Graphics> object maintains a clipping region that applies to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="36cb4-135">您可以藉由呼叫設定的裁剪區域<xref:System.Drawing.Graphics.SetClip%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="36cb4-135">You can set the clipping region by calling the <xref:System.Drawing.Graphics.SetClip%2A> method.</span></span>  
  
 <span data-ttu-id="36cb4-136">下列範例會建立由形成聯集兩個矩形的加號形狀的區域。</span><span class="sxs-lookup"><span data-stu-id="36cb4-136">The following example creates a plus-shaped region by forming the union of two rectangles.</span></span> <span data-ttu-id="36cb4-137">該區域會指定為的裁剪區域<xref:System.Drawing.Graphics>物件。</span><span class="sxs-lookup"><span data-stu-id="36cb4-137">That region is designated as the clipping region of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="36cb4-138">然後程式碼繪製的裁剪區域的內部類型受限於的兩行。</span><span class="sxs-lookup"><span data-stu-id="36cb4-138">Then the code draws two lines that are restricted to the interior of the clipping region.</span></span>  
  
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
  
 <span data-ttu-id="36cb4-139">下圖顯示裁剪的線條。</span><span class="sxs-lookup"><span data-stu-id="36cb4-139">The following illustration shows the clipped lines.</span></span>  
  
 <span data-ttu-id="36cb4-140">![有限的裁剪區域](./media/graphicsascon2.png "graphicsascon2")</span><span class="sxs-lookup"><span data-stu-id="36cb4-140">![Limited Clip Region](./media/graphicsascon2.png "graphicsascon2")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36cb4-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36cb4-141">See also</span></span>
- [<span data-ttu-id="36cb4-142">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="36cb4-142">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="36cb4-143">使用巢狀圖形容器</span><span class="sxs-lookup"><span data-stu-id="36cb4-143">Using Nested Graphics Containers</span></span>](using-nested-graphics-containers.md)
