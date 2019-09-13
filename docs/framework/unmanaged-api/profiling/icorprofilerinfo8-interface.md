---
title: ICorProfilerInfo8 介面
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 2baa33a7a3527392d8095b5d0ec7ad6af8a71a8e
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928928"
---
# <a name="icorprofilerinfo8-interface"></a><span data-ttu-id="5c8db-102">ICorProfilerInfo8 介面</span><span class="sxs-lookup"><span data-stu-id="5c8db-102">ICorProfilerInfo8 Interface</span></span>

<span data-ttu-id="5c8db-103">[ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)的子類別，提供方法來查詢動態方法的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5c8db-103">A subclass of [ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) that provides methods to query information about dynamic methods.</span></span>

## <a name="methods"></a><span data-ttu-id="5c8db-104">方法</span><span class="sxs-lookup"><span data-stu-id="5c8db-104">Methods</span></span>  

| <span data-ttu-id="5c8db-105">方法</span><span class="sxs-lookup"><span data-stu-id="5c8db-105">Method</span></span>|<span data-ttu-id="5c8db-106">描述</span><span class="sxs-lookup"><span data-stu-id="5c8db-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="5c8db-107">IsFunctionDynamic 方法</span><span class="sxs-lookup"><span data-stu-id="5c8db-107">IsFunctionDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-isfunctiondynamic-method.md)| <span data-ttu-id="5c8db-108">判斷函數是否沒有相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="5c8db-108">Determines if a function does not have associated metadata.</span></span>|
|[<span data-ttu-id="5c8db-109">GetFunctionFromIP3 方法</span><span class="sxs-lookup"><span data-stu-id="5c8db-109">GetFunctionFromIP3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getfunctionfromip3-method.md)| <span data-ttu-id="5c8db-110">將 managed 程式碼指令指標對應至 FunctionID。</span><span class="sxs-lookup"><span data-stu-id="5c8db-110">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="5c8db-111">這個方法適用于動態和非動態方法。</span><span class="sxs-lookup"><span data-stu-id="5c8db-111">This method works for both dynamic and non-dynamic methods.</span></span> |
|[<span data-ttu-id="5c8db-112">GetDynamicFunctionInfo 方法</span><span class="sxs-lookup"><span data-stu-id="5c8db-112">GetDynamicFunctionInfo Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getdynamicfunctioninfo-method.md)| <span data-ttu-id="5c8db-113">抓取動態方法的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5c8db-113">Retrieves information about dynamic methods.</span></span> |

## <a name="requirements"></a><span data-ttu-id="5c8db-114">需求</span><span class="sxs-lookup"><span data-stu-id="5c8db-114">Requirements</span></span>  
<span data-ttu-id="5c8db-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5c8db-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="5c8db-116">**標頭：** Corprof.idl .idl，Corprof.idl。h</span><span class="sxs-lookup"><span data-stu-id="5c8db-116">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="5c8db-117">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5c8db-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="5c8db-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c8db-118">See also</span></span>

- [<span data-ttu-id="5c8db-119">分析介面</span><span class="sxs-lookup"><span data-stu-id="5c8db-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
