---
title: ICorDebugExceptionDebugEvent::GetFlags 方法
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fbe6f6a2953c3f815606e881b86a693b7a0e6ec7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951904"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="8ed23-102">ICorDebugExceptionDebugEvent::GetFlags 方法</span><span class="sxs-lookup"><span data-stu-id="8ed23-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="8ed23-103">取得指出例外狀況是否可以被攔截的旗標。</span><span class="sxs-lookup"><span data-stu-id="8ed23-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ed23-104">語法</span><span class="sxs-lookup"><span data-stu-id="8ed23-104">Syntax</span></span>  
  
```  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ed23-105">參數</span><span class="sxs-lookup"><span data-stu-id="8ed23-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="8ed23-106">脫銷[CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)值的指標, 指出是否可以攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8ed23-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ed23-107">備註</span><span class="sxs-lookup"><span data-stu-id="8ed23-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ed23-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="8ed23-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ed23-109">需求</span><span class="sxs-lookup"><span data-stu-id="8ed23-109">Requirements</span></span>  
 <span data-ttu-id="8ed23-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8ed23-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ed23-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ed23-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ed23-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ed23-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ed23-113">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ed23-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ed23-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ed23-114">See also</span></span>

- [<span data-ttu-id="8ed23-115">ICorDebugExceptionDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="8ed23-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="8ed23-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="8ed23-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
