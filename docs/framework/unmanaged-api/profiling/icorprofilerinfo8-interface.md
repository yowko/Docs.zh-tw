---
title: ICorProfilerInfo8 介面
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 2cca915eda44d73aea7469e5f752c57309c2300d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495160"
---
# <a name="icorprofilerinfo8-interface"></a><span data-ttu-id="5e7a4-102">ICorProfilerInfo8 介面</span><span class="sxs-lookup"><span data-stu-id="5e7a4-102">ICorProfilerInfo8 Interface</span></span>

<span data-ttu-id="5e7a4-103">[ICorProfilerInfo7](icorprofilerinfo7-interface.md)的子類別，提供方法來查詢動態方法的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5e7a4-103">A subclass of [ICorProfilerInfo7](icorprofilerinfo7-interface.md) that provides methods to query information about dynamic methods.</span></span>

## <a name="methods"></a><span data-ttu-id="5e7a4-104">方法</span><span class="sxs-lookup"><span data-stu-id="5e7a4-104">Methods</span></span>  

| <span data-ttu-id="5e7a4-105">方法</span><span class="sxs-lookup"><span data-stu-id="5e7a4-105">Method</span></span>|<span data-ttu-id="5e7a4-106">描述</span><span class="sxs-lookup"><span data-stu-id="5e7a4-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="5e7a4-107">IsFunctionDynamic 方法</span><span class="sxs-lookup"><span data-stu-id="5e7a4-107">IsFunctionDynamic Method</span></span>](icorprofilerinfo8-isfunctiondynamic-method.md)| <span data-ttu-id="5e7a4-108">判斷函數是否沒有相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="5e7a4-108">Determines if a function does not have associated metadata.</span></span>|
|[<span data-ttu-id="5e7a4-109">GetFunctionFromIP3 方法</span><span class="sxs-lookup"><span data-stu-id="5e7a4-109">GetFunctionFromIP3 Method</span></span>](icorprofilerinfo8-getfunctionfromip3-method.md)| <span data-ttu-id="5e7a4-110">將 managed 程式碼指令指標對應至 FunctionID。</span><span class="sxs-lookup"><span data-stu-id="5e7a4-110">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="5e7a4-111">這個方法適用于動態和非動態方法。</span><span class="sxs-lookup"><span data-stu-id="5e7a4-111">This method works for both dynamic and non-dynamic methods.</span></span> |
|[<span data-ttu-id="5e7a4-112">GetDynamicFunctionInfo 方法</span><span class="sxs-lookup"><span data-stu-id="5e7a4-112">GetDynamicFunctionInfo Method</span></span>](icorprofilerinfo8-getdynamicfunctioninfo-method.md)| <span data-ttu-id="5e7a4-113">抓取動態方法的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5e7a4-113">Retrieves information about dynamic methods.</span></span> |

## <a name="requirements"></a><span data-ttu-id="5e7a4-114">規格需求</span><span class="sxs-lookup"><span data-stu-id="5e7a4-114">Requirements</span></span>  
<span data-ttu-id="5e7a4-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5e7a4-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="5e7a4-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5e7a4-116">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="5e7a4-117">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5e7a4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="5e7a4-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e7a4-118">See also</span></span>

- [<span data-ttu-id="5e7a4-119">分析介面</span><span class="sxs-lookup"><span data-stu-id="5e7a4-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
