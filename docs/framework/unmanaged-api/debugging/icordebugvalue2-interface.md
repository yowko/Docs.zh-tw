---
title: ICorDebugValue2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugValue2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2
helpviewer_keywords:
- ICorDebugValue2 interface [.NET Framework debugging]
ms.assetid: 3ff2ad2a-da5a-461b-8627-1a8eba49df9c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0925cf217afafe57abf82cf51a77b1992bad5152
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966834"
---
# <a name="icordebugvalue2-interface"></a><span data-ttu-id="54072-102">ICorDebugValue2 介面</span><span class="sxs-lookup"><span data-stu-id="54072-102">ICorDebugValue2 Interface</span></span>
<span data-ttu-id="54072-103">擴充 "ICorDebugValue" 介面, 以提供對 "ICorDebugType" 物件的支援。</span><span class="sxs-lookup"><span data-stu-id="54072-103">Extends the "ICorDebugValue" interface to provide support for "ICorDebugType" objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="54072-104">方法</span><span class="sxs-lookup"><span data-stu-id="54072-104">Methods</span></span>  
  
|<span data-ttu-id="54072-105">方法</span><span class="sxs-lookup"><span data-stu-id="54072-105">Method</span></span>|<span data-ttu-id="54072-106">描述</span><span class="sxs-lookup"><span data-stu-id="54072-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="54072-107">GetExactType 方法</span><span class="sxs-lookup"><span data-stu-id="54072-107">GetExactType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md)|<span data-ttu-id="54072-108">取得`ICorDebugType`物件的介面指標, <xref:System.Type>表示這個值的。</span><span class="sxs-lookup"><span data-stu-id="54072-108">Gets an interface pointer to an `ICorDebugType` object that represents the <xref:System.Type> of this value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54072-109">備註</span><span class="sxs-lookup"><span data-stu-id="54072-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="54072-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="54072-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54072-111">需求</span><span class="sxs-lookup"><span data-stu-id="54072-111">Requirements</span></span>  
 <span data-ttu-id="54072-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="54072-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54072-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="54072-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54072-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54072-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54072-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54072-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54072-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54072-116">See also</span></span>

- [<span data-ttu-id="54072-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="54072-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

- [<span data-ttu-id="54072-118">ICorDebugValue3 介面</span><span class="sxs-lookup"><span data-stu-id="54072-118">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
