---
title: "ICorDebugExceptionObjectValue::EnumerateExceptionCallStack 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugExceptionObjectValue.EnumerateExceptionCallStack
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
helpviewer_keywords:
- EnumerateExceptionCallStack method, ICorDebugExceptionObjectValue interface [.NET Framework debugging]
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack method [.NET Framework debugging]
ms.assetid: 00c64533-15dd-47f4-bb97-fe80a1ebadef
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 861d2ad5f9ce0fcc11ea7b1743cd369235cbd878
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="e344a-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack 方法</span><span class="sxs-lookup"><span data-stu-id="e344a-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>
<span data-ttu-id="e344a-103">取得列舉值例外狀況物件中內嵌的呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="e344a-103">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e344a-104">語法</span><span class="sxs-lookup"><span data-stu-id="e344a-104">Syntax</span></span>  
  
```  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e344a-105">參數</span><span class="sxs-lookup"><span data-stu-id="e344a-105">Parameters</span></span>  
 <span data-ttu-id="e344a-106">ppCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="e344a-106">ppCallStackEnum</span></span>  
 <span data-ttu-id="e344a-107">[out]位址指標[ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)為堆疊追蹤列舉值的 managed 例外狀況物件的介面物件。</span><span class="sxs-lookup"><span data-stu-id="e344a-107">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e344a-108">備註</span><span class="sxs-lookup"><span data-stu-id="e344a-108">Remarks</span></span>  
 <span data-ttu-id="e344a-109">沒有呼叫堆疊資訊是否可用，則方法會傳回`S_OK`，和[ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)是有效的列舉值的長度為 0。</span><span class="sxs-lookup"><span data-stu-id="e344a-109">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="e344a-110">如果無法擷取的堆疊追蹤資訊的方法，則傳回值是`E_FAIL`並傳回沒有列舉值。</span><span class="sxs-lookup"><span data-stu-id="e344a-110">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="e344a-111">[ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)物件負責從堆疊追蹤資料解碼`_stackTrace`例外狀況物件的欄位。</span><span class="sxs-lookup"><span data-stu-id="e344a-111">The [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e344a-112">需求</span><span class="sxs-lookup"><span data-stu-id="e344a-112">Requirements</span></span>  
 <span data-ttu-id="e344a-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e344a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e344a-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e344a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e344a-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e344a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e344a-116">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e344a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e344a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e344a-117">See Also</span></span>  
 [<span data-ttu-id="e344a-118">ICorDebugExceptionObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="e344a-118">ICorDebugExceptionObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 [<span data-ttu-id="e344a-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e344a-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
