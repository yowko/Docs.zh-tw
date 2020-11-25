---
title: ICorDebugManagedCallback::UnloadModule 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadModule
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadModule method [.NET Framework debugging]
- UnloadModule method [.NET Framework debugging]
ms.assetid: b12bfcd9-1e29-48bf-9a3d-44bfae5df5e8
topic_type:
- apiref
ms.openlocfilehash: f24d49189ee81a80397b94ee4113c9514c083dbc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723983"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="013cf-102">ICorDebugManagedCallback::UnloadModule 方法</span><span class="sxs-lookup"><span data-stu-id="013cf-102">ICorDebugManagedCallback::UnloadModule Method</span></span>

<span data-ttu-id="013cf-103">通知偵錯工具， (DLL) 的 common language runtime 模組已卸載。</span><span class="sxs-lookup"><span data-stu-id="013cf-103">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="013cf-104">語法</span><span class="sxs-lookup"><span data-stu-id="013cf-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="013cf-105">參數</span><span class="sxs-lookup"><span data-stu-id="013cf-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="013cf-106">在ICorDebugAppDomain 物件的指標，代表包含模組的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="013cf-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="013cf-107">在代表模組之 ICorDebugModule 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="013cf-107">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="013cf-108">備註</span><span class="sxs-lookup"><span data-stu-id="013cf-108">Remarks</span></span>  

 <span data-ttu-id="013cf-109">此呼叫之後不應使用模組。</span><span class="sxs-lookup"><span data-stu-id="013cf-109">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="013cf-110">需求</span><span class="sxs-lookup"><span data-stu-id="013cf-110">Requirements</span></span>  

 <span data-ttu-id="013cf-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="013cf-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="013cf-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="013cf-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="013cf-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="013cf-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="013cf-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="013cf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="013cf-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="013cf-115">See also</span></span>

- [<span data-ttu-id="013cf-116">LoadModule 方法</span><span class="sxs-lookup"><span data-stu-id="013cf-116">LoadModule Method</span></span>](icordebugmanagedcallback-loadmodule-method.md)
- [<span data-ttu-id="013cf-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="013cf-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
