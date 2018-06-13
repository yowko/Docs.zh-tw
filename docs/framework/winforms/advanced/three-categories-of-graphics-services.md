---
title: 圖形服務的三個分類
ms.date: 03/30/2017
helpviewer_keywords:
- imaging
- graphics [Windows Forms], categories
- 2-D vector graphics
- vector graphics
- typography
ms.assetid: 068c0ef3-f6ee-4d58-a7b6-eb2531ead408
ms.openlocfilehash: 5621a2c0bba2e922e62006feba9ca0381181c780
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525043"
---
# <a name="three-categories-of-graphics-services"></a><span data-ttu-id="904f4-102">圖形服務的三個分類</span><span class="sxs-lookup"><span data-stu-id="904f4-102">Three Categories of Graphics Services</span></span>
<span data-ttu-id="904f4-103">在 Windows Form 中的圖形供應項目可分為下列三個主要類別：</span><span class="sxs-lookup"><span data-stu-id="904f4-103">The graphics offerings in Windows Forms fall into the following three broad categories:</span></span>  
  
-   <span data-ttu-id="904f4-104">二維 (2d) 向量圖形</span><span class="sxs-lookup"><span data-stu-id="904f4-104">Two-dimensional (2-D) vector graphics</span></span>  
  
-   <span data-ttu-id="904f4-105">映像</span><span class="sxs-lookup"><span data-stu-id="904f4-105">Imaging</span></span>  
  
-   <span data-ttu-id="904f4-106">印刷樣式</span><span class="sxs-lookup"><span data-stu-id="904f4-106">Typography</span></span>  
  
## <a name="2-d-vector-graphics"></a><span data-ttu-id="904f4-107">2d 向量圖形</span><span class="sxs-lookup"><span data-stu-id="904f4-107">2-D Vector Graphics</span></span>  
 <span data-ttu-id="904f4-108">2d 向量圖形是基本型別。例如線條、 曲線和數字。所指定的座標系統上的點集合。</span><span class="sxs-lookup"><span data-stu-id="904f4-108">Two-dimensional vector graphics are primitives; such as lines, curves, and figures; that are specified by sets of points on a coordinate system.</span></span> <span data-ttu-id="904f4-109">比方說，直線由兩個端點，並提供其左上角和提供其寬度和高度的數字組的位置點所指定的矩形。</span><span class="sxs-lookup"><span data-stu-id="904f4-109">For example, a straight line is specified by its two endpoints, and a rectangle is specified by a point giving the location of its upper-left corner and a pair of numbers giving its width and height.</span></span> <span data-ttu-id="904f4-110">連接的直線的點陣列所指定簡單的路徑。</span><span class="sxs-lookup"><span data-stu-id="904f4-110">A simple path is specified by an array of points that are connected by straight lines.</span></span> <span data-ttu-id="904f4-111">貝茲曲線是由四個控點的高性能的曲線。</span><span class="sxs-lookup"><span data-stu-id="904f4-111">A Bézier spline is a sophisticated curve specified by four control points.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="904f4-112"> 提供類別和儲存自己的基本類型的相關資訊的結構、 類別可儲存資訊有關如何將繪製基本項目，以及實際進行繪製的類別。</span><span class="sxs-lookup"><span data-stu-id="904f4-112"> provides classes and structures that store information about the primitives themselves, classes that store information about how the primitives will be drawn, and classes that actually do the drawing.</span></span> <span data-ttu-id="904f4-113">比方說，<xref:System.Drawing.Rectangle>結構會儲存的位置和大小的矩形;<xref:System.Drawing.Pen>類別會儲存有關線條色彩、 線條寬度和線條樣式，而<xref:System.Drawing.Graphics>類別具有繪製線條、 矩形、 路徑、 方法和其他幾張圖。</span><span class="sxs-lookup"><span data-stu-id="904f4-113">For example, the <xref:System.Drawing.Rectangle> structure stores the location and size of a rectangle; the <xref:System.Drawing.Pen> class stores information about line color, line width, and line style; and the <xref:System.Drawing.Graphics> class has methods for drawing lines, rectangles, paths, and other figures.</span></span> <span data-ttu-id="904f4-114">有數個也<xref:System.Drawing.Brush>儲存方式的相關資訊的類別關閉圖表，而且路徑會填滿色彩或圖樣。</span><span class="sxs-lookup"><span data-stu-id="904f4-114">There are also several <xref:System.Drawing.Brush> classes that store information about how closed figures and paths will be filled with colors or patterns.</span></span>  
  
 <span data-ttu-id="904f4-115">您可以記錄是一串圖形命令，以向量映像中繼檔中。</span><span class="sxs-lookup"><span data-stu-id="904f4-115">You can record a vector image, which is a sequence of graphics commands, in a metafile.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="904f4-116"> 提供<xref:System.Drawing.Imaging.Metafile>錄製、 顯示和儲存中繼檔的類別。</span><span class="sxs-lookup"><span data-stu-id="904f4-116"> provides the <xref:System.Drawing.Imaging.Metafile> class for recording, displaying, and saving metafiles.</span></span> <span data-ttu-id="904f4-117">與<xref:System.Drawing.Imaging.MetafileHeader>和<xref:System.Drawing.Imaging.MetaHeader>類別，您可以檢查儲存在中繼檔標頭中的資料。</span><span class="sxs-lookup"><span data-stu-id="904f4-117">With the <xref:System.Drawing.Imaging.MetafileHeader> and <xref:System.Drawing.Imaging.MetaHeader> classes, you can inspect the data stored in a metafile header.</span></span>  
  
