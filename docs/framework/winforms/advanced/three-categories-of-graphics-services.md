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
ms.openlocfilehash: e5ab99095bbe69eb05f16e2f1a628004c7777c97
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64654515"
---
# <a name="three-categories-of-graphics-services"></a><span data-ttu-id="2f1aa-102">圖形服務的三個分類</span><span class="sxs-lookup"><span data-stu-id="2f1aa-102">Three Categories of Graphics Services</span></span>
<span data-ttu-id="2f1aa-103">在 Windows Form 中的圖形供應項目可分為下列三個廣泛的類別：</span><span class="sxs-lookup"><span data-stu-id="2f1aa-103">The graphics offerings in Windows Forms fall into the following three broad categories:</span></span>  
  
- <span data-ttu-id="2f1aa-104">二維 (2-d) 向量圖形</span><span class="sxs-lookup"><span data-stu-id="2f1aa-104">Two-dimensional (2-D) vector graphics</span></span>  
  
- <span data-ttu-id="2f1aa-105">映像</span><span class="sxs-lookup"><span data-stu-id="2f1aa-105">Imaging</span></span>  
  
- <span data-ttu-id="2f1aa-106">印刷樣式</span><span class="sxs-lookup"><span data-stu-id="2f1aa-106">Typography</span></span>  
  
## <a name="2-d-vector-graphics"></a><span data-ttu-id="2f1aa-107">2d 向量圖形</span><span class="sxs-lookup"><span data-stu-id="2f1aa-107">2-D Vector Graphics</span></span>  
 <span data-ttu-id="2f1aa-108">二維向量圖形是基本型別;例如線條、 曲線和圖形;由組點座標系統上所指定。</span><span class="sxs-lookup"><span data-stu-id="2f1aa-108">Two-dimensional vector graphics are primitives; such as lines, curves, and figures; that are specified by sets of points on a coordinate system.</span></span> <span data-ttu-id="2f1aa-109">比方說，一條直線由其兩個端點，並讓其左上角，以及提供其寬度和高度的數字的一組的位置點所指定的矩形。</span><span class="sxs-lookup"><span data-stu-id="2f1aa-109">For example, a straight line is specified by its two endpoints, and a rectangle is specified by a point giving the location of its upper-left corner and a pair of numbers giving its width and height.</span></span> <span data-ttu-id="2f1aa-110">連接的直線，線條的點陣列所指定簡單的路徑。</span><span class="sxs-lookup"><span data-stu-id="2f1aa-110">A simple path is specified by an array of points that are connected by straight lines.</span></span> <span data-ttu-id="2f1aa-111">貝茲曲線是由四個控制點的複雜的曲線。</span><span class="sxs-lookup"><span data-stu-id="2f1aa-111">A Bézier spline is a sophisticated curve specified by four control points.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="2f1aa-112">提供類別和儲存的基本項目本身的相關資訊的結構，用以儲存資訊有關如何將繪製基本項目和實際進行繪製的類別。</span><span class="sxs-lookup"><span data-stu-id="2f1aa-112">provides classes and structures that store information about the primitives themselves, classes that store information about how the primitives will be drawn, and classes that actually do the drawing.</span></span> <span data-ttu-id="2f1aa-113">比方說，<xref:System.Drawing.Rectangle>結構會儲存的位置和大小的矩形<xref:System.Drawing.Pen>類別會儲存有關線條色彩、 線條寬度和線條樣式，和<xref:System.Drawing.Graphics>類別有方法來繪製線條、 矩形、 路徑和其他數字。</span><span class="sxs-lookup"><span data-stu-id="2f1aa-113">For example, the <xref:System.Drawing.Rectangle> structure stores the location and size of a rectangle; the <xref:System.Drawing.Pen> class stores information about line color, line width, and line style; and the <xref:System.Drawing.Graphics> class has methods for drawing lines, rectangles, paths, and other figures.</span></span> <span data-ttu-id="2f1aa-114">有數個也<xref:System.Drawing.Brush>儲存方式的相關資訊的類別會關閉數字，而且路徑會填滿色彩或圖樣。</span><span class="sxs-lookup"><span data-stu-id="2f1aa-114">There are also several <xref:System.Drawing.Brush> classes that store information about how closed figures and paths will be filled with colors or patterns.</span></span>  
  
 <span data-ttu-id="2f1aa-115">您可以記錄向量映像，也就是一連串的圖形命令，在中繼檔中。</span><span class="sxs-lookup"><span data-stu-id="2f1aa-115">You can record a vector image, which is a sequence of graphics commands, in a metafile.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="2f1aa-116">提供<xref:System.Drawing.Imaging.Metafile>記錄、 顯示及儲存的中繼檔的類別。</span><span class="sxs-lookup"><span data-stu-id="2f1aa-116">provides the <xref:System.Drawing.Imaging.Metafile> class for recording, displaying, and saving metafiles.</span></span> <span data-ttu-id="2f1aa-117">具有<xref:System.Drawing.Imaging.MetafileHeader>和<xref:System.Drawing.Imaging.MetaHeader>類別，您可以檢查儲存在中繼檔標頭中的資料。</span><span class="sxs-lookup"><span data-stu-id="2f1aa-117">With the <xref:System.Drawing.Imaging.MetafileHeader> and <xref:System.Drawing.Imaging.MetaHeader> classes, you can inspect the data stored in a metafile header.</span></span>  
  
