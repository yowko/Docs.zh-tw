---
title: 圖形和繪圖
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 10ad18d38c84f6e447601ab6c8bf1a953dabb7cf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746398"
---
# <a name="graphics-and-drawing-in-windows-forms"></a><span data-ttu-id="9a42b-102">Windows Form 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="9a42b-102">Graphics and Drawing in Windows Forms</span></span>
<span data-ttu-id="9a42b-103">通用語言執行平臺會使用稱為 GDI + 的 Windows 圖形裝置介面（GDI）的先進實作為。</span><span class="sxs-lookup"><span data-stu-id="9a42b-103">The common language runtime uses an advanced implementation of the Windows Graphics Device Interface (GDI) called GDI+.</span></span> <span data-ttu-id="9a42b-104">使用 GDI +，您可以建立圖形、繪製文字，並將圖形影像當做物件來操作。</span><span class="sxs-lookup"><span data-stu-id="9a42b-104">With GDI+ you can create graphics, draw text, and manipulate graphical images as objects.</span></span> <span data-ttu-id="9a42b-105">GDI + 的設計可提供效能和方便使用。</span><span class="sxs-lookup"><span data-stu-id="9a42b-105">GDI+ is designed to offer performance and ease of use.</span></span> <span data-ttu-id="9a42b-106">您可以使用 GDI + 在 Windows Forms 和控制項上轉譯圖形影像。</span><span class="sxs-lookup"><span data-stu-id="9a42b-106">You can use GDI+ to render graphical images on Windows Forms and controls.</span></span> <span data-ttu-id="9a42b-107">雖然您無法直接在 Web Forms 上使用 GDI +，但是您可以透過影像 Web 服務器控制項顯示圖形影像。</span><span class="sxs-lookup"><span data-stu-id="9a42b-107">Although you cannot use GDI+ directly on Web Forms, you can display graphical images through the Image Web Server control.</span></span>  
  
 <span data-ttu-id="9a42b-108">在本節中，您會找到介紹 GDI + 程式設計基本概念的主題。</span><span class="sxs-lookup"><span data-stu-id="9a42b-108">In this section, you will find topics that introduce the fundamentals of GDI+ programming.</span></span> <span data-ttu-id="9a42b-109">雖然本節不是完整的參考，但包含 <xref:System.Drawing.Graphics>、<xref:System.Drawing.Pen>、<xref:System.Drawing.Brush> 和 <xref:System.Drawing.Color> 物件的相關資訊，並說明如何執行繪製圖案、繪製文字或顯示影像等工作。</span><span class="sxs-lookup"><span data-stu-id="9a42b-109">Although not intended to be a comprehensive reference, this section includes information about the <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, and <xref:System.Drawing.Color> objects, and explains how to perform such tasks as drawing shapes, drawing text, or displaying images.</span></span> <span data-ttu-id="9a42b-110">如需詳細資訊，請參閱[Gdi + 參考](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference)。</span><span class="sxs-lookup"><span data-stu-id="9a42b-110">For more information, see [GDI+ Reference](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span></span>  
  
 <span data-ttu-id="9a42b-111">如果您想要參與並立即開始，請參閱[圖形程式設計入門](getting-started-with-graphics-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="9a42b-111">If you'd like to jump in and get started right away, see [Getting Started with Graphics Programming](getting-started-with-graphics-programming.md).</span></span> <span data-ttu-id="9a42b-112">它包含如何使用程式碼在 Windows 表單上繪製線條、圖形、文字和其他項目的主題。</span><span class="sxs-lookup"><span data-stu-id="9a42b-112">It has topics on how to use code to draw lines, shapes, text, and more on Windows forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9a42b-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="9a42b-113">In This Section</span></span>  
 [<span data-ttu-id="9a42b-114">圖形概觀</span><span class="sxs-lookup"><span data-stu-id="9a42b-114">Graphics Overview</span></span>](graphics-overview-windows-forms.md)  
 <span data-ttu-id="9a42b-115">介紹與圖形相關的 Managed 類別。</span><span class="sxs-lookup"><span data-stu-id="9a42b-115">Provides an introduction to the graphics-related managed classes.</span></span>  
  
 [<span data-ttu-id="9a42b-116">關於 GDI+ Managed 程式碼</span><span class="sxs-lookup"><span data-stu-id="9a42b-116">About GDI+ Managed Code</span></span>](about-gdi-managed-code.md)  
 <span data-ttu-id="9a42b-117">提供 managed GDI + 類別的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9a42b-117">Provides information about the managed GDI+ classes.</span></span>  
  
 [<span data-ttu-id="9a42b-118">使用 Managed 圖形類別</span><span class="sxs-lookup"><span data-stu-id="9a42b-118">Using Managed Graphics Classes</span></span>](using-managed-graphics-classes.md)  
 <span data-ttu-id="9a42b-119">示範如何使用 GDI + managed 類別完成各種工作。</span><span class="sxs-lookup"><span data-stu-id="9a42b-119">Demonstrates how to complete a variety of tasks using the GDI+ managed classes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9a42b-120">參考</span><span class="sxs-lookup"><span data-stu-id="9a42b-120">Reference</span></span>  
 <xref:System.Drawing>  
 <span data-ttu-id="9a42b-121">提供對 GDI + 基本圖形功能的存取。</span><span class="sxs-lookup"><span data-stu-id="9a42b-121">Provides access to GDI+ basic graphics functionality.</span></span>  
  
 <xref:System.Drawing.Drawing2D>  
 <span data-ttu-id="9a42b-122">提供進階二維和向量圖形功能。</span><span class="sxs-lookup"><span data-stu-id="9a42b-122">Provides advanced two-dimensional and vector graphics functionality.</span></span>  
  
 <xref:System.Drawing.Imaging>  
 <span data-ttu-id="9a42b-123">提供 advanced GDI + 影像處理功能。</span><span class="sxs-lookup"><span data-stu-id="9a42b-123">Provides advanced GDI+ imaging functionality.</span></span>  
  
 <xref:System.Drawing.Text>  
 <span data-ttu-id="9a42b-124">提供 advanced GDI + 印刷樣式功能。</span><span class="sxs-lookup"><span data-stu-id="9a42b-124">Provides advanced GDI+ typography functionality.</span></span> <span data-ttu-id="9a42b-125">這個命名空間中的類別可以用來建立及使用字型集合。</span><span class="sxs-lookup"><span data-stu-id="9a42b-125">The classes in this namespace can be used to create and use collections of fonts.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="9a42b-126">提供列印功能。</span><span class="sxs-lookup"><span data-stu-id="9a42b-126">Provides printing functionality.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9a42b-127">相關章節</span><span class="sxs-lookup"><span data-stu-id="9a42b-127">Related Sections</span></span>  
 [<span data-ttu-id="9a42b-128">自訂控制項繪製和轉譯 </span><span class="sxs-lookup"><span data-stu-id="9a42b-128">Custom Control Painting and Rendering</span></span>](../controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="9a42b-129">詳細說明如何提供繪製控制項的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9a42b-129">Details how to provide code for painting controls.</span></span>
