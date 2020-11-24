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
ms.openlocfilehash: 243a1661ce2910cf1713ef8884bb6ae5422e8013
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679676"
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="c6aaf-102">ICorDebugManagedCallback::LoadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="c6aaf-102">ICorDebugManagedCallback::LoadAssembly Method</span></span>

<span data-ttu-id="c6aaf-103">通知偵錯工具已順利載入 common language runtime (CLR) 元件。</span><span class="sxs-lookup"><span data-stu-id="c6aaf-103">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6aaf-104">語法</span><span class="sxs-lookup"><span data-stu-id="c6aaf-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6aaf-105">參數</span><span class="sxs-lookup"><span data-stu-id="c6aaf-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="c6aaf-106">在ICorDebugAppDomain 物件的指標，代表已載入元件的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="c6aaf-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="c6aaf-107">在代表元件之 ICorDebugAssembly 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="c6aaf-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6aaf-108">需求</span><span class="sxs-lookup"><span data-stu-id="c6aaf-108">Requirements</span></span>  

 <span data-ttu-id="c6aaf-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c6aaf-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6aaf-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6aaf-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6aaf-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6aaf-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6aaf-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6aaf-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6aaf-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6aaf-113">See also</span></span>

- [<span data-ttu-id="c6aaf-114">UnloadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="c6aaf-114">UnloadAssembly Method</span></span>](icordebugmanagedcallback-unloadassembly-method.md)
- [<span data-ttu-id="c6aaf-115">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="c6aaf-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
