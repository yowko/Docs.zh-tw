---
title: "使用字型和文字"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing in Windows Forms
- examples [Windows Forms], fonts and text
- fonts [Windows Forms], using in Windows Forms
- strings [Windows Forms], drawing in Windows Forms
ms.assetid: d43640f3-da94-4df2-a29d-a9d021a1c069
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c18dde7265a07eb45e0211a882b19acc6342e924
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="using-fonts-and-text"></a><span data-ttu-id="5af62-102">使用字型和文字</span><span class="sxs-lookup"><span data-stu-id="5af62-102">Using Fonts and Text</span></span>
<span data-ttu-id="5af62-103">所提供的許多類別[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]和[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]Windows Form 上繪製文字。</span><span class="sxs-lookup"><span data-stu-id="5af62-103">There are several classes offered by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] for drawing text on Windows Forms.</span></span> <span data-ttu-id="5af62-104">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics>類別有數個<xref:System.Drawing.Graphics.DrawString%2A>方法可讓您指定的文字，例如位置、 週框矩形、 字型及格式的各種功能。</span><span class="sxs-lookup"><span data-stu-id="5af62-104">The [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> class has several <xref:System.Drawing.Graphics.DrawString%2A> methods that allow you to specify various features of text, such as location, bounding rectangle, font, and format.</span></span> <span data-ttu-id="5af62-105">此外，您可以在 繪圖，並測量的文字[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]使用靜態<xref:System.Windows.Forms.TextRenderer.DrawText%2A>和<xref:System.Windows.Forms.TextRenderer.MeasureText%2A>方法所提供`TextRenderer`類別。</span><span class="sxs-lookup"><span data-stu-id="5af62-105">In addition, you can draw and measure text with [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] using the static <xref:System.Windows.Forms.TextRenderer.DrawText%2A> and <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> methods offered by the `TextRenderer` class.</span></span> <span data-ttu-id="5af62-106">[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]方法也可讓您指定的位置、 字型及格式。</span><span class="sxs-lookup"><span data-stu-id="5af62-106">The [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] methods also allow you to specify location, font, and format.</span></span> <span data-ttu-id="5af62-107">您可以任選[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]或[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]文字轉譯; 不過，[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]通常提供較佳的效能和更精確測量的文字。</span><span class="sxs-lookup"><span data-stu-id="5af62-107">You can choose either [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] or [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] for text rendering; however, [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] generally offers better performance and more accurate text measuring.</span></span> <span data-ttu-id="5af62-108">用於文字轉譯的其他類別包含`FontFamily`， `Font`， <xref:System.Drawing.StringFormat>，和`TextFormatFlags`。</span><span class="sxs-lookup"><span data-stu-id="5af62-108">Other classes that contribute to text rendering include `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, and `TextFormatFlags`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5af62-109">本章節內容</span><span class="sxs-lookup"><span data-stu-id="5af62-109">In This Section</span></span>  
 [<span data-ttu-id="5af62-110">操作說明：建構字型系列和字型</span><span class="sxs-lookup"><span data-stu-id="5af62-110">How to: Construct Font Families and Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 <span data-ttu-id="5af62-111">示範如何建立`Font`和`FontFamily`物件。</span><span class="sxs-lookup"><span data-stu-id="5af62-111">Shows how to create `Font` and `FontFamily` objects.</span></span>  
  
 [<span data-ttu-id="5af62-112">操作說明：在指定的位置繪製文字</span><span class="sxs-lookup"><span data-stu-id="5af62-112">How to: Draw Text at a Specified Location</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)  
 <span data-ttu-id="5af62-113">描述如何繪製文字中特定位置使用[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]和[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5af62-113">Describes how to draw text in a certain location using [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 [<span data-ttu-id="5af62-114">操作說明：在矩形中繪製被包圍的文字</span><span class="sxs-lookup"><span data-stu-id="5af62-114">How to: Draw Wrapped Text in a Rectangle</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)  
 <span data-ttu-id="5af62-115">說明如何繪製矩形，利用文字[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]和[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5af62-115">Explains how to draw text in a rectangle using [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 [<span data-ttu-id="5af62-116">操作說明：使用 GDI 繪製文字</span><span class="sxs-lookup"><span data-stu-id="5af62-116">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 <span data-ttu-id="5af62-117">示範如何使用[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]來繪製文字。</span><span class="sxs-lookup"><span data-stu-id="5af62-117">Demonstrates how to use [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] for drawing text.</span></span>  
  
 [<span data-ttu-id="5af62-118">操作說明：對齊繪製的文字</span><span class="sxs-lookup"><span data-stu-id="5af62-118">How to: Align Drawn Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-align-drawn-text.md)  
 <span data-ttu-id="5af62-119">示範如何格式化[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]和[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]文字。</span><span class="sxs-lookup"><span data-stu-id="5af62-119">Shows how to format [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] text.</span></span>  
  
 [<span data-ttu-id="5af62-120">操作說明：建立垂直文字</span><span class="sxs-lookup"><span data-stu-id="5af62-120">How to: Create Vertical Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-vertical-text.md)  
 <span data-ttu-id="5af62-121">描述如何繪製垂直對齊的文字與[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5af62-121">Describes how to draw vertically aligned text with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
 [<span data-ttu-id="5af62-122">操作說明：在已繪製的文字中設定定位停駐點</span><span class="sxs-lookup"><span data-stu-id="5af62-122">How to: Set Tab Stops in Drawn Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-tab-stops-in-drawn-text.md)  
 <span data-ttu-id="5af62-123">顯示如何繪製文字的定位停駐點[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5af62-123">Shows how draw text with tab stops with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
 [<span data-ttu-id="5af62-124">操作說明：列舉已安裝的字型</span><span class="sxs-lookup"><span data-stu-id="5af62-124">How to: Enumerate Installed Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-enumerate-installed-fonts.md)  
 <span data-ttu-id="5af62-125">說明如何列出已安裝的字型名稱。</span><span class="sxs-lookup"><span data-stu-id="5af62-125">Explains how to list the names of installed fonts.</span></span>  
  
 [<span data-ttu-id="5af62-126">操作說明：建立私用字型集合</span><span class="sxs-lookup"><span data-stu-id="5af62-126">How to: Create a Private Font Collection</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-private-font-collection.md)  
 <span data-ttu-id="5af62-127">描述如何建立<xref:System.Drawing.Text.PrivateFontCollection>物件。</span><span class="sxs-lookup"><span data-stu-id="5af62-127">Describes how to create a <xref:System.Drawing.Text.PrivateFontCollection> object.</span></span>  
  
 [<span data-ttu-id="5af62-128">操作說明：取得字型度量資訊</span><span class="sxs-lookup"><span data-stu-id="5af62-128">How to: Obtain Font Metrics</span></span>](../../../../docs/framework/winforms/advanced/how-to-obtain-font-metrics.md)  
 <span data-ttu-id="5af62-129">示範如何取得字型度量資訊，例如方格上移和下移。</span><span class="sxs-lookup"><span data-stu-id="5af62-129">Shows how to obtain font metrics such as cell ascent and descent.</span></span>  
  
 [<span data-ttu-id="5af62-130">操作說明：使用文字反鋸齒功能</span><span class="sxs-lookup"><span data-stu-id="5af62-130">How to: Use Antialiasing with Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)  
 <span data-ttu-id="5af62-131">說明如何使用時繪製文字的消除鋸齒。</span><span class="sxs-lookup"><span data-stu-id="5af62-131">Explains how to use antialiasing when drawing text.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5af62-132">參考資料</span><span class="sxs-lookup"><span data-stu-id="5af62-132">Reference</span></span>  
 <xref:System.Drawing.Font>  
 <span data-ttu-id="5af62-133">描述這個類別，並包含其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="5af62-133">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.FontFamily>  
 <span data-ttu-id="5af62-134">描述這個類別，並包含其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="5af62-134">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 <span data-ttu-id="5af62-135">描述這個類別，並包含其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="5af62-135">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextRenderer>  
 <span data-ttu-id="5af62-136">描述這個類別，並包含其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="5af62-136">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 <span data-ttu-id="5af62-137">描述這個類別，並包含其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="5af62-137">Describes this class and contains links to all of its members.</span></span>
