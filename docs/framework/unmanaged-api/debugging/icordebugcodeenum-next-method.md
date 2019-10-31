---
title: ICorDebugCodeEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type:
- apiref
ms.openlocfilehash: 04c36d1e5f0e79b71963683a3b613a9ad7392bcf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125531"
---
# <a name="icordebugcodeenumnext-method"></a><span data-ttu-id="20a86-102">ICorDebugCodeEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="20a86-102">ICorDebugCodeEnum::Next Method</span></span>

<span data-ttu-id="20a86-103">從列舉中取得指定數目的 "ICorDebugCode" 實例，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="20a86-103">Gets the specified number of "ICorDebugCode" instances from the enumeration, starting at the current position.</span></span>

## <a name="syntax"></a><span data-ttu-id="20a86-104">語法</span><span class="sxs-lookup"><span data-stu-id="20a86-104">Syntax</span></span>

```cpp
HRESULT Next (
    [in] ULONG  celt,
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorDebugCode *values[],
    [out] ULONG *pceltFetched
);
```

## <a name="parameters"></a><span data-ttu-id="20a86-105">參數</span><span class="sxs-lookup"><span data-stu-id="20a86-105">Parameters</span></span>

`celt`  
<span data-ttu-id="20a86-106">在要抓取 `ICorDebugCode` 實例的數目。</span><span class="sxs-lookup"><span data-stu-id="20a86-106">[in] The number of `ICorDebugCode` instances to be retrieved.</span></span>

`values`  
<span data-ttu-id="20a86-107">脫銷指標陣列，其中每一個都會指向 `ICorDebugCode` 物件。</span><span class="sxs-lookup"><span data-stu-id="20a86-107">[out] An array of pointers, each of which points to an `ICorDebugCode` object.</span></span>

`pceltFetched`  
<span data-ttu-id="20a86-108">脫銷實際傳回的 `ICorDebugCode` 實例數目的指標。</span><span class="sxs-lookup"><span data-stu-id="20a86-108">[out] A pointer to the number of `ICorDebugCode` instances actually returned.</span></span> <span data-ttu-id="20a86-109">如果 `celt` 是一個，這個值可能會是 null。</span><span class="sxs-lookup"><span data-stu-id="20a86-109">This value may be null if `celt` is one.</span></span>

## <a name="requirements"></a><span data-ttu-id="20a86-110">需求</span><span class="sxs-lookup"><span data-stu-id="20a86-110">Requirements</span></span>

<span data-ttu-id="20a86-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="20a86-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="20a86-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20a86-112">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="20a86-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20a86-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="20a86-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20a86-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
