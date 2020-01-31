---
title: ICorDebugManagedCallback2::FunctionRemapComplete 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapComplete
helpviewer_keywords:
- FunctionRemapComplete method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapComplete method [.NET Framework debugging]
ms.assetid: 5396c4c3-4ec3-4e3a-a38d-d65b21f0a2fc
topic_type:
- apiref
ms.openlocfilehash: c6c1fa12248b9ff871e4a62a1a3584f688f2a921
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781494"
---
# <a name="icordebugmanagedcallback2functionremapcomplete-method"></a><span data-ttu-id="a17c6-102">ICorDebugManagedCallback2::FunctionRemapComplete 方法</span><span class="sxs-lookup"><span data-stu-id="a17c6-102">ICorDebugManagedCallback2::FunctionRemapComplete Method</span></span>
<span data-ttu-id="a17c6-103">通知偵錯工具程式碼執行已切換至新版本的已編輯函式。</span><span class="sxs-lookup"><span data-stu-id="a17c6-103">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a17c6-104">語法</span><span class="sxs-lookup"><span data-stu-id="a17c6-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionRemapComplete (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a17c6-105">參數</span><span class="sxs-lookup"><span data-stu-id="a17c6-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="a17c6-106">在ICorDebugAppDomain 物件的指標，表示包含已編輯之函數的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="a17c6-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="a17c6-107">在ICorDebugThread 物件的指標，代表發生重新對應中斷點的執行緒。</span><span class="sxs-lookup"><span data-stu-id="a17c6-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pFunction`  
 <span data-ttu-id="a17c6-108">在ICorDebugFunction 物件的指標，代表目前正線上程上執行的函式版本。</span><span class="sxs-lookup"><span data-stu-id="a17c6-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function currently running on the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a17c6-109">備註</span><span class="sxs-lookup"><span data-stu-id="a17c6-109">Remarks</span></span>  
 <span data-ttu-id="a17c6-110">此回呼可讓偵錯工具有機會重新建立先前存在的任何 steppers。</span><span class="sxs-lookup"><span data-stu-id="a17c6-110">This callback gives the debugger an opportunity to recreate any steppers that previously existed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a17c6-111">需求</span><span class="sxs-lookup"><span data-stu-id="a17c6-111">Requirements</span></span>  
 <span data-ttu-id="a17c6-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a17c6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a17c6-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a17c6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a17c6-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a17c6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a17c6-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a17c6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a17c6-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="a17c6-116">See also</span></span>

- [<span data-ttu-id="a17c6-117">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="a17c6-117">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="a17c6-118">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="a17c6-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
