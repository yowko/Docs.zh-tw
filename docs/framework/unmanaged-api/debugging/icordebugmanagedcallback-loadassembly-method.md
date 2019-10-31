---
title: ICorDebugManagedCallback::LoadAssembly 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadAssembly
helpviewer_keywords:
- LoadAssembly method [.NET Framework debugging]
- ICorDebugManagedCallback::LoadAssembly method [.NET Framework debugging]
ms.assetid: 55cb673a-e240-43a6-a406-6912e7c0fe66
topic_type:
- apiref
ms.openlocfilehash: c6d77ff1393bc0ba4884dfa34810fee5316e33ef
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130739"
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="88e07-102">ICorDebugManagedCallback::LoadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="88e07-102">ICorDebugManagedCallback::LoadAssembly Method</span></span>
<span data-ttu-id="88e07-103">通知偵錯工具已成功載入 common language runtime （CLR）元件。</span><span class="sxs-lookup"><span data-stu-id="88e07-103">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88e07-104">語法</span><span class="sxs-lookup"><span data-stu-id="88e07-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88e07-105">參數</span><span class="sxs-lookup"><span data-stu-id="88e07-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="88e07-106">在ICorDebugAppDomain 物件的指標，表示已載入元件的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="88e07-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="88e07-107">在表示元件之 ICorDebugAssembly 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="88e07-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88e07-108">需求</span><span class="sxs-lookup"><span data-stu-id="88e07-108">Requirements</span></span>  
 <span data-ttu-id="88e07-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="88e07-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88e07-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="88e07-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88e07-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88e07-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88e07-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88e07-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88e07-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="88e07-113">See also</span></span>

- [<span data-ttu-id="88e07-114">UnloadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="88e07-114">UnloadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)
- [<span data-ttu-id="88e07-115">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="88e07-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
