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
ms.openlocfilehash: e7ed6c04a46a767ed122e54df0695429cf923b8a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126200"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="c1765-102">ICorDebugExceptionObjectCallStackEnum 介面</span><span class="sxs-lookup"><span data-stu-id="c1765-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="c1765-103">提供例外狀況物件中內嵌之呼叫堆疊資訊的列舉值。</span><span class="sxs-lookup"><span data-stu-id="c1765-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="c1765-104">這個介面是 ICorDebugEnum 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="c1765-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c1765-105">方法</span><span class="sxs-lookup"><span data-stu-id="c1765-105">Methods</span></span>  
  
|<span data-ttu-id="c1765-106">方法</span><span class="sxs-lookup"><span data-stu-id="c1765-106">Method</span></span>|<span data-ttu-id="c1765-107">描述</span><span class="sxs-lookup"><span data-stu-id="c1765-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c1765-108">ICorDebugExceptionObjectCallStackEnum::Next</span><span class="sxs-lookup"><span data-stu-id="c1765-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="c1765-109">取得指定的數目[CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)包含例外狀況物件的呼叫堆疊的相關資訊的物件。</span><span class="sxs-lookup"><span data-stu-id="c1765-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1765-110">備註</span><span class="sxs-lookup"><span data-stu-id="c1765-110">Remarks</span></span>  
 <span data-ttu-id="c1765-111">`ICorDebugExceptionObjectCallStackEnum` ICorDebugEnum 介面實作的介面。</span><span class="sxs-lookup"><span data-stu-id="c1765-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="c1765-112">`ICorDebugExceptionObjectCallStackEnum`執行個體填入[CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)藉由呼叫物件[icordebugexceptionobjectvalue:: Enumerateexceptioncallstack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="c1765-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="c1765-113">可列舉集合中的呼叫堆疊項目，藉由呼叫[icordebugexceptionobjectcallstackenum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)方法</span><span class="sxs-lookup"><span data-stu-id="c1765-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1765-114">需求</span><span class="sxs-lookup"><span data-stu-id="c1765-114">Requirements</span></span>  
 <span data-ttu-id="c1765-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c1765-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1765-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c1765-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1765-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1765-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c1765-118">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="c1765-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c1765-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1765-119">See also</span></span>

- [<span data-ttu-id="c1765-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="c1765-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="c1765-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="c1765-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
