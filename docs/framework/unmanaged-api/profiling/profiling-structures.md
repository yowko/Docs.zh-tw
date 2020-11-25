---
title: 分析結構
ms.date: 03/30/2017
helpviewer_keywords:
- profiling structures [.NET Framework]
- unmanaged structures [.NET Framework], profiling
- structures [.NET Framework profiling]
ms.assetid: 750385f2-f365-41b1-939f-ca2f2ff9b466
ms.openlocfilehash: 3f832850fac918a568d02e9ef2f1e5b140ffc04f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722748"
---
# <a name="profiling-structures"></a><span data-ttu-id="38cec-102">分析結構</span><span class="sxs-lookup"><span data-stu-id="38cec-102">Profiling Structures</span></span>

<span data-ttu-id="38cec-103">本節說明分析 API 所使用的 Unmanaged 結構。</span><span class="sxs-lookup"><span data-stu-id="38cec-103">This section describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="38cec-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="38cec-104">In This Section</span></span>  

 [<span data-ttu-id="38cec-105">COR_PRF_ASSEMBLY_REFERENCE_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="38cec-105">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](cor-prf-assembly-reference-info-structure.md)  
 <span data-ttu-id="38cec-106">提供在執行組件參考結束查核時，所應考量的參考組件相關資訊給通用語言執行平台。</span><span class="sxs-lookup"><span data-stu-id="38cec-106">Provides the common language runtime with information about a reference assembly that it should consider when performing an assembly reference closure walk.</span></span>  
  
 [<span data-ttu-id="38cec-107">COR_PRF_CODE_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="38cec-107">COR_PRF_CODE_INFO Structure</span></span>](cor-prf-code-info-structure.md)  
 <span data-ttu-id="38cec-108">代表儲存在記憶體中的一個機器碼連續區塊。</span><span class="sxs-lookup"><span data-stu-id="38cec-108">Represents one contiguous block of native code stored in memory.</span></span>  
  
 [<span data-ttu-id="38cec-109">COR_PRF_EX_CLAUSE_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="38cec-109">COR_PRF_EX_CLAUSE_INFO Structure</span></span>](cor-prf-ex-clause-info-structure.md)  
 <span data-ttu-id="38cec-110">儲存特定例外狀況子句執行個體及其關聯框架的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="38cec-110">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
 [<span data-ttu-id="38cec-111">COR_PRF_FUNCTION 結構</span><span class="sxs-lookup"><span data-stu-id="38cec-111">COR_PRF_FUNCTION Structure</span></span>](cor-prf-function-structure.md)  
 <span data-ttu-id="38cec-112">將其 ID 與其重新編譯版本的 ID 合併在一起，以提供函式的唯一表示法。</span><span class="sxs-lookup"><span data-stu-id="38cec-112">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
 [<span data-ttu-id="38cec-113">COR_PRF_FUNCTION_ARGUMENT_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="38cec-113">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>](cor-prf-function-argument-info-structure.md)  
 <span data-ttu-id="38cec-114">代表函式的引數，順序由左至右。</span><span class="sxs-lookup"><span data-stu-id="38cec-114">Represents a function's arguments, in left-to-right order.</span></span>  
  
 [<span data-ttu-id="38cec-115">COR_PRF_FUNCTION_ARGUMENT_RANGE 結構</span><span class="sxs-lookup"><span data-stu-id="38cec-115">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>](cor-prf-function-argument-range-structure.md)  
 <span data-ttu-id="38cec-116">代表記憶體中由左至右連續儲存的函式引數區塊。</span><span class="sxs-lookup"><span data-stu-id="38cec-116">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
 [<span data-ttu-id="38cec-117">COR_PRF_GC_GENERATION_RANGE 結構</span><span class="sxs-lookup"><span data-stu-id="38cec-117">COR_PRF_GC_GENERATION_RANGE Structure</span></span>](cor-prf-gc-generation-range-structure.md)  
 <span data-ttu-id="38cec-118">說明正在進行記憶體回收的記憶體範圍 (亦即區塊)。</span><span class="sxs-lookup"><span data-stu-id="38cec-118">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="38cec-119">相關章節</span><span class="sxs-lookup"><span data-stu-id="38cec-119">Related Sections</span></span>  

 <span data-ttu-id="38cec-120">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="38cec-120">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
  
 <span data-ttu-id="38cec-121">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="38cec-121">COR_IL_MAP</span></span>  
  
 [<span data-ttu-id="38cec-122">分析概觀</span><span class="sxs-lookup"><span data-stu-id="38cec-122">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="38cec-123">分析介面</span><span class="sxs-lookup"><span data-stu-id="38cec-123">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="38cec-124">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="38cec-124">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="38cec-125">分析列舉</span><span class="sxs-lookup"><span data-stu-id="38cec-125">Profiling Enumerations</span></span>](profiling-enumerations.md)
