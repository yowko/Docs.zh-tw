---
title: "如何：取得字型度量資訊"
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
- fonts [Windows Forms], obtaining metrics
- font metrics [Windows Forms], obtaining
ms.assetid: ff7c0616-67f7-4fa2-84ee-b8d642f2b09b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 16f1126cc75b75ae98298f5d1c58c78ff30edbb6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-obtain-font-metrics"></a><span data-ttu-id="0cf9b-102">如何：取得字型度量資訊</span><span class="sxs-lookup"><span data-stu-id="0cf9b-102">How to: Obtain Font Metrics</span></span>
<span data-ttu-id="0cf9b-103"><xref:System.Drawing.FontFamily>類別提供下列方法，擷取特定的系列樣式組合的各種度量：</span><span class="sxs-lookup"><span data-stu-id="0cf9b-103">The <xref:System.Drawing.FontFamily> class provides the following methods that retrieve various metrics for a particular family/style combination:</span></span>  
  
-   <span data-ttu-id="0cf9b-104"><xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="0cf9b-104"><xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)</span></span>  
  
-   <span data-ttu-id="0cf9b-105"><xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="0cf9b-105"><xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)</span></span>  
  
-   <span data-ttu-id="0cf9b-106"><xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="0cf9b-106"><xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)</span></span>  
  
