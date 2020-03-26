---
title: 圖形服務的三個分類
ms.date: 03/30/2017
helpviewer_keywords:
- imaging
- graphics [Windows Forms], categories
- 2D vector graphics
- vector graphics
- typography
ms.assetid: 068c0ef3-f6ee-4d58-a7b6-eb2531ead408
ms.openlocfilehash: fa7391ef0f7170ddb9d9d24aa5a1a03635bf46e0
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291731"
---
# <a name="three-categories-of-graphics-services"></a><span data-ttu-id="e110f-102">圖形服務的三個分類</span><span class="sxs-lookup"><span data-stu-id="e110f-102">Three Categories of Graphics Services</span></span>
<span data-ttu-id="e110f-103">Windows 表單中的圖形產品分為以下三大類：</span><span class="sxs-lookup"><span data-stu-id="e110f-103">The graphics offerings in Windows Forms fall into the following three broad categories:</span></span>  
  
- <span data-ttu-id="e110f-104">二維 （二-D） 向量圖形</span><span class="sxs-lookup"><span data-stu-id="e110f-104">Two-dimensional (2-D) vector graphics</span></span>  
  
- <span data-ttu-id="e110f-105">建立映像</span><span class="sxs-lookup"><span data-stu-id="e110f-105">Imaging</span></span>  
  
- <span data-ttu-id="e110f-106">印刷樣式</span><span class="sxs-lookup"><span data-stu-id="e110f-106">Typography</span></span>  
  
## <a name="2d-vector-graphics"></a><span data-ttu-id="e110f-107">2D 向量圖形</span><span class="sxs-lookup"><span data-stu-id="e110f-107">2D Vector Graphics</span></span>  
 <span data-ttu-id="e110f-108">二維向量圖形（如直線、曲線和圖形）是由坐標系上的點集指定的基元。</span><span class="sxs-lookup"><span data-stu-id="e110f-108">Two-dimensional vector graphics, such as lines, curves, and figures, are primitives that are specified by sets of points on a coordinate system.</span></span> <span data-ttu-id="e110f-109">例如，直線由其兩個端點指定，矩形由一個點指定，該點給出其左上角的位置，以及一對表示其寬度和高度的數位。</span><span class="sxs-lookup"><span data-stu-id="e110f-109">For example, a straight line is specified by its two endpoints, and a rectangle is specified by a point giving the location of its upper-left corner and a pair of numbers giving its width and height.</span></span> <span data-ttu-id="e110f-110">簡單路徑由由直線連接的點陣列指定。</span><span class="sxs-lookup"><span data-stu-id="e110f-110">A simple path is specified by an array of points that are connected by straight lines.</span></span> <span data-ttu-id="e110f-111">貝塞爾樣條線是由四個控制點指定的複雜曲線。</span><span class="sxs-lookup"><span data-stu-id="e110f-111">A Bézier spline is a sophisticated curve specified by four control points.</span></span>  
  
 <span data-ttu-id="e110f-112">GDI+ 提供類和結構，這些類和結構存儲有關基元本身的資訊、存儲有關基元繪製方式的資訊的類以及實際執行繪圖的類。</span><span class="sxs-lookup"><span data-stu-id="e110f-112">GDI+ provides classes and structures that store information about the primitives themselves, classes that store information about how the primitives will be drawn, and classes that actually do the drawing.</span></span> <span data-ttu-id="e110f-113">例如，結構存儲<xref:System.Drawing.Rectangle>矩形的位置和大小;例如，該結構存儲矩形的位置和大小。類<xref:System.Drawing.Pen>存儲有關線顏色、線寬和線樣式的資訊;<xref:System.Drawing.Graphics>類具有繪製線條、矩形、路徑和其他圖形的方法。</span><span class="sxs-lookup"><span data-stu-id="e110f-113">For example, the <xref:System.Drawing.Rectangle> structure stores the location and size of a rectangle; the <xref:System.Drawing.Pen> class stores information about line color, line width, and line style; and the <xref:System.Drawing.Graphics> class has methods for drawing lines, rectangles, paths, and other figures.</span></span> <span data-ttu-id="e110f-114">還有幾個<xref:System.Drawing.Brush>類存儲有關如何用顏色或圖案填充閉合的數位和路徑的資訊。</span><span class="sxs-lookup"><span data-stu-id="e110f-114">There are also several <xref:System.Drawing.Brush> classes that store information about how closed figures and paths will be filled with colors or patterns.</span></span>  
  
 <span data-ttu-id="e110f-115">您可以在中繼檔中記錄向量圖像（即圖形命令序列）。</span><span class="sxs-lookup"><span data-stu-id="e110f-115">You can record a vector image, which is a sequence of graphics commands, in a metafile.</span></span> <span data-ttu-id="e110f-116">GDI+ 提供<xref:System.Drawing.Imaging.Metafile>用於錄製、顯示和保存中繼檔的類。</span><span class="sxs-lookup"><span data-stu-id="e110f-116">GDI+ provides the <xref:System.Drawing.Imaging.Metafile> class for recording, displaying, and saving metafiles.</span></span> <span data-ttu-id="e110f-117">使用<xref:System.Drawing.Imaging.MetafileHeader>和<xref:System.Drawing.Imaging.MetaHeader>類，可以檢查存儲在中繼檔標頭中的資料。</span><span class="sxs-lookup"><span data-stu-id="e110f-117">With the <xref:System.Drawing.Imaging.MetafileHeader> and <xref:System.Drawing.Imaging.MetaHeader> classes, you can inspect the data stored in a metafile header.</span></span>  
  
