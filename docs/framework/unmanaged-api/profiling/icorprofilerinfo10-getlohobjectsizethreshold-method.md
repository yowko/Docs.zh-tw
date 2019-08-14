---
title: ICorProfilerInfo10::GetLOHObjectSizeThreshold
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.GetLOHObjectSizeThreshold
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: d6b6575cf04635b40b504b11bc415f61f05b4205
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68974018"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="fd4d4-102">ICorProfilerInfo10:: GetLOHObjectSizeThreshold 方法</span><span class="sxs-lookup"><span data-stu-id="fd4d4-102">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>
  
 <span data-ttu-id="fd4d4-103">取得已設定的大型物件堆積 (LOH) 閾值的值。</span><span class="sxs-lookup"><span data-stu-id="fd4d4-103">Gets the value of the configured large object heap (LOH) threshold.</span></span>   
  
## <a name="syntax"></a><span data-ttu-id="fd4d4-104">語法</span><span class="sxs-lookup"><span data-stu-id="fd4d4-104">Syntax</span></span>  
  
```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```  
  
#### <a name="parameters"></a><span data-ttu-id="fd4d4-105">參數</span><span class="sxs-lookup"><span data-stu-id="fd4d4-105">Parameters</span></span>  
 `pThreshold` \
 <span data-ttu-id="fd4d4-106">脫銷大型物件堆積閾值 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="fd4d4-106">[out] The large object heap threshold in bytes.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="fd4d4-107">備註</span><span class="sxs-lookup"><span data-stu-id="fd4d4-107">Remarks</span></span>  
 <span data-ttu-id="fd4d4-108">大於大型物件堆積閾值的物件將會配置在大型物件堆積上。</span><span class="sxs-lookup"><span data-stu-id="fd4d4-108">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="fd4d4-109">從 .net Core 3.0 開始, 大型物件堆積閾值是可設定`pThreshold`的, 它會包含作用中的大型物件堆積閾值大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="fd4d4-109">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="fd4d4-110">需求</span><span class="sxs-lookup"><span data-stu-id="fd4d4-110">Requirements</span></span>  
 <span data-ttu-id="fd4d4-111">**平台：** 請參閱[.Net Core 支援的作業系統](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)。</span><span class="sxs-lookup"><span data-stu-id="fd4d4-111">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="fd4d4-112">**標頭：** Corprof.idl .idl, Corprof.idl。h</span><span class="sxs-lookup"><span data-stu-id="fd4d4-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fd4d4-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd4d4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd4d4-114">**.Net 版本:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd4d4-114">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fd4d4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd4d4-115">See also</span></span>
- [<span data-ttu-id="fd4d4-116">ICorProfilerInfo10 介面</span><span class="sxs-lookup"><span data-stu-id="fd4d4-116">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)

