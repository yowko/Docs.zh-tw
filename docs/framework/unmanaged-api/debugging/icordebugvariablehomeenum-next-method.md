---
title: ICorDebugVariableHomeEnum：： Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type:
- apiref
ms.openlocfilehash: 9c2c16789fb61099c9b7c58154810739d225af1f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121927"
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="dd9dc-102">ICorDebugVariableHomeEnum：： Next 方法</span><span class="sxs-lookup"><span data-stu-id="dd9dc-102">ICorDebugVariableHomeEnum::Next Method</span></span>
<span data-ttu-id="dd9dc-103">取得指定的[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)實例數目，其中包含函式中區域變數和引數的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="dd9dc-103">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd9dc-104">語法</span><span class="sxs-lookup"><span data-stu-id="dd9dc-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd9dc-105">參數</span><span class="sxs-lookup"><span data-stu-id="dd9dc-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="dd9dc-106">[in] 要擷取的物件數目。</span><span class="sxs-lookup"><span data-stu-id="dd9dc-106">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="dd9dc-107">指標的陣列，其中每一個都會指向一個[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)物件，它會提供有關函數的區域變數或引數的資訊。</span><span class="sxs-lookup"><span data-stu-id="dd9dc-107">An array of pointers, each of which points to a [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="dd9dc-108">脫銷物件中實際傳回的實例數目。</span><span class="sxs-lookup"><span data-stu-id="dd9dc-108">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd9dc-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="dd9dc-109">Return Value</span></span>  
 <span data-ttu-id="dd9dc-110">方法會傳回下列值。</span><span class="sxs-lookup"><span data-stu-id="dd9dc-110">The method returns the following values.</span></span>  
  
|<span data-ttu-id="dd9dc-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dd9dc-111">HRESULT</span></span>|<span data-ttu-id="dd9dc-112">描述</span><span class="sxs-lookup"><span data-stu-id="dd9dc-112">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="dd9dc-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="dd9dc-113">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="dd9dc-114">如 `pceltFetched`所反映的實際實例數目，小於所要求的實例數目。</span><span class="sxs-lookup"><span data-stu-id="dd9dc-114">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd9dc-115">備註</span><span class="sxs-lookup"><span data-stu-id="dd9dc-115">Remarks</span></span>  
 <span data-ttu-id="dd9dc-116">[ICorDebugVariableHomeEnum：： Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)方法會從列舉值的目前位置開始，抓取 `celt` 物件的上限。</span><span class="sxs-lookup"><span data-stu-id="dd9dc-116">The [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="dd9dc-117">當此方法傳回時，`pceltFetched` 包含所抓取物件的實際數目。</span><span class="sxs-lookup"><span data-stu-id="dd9dc-117">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd9dc-118">需求</span><span class="sxs-lookup"><span data-stu-id="dd9dc-118">Requirements</span></span>  
 <span data-ttu-id="dd9dc-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dd9dc-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd9dc-120">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dd9dc-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd9dc-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd9dc-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd9dc-122">**.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd9dc-122">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd9dc-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="dd9dc-123">See also</span></span>

- [<span data-ttu-id="dd9dc-124">ICorDebugVariableHomeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="dd9dc-124">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
- [<span data-ttu-id="dd9dc-125">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="dd9dc-125">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
