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
ms.openlocfilehash: cd24e672c65769586dc618c21503dbb344566974
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731809"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="ea464-102">ICorDebugManagedCallback::CreateProcess 方法</span><span class="sxs-lookup"><span data-stu-id="ea464-102">ICorDebugManagedCallback::CreateProcess Method</span></span>

<span data-ttu-id="ea464-103">第一次附加或啟動處理常式時，通知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="ea464-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea464-104">語法</span><span class="sxs-lookup"><span data-stu-id="ea464-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea464-105">參數</span><span class="sxs-lookup"><span data-stu-id="ea464-105">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="ea464-106">在ICorDebugProcess 物件的指標，代表已附加或已啟動的進程。</span><span class="sxs-lookup"><span data-stu-id="ea464-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea464-107">備註</span><span class="sxs-lookup"><span data-stu-id="ea464-107">Remarks</span></span>  

 <span data-ttu-id="ea464-108">在 common language runtime 初始化之前，不會呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="ea464-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="ea464-109">大部分的 [ICorDebug](icordebug-interface.md) 方法會在回呼之前傳回 CORDBG_E_NOTREADY `CreateProcess` 。</span><span class="sxs-lookup"><span data-stu-id="ea464-109">Most of the [ICorDebug](icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea464-110">需求</span><span class="sxs-lookup"><span data-stu-id="ea464-110">Requirements</span></span>  

 <span data-ttu-id="ea464-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ea464-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea464-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ea464-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea464-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea464-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea464-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea464-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea464-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea464-115">See also</span></span>

- [<span data-ttu-id="ea464-116">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="ea464-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
