---
title: ICorDebugRemote::DebugActiveProcessEx 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.DebugActiveProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::DebugActiveProcessEx
helpviewer_keywords:
- ICorDebugRemote::DebugActiveProcessEx method [.NET Framework debugging]
- DebugActiveProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: b0df5c5d-9a2e-47bf-894c-6f8a9fe24a1f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13371d15c8b29f9ef93cc4af87acf85029404644
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744761"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="83b4d-102">ICorDebugRemote::DebugActiveProcessEx 方法</span><span class="sxs-lookup"><span data-stu-id="83b4d-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>
<span data-ttu-id="83b4d-103">啟動處理序在偵錯工具在遠端電腦上。</span><span class="sxs-lookup"><span data-stu-id="83b4d-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83b4d-104">語法</span><span class="sxs-lookup"><span data-stu-id="83b4d-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83b4d-105">參數</span><span class="sxs-lookup"><span data-stu-id="83b4d-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="83b4d-106">[in]指標[ICorDebugRemoteTarget 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="83b4d-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="83b4d-107">這個參數用來判斷處理程序執行所在的機器。</span><span class="sxs-lookup"><span data-stu-id="83b4d-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="83b4d-108">[in]偵錯工具後要附加到處理序的識別碼。</span><span class="sxs-lookup"><span data-stu-id="83b4d-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="83b4d-109">[in]`true`如果偵錯工具應該做為處理序的 Win32 偵錯工具，並分派 unmanaged 的回呼中; 否則`false`。</span><span class="sxs-lookup"><span data-stu-id="83b4d-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="83b4d-110">[out]表示要附加偵錯工具的程序的"ICorDebugProcess 」 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="83b4d-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83b4d-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="83b4d-111">Return Value</span></span>  
 <span data-ttu-id="83b4d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="83b4d-112">S_OK</span></span>  
 <span data-ttu-id="83b4d-113">已成功附加至遠端電腦上的處理序。</span><span class="sxs-lookup"><span data-stu-id="83b4d-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="83b4d-114">E_FAIL (或其他 E_ 傳回碼)</span><span class="sxs-lookup"><span data-stu-id="83b4d-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="83b4d-115">無法附加至遠端電腦上的處理序。</span><span class="sxs-lookup"><span data-stu-id="83b4d-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83b4d-116">備註</span><span class="sxs-lookup"><span data-stu-id="83b4d-116">Remarks</span></span>  
 <span data-ttu-id="83b4d-117">在 Silverlight 中不支援混合模式偵錯。</span><span class="sxs-lookup"><span data-stu-id="83b4d-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83b4d-118">需求</span><span class="sxs-lookup"><span data-stu-id="83b4d-118">Requirements</span></span>  
 <span data-ttu-id="83b4d-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="83b4d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83b4d-120">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83b4d-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83b4d-121">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83b4d-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83b4d-122">**.NET framework 版本：** 4.5，4，3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="83b4d-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83b4d-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83b4d-123">See also</span></span>

- [<span data-ttu-id="83b4d-124">ICorDebugRemote 介面</span><span class="sxs-lookup"><span data-stu-id="83b4d-124">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [<span data-ttu-id="83b4d-125">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="83b4d-125">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="83b4d-126">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="83b4d-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