## <a name="imaging"></a><span data-ttu-id="2f1aa-118">映像</span><span class="sxs-lookup"><span data-stu-id="2f1aa-118">Imaging</span></span>  
 <span data-ttu-id="2f1aa-119">某些類型的圖片會很難或無法以顯示與向量圖形的技術。</span><span class="sxs-lookup"><span data-stu-id="2f1aa-119">Certain kinds of pictures are difficult or impossible to display with the techniques of vector graphics.</span></span> <span data-ttu-id="2f1aa-120">比方說，在工具列按鈕上的圖片，會顯示為圖示的圖片很難進行指定為直線和曲線的集合。</span><span class="sxs-lookup"><span data-stu-id="2f1aa-120">For example, the pictures on toolbar buttons and the pictures that appear as icons are difficult to specify as collections of lines and curves.</span></span> <span data-ttu-id="2f1aa-121">太過擁擠的棒球最高解析度數位相片是更難以建立與向量技巧。</span><span class="sxs-lookup"><span data-stu-id="2f1aa-121">A high-resolution digital photograph of a crowded baseball stadium is even more difficult to create with vector techniques.</span></span> <span data-ttu-id="2f1aa-122">此類型的映像會儲存為點陣圖，也就是數字，代表在螢幕上的每個點的色彩的陣列。</span><span class="sxs-lookup"><span data-stu-id="2f1aa-122">Images of this type are stored as bitmaps, which are arrays of numbers that represent the colors of individual dots on the screen.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="2f1aa-123">提供<xref:System.Drawing.Bitmap>以便顯示、 管理，以及將點陣圖儲存的類別。</span><span class="sxs-lookup"><span data-stu-id="2f1aa-123">provides the <xref:System.Drawing.Bitmap> class for displaying, manipulating, and saving bitmaps.</span></span>  
  
## <a name="typography"></a><span data-ttu-id="2f1aa-124">印刷樣式</span><span class="sxs-lookup"><span data-stu-id="2f1aa-124">Typography</span></span>  
 <span data-ttu-id="2f1aa-125">印刷樣式是文字的以各種不同的字型、 大小和樣式的顯示。</span><span class="sxs-lookup"><span data-stu-id="2f1aa-125">Typography is the display of text in a variety of fonts, sizes, and styles.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="2f1aa-126">可廣泛支援這項複雜工作。</span><span class="sxs-lookup"><span data-stu-id="2f1aa-126">provides extensive support for this complex task.</span></span> <span data-ttu-id="2f1aa-127">其中一項新功能[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]子像素反鋸齒功能，提供文字轉譯 LCD 螢幕較平滑的外觀。</span><span class="sxs-lookup"><span data-stu-id="2f1aa-127">One of the new features in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is subpixel antialiasing, which gives text rendered on an LCD screen a smoother appearance.</span></span>  
  
 <span data-ttu-id="2f1aa-128">此外，Windows Forms 會提供選項來繪製的文字[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]中的功能及其<xref:System.Windows.Forms.TextRenderer>類別。</span><span class="sxs-lookup"><span data-stu-id="2f1aa-128">In addition, Windows Forms offers the option to draw text with [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] capabilities in its <xref:System.Windows.Forms.TextRenderer> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f1aa-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f1aa-129">See also</span></span>

- [<span data-ttu-id="2f1aa-130">圖形概觀</span><span class="sxs-lookup"><span data-stu-id="2f1aa-130">Graphics Overview</span></span>](graphics-overview-windows-forms.md)
- [<span data-ttu-id="2f1aa-131">關於 GDI+ Managed 程式碼</span><span class="sxs-lookup"><span data-stu-id="2f1aa-131">About GDI+ Managed Code</span></span>](about-gdi-managed-code.md)
- [<span data-ttu-id="2f1aa-132">使用 Managed 圖形類別</span><span class="sxs-lookup"><span data-stu-id="2f1aa-132">Using Managed Graphics Classes</span></span>](using-managed-graphics-classes.md)