## <a name="imaging"></a><span data-ttu-id="e110f-118">建立映像</span><span class="sxs-lookup"><span data-stu-id="e110f-118">Imaging</span></span>  
 <span data-ttu-id="e110f-119">使用向量圖形技術很難或不可能顯示某些類型的圖片。</span><span class="sxs-lookup"><span data-stu-id="e110f-119">Certain kinds of pictures are difficult or impossible to display with the techniques of vector graphics.</span></span> <span data-ttu-id="e110f-120">例如，工具列按鈕上的圖片和顯示為圖示的圖片很難指定為線條和曲線的集合。</span><span class="sxs-lookup"><span data-stu-id="e110f-120">For example, the pictures on toolbar buttons and the pictures that appear as icons are difficult to specify as collections of lines and curves.</span></span> <span data-ttu-id="e110f-121">使用向量技術，製作擁擠的棒球場的高解析度數位照片就更加困難了。</span><span class="sxs-lookup"><span data-stu-id="e110f-121">A high-resolution digital photograph of a crowded baseball stadium is even more difficult to create with vector techniques.</span></span> <span data-ttu-id="e110f-122">此類型的圖像存儲為點陣圖，即表示螢幕上單個點顏色的數位陣列。</span><span class="sxs-lookup"><span data-stu-id="e110f-122">Images of this type are stored as bitmaps, which are arrays of numbers that represent the colors of individual dots on the screen.</span></span> <span data-ttu-id="e110f-123">GDI+ 提供<xref:System.Drawing.Bitmap>用於顯示、操作和保存點陣圖的類。</span><span class="sxs-lookup"><span data-stu-id="e110f-123">GDI+ provides the <xref:System.Drawing.Bitmap> class for displaying, manipulating, and saving bitmaps.</span></span>  
  
## <a name="typography"></a><span data-ttu-id="e110f-124">印刷樣式</span><span class="sxs-lookup"><span data-stu-id="e110f-124">Typography</span></span>  
 <span data-ttu-id="e110f-125">排版是文本以各種字體、大小和樣式顯示的。</span><span class="sxs-lookup"><span data-stu-id="e110f-125">Typography is the display of text in a variety of fonts, sizes, and styles.</span></span> <span data-ttu-id="e110f-126">GDI+ 為這一複雜任務提供了廣泛的支援。</span><span class="sxs-lookup"><span data-stu-id="e110f-126">GDI+ provides extensive support for this complex task.</span></span> <span data-ttu-id="e110f-127">GDI+ 中的新功能之一是子圖元抗鋸齒，它使在 LCD 螢幕上呈現的文本外觀更平滑。</span><span class="sxs-lookup"><span data-stu-id="e110f-127">One of the new features in GDI+ is subpixel antialiasing, which gives text rendered on an LCD screen a smoother appearance.</span></span>  
  
 <span data-ttu-id="e110f-128">此外，Windows 表單還提供使用類<xref:System.Windows.Forms.TextRenderer>中的 GDI 功能繪製文本的選項。</span><span class="sxs-lookup"><span data-stu-id="e110f-128">In addition, Windows Forms offers the option to draw text with GDI capabilities in its <xref:System.Windows.Forms.TextRenderer> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e110f-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e110f-129">See also</span></span>

- [<span data-ttu-id="e110f-130">圖形概觀</span><span class="sxs-lookup"><span data-stu-id="e110f-130">Graphics Overview</span></span>](graphics-overview-windows-forms.md)
- [<span data-ttu-id="e110f-131">關於 GDI+ Managed 程式碼</span><span class="sxs-lookup"><span data-stu-id="e110f-131">About GDI+ Managed Code</span></span>](about-gdi-managed-code.md)
- [<span data-ttu-id="e110f-132">使用 Managed 圖形類別</span><span class="sxs-lookup"><span data-stu-id="e110f-132">Using Managed Graphics Classes</span></span>](using-managed-graphics-classes.md)
