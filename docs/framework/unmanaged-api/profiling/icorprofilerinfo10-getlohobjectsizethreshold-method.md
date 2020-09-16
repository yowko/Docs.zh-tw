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
ms.openlocfilehash: 280f0a401f87f81e1ef9d4a2c85c06599442b5ec
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543942"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="2a85a-102">ICorProfilerInfo10：： GetLOHObjectSizeThreshold 方法</span><span class="sxs-lookup"><span data-stu-id="2a85a-102">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>

<span data-ttu-id="2a85a-103">取得已設定之大型物件堆積 (LOH) 臨界值的值。</span><span class="sxs-lookup"><span data-stu-id="2a85a-103">Gets the value of the configured large object heap (LOH) threshold.</span></span>

## <a name="syntax"></a><span data-ttu-id="2a85a-104">語法</span><span class="sxs-lookup"><span data-stu-id="2a85a-104">Syntax</span></span>

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a><span data-ttu-id="2a85a-105">參數</span><span class="sxs-lookup"><span data-stu-id="2a85a-105">Parameters</span></span>

- `pThreshold`

  <span data-ttu-id="2a85a-106">\[out）大型物件堆積閾值（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="2a85a-106">\[out] The large object heap threshold in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="2a85a-107">備註</span><span class="sxs-lookup"><span data-stu-id="2a85a-107">Remarks</span></span>

<span data-ttu-id="2a85a-108">大於大型物件堆積閾值的物件將會配置在大型物件堆積上。</span><span class="sxs-lookup"><span data-stu-id="2a85a-108">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="2a85a-109">從 .NET Core 3.0 開始，可以設定大型物件堆積閾值，其中 `pThreshold` 將包含使用中的大型物件堆積閾值大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="2a85a-109">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="2a85a-110">需求</span><span class="sxs-lookup"><span data-stu-id="2a85a-110">Requirements</span></span>

<span data-ttu-id="2a85a-111">**平臺：** 請參閱 [.Net Core 支援的作業系統](../../../core/install/windows.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="2a85a-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="2a85a-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2a85a-112">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="2a85a-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a85a-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="2a85a-114">**.Net 版本：**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a85a-114">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="2a85a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a85a-115">See also</span></span>

- [<span data-ttu-id="2a85a-116">ICorProfilerInfo10 介面</span><span class="sxs-lookup"><span data-stu-id="2a85a-116">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
