---
title: ICorDebugManagedCallback::UnloadAssembly 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadAssembly
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadAssembly method [.NET Framework debugging]
- UnloadAssembly method [.NET Framework debugging]
ms.assetid: 6734321c-c8a9-401f-a558-cad715ec4a77
topic_type:
- apiref
ms.openlocfilehash: 06c08499298656c8314d72667d9dac88c8d11e6a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788347"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="0ae8b-102">ICorDebugManagedCallback::UnloadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="0ae8b-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="0ae8b-103">通知偵錯工具已卸載通用語言執行時間元件。</span><span class="sxs-lookup"><span data-stu-id="0ae8b-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ae8b-104">語法</span><span class="sxs-lookup"><span data-stu-id="0ae8b-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ae8b-105">參數</span><span class="sxs-lookup"><span data-stu-id="0ae8b-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="0ae8b-106">在ICorDebugAppDomain 物件的指標，表示包含該元件的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="0ae8b-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="0ae8b-107">在表示元件之 ICorDebugAssembly 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="0ae8b-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ae8b-108">備註</span><span class="sxs-lookup"><span data-stu-id="0ae8b-108">Remarks</span></span>  
 <span data-ttu-id="0ae8b-109">此回呼之後，不應使用此元件。</span><span class="sxs-lookup"><span data-stu-id="0ae8b-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ae8b-110">需求</span><span class="sxs-lookup"><span data-stu-id="0ae8b-110">Requirements</span></span>  
 <span data-ttu-id="0ae8b-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ae8b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ae8b-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ae8b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ae8b-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ae8b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ae8b-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ae8b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ae8b-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="0ae8b-115">See also</span></span>

- [<span data-ttu-id="0ae8b-116">LoadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="0ae8b-116">LoadAssembly Method</span></span>](icordebugmanagedcallback-loadassembly-method.md)
- [<span data-ttu-id="0ae8b-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="0ae8b-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
