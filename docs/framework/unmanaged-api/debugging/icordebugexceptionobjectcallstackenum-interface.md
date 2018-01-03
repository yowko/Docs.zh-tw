---
title: "ICorDebugExceptionObjectCallStackEnum 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugExceptionObjectCallStackEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords: ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f353ecaf4f0a64920fa7e23b98d09ef3191428cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="a5fc9-102">ICorDebugExceptionObjectCallStackEnum 介面</span><span class="sxs-lookup"><span data-stu-id="a5fc9-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="a5fc9-103">提供例外狀況物件中內嵌之呼叫堆疊資訊的列舉值。</span><span class="sxs-lookup"><span data-stu-id="a5fc9-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="a5fc9-104">這個介面是 ICorDebugEnum 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="a5fc9-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a5fc9-105">方法</span><span class="sxs-lookup"><span data-stu-id="a5fc9-105">Methods</span></span>  
  
|<span data-ttu-id="a5fc9-106">方法</span><span class="sxs-lookup"><span data-stu-id="a5fc9-106">Method</span></span>|<span data-ttu-id="a5fc9-107">描述</span><span class="sxs-lookup"><span data-stu-id="a5fc9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a5fc9-108">Icordebugexceptionobjectcallstackenum:: Next</span><span class="sxs-lookup"><span data-stu-id="a5fc9-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="a5fc9-109">取得指定的數目[CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)包含例外狀況物件的呼叫堆疊的相關資訊的物件。</span><span class="sxs-lookup"><span data-stu-id="a5fc9-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5fc9-110">備註</span><span class="sxs-lookup"><span data-stu-id="a5fc9-110">Remarks</span></span>  
 <span data-ttu-id="a5fc9-111">`ICorDebugExceptionObjectCallStackEnum`介面會實作 ICorDebugEnum 介面。</span><span class="sxs-lookup"><span data-stu-id="a5fc9-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="a5fc9-112">`ICorDebugExceptionObjectCallStackEnum`執行個體填入[CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)藉由呼叫物件[icordebugexceptionobjectvalue:: Enumerateexceptioncallstack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="a5fc9-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="a5fc9-113">可列舉集合中的呼叫堆疊項目，藉由呼叫[icordebugexceptionobjectcallstackenum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)方法</span><span class="sxs-lookup"><span data-stu-id="a5fc9-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5fc9-114">需求</span><span class="sxs-lookup"><span data-stu-id="a5fc9-114">Requirements</span></span>  
 <span data-ttu-id="a5fc9-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a5fc9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5fc9-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5fc9-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5fc9-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5fc9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5fc9-118">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5fc9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5fc9-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="a5fc9-119">See Also</span></span>  
 [<span data-ttu-id="a5fc9-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a5fc9-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="a5fc9-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="a5fc9-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
