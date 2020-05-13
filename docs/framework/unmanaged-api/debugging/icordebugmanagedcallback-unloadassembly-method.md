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
ms.openlocfilehash: 07996a78d7f559de587c8a3eb2babfc06675169d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212642"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="66622-102">ICorDebugManagedCallback::UnloadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="66622-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="66622-103">通知偵錯工具已卸載通用語言執行時間元件。</span><span class="sxs-lookup"><span data-stu-id="66622-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66622-104">語法</span><span class="sxs-lookup"><span data-stu-id="66622-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66622-105">參數</span><span class="sxs-lookup"><span data-stu-id="66622-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="66622-106">在ICorDebugAppDomain 物件的指標，表示包含該元件的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="66622-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="66622-107">在表示元件之 ICorDebugAssembly 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="66622-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66622-108">備註</span><span class="sxs-lookup"><span data-stu-id="66622-108">Remarks</span></span>  
 <span data-ttu-id="66622-109">此回呼之後，不應使用此元件。</span><span class="sxs-lookup"><span data-stu-id="66622-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66622-110">需求</span><span class="sxs-lookup"><span data-stu-id="66622-110">Requirements</span></span>  
 <span data-ttu-id="66622-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="66622-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66622-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66622-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66622-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66622-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66622-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66622-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66622-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="66622-115">See also</span></span>

- [<span data-ttu-id="66622-116">LoadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="66622-116">LoadAssembly Method</span></span>](icordebugmanagedcallback-loadassembly-method.md)
- [<span data-ttu-id="66622-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="66622-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
