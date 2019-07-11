---
title: ICorDebugManagedCallback::UnloadClass 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadClass
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadClass method [.NET Framework debugging]
- UnloadClass method [.NET Framework debugging]
ms.assetid: 66a59b18-ce9a-41f4-b23b-4dd6753d6d36
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 629a4850d47940633c8c69a7e464cfae315b3c56
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761241"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="12bc5-102">ICorDebugManagedCallback::UnloadClass 方法</span><span class="sxs-lookup"><span data-stu-id="12bc5-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="12bc5-103">正在卸載類別會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="12bc5-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12bc5-104">語法</span><span class="sxs-lookup"><span data-stu-id="12bc5-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12bc5-105">參數</span><span class="sxs-lookup"><span data-stu-id="12bc5-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="12bc5-106">[in]表示包含類別的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="12bc5-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="12bc5-107">[in]ICorDebugClass 物件，代表的類別指標。</span><span class="sxs-lookup"><span data-stu-id="12bc5-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12bc5-108">備註</span><span class="sxs-lookup"><span data-stu-id="12bc5-108">Remarks</span></span>  
 <span data-ttu-id="12bc5-109">在這個呼叫之後，類別不應參考。</span><span class="sxs-lookup"><span data-stu-id="12bc5-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12bc5-110">需求</span><span class="sxs-lookup"><span data-stu-id="12bc5-110">Requirements</span></span>  
 <span data-ttu-id="12bc5-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="12bc5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12bc5-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12bc5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12bc5-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12bc5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12bc5-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12bc5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12bc5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12bc5-115">See also</span></span>

- [<span data-ttu-id="12bc5-116">LoadClass 方法</span><span class="sxs-lookup"><span data-stu-id="12bc5-116">LoadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="12bc5-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="12bc5-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
