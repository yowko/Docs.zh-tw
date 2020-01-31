---
title: ICorDebugExceptionDebugEvent::GetFlags 方法
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: aaf137b1d851d0de86bde697c9e3a512f34d2aa9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782923"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="50fc6-102">ICorDebugExceptionDebugEvent::GetFlags 方法</span><span class="sxs-lookup"><span data-stu-id="50fc6-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="50fc6-103">取得指出例外狀況是否可以被攔截的旗標。</span><span class="sxs-lookup"><span data-stu-id="50fc6-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50fc6-104">語法</span><span class="sxs-lookup"><span data-stu-id="50fc6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50fc6-105">參數</span><span class="sxs-lookup"><span data-stu-id="50fc6-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="50fc6-106">脫銷[CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md)值的指標，指出是否可以攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="50fc6-106">[out] A pointer to a [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50fc6-107">備註</span><span class="sxs-lookup"><span data-stu-id="50fc6-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50fc6-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="50fc6-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50fc6-109">需求</span><span class="sxs-lookup"><span data-stu-id="50fc6-109">Requirements</span></span>  
 <span data-ttu-id="50fc6-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="50fc6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50fc6-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50fc6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50fc6-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50fc6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50fc6-113">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50fc6-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50fc6-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="50fc6-114">See also</span></span>

- [<span data-ttu-id="50fc6-115">ICorDebugExceptionDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="50fc6-115">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="50fc6-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="50fc6-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
