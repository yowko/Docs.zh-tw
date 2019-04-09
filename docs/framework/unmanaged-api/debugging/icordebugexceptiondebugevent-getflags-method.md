---
title: ICorDebugExceptionDebugEvent::GetFlags 方法
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af4c7feb7076eeac6089a3255c7832c17a43469b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208835"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="d7d49-102">ICorDebugExceptionDebugEvent::GetFlags 方法</span><span class="sxs-lookup"><span data-stu-id="d7d49-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="d7d49-103">取得指出例外狀況是否可以被攔截的旗標。</span><span class="sxs-lookup"><span data-stu-id="d7d49-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7d49-104">語法</span><span class="sxs-lookup"><span data-stu-id="d7d49-104">Syntax</span></span>  
  
```  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7d49-105">參數</span><span class="sxs-lookup"><span data-stu-id="d7d49-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="d7d49-106">[out]指標[CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)值，指出是否可以被攔截的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d7d49-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7d49-107">備註</span><span class="sxs-lookup"><span data-stu-id="d7d49-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7d49-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="d7d49-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7d49-109">需求</span><span class="sxs-lookup"><span data-stu-id="d7d49-109">Requirements</span></span>  
 <span data-ttu-id="d7d49-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d7d49-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7d49-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7d49-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7d49-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7d49-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d7d49-113">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="d7d49-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d7d49-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7d49-114">See also</span></span>

- [<span data-ttu-id="d7d49-115">ICorDebugExceptionDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="d7d49-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="d7d49-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d7d49-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