## <a name="imaging"></a><span data-ttu-id="904f4-118">映像</span><span class="sxs-lookup"><span data-stu-id="904f4-118">Imaging</span></span>  
 <span data-ttu-id="904f4-119">某些類型的圖片會很難或無法與向量圖形的技術一起顯示。</span><span class="sxs-lookup"><span data-stu-id="904f4-119">Certain kinds of pictures are difficult or impossible to display with the techniques of vector graphics.</span></span> <span data-ttu-id="904f4-120">比方說，在工具列按鈕上的圖片，會顯示為圖示的圖片難以指定做為集合的直線和曲線。</span><span class="sxs-lookup"><span data-stu-id="904f4-120">For example, the pictures on toolbar buttons and the pictures that appear as icons are difficult to specify as collections of lines and curves.</span></span> <span data-ttu-id="904f4-121">高解析度數位擁擠的棒球場上所拍攝的相片是更難以建立與向量技巧。</span><span class="sxs-lookup"><span data-stu-id="904f4-121">A high-resolution digital photograph of a crowded baseball stadium is even more difficult to create with vector techniques.</span></span> <span data-ttu-id="904f4-122">此類型的影像會儲存為點陣圖，也就是數字，代表在螢幕上的每個點的色彩的陣列。</span><span class="sxs-lookup"><span data-stu-id="904f4-122">Images of this type are stored as bitmaps, which are arrays of numbers that represent the colors of individual dots on the screen.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="904f4-123"> 提供<xref:System.Drawing.Bitmap>以便顯示、 管理，以及將點陣圖另存的類別。</span><span class="sxs-lookup"><span data-stu-id="904f4-123"> provides the <xref:System.Drawing.Bitmap> class for displaying, manipulating, and saving bitmaps.</span></span>  
  
## <a name="typography"></a><span data-ttu-id="904f4-124">印刷樣式</span><span class="sxs-lookup"><span data-stu-id="904f4-124">Typography</span></span>  
 <span data-ttu-id="904f4-125">印刷樣式是文字的各種不同的字型、 大小及樣式中顯示。</span><span class="sxs-lookup"><span data-stu-id="904f4-125">Typography is the display of text in a variety of fonts, sizes, and styles.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="904f4-126"> 這個複雜的工作，提供更詳盡的支援。</span><span class="sxs-lookup"><span data-stu-id="904f4-126"> provides extensive support for this complex task.</span></span> <span data-ttu-id="904f4-127">中的新功能的其中一個[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]素反鋸齒功能，可讓文字呈現 LCD 螢幕更順暢的外觀。</span><span class="sxs-lookup"><span data-stu-id="904f4-127">One of the new features in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is subpixel antialiasing, which gives text rendered on an LCD screen a smoother appearance.</span></span>  
  
 <span data-ttu-id="904f4-128">此外，Windows Form 提供繪製文字的選項[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]中的功能及其<xref:System.Windows.Forms.TextRenderer>類別。</span><span class="sxs-lookup"><span data-stu-id="904f4-128">In addition, Windows Forms offers the option to draw text with [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] capabilities in its <xref:System.Windows.Forms.TextRenderer> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="904f4-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="904f4-129">See Also</span></span>  
 [<span data-ttu-id="904f4-130">圖形概觀</span><span class="sxs-lookup"><span data-stu-id="904f4-130">Graphics Overview</span></span>](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 [<span data-ttu-id="904f4-131">關於 GDI+ Managed 程式碼</span><span class="sxs-lookup"><span data-stu-id="904f4-131">About GDI+ Managed Code</span></span>](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 [<span data-ttu-id="904f4-132">使用 Managed 圖形類別</span><span class="sxs-lookup"><span data-stu-id="904f4-132">Using Managed Graphics Classes</span></span>](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
