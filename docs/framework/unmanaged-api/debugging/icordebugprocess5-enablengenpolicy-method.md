---
title: "ICorDebugProcess5::EnableNGENPolicy 方法"
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
- ICorDebugProcess5::EnableNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dca0df7b0be643d53bb5b9a03bd3abbb186d69dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5enablengenpolicy-method"></a><span data-ttu-id="c2a9d-102">ICorDebugProcess5::EnableNGENPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="c2a9d-102">ICorDebugProcess5::EnableNGENPolicy Method</span></span>
<span data-ttu-id="c2a9d-103">設定值，這個值會決定應用程式載入 managed 偵錯工具下執行時的原生映像的方式。</span><span class="sxs-lookup"><span data-stu-id="c2a9d-103">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2a9d-104">語法</span><span class="sxs-lookup"><span data-stu-id="c2a9d-104">Syntax</span></span>  
  
```  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c2a9d-105">參數</span><span class="sxs-lookup"><span data-stu-id="c2a9d-105">Parameters</span></span>  
 `ePolicy`  
 <span data-ttu-id="c2a9d-106">[in]A [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)常數，決定如何應用程式載入 managed 偵錯工具下執行時的原生映像。</span><span class="sxs-lookup"><span data-stu-id="c2a9d-106">[in] A [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) constant that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2a9d-107">備註</span><span class="sxs-lookup"><span data-stu-id="c2a9d-107">Remarks</span></span>  
 <span data-ttu-id="c2a9d-108">如果原則設定已成功，則方法會傳回`S_OK`。</span><span class="sxs-lookup"><span data-stu-id="c2a9d-108">If the policy is set successfully, the method returns `S_OK`.</span></span> <span data-ttu-id="c2a9d-109">如果`ePolicy`超出所定義之列舉值的範圍[CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)，方法會傳回`E_INVALIDARG`和方法呼叫沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="c2a9d-109">If `ePolicy` is outside the range of the enumerated values defined by [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), the method returns `E_INVALIDARG` and the method call has no effect.</span></span> <span data-ttu-id="c2a9d-110">如果無法更新原生映像產生器 (Ngen.exe) 的原則，則方法會傳回`E_FAIL`。</span><span class="sxs-lookup"><span data-stu-id="c2a9d-110">If the policy of the Native Image Generator (Ngen.exe) cannot be updated, the method returns `E_FAIL`.</span></span>  
  
 <span data-ttu-id="c2a9d-111">`ICorDebugProcess5::EnableNGenPolicy`程序的存留期間，隨時可以呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="c2a9d-111">The `ICorDebugProcess5::EnableNGenPolicy` method can be called at any time during the lifetime of the process.</span></span> <span data-ttu-id="c2a9d-112">原則是作用中的任何原則設定之後載入的模組。</span><span class="sxs-lookup"><span data-stu-id="c2a9d-112">The policy is in effect for any modules that are loaded after the policy is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2a9d-113">需求</span><span class="sxs-lookup"><span data-stu-id="c2a9d-113">Requirements</span></span>  
 <span data-ttu-id="c2a9d-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c2a9d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2a9d-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2a9d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2a9d-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2a9d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2a9d-117">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2a9d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2a9d-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="c2a9d-118">See Also</span></span>  
 [<span data-ttu-id="c2a9d-119">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="c2a9d-119">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="c2a9d-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="c2a9d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="c2a9d-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="c2a9d-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
