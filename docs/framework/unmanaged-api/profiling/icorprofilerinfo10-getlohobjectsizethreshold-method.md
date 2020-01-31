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
ms.openlocfilehash: 95473a8ce8d5fd7540228ecd9767448e51b5b326
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868980"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="cdb22-102">ICorProfilerInfo10：： GetLOHObjectSizeThreshold 方法</span><span class="sxs-lookup"><span data-stu-id="cdb22-102">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>

<span data-ttu-id="cdb22-103">取得已設定的大型物件堆積（LOH）閾值的值。</span><span class="sxs-lookup"><span data-stu-id="cdb22-103">Gets the value of the configured large object heap (LOH) threshold.</span></span>

## <a name="syntax"></a><span data-ttu-id="cdb22-104">語法</span><span class="sxs-lookup"><span data-stu-id="cdb22-104">Syntax</span></span>

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a><span data-ttu-id="cdb22-105">參數</span><span class="sxs-lookup"><span data-stu-id="cdb22-105">Parameters</span></span>

- `pThreshold`

  <span data-ttu-id="cdb22-106">\[out] 大型物件堆積閾值（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="cdb22-106">\[out] The large object heap threshold in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="cdb22-107">備註</span><span class="sxs-lookup"><span data-stu-id="cdb22-107">Remarks</span></span>

<span data-ttu-id="cdb22-108">大於大型物件堆積閾值的物件將會配置在大型物件堆積上。</span><span class="sxs-lookup"><span data-stu-id="cdb22-108">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="cdb22-109">從 .NET Core 3.0 開始，可設定大型物件堆積閾值，`pThreshold` 將包含作用中的大型物件堆積閾值大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="cdb22-109">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="cdb22-110">需求</span><span class="sxs-lookup"><span data-stu-id="cdb22-110">Requirements</span></span>

<span data-ttu-id="cdb22-111">**平臺：** 請參閱[.Net Core 支援的作業系統](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="cdb22-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="cdb22-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cdb22-112">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="cdb22-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cdb22-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="cdb22-114">**.Net 版本：** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdb22-114">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="cdb22-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="cdb22-115">See also</span></span>

- [<span data-ttu-id="cdb22-116">ICorProfilerInfo10 介面</span><span class="sxs-lookup"><span data-stu-id="cdb22-116">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
