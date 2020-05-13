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
ms.openlocfilehash: 4b44a16d143c1daea1ea6c36eb096ab9a937b272
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210037"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="81db3-102">ICorDebugManagedCallback::UnloadModule 方法</span><span class="sxs-lookup"><span data-stu-id="81db3-102">ICorDebugManagedCallback::UnloadModule Method</span></span>
<span data-ttu-id="81db3-103">通知偵錯工具已卸載通用語言執行時間模組（DLL）。</span><span class="sxs-lookup"><span data-stu-id="81db3-103">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81db3-104">語法</span><span class="sxs-lookup"><span data-stu-id="81db3-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81db3-105">參數</span><span class="sxs-lookup"><span data-stu-id="81db3-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="81db3-106">在代表包含模組之應用程式域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="81db3-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="81db3-107">在代表模組之 ICorDebugModule 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="81db3-107">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81db3-108">備註</span><span class="sxs-lookup"><span data-stu-id="81db3-108">Remarks</span></span>  
 <span data-ttu-id="81db3-109">此呼叫之後，不應使用此模組。</span><span class="sxs-lookup"><span data-stu-id="81db3-109">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81db3-110">需求</span><span class="sxs-lookup"><span data-stu-id="81db3-110">Requirements</span></span>  
 <span data-ttu-id="81db3-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="81db3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81db3-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81db3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81db3-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81db3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81db3-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81db3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81db3-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="81db3-115">See also</span></span>

- [<span data-ttu-id="81db3-116">LoadModule 方法</span><span class="sxs-lookup"><span data-stu-id="81db3-116">LoadModule Method</span></span>](icordebugmanagedcallback-loadmodule-method.md)
- [<span data-ttu-id="81db3-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="81db3-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
