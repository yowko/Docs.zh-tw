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
ms.openlocfilehash: 8c9a85e9f00027f597795eea55a9bbb0364790f8
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69661232"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="c74ad-102">ICorProfilerInfo10:: GetLOHObjectSizeThreshold 方法</span><span class="sxs-lookup"><span data-stu-id="c74ad-102">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>

<span data-ttu-id="c74ad-103">取得已設定的大型物件堆積 (LOH) 閾值的值。</span><span class="sxs-lookup"><span data-stu-id="c74ad-103">Gets the value of the configured large object heap (LOH) threshold.</span></span>

## <a name="syntax"></a><span data-ttu-id="c74ad-104">語法</span><span class="sxs-lookup"><span data-stu-id="c74ad-104">Syntax</span></span>

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

#### <a name="parameters"></a><span data-ttu-id="c74ad-105">參數</span><span class="sxs-lookup"><span data-stu-id="c74ad-105">Parameters</span></span>

`pThreshold` \
<span data-ttu-id="c74ad-106">脫銷大型物件堆積閾值 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="c74ad-106">[out] The large object heap threshold in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="c74ad-107">備註</span><span class="sxs-lookup"><span data-stu-id="c74ad-107">Remarks</span></span>

<span data-ttu-id="c74ad-108">大於大型物件堆積閾值的物件將會配置在大型物件堆積上。</span><span class="sxs-lookup"><span data-stu-id="c74ad-108">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="c74ad-109">從 .net Core 3.0 開始, 大型物件堆積閾值是可設定`pThreshold`的, 它會包含作用中的大型物件堆積閾值大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="c74ad-109">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="c74ad-110">需求</span><span class="sxs-lookup"><span data-stu-id="c74ad-110">Requirements</span></span>

<span data-ttu-id="c74ad-111">**平台：** 請參閱[.Net Core 支援的作業系統](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)。</span><span class="sxs-lookup"><span data-stu-id="c74ad-111">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>

<span data-ttu-id="c74ad-112">**標頭：** Corprof.idl .idl, Corprof.idl。h</span><span class="sxs-lookup"><span data-stu-id="c74ad-112">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="c74ad-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c74ad-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="c74ad-114">**.Net 版本:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c74ad-114">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c74ad-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c74ad-115">See also</span></span>

- [<span data-ttu-id="c74ad-116">ICorProfilerInfo10 介面</span><span class="sxs-lookup"><span data-stu-id="c74ad-116">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
