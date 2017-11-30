---
title: "ICorDebugAppDomain4::GetObjectForCCW 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: abce5563e8cd7eb0c599e835d0217157cf073485
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="5c79d-102">ICorDebugAppDomain4::GetObjectForCCW 方法</span><span class="sxs-lookup"><span data-stu-id="5c79d-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="5c79d-103">從 COM 可呼叫包裝函式 (CCW) 指標取得 Managed 物件。</span><span class="sxs-lookup"><span data-stu-id="5c79d-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c79d-104">語法</span><span class="sxs-lookup"><span data-stu-id="5c79d-104">Syntax</span></span>  
  
```  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c79d-105">參數</span><span class="sxs-lookup"><span data-stu-id="5c79d-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="5c79d-106">[in] COM 可呼叫包裝函式 (CCW) 指標。</span><span class="sxs-lookup"><span data-stu-id="5c79d-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="5c79d-107">[out]"ICorDebugValue 」 物件，代表指定 CCW 指標對應之 managed 的物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="5c79d-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c79d-108">備註</span><span class="sxs-lookup"><span data-stu-id="5c79d-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c79d-109">需求</span><span class="sxs-lookup"><span data-stu-id="5c79d-109">Requirements</span></span>  
 <span data-ttu-id="5c79d-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5c79d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c79d-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c79d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c79d-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c79d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c79d-113">**.NET framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c79d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c79d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c79d-114">See Also</span></span>  
 [<span data-ttu-id="5c79d-115">ICorDebugAppDomain4 介面</span><span class="sxs-lookup"><span data-stu-id="5c79d-115">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 [<span data-ttu-id="5c79d-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="5c79d-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
