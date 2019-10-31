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
ms.openlocfilehash: 9f54fdfe16bc24394503ba6f5a9b906a32ec2c8b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091095"
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="a7b83-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack 方法</span><span class="sxs-lookup"><span data-stu-id="a7b83-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>
<span data-ttu-id="a7b83-103">取得內嵌在例外狀況物件中之呼叫堆疊的列舉值。</span><span class="sxs-lookup"><span data-stu-id="a7b83-103">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7b83-104">語法</span><span class="sxs-lookup"><span data-stu-id="a7b83-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7b83-105">參數</span><span class="sxs-lookup"><span data-stu-id="a7b83-105">Parameters</span></span>  
 <span data-ttu-id="a7b83-106">ppCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="a7b83-106">ppCallStackEnum</span></span>  
 <span data-ttu-id="a7b83-107">脫銷[ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)介面物件之位址的指標，這是 managed 例外狀況物件的堆疊追蹤列舉值。</span><span class="sxs-lookup"><span data-stu-id="a7b83-107">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7b83-108">備註</span><span class="sxs-lookup"><span data-stu-id="a7b83-108">Remarks</span></span>  
 <span data-ttu-id="a7b83-109">如果沒有可用的呼叫堆疊資訊，方法會傳回 `S_OK`，而[ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)是長度為0的有效枚舉器。</span><span class="sxs-lookup"><span data-stu-id="a7b83-109">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="a7b83-110">如果方法無法取得堆疊追蹤資訊，則傳回值會 `E_FAIL`，而且不會傳回任何枚舉器。</span><span class="sxs-lookup"><span data-stu-id="a7b83-110">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="a7b83-111">[ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)物件負責從 exception 物件的 `_stackTrace` 欄位解碼堆疊追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="a7b83-111">The [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7b83-112">需求</span><span class="sxs-lookup"><span data-stu-id="a7b83-112">Requirements</span></span>  
 <span data-ttu-id="a7b83-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a7b83-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7b83-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7b83-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7b83-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7b83-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7b83-116">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7b83-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7b83-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="a7b83-117">See also</span></span>

- [<span data-ttu-id="a7b83-118">ICorDebugExceptionObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="a7b83-118">ICorDebugExceptionObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)
- [<span data-ttu-id="a7b83-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a7b83-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
