---
title: ICorDebugExceptionObjectCallStackEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 00b52f9f058853ba14fcfd1986366527de25a427
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680698"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="75b82-102">ICorDebugExceptionObjectCallStackEnum 介面</span><span class="sxs-lookup"><span data-stu-id="75b82-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="75b82-103">提供例外狀況物件中內嵌之呼叫堆疊資訊的列舉值。</span><span class="sxs-lookup"><span data-stu-id="75b82-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="75b82-104">這個介面是 ICorDebugEnum 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="75b82-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="75b82-105">方法</span><span class="sxs-lookup"><span data-stu-id="75b82-105">Methods</span></span>  
  
|<span data-ttu-id="75b82-106">方法</span><span class="sxs-lookup"><span data-stu-id="75b82-106">Method</span></span>|<span data-ttu-id="75b82-107">描述</span><span class="sxs-lookup"><span data-stu-id="75b82-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="75b82-108">ICorDebugExceptionObjectCallStackEnum::Next</span><span class="sxs-lookup"><span data-stu-id="75b82-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="75b82-109">取得指定的數目[CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)包含例外狀況物件的呼叫堆疊的相關資訊的物件。</span><span class="sxs-lookup"><span data-stu-id="75b82-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75b82-110">備註</span><span class="sxs-lookup"><span data-stu-id="75b82-110">Remarks</span></span>  
 <span data-ttu-id="75b82-111">`ICorDebugExceptionObjectCallStackEnum` ICorDebugEnum 介面實作的介面。</span><span class="sxs-lookup"><span data-stu-id="75b82-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="75b82-112">`ICorDebugExceptionObjectCallStackEnum`執行個體填入[CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)藉由呼叫物件[icordebugexceptionobjectvalue:: Enumerateexceptioncallstack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="75b82-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="75b82-113">可列舉集合中的呼叫堆疊項目，藉由呼叫[icordebugexceptionobjectcallstackenum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)方法</span><span class="sxs-lookup"><span data-stu-id="75b82-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75b82-114">需求</span><span class="sxs-lookup"><span data-stu-id="75b82-114">Requirements</span></span>  
 <span data-ttu-id="75b82-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="75b82-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75b82-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="75b82-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75b82-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75b82-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75b82-118">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75b82-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75b82-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75b82-119">See also</span></span>
- [<span data-ttu-id="75b82-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="75b82-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="75b82-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="75b82-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
