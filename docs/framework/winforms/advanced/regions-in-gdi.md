---
title: GDI+ 中的區域
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, regions
- drawing [Windows Forms], regions
- regions
ms.assetid: 52184f9b-16dd-4bbd-85be-029112644ceb
ms.openlocfilehash: ae4931a464421639112c8f369bd27a45550fe7f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708266"
---
# <a name="regions-in-gdi"></a><span data-ttu-id="f1763-102">GDI+ 中的區域</span><span class="sxs-lookup"><span data-stu-id="f1763-102">Regions in GDI+</span></span>
<span data-ttu-id="f1763-103">區域是輸出裝置的顯示區域的一部分。</span><span class="sxs-lookup"><span data-stu-id="f1763-103">A region is a portion of the display area of an output device.</span></span> <span data-ttu-id="f1763-104">區域可以是簡單 （一個矩形） 或複雜 （多邊形和封閉型曲線的組合）。</span><span class="sxs-lookup"><span data-stu-id="f1763-104">Regions can be simple (a single rectangle) or complex (a combination of polygons and closed curves).</span></span> <span data-ttu-id="f1763-105">下圖顯示兩個區域： 其中一個矩形，從建構和其他建構從路徑。</span><span class="sxs-lookup"><span data-stu-id="f1763-105">The following illustration shows two regions: one constructed from a rectangle, and the other constructed from a path.</span></span>  
  
 <span data-ttu-id="f1763-106">![Regions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art27.gif "AboutGdip02_Art27")</span><span class="sxs-lookup"><span data-stu-id="f1763-106">![Regions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art27.gif "AboutGdip02_Art27")</span></span>  
  
