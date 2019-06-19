---
title: 雙重緩衝的使用
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], double buffering
- double buffering
- flicker [Windows Forms], reducing in Windows Forms
- buffering [Windows Forms], double buffering
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
ms.openlocfilehash: 5b22336221c7bdda3c9dd7adf23308a2b0bad450
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169913"
---
# <a name="using-double-buffering"></a><span data-ttu-id="dc060-102">雙重緩衝的使用</span><span class="sxs-lookup"><span data-stu-id="dc060-102">Using Double Buffering</span></span>
<span data-ttu-id="dc060-103">若要減少重繪閃動包含複雜繪製作業的應用程式中，您可以使用雙重緩衝的圖形。</span><span class="sxs-lookup"><span data-stu-id="dc060-103">You can use double-buffered graphics to reduce flicker in your applications that contain complex painting operations.</span></span> <span data-ttu-id="dc060-104">.NET Framework 包含雙重緩衝的內建支援，或者您可以管理並手動呈現圖形。</span><span class="sxs-lookup"><span data-stu-id="dc060-104">The .NET Framework contains built-in support for double-buffering or you can manage and render graphics manually.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dc060-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="dc060-105">In This Section</span></span>  
 [<span data-ttu-id="dc060-106">雙重緩衝的圖形</span><span class="sxs-lookup"><span data-stu-id="dc060-106">Double Buffered Graphics</span></span>](double-buffered-graphics.md)  
 <span data-ttu-id="dc060-107">導入雙重緩衝概念並勾畫.NET Framework 支援。</span><span class="sxs-lookup"><span data-stu-id="dc060-107">Introduces double buffering concept and outlines .NET Framework support.</span></span>  
  
 [<span data-ttu-id="dc060-108">如何：減少使用表單和控制項的雙重緩衝的圖形重繪閃動</span><span class="sxs-lookup"><span data-stu-id="dc060-108">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 <span data-ttu-id="dc060-109">示範如何使用雙重緩衝支援.NET Framework 中的預設值。</span><span class="sxs-lookup"><span data-stu-id="dc060-109">Demonstrates how to use the default double buffering support in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="dc060-110">如何：手動管理已緩衝的圖形</span><span class="sxs-lookup"><span data-stu-id="dc060-110">How to: Manually Manage Buffered Graphics</span></span>](how-to-manually-manage-buffered-graphics.md)  
 <span data-ttu-id="dc060-111">示範如何管理應用程式中的雙重緩衝。</span><span class="sxs-lookup"><span data-stu-id="dc060-111">Shows how to manage double buffering in applications.</span></span>  
  
 [<span data-ttu-id="dc060-112">如何：手動轉譯已緩衝的圖形</span><span class="sxs-lookup"><span data-stu-id="dc060-112">How to: Manually Render Buffered Graphics</span></span>](how-to-manually-render-buffered-graphics.md)  
 <span data-ttu-id="dc060-113">示範如何轉譯雙重緩衝的圖形。</span><span class="sxs-lookup"><span data-stu-id="dc060-113">Demonstrates how to render double-buffered graphics.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="dc060-114">參考資料</span><span class="sxs-lookup"><span data-stu-id="dc060-114">Reference</span></span>  
 <span data-ttu-id="dc060-115"><xref:System.Windows.Forms.Control.SetStyle%2A> 啟用雙重緩衝處理的控制方法。</span><span class="sxs-lookup"><span data-stu-id="dc060-115"><xref:System.Windows.Forms.Control.SetStyle%2A> Control method that enables double buffering.</span></span>  
  
 <span data-ttu-id="dc060-116"><xref:System.Drawing.BufferedGraphicsContext> 提供方法來建立圖形緩衝區。</span><span class="sxs-lookup"><span data-stu-id="dc060-116"><xref:System.Drawing.BufferedGraphicsContext> Provides methods for creating graphics buffers.</span></span>  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 <span data-ttu-id="dc060-117">提供應用程式定義域的存取權的已緩衝的圖形內容。</span><span class="sxs-lookup"><span data-stu-id="dc060-117">Provides access to the buffered graphics context for a application domain.</span></span>
