---
title: "分析 (Unmanaged API 參考)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- profiling [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], profiling
- unmanaged API reference [.NET Framework], profiling
ms.assetid: 14c68e84-657e-49c2-aa8b-4978dbaf4454
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 26fa9471b46a7a963d66ebf0d5b3c6a0286ae640
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="profiling-unmanaged-api-reference"></a><span data-ttu-id="93370-102">分析 (Unmanaged API 參考)</span><span class="sxs-lookup"><span data-stu-id="93370-102">Profiling (Unmanaged API Reference)</span></span>
<span data-ttu-id="93370-103">分析 API 可讓監視程式執行的 common language runtime (CLR) 分析工具。</span><span class="sxs-lookup"><span data-stu-id="93370-103">The profiling API enables a profiler to monitor a program's execution by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="93370-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="93370-104">In This Section</span></span>  
 [<span data-ttu-id="93370-105">程式碼剖析概觀</span><span class="sxs-lookup"><span data-stu-id="93370-105">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
 <span data-ttu-id="93370-106">說明服務與介面，CLR 會提供以支援.NET Framework 環境中的 程式碼剖析。</span><span class="sxs-lookup"><span data-stu-id="93370-106">Describes the services and interfaces that the CLR provides to support profiling in the .NET Framework environment.</span></span>  
  
 [<span data-ttu-id="93370-107">分析介面</span><span class="sxs-lookup"><span data-stu-id="93370-107">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 <span data-ttu-id="93370-108">說明分析 API 所使用的 Unmanaged 介面。</span><span class="sxs-lookup"><span data-stu-id="93370-108">Describes the unmanaged interfaces that the profiling API uses.</span></span>  
  
 [<span data-ttu-id="93370-109">設定程式碼剖析環境</span><span class="sxs-lookup"><span data-stu-id="93370-109">Setting Up a Profiling Environment</span></span>](../../../../docs/framework/unmanaged-api/profiling/setting-up-a-profiling-environment.md)  
 <span data-ttu-id="93370-110">描述.NET Framework 應用程式設定檔時，必須採取的步驟。</span><span class="sxs-lookup"><span data-stu-id="93370-110">Describes the steps you must take to profile a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="93370-111">CLR 分析工具和 Windows 市集應用程式</span><span class="sxs-lookup"><span data-stu-id="93370-111">CLR Profilers and Windows Store Apps</span></span>](../../../../docs/framework/unmanaged-api/profiling/clr-profilers-and-windows-store-apps.md)  
 <span data-ttu-id="93370-112">討論如何使用 Windows 市集應用程式順利運作的 CLR 程式碼剖析 API 的診斷工具的連接埠。</span><span class="sxs-lookup"><span data-stu-id="93370-112">Discusses how to port diagnostic tools that consume the CLR Profiling API to work successfully with Windows Store apps.</span></span>  
  
 [<span data-ttu-id="93370-113">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT</span><span class="sxs-lookup"><span data-stu-id="93370-113">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT</span></span>](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md)  
 <span data-ttu-id="93370-114">文件的方法呼叫會傳回在其下的條件`CORPROF_E_UNSUPPORTED_CALL_SEQUENCE`HRESULT。</span><span class="sxs-lookup"><span data-stu-id="93370-114">Documents the conditions under which a method call returns the `CORPROF_E_UNSUPPORTED_CALL_SEQUENCE` HRESULT.</span></span>  
  
 [<span data-ttu-id="93370-115">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="93370-115">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
 <span data-ttu-id="93370-116">說明分析 API 所使用的 Unmanaged 全域靜態函式。</span><span class="sxs-lookup"><span data-stu-id="93370-116">Describes the unmanaged global static functions that the profiling API uses.</span></span>  
  
 [<span data-ttu-id="93370-117">分析列舉</span><span class="sxs-lookup"><span data-stu-id="93370-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
 <span data-ttu-id="93370-118">說明分析 API 所使用的 Unmanaged 列舉。</span><span class="sxs-lookup"><span data-stu-id="93370-118">Describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
 [<span data-ttu-id="93370-119">分析結構</span><span class="sxs-lookup"><span data-stu-id="93370-119">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)  
 <span data-ttu-id="93370-120">說明分析 API 所使用的 Unmanaged 結構。</span><span class="sxs-lookup"><span data-stu-id="93370-120">Describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="93370-121">相關章節</span><span class="sxs-lookup"><span data-stu-id="93370-121">Related Sections</span></span>  
 [<span data-ttu-id="93370-122">逐步解說：找出效能問題</span><span class="sxs-lookup"><span data-stu-id="93370-122">Walkthrough: Identifying Performance Problems</span></span>](/visualstudio/profiling/walkthrough-identifying-performance-problems)  
 <span data-ttu-id="93370-123">說明如何在 Microsoft Visual Studio 2005 Team System 中使用內建的程式碼剖析工具。</span><span class="sxs-lookup"><span data-stu-id="93370-123">Explains how to use the built-in profiling tools in the Microsoft Visual Studio 2005 Team System.</span></span> <span data-ttu-id="93370-124">這些工具提供另一個方法，使用程式碼剖析 API。</span><span class="sxs-lookup"><span data-stu-id="93370-124">These tools provide an alternative approach to using the profiling API.</span></span>
