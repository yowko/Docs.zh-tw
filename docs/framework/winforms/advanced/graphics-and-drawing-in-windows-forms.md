---
title: "Windows Form 中的圖形和繪圖"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ae9810b10a7357f7f8d00783335335a391a5211
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="graphics-and-drawing-in-windows-forms"></a><span data-ttu-id="866cf-102">Windows Form 中的圖形和繪圖</span><span class="sxs-lookup"><span data-stu-id="866cf-102">Graphics and Drawing in Windows Forms</span></span>
<span data-ttu-id="866cf-103">Common Language Runtime 使用 Windows 圖形裝置介面 ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) 的進階實作，稱為 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="866cf-103">The common language runtime uses an advanced implementation of the Windows Graphics Device Interface ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) called [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="866cf-104">透過 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，您可以建立圖形、繪製文字，並將圖形影像當做物件來管理。</span><span class="sxs-lookup"><span data-stu-id="866cf-104">With [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] you can create graphics, draw text, and manipulate graphical images as objects.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="866cf-105"> 的設計目的在於提升效能和方便使用。</span><span class="sxs-lookup"><span data-stu-id="866cf-105"> is designed to offer performance and ease of use.</span></span> <span data-ttu-id="866cf-106">您可以使用 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 在 Windows Form 和控制項上呈現圖形影像。</span><span class="sxs-lookup"><span data-stu-id="866cf-106">You can use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to render graphical images on Windows Forms and controls.</span></span> <span data-ttu-id="866cf-107">雖然您無法直接在 Web Form 上使用 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，但是您可以透過 Image Web 伺服器控制項顯示圖形影像。</span><span class="sxs-lookup"><span data-stu-id="866cf-107">Although you cannot use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] directly on Web Forms, you can display graphical images through the Image Web Server control.</span></span>  
  
 <span data-ttu-id="866cf-108">在本節中，您將找到介紹 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 程式設計之基本概念的主題。</span><span class="sxs-lookup"><span data-stu-id="866cf-108">In this section, you will find topics that introduce the fundamentals of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] programming.</span></span> <span data-ttu-id="866cf-109">雖然本節不是完整的參考，但包含 <xref:System.Drawing.Graphics>、<xref:System.Drawing.Pen>、<xref:System.Drawing.Brush> 和 <xref:System.Drawing.Color> 物件的相關資訊，並說明如何執行繪製圖案、繪製文字或顯示影像等工作。</span><span class="sxs-lookup"><span data-stu-id="866cf-109">Although not intended to be a comprehensive reference, this section includes information about the <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, and <xref:System.Drawing.Color> objects, and explains how to perform such tasks as drawing shapes, drawing text, or displaying images.</span></span> <span data-ttu-id="866cf-110">如需詳細資訊，請參閱[GDI + 參考](https://msdn.microsoft.com/library/vs/alm/ms533799.aspx)。</span><span class="sxs-lookup"><span data-stu-id="866cf-110">For more information, see [GDI+ Reference](https://msdn.microsoft.com/library/vs/alm/ms533799.aspx).</span></span>  
  
 <span data-ttu-id="866cf-111">如果您想要參與並立即開始，請參閱[圖形程式設計入門](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="866cf-111">If you'd like to jump in and get started right away, see [Getting Started with Graphics Programming](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md).</span></span> <span data-ttu-id="866cf-112">它包含如何使用程式碼在 Windows 表單上繪製線條、圖形、文字和其他項目的主題。</span><span class="sxs-lookup"><span data-stu-id="866cf-112">It has topics on how to use code to draw lines, shapes, text, and more on Windows forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="866cf-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="866cf-113">In This Section</span></span>  
 [<span data-ttu-id="866cf-114">圖形概觀</span><span class="sxs-lookup"><span data-stu-id="866cf-114">Graphics Overview</span></span>](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 <span data-ttu-id="866cf-115">介紹與圖形相關的 Managed 類別。</span><span class="sxs-lookup"><span data-stu-id="866cf-115">Provides an introduction to the graphics-related managed classes.</span></span>  
  
 [<span data-ttu-id="866cf-116">關於 GDI+ Managed 程式碼</span><span class="sxs-lookup"><span data-stu-id="866cf-116">About GDI+ Managed Code</span></span>](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 <span data-ttu-id="866cf-117">提供 Managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 類別的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="866cf-117">Provides information about the managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes.</span></span>  
  
 [<span data-ttu-id="866cf-118">使用 Managed 圖形類別</span><span class="sxs-lookup"><span data-stu-id="866cf-118">Using Managed Graphics Classes</span></span>](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 <span data-ttu-id="866cf-119">示範如何使用 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Managed 類別完成各種工作。</span><span class="sxs-lookup"><span data-stu-id="866cf-119">Demonstrates how to complete a variety of tasks using the [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] managed classes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="866cf-120">參考資料</span><span class="sxs-lookup"><span data-stu-id="866cf-120">Reference</span></span>  
 <xref:System.Drawing>  
 <span data-ttu-id="866cf-121">提供對 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 基本圖形功能的存取。</span><span class="sxs-lookup"><span data-stu-id="866cf-121">Provides access to [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] basic graphics functionality.</span></span>  
  
 <xref:System.Drawing.Drawing2D>  
 <span data-ttu-id="866cf-122">提供進階二維和向量圖形功能。</span><span class="sxs-lookup"><span data-stu-id="866cf-122">Provides advanced two-dimensional and vector graphics functionality.</span></span>  
  
 <xref:System.Drawing.Imaging>  
 <span data-ttu-id="866cf-123">提供進階 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 影像處理功能。</span><span class="sxs-lookup"><span data-stu-id="866cf-123">Provides advanced [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] imaging functionality.</span></span>  
  
 <xref:System.Drawing.Text>  
 <span data-ttu-id="866cf-124">提供進階 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 印刷樣式功能。</span><span class="sxs-lookup"><span data-stu-id="866cf-124">Provides advanced [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] typography functionality.</span></span> <span data-ttu-id="866cf-125">這個命名空間中的類別可以用來建立及使用字型集合。</span><span class="sxs-lookup"><span data-stu-id="866cf-125">The classes in this namespace can be used to create and use collections of fonts.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="866cf-126">提供列印功能。</span><span class="sxs-lookup"><span data-stu-id="866cf-126">Provides printing functionality.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="866cf-127">相關章節</span><span class="sxs-lookup"><span data-stu-id="866cf-127">Related Sections</span></span>  
 [<span data-ttu-id="866cf-128">自訂控制項繪製和轉譯 </span><span class="sxs-lookup"><span data-stu-id="866cf-128">Custom Control Painting and Rendering</span></span>](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="866cf-129">詳細說明如何提供繪製控制項的程式碼。</span><span class="sxs-lookup"><span data-stu-id="866cf-129">Details how to provide code for painting controls.</span></span>
