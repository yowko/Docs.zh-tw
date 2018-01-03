---
title: "ICorDebugExceptionDebugEvent::GetFlags 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c6e7767ca5467f69dc7f53728bda9daf5f08331c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="4cad8-102">ICorDebugExceptionDebugEvent::GetFlags 方法</span><span class="sxs-lookup"><span data-stu-id="4cad8-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="4cad8-103">取得指出例外狀況是否可以被攔截的旗標。</span><span class="sxs-lookup"><span data-stu-id="4cad8-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cad8-104">語法</span><span class="sxs-lookup"><span data-stu-id="4cad8-104">Syntax</span></span>  
  
```  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4cad8-105">參數</span><span class="sxs-lookup"><span data-stu-id="4cad8-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="4cad8-106">[out]指標[CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)值，指出是否可以被攔截的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4cad8-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cad8-107">備註</span><span class="sxs-lookup"><span data-stu-id="4cad8-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4cad8-108">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="4cad8-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cad8-109">需求</span><span class="sxs-lookup"><span data-stu-id="4cad8-109">Requirements</span></span>  
 <span data-ttu-id="4cad8-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4cad8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cad8-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4cad8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4cad8-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4cad8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4cad8-113">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cad8-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cad8-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="4cad8-114">See Also</span></span>  
 [<span data-ttu-id="4cad8-115">ICorDebugExceptionDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="4cad8-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="4cad8-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4cad8-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
