---
title: ICorDebugExceptionDebugEvent：： GetFlags 方法
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: 6c330ce5b375daacdf257eda16fd5e34012f5d69
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084758"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="52ccb-102">ICorDebugExceptionDebugEvent：： GetFlags 方法</span><span class="sxs-lookup"><span data-stu-id="52ccb-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="52ccb-103">取得指出例外狀況是否可以被攔截的旗標。</span><span class="sxs-lookup"><span data-stu-id="52ccb-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52ccb-104">語法</span><span class="sxs-lookup"><span data-stu-id="52ccb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52ccb-105">參數</span><span class="sxs-lookup"><span data-stu-id="52ccb-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="52ccb-106">脫銷[CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)值的指標，指出是否可以攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="52ccb-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52ccb-107">備註</span><span class="sxs-lookup"><span data-stu-id="52ccb-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52ccb-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="52ccb-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52ccb-109">需求</span><span class="sxs-lookup"><span data-stu-id="52ccb-109">Requirements</span></span>  
 <span data-ttu-id="52ccb-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="52ccb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52ccb-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52ccb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52ccb-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52ccb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52ccb-113">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52ccb-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52ccb-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="52ccb-114">See also</span></span>

- [<span data-ttu-id="52ccb-115">ICorDebugExceptionDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="52ccb-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="52ccb-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="52ccb-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
