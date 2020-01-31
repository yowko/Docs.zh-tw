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
ms.openlocfilehash: 80836cbbf82a97ccd6dc7251e5cbe934e0cbe66f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777282"
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="67575-102">ICorDebugManagedCallback::LoadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="67575-102">ICorDebugManagedCallback::LoadAssembly Method</span></span>
<span data-ttu-id="67575-103">通知偵錯工具已成功載入 common language runtime （CLR）元件。</span><span class="sxs-lookup"><span data-stu-id="67575-103">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67575-104">語法</span><span class="sxs-lookup"><span data-stu-id="67575-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67575-105">參數</span><span class="sxs-lookup"><span data-stu-id="67575-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="67575-106">在ICorDebugAppDomain 物件的指標，表示已載入元件的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="67575-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="67575-107">在表示元件之 ICorDebugAssembly 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="67575-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67575-108">需求</span><span class="sxs-lookup"><span data-stu-id="67575-108">Requirements</span></span>  
 <span data-ttu-id="67575-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="67575-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67575-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67575-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67575-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67575-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67575-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67575-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67575-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="67575-113">See also</span></span>

- [<span data-ttu-id="67575-114">UnloadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="67575-114">UnloadAssembly Method</span></span>](icordebugmanagedcallback-unloadassembly-method.md)
- [<span data-ttu-id="67575-115">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="67575-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
