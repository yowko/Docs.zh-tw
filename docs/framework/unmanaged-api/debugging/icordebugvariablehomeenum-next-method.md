---
title: ICorDebugVariableHomeEnum::Next 方法
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d5ab18d6c2ae8bbf47a3bcd7cb892530be4f8f4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421580"
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="f62c6-102">ICorDebugVariableHomeEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="f62c6-102">ICorDebugVariableHomeEnum::Next Method</span></span>
<span data-ttu-id="f62c6-103">取得指定的數目[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)包含本機變數和引數的函式中的相關資訊的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f62c6-103">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f62c6-104">語法</span><span class="sxs-lookup"><span data-stu-id="f62c6-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f62c6-105">參數</span><span class="sxs-lookup"><span data-stu-id="f62c6-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f62c6-106">[in] 要擷取的物件數目。</span><span class="sxs-lookup"><span data-stu-id="f62c6-106">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="f62c6-107">陣列的指標，其中每個指向[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)提供本機變數或函式的引數的相關資訊的物件。</span><span class="sxs-lookup"><span data-stu-id="f62c6-107">An array of pointers, each of which points to a [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f62c6-108">[out]物件中實際傳回的執行個體數目。</span><span class="sxs-lookup"><span data-stu-id="f62c6-108">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f62c6-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="f62c6-109">Return Value</span></span>  
 <span data-ttu-id="f62c6-110">方法會傳回下列值。</span><span class="sxs-lookup"><span data-stu-id="f62c6-110">The method returns the following values.</span></span>  
  
|<span data-ttu-id="f62c6-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f62c6-111">HRESULT</span></span>|<span data-ttu-id="f62c6-112">描述</span><span class="sxs-lookup"><span data-stu-id="f62c6-112">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f62c6-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="f62c6-113">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f62c6-114">擷取執行個體的實際數目，如中所反映`pceltFetched`，小於要求的執行個體數目。</span><span class="sxs-lookup"><span data-stu-id="f62c6-114">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f62c6-115">備註</span><span class="sxs-lookup"><span data-stu-id="f62c6-115">Remarks</span></span>  
 <span data-ttu-id="f62c6-116">[ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)方法會擷取最多`celt`物件列舉值的目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="f62c6-116">The [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="f62c6-117">方法傳回時，`pceltFetched`包含實際的擷取的物件數目。</span><span class="sxs-lookup"><span data-stu-id="f62c6-117">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f62c6-118">需求</span><span class="sxs-lookup"><span data-stu-id="f62c6-118">Requirements</span></span>  
 <span data-ttu-id="f62c6-119">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f62c6-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f62c6-120">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f62c6-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f62c6-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f62c6-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f62c6-122">**.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f62c6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f62c6-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f62c6-123">See Also</span></span>  
 [<span data-ttu-id="f62c6-124">ICorDebugVariableHomeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="f62c6-124">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 [<span data-ttu-id="f62c6-125">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="f62c6-125">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
