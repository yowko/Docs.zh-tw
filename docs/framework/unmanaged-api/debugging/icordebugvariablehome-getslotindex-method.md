---
title: ICorDebugVariableHome::GetSlotIndex 方法
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetSlotIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b819f1f02870a8a85a531d7d341cbaf488a1ccd6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993664"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="5f2fe-102">ICorDebugVariableHome::GetSlotIndex 方法</span><span class="sxs-lookup"><span data-stu-id="5f2fe-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="5f2fe-103">取得區域變數的 managed 的位置索引。</span><span class="sxs-lookup"><span data-stu-id="5f2fe-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f2fe-104">語法</span><span class="sxs-lookup"><span data-stu-id="5f2fe-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f2fe-105">參數</span><span class="sxs-lookup"><span data-stu-id="5f2fe-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="5f2fe-106">[out]區域變數位置索引指標。</span><span class="sxs-lookup"><span data-stu-id="5f2fe-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f2fe-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="5f2fe-107">Return Value</span></span>  
 <span data-ttu-id="5f2fe-108">方法會傳回下列值。</span><span class="sxs-lookup"><span data-stu-id="5f2fe-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="5f2fe-109">值</span><span class="sxs-lookup"><span data-stu-id="5f2fe-109">Value</span></span>|<span data-ttu-id="5f2fe-110">描述</span><span class="sxs-lookup"><span data-stu-id="5f2fe-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="5f2fe-111">方法呼叫傳回的位置索引值`pSlotIndex`。</span><span class="sxs-lookup"><span data-stu-id="5f2fe-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="5f2fe-112">目前[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)執行個體代表的函式引數。</span><span class="sxs-lookup"><span data-stu-id="5f2fe-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f2fe-113">備註</span><span class="sxs-lookup"><span data-stu-id="5f2fe-113">Remarks</span></span>  
 <span data-ttu-id="5f2fe-114">位置索引可用來擷取這個區域變數的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="5f2fe-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f2fe-115">需求</span><span class="sxs-lookup"><span data-stu-id="5f2fe-115">Requirements</span></span>  
 <span data-ttu-id="5f2fe-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5f2fe-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f2fe-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5f2fe-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f2fe-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f2fe-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f2fe-119">**.NET framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f2fe-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f2fe-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f2fe-120">See also</span></span>

- [<span data-ttu-id="5f2fe-121">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="5f2fe-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
