---
title: ICorDebugTypeEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugTypeEnum::Next
helpviewer_keywords:
- ICorDebugTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugTypeEnum interface [.NET Framework debugging]
ms.assetid: d0fdeba3-c195-4ece-8caf-79b1f40025d2
topic_type:
- apiref
ms.openlocfilehash: fc205e347fc39fd486d9b8a3fb256a5d29a980a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110057"
---
# <a name="icordebugtypeenumnext-method"></a><span data-ttu-id="36c56-102">ICorDebugTypeEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="36c56-102">ICorDebugTypeEnum::Next Method</span></span>
<span data-ttu-id="36c56-103">從目前位置開始，取得列舉中 `celt` 所指定的 "ICorDebugType" 實例數目。</span><span class="sxs-lookup"><span data-stu-id="36c56-103">Gets the number of "ICorDebugType" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36c56-104">語法</span><span class="sxs-lookup"><span data-stu-id="36c56-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugType *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36c56-105">參數</span><span class="sxs-lookup"><span data-stu-id="36c56-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="36c56-106">在要抓取 `ICorDebugType` 實例的數目。</span><span class="sxs-lookup"><span data-stu-id="36c56-106">[in] The number of `ICorDebugType` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="36c56-107">脫銷指標陣列，其中每一個都會指向 `ICorDebugType` 物件。</span><span class="sxs-lookup"><span data-stu-id="36c56-107">[out] An array of pointers, each of which points to an `ICorDebugType` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="36c56-108">脫銷實際傳回的 `ICorDebugType` 實例數目的指標。</span><span class="sxs-lookup"><span data-stu-id="36c56-108">[out] Pointer to the number of `ICorDebugType` instances actually returned.</span></span> <span data-ttu-id="36c56-109">如果 `celt` 是一個，這個值可能會是 null。</span><span class="sxs-lookup"><span data-stu-id="36c56-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36c56-110">需求</span><span class="sxs-lookup"><span data-stu-id="36c56-110">Requirements</span></span>  
 <span data-ttu-id="36c56-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="36c56-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36c56-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36c56-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36c56-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36c56-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36c56-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36c56-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36c56-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="36c56-115">See also</span></span>
