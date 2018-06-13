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
ms.openlocfilehash: 61014e067b2afb8b7e4be0488ed6a3c7f1bd6fc4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420696"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="6c75b-102">ICorDebugVariableHome::GetSlotIndex 方法</span><span class="sxs-lookup"><span data-stu-id="6c75b-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="6c75b-103">取得區域變數的 managed 的位置索引。</span><span class="sxs-lookup"><span data-stu-id="6c75b-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c75b-104">語法</span><span class="sxs-lookup"><span data-stu-id="6c75b-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c75b-105">參數</span><span class="sxs-lookup"><span data-stu-id="6c75b-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="6c75b-106">[out]區域變數位置索引指標。</span><span class="sxs-lookup"><span data-stu-id="6c75b-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c75b-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="6c75b-107">Return Value</span></span>  
 <span data-ttu-id="6c75b-108">方法會傳回下列值。</span><span class="sxs-lookup"><span data-stu-id="6c75b-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="6c75b-109">值</span><span class="sxs-lookup"><span data-stu-id="6c75b-109">Value</span></span>|<span data-ttu-id="6c75b-110">描述</span><span class="sxs-lookup"><span data-stu-id="6c75b-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="6c75b-111">方法呼叫傳回中的位置索引值`pSlotIndex`。</span><span class="sxs-lookup"><span data-stu-id="6c75b-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="6c75b-112">目前[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)的執行個體表示的函式引數。</span><span class="sxs-lookup"><span data-stu-id="6c75b-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c75b-113">備註</span><span class="sxs-lookup"><span data-stu-id="6c75b-113">Remarks</span></span>  
 <span data-ttu-id="6c75b-114">位置索引可用來擷取這個本機變數的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6c75b-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c75b-115">需求</span><span class="sxs-lookup"><span data-stu-id="6c75b-115">Requirements</span></span>  
 <span data-ttu-id="6c75b-116">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6c75b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c75b-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c75b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c75b-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c75b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c75b-119">**.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c75b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c75b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c75b-120">See Also</span></span>  
 [<span data-ttu-id="6c75b-121">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="6c75b-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
