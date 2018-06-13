---
title: 分析 (Unmanaged API 參考)
ms.date: 03/30/2017
helpviewer_keywords:
- profiling [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], profiling
- unmanaged API reference [.NET Framework], profiling
ms.assetid: 14c68e84-657e-49c2-aa8b-4978dbaf4454
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 581f42dc83622712dbb30ef556a481388bafe259
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455568"
---
# <a name="profiling-unmanaged-api-reference"></a><span data-ttu-id="8b9b9-102">分析 (Unmanaged API 參考)</span><span class="sxs-lookup"><span data-stu-id="8b9b9-102">Profiling (Unmanaged API Reference)</span></span>
<span data-ttu-id="8b9b9-103">分析 API 可讓監視程式執行的 common language runtime (CLR) 分析工具。</span><span class="sxs-lookup"><span data-stu-id="8b9b9-103">The profiling API enables a profiler to monitor a program's execution by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b9b9-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="8b9b9-104">In This Section</span></span>  
 [<span data-ttu-id="8b9b9-105">分析概觀</span><span class="sxs-lookup"><span data-stu-id="8b9b9-105">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
 <span data-ttu-id="8b9b9-106">說明服務與介面，CLR 會提供以支援.NET Framework 環境中的 程式碼剖析。</span><span class="sxs-lookup"><span data-stu-id="8b9b9-106">Describes the services and interfaces that the CLR provides to support profiling in the .NET Framework environment.</span></span>  
  
 [<span data-ttu-id="8b9b9-107">分析介面</span><span class="sxs-lookup"><span data-stu-id="8b9b9-107">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 <span data-ttu-id="8b9b9-108">說明分析 API 所使用的 Unmanaged 介面。</span><span class="sxs-lookup"><span data-stu-id="8b9b9-108">Describes the unmanaged interfaces that the profiling API uses.</span></span>  
  
 [<span data-ttu-id="8b9b9-109">設定分析環境</span><span class="sxs-lookup"><span data-stu-id="8b9b9-109">Setting Up a Profiling Environment</span></span>](../../../../docs/framework/unmanaged-api/profiling/setting-up-a-profiling-environment.md)  
 <span data-ttu-id="8b9b9-110">描述.NET Framework 應用程式設定檔時，必須採取的步驟。</span><span class="sxs-lookup"><span data-stu-id="8b9b9-110">Describes the steps you must take to profile a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="8b9b9-111">CLR 分析工具和 Windows 市集應用程式</span><span class="sxs-lookup"><span data-stu-id="8b9b9-111">CLR Profilers and Windows Store Apps</span></span>](../../../../docs/framework/unmanaged-api/profiling/clr-profilers-and-windows-store-apps.md)  
 <span data-ttu-id="8b9b9-112">討論如何使用 Windows 市集應用程式順利運作的 CLR 程式碼剖析 API 的診斷工具的連接埠。</span><span class="sxs-lookup"><span data-stu-id="8b9b9-112">Discusses how to port diagnostic tools that consume the CLR Profiling API to work successfully with Windows Store apps.</span></span>  
  
 [<span data-ttu-id="8b9b9-113">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT</span><span class="sxs-lookup"><span data-stu-id="8b9b9-113">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT</span></span>](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md)  
 <span data-ttu-id="8b9b9-114">文件的方法呼叫會傳回在其下的條件`CORPROF_E_UNSUPPORTED_CALL_SEQUENCE`HRESULT。</span><span class="sxs-lookup"><span data-stu-id="8b9b9-114">Documents the conditions under which a method call returns the `CORPROF_E_UNSUPPORTED_CALL_SEQUENCE` HRESULT.</span></span>  
  
 [<span data-ttu-id="8b9b9-115">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="8b9b9-115">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
 <span data-ttu-id="8b9b9-116">說明分析 API 所使用的 Unmanaged 全域靜態函式。</span><span class="sxs-lookup"><span data-stu-id="8b9b9-116">Describes the unmanaged global static functions that the profiling API uses.</span></span>  
  
 [<span data-ttu-id="8b9b9-117">分析列舉</span><span class="sxs-lookup"><span data-stu-id="8b9b9-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
 <span data-ttu-id="8b9b9-118">說明分析 API 所使用的 Unmanaged 列舉。</span><span class="sxs-lookup"><span data-stu-id="8b9b9-118">Describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
 [<span data-ttu-id="8b9b9-119">分析結構</span><span class="sxs-lookup"><span data-stu-id="8b9b9-119">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)  
 <span data-ttu-id="8b9b9-120">說明分析 API 所使用的 Unmanaged 結構。</span><span class="sxs-lookup"><span data-stu-id="8b9b9-120">Describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8b9b9-121">相關章節</span><span class="sxs-lookup"><span data-stu-id="8b9b9-121">Related Sections</span></span>  
 [<span data-ttu-id="8b9b9-122">逐步解說：找出效能問題</span><span class="sxs-lookup"><span data-stu-id="8b9b9-122">Walkthrough: Identifying Performance Problems</span></span>](/visualstudio/profiling/walkthrough-identifying-performance-problems)  
 <span data-ttu-id="8b9b9-123">說明如何在 Microsoft Visual Studio 2005 Team System 中使用內建的程式碼剖析工具。</span><span class="sxs-lookup"><span data-stu-id="8b9b9-123">Explains how to use the built-in profiling tools in the Microsoft Visual Studio 2005 Team System.</span></span> <span data-ttu-id="8b9b9-124">這些工具提供另一個方法，使用程式碼剖析 API。</span><span class="sxs-lookup"><span data-stu-id="8b9b9-124">These tools provide an alternative approach to using the profiling API.</span></span>
