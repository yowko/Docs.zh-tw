---
title: 使用字型和文字
ms.date: 03/30/2017
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing in Windows Forms
- examples [Windows Forms], fonts and text
- fonts [Windows Forms], using in Windows Forms
- strings [Windows Forms], drawing in Windows Forms
ms.assetid: d43640f3-da94-4df2-a29d-a9d021a1c069
ms.openlocfilehash: 73a4af5fe7367e777fcb83af8c84c09be91e5b1e
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505116"
---
# <a name="using-fonts-and-text"></a><span data-ttu-id="160e6-102">使用字型和文字</span><span class="sxs-lookup"><span data-stu-id="160e6-102">Using Fonts and Text</span></span>
<span data-ttu-id="160e6-103">有數個 Windows Form 上繪製文字的 GDI + 和 GDI 所提供的類別。</span><span class="sxs-lookup"><span data-stu-id="160e6-103">There are several classes offered by GDI+ and GDI for drawing text on Windows Forms.</span></span> <span data-ttu-id="160e6-104">GDI +<xref:System.Drawing.Graphics>類別有數個<xref:System.Drawing.Graphics.DrawString%2A>方法，可讓您指定的文字，例如地點、 週框矩形、 字型和格式的各種功能。</span><span class="sxs-lookup"><span data-stu-id="160e6-104">The GDI+ <xref:System.Drawing.Graphics> class has several <xref:System.Drawing.Graphics.DrawString%2A> methods that allow you to specify various features of text, such as location, bounding rectangle, font, and format.</span></span> <span data-ttu-id="160e6-105">此外，您可以在其中繪製並測量的文字與使用靜態的 GDI<xref:System.Windows.Forms.TextRenderer.DrawText%2A>並<xref:System.Windows.Forms.TextRenderer.MeasureText%2A>所提供的方法`TextRenderer`類別。</span><span class="sxs-lookup"><span data-stu-id="160e6-105">In addition, you can draw and measure text with GDI using the static <xref:System.Windows.Forms.TextRenderer.DrawText%2A> and <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> methods offered by the `TextRenderer` class.</span></span> <span data-ttu-id="160e6-106">GDI 方法也可讓您指定的位置、 字型和格式。</span><span class="sxs-lookup"><span data-stu-id="160e6-106">The GDI methods also allow you to specify location, font, and format.</span></span> <span data-ttu-id="160e6-107">您可以選擇 GDI 或 GDI + 的文字呈現;不過，GDI 通常提供較佳的效能和更精確測量的文字。</span><span class="sxs-lookup"><span data-stu-id="160e6-107">You can choose either GDI or GDI+ for text rendering; however, GDI generally offers better performance and more accurate text measuring.</span></span> <span data-ttu-id="160e6-108">用於文字轉譯的其他類別包含`FontFamily`， `Font`， <xref:System.Drawing.StringFormat>，和`TextFormatFlags`。</span><span class="sxs-lookup"><span data-stu-id="160e6-108">Other classes that contribute to text rendering include `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, and `TextFormatFlags`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="160e6-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="160e6-109">In This Section</span></span>  
 [<span data-ttu-id="160e6-110">如何：建構字型系列和字型</span><span class="sxs-lookup"><span data-stu-id="160e6-110">How to: Construct Font Families and Fonts</span></span>](how-to-construct-font-families-and-fonts.md)  
 <span data-ttu-id="160e6-111">示範如何建立`Font`和`FontFamily`物件。</span><span class="sxs-lookup"><span data-stu-id="160e6-111">Shows how to create `Font` and `FontFamily` objects.</span></span>  
  
 [<span data-ttu-id="160e6-112">如何：在指定的位置繪製文字</span><span class="sxs-lookup"><span data-stu-id="160e6-112">How to: Draw Text at a Specified Location</span></span>](how-to-draw-text-at-a-specified-location.md)  
 <span data-ttu-id="160e6-113">描述如何在特定位置使用 GDI + 和 GDI 繪製文字。</span><span class="sxs-lookup"><span data-stu-id="160e6-113">Describes how to draw text in a certain location using GDI+ and GDI.</span></span>  
  
 [<span data-ttu-id="160e6-114">如何：在矩形中繪製被包圍的文字</span><span class="sxs-lookup"><span data-stu-id="160e6-114">How to: Draw Wrapped Text in a Rectangle</span></span>](how-to-draw-wrapped-text-in-a-rectangle.md)  
 <span data-ttu-id="160e6-115">說明如何使用 GDI + 和 GDI 矩形中繪製文字。</span><span class="sxs-lookup"><span data-stu-id="160e6-115">Explains how to draw text in a rectangle using GDI+ and GDI.</span></span>  
  
 [<span data-ttu-id="160e6-116">如何：使用 GDI 繪製文字</span><span class="sxs-lookup"><span data-stu-id="160e6-116">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)  
 <span data-ttu-id="160e6-117">示範如何使用 GDI 繪製文字。</span><span class="sxs-lookup"><span data-stu-id="160e6-117">Demonstrates how to use GDI for drawing text.</span></span>  
  
 [<span data-ttu-id="160e6-118">如何：對齊繪製的文字</span><span class="sxs-lookup"><span data-stu-id="160e6-118">How to: Align Drawn Text</span></span>](how-to-align-drawn-text.md)  
 <span data-ttu-id="160e6-119">示範如何設定 GDI + 和 GDI 文字格式。</span><span class="sxs-lookup"><span data-stu-id="160e6-119">Shows how to format GDI+ and GDI text.</span></span>  
  
 [<span data-ttu-id="160e6-120">如何：建立垂直文字</span><span class="sxs-lookup"><span data-stu-id="160e6-120">How to: Create Vertical Text</span></span>](how-to-create-vertical-text.md)  
 <span data-ttu-id="160e6-121">描述如何繪製使用 GDI + 的垂直對齊的文字。</span><span class="sxs-lookup"><span data-stu-id="160e6-121">Describes how to draw vertically aligned text with GDI+.</span></span>  
  
 [<span data-ttu-id="160e6-122">如何：在繪製文字中設定定位停駐點</span><span class="sxs-lookup"><span data-stu-id="160e6-122">How to: Set Tab Stops in Drawn Text</span></span>](how-to-set-tab-stops-in-drawn-text.md)  
 <span data-ttu-id="160e6-123">示範如何使用繪製文字使用 GDI + 的定位停駐點。</span><span class="sxs-lookup"><span data-stu-id="160e6-123">Shows how draw text with tab stops with GDI+.</span></span>  
  
 [<span data-ttu-id="160e6-124">如何：列舉已安裝的字型</span><span class="sxs-lookup"><span data-stu-id="160e6-124">How to: Enumerate Installed Fonts</span></span>](how-to-enumerate-installed-fonts.md)  
 <span data-ttu-id="160e6-125">說明如何列出已安裝的字型的名稱。</span><span class="sxs-lookup"><span data-stu-id="160e6-125">Explains how to list the names of installed fonts.</span></span>  
  
 [<span data-ttu-id="160e6-126">如何：建立私用字型集合</span><span class="sxs-lookup"><span data-stu-id="160e6-126">How to: Create a Private Font Collection</span></span>](how-to-create-a-private-font-collection.md)  
 <span data-ttu-id="160e6-127">描述如何建立<xref:System.Drawing.Text.PrivateFontCollection>物件。</span><span class="sxs-lookup"><span data-stu-id="160e6-127">Describes how to create a <xref:System.Drawing.Text.PrivateFontCollection> object.</span></span>  
  
 [<span data-ttu-id="160e6-128">如何：取得字型度量資訊</span><span class="sxs-lookup"><span data-stu-id="160e6-128">How to: Obtain Font Metrics</span></span>](how-to-obtain-font-metrics.md)  
 <span data-ttu-id="160e6-129">示範如何取得字型度量資訊，例如方格上移和下移。</span><span class="sxs-lookup"><span data-stu-id="160e6-129">Shows how to obtain font metrics such as cell ascent and descent.</span></span>  
  
 [<span data-ttu-id="160e6-130">如何：使用文字反鋸齒功能</span><span class="sxs-lookup"><span data-stu-id="160e6-130">How to: Use Antialiasing with Text</span></span>](how-to-use-antialiasing-with-text.md)  
 <span data-ttu-id="160e6-131">說明如何繪製文字時使用消除鋸齒。</span><span class="sxs-lookup"><span data-stu-id="160e6-131">Explains how to use antialiasing when drawing text.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="160e6-132">參考資料</span><span class="sxs-lookup"><span data-stu-id="160e6-132">Reference</span></span>  
 <xref:System.Drawing.Font>  
 <span data-ttu-id="160e6-133">描述這個類別，並且包含其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="160e6-133">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.FontFamily>  
 <span data-ttu-id="160e6-134">描述這個類別，並且包含其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="160e6-134">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 <span data-ttu-id="160e6-135">描述這個類別，並且包含其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="160e6-135">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextRenderer>  
 <span data-ttu-id="160e6-136">描述這個類別，並且包含其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="160e6-136">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 <span data-ttu-id="160e6-137">描述這個類別，並且包含其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="160e6-137">Describes this class and contains links to all of its members.</span></span>
