---
title: ICorProfilerFunctionEnum::Skip 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
- ICorProfilerFunctionEnum::Skip method [.NET Framework profiling]
ms.assetid: 051465b9-e479-494a-804b-c880323b4cbe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0e334c75afee60591db2b4e1f45cf0ec753ee2e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141644"
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="84a76-102">ICorProfilerFunctionEnum::Skip 方法</span><span class="sxs-lookup"><span data-stu-id="84a76-102">ICorProfilerFunctionEnum::Skip Method</span></span>
<span data-ttu-id="84a76-103">將列舉值的資料指標從其目前位置前移，以略過指定數目的項目。</span><span class="sxs-lookup"><span data-stu-id="84a76-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84a76-104">語法</span><span class="sxs-lookup"><span data-stu-id="84a76-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84a76-105">參數</span><span class="sxs-lookup"><span data-stu-id="84a76-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="84a76-106">[in]略過的項目數目。</span><span class="sxs-lookup"><span data-stu-id="84a76-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84a76-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="84a76-107">Return Value</span></span>  
 <span data-ttu-id="84a76-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="84a76-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="84a76-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="84a76-109">HRESULT</span></span>|<span data-ttu-id="84a76-110">描述</span><span class="sxs-lookup"><span data-stu-id="84a76-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="84a76-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="84a76-111">S_OK</span></span>|`celt` <span data-ttu-id="84a76-112">已略過項目。</span><span class="sxs-lookup"><span data-stu-id="84a76-112">elements were skipped.</span></span>|  
|<span data-ttu-id="84a76-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="84a76-113">S_FALSE</span></span>|<span data-ttu-id="84a76-114">少於`celt`項目已略過，這表示為沒有多個項目。</span><span class="sxs-lookup"><span data-stu-id="84a76-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84a76-115">備註</span><span class="sxs-lookup"><span data-stu-id="84a76-115">Remarks</span></span>  
 <span data-ttu-id="84a76-116">此列舉值的資料指標的新位置是 （目前的位置） + `celt`。</span><span class="sxs-lookup"><span data-stu-id="84a76-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84a76-117">需求</span><span class="sxs-lookup"><span data-stu-id="84a76-117">Requirements</span></span>  
 <span data-ttu-id="84a76-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="84a76-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84a76-119">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="84a76-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="84a76-120">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84a76-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="84a76-121">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="84a76-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="84a76-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84a76-122">See also</span></span>

- [<span data-ttu-id="84a76-123">ICorProfilerFunctionEnum 介面</span><span class="sxs-lookup"><span data-stu-id="84a76-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="84a76-124">分析介面</span><span class="sxs-lookup"><span data-stu-id="84a76-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
