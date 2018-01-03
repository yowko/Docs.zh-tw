---
title: "ICorDebugVariableHome::GetSlotIndex 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetSlotIndex
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ff62b79fbbb0896941730797473209872e6bfc2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="cc561-102">ICorDebugVariableHome::GetSlotIndex 方法</span><span class="sxs-lookup"><span data-stu-id="cc561-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="cc561-103">取得區域變數的 managed 的位置索引。</span><span class="sxs-lookup"><span data-stu-id="cc561-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc561-104">語法</span><span class="sxs-lookup"><span data-stu-id="cc561-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cc561-105">參數</span><span class="sxs-lookup"><span data-stu-id="cc561-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="cc561-106">[out]區域變數位置索引指標。</span><span class="sxs-lookup"><span data-stu-id="cc561-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc561-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="cc561-107">Return Value</span></span>  
 <span data-ttu-id="cc561-108">方法會傳回下列值。</span><span class="sxs-lookup"><span data-stu-id="cc561-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="cc561-109">值</span><span class="sxs-lookup"><span data-stu-id="cc561-109">Value</span></span>|<span data-ttu-id="cc561-110">描述</span><span class="sxs-lookup"><span data-stu-id="cc561-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="cc561-111">方法呼叫傳回中的位置索引值`pSlotIndex`。</span><span class="sxs-lookup"><span data-stu-id="cc561-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="cc561-112">目前[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)的執行個體表示的函式引數。</span><span class="sxs-lookup"><span data-stu-id="cc561-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc561-113">備註</span><span class="sxs-lookup"><span data-stu-id="cc561-113">Remarks</span></span>  
 <span data-ttu-id="cc561-114">位置索引可用來擷取這個本機變數的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="cc561-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc561-115">需求</span><span class="sxs-lookup"><span data-stu-id="cc561-115">Requirements</span></span>  
 <span data-ttu-id="cc561-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cc561-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc561-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc561-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc561-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc561-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc561-119">**.NET framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc561-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc561-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="cc561-120">See Also</span></span>  
 [<span data-ttu-id="cc561-121">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="cc561-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
