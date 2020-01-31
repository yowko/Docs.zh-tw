---
title: ICorDebugManagedCallback::CreateProcess 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateProcess
helpviewer_keywords:
- ICorDebugManagedCallback::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: 8e89d5ee-e4e3-4738-8302-0b7d1cf4846e
topic_type:
- apiref
ms.openlocfilehash: 0c3059697014cea33081f6cb81b9d93c7d028c2e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777474"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="65bfa-102">ICorDebugManagedCallback::CreateProcess 方法</span><span class="sxs-lookup"><span data-stu-id="65bfa-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="65bfa-103">第一次附加或啟動進程時，會通知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="65bfa-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65bfa-104">語法</span><span class="sxs-lookup"><span data-stu-id="65bfa-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65bfa-105">參數</span><span class="sxs-lookup"><span data-stu-id="65bfa-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="65bfa-106">在ICorDebugProcess 物件的指標，表示已附加或已啟動的進程。</span><span class="sxs-lookup"><span data-stu-id="65bfa-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65bfa-107">備註</span><span class="sxs-lookup"><span data-stu-id="65bfa-107">Remarks</span></span>  
 <span data-ttu-id="65bfa-108">在通用語言執行時間初始化之前，不會呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="65bfa-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="65bfa-109">大部分的[ICorDebug](icordebug-interface.md)方法會在 `CreateProcess` 回呼之前傳回 CORDBG_E_NOTREADY。</span><span class="sxs-lookup"><span data-stu-id="65bfa-109">Most of the [ICorDebug](icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65bfa-110">需求</span><span class="sxs-lookup"><span data-stu-id="65bfa-110">Requirements</span></span>  
 <span data-ttu-id="65bfa-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="65bfa-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65bfa-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65bfa-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65bfa-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65bfa-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65bfa-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65bfa-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65bfa-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="65bfa-115">See also</span></span>

- [<span data-ttu-id="65bfa-116">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="65bfa-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
