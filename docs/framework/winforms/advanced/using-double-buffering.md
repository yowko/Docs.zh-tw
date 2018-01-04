---
title: "雙重緩衝的使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], double buffering
- double buffering
- flicker [Windows Forms], reducing in Windows Forms
- buffering [Windows Forms], double buffering
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d83846dcded620b74f7d276fd241a302cce1b60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="using-double-buffering"></a><span data-ttu-id="840b5-102">雙重緩衝的使用</span><span class="sxs-lookup"><span data-stu-id="840b5-102">Using Double Buffering</span></span>
<span data-ttu-id="840b5-103">若要減少重繪閃動在包含複雜繪製作業的應用程式中，您可以使用雙重緩衝的圖形。</span><span class="sxs-lookup"><span data-stu-id="840b5-103">You can use double-buffered graphics to reduce flicker in your applications that contain complex painting operations.</span></span> <span data-ttu-id="840b5-104">.NET Framework 包含雙重緩衝的內建支援，或您可以管理，並手動呈現圖形。</span><span class="sxs-lookup"><span data-stu-id="840b5-104">The .NET Framework contains built-in support for double-buffering or you can manage and render graphics manually.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="840b5-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="840b5-105">In This Section</span></span>  
 [<span data-ttu-id="840b5-106">雙重緩衝的圖形</span><span class="sxs-lookup"><span data-stu-id="840b5-106">Double Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 <span data-ttu-id="840b5-107">導入了雙重緩衝概念和大綱.NET Framework 支援。</span><span class="sxs-lookup"><span data-stu-id="840b5-107">Introduces double buffering concept and outlines .NET Framework support.</span></span>  
  
 [<span data-ttu-id="840b5-108">操作說明：使用表單和控制項的雙重緩衝以減少圖形閃爍</span><span class="sxs-lookup"><span data-stu-id="840b5-108">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 <span data-ttu-id="840b5-109">示範如何使用雙重緩衝支援.NET Framework 中的預設值。</span><span class="sxs-lookup"><span data-stu-id="840b5-109">Demonstrates how to use the default double buffering support in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="840b5-110">操作說明：手動管理已緩衝的圖形</span><span class="sxs-lookup"><span data-stu-id="840b5-110">How to: Manually Manage Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)  
 <span data-ttu-id="840b5-111">示範如何管理應用程式中的雙重緩衝。</span><span class="sxs-lookup"><span data-stu-id="840b5-111">Shows how to manage double buffering in applications.</span></span>  
  
 [<span data-ttu-id="840b5-112">操作說明：手動轉譯已緩衝的圖形</span><span class="sxs-lookup"><span data-stu-id="840b5-112">How to: Manually Render Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)  
 <span data-ttu-id="840b5-113">示範如何轉譯雙重緩衝的圖形。</span><span class="sxs-lookup"><span data-stu-id="840b5-113">Demonstrates how to render double-buffered graphics.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="840b5-114">參考資料</span><span class="sxs-lookup"><span data-stu-id="840b5-114">Reference</span></span>  
 <span data-ttu-id="840b5-115"><xref:System.Windows.Forms.Control.SetStyle%2A> ,</span><span class="sxs-lookup"><span data-stu-id="840b5-115"><xref:System.Windows.Forms.Control.SetStyle%2A> ,</span></span>  
 <span data-ttu-id="840b5-116">控制項可讓雙重緩衝的方法。</span><span class="sxs-lookup"><span data-stu-id="840b5-116">Control method that enables double buffering.</span></span>  
  
 <span data-ttu-id="840b5-117"><xref:System.Drawing.BufferedGraphicsContext> ,</span><span class="sxs-lookup"><span data-stu-id="840b5-117"><xref:System.Drawing.BufferedGraphicsContext> ,</span></span>  
 <span data-ttu-id="840b5-118">提供方法來建立圖形緩衝區。</span><span class="sxs-lookup"><span data-stu-id="840b5-118">Provides methods for creating graphics buffers.</span></span>  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 <span data-ttu-id="840b5-119">提供應用程式定義域已緩衝的圖形內容的存取。</span><span class="sxs-lookup"><span data-stu-id="840b5-119">Provides access to the buffered graphics context for a application domain.</span></span>
