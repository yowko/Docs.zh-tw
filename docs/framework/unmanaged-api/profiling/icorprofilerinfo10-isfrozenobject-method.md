---
title: ICorProfilerInfo10::IsFrozenObject
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.IsFrozenObject
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: b6dabefceba038a129148f7ba36d4ffcfc425c80
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790030"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="7da6c-102">ICorProfilerInfo10：： IsFrozenObject 方法</span><span class="sxs-lookup"><span data-stu-id="7da6c-102">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="7da6c-103">給定 ObjectID，判斷物件是否在唯讀區段中。</span><span class="sxs-lookup"><span data-stu-id="7da6c-103">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="7da6c-104">語法</span><span class="sxs-lookup"><span data-stu-id="7da6c-104">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a><span data-ttu-id="7da6c-105">參數</span><span class="sxs-lookup"><span data-stu-id="7da6c-105">Parameters</span></span>

- `objectId`

  <span data-ttu-id="7da6c-106">中的 \[] 要檢查的物件。</span><span class="sxs-lookup"><span data-stu-id="7da6c-106">\[in] The object to examine.</span></span>

- `pbFrozen`

  <span data-ttu-id="7da6c-107">\[out] `BOOL`，指出物件是否在唯讀區段中。</span><span class="sxs-lookup"><span data-stu-id="7da6c-107">\[out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="7da6c-108">需求</span><span class="sxs-lookup"><span data-stu-id="7da6c-108">Requirements</span></span>

<span data-ttu-id="7da6c-109">**平臺：** 請參閱[.Net Core 支援的作業系統](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="7da6c-109">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="7da6c-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7da6c-110">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="7da6c-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7da6c-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="7da6c-112">**.Net 版本：** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7da6c-112">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="7da6c-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="7da6c-113">See also</span></span>

- [<span data-ttu-id="7da6c-114">ICorProfilerInfo10 介面</span><span class="sxs-lookup"><span data-stu-id="7da6c-114">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
