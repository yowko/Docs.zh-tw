---
title: ICorDebugAppDomainEnum Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum
helpviewer_keywords:
- ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: e9226e6e-ca2c-428e-bb38-0c099210f507
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e5d3d11e3897ff56ffcd475eb363405651578c1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomainenum-interface1"></a><span data-ttu-id="5c84e-102">ICorDebugAppDomainEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="5c84e-102">ICorDebugAppDomainEnum Interface1</span></span>
<span data-ttu-id="5c84e-103">提供`Next`方法，這個方法會傳回指定的數目的`ICorDebugAppDomainEnum`開始列舉中的下一個位置的值。</span><span class="sxs-lookup"><span data-stu-id="5c84e-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="5c84e-104">這個介面是 「 ICorDebugEnum"的子類別。</span><span class="sxs-lookup"><span data-stu-id="5c84e-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5c84e-105">方法</span><span class="sxs-lookup"><span data-stu-id="5c84e-105">Methods</span></span>  
  
|<span data-ttu-id="5c84e-106">方法</span><span class="sxs-lookup"><span data-stu-id="5c84e-106">Method</span></span>|<span data-ttu-id="5c84e-107">描述</span><span class="sxs-lookup"><span data-stu-id="5c84e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5c84e-108">Next 方法</span><span class="sxs-lookup"><span data-stu-id="5c84e-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-next-method.md)|<span data-ttu-id="5c84e-109">從集合中，從目前游標位置開始，取得指定的應用程式定義域數目。</span><span class="sxs-lookup"><span data-stu-id="5c84e-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c84e-110">備註</span><span class="sxs-lookup"><span data-stu-id="5c84e-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c84e-111">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="5c84e-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c84e-112">需求</span><span class="sxs-lookup"><span data-stu-id="5c84e-112">Requirements</span></span>  
 <span data-ttu-id="5c84e-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5c84e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c84e-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c84e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c84e-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c84e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c84e-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c84e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c84e-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="5c84e-117">See Also</span></span>  
 [<span data-ttu-id="5c84e-118">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="5c84e-118">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="5c84e-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="5c84e-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