-   <span data-ttu-id="0cf9b-107"><xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="0cf9b-107"><xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)</span></span>  
  
 <span data-ttu-id="0cf9b-108">這些方法所傳回的數字是單位為字型設計單位，因此它們都是獨立的大小和單位特定的<xref:System.Drawing.Font>物件。</span><span class="sxs-lookup"><span data-stu-id="0cf9b-108">The numbers returned by these methods are in font design units, so they are independent of the size and units of a particular <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="0cf9b-109">下圖顯示各種標準。</span><span class="sxs-lookup"><span data-stu-id="0cf9b-109">The following illustration shows the various metrics.</span></span>  
  
 <span data-ttu-id="0cf9b-110">![字型文字](../../../../docs/framework/winforms/advanced/media/fontstext7a.png "fontstext7A")</span><span class="sxs-lookup"><span data-stu-id="0cf9b-110">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext7a.png "fontstext7A")</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cf9b-111">範例</span><span class="sxs-lookup"><span data-stu-id="0cf9b-111">Example</span></span>  
 <span data-ttu-id="0cf9b-112">下列範例會顯示標準的樣式，新細明體字型家族的度量。</span><span class="sxs-lookup"><span data-stu-id="0cf9b-112">The following example displays the metrics for the regular style of the Arial font family.</span></span> <span data-ttu-id="0cf9b-113">程式碼也建立<xref:System.Drawing.Font>具有 16 個像素大小和顯示該特定的度量 （以像素為單位） （根據新細明體系列） 的物件<xref:System.Drawing.Font>物件。</span><span class="sxs-lookup"><span data-stu-id="0cf9b-113">The code also creates a <xref:System.Drawing.Font> object (based on the Arial family) with size 16 pixels and displays the metrics (in pixels) for that particular <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="0cf9b-114">下圖顯示的範例程式碼的輸出。</span><span class="sxs-lookup"><span data-stu-id="0cf9b-114">The following illustration shows the output of the example code.</span></span>  
  
 <span data-ttu-id="0cf9b-115">![字型文字](../../../../docs/framework/winforms/advanced/media/csfontstext8.png "csFontsText8")</span><span class="sxs-lookup"><span data-stu-id="0cf9b-115">![Fonts Text](../../../../docs/framework/winforms/advanced/media/csfontstext8.png "csFontsText8")</span></span>  
  
 <span data-ttu-id="0cf9b-116">請注意上圖中的前兩行。</span><span class="sxs-lookup"><span data-stu-id="0cf9b-116">Note the first two lines of output in the preceding illustration.</span></span> <span data-ttu-id="0cf9b-117"><xref:System.Drawing.Font>物件傳回的大小為 16，而<xref:System.Drawing.FontFamily>物件傳回 2048 em 高度。</span><span class="sxs-lookup"><span data-stu-id="0cf9b-117">The <xref:System.Drawing.Font> object returns a size of 16, and the <xref:System.Drawing.FontFamily> object returns an em height of 2,048.</span></span> <span data-ttu-id="0cf9b-118">這些兩個數字 （16 和 2048） 是用於轉換字型設計單位之間的單位 （在此案例的像素） 的關鍵<xref:System.Drawing.Font>物件。</span><span class="sxs-lookup"><span data-stu-id="0cf9b-118">These two numbers (16 and 2,048) are the key to converting between font design units and the units (in this case pixels) of the <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="0cf9b-119">例如，您可以將轉換 （堆疊） 設計單位為像素為單位，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0cf9b-119">For example, you can convert the ascent from design units to pixels as follows:</span></span>  
  
 <span data-ttu-id="0cf9b-120">![字型文字](../../../../docs/framework/winforms/advanced/media/fontstext9.png "FontsText9")</span><span class="sxs-lookup"><span data-stu-id="0cf9b-120">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext9.png "FontsText9")</span></span>  
  
 <span data-ttu-id="0cf9b-121">下列程式碼文字垂直定位藉由設定<xref:System.Drawing.PointF.Y%2A>資料成員<xref:System.Drawing.PointF>物件。</span><span class="sxs-lookup"><span data-stu-id="0cf9b-121">The following code positions text vertically by setting the <xref:System.Drawing.PointF.Y%2A> data member of a <xref:System.Drawing.PointF> object.</span></span> <span data-ttu-id="0cf9b-122">Y 座標會增加`font.Height`每一個新的文字行。</span><span class="sxs-lookup"><span data-stu-id="0cf9b-122">The y-coordinate is increased by `font.Height` for each new line of text.</span></span> <span data-ttu-id="0cf9b-123"><xref:System.Drawing.Font.Height%2A>屬性<xref:System.Drawing.Font>物件傳回該特定的行距 （單位為像素為單位）<xref:System.Drawing.Font>物件。</span><span class="sxs-lookup"><span data-stu-id="0cf9b-123">The <xref:System.Drawing.Font.Height%2A> property of a <xref:System.Drawing.Font> object returns the line spacing (in pixels) for that particular <xref:System.Drawing.Font> object.</span></span> <span data-ttu-id="0cf9b-124">在此範例中，數字傳回<xref:System.Drawing.Font.Height%2A>為 19。</span><span class="sxs-lookup"><span data-stu-id="0cf9b-124">In this example, the number returned by <xref:System.Drawing.Font.Height%2A> is 19.</span></span> <span data-ttu-id="0cf9b-125">請注意，這是取得行距度量資訊轉換為像素 （無條件進位到整數） 的數字相同。</span><span class="sxs-lookup"><span data-stu-id="0cf9b-125">Note that this is the same as the number (rounded up to an integer) obtained by converting the line-spacing metric to pixels.</span></span>  
  
 <span data-ttu-id="0cf9b-126">請注意，（也稱為大小或 em 大小） 其 em 高度不 （堆疊） 和深度的總和。</span><span class="sxs-lookup"><span data-stu-id="0cf9b-126">Note that the em height (also called size or em size) is not the sum of the ascent and the descent.</span></span> <span data-ttu-id="0cf9b-127">（堆疊） 和深度的總和稱為儲存格的高度。</span><span class="sxs-lookup"><span data-stu-id="0cf9b-127">The sum of the ascent and the descent is called the cell height.</span></span> <span data-ttu-id="0cf9b-128">儲存格的高度減去內部的前置字元會等於其 em 高度。</span><span class="sxs-lookup"><span data-stu-id="0cf9b-128">The cell height minus the internal leading is equal to the em height.</span></span> <span data-ttu-id="0cf9b-129">儲存格的高度加上外部的前置字元等於行距。</span><span class="sxs-lookup"><span data-stu-id="0cf9b-129">The cell height plus the external leading is equal to the line spacing.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.FontsAndText#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0cf9b-130">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="0cf9b-130">Compiling the Code</span></span>  
 <span data-ttu-id="0cf9b-131">上述範例設計是為搭配 Windows Form 使用所設計，而且需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.PaintEventHandler> 的參數。</span><span class="sxs-lookup"><span data-stu-id="0cf9b-131">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cf9b-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="0cf9b-132">See Also</span></span>  
 [<span data-ttu-id="0cf9b-133">Windows Forms 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="0cf9b-133">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="0cf9b-134">使用字型和文字</span><span class="sxs-lookup"><span data-stu-id="0cf9b-134">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