## <a name="using-regions"></a><span data-ttu-id="f1763-107">使用區域</span><span class="sxs-lookup"><span data-stu-id="f1763-107">Using Regions</span></span>  
 <span data-ttu-id="f1763-108">通常用於裁剪區域，和點擊測試。</span><span class="sxs-lookup"><span data-stu-id="f1763-108">Regions are often used for clipping and hit testing.</span></span> <span data-ttu-id="f1763-109">裁剪是指限制到特定區域的顯示區域，通常需要更新的部分繪圖。</span><span class="sxs-lookup"><span data-stu-id="f1763-109">Clipping involves restricting drawing to a certain region of the display area, usually the portion that needs to be updated.</span></span> <span data-ttu-id="f1763-110">點擊測試，包括檢查並判斷游標是否在特定區域的畫面在按下滑鼠按鈕時。</span><span class="sxs-lookup"><span data-stu-id="f1763-110">Hit testing involves checking to determine whether the cursor is in a certain region of the screen when a mouse button is pressed.</span></span>  
  
 <span data-ttu-id="f1763-111">您可以建構從矩形或路徑的區域。</span><span class="sxs-lookup"><span data-stu-id="f1763-111">You can construct a region from a rectangle or a path.</span></span> <span data-ttu-id="f1763-112">您也可以藉由結合現有的區域建立複雜的區域。</span><span class="sxs-lookup"><span data-stu-id="f1763-112">You can also create complex regions by combining existing regions.</span></span> <span data-ttu-id="f1763-113"><xref:System.Drawing.Region>類別提供下列方法來結合區域： <xref:System.Drawing.Region.Intersect%2A>， <xref:System.Drawing.Region.Union%2A>， <xref:System.Drawing.Region.Xor%2A>， <xref:System.Drawing.Region.Exclude%2A>，和<xref:System.Drawing.Region.Complement%2A>。</span><span class="sxs-lookup"><span data-stu-id="f1763-113">The <xref:System.Drawing.Region> class provides the following methods for combining regions: <xref:System.Drawing.Region.Intersect%2A>, <xref:System.Drawing.Region.Union%2A>, <xref:System.Drawing.Region.Xor%2A>, <xref:System.Drawing.Region.Exclude%2A>, and <xref:System.Drawing.Region.Complement%2A>.</span></span>  
  
 <span data-ttu-id="f1763-114">兩個區域的交集是屬於這兩個區域的所有點的集合。</span><span class="sxs-lookup"><span data-stu-id="f1763-114">The intersection of two regions is the set of all points belonging to both regions.</span></span> <span data-ttu-id="f1763-115">聯集是一組屬於其中一個或兩個區域的所有點。</span><span class="sxs-lookup"><span data-stu-id="f1763-115">The union is the set of all points belonging to one or the other or both regions.</span></span> <span data-ttu-id="f1763-116">區域的補數是一組不在區域中的所有點。</span><span class="sxs-lookup"><span data-stu-id="f1763-116">The complement of a region is the set of all points that are not in the region.</span></span> <span data-ttu-id="f1763-117">下圖顯示在上圖中顯示的兩個區域的聯集和交集。</span><span class="sxs-lookup"><span data-stu-id="f1763-117">The following illustration shows the intersection and union of the two regions shown in the preceding illustration.</span></span>  
  
 <span data-ttu-id="f1763-118">![Regions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art28.gif "AboutGdip02_Art28")</span><span class="sxs-lookup"><span data-stu-id="f1763-118">![Regions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art28.gif "AboutGdip02_Art28")</span></span>  
  
 <span data-ttu-id="f1763-119"><xref:System.Drawing.Region.Xor%2A>方法，套用至配對的區域，會產生包含隸屬於一個區域或其他的但非兩者的所有點的區域。</span><span class="sxs-lookup"><span data-stu-id="f1763-119">The <xref:System.Drawing.Region.Xor%2A> method, applied to a pair of regions, produces a region that contains all points that belong to one region or the other, but not both.</span></span> <span data-ttu-id="f1763-120"><xref:System.Drawing.Region.Exclude%2A>方法，套用至配對的區域，會產生包含中的第一個區域不在第二個區域中的所有點的區域。</span><span class="sxs-lookup"><span data-stu-id="f1763-120">The <xref:System.Drawing.Region.Exclude%2A> method, applied to a pair of regions, produces a region that contains all points in the first region that are not in the second region.</span></span> <span data-ttu-id="f1763-121">下圖顯示將套用所得到的區域<xref:System.Drawing.Region.Xor%2A>和<xref:System.Drawing.Region.Exclude%2A>方法來顯示位於本主題開頭的兩個區域。</span><span class="sxs-lookup"><span data-stu-id="f1763-121">The following illustration shows the regions that result from applying the <xref:System.Drawing.Region.Xor%2A> and <xref:System.Drawing.Region.Exclude%2A> methods to the two regions shown at the beginning of this topic.</span></span>  
  
 <span data-ttu-id="f1763-122">![Regions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art29.gif "AboutGdip02_Art29")</span><span class="sxs-lookup"><span data-stu-id="f1763-122">![Regions](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art29.gif "AboutGdip02_Art29")</span></span>  
  
 <span data-ttu-id="f1763-123">若要填滿的區域，您需要<xref:System.Drawing.Graphics>物件，<xref:System.Drawing.Brush>物件，和<xref:System.Drawing.Region>物件。</span><span class="sxs-lookup"><span data-stu-id="f1763-123">To fill a region, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Brush> object, and a <xref:System.Drawing.Region> object.</span></span> <span data-ttu-id="f1763-124"><xref:System.Drawing.Graphics>物件會提供<xref:System.Drawing.Graphics.FillRegion%2A>方法，而<xref:System.Drawing.Brush>物件會儲存屬性的 fill 設定，例如色彩或圖樣。</span><span class="sxs-lookup"><span data-stu-id="f1763-124">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.FillRegion%2A> method, and the <xref:System.Drawing.Brush> object stores attributes of the fill, such as color or pattern.</span></span> <span data-ttu-id="f1763-125">下列範例會填滿區域，以使用純色。</span><span class="sxs-lookup"><span data-stu-id="f1763-125">The following example fills a region with a solid color.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#61)]
 [!code-vb[LinesCurvesAndShapes#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#61)]  
  
## <a name="see-also"></a><span data-ttu-id="f1763-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1763-126">See also</span></span>
- <xref:System.Drawing.Region?displayProperty=nameWithType>
- [<span data-ttu-id="f1763-127">線條、曲線和形狀</span><span class="sxs-lookup"><span data-stu-id="f1763-127">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)
- [<span data-ttu-id="f1763-128">使用區域</span><span class="sxs-lookup"><span data-stu-id="f1763-128">Using Regions</span></span>](../../../../docs/framework/winforms/advanced/using-regions.md)
