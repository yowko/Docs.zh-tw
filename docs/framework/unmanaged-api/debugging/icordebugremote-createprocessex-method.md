---
title: "ICorDebugRemote::CreateProcessEx 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRemote.CreateProcessEx
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugRemoteTarget::CreateProcessEx
helpviewer_keywords:
- CreateProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
- ICorDebugRemote::CreateProcessEx method [.NET Framework debugging]
ms.assetid: 41af93c7-e448-4251-8d4d-413d38c635f2
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 00709ffe4695ea0b56982cb60df15c2991b49d4e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugremotecreateprocessex-method"></a><span data-ttu-id="d5e68-102">ICorDebugRemote::CreateProcessEx 方法</span><span class="sxs-lookup"><span data-stu-id="d5e68-102">ICorDebugRemote::CreateProcessEx Method</span></span>
<span data-ttu-id="d5e68-103">啟動處理序在偵錯工具在遠端電腦上。</span><span class="sxs-lookup"><span data-stu-id="d5e68-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5e68-104">語法</span><span class="sxs-lookup"><span data-stu-id="d5e68-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="d5e68-105">參數</span><span class="sxs-lookup"><span data-stu-id="d5e68-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="d5e68-106">[in]指標[ICorDebugRemoteTarget 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="d5e68-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="d5e68-107">用來決定處理程序就會啟動所在的遠端電腦。</span><span class="sxs-lookup"><span data-stu-id="d5e68-107">Used to determine the remote machine on which the process will be launched.</span></span>  
  
 `lpApplicationName`  
 <span data-ttu-id="d5e68-108">[in]以 null 終止的字串，指定要啟動的程序中執行之模組的指標。</span><span class="sxs-lookup"><span data-stu-id="d5e68-108">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="d5e68-109">呼叫處理序的安全性內容中執行模組。</span><span class="sxs-lookup"><span data-stu-id="d5e68-109">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="d5e68-110">[in]以 null 終止的字串，指定要啟動的程序中執行的命令列的指標。</span><span class="sxs-lookup"><span data-stu-id="d5e68-110">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="d5e68-111">[in]未使用的遠端偵錯。</span><span class="sxs-lookup"><span data-stu-id="d5e68-111">[in] Unused for remote debugging.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="d5e68-112">[in]未使用的遠端偵錯。</span><span class="sxs-lookup"><span data-stu-id="d5e68-112">[in] Unused for remote debugging.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="d5e68-113">[in]未使用的遠端偵錯。</span><span class="sxs-lookup"><span data-stu-id="d5e68-113">[in] Unused for remote debugging.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="d5e68-114">[in]未使用的遠端偵錯。</span><span class="sxs-lookup"><span data-stu-id="d5e68-114">[in] Unused for remote debugging.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="d5e68-115">[in]新處理序的環境區塊的指標。</span><span class="sxs-lookup"><span data-stu-id="d5e68-115">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="d5e68-116">[in]以 null 終止的字串，指定處理序的目前目錄的完整路徑的指標。</span><span class="sxs-lookup"><span data-stu-id="d5e68-116">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="d5e68-117">如果這個參數是 null，新處理序必須相同目前的磁碟機和目錄做為呼叫處理序。</span><span class="sxs-lookup"><span data-stu-id="d5e68-117">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="d5e68-118">[in]未使用的遠端偵錯。</span><span class="sxs-lookup"><span data-stu-id="d5e68-118">[in] Unused for remote debugging.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="d5e68-119">[in]未使用的遠端偵錯。</span><span class="sxs-lookup"><span data-stu-id="d5e68-119">[in] Unused for remote debugging.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="d5e68-120">[in]未使用的遠端偵錯。</span><span class="sxs-lookup"><span data-stu-id="d5e68-120">[in] Unused for remote debugging.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="d5e68-121">[out]表示處理程序的 「 ICorDebugProcess 介面 」 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="d5e68-121">[out] A pointer to the address of a"ICorDebugProcess Interface" object that represents the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5e68-122">傳回值</span><span class="sxs-lookup"><span data-stu-id="d5e68-122">Return Value</span></span>  
 <span data-ttu-id="d5e68-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="d5e68-123">S_OK</span></span>  
 <span data-ttu-id="d5e68-124">已成功啟動遠端電腦，並傳回 「 ICorDebugProcess 介面 」 上的處理序進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="d5e68-124">Successfully launched the process on the remote machine and returned an "ICorDebugProcess Interface" for debugging.</span></span>  
  
 <span data-ttu-id="d5e68-125">E_FAIL (或其他 E_ 傳回碼)</span><span class="sxs-lookup"><span data-stu-id="d5e68-125">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="d5e68-126">無法啟動遠端電腦上的處理序，並傳回 「 ICorDebugProcess 介面 」，以供偵錯。</span><span class="sxs-lookup"><span data-stu-id="d5e68-126">Unable to launch the process on the remote machine and return an "ICorDebugProcess Interface" for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5e68-127">備註</span><span class="sxs-lookup"><span data-stu-id="d5e68-127">Remarks</span></span>  
 <span data-ttu-id="d5e68-128">Silverlight 中不支援混合模式偵錯。</span><span class="sxs-lookup"><span data-stu-id="d5e68-128">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5e68-129">需求</span><span class="sxs-lookup"><span data-stu-id="d5e68-129">Requirements</span></span>  
 <span data-ttu-id="d5e68-130">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d5e68-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5e68-131">**標頭：** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="d5e68-131">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="d5e68-132">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5e68-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5e68-133">**.NET framework 版本：** 4.5、 4、 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="d5e68-133">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5e68-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5e68-134">See Also</span></span>  
 [<span data-ttu-id="d5e68-135">ICorDebugRemote 介面</span><span class="sxs-lookup"><span data-stu-id="d5e68-135">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [<span data-ttu-id="d5e68-136">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="d5e68-136">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="d5e68-137">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d5e68-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
