---
title: ICorDebugExceptionObjectValue::EnumerateExceptionCallStack 方法
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue.EnumerateExceptionCallStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
helpviewer_keywords:
- EnumerateExceptionCallStack method, ICorDebugExceptionObjectValue interface [.NET Framework debugging]
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack method [.NET Framework debugging]
ms.assetid: 00c64533-15dd-47f4-bb97-fe80a1ebadef
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db0e794953578fccd08428b730b3d7951e13bee3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074075"
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="e0f9a-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack 方法</span><span class="sxs-lookup"><span data-stu-id="e0f9a-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>
<span data-ttu-id="e0f9a-103">取得列舉值例外狀況物件中內嵌的呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="e0f9a-103">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0f9a-104">語法</span><span class="sxs-lookup"><span data-stu-id="e0f9a-104">Syntax</span></span>  
  
```  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0f9a-105">參數</span><span class="sxs-lookup"><span data-stu-id="e0f9a-105">Parameters</span></span>  
 <span data-ttu-id="e0f9a-106">ppCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="e0f9a-106">ppCallStackEnum</span></span>  
 <span data-ttu-id="e0f9a-107">[out]位址指標[ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)介面物件的 managed 例外狀況物件的堆疊追蹤列舉值。</span><span class="sxs-lookup"><span data-stu-id="e0f9a-107">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0f9a-108">備註</span><span class="sxs-lookup"><span data-stu-id="e0f9a-108">Remarks</span></span>  
 <span data-ttu-id="e0f9a-109">如果沒有呼叫堆疊資訊可用，此方法會傳回`S_OK`，並[ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)是有效的列舉值，長度為 0。</span><span class="sxs-lookup"><span data-stu-id="e0f9a-109">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="e0f9a-110">如果無法擷取堆疊追蹤資訊的方法，則傳回值是`E_FAIL`並傳回沒有列舉值。</span><span class="sxs-lookup"><span data-stu-id="e0f9a-110">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="e0f9a-111">[ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)物件會負責從堆疊追蹤資料解碼`_stackTrace`例外狀況物件的欄位。</span><span class="sxs-lookup"><span data-stu-id="e0f9a-111">The [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0f9a-112">需求</span><span class="sxs-lookup"><span data-stu-id="e0f9a-112">Requirements</span></span>  
 <span data-ttu-id="e0f9a-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e0f9a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0f9a-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0f9a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0f9a-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0f9a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0f9a-116">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0f9a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0f9a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0f9a-117">See also</span></span>

- [<span data-ttu-id="e0f9a-118">ICorDebugExceptionObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="e0f9a-118">ICorDebugExceptionObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)
- [<span data-ttu-id="e0f9a-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e0f9a-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
