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
ms.openlocfilehash: d212c06c7ddc9f22095c0b95f19fd1083482435c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69661227"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="5ab8e-102">ICorProfilerInfo10:: IsFrozenObject 方法</span><span class="sxs-lookup"><span data-stu-id="5ab8e-102">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="5ab8e-103">給定 ObjectID, 判斷物件是否在唯讀區段中。</span><span class="sxs-lookup"><span data-stu-id="5ab8e-103">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="5ab8e-104">語法</span><span class="sxs-lookup"><span data-stu-id="5ab8e-104">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

#### <a name="parameters"></a><span data-ttu-id="5ab8e-105">參數</span><span class="sxs-lookup"><span data-stu-id="5ab8e-105">Parameters</span></span>

`objectId` \
<span data-ttu-id="5ab8e-106">在要檢查的物件。</span><span class="sxs-lookup"><span data-stu-id="5ab8e-106">[in] The object to examine.</span></span>

`pbFrozen` \
<span data-ttu-id="5ab8e-107">脫銷`BOOL` , 指出物件是否在唯讀區段中。</span><span class="sxs-lookup"><span data-stu-id="5ab8e-107">[out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="5ab8e-108">需求</span><span class="sxs-lookup"><span data-stu-id="5ab8e-108">Requirements</span></span>

<span data-ttu-id="5ab8e-109">**平台：** 請參閱[.Net Core 支援的作業系統](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)。</span><span class="sxs-lookup"><span data-stu-id="5ab8e-109">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>

<span data-ttu-id="5ab8e-110">**標頭：** Corprof.idl .idl, Corprof.idl。h</span><span class="sxs-lookup"><span data-stu-id="5ab8e-110">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="5ab8e-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ab8e-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="5ab8e-112">**.Net 版本:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ab8e-112">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5ab8e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ab8e-113">See also</span></span>

- [<span data-ttu-id="5ab8e-114">ICorProfilerInfo10 介面</span><span class="sxs-lookup"><span data-stu-id="5ab8e-114">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
