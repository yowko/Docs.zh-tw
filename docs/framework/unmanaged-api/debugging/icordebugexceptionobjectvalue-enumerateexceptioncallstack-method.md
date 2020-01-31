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
ms.openlocfilehash: 57eb284bfe39ce92b2d6c03a2aeb4ae84d6aba91
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788672"
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="9c60b-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack 方法</span><span class="sxs-lookup"><span data-stu-id="9c60b-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>
<span data-ttu-id="9c60b-103">取得內嵌在例外狀況物件中之呼叫堆疊的列舉值。</span><span class="sxs-lookup"><span data-stu-id="9c60b-103">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c60b-104">語法</span><span class="sxs-lookup"><span data-stu-id="9c60b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c60b-105">參數</span><span class="sxs-lookup"><span data-stu-id="9c60b-105">Parameters</span></span>  
 <span data-ttu-id="9c60b-106">ppCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="9c60b-106">ppCallStackEnum</span></span>  
 <span data-ttu-id="9c60b-107">脫銷[ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md)介面物件之位址的指標，這是 managed 例外狀況物件的堆疊追蹤列舉值。</span><span class="sxs-lookup"><span data-stu-id="9c60b-107">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c60b-108">備註</span><span class="sxs-lookup"><span data-stu-id="9c60b-108">Remarks</span></span>  
 <span data-ttu-id="9c60b-109">如果沒有可用的呼叫堆疊資訊，方法會傳回 `S_OK`，而[ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md)是長度為0的有效枚舉器。</span><span class="sxs-lookup"><span data-stu-id="9c60b-109">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="9c60b-110">如果方法無法取得堆疊追蹤資訊，則傳回值會 `E_FAIL`，而且不會傳回任何枚舉器。</span><span class="sxs-lookup"><span data-stu-id="9c60b-110">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="9c60b-111">[ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md)物件負責從 exception 物件的 `_stackTrace` 欄位解碼堆疊追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="9c60b-111">The [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c60b-112">需求</span><span class="sxs-lookup"><span data-stu-id="9c60b-112">Requirements</span></span>  
 <span data-ttu-id="9c60b-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9c60b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c60b-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c60b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c60b-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c60b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c60b-116">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c60b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c60b-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="9c60b-117">See also</span></span>

- [<span data-ttu-id="9c60b-118">ICorDebugExceptionObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="9c60b-118">ICorDebugExceptionObjectValue Interface</span></span>](icordebugexceptionobjectvalue-interface.md)
- [<span data-ttu-id="9c60b-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="9c60b-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
