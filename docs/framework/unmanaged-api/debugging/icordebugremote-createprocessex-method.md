---
title: ICorDebugRemote::CreateProcessEx 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.CreateProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::CreateProcessEx
helpviewer_keywords:
- CreateProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
- ICorDebugRemote::CreateProcessEx method [.NET Framework debugging]
ms.assetid: 41af93c7-e448-4251-8d4d-413d38c635f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d05384af8201fae8cf81650d38c99a5c44e6bd16
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744783"
---
# <a name="icordebugremotecreateprocessex-method"></a><span data-ttu-id="e760f-102">ICorDebugRemote::CreateProcessEx 方法</span><span class="sxs-lookup"><span data-stu-id="e760f-102">ICorDebugRemote::CreateProcessEx Method</span></span>
<span data-ttu-id="e760f-103">啟動處理序在偵錯工具在遠端電腦上。</span><span class="sxs-lookup"><span data-stu-id="e760f-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e760f-104">語法</span><span class="sxs-lookup"><span data-stu-id="e760f-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcessEx (  
    [in]  ICorDebugRemoteTarget*      pRemoteTarget,  
    [in]  LPCWSTR                     lpApplicationName,  
    [in]  LPWSTR                      lpCommandLine,  
    [in]  LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
    [in]  LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
    [in]  BOOL                        bInheritHandles,  
    [in]  DWORD                       dwCreationFlags,  
    [in]  PVOID                       lpEnvironment,  
    [in]  LPCWSTR                     lpCurrentDirectory,  
    [in]  LPSTARTUPINFOW              lpStartupInfo,  
    [in]  LPPROCESS_INFORMATION       lpProcessInformation,  
    [in]  CorDebugCreateProcessFlags  debuggingFlags,  
    [out] ICorDebugProcess**          ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e760f-105">參數</span><span class="sxs-lookup"><span data-stu-id="e760f-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="e760f-106">[in]指標[ICorDebugRemoteTarget 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="e760f-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="e760f-107">用來判斷遠端電腦將在其啟動處理程序。</span><span class="sxs-lookup"><span data-stu-id="e760f-107">Used to determine the remote machine on which the process will be launched.</span></span>  
  
 `lpApplicationName`  
 <span data-ttu-id="e760f-108">[in]以 null 終止的字串，指定要啟動的程序執行模組的指標。</span><span class="sxs-lookup"><span data-stu-id="e760f-108">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="e760f-109">呼叫處理序的安全性內容中執行模組。</span><span class="sxs-lookup"><span data-stu-id="e760f-109">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="e760f-110">[in]以 null 終止的字串，指定要啟動的程序執行的命令列的指標。</span><span class="sxs-lookup"><span data-stu-id="e760f-110">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="e760f-111">[in]若未使用，可進行遠端偵錯。</span><span class="sxs-lookup"><span data-stu-id="e760f-111">[in] Unused for remote debugging.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="e760f-112">[in]若未使用，可進行遠端偵錯。</span><span class="sxs-lookup"><span data-stu-id="e760f-112">[in] Unused for remote debugging.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="e760f-113">[in]若未使用，可進行遠端偵錯。</span><span class="sxs-lookup"><span data-stu-id="e760f-113">[in] Unused for remote debugging.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="e760f-114">[in]若未使用，可進行遠端偵錯。</span><span class="sxs-lookup"><span data-stu-id="e760f-114">[in] Unused for remote debugging.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="e760f-115">[in]新的處理序的環境區塊的指標。</span><span class="sxs-lookup"><span data-stu-id="e760f-115">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="e760f-116">[in]以 null 終止的字串，指定處理程序的目前目錄的完整路徑的指標。</span><span class="sxs-lookup"><span data-stu-id="e760f-116">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="e760f-117">如果此參數為 null，新處理序會為呼叫處理序有相同的目前磁碟機和目錄。</span><span class="sxs-lookup"><span data-stu-id="e760f-117">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="e760f-118">[in]若未使用，可進行遠端偵錯。</span><span class="sxs-lookup"><span data-stu-id="e760f-118">[in] Unused for remote debugging.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="e760f-119">[in]若未使用，可進行遠端偵錯。</span><span class="sxs-lookup"><span data-stu-id="e760f-119">[in] Unused for remote debugging.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="e760f-120">[in]若未使用，可進行遠端偵錯。</span><span class="sxs-lookup"><span data-stu-id="e760f-120">[in] Unused for remote debugging.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="e760f-121">[out]表示處理程序的 「 ICorDebugProcess 介面 」 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="e760f-121">[out] A pointer to the address of a"ICorDebugProcess Interface" object that represents the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e760f-122">傳回值</span><span class="sxs-lookup"><span data-stu-id="e760f-122">Return Value</span></span>  
 <span data-ttu-id="e760f-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="e760f-123">S_OK</span></span>  
 <span data-ttu-id="e760f-124">已成功啟動遠端電腦並傳回 「 ICorDebugProcess 介面 」 上的處理序進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="e760f-124">Successfully launched the process on the remote machine and returned an "ICorDebugProcess Interface" for debugging.</span></span>  
  
 <span data-ttu-id="e760f-125">E_FAIL (或其他 E_ 傳回碼)</span><span class="sxs-lookup"><span data-stu-id="e760f-125">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="e760f-126">無法啟動遠端電腦上的處理序，並傳回 「 ICorDebugProcess 介面 」 偵錯。</span><span class="sxs-lookup"><span data-stu-id="e760f-126">Unable to launch the process on the remote machine and return an "ICorDebugProcess Interface" for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e760f-127">備註</span><span class="sxs-lookup"><span data-stu-id="e760f-127">Remarks</span></span>  
 <span data-ttu-id="e760f-128">在 Silverlight 中不支援混合模式偵錯。</span><span class="sxs-lookup"><span data-stu-id="e760f-128">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e760f-129">需求</span><span class="sxs-lookup"><span data-stu-id="e760f-129">Requirements</span></span>  
 <span data-ttu-id="e760f-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e760f-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e760f-131">**標頭：** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="e760f-131">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="e760f-132">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e760f-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e760f-133">**.NET framework 版本：** 4.5，4，3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="e760f-133">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e760f-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e760f-134">See also</span></span>

- [<span data-ttu-id="e760f-135">ICorDebugRemote 介面</span><span class="sxs-lookup"><span data-stu-id="e760f-135">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [<span data-ttu-id="e760f-136">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="e760f-136">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="e760f-137">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e760f-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
